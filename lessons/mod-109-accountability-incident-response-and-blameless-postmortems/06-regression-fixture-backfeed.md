# Chapter 6 — The Regression-Fixture Backfeed

> *A post-mortem that does not close the loop is an expensive essay. The ritual in this chapter is the part of incident response that most teams get wrong — not because the ritual is complicated, but because the ritual is not scheduled. An incident ends, the write-up is filed, the team moves on, and nothing structurally changes. Six weeks later the same incident class lands. Chapter 6 is the small weekly discipline that prevents the same incident twice.*

## Motivation

[`mod-103` Chapter 5](../mod-103-review-standards-and-eval-commissioning/05-the-accountability-contract-ai-generates-humans-own.md) names the commitment: *"we close the loop into the review checklist, the standards-as-code stack, and the commissioning backlog within two weeks."* [Chapter 2](02-operating-the-accountability-contract-end-to-end.md) of this module names Step 7 (Close) and lists the backfeed artifacts. [Chapter 3](03-blameless-postmortems-adapted-for-ai.md) specifies the five systemic questions whose answers become action items. All of that infrastructure exists so that the backfeed *happens*. The chapter you are reading is the practice that makes it happen.

The backfeed is where incident response earns the team its compounding return. A well-run post-mortem produces 3–6 action items; without a discipline for landing them, roughly half will not land within the two-week commitment. Over a year the team's standards drift sideways while incidents repeat. With a discipline for landing them, the opposite compound happens — the team's standards stack tightens on each real failure mode, the commissioned eval set grows a row per confirmed class, and the next incident of a given shape is caught by the eval before it ships.

Three operational pieces make the practice work:

- **The backfeed ticket shape.** Not a free-text note; a specific ticket with owner, destination (mod-103 artifact or mod-106 artifact), close-out criterion, and date.
- **The regression-fixture discipline.** Every confirmed incident produces at least one landed eval row. This is the single highest-leverage output; a team that does nothing else but this will catch 60–80% of recurrences by eval alone over 18 months.
- **The weekly ritual.** 20 minutes on a standing cadence that walks every open backfeed ticket to completion. Without the ritual the tickets accumulate.

The chapter is the discipline. Exercise 05 is the ritual applied to a worked case.

## Core concepts

### The backfeed ticket as an artifact

A backfeed ticket is not a Jira "action item" row with free-text. It has a specific shape:

| Field | Content |
|---|---|
| **Title** | Short — "add eval row: idempotency-TTL mutation" / "update AGENTS.md: staleness detection on retrieval" |
| **Source incident** | Link to the incident ticket and the post-mortem write-up |
| **Destination artifact** | Which specific mod-103 / mod-106 artifact gets updated — e.g., `/docs/ai-review-checklist.md`, `/.cursor/rules/20-security.mdc`, `evals/golden-tasks.jsonl`, `/docs/routing-matrix.md` |
| **Owner** | One person (not a team, not a role, a person) |
| **Close-out criterion** | What has to be true for the ticket to close — "PR merged with the new row, eval run showing new row covers the regression" |
| **Date** | Two weeks from the post-mortem by default; longer only with a stated reason |

The specificity matters. "Update the review checklist" is not actionable; "add row 14 to `/docs/ai-review-checklist.md` requiring diff-vs-prior snapshot for AI-authored pipeline changes" is. The post-mortem's Section 7 should produce tickets in this shape, not free-text. [Exercise 02](exercises/exercise-02-blameless-postmortem-adapted-for-ai.md) is where the post-mortem template is tuned to produce tickets of this shape.

### The eval row — the highest-leverage output

Of the backfeed destinations in Chapter 2's Step 7, the **commissioned eval row** is the highest-leverage. Reasons:

- **An eval row catches the regression next time, automatically.** Standards and checklists catch regressions only when a human reviewer is present and remembers; an eval catches regressions on every CI run, every nightly cadence, every pre-release gate.
- **An eval row is a durable testbed for vendor changes.** When a model version changes under the team (Class 4), the eval row is the first signal; without it, the team learns about the change from a user.
- **An eval row is portable.** A row authored for one workflow is often adaptable to related workflows. A checklist entry is not portable in the same way.

The eval-row discipline:

