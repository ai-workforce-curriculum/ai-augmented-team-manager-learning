# Chapter 2 — The Ritual Calendar Under AI-Augmented Work

> *A ritual on the calendar is a claim that the team's measurement framework will be worse if the ritual stops. If the claim cannot be made in one sentence citing a specific dashboard tile, the ritual is drift. The quarterly ritual audit is where drift gets caught; the Lencioni meeting-type classification is how the audit stays honest about what each ritual is actually for.*

## Motivation

AI-augmented work changes the time-shape of a team's week in two directions at once. On one side, [NBER 31161](https://www.nber.org/papers/w31161) and [BCG / HBS *Jagged Frontier*](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321) show measurable throughput gains on tasks inside the AI frontier; the team's heads-down maker time is more productive per hour than it was pre-AI. On the other side, the number of coordination artifacts a modern team is expected to maintain — adoption roadmaps, review-standard audits, eval-set curation, governance crosswalks, data-and-IP matrix refreshes, tool-registry reviews, incident retrospectives — has roughly doubled in the two years since general-purpose code assistants became organisationally serious. The maker-time gains land straight into coordination debt unless the ritual calendar is actively managed.

The default behaviour under that pressure is to add rituals and never retire any. The AI-adoption roadmap gets a monthly review; the governance crosswalk gets a quarterly review; the tool registry gets a quarterly review; the eval set gets a monthly review; the incident backlog gets a biweekly review; the community-of-practice gets a weekly session; the manager's 1:1 stack grows with headcount; the planning / review / retro / demo canon inherited from the agile tradition is untouched — and, three quarters in, the team's calendar has fifteen weekly recurring meetings and a 40%-of-headcount coordination tax. The team ships less than it did before AI. The dashboard tiles the rituals are supposed to defend have no demonstrable improvement attributable to the rituals.

