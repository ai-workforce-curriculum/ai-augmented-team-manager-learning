# Chapter 1 — Team-Scope AI Enablement Is a Manager Artifact, Not an L&D Deliverable

> *If your plan for "AI enablement" is "we booked a vendor for a one-day Copilot workshop in March," you are outsourcing the curriculum to someone who does not understand your team's work. The workshop may run. The fluency will not land.*

## Motivation

R5 of the posting sample that seeded this track (see [`JOB_REQUIREMENTS.md`](../../JOB_REQUIREMENTS.md)) names *"design and run team-level AI enablement programs — Day 0 / 30 / 60 / 90, bootcamps, workshops, communities of practice, tool-budget distribution, fluency measurement"* as a distinct manager requirement. Posting frequency **0.36** (4 in-window postings in the 25-posting sample; the remainder is live-but-undated ATS language treated as corroborating). Verbatim phrasings include *"run team AI bootcamps,"* *"stand up and run a community of practice,"* *"distribute tool licences by learning stage,"* *"author the 30/60/90 fluency plan,"* and *"own fluency growth artifacts for the team."*

R5 is lower-frequency than R1 (team adoption, 0.76) or R2 (review standards, 0.60) because the market is still in the early phase of codifying it — and because many organisations currently route enablement through a corporate L&D or People function that does not speak the team's technical vocabulary. Two neighbouring realities push against the lower frequency:

- **The L&D-only version does not land.** A corporate AI-literacy course that is the same for a payroll team, a sales team, and your platform team is not a programme — it is a compliance checkbox. Your team will sit through it, learn nothing specific to the actual work, and go back to the tools without having moved. Microsoft's own *Work Trend Index* data on generative-AI adoption is explicit that most self-reported productivity comes from users who have *learned the tool in the context of their actual work*, not from users who sat through a generic workshop ([Microsoft/LinkedIn, *Work Trend Index Annual Report*](https://www.microsoft.com/en-us/worklab/work-trend-index) — see Chapter 6 for the specific citations that back the shape of the programme in this module).
- **The manager owns the delivery contract.** HR / L&D / Platform are delivery partners, not programme owners. Your team's fluency is on *your* performance review, not theirs. Chapter 7 handles the partnership mechanics; this chapter establishes the premise.

This chapter is the frame that holds Chapters 2–8. Chapters 2 and 3 handle the **Day 0 / 30 / 60 / 90 structure** and the **delivery formats** (bootcamps, workshops, community of practice). Chapter 4 handles **tool-budget distribution by learning stage**. Chapter 5 handles the **fluency-growth measurement artifacts** — the first-successful-PR-with-tool, the pair-with-agent reflection, the review-of-your-review. Chapter 6 handles the **research anchors** (Josh Bersin AI-in-L&D, Microsoft Work Trend Index). Chapter 7 handles the **HR / L&D / Platform partnership**. Chapter 8 handles the **handoff upward** to `ai-enablement-lead` (level 45) when scope graduates.

## Core concepts

### What "team-scope AI enablement" actually means

Three recognisable failure modes seed this module. Each is a specific shape of mis-scoped enablement that an unexamined programme can produce. Noticing them is the first manager skill.