- **Every confirmed incident produces at least one eval row** unless there is a specific reason (the post-mortem names it) that no eval row is possible. "No eval row possible" is rare; it usually means the behaviour is not reproducible or requires human judgement at a scale the eval can't cover.
- **The eval row is authored by the engineered-risk peer when the method requires it** (Chapter 5). Golden tasks and mutation tests are often team-authorable; LLM-as-judge rubrics and adversarial tests typically route through the risk engineer.
- **The eval row lands with a *demonstrated regression* in CI.** That is: the row first reproduces the incident's failure (red), the fix is validated (green), and the row goes into the regression gate. A row that passes on initial run has not demonstrated what it is for.
- **The eval row has a retention policy.** A row authored on an incident that is superseded by a structural change (the whole workflow is removed) is retired, not left to rot. The post-mortem's annual review (Chapter 7) covers retirement.

The eval row's destination is the commissioning backlog authored in [`mod-103` Chapter 4](../mod-103-review-standards-and-eval-commissioning/04-commissioning-eval-frameworks-at-team-scope.md). The manager commissions; the `ai-risk-engineer` or the team's eval-engineer authors; the row lands in the team's eval repository (whatever tooling the team uses — `promptfoo`, `LangSmith` datasets, `Inspect AI` suites, bespoke).

### The routing-matrix amendment

The second-highest-leverage backfeed destination is the routing-matrix amendment in [`mod-106` Chapter 2](../mod-106-workflow-redesign-and-agent-delegation/02-the-task-routing-decision.md). When an incident surfaces that a workflow was routed to AI-first when it should have been paired-review, or that a workflow was authored as paired-review when the HITL checkpoints were insufficient, the matrix is amended.

The matrix amendment is more powerful than an eval row when the root cause is *the AI should not have been doing this workflow in this way*. An eval row makes the AI do the workflow more carefully; a matrix amendment moves the workflow to a different destination.

Both are typically needed on the same incident; they are not alternatives. The eval catches the specific case; the matrix amendment prevents similar cases structurally.

### The HITL-checkpoint and tool-authorisation amendments

Two mod-106 Chapter 4 and Chapter 6 destinations. These are specific, often small, high-leverage changes:

- **HITL checkpoint added.** A new checkpoint in a workflow, before an action that the incident showed should have been gated.
- **HITL checkpoint escalated.** An existing checkpoint that was configured lightweight (automated check only) is upgraded to require a human reviewer.
- **Tool authorisation tightened.** A tool that was authorised unattended is now gated; a tool authorisation is narrowed in scope; a tool is removed from the authorisation set entirely.

These are often where Class 2 and Class 3 incident backfeeds land. The amendments are usually one-line changes to a configuration file or a policy document; what makes them durable is that the ticket exists and the change was *landed*, not merely discussed.

### The standards-as-code amendment

The third mod-103 destination: the standards-as-code stack from [Chapter 3](../mod-103-review-standards-and-eval-commissioning/03-standards-as-code-for-human-and-agent-authors.md). A new Cursor rule, an AGENTS.md section, a lint policy, an ADR. These amendments are author-time catches: the agent is prevented from authoring the failure mode in the first place.

Standards-as-code amendments are powerful because they shift-left — the problem is caught before review, not at review — but they are *specific* catches, not general ones. A rule file is a list of concrete behaviours to prevent; it does not substitute for the review checklist's broader judgement.

### The review-checklist amendment

The pre-code catch. A new row in the team's review checklist from [`mod-103` Chapter 2](../mod-103-review-standards-and-eval-commissioning/02-the-ai-work-review-checklist.md) that names what the reviewer must look at on this class of artifact. Lower-leverage than an eval row (depends on human attention) but necessary when the catch requires judgement the eval cannot encode.

### The accountability-contract change-log entry

The last destination. The accountability contract from [`mod-103` Chapter 5](../mod-103-review-standards-and-eval-commissioning/05-the-accountability-contract-ai-generates-humans-own.md) has a change-log; every incident produces a one-line entry naming what tightened. The contract itself is amended when:

- The C1 scope (what AI may draft) changes — a class of work is removed from AI-first or added.
- The C2 verification bar changes — the review checklist's load-bearing commitment is updated.
- The C4 process changes — a step is added, a trigger line moves (per [Chapter 5](05-routing-contract-with-risk-engineer-and-secops.md) of this module).

Most incidents produce a change-log entry rather than a contract amendment. The entry is the audit trail.

### The weekly backfeed ritual

The ritual is small enough to survive a quarter. 20 minutes, weekly, at a fixed time (not "when we have time," because that time does not arrive). A workable agenda:

| Minute | Activity |
|---|---|
| 0–5 | Open-ticket review. Each open backfeed ticket: *is it on track? Blocker? New blocker since last week?* |
| 5–15 | Close-out verification. For each ticket claimed "done" in the week: *is the destination artifact actually updated? Did the eval row demonstrate red-to-green? Is the change-log entry present?* |
| 15–18 | New tickets from the week's incidents (if any) opened and routed. |
| 18–20 | Blockers escalated. Tickets stuck > 2 weeks escalated to the manager's calendar for follow-through. |

