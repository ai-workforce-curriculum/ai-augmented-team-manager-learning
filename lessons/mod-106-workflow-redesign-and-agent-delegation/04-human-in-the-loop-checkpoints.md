# Chapter 4 — Human-in-the-Loop Checkpoints

> *"Human in the loop" is not a single pattern. There are at least four, they go in different places in the workflow, and picking the wrong one is a specific failure mode. A manager who signs an AI-governance questionnaire that asks for "HITL" without naming which kind is signing something they cannot actually operate.*

## Motivation

[EU AI Act (Regulation 2024/1689)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj), Article 14, requires that high-risk AI systems be designed so that *natural persons can effectively oversee them*. The [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf) GOVERN and MANAGE functions name human oversight as a load-bearing control. Internal AI-governance questionnaires at most organisations reduce both to a single checkbox: *"HITL: yes / no."* The checkbox is worse than nothing; it reads as a control when it is at most a label.

The routing matrix (Chapter 2) said *where the work goes.* The delegation ladder (Chapter 3) said *how much authority the agent has.* This chapter says *where humans actually sit in the loop* — and which **kind** of HITL applies at each sitting. Four kinds. Each has a specific job; each has a specific failure mode when misused as a substitute for the others.

Chapter 6's tool-authorisation policy enforces some of these checkpoints at the tool-call layer. Chapter 5's AGENTS.md documents them for the agent. But the design decision — which checkpoint of which kind sits where — is this chapter's job, and Exercise 04's.

## Core concepts

### The four kinds of HITL

Name them explicitly in the artifact. *Any* unlabelled "HITL" in a workflow document is a defect.

**Kind 1 — Pre-invocation approval.** A human is asked to approve *before* the agent is allowed to act. The human sees the proposed action; signs off or rejects; the agent then proceeds (or does not). Typical where the action is irrevocable or externally-visible. Examples: the agent proposes to send a customer email, deploy a release, or merge a PR — a human clicks *approve* before the action runs. The Cursor / Claude Code / Codex permission prompt that says *"Agent wants to run: `rm -rf node_modules`. Allow? [y/N/always]"* is a pre-invocation approval checkpoint rendered at the tool-call layer.

**Kind 2 — Mid-run gate.** A human is inserted into the agent's run at a defined point. The agent completes phase 1; the human reviews an intermediate artifact; the agent continues with phase 2 only after the review. The review can be lightweight (a human skims a plan and says *go*) or heavy (a human edits an intermediate draft before the agent proceeds). Typical in long-running agent workflows where the early phase is inside the frontier (fast planning) and later phases are near-or-outside (execution with real-world effects). The *planning review* in a software-agent run — the human reads the plan, edits one step, says *proceed* — is the canonical example.

**Kind 3 — Post-generation review.** The agent completes the run. The output is reviewed by a named human before it is used. This is the most common kind on an AI-paired workflow. The mod-103 review standard specifies what the human checks; mod-103's checklists are the operational form. Examples: the agent writes a code review comment; the PR author reads it and decides whether to act. The agent drafts the weekly team report; the manager reads it and sends it. The agent produces the aggregate alert summary; the outgoing on-call reads it before the handoff.

**Kind 4 — Periodic audit (aggregate HITL).** No per-instance human-in-the-loop; humans sample the aggregate on a cadence (weekly, monthly, per-N-outputs) and check for systematic errors. Appropriate only when the per-instance cost of a bad output is small *and* a cheap aggregate quality signal exists. The delegation-ladder levels 5, 6, and 7 (Chapter 3) are the typical home for kind-4-only workflows.

A row in the routing matrix can carry *more than one* kind. A Level-3 delegation can have Kind 3 (post-generation review) plus Kind 4 (monthly sample-audit). A Level-2 delegation can have Kind 1 (pre-invocation approval) plus Kind 3 (post-generation review) for different sub-steps of the same workflow.

### The mapping between delegation level and HITL kind

Chapter 3's ladder and this chapter's kinds must be consistent. The default mapping below is a starting point; your team will adjust specific rows.

| Delegation level (Chapter 3) | Minimum HITL kind required | Typical additional HITL |
|---|---|---|
| 1 — Shadow | Kind 4 only (periodic audit of suggestions) | None |
| 2 — Draft-and-present (approval) | Kind 3 (post-generation review, every instance) | Kind 1 for irrevocable tool calls inside the task |
| 3 — Draft-and-present (aggregate) | Kind 4 (periodic audit) | Kind 1 for any irrevocable call |
| 4 — Bounded co-decision | Kind 2 (mid-run gate at the decision point) | Kind 4 for the decision history |
| 5 — Act with advisory review | Kind 4 (periodic audit) + Kind 1 for irrevocable | — |
| 6 — Act unattended with post-hoc audit | Kind 4 only (at defined cadence) | — |
| 7 — Full automation | Kind 4 at low cadence; aggregate quality signal monitored | Aggregate-signal alerts |

Two rules the table encodes.