mod-112 refuses this pattern. Every ritual on the calendar must justify itself against the [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) measurement framework — a *specific* tile that gets worse if the ritual stops — and must have a classified *meeting type* per [Lencioni's *Death by Meeting*](https://www.tablegroup.com/product/death-by-meeting/) framing. Rituals that fail either test are retired or merged. The audit runs on a known cadence. The default state of the calendar is lean; new rituals are added deliberately, not accreted.

This chapter does four things. First, it names the full ritual inventory an AI-augmented team at L40 can plausibly run. Second, it introduces Lencioni's four meeting-type canon and the practical use of it. Third, it names the measurement-framework justification — every ritual connects back to a tile. Fourth, it gives the calendar-budget math — how much of a team's week a reasonable calendar consumes and when the budget is being overspent.

## Core concepts

### The ritual inventory

A reasonable inventory of rituals that an AI-augmented team might run, drawn from the prior eleven modules. Not every team runs every ritual; the point of the audit is to decide which are earning their slots.

**Delivery and flow:**

- **Planning / backlog refinement.** Cadence: sprint-shaped (biweekly) or continuous (weekly top-of-stack review). Purpose: shape upcoming work. Tile anchor: [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) DORA lead-time, flow efficiency ([`mod-104` Ch. 4](../mod-104-productivity-measurement-and-ai-roi/04-flow-metrics-and-kersten.md)).
- **Standup / daily async check-in.** Cadence: daily or daily-async. Purpose: unblock within-day. Tile anchor: flow blocker count, WIP.
- **Review / sprint demo / PR-level demo.** Cadence: biweekly or on-ship. Purpose: show working software to stakeholders. Tile anchor: product-outcome tile, demo-attendance rate as proxy for stakeholder alignment.
- **Retrospective.** Cadence: biweekly (sprint-shaped) or monthly (continuous). Purpose: inspect and amend the practice. Tile anchor: amendment land-rate, repeat-incident rate from [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/).

**People:**

- **1:1s.** Cadence: weekly or biweekly per direct report. Purpose: growth, performance, personal signal — not status reporting. Tile anchor: [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/) growth plan progress, [`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/) calibration input.
- **Peer / skip-level 1:1s.** Cadence: quarterly or by exception. Purpose: cross-team signal, calibration.

**Enablement and craft:**

- **Office hours.** Cadence: weekly or biweekly. Purpose: open coaching for AI-augmented workflow friction, review-standard questions, eval questions. Tile anchor: [`mod-105`](../mod-105-team-ai-enablement-programs/) stage-progression rate, [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) review-standard adoption.
- **Community of practice (CoP).** Cadence: biweekly or monthly. Purpose: cross-team pattern sharing, workflow show-and-tell, agent-authoring demos. Tile anchor: stage progression; novel-workflow adoption rate from [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/).
- **Review-standard calibration.** Cadence: monthly or quarterly. Purpose: keep [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) checklists live; reconcile reviewer disagreements. Tile anchor: review-time variance, review-rejection rate.

**Measurement and improvement:**

- **Dashboard review.** Cadence: weekly or biweekly. Purpose: look at the measurement framework together; catch drift, surface anomalies. Tile anchor: the dashboard itself ([`mod-104`](../mod-104-productivity-measurement-and-ai-roi/)).
- **Eval-set review.** Cadence: monthly. Purpose: curate [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) eval set; retire regressions; add new tasks. Tile anchor: eval-regression count, eval coverage.
- **Incident retrospective.** Cadence: per-incident (within 7 business days). Purpose: [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) blameless post-mortem. Tile anchor: incident count by class; regression-fixture-landing rate.
- **Governance retrospective.** Cadence: semiannual or event-triggered. Purpose: [`mod-110` Ch. 7](../mod-110-ai-governance-and-policy-at-team-scope/07-upward-evidence-packet-and-ownership-boundary.md) retro. Tile anchor: gap-register closure rate.
- **Vendor / tool-registry review.** Cadence: quarterly. Purpose: [`mod-111` Ch. 7](../mod-111-vendor-budget-and-tool-selection-at-team-scope/07-tool-registry-ongoing-evaluation-and-ownership-boundary.md) ongoing-evaluation ritual. Tile anchor: AI-cost tile, usage-per-seat, stage-aligned budget distribution.

**Cross-functional:**

- **Roadmap review with Product partner.** Cadence: biweekly or monthly. Purpose: shape upcoming work with the PM. Tile anchor: outcome tile; roadmap-vs-delivered variance.
- **Platform / DevEx sync.** Cadence: monthly or quarterly. Purpose: alignment on platform roadmap, DevEx investment, shared infrastructure. Tile anchor: DX Core 4 pattern, [`mod-104` Ch. 2](../mod-104-productivity-measurement-and-ai-roi/02-dx-core-4-and-space-anchors.md).
- **Design pattern review.** Cadence: as needed (triggered by design-system changes or new patterns). Purpose: alignment with Design partner on patterns used in team output.
- **Data / analytics sync.** Cadence: monthly or quarterly. Purpose: alignment on metric definitions, instrumentation, analytics roadmap. Tile anchor: metric-definition version coherence.
- **AI-Governance partner sync.** Cadence: quarterly or event-triggered. Purpose: alignment with the governance peer on the upward packet shape and gap register.

**Upward:**

- **Quarterly business review (QBR) / exec pre-read.** Cadence: quarterly. Purpose: [`mod-104` Ch. 7](../mod-104-productivity-measurement-and-ai-roi/07-the-ai-roi-narrative-for-leadership.md) + [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) + [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) rolled up for leadership. See Chapter 4 of this module.
- **Manager 1:1 with own manager.** Cadence: weekly or biweekly.

A real team's calendar is a *subset* of this inventory, with explicit retirements of items that do not pay rent.

### Lencioni's four meeting types

[Patrick Lencioni's *Death by Meeting* (Jossey-Bass, 2004)](https://www.tablegroup.com/product/death-by-meeting/) proposes that most organisational meetings fail because a single calendar slot tries to serve two or more incompatible purposes at once. Lencioni's answer is to classify meetings into four types with distinct purposes, cadences, and preparation discipline, and run them cleanly rather than merging them.

| Type | Purpose | Typical duration | Typical cadence |
|---|---|---|---|
| **Daily check-in** | Administrative alignment on the day's shape — no decisions, no discussion, just synchronisation | ~5 minutes | Daily |
| **Weekly tactical** | Operational issues of the current week — real-time agenda, resolution of tactical obstacles, status on near-term commitments | 45–90 minutes | Weekly |
| **Monthly strategic** | Deep work on one or two strategic topics — real deliberation, live decisions, policy-level questions | 2–4 hours | Monthly (or ad-hoc when the topic matures) |
| **Quarterly off-site review** | Reset — review the strategy, team health, culture, external environment; refresh the framework the other three types operate under | Half-day to two days | Quarterly |

The use of the framing at team scope is not prescriptive — a team does not need all four types. The use is as a *classifier*. Every ritual on the calendar is one of the four types; a ritual that is more than one is a sign the slot is overloaded and should be split.

**Common mis-classifications a team scope reveals:**

- *Weekly tactical pretending to be monthly strategic.* "We'll discuss the roadmap this week" — one weekly tactical in a quarter does not do the work of a monthly strategic session. The roadmap discussion needs its own slot or it does not happen.
- *Monthly strategic drifting into weekly tactical.* "We have a monthly team meeting" where the agenda is this week's blockers is a mis-classified weekly tactical. It either consumes strategic-deliberation time without strategic output or starves tactical resolution between months.
- *Standup as tactical.* The standup becomes 30 minutes of problem-solving. Problem-solving belongs to the weekly tactical or the sidebar it triggers. The daily check-in exists to synchronise, not resolve.
- *Retro as off-site review.* "We'll discuss the strategy at the retro" — the retrospective is an inspection-and-amendment ritual, not a strategy refresh. Strategy belongs to the quarterly off-site review.

A mod-112-literate manager tags every ritual on the calendar with one of the four types and retires rituals that cannot be cleanly classified.

### Every ritual justifies itself against a dashboard tile

The second discipline: every ritual must cite a specific [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) dashboard tile (or a named [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) incident-class tile, or a named [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) gap-register tile) that would plausibly get worse if the ritual stopped. The claim is written down in the ritual's description. The audit (Exercise 01) verifies the claim annually; rituals that have not plausibly moved their tile in a year are retired.

A workable template per ritual:

| Field | Example |
|---|---|
| **Ritual** | Eval-set review |
| **Cadence** | Monthly, Thursday 10:00, 60 minutes |
| **Lencioni type** | Monthly strategic |
| **Attendees** | Tech lead, review-standard owner, two rotating ICs |
| **Purpose (one sentence)** | Curate the eval set used by the review standard; retire regressions, add new tasks reflecting actual workflow |
| **Tile defended** | Eval-regression count (mod-104 Ch. 3) and review-rejection rate (mod-103 artifact) |
| **Signal-of-decay** | Three consecutive months with no amendments; consecutive quarters with no measurable movement in the defended tile |
| **Owner** | Review-standard owner |
| **Last audit** | 2026-09-15 (confirmed earning) |

Rituals without a defended tile are rituals without a measurable claim. Keeping them is a judgment call the manager can make, but the judgment is made in the open — on the calendar audit (Exercise 01), with the reasoning recorded — rather than by accretion.

### The calendar budget

The practical constraint. A ritual costs the time of the people in the room multiplied by the slot length, multiplied by the frequency.

A workable budget estimate for a nine-person team (one manager, eight ICs):

| Ritual | Per-session cost | Annual sessions | Annual cost |
|---|---|---|---|
| Standup (9 people × 10 min × 48 weeks × 4 days/week) | 1.5 person-hr | 192 | **~288 person-hr** |
| Sprint planning (9 × 60 min × 26 sprints) | 9 person-hr | 26 | **~234 person-hr** |
| Sprint review / demo (9 × 45 min × 26) | 6.75 person-hr | 26 | **~175 person-hr** |
| Retrospective (9 × 60 min × 26) | 9 person-hr | 26 | **~234 person-hr** |
| 1:1 (1 × 30 min × 8 reports × 48 weeks) | 0.5 person-hr | 384 | **~192 person-hr** |
| Dashboard review (5 × 30 min × 48 weeks) | 2.5 person-hr | 48 | **~120 person-hr** |
| Office hours (3 × 60 min × 48 weeks) | 3 person-hr | 48 | **~144 person-hr** |
| CoP (9 × 60 min × 24 biweekly) | 9 person-hr | 24 | **~216 person-hr** |
| Eval review (4 × 60 min × 12) | 4 person-hr | 12 | **~48 person-hr** |
| Tool registry review (5 × 2 hr × 4) | 10 person-hr | 4 | **~40 person-hr** |
| Governance retro (9 × 90 min × 2) | 13.5 person-hr | 2 | **~27 person-hr** |
| Incident retro (6 avg × 60 min × ~8/yr) | 6 person-hr | 8 | **~48 person-hr** |
| Cross-functional syncs (5 attendees × avg 60 min × ~24) | 5 person-hr | 24 | **~120 person-hr** |
| **Subtotal** | — | — | **~1,886 person-hr/yr** |

A nine-person team has roughly 9 × 2,000 = 18,000 person-hr/yr of working time. The ritual load above is **~10.5%** of total capacity. This is a *sustainable* number; teams with calendars at 15–20% of capacity in rituals have crossed into overspend. Teams at 25%+ are not so much AI-augmented as meeting-augmented.

Two caveats:

- The number *does not include* ad-hoc meetings, cross-team meetings, planning on top of the above, or deep-work interruption cost. Real coordination tax is higher than the ritual budget.
- The budget is not something to *minimise* to zero. Rituals are coordination capital; the team that cuts every meeting loses more in dropped balls than it gains in maker time. The *right* budget for a given team depends on the composition — distributed teams need more deliberate synchronous ritual than co-located ones; junior-heavy teams need more enablement ritual than senior ones; early-adoption teams need more roadmap-review ritual than teams in steady state.

The budget is there to make the trade-off visible. A manager adding a new ritual is spending capacity; the audit ensures the spend is deliberate.

### The audit cadence

Running the audit once in a lifetime is not enough; the ritual landscape drifts. A reasonable cadence:

- **Annual full audit.** Once per year (Exercise 01). Every ritual gets the template filled, the tile defended, the Lencioni classification confirmed, the retirement decision made.
- **Quarterly spot audit.** At the quarterly review (Lencioni's fourth type), look at the three rituals most changed, added, or shifted since last quarter. Confirm or amend.
- **Event-triggered audit.** Headcount change of ±2, major scope change (new product line or sunset), significant process incident (a decision missed because a ritual did not surface it).

Audits produce decisions that are recorded in the decision log (Chapter 5). "Retired the Wednesday standup on 2026-10-14; reason: dashboard shows blockers resolving async faster than in-ritual; will revisit if blocker-count tile exceeds threshold X" is a decision-log entry. "We don't do standups anymore" is not; a successor reads the second and does not know what to do with it.

## Example: a calendar audit that retires a ritual

Composite — calibration, not a case study.

An eight-person engineering team on a SaaS product has run a weekly 60-minute "AI tools sync" for nine months. The ritual was added in Q1 after [`mod-105`](../mod-105-team-ai-enablement-programs/) adoption; at the time, the team was in Chapter 2 / 3 of the enablement journey and the sync was carrying real content — tool demos, workflow refinements, review-standard adjustments as the team learned what AI pairing did to PR patterns.

By Q3 the team is mostly at Stage 3 / 4 of the enablement ladder. The sync's content has thinned. The last four sessions have been: a tool demo from the vendor's release notes, a repeat of a demo from six months ago, a general-chat session, and a cancelled meeting. The manager runs the Q4 audit.

The template for the AI tools sync:

| Field | Value |
|---|---|
| **Ritual** | AI tools sync |
| **Cadence** | Weekly, Wednesday 11:00, 60 minutes |
| **Lencioni type** | Attempted monthly strategic, running as weekly tactical |
| **Attendees** | Whole team, 8 people |
| **Purpose** | Cross-pollinate AI-augmented workflow learning |
| **Tile defended** | Novel-workflow adoption rate (mod-106 artifact), stage progression (mod-105) |
| **Signal-of-decay** | Four consecutive weeks of weak content; stage distribution stable for two quarters |
| **Annual cost** | 8 × 1 hr × 48 = **384 person-hr/yr** |

The audit decision:

> "The sync earned its slot in Q1–Q2 while the team was moving through enablement stages. In Q3 the stage distribution stabilised; the content thinned to repeats and demos; the defended tile is not moving. Retiring the weekly recurring slot. Replacing with a monthly 45-minute CoP session owned by the enablement champ, with explicit purpose: one novel-workflow demo per session, rotating owner. Expected annual cost reduction: ~288 person-hr. If stage-progression tile regresses or novel-workflow adoption drops in Q1 next year, revisit with potential bi-weekly cadence."

Note what the decision does:

- It is *dated* and *explicit about the reasoning*. A successor reading this in six months knows exactly why the ritual changed.
- It names the *reversal condition*. If the signal the ritual defended comes back, the ritual comes back. Not forever retired; appropriately retired for the current state of the team.
- It names the *replacement*. Not "we won't do this anymore"; "we'll do a leaner version". Rituals rarely retire outright at team scope; they usually right-size.
- It *measures the cost saved*. The cost savings go on the operating-system scorecard — the team now has ~288 person-hr/yr for other work.

The audit decision lands in the decision log. The replacement CoP is added to the calendar with its own template filled. The next quarterly spot audit checks that the replacement is holding up.

## Summary

- The ritual calendar is a **budget**. Every ritual costs the team's time; the budget is visible; new rituals are deliberate spends, not accretion.
- Every ritual must be one of [Lencioni's four types](https://www.tablegroup.com/product/death-by-meeting/) — **daily check-in, weekly tactical, monthly strategic, quarterly off-site review** — cleanly. Overloaded slots that serve two incompatible purposes get split or retired.
- Every ritual must **defend a specific dashboard tile** from [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/), [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/), or [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/). Rituals without a defended tile are rituals without a measurable claim; keep them only with eyes open.
- A **reasonable ritual budget** for a nine-person team is ~10% of annual capacity — the arithmetic is on the page; teams at 15–20% are overspent; teams at 25%+ are meeting-augmented, not AI-augmented.
- The audit runs **annually in full (Exercise 01)**, **quarterly in spot form**, **event-triggered on material change**. Audit decisions land in the decision log (Chapter 5) with dated rationale and reversal conditions.
- Retirement is usually **right-sizing**, not elimination: the quarterly AI tools sync that was weekly in Q1 is a normal shape change, not a failure of the ritual.