The ritual is run by the manager or a delegated senior IC on the team. It is *not* run by the `ai-risk-engineer` or SecOps peers; they are informed of outcomes but do not own the ritual.

The output of the ritual is a running dashboard: how many tickets open, how many closed in the week, how many > 2 weeks old. A team that closes within SLA most weeks has a healthy backfeed; a team with a growing > 2-week backlog has a priority or capacity problem the manager has to fix.

The ritual lands on the [`mod-112`](../mod-112-cross-functional-leadership-and-ritual-calendar/) ritual calendar.

### What makes a ticket stall

A specific list, because the manager will have to debug stalled tickets:

- **The owner is a team, not a person.** Teams do not own tickets; people do. Re-assign.
- **The close-out criterion is vague.** "The checklist is updated" is vague; "PR merged with row 14 added" is specific. Re-specify.
- **The owner lacks capacity.** Managerial problem. Either re-route to a different owner or reduce the owner's other load. Do not leave the ticket on the owner as a slow regret.
- **The owner lacks authority.** An eval-row ticket owned by an IC when the risk engineer has to author — wrong routing. Re-route.
- **The destination artifact does not exist.** The team is trying to update a `/docs/ai-review-checklist.md` that was never created. The post-mortem assumed artifacts the team does not have. Create the artifact or re-shape the ticket.
- **The ticket is actually two tickets.** "Add eval row *and* update AGENTS.md" is two tickets with two owners. Split.

### Common failure modes

- **Post-mortem write-up filed without tickets.** The action items are prose, not tickets. Fix: the post-mortem template requires tickets in the backfeed shape.
- **Tickets opened in a different tracker than the team uses day-to-day.** They disappear into an incident-specific tool nobody opens. Fix: backfeed tickets live in the team's normal tracker, not in the incident tool.
- **No eval row.** Every single incident produces a standards-only change. Over a year the eval set does not grow. Fix: the ritual's close-out verification specifically checks for an eval row.
- **The ritual runs for a quarter and then is dropped.** Classic failure mode. Fix: the ritual is on the calendar as a recurring 20-minute slot with the manager as owner; dropping it requires a manager decision to drop it.
- **The ritual becomes a status meeting.** Scope creep. Fix: 20 minutes, fixed agenda, hard end.
- **Action items are over-written across incidents.** The same checklist row is updated by three different incidents and the resulting row is incoherent. Fix: the close-out verification includes "does the row still make sense after this change?" The post-mortem co-author (often the manager) owns coherence.
- **Eval rows rot.** Rows authored for workflows that no longer exist stay in the regression gate, waste compute, and produce noise. Fix: annual review (Chapter 7) retires obsolete rows.

### The incident-to-eval metric

A simple metric worth tracking:

> **% of confirmed incidents in the last two quarters that produced a landed eval row.**

Target: 100%. A team below 80% is leaking regression coverage; the ritual is not working. A team above 100% (incidents producing multiple eval rows) is fine. The metric is not for leadership comms; it is for the manager's own calibration on whether the ritual is working.

### How the backfeed composes with mod-110 and mod-111

- **To [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/).** The accountability-contract change-log, the post-mortem write-up, and the routing-contract updates all compose into the NIST AI RMF MANAGE 2 and MANAGE 4 evidence base. Where the team participates in an organisation-wide governance program, the post-mortem is the primary evidence artifact.
- **To [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/).** Class 4 incidents produce vendor-governance tickets. The vendor's SLA, notification obligations, and model-deprecation policy all route through mod-111's vendor framework. A pattern of Class 4 incidents across vendors feeds into vendor re-selection.

The manager does not have to author the mod-110 or mod-111 artifacts from scratch during the backfeed. The post-mortem and the backfeed tickets are the input; the governance and vendor artifacts consume them.

## Example: the backfeed ritual over one quarter

Composite illustrative sketch; calibration, not a case study. Walks a hypothetical team's backfeed state over a quarter.

**Week 1.** Incident A from Chapter 2's example (wrong number via AI-authored pipeline change). Post-mortem Thursday. Three tickets opened Friday:

- *Ticket A1*: Add eval row — mutation test on column aggregation. Owner: risk engineer. Due: week 3.
- *Ticket A2*: Review-checklist row 14 — AI-authored pipeline changes include diff-vs-prior snapshot. Owner: team manager. Due: week 2.
- *Ticket A3*: Staleness-signal on retrieval configuration. Owner: senior IC on the pipeline team. Due: week 4.