- **Kind 1 (pre-invocation approval) is independent of delegation level.** Any workflow with an irrevocable tool call has Kind 1 at that call site, regardless of overall level. Chapter 6 enforces this at the tool-authorisation policy layer.
- **Kind 4 (periodic audit) is required everywhere.** Even at Level 2, where every output is reviewed individually, the audit cadence catches systematic drift the per-instance reviewer may have grown lax about. Humans adapt quickly; a review that was rigorous in month 1 becomes rubber-stamp in month 6 unless an aggregate cross-check exists.

### What a checkpoint actually specifies

Designing a HITL checkpoint is specifying five fields. Any missing field makes the checkpoint non-operational.

- **Trigger** — the condition that fires the checkpoint. "Before any tool call matching `write|deploy|send` runs" is a trigger for Kind 1. "After phase 2 produces its artifact" is a trigger for Kind 2. "Every Friday at 10:00" is a trigger for Kind 4.
- **Reviewer role.** Not a person; a role. "On-call reviewer," "PR author," "staff engineer for this domain," "manager." Rotations and backups are specified at the role level.
- **What the reviewer checks.** A checklist, not a gut-check. For Kind 3, this is the mod-103 review-standard checklist (or a tailored subset). For Kind 1, this is a pre-defined list of impact questions: *who sees this output? can it be reversed? who else should see this before it ships?*
- **The decision surface.** Accept, reject, edit-and-accept, escalate. A checkpoint with only *"approve / reject"* loses the edit-and-accept case; most real reviews are edit-and-accept.
- **The SLA.** How long the reviewer has, and what happens on timeout. A Kind 1 checkpoint with no SLA degrades to *"the engineer eventually clicks yes."* A Kind 1 checkpoint with SLA *"5 minutes, then the agent aborts"* behaves. Kind 4 audits need a scheduled-time-on-calendar, not a vague cadence.

Any HITL checkpoint missing any one of these five fields is a draft, not a design. Exercise 04 asks you to produce fully-specified checkpoints for three real workflows on your team.

### The most common HITL design failures

Four recognisable failures, roughly mapped to the four kinds.

**Failure A — the "yes to all" pre-invocation approval.** Kind 1 checkpoints that fire too often, on low-impact actions, train the reviewer to accept without reading. In the limit, the reviewer configures *"always allow"* and the checkpoint is now a no-op. Counter-measure: scope Kind 1 to irrevocable or externally-visible actions only. If a Kind 1 is firing more than ~1 time per engineer per hour sustained, something is wrong with the tool-authorisation policy (Chapter 6).

The pattern is the same as alert fatigue in the security-engineering literature: sustained high-rate review degrades detection to near zero. <!-- needs-research: cite a canonical SOC alert-fatigue study (SANS, Ponemon, or academic review) to anchor the rate-vs-detection curve claim -->

**Failure B — the "missing" mid-run gate.** Workflows that look short enough to skip Kind 2, but have a judgment point in the middle (plan → execute → verify) where the plan review would have caught a bad decision cheaply. The absence is visible in the retrospective: *"the agent was going to do the wrong thing from step 1 but nobody saw the plan."* Counter-measure: any workflow with a planning phase and an execution phase that affects shared state has a Kind 2 at the boundary.

**Failure C — the "rubber-stamp" post-generation review.** Kind 3 checkpoints where the reviewer always accepts because the agent's output almost always looks fine. The failure is slow: the reviewer stops reading carefully, and eventually misses a subtle outside-frontier error. Counter-measures: *checklist-based reviews* (mod-103 standard — thumbs-up is not a checklist); *sample-audit of past approvals* (a Kind 4 audit on the Kind 3 reviewer's track record, quarterly); and a rotation on the reviewer role to prevent the specific drift of "I always approve this one."

**Failure D — the "ghost" periodic audit.** A Kind 4 audit that is scheduled but never happens, or that happens but produces no written artifact and no follow-up action. The audit's load-bearing property is the *writing-down-of-findings*; if the audit is a ten-minute Zoom with no document, it is theatre. Counter-measures: the audit produces a dated one-page finding (even *"no issues this cycle"* is a valid finding); a missing audit is a visible defect in the ladder review (Chapter 3).

### Edge cases that reshape the checkpoint design

Three situations reshape the default checkpoint patterns above.

**Edge case 1 — latency-critical workflows.** A workflow where response time is a feature (customer-facing chat, incident triage, trading, synchronous document co-editing) cannot afford a Kind 1 or Kind 2 checkpoint in the hot path without destroying the feature. The checkpoint pattern shifts: Kind 3 may become asynchronous ("review the day's chat transcripts the next morning"), Kind 4 becomes the primary mechanism, and Kind 1 is reserved for actions outside the latency-critical core (escalation to a human agent, refund issuance, compliance flag). The explicit trade — latency vs. control — is the design decision; a workflow with latency requirements and a Kind 1 checkpoint in the hot path is mis-designed.

