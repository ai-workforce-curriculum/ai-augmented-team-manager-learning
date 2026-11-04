# Chapter 7 — The Post-Automation Attention Shift

> *The first-order win of a good routing matrix is that the routine slice gets automated. The second-order risk is that the humans you freed up drift back into the routine slice because it still looks like work. Where their highest-value attention actually goes is a managerial design decision, not a bystander effect.*

## Motivation

[Dell'Acqua et al., *Navigating the Jagged Technological Frontier*](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321) returned to the analysis a year later with a follow-up finding that is specifically a managerial problem. In the inside-the-frontier condition, consultants did not just finish the tasks AI helped with faster — they *redirected* their freed capacity to tasks AI could not do well, and were *distinctively better* at those outside-frontier tasks than the control group. The AI did not just raise throughput on the inside-frontier work; it *reshaped the distribution of human effort* across the whole task portfolio.

That reshaping did not happen automatically in every participant. The study's narrative — and the broader workforce-transformation research that has followed, including [Microsoft's *Work Trend Index*](https://www.microsoft.com/en-us/worklab/work-trend-index) reporting on how time is reallocated after AI adoption — makes the pattern clear: the *attention shift* is an outcome of deliberate choice, not a passive consequence of automation. Workers (and managers) who do not actively redirect the freed capacity find it drifts: back into the now-automated work (because the AI's output still needs the kind of micro-supervision that resembles doing it); into longer meetings that compensate for the trust ambiguity of AI-produced artifacts; into Slack conversations about the AI itself.

This chapter is the design response. Once the routing matrix (Chapter 2) and the delegation ladder (Chapter 3) have moved the routine slice onto the agent, *where the freed human attention goes* is the artifact the manager owns. Exercise 05 produces the one-pager.

## Core concepts

### What "attention" actually means at team scope

The managerial vocabulary of *attention* is more precise than *time saved*. Three distinctions.

- **Clock time vs. cognitive attention.** AI assistance on an inside-frontier task does not just reduce clock time; it reduces the *cognitive load* of producing the artifact, which frees a different (and often more valuable) resource than wall-clock hours. An engineer who used to spend 40 minutes drafting a PR description now spends 5 and still has the cognitive budget for the architectural-decision conversation at 2pm that the 40-minute drafting session would have depleted. Recovering clock time is nice; recovering cognitive bandwidth for judgment-heavy work is the lever.
- **Freed attention vs. drifted attention.** Freed attention is what the manager measures and redirects. Drifted attention is what happens to the freed capacity when no one redirects it. If the measurement work in [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) only tracks clock time saved, the drift will be invisible — hours look recovered, and the fact that the hours went into longer standups or re-reviews of AI output will not surface until the next productivity-measurement cycle.
- **Individual attention vs. team-portfolio attention.** A manager designing the attention shift does so at team-portfolio scope, not per-engineer scope. The question is not *"what is this engineer now free to do?"* — that is a personal-career-planning question handled in [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/). The question is *"what shape of work does the team's freed capacity now go into?"* The answer is a managerial design.

### Where high-value team attention can go

Six destinations the research and the posting evidence both surface. Not all apply to every team; pick deliberately.

**Destination 1 — Outside-frontier work on the team's existing portfolio.** The Dell'Acqua et al. second-order finding at its most direct: the team spends more of its freed capacity on the tasks AI cannot do well. For an engineering team: architectural decisions with multi-quarter blast radius; cross-team coordination work; production-incident root-cause analysis; the design-document quality bar. These are the tasks where the team's seniority produces disproportionate value and where AI is weakest.

**Destination 2 — The craft of noticing when the AI is subtly wrong.** The AI-era IC skill — read an AI-generated artifact and spot the subtle wrong thing — is itself a craft that compounds with practice. Routing team attention here deliberately (through the Kind 3 review process, through the quarterly ladder review, through postmortem-era training) produces a team that gets measurably better at *catching* the outside-frontier errors AI produces. This is also the specific craft that [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/) treats as the anti-atrophy anchor.

**Destination 3 — Cross-functional relationships.** Attention freed from drafting goes into the kind of work engineering teams historically underweight: the hour-long conversation with the PM to understand what the product actually needs; the slow consultation with legal about the compliance implication; the architectural walkthrough with another team. These are cognitively expensive to initiate and therefore the first things to atrophy when individual contributors are over-loaded; they are the first to recover when load reduces.

**Destination 4 — Learning compounding.** Freed attention pointed at skill-growth produces a team whose fluency compounds. [`mod-105`](../mod-105-team-ai-enablement-programs/)'s enablement programme is the operational home; Chapter 7 here is the explicit statement that *attention for learning* is a legitimate destination for freed capacity, not a nice-to-have. A disciplined team schedules it in the quarter, not in the margins.

**Destination 5 — New product or platform surface.** At some teams the freed capacity is best pointed at *new work* — a new service, a new internal tool, a new product feature the backlog has been deferring. This destination is the easiest to argue to leadership and the easiest to over-weight. The failure case is routing *all* freed capacity here, which collapses Destinations 1 and 2 (no one is reviewing the AI output or deepening the craft) and produces a team that ships more features of declining quality.

**Destination 6 — Managerial and organisational work the team had been under-doing.** Senior engineers taking on more mentorship. The team contributing to the tooling platform instead of consuming it silently. The team writing the design-pattern library that nobody has had the time to author. The team participating in cross-team architectural review. These are the *organisation-building* activities that sustain a team's trajectory beyond any single quarter's throughput.

Across the six, the consistent shape is: **higher-judgment, higher-context, more-ambiguous work**. The managerial design question is *which specific destinations fit this team's ambitions and portfolio right now*, in what rough proportion, with what visible evidence.

### The two anti-destinations

Equally important to name.

**Anti-destination 1 — Drift back into the automated work.** The agent produces a draft; the engineer who used to write the draft spends the same 40 minutes "polishing" it, chasing the AI through revisions, re-prompting, re-reading. Net clock time: same. Net cognitive attention on the outside-frontier work: zero. This is the most common anti-destination and the hardest to see because it looks like engineering care.

Counter-measure: the Kind 3 review checklist (Chapter 4) and the review standard ([`mod-103`](../mod-103-review-standards-and-eval-commissioning/)) should be *time-bounded*. A review that takes 10 minutes because the checklist is 10 items is correct; a review that takes 45 minutes because the engineer is also re-doing the drafting is a leak. The manager's role is to name the leak when it appears.

**Anti-destination 2 — Longer meetings to compensate for trust ambiguity.** AI-produced artifacts introduce a new ambiguity for the team: *"I don't fully trust this draft; let's have a meeting to go over it."* In the first six months this is reasonable; sustained, it is the equivalent of a trust-tax that negates the time-saving. Compensating meetings expand to fill the vacated calendar and produce the appearance of work.

Counter-measure: the quarterly measurement review ([`mod-104`](../mod-104-productivity-measurement-and-ai-roi/)) reads *meeting time trend* alongside clock-time saved. A rising meeting trend is a signal that the trust mechanism (the review standard, the HITL set, the delegation ladder) is not strong enough, and the team is compensating with synchronous conversation. Fix the mechanism; retire the compensating meeting.

### The attention-redirection plan as an artifact

Exercise 05 produces a one-page document. Its four fields.

- **Freed capacity, estimated.** From the routing matrix: the task types now routed to AI (unattended or paired), and the rough team-hours per week that frees. Use [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) vocabulary; a precise estimate is not the goal, an honest one is.
- **Destinations, ranked.** Which of the six destinations get the freed capacity, in rough proportion, with a named reason per destination. *"30% to Destination 2 (noticing-AI-errors craft) because our mod-103 review-standard quality signal has plateaued and the next quality step needs more AI-review practice; 40% to Destination 1 (outside-frontier work) because the Q2 roadmap has three architectural decisions deferred from Q1; 20% to Destination 4 (learning); 10% to Destination 6 (team pattern-library authoring)."*
- **Visible evidence.** How the team will know the redirection worked. *"Two of the three deferred architectural decisions are closed with written ADRs by end of Q2; the mod-103 review-standard aggregate quality signal improves by X; the pattern-library has three new entries by end of Q2."* Not vanity metrics; concrete artifacts produced.
- **Anti-destination monitoring.** How the team will spot the two anti-destinations. *"Monthly check of average Kind 3 review time (target: ≤12 minutes median); quarterly trend on team meeting hours."* The signal and the response are named explicitly.

A redirection plan without visible evidence or anti-destination monitoring is a wish, not a plan.

### How the plan composes with mod-104 and mod-107

The plan sits between two neighbouring modules.

- **With [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) (productivity measurement):** mod-104 produces the quarterly ROI narrative. The attention-redirection plan is *inside* that narrative: *"freed capacity went to destinations X, Y, Z; the evidence is A, B, C."* Without the redirection plan, the mod-104 narrative reduces to "we saved N hours" and leaves the second-order question unanswered. Pair the two.
- **With [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/) (skill growth):** Destinations 2 and 4 are mod-107 territory from the individual-engineer side; Chapter 7 here is the team-portfolio side. If an engineer's individual growth plan says *"I want to deepen my architectural-decision craft,"* the team-portfolio redirection plan should name the specific decision that engineer will own this quarter. The two artifacts cite each other.

### The attention shift at the manager's own altitude

Final note. The attention shift applies to the manager too. If the mod-106 routing matrix moves drafting the weekly team report to AI-paired, the manager's freed 90 minutes a week has to go somewhere. The default is *a longer meeting* or *another report*; the deliberate choice is cross-team architectural review, one more 1:1, an actual walk-the-floor hour, or the next module's work.

A manager who has authored a team-scope redirection plan but has no personal attention plan is modelling exactly the drift Chapter 7 is about. The redirection plan should name *the manager's own destination* in one line.

## Example: a two-paragraph attention redirection plan sketch

For the platform team example from Chapter 2.

> **Freed capacity.** The v0.1 routing matrix (Exercise 01) moves five recurring task types to AI-paired or AI-unattended: on-call handoff summary (Level 6, ~3 hours/week freed), weekly VP status (Level 3, ~1 hour), initial PR-review draft on single-file bug-fixes (Level 3, ~2 hours), routine postmortem timeline drafting (Level 3, ~1 hour), weekly service-dashboard commentary (Level 5, ~1 hour). Total estimated: ~8 team-hours/week, uneven across engineers. Senior ICs see the largest reduction; juniors see the smallest.
>
> **Redirection.** 40% (≈3 hrs/week) to Destination 1 (outside-frontier): the Q2 storage-choice ADR (staff engineer owns), the cross-team data-contract alignment work (two senior ICs), the renewed incident-root-cause practice (open on the ladder). 25% (≈2 hrs) to Destination 2 (noticing-AI-errors craft): the Kind 4 monthly audits of AI-unattended work are rotated and run as mentoring sessions — staff engineer walks a mid-level engineer through the audit, naming what to look for. 20% (≈1.5 hrs) to Destination 4 (learning): the team's AGENTS.md change reviews and quarterly ladder review become shared learning events, not manager-only. 10% (≈1 hr) to Destination 6 (team pattern-library): each senior IC contributes one pattern per quarter. 5% (≈0.5 hrs) to the manager's own redirection: one additional 1:1 on a rotation with a staff engineer across teams who the manager has been under-invested in. Evidence: Q2 close finds two ADRs filed, four audits completed with mentoring, three pattern-library entries, no sustained rise in Kind 3 review median above 12 minutes. Anti-destination monitors: Kind 3 review-time median tracked monthly; team meeting hours trend tracked quarterly and surfaced in the mod-104 narrative.

Two paragraphs, named destinations, specific evidence, anti-destination monitoring, one line on the manager's own shift. This is the shape Exercise 05 produces.

## Summary

- Dell'Acqua et al.'s **second-order finding**: AI-augmented workers do not just finish inside-frontier tasks faster; they redirect capacity to outside-frontier work and perform better there than the control group. The redirect is a design decision, not an automatic effect.
- *Attention* is more precise than *time saved*: distinguish **clock time vs. cognitive attention**, **freed vs. drifted attention**, **individual vs. team-portfolio attention**.
- **Six destinations** for freed team attention: outside-frontier portfolio work; noticing-AI-errors craft; cross-functional relationships; learning compounding; new product/platform surface; organisational work the team had been under-doing. All share the shape *higher-judgment, higher-context, more-ambiguous*.
- **Two anti-destinations** to name explicitly: **drift back into the automated work** (looks like engineering care); **longer compensating meetings** (looks like collaboration).
- The **attention-redirection plan** is a one-page artifact with four fields: freed capacity estimate; destinations ranked with reasons; visible evidence; anti-destination monitoring.
- The plan composes with [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) (as a slice of the ROI narrative) and with [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/) (as the team-portfolio counterpart to individual skill growth).
- The **manager's own redirection** is named in the plan too. A manager with a team plan and no personal plan is modelling the drift the plan is supposed to prevent.
- Exercise 05 produces v0.1 of the plan for your team.