**Failure A — the one-shot workshop.** The programme is a half-day vendor-led Copilot demo. Everyone leaves inspired. Nobody's workflow changes the following Monday because there is no *practice loop* behind the demo. Josh Bersin's AI-in-L&D work calls this pattern out explicitly — generative-AI enablement that stops at exposure does not produce capability, because the learner has no concrete artifact to produce and no cohort to produce it with ([Josh Bersin, *The Definitive Guide to Learning in the Age of AI*](https://joshbersin.com/) — see Chapter 6).

**Failure B — the licence drop.** The programme is "we bought everyone a Cursor seat." Six weeks later, usage telemetry shows seven of the thirty engineers log in daily and the rest have opened the IDE twice. No baseline, no stage-shaped expectation, no cohort structure. The team now has a ~$600/engineer/year licence fee that funds a fluency delta of near-zero. Chapter 4 is the response: tool budgets should follow *learning stage*, not seniority — a Cursor seat lands differently on a day-5 engineer than on a day-45 one.

**Failure C — the vanity bootcamp.** The programme is a three-day bootcamp with no pre-work, no post-work, and no on-the-job artifacts. Attendance is 100%. Satisfaction is 4.7/5. Six months later, no measured change in review quality, PR composition, or incident chain. Chapter 5 is the response: a programme is measured by its *artifacts* produced on the real codebase, not by its *events* completed.

A programme that stacks A, B, and C without a measurement frame is theatre by construction. A programme that names a day-0-to-day-90 structure, picks delivery formats *and* a sustaining format, distributes tool budgets by stage, and measures fluency growth through concrete artifacts, is a defensible enablement practice.

### The five-piece shape of a mod-105 programme

A mod-105-literate programme has roughly five pieces, not thirty. Favour a small number of load-bearing pieces that compose over a sprawl of initiatives nobody can recall.

| Piece | What it does | Chapter |
|---|---|---|
| **Day 0 / 30 / 60 / 90 structure** | A dated timeline a 5–30-person team can walk through together, with concrete checkpoints at each boundary | 2 |
| **Delivery formats** | Internal bootcamps (concentrated, cohort-based), workshops (focused, topic-by-topic), community of practice (sustaining) | 3, 7 |
| **Tool-budget distribution by learning stage** | Cursor / Copilot / Claude seats and token allowances allocated by where each engineer is in the curve, not by title | 4 |
| **Fluency-growth measurement artifacts** | The *first-successful-PR-with-tool*, the *pair-with-agent reflection*, the *review-of-your-review* — practical artifacts, grounded in Bersin AI-in-L&D and MSFT Work Trend Index | 5, 6 |
| **Partnership + graduation plan** | HR / L&D / Platform as delivery partners; written handoff contract to `ai-enablement-lead` (L45) when scope graduates | 7, 8 |

Chapter 2 opens the structure; Chapters 3–6 build the four execution pieces; Chapters 7–8 handle the organisational layer above the programme. You will produce one exercise per piece: five exercises for the five pieces.

### Why "learning stage, not seniority" is the load-bearing distinction

The default mental model a manager inherits from pre-AI enablement work is *seniority-shaped*: more senior engineers get more tooling, more junior engineers get more training, the two tracks run in parallel. mod-105 inherits a different shape because the data breaks the seniority assumption.

- [Brynjolfsson, Li, Raymond, *Generative AI at Work* (NBER Working Paper 31161)](https://www.nber.org/papers/w31161) found that in a contact-centre deployment, productivity gains from generative-AI assistance were **concentrated at lower-tenure workers**. The senior cohort moved less. The same pattern shows up, with caveats, in some of the software-engineering studies in mod-104 Chapter 5.
- [Dell'Acqua et al., *Navigating the Jagged Technological Frontier* (BCG + HBS)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321) found that AI assistance produces *performance variance by task*, not by seniority — and that under-performers who used AI appropriately gained the most, while top performers who used AI uncritically could *lose* ground.

The implication for enablement is operational, not ideological: a senior engineer who has never used an agent is a *day-5* learner on that tool, regardless of their title. A junior engineer who spent a year building their own agent harness as a side project is a *day-60* learner. The programme shapes to where they are on the curve, not to what their H1-B says. Chapter 4 is the budget-side version; Chapter 5 is the measurement-side version.

### Why the manager authors the curriculum even when they do not deliver it

Chapter 5 of mod-101 established the manager's AI-fluency bar: *enough fluency to review and model, not to out-ship the team*. R5 extends that bar in a specific direction: the manager **authors the curriculum and sets the measurement rubric**, even when someone else — an internal senior IC, an L&D partner, a vendor trainer — delivers the sessions.

Why the authoring cannot be delegated:

- **Only you know the team's actual workflow.** A generic Copilot workshop does not know that your team's primary pain is debugging agent-authored migrations in a proprietary ORM. An L&D partner cannot invent that curriculum from scratch; they can deliver it once you have authored the scope.
- **Only you own the measurement rubric.** A vendor trainer leaves after the workshop. Your dashboard (mod-104) keeps reporting. The fluency-growth artifacts (Chapter 5) have to map to *your* review standards (mod-103) and *your* productivity narrative (mod-104). An externally-authored rubric will not align.
- **Only you can refuse the wrong intervention.** When the corporate L&D function proposes a four-hour prompt-engineering workshop in a quarter where your team actually needs structured agent-review practice, the manager who has authored the curriculum can redirect the spend. The manager who outsourced authoring cannot.

The division of labour is therefore: **you author, your partners deliver, your team practices, you measure**. Chapter 7 operationalises each piece of that sentence.

### What this module is *not*

As with every module in this track, the adjacent-but-distinct work matters.

- **Not an org-wide AI enablement course.** Programmes that span three or more teams, central tooling procurement, cross-functional literacy campaigns at thousands-of-employees scale, all belong to [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) at level 45 (AI Workforce family). Chapter 8 draws the graduation contract. The manager-level programme hands up evidence; it does not hold the org-wide procurement portfolio.
- **Not a corporate L&D course.** The instructional-design mechanics of a generic AI-literacy curriculum — pedagogy at scale, LMS integration, SCORM, assessment banks — belong to Learning & Development as a function. Chapter 7 handles the partnership interface. This module is *team-shaped*: a programme for a specific 5–30 person team doing a specific kind of work.
- **Not a workforce-strategy course.** The talent-strategy / role-redesign dimension of AI workforce transformation — level ladders, succession planning, strategic workforce planning — is covered partially in [`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/) at team scope, and above the team-manager altitude belongs to HR leadership and `head-of-ai-governance` / `chief-ai-officer`. Not mod-105's remit.
- **Not a productivity-measurement course.** Fluency-growth measurement (Chapter 5) is a *learning-outcome* instrument — it tells you whether the enablement worked. Team-productivity measurement (change failure rate, lead time, PRs/engineer) is a *throughput* instrument. The two compose in the ROI narrative but are separate. [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) owns the throughput side.

### The five artifacts a mod-105-literate manager owns

By the end of this module, you have:

1. A **Day 0 / 30 / 60 / 90 enablement plan** for your actual team, dated, with checkpoints (Exercise 01).
2. A **tool-budget distribution rubric** that allocates Cursor / Copilot / Claude / token budgets by learning stage, not seniority (Exercise 02).
3. A **fluency-growth measurement artifact set** — first-successful-PR-with-tool, pair-with-agent reflection, review-of-your-review — operational, scored, repeatable (Exercise 03).
4. A **community-of-practice charter** for your team — cadence, format, rotations, sustaining mechanism (Exercise 04).
5. A **handoff contract to `ai-enablement-lead` (L45)** — the written criteria for when your team-scope programme graduates to org-wide ownership (Exercise 05).

Exercise 05 is the one most managers skip. It is also the one that most clearly separates a mod-105-literate manager from one who runs a programme in isolation from the broader workforce portfolio.

### Grounding in posting evidence and authoritative references

Two anchors keep this module honest.

- **Posting evidence.** R5 (0.36) in [`JOB_REQUIREMENTS.md`](../../JOB_REQUIREMENTS.md). Treat the recurring vocabulary — *"Day 30/60/90 fluency plan,"* *"community of practice,"* *"bootcamp,"* *"tool-budget distribution,"* *"learning stage,"* *"fluency measurement"* — as the hiring-side signal of what artifacts the market wants to see.
- **Authoritative references.** Primary and public. Josh Bersin's AI-in-L&D research; Microsoft/LinkedIn *Work Trend Index* annual reports; Wenger-Trayner on communities of practice; the five empirical studies from mod-104 Chapter 5 that ground the "learning stage, not seniority" distinction (Brynjolfsson-Li-Raymond, Noy & Zhang, Dell'Acqua et al., Peng et al., Ziegler et al.). Full list in [`resources.md`](resources.md).

A defensible enablement programme cites both. The postings establish *what the market expects the manager to produce*; the references establish *what the evidence says about how adults learn these tools in the context of real work*.

## Example: a two-paragraph sketch of the enablement frame

Treat this as calibration for shape, not a template to adopt.

> **Frame.** On this team (platform infra, 18 engineers, mixed seniority), the AI enablement programme runs on a Day 0 / 30 / 60 / 90 cadence anchored to each engineer's individual join-the-programme date, not to the calendar quarter. Day 0 is the *stage-assessment conversation* (Chapter 4's budget assessment doubles as the stage pin): each engineer is scored 1–4 on each of four tools (AI coding assistant, general-purpose assistant, eval tool at reading level, agent-authoring environment at reading level). Days 1–30 run a **cohort bootcamp** — small-group, cohort-based, concentrated on one tool at a time. Days 31–60 run **topic workshops** (prompt-authoring for code review; delegating a task to an agent; reading an eval report) at a weekly cadence. Days 61–90 run the **community of practice**: one show-and-tell every two weeks, one pattern-library contribution per quarter, one review-of-your-review per month. The manager authors the curriculum and the measurement rubric; the senior IC runs two of the workshops; an L&D partner runs intake + scheduling; Platform runs the tooling onboarding.
>
> **Measurement.** Fluency growth is read from three artifacts that produce evidence on the real codebase (Chapter 5). The *first-successful-PR-with-tool* — opened, reviewed, merged — is recorded per engineer per tool and lands at a checkpoint between Day 14 and Day 30. The *pair-with-agent reflection* — a one-page write-up after a specific delegation-to-agent task — lands at Day 45. The *review-of-your-review* — an engineer reads their own prior review of an agent-generated PR with 30 days of distance and writes what they would do differently — lands at Day 75. All three artifacts cross-link to the mod-103 review standard and the mod-104 ROI narrative. The handoff contract to `ai-enablement-lead` (L45) is written on Day 90 if the programme needs to graduate.

Two paragraphs, legible to the team, to the L&D partner, and to the ai-enablement-lead the programme might graduate up to.

## Summary

- R5 (0.36) names *design and run team-scope AI enablement programmes* as a distinct manager requirement. The posting language says *design*, *run*, and *distribute* — not *sponsor* or *approve*.
- Three recognisable failure modes to avoid: the one-shot workshop, the licence drop, the vanity bootcamp.
- Five-piece shape: Day 0/30/60/90 structure, delivery formats, learning-stage tool budget, fluency-growth artifacts, partnership + graduation plan.
- The load-bearing distinction is **learning stage, not seniority** — grounded in Brynjolfsson-Li-Raymond and Dell'Acqua.
- The manager **authors the curriculum and the measurement rubric** even when partners deliver. Delivery is delegable; authoring and measurement are not.
- This module is *not* an org-wide programme course (that is `ai-enablement-lead`, L45), a corporate L&D course, a workforce-strategy course, or a productivity-measurement course (that is `mod-104`).
- Five artifacts to produce, one exercise each: Day 0/30/60/90 plan, tool-budget rubric, fluency-growth measurement set, community-of-practice charter, L45 handoff contract.