**Edge case 2 — bursty workflows.** A workflow that runs at 100× its typical rate on specific days (incident response, product-launch eve, quarter-close) will overwhelm any Kind 3 checkpoint built for the typical rate. The design response: name the *burst mode* explicitly in the checkpoint spec. *"Under normal volume, Kind 3 fires on every output; under burst conditions (>50 per hour), Kind 3 drops to sampled Kind 4 at 10% sample rate, and the manager is paged so a human can scale the review."* The burst-mode downgrade is a *design*, not an *accident*.

**Edge case 3 — agent-to-agent workflows.** When the agent's output is consumed by another agent (not by a human), the Kind 3 "post-generation review" cannot be inherited from the downstream. The consuming agent is not a reviewer. Kind 3 either happens before the downstream agent runs, or Kind 4 (sample-audit the agent-to-agent transcript) replaces it. Chapter 6 discusses the Google A2A protocol in exactly this context — agent-to-agent pipelines without a human-review layer need their aggregate audit to be designed in explicitly, not assumed.

### How this chapter composes with mod-103 and the mod-101 contract

The mod-103 review standard is the operational content of the Kind 3 checkpoint. Any Kind 3 checkpoint in this chapter's design points to a mod-103 standard (or a sub-set of one tailored to the task). If your team's mod-103 review standard is still v0.1, the Kind 3 checkpoints in this exercise will outpace what mod-103 can back — note that explicitly in the checkpoint spec with a *"blocked on mod-103 §Review Standard v0.2"* marker.

The mod-101 human/machine contract's clause C2 (*"what humans must do before shipping"*) is instantiated by the Kind 1, 2, and 3 checkpoints. Your contract read without this chapter's checkpoint set is a sentence; with the checkpoint set, it is an operational plan. Cross-link in both directions.

## Example: HITL design for the on-call handoff workflow

Continuing the platform team example from Chapter 1. Three sub-tasks with three different HITL designs.

**Sub-task 1 — quantitative alert aggregation (Level 6 from Chapter 3).**

- Kind 1: none required (reads only).
- Kind 2: none (single-phase).
- Kind 3: none (Level 6 — no per-instance review).
- Kind 4: monthly sample-audit by rotating senior; written finding of each audit filed in `docs/mod-106-audit/`.
- SLA: audit date set at first-Monday-of-the-month; auditor named on the quarterly ladder-review (Chapter 3).

**Sub-task 2 — incident-narrative draft (Level 3 from Chapter 3).**

- Kind 1: at tool-call layer for any attempt to write to a channel other than the handoff draft channel.
- Kind 2: none.
- Kind 3: outgoing on-call reviews the narrative before the handoff meeting; mod-103 §On-call Doc Review checklist (five items); outgoing on-call rewrites root-cause section themselves (that section is *not* an AI output).
- Kind 4: monthly: pull five random weeks' incident narratives, re-read against the mod-109 postmortem standard, file a finding.
- Decision surface: accept / edit-and-accept / rewrite / escalate-to-postmortem.
- SLA: Kind 3 review completes within 90 minutes of the handoff meeting start.

**Sub-task 3 — live-risks list for next week (Senior human routing from Chapter 2).**

- Kind 1, 2, 3: not applicable (no AI in the loop for the artifact).
- Kind 4: the outgoing on-call's live-risks list is reviewed with the incoming on-call at handoff; "live risks" from previous handoffs that did not surface in the following week are archived, and the manager scans the archive quarterly to check whether the team's risk-reading is miscalibrated.
- SLA: quarterly review scheduled.

Three sub-tasks, three different HITL designs, none of them "HITL: yes."

## Summary

- **Four kinds of HITL,** each with a specific job: **Kind 1** pre-invocation approval; **Kind 2** mid-run gate; **Kind 3** post-generation review; **Kind 4** periodic audit.
- **Kind 1 is independent of delegation level** and is always required at irrevocable tool-call sites, regardless of frontier placement.
- **Kind 4 is required everywhere,** even at Level 2 workflows where every output is also reviewed, because per-instance reviewers drift.
- **A checkpoint is a five-field specification:** trigger, reviewer role, what the reviewer checks, decision surface, SLA. Missing any field makes the checkpoint non-operational.
- Four named failure modes: ***yes-to-all*** pre-invocation approval (Kind 1 scoped wrong); ***missing mid-run gate*** (Kind 2 absent from workflows with a judgment point); ***rubber-stamp post-generation review*** (Kind 3 without a checklist or rotation); ***ghost periodic audit*** (Kind 4 without a written finding).
- Three edge cases reshape the default pattern: **latency-critical workflows** (Kind 1/2 moved out of the hot path); **bursty workflows** (explicit burst-mode downgrade); **agent-to-agent workflows** (where the downstream agent cannot serve as the reviewer).
- The Kind 3 checkpoint is operationally the [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) review standard. The Kind 1, 2, 3 checkpoints collectively are the operational form of the mod-101 contract's **C2** clause.
- Exercise 04 produces fully-specified HITL checkpoints for three real workflows on your team; Chapter 6's tool-authorisation policy and Chapter 5's AGENTS.md encode them for the agent itself.
