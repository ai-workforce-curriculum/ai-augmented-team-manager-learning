# Chapter 3 — Authoring the Delegation Ladder

> *Delegation is a scalar, not a binary. For every task you route (even partially) to an agent, you have to say how much authority the agent has to act, where the human sits in the loop, and what happens when the agent reaches the ceiling. The delegation ladder is the artifact that answers.*

## Motivation

Pre-AI engineering management inherited a well-established vocabulary for human delegation. Jurgen Appelo's [*Delegation Poker* / seven levels of delegation](https://management30.com/practice/delegation-poker/) is the most compact version: *tell, sell, consult, agree, advise, inquire, delegate* — a ladder from "manager decides" to "report decides, manager informed afterwards (or not)." Andrew Grove's *task-relevant maturity* framing in [*High Output Management*](https://www.hachettebookgroup.com/titles/andrew-s-grove/high-output-management/9780679762881/) says the same thing from the other side: delegation level is a function of the delegatee's demonstrated competence on *this specific task*, not their title.

AI delegation inherits that vocabulary and *breaks it in one specific way*. A human delegatee has two properties the agent lacks: an internal sense of when they are out of their depth, and the social accountability that makes them escalate. An agent will not escalate by default. If you tell an agent to *"handle this,"* it will handle it — correctly if inside the frontier, plausibly-but-wrongly if outside. The delegation ladder for agent work must therefore do two jobs the human version did not need to do explicitly: it must name the *irrevocability class* of every tool call the agent is about to make, and it must name the *escalation condition* that forces the agent to stop and surface the decision.

Chapter 2 produced the task-routing matrix. For every row routed to AI, this chapter adds the *level* at which the agent is delegated to. Together with Chapter 4's HITL checkpoints and Chapter 6's tool-authorisation policy, the ladder is the operational spec for what the agent is allowed to do.

## Core concepts

### From Appelo's seven levels to an agent-delegation ladder

Appelo's seven levels for human delegation, mapped at least approximately to generative-AI agent work.

| Appelo (human) | Agent-delegation equivalent | What the agent does | What the human does |
|---|---|---|---|
| 1 — Tell | **Shadow mode** | Agent observes; produces suggestions that are logged and reviewed in aggregate, never used inline | Human does the work; reviews the aggregated agent suggestions on a cadence to calibrate future levels |
| 2 — Sell | **Draft-and-present (approval required)** | Agent produces a complete draft and surfaces it to a specific human reviewer; no artifact leaves until the reviewer approves | Reviewer approves, edits-and-approves, or rejects before the artifact is used |
| 3 — Consult | **Draft-and-present (approval optional for inside-frontier scope)** | Agent produces a draft; a lightweight review mechanism (checklist, aggregate audit) replaces per-instance human approval | Human runs the review mechanism on sampled outputs and on all out-of-scope outputs |
| 4 — Agree | **Bounded co-decision** | Agent proposes action; human agrees or disagrees; neither acts without the other | Human co-decides; the co-decision is the checkpoint |
| 5 — Advise | **Act with advisory review** | Agent takes the action; a human-reviewed advisory appears in a dashboard or digest; no per-action human in the loop | Human watches the advisory stream; intervenes if a pattern emerges |
| 6 — Inquire | **Act unattended with post-hoc audit** | Agent acts; audit happens on a cadence or on exception | Human runs the audit on a cadence; responds to exceptions |
| 7 — Delegate | **Full automation (rare)** | Agent acts; no human-facing audit per instance; aggregate quality signals only | Human owns the aggregate quality signal, not the per-instance outcome |

The mapping is approximate because agent delegation has a shape the human one does not: it is *per-task* and *per-tool-call*, not per-person. A single workflow can have a level-2 agent delegation on the planning step, a level-4 on tool selection, a level-5 on execution within a safe tool band, and a level-2 again on the final commit step. Chapter 6's tool-authorisation policy is where the per-tool-call grain lives; this chapter is where the per-workflow grain lives.

### The four pieces of a delegation ladder entry

Every row in the delegation ladder (one row per AI-touching row in your routing matrix) has four fields.

- **Level** (1–7 above), with a one-sentence justification in the matrix idiom from Chapter 2 (*"Level 3 because the task is inside the frontier and we have an aggregate audit mechanism; see mod-103 §Review Standard"*).
- **Scope ceiling.** What the agent is permitted to touch at this level. *"May read PR diff, call tests, write a review comment; may not merge, may not request changes from a human reviewer, may not modify PR."*
- **Escalation condition.** The named condition that forces the agent to stop and surface. *"Any proposed action affecting more than one file; any test failure the agent cannot localise to a single named cause; any PR touching `auth/`."*
- **Human on the loop.** The named role (not person) that receives the escalation and signs off. *"The PR author for level 3 reviews; the on-call reviewer for level 2."*

Four fields is the minimum. Chapter 5's AGENTS.md may add more team-specific fields; the four above are load-bearing.

### What changes between the human and agent versions of delegation

Three structural differences deserve attention.

**Difference 1: the agent does not escalate by default.** A human at delegation level 3 who hits a wall will ask. An agent will not, unless the escalation condition is *in the spec*. The delegation ladder for agent work therefore must make the escalation condition explicit, in machine-checkable form where possible ("more than one file touched," "test suite ran for >15 minutes," "any file matching `auth/*`"). The rough test: *if you cannot describe the escalation condition to a less-experienced engineer in one paragraph, the agent cannot act on it.*

**Difference 2: some tool calls are irrevocable.** A human engineer who does the wrong thing can usually back it out. An agent that sends a customer-facing email, posts to a public Slack channel, deploys code to production, or issues a payment has done something the human reviewer cannot un-do once it is done. The delegation ladder must therefore name the *irrevocability class* of the actions it permits. Chapter 6 formalises three classes:

- **Reversible** (reading, drafting, operations on ephemeral state) — can be routed to level 5–7 if the task is inside the frontier.
- **Reversible-with-work** (writes to version control before merge, draft artifacts, local changes before share) — level 3–5 typical.
- **Irrevocable at external effect** (deploys, external messages, payments, data deletions, workflow approvals) — level 2–4, with hard HITL gates (Chapter 4). Never promoted to level 7 at team scope regardless of frontier position; frontier placement is irrelevant to irrevocability.

The irrevocability class is a property of the *tool call*, not the *task*. A task that is inside the frontier can still have an irrevocable tool call inside it — and the irrevocable call dominates the delegation level.

**Difference 3: the agent's competence is not stable.** A human at task-relevant maturity N on task X is approximately at N on X next week. An agent on task X at frontier placement P today may be at a different P next month: model upgrade, prompt change, new tool, different team context. The ladder must carry a *re-check date* on every row, as the routing matrix does. A promotion from level 3 to level 5 is a *deliberate* decision with a date for review; a silent drift from level 3 to level 5 (because the team got lax about the review step) is the single most common delegation-ladder failure.

### The ladder change-management mechanic

A ladder with 12–20 rows will evolve. Four changes are common in the first 90 days of a mod-106-literate team:

- **Promotion.** A row moves from level 2 to level 3 (or 3 to 5). The team has watched the aggregate audits for a cycle and the quality signal is stable enough to reduce the per-instance human touch. A promotion needs a *written* justification one paragraph long, filed with the matrix row, naming the aggregate signal and the audit cadence.
- **Demotion.** A row moves from level 5 to level 3 (or worse). A near-miss, an incident ([`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/)), or a model regression has surfaced a class of error the previous level did not catch. The demotion is immediate; a written justification follows. Chapter 4 cross-links to the demotion-triggered checkpoint change.
- **Decomposition.** A row is split because the task-type was named too coarsely in Chapter 2. "Code review" splits into "single-file bug fix with regression test present" (level 3) and "multi-file refactor" (level 2) because the frontier runs between them.
- **Retirement.** A row is dropped from the ladder because the task is now routed entirely to a human (Chapter 2's *stop-doing-this* or route-to-human-only lanes). Retirements go into the quarterly audit record — they are a positive signal, not a failure.

Promotions are the most dangerous change; a disciplined ladder has a rule: *at most one promotion per row per quarter*. The temptation to promote several rows at once after a quarter of clean quality signal is real and should be resisted; the aggregate quality signal can hide a correlation (same model, same prompt, same team context) that will break on the next change.

### How the ladder composes with the routing matrix, the HITL checkpoints, and the tool-authorisation policy

Four artifacts, four layers.

- The **routing matrix** (Chapter 2) decides *which destination* owns the task.
- The **delegation ladder** (this chapter) decides *how much authority the agent has* inside the AI-touching routings.
- The **HITL checkpoints** (Chapter 4) decide *when and where humans sit in the loop* given the delegation level.
- The **tool-authorisation policy** (Chapter 6) decides *which tool calls* the agent can make at which delegation level.

A consistency rule: the delegation level and the HITL checkpoint set must agree. A level-2 row (draft-and-present) must have a post-generation review checkpoint; a level-5 row cannot have one (because level 5 by definition does not require per-instance review). Chapter 4 makes the mapping explicit.

The ladder is the artifact ICs read first. A new engineer on your team, after reading the mod-101 contract and the mod-103 review standard, should be able to read the ladder and know, for every workflow they will touch this quarter, *what the agent is allowed to do without asking a human.* If the ladder does not support that read in one sitting, it is not done.

### Where the ladder lives

Three conventions for the artifact's physical home.

- **Alongside the routing matrix in the repo.** If the matrix is `docs/mod-106-routing-matrix.md`, the ladder is `docs/mod-106-delegation-ladder.md`. Both are version-controlled, both are reviewed in the quarterly cadence.
- **Cross-referenced in the AGENTS.md** (Chapter 5). The AGENTS.md is the file the agent itself reads; the ladder is the file the humans read. The two must stay consistent — a mismatch is a blocking review item.
- **Exported to the dashboard or the team wiki read-only.** The ladder is a change-controlled artifact; the dashboard view is the live read for the team. The source of truth is the versioned file, not the dashboard — but the dashboard is the view junior engineers will actually open.

### Appelo's "delegation board" as the quarterly ritual

Appelo's [*Delegation Board*](https://management30.com/practice/delegation-board/) — a wall with the delegation level visible per decision area — is a useful shape to steal for the quarterly ladder review. On a mod-106-literate team, the quarterly cadence is: pull the ladder on screen; one row at a time, read the current level, the audit signal, the escalation record; decide *keep, promote, demote, decompose, retire*; one paragraph of justification per change; sign off. The ritual runs 45–60 minutes for a ladder of 12–20 rows.

The ritual is where the manager models the delegation discipline. A manager who announces a promotion with *"the AI's been doing great, let's give it more rope"* models the exact failure Chapter 2 named. A manager who announces a promotion with *"over the last two cycles the aggregate audit showed 97% acceptance, the sample-audit surfaced no new error class, we tested the model upgrade, and the delegation contract covers the irrevocability case — promote to level 5"* models the discipline the team will take home. Chapter 4's checkpoint review, Chapter 6's tool-authorisation review, and [`mod-103`](../mod-103-review-standards-and-eval-commissioning/)'s eval-finding review can all share the same hour.

## Example: three ladder entries from the platform team

Three rows from the delegation ladder for the platform team sketched at the end of Chapter 2. Format: level, scope ceiling, escalation condition, human on the loop, re-check date, one-sentence justification.

**Row 1 — on-call handoff: quantitative alert aggregation.**

- **Level: 6** — act unattended with post-hoc audit.
- **Scope ceiling:** read alert history for the past 7 days; produce aggregate counts and the Slack-format summary; write the summary to a specific handoff channel.
- **Escalation condition:** if the aggregation cannot complete due to a schema change, missing data, or a new service appearing in the data, raise and stop.
- **Human on the loop:** outgoing on-call runs a monthly sample-audit; the handoff-channel subscribers scan the daily summary.
- **Re-check date:** 2026-04-01.
- **Why:** inside frontier (mechanical aggregation); blast radius small (internal doc); aggregate audit mechanism in place.

**Row 2 — on-call handoff: narrative of the week's two critical incidents.**

- **Level: 3** — draft-and-present with aggregate audit replacing per-instance approval; outgoing on-call still reads and may rewrite the root-cause section, which the agent is not permitted to author.
- **Scope ceiling:** read incident Slack timeline, ticket data, and runbook; produce a narrative draft of the sequence of events; stop at the transition to "root-cause analysis."
- **Escalation condition:** if the timeline contains any event the agent cannot attribute to a named actor (human or service); if the incident is marked as externally-reported.
- **Human on the loop:** outgoing on-call.
- **Re-check date:** 2026-04-01.
- **Why:** sequence-of-events narrative is inside frontier; root-cause claim is outside frontier and must be authored by a human (see mod-109).

**Row 3 — new-service architecture decision record (ADR) authoring.**

- **Level: 2** — draft-and-present, human reviews full draft before any external use.
- **Scope ceiling:** may draft the background and alternatives-considered sections only; may *not* author the decision, consequences, or follow-up-actions sections; must flag the sections it did not author.
- **Escalation condition:** any request to author a section outside its scope ceiling; any proposal that cites internal systems the agent cannot verify from the repo context.
- **Human on the loop:** staff engineer who owns the service domain.
- **Re-check date:** 2026-07-01.
- **Why:** outside frontier on judgment; multi-quarter blast radius; AI useful only as background-reading drafter.

Three rows at three different delegation levels, each with an escalation condition the agent can actually check and a human role (not person) on the loop. The platform team's full ladder would carry 12–20 rows like these.

## Summary

- The delegation ladder maps **Appelo's seven levels of delegation** to agent work: *shadow, draft-and-present (approval), draft-and-present (aggregate audit), bounded co-decision, act with advisory review, act with post-hoc audit, full automation*.
- Four load-bearing fields per row: **level, scope ceiling, escalation condition, human on the loop** (plus a re-check date, inherited from the routing matrix).
- Three structural differences from human delegation: **the agent does not escalate by default** (so the escalation condition must be explicit), **some tool calls are irrevocable** (and the irrevocable class dominates the delegation level), **agent competence is not stable** (so every row carries a re-check date).
- Four change types in the quarterly ritual: **promotion, demotion, decomposition, retirement.** The rule-of-thumb is *at most one promotion per row per quarter*.
- The ladder composes with the routing matrix ([Chapter 2](02-the-task-routing-decision.md)), the HITL checkpoints ([Chapter 4](04-human-in-the-loop-checkpoints.md)), and the tool-authorisation policy ([Chapter 6](06-mcp-a2a-and-tool-authorisation-policy.md)); the AGENTS.md ([Chapter 5](05-agents-md-and-team-scope-conventions.md)) is where humans and agents share the summary.
- The quarterly **delegation-board ritual** (a one-hour review of the full ladder) is where the manager models the discipline that keeps the ladder honest.
- Exercise 02 (part) produces v0.1 of your team's ladder, alongside the AGENTS.md.