**Week 2 ritual.** A2 closed (checklist PR merged Thursday). A1 and A3 on track. No new incidents.

**Week 3 ritual.** A1 closed (eval row red-to-green demonstrated, merged). A3 slipping — owner on leave. Re-routed to a different senior IC, due extended to week 5. Incident B (Class 2 prompt injection near-miss on a README) occurs mid-week. Post-mortem next Thursday. Two tickets opened Friday:

- *Ticket B1*: Input sanitisation on README ingestion. Owner: eval-engineer. Due: week 6.
- *Ticket B2*: HITL checkpoint on shell tool calls originating from external content. Owner: team manager. Due: week 5.

**Week 4 ritual.** A3 and B2 on track. B1 in flight.

**Week 5 ritual.** A3 closed. B2 closed. Incident C (Class 4 model regression) occurs end of week. Risk engineer engaged; eval dashboard caught it; post-mortem the following Thursday produces:

- *Ticket C1*: Version-pin the affected model in team's inference configuration. Owner: senior IC. Due: week 7.
- *Ticket C2*: Vendor-governance ticket to mod-111 escalation — notification SLA failure. Owner: team manager, routed to vendor-management. Due: week 9.
- *Ticket C3*: Canary eval row for the regression class. Owner: risk engineer. Due: week 7.

**Weeks 6–9.** Tickets close on schedule. B1 closes week 6. C1 and C3 close week 7. C2 closes week 9 after the vendor-management conversation.

**End-of-quarter review.** 8 tickets opened, 8 closed, 0 open past SLA. Incident-to-eval metric: 3/3 (every confirmed incident produced at least one eval row). Standards stack has grown by three rows (two checklist, one Cursor rule); the routing matrix has not amended (the incidents did not shift the AI/human/junior routing calls); the HITL set has grown by one checkpoint; one tool authorisation has tightened; the eval set has grown by three rows (two golden-task mutation, one canary).

Three incidents, two durable preventive measures per incident, no heroics. The team's standards stack tightened in six places during the quarter; the next quarter's incidents will test what tightened.

## Summary

- The backfeed is where incident response earns its compounding return. Without a landing discipline, roughly half of post-mortem action items do not land within the two-week commitment; with the discipline, standards and evals tighten with each real failure mode.
- **The backfeed ticket shape is specific:** title, source incident, destination artifact (specific file or doc), named owner (a person), close-out criterion, date. Not a free-text action item.
- **The eval row is the highest-leverage output.** Every confirmed incident produces at least one, demonstrated red-to-green in CI. The commissioning route is [`mod-103` Chapter 4](../mod-103-review-standards-and-eval-commissioning/04-commissioning-eval-frameworks-at-team-scope.md); the method owner is typically the [`ai-risk-engineer`](https://github.com/ai-governance-curriculum/ai-risk-engineer-learning).
- **Other backfeed destinations:** routing-matrix amendment (mod-106 Chapter 2), HITL-checkpoint amendment (mod-106 Chapter 4), tool-authorisation amendment (mod-106 Chapter 6), standards-as-code amendment (mod-103 Chapter 3), review-checklist amendment (mod-103 Chapter 2), accountability-contract change-log entry (mod-103 Chapter 5).
- **The weekly 20-minute ritual** — open-ticket review, close-out verification, new tickets, blockers escalated — is the discipline that makes the backfeed survive the quarter. Lands on the [`mod-112`](../mod-112-cross-functional-leadership-and-ritual-calendar/) ritual calendar.
- **Stalled tickets debug consistently:** owner is a team not a person; close-out criterion vague; owner lacks capacity or authority; destination artifact doesn't exist; two tickets collapsed into one.
- **The incident-to-eval metric** (% of confirmed incidents in the last two quarters that produced a landed eval row) is the manager's calibration — target 100%.
- **Common failure modes:** post-mortem filed without tickets; tickets in the wrong tracker; no eval row; ritual drops after a quarter; ritual becomes a status meeting; action items over-write incoherently; eval rows rot.
- **Composes with** [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) (standards, standards-as-code, evals, contract — the backfeed destinations), [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) (routing / HITL / tool-authorisation — the backfeed destinations), [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) ([NIST AI RMF](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf) MANAGE evidence), [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) (vendor governance tickets from Class 4), and [`mod-112`](../mod-112-cross-functional-leadership-and-ritual-calendar/) (ritual calendar).
- [Exercise 05](exercises/exercise-05-regression-fixture-backfeed-ritual.md) is the ritual designed and run against a worked case.
