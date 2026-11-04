# Chapter 2 — Operating the Accountability Contract End-to-End

> *The accountability contract from mod-103 Chapter 5 fits on a wall. The practice it implies fits in a runbook. This chapter walks the full flow — from the moment someone suspects an AI-produced artifact is wrong to the moment the standards are updated — and names the artifacts the manager owns at each step. The practice is deliberately mapped onto the team's existing incident-response flow (NIST SP 800-61 / Google SRE Managing Incidents / whatever your org already uses) rather than introducing a competing one.*

## Motivation

[`mod-103` Chapter 5](../mod-103-review-standards-and-eval-commissioning/05-the-accountability-contract-ai-generates-humans-own.md) names the C4 play when AI is wrong — pull it back, report within the window, preserve the trace, run the post-mortem, close the loop. Those five commitments compress the practice usefully for the contract text. For the team to actually run the practice, each needs to be decomposed into: *who does what, in which channel, within which time-window, producing which artifact*.

This chapter is that decomposition. It turns the five commitments into a seven-step flow — **detect, triage, contain, preserve, report, learn, close** — and names the manager-owned artifact at each step. The seven steps map onto the industry-standard IR flow (NIST SP 800-61 Rev. 2 *Computer Security Incident Handling Guide*; Google SRE's *Managing Incidents* chapter). The seven are not new; what is new is the *AI-specific* content of each step. The chapter is structured so a team already running an IR flow can slot the AI-specific pieces into the flow they have, rather than operate two flows in parallel.

The chapter also makes an important separation visible: **the detection channel for AI-produced wrongness is often not the production-outage channel**. Hallucination-driven harm, quiet model regression, and prompt-injection exploitation frequently surface through downstream data consumers, end-user reports, or partners, not through a pager. Chapter 2's detection discipline is therefore wider than SRE-style alerting.

## Core concepts

### The seven steps, named plainly

| Step | What happens | Manager artifact | Timing |
|---|---|---|---|
| **1. Detect** | A human (IC, reviewer, downstream consumer, partner, customer) or an automated signal (eval regression, guardrail trip, usage-metric anomaly) surfaces the suspicion that an AI-produced artifact is wrong. | Detection channels (named in the runbook) | *T = 0* |
| **2. Triage** | The on-call or named owner confirms whether this meets the incident bar, picks the severity, names the primary incident class (Chapter 4), and names an incident commander. | Severity ladder + incident-class picker | Within 30 minutes of detection |
| **3. Contain** | Revert if revertable; correct forward if not; stop the agent from making the situation worse (revoke tool authorisations if the agent is still active). | Contain checklist | Within 1 hour of triage |
| **4. Preserve trace** | Capture the AI-specific trace: prompt / prompt chain, model and version, agent harness and version, tool / MCP authorisations, retrieved context, as-submitted artifact. The AI-specific obligation. | Trace-preservation checklist | Within 1 hour of containment — *this step is time-critical* |
| **5. Report** | Post to the named incident channel with a short structured message; notify the accountable parties per the mod-103 contract; flag triggers to risk engineer / SecOps / counsel / upward (per Chapter 5). | Short-form report template | Within 1 working hour of triage for Sev-1/2; same day for Sev-3/4 |
| **6. Learn** | Run the blameless post-mortem per Chapter 3 within one week of resolution. Walk the fault chain. Produce the write-up. | Post-mortem artifact | Within one week |
| **7. Close** | Fold the learning back into the review checklist (mod-103), the standards-as-code stack (mod-103), the eval commissioning backlog (mod-103), and/or the routing-matrix and HITL checkpoints (mod-106). Verify the write-up names the specific changes. | Backfeed ticket(s) + updated change-log on the contract | Within two weeks of the post-mortem |

Steps 1–4 are the hour-scale work. Step 5 is the day-scale work. Steps 6–7 are the week-scale work. The runbook makes each explicit; Exercise 01 produces it for the team.

### Step 1 — Detection: the channels are plural

Pre-AI, "detection" is largely a production-signal question — pager, alert, error-rate spike. Under AI augmentation, four detection channels run in parallel and the team has to monitor all of them:

- **Operational signals.** The team's existing monitoring, error budgets, SLOs, alert-routing. AI-produced incidents sometimes surface here (a bug in AI-authored code causes a 500 rate spike), but often do not (a factual error in an AI-produced document is invisible to ops).
- **Eval-regression signals.** The regression gates the team commissioned in mod-103 Chapter 4 running on a cadence (CI, nightly, pre-release). When a commissioned eval that was passing starts failing after a model-version change or a prompt change, that is a detection signal before anything has shipped broken.
- **Downstream-consumer signals.** The reviewer of a downstream report, the partner who got the email, the customer-success engineer who got the ticket. These signals arrive in human channels (Slack, email, ticket systems) that the engineering team may not monitor by default. The runbook has to name which channels and which humans have the responsibility to escalate what they see.
- **Vendor-side signals.** Model-vendor changelog, provider status page, guardrail-vendor advisory, security-vendor CVE for an MCP server or an agent harness. These are *leading* signals — they predict a class of incident is now more likely, before any specific case has surfaced.

The runbook names the detection channel for each category and the on-call rotation or named owner who responds. The default production-incident-channel-is-enough answer is wrong for AI-produced wrongness; Chapter 4's taxonomy makes the shortfall concrete.

### Step 2 — Triage: the severity ladder and the incident-class picker

The team already has a severity ladder for production incidents. For AI-produced incidents, extend the ladder along two dimensions the pre-AI version does not cover:

- **Reach of the wrong output.** Did the wrong output ship to zero external parties, one, dozens, or many? Partner-report-level reach is higher-severity than internal-dashboard-level reach is higher-severity than dev-sandbox-level reach.
- **Reversibility.** Can the wrong output be recalled (internal document — yes; dashboard that was screen-shared in an executive meeting — partly; email sent to a partner — no; number shared in a public post — no).

A workable team-scope ladder:

- **Sev-1.** External harm (partner, customer, public). Irreversible or time-critical. Legal / counsel trigger likely. Executive stakeholder likely involved.
- **Sev-2.** Material internal harm (wrong number in an executive dashboard, wrong data in a critical pipeline, wrong output to a cross-functional stakeholder) with limited external reach.
- **Sev-3.** Internal harm contained to the team or to a tight loop (wrong code shipped to pre-prod; wrong internal doc; wrong eval output that would have landed broken but was caught).
- **Sev-4.** Potential-harm learning case (a near-miss, an eval regression that caught a model behaviour before it shipped). Runs through the same flow but at lighter weight.

The **incident-class picker** sits beside the severity ladder: the on-call incident commander names which of the four AI-specific classes (Chapter 4) this incident is most likely in — hallucination-driven harm, prompt-injection exploitation, unauthorised-tool-use, model regression — because the trace-preservation and the routing contract differ by class.

Name an **incident commander**. For Sev-1 / Sev-2, the manager is typically the IC by default until delegated. For Sev-3 / Sev-4, a senior IC on the team runs the response and the manager coordinates.

### Step 3 — Contain: stop the agent from making it worse

Containment in an AI-produced incident has one specific move that pre-AI containment does not: **if the agent that caused the incident is still active, revoke its authorisations before anything else**. If the agent has tool authorisations (file write, API calls, MCP tool connections, outbound comms), a long-running session can continue to produce output while the human is figuring out what to do. The default contain action is: revoke the agent's tool authorisations, close the session, archive the session state.

Other contain actions, in rough order:

1. Revoke agent tool authorisations if still active.
2. Revert the AI-produced change if revertable.
3. If not revertable, correct forward and queue the comms (Step 5).
4. If the incident involves data exposure, credential compromise, or intrusion → engage SecOps *now*, not later. Containment for the SOC-side chain belongs to SecOps.
5. If the incident is likely to recur for other users or other sessions, pause the specific workflow or guard the specific prompt until the fix lands.

The contain step is time-pressured but is not where the post-mortem happens. Do not conflate containment with root-cause analysis. The goal is to stop the bleeding; the root cause is for Step 6.

### Step 4 — Preserve trace: the AI-specific obligation

This step is the one the pre-AI runbook does not have, and it is the one most likely to be skipped under time pressure. Preserve, before anything can decay:

- **The prompt or prompt chain.** The exact text the human sent to the model, including any prior conversation state the model saw. For agent systems with internal planning prompts, the planning-prompt tree if the harness exposes it.
- **The model and version.** Vendor, model identifier, model version at the time of the call. If the vendor does not expose version pinning, record the date and time stamp against the vendor's changelog or deprecation page.
- **The agent harness and version.** Which harness was running (Claude Code, Cursor, Copilot, internal agent, bespoke orchestrator), the harness version, the configuration (which rules files, which AGENTS.md, which tool connections authorised, which guardrails on).
- **The tool / MCP authorisations.** Every tool the agent was allowed to call in this session, every tool it actually called, the arguments and returns of each call. If an [MCP](https://modelcontextprotocol.io/) server was involved, name which one and what tools it exposed.
- **The retrieved context.** Any RAG hits, file contents the agent was given, documentation the agent accessed, tool-call returns that fed back into the model's context window.
- **The as-submitted artifact.** The exact output — the code diff, the document, the number, the email — as submitted, not as corrected.
- **The reviewer's path.** What the reviewer saw at review time, how long they spent, what passed through automated checks before them.

A **trace-preservation checklist** is the artifact. The checklist is written to be runnable by a non-manager in the hour after an incident surfaces — the IC or the reviewer can run it with the manager supervising. Observability platforms purpose-built for LLM applications (e.g., [LangSmith](https://docs.smith.langchain.com/) trace views, [Weights & Biases Weave](https://wandb.ai/site/weave), [Arize](https://arize.com/)) make much of this automatic if they are wired up in advance; the runbook names which of these the team uses and where the archive lives.

The checklist exists as a static artifact *before* an incident so it is not improvised during one. Exercise 01 produces the v0.1.

Why this step is load-bearing: the fault chain in Chapter 3 is walked across the preserved trace. If the trace is incomplete — the agent session closed and the retrieved context was not captured — the fault chain stops at "the model said something wrong" and the systemic cause is invisible. The team cannot change the system to prevent the next incident of the same shape because it did not learn what the system was doing.

### Step 5 — Report: structure the message, route to the accountable parties

The report to the incident channel is short-form and structured. A workable five-field template:

- **What happened** (one sentence).
- **Severity** (ladder entry) and **incident class** (one of the four from Chapter 4, best-guess OK at this point).
- **Who is on it** (incident commander + supporting roles).
- **Blast radius so far** (external reach, internal reach, whether contained).
- **Known triggers flagged** (risk engineer? SecOps? counsel? upward to L45+?).

The structured form matters because the manager has to produce this report under pressure, often while coordinating multiple other things. A fill-in-the-blanks template reads faster for leadership and reads more consistently across incident commanders.

Beyond the channel post, Step 5 also routes to the accountable parties named in the mod-103 contract:

- The **IC** who submitted the artifact: already engaged by this point (they are often the one who flagged it or is being asked to help contain). Notified formally that this is now a logged incident.
- The **reviewer** who approved: notified formally. This is a sensitive moment; Chapter 3 is explicit on the blameless frame. The reviewer is notified because they are an accountable party in the contract, not because they are at fault.
- The **manager**: if the manager is not the incident commander, the commander notifies the manager at this step.
- The **vendor**: not at this step, except in narrow cases (the vendor has a security-reporting process and the incident is a security case). Vendor engagement is a Step 6 or Step 7 artifact unless SLA-triggered action is required immediately.

Chapter 5 is where the routing contract with `ai-risk-engineer` and SecOps lives; this step's trigger-flag notes populate that routing.

### Step 6 — Learn: the post-mortem (handed to Chapter 3)

The post-mortem is the Chapter 3 deliverable. From Step 6's perspective in this chapter, the thing to note is the *timing* and the *attendance list*:

- **Timing.** Within one week of Sev-1 / Sev-2 resolution; within two weeks for Sev-3; Sev-4 is folded into the next retrospective rather than run standalone.
- **Attendance.** The incident commander, the IC, the reviewer, the manager, and whichever specialist peer was engaged (`ai-risk-engineer` or SecOps if applicable). Not attended by: anyone whose role is primarily to assign blame.
- **Artefact.** The blameless post-mortem write-up per the Chapter 3 template. Exercise 02 is the artifact.

### Step 7 — Close: the backfeed to standards

The backfeed closes the loop that mod-103 Chapter 5 described conceptually. For each incident, one or more of the following tickets is opened and tracked to completion:

- **Review-checklist update** (mod-103 Chapter 2). A new row in the review checklist that catches the next incident of this shape.
- **Standards-as-code update** (mod-103 Chapter 3). A new Cursor rule, AGENTS.md section, lint policy, or ADR rule that prevents the authoring step.
- **Eval-commissioning ticket** (mod-103 Chapter 4). A new regression row — a golden task, a mutation test, an LLM-as-judge rubric — that would catch the next incident automatically.
- **Routing-matrix amendment** (mod-106 Chapter 2). A change to which workflow shapes route to which destination (AI-first, paired-review, human-first) based on the incident shape.
- **HITL-checkpoint amendment** (mod-106 Chapter 4). A new checkpoint or an escalated checkpoint on the specific workflow.
- **Tool-authorisation amendment** (mod-106 Chapter 6). A tool that was authorised unattended that is now gated, or a tool authorisation that is removed entirely.
- **Contract change-log entry** (mod-103 Chapter 5). The accountability contract's change-log gets a one-line entry: what incident, what changed, which section.

Chapter 6 is the backfeed discipline in full. Step 7 is the runbook-level checklist that the discipline is actually running.

### The runbook as one artifact

The runbook is not a stack of seven loose pieces; it is one artifact that fits on 5–8 pages. Suggested table of contents:

1. Scope. What incidents this runbook covers; what routes to SecOps, counsel, or upward instead.
2. Detection channels (Step 1 content).
3. Severity ladder and incident-class picker (Step 2 content).
4. Contain checklist (Step 3 content).
5. Trace-preservation checklist (Step 4 content).
6. Report template and routing (Step 5 content).
7. Post-mortem cadence (Step 6 pointer to Chapter 3).
8. Backfeed tickets (Step 7 pointer to Chapter 6).
9. Change log.

Exercise 01 produces v0.1 of this artifact.

### What the C4 contract looks like running correctly

A single-paragraph before-and-after, illustrative:

> *Before mod-109:* an AI-produced artifact ships broken; the reviewer notices two days later; the team improvises a response; the post-mortem is written but no standards change; the next incident of the same shape lands six weeks later.
>
> *After mod-109:* detection via the named channel (24 hours faster because the downstream-consumer path now routes to the incident channel); triage in 25 minutes picking Sev-2 and the `hallucination-driven harm` class; contain in 40 minutes; trace preserved via the checklist in the 20 minutes after that; structured report posted at the one-working-hour mark naming the IC, the reviewer, the risk-engineer trigger, and the executive stakeholder; post-mortem run in the Friday ritual five working days later; three backfeed tickets opened — one eval row commissioned, one review-checklist row added, one HITL checkpoint escalated on the specific workflow; contract change-log updated. The next incident of the same shape does not land, because the eval catches the regression before the artifact ships.

The practice is not heroic. It is specifically the small moves, in sequence, that compound.

## Example: the seven steps run on a composite incident

Illustrative composite; calibration, not a case study. Carries forward the Chapter 1 example (a wrong number reached an executive dashboard through an AI-authored pipeline change).

1. **Detect** (Monday 09:30). A business-partner downstream consumer flags the wrong number in `#reports-feedback`. The runbook has named `#reports-feedback` as a detection channel; the pipeline team's on-call engineer sees the flag and acknowledges.
2. **Triage** (09:55). On-call engineer confirms the artifact is wrong, severity Sev-2 (material internal reach; one external email mentioned the number over the weekend; reversibility partial). Incident class: hallucination-driven harm by Chapter 4's taxonomy (the AI-authored change introduced a silent column-aggregation error that the pre-release pass through the pipeline did not catch). Incident commander: senior IC on the pipeline team; manager coordinating.
3. **Contain** (10:35). The IC reverts the AI-authored change in the pipeline. A re-run of the pipeline produces the corrected number. The agent session that produced the original change is no longer active; no tool authorisations to revoke. Downstream dashboards are updated.
4. **Preserve trace** (10:55). The IC walks the trace-preservation checklist: the Claude Code session ID, the prompt chain, the retrieved context (which included a stale column-mapping doc the agent read), the exact as-submitted diff, the model version. Captured to the incident ticket.
5. **Report** (11:04). Incident commander posts the structured report in `#eng-ai-incidents`. Trigger-flags: `ai-risk-engineer` (eval gap → yes), SecOps (no, no data exposure), counsel (one external email with the wrong number → *flag for the CFO's EA to assess*), upward (VP who received the Monday morning question → *looped in by the manager*).
6. **Learn** (Thursday 15:00). Blameless post-mortem run per Chapter 3. Fault chain walked: reviewer approved in three minutes, under queue pressure; the AI-authored diff had a subtle column-aggregation bug that unit tests did not exercise; the retrieved context the agent used included a stale column-mapping doc; the harness did not flag the stale doc because the staleness signal was not in its scope; no eval existed that would have caught the aggregation. Write-up published Friday.
7. **Close** (next two weeks). Three backfeed tickets open: (a) commission an eval row — mutation test on the aggregation function — through the `ai-risk-engineer` (Exercise 05 is the ritual that makes this land); (b) update the review checklist with a *"AI-authored pipeline changes must include a diff-vs-prior-run snapshot in the PR"* row; (c) update the stale-context detection rule in the agent's retrieval configuration (mod-106 Chapter 6 tool-authorisation amendment). Contract change-log entry filed. Four weeks later the eval catches a similar near-miss on a different pipeline change; it does not ship.

Seven steps, 30 working hours of effort spread over three weeks, no heroics, two durable changes to the standards stack, one near-miss caught.

## Summary

- The C4 play from [`mod-103` Chapter 5](../mod-103-review-standards-and-eval-commissioning/05-the-accountability-contract-ai-generates-humans-own.md) decomposes into **seven steps** — detect, triage, contain, preserve, report, learn, close — mapped onto the team's existing IR flow (NIST SP 800-61, Google SRE *Managing Incidents*).
- **Detection channels are plural.** Operational signals, eval-regression signals, downstream-consumer signals, vendor-side signals. The default production-channel is not enough for AI-produced wrongness.
- **Triage adds AI-specific extensions.** Severity ladder extended for reach and reversibility; incident-class picker names one of the four AI-specific classes ([Chapter 4](04-ai-specific-incident-taxonomy-and-triage.md)); named incident commander.
- **Containment has one AI-specific move:** revoke the agent's tool authorisations if still active, then revert or correct forward.
- **Trace preservation is the load-bearing AI-specific step.** Prompt / prompt chain, model + version, agent harness + version, tool / MCP authorisations, retrieved context, as-submitted artifact, reviewer's path. Runbook names the checklist and the observability tooling.
- **Report short-form, route per contract.** Five-field structured message; accountable parties notified per the mod-103 contract; triggers flagged to risk engineer / SecOps / counsel / upward per [Chapter 5](05-routing-contract-with-risk-engineer-and-secops.md).
- **Learn** within one week of Sev-1 / Sev-2 resolution; the blameless post-mortem is the [Chapter 3](03-blameless-postmortems-adapted-for-ai.md) deliverable.
- **Close** the backfeed within two weeks: review-checklist update, standards-as-code update, eval row, routing-matrix / HITL / tool-authorisation amendment, contract change-log entry. [Chapter 6](06-regression-fixture-backfeed.md) is the full discipline.
- **One runbook artifact** covers Steps 1–7 in 5–8 pages; [Exercise 01](exercises/exercise-01-team-incident-runbook-authoring.md) produces v0.1.
- **Composes with** [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) (standards and evals the backfeed closes into) and [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) (routing, HITL, tool-authorisation layers the backfeed amends).
