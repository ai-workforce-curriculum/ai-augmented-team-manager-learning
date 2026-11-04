# Chapter 1 — Metrics That Separate AI-Induced Gain from AI Theatre

> *A number that goes up because people are typing into Copilot more is not evidence that the team is shipping more. A manager who cannot tell the difference will be asked to defend a spend they cannot explain.*

## Motivation

R4 of the posting sample that seeded this track (see [`JOB_REQUIREMENTS.md`](../../JOB_REQUIREMENTS.md)) names *"measure team productivity, cost, and AI ROI"* as a distinct requirement for the role. Posting frequency **0.40** (4 in-window postings in the 25-posting sample; the remainder is live-but-undated ATS language treated as corroborating). Verbatim phrasings include *"defend the AI tooling spend to leadership,"* *"report on team productivity under AI,"* *"track adoption and activation of AI tooling,"* and *"own the ROI narrative for the AI investment on this team."*

R4 is lower-frequency than R1 (0.76, team adoption) or R2 (0.60, review standards) because the market is still in the early phase of codifying it. That does not make it less load-bearing. Two neighbouring realities push the opposite way:

- The CFO-and-above audience that signs off on your tool-budget *already* operates in the ROI frame. The question *"what did we get for the $N we spent on AI tooling last quarter"* arrives on your desk whether or not the postings have standardised the vocabulary yet.
- The skeptical IC audience on your team is watching for whether the metric story is honest. If you arrive at the Q-review with a slide claiming "+25% productivity" and half your team saw two hours of debugging agent output last Tuesday, you have spent trust you will need in `mod-109` when something breaks.

The metric story is therefore a *two-audience* artifact. Leadership reads it to decide whether to keep paying. The team reads it to decide whether you are a manager who understands what they do. Both audiences detect theatre quickly.

This chapter is the frame that holds the next eight. Chapters 2–4 go deep on the three named frameworks — **DX Core 4**, **SPACE**, **DORA** — plus **Kersten flow metrics**. Chapter 5 handles the empirical literature that grounds the metric *choice* in evidence rather than fashion. Chapter 6 handles **cost tracking** (token, seat, tool-budget, adoption-vs-activation). Chapter 7 is the **ROI narrative** artifact set — the one-pager, the dashboard, the retro. Chapter 8 is the **qualitative instrumentation** that keeps the quantitative story from drifting. Chapter 9 draws the **ownership boundaries** with `ai-augmented-analyst` (dashboard mechanics) and `ai-augmented-product-manager` (product-feature ROI).

## Core concepts

### What "AI theatre" looks like in a metrics dashboard

Three recognisable failure modes seed this module. Each is a specific shape of theatre that an unexamined dashboard can produce. Noticing them is the first manager skill.

**Theatre A — adoption-count as productivity.** The dashboard reports *"78% of engineers used Copilot this week."* This is an **adoption** number, not a productivity number. It says the tool was invoked, not that anything shipped faster, nothing shipped broken, or that the team made fewer trade-off errors. When a VP asks *"so what did we get for the licence spend?"*, "78% adoption" is a non-answer dressed as a data point. GitHub's own research is explicit on this — [Ziegler et al., *Measuring GitHub Copilot's Impact on Productivity*](https://cacm.acm.org/research/measuring-github-copilots-impact-on-productivity/) (Communications of the ACM) treats *acceptance rate* as the strongest *leading* indicator of a developer's *felt* productivity, not as productivity itself.

**Theatre B — suggestion-acceptance as output.** The dashboard reports *"42% of Copilot suggestions were accepted."* Acceptance is a real signal — it correlates with self-reported productivity in the Ziegler study — but a suggestion accepted is not a feature shipped. A team that accepts many suggestions and still misses its DORA deployment-frequency band has not become more productive; it has become more reliant on autocomplete.

**Theatre C — self-reported time saved, uncorrected.** The pulse survey reports *"engineers say they save 7 hours/week with the agent."* Self-reported time savings is a legitimate signal — it is in fact the primary endpoint in some of the academic work in Chapter 5 — but it is neither a cost nor a throughput number. [Peng et al., arXiv:2302.06590](https://arxiv.org/abs/2302.06590) found a ~55% speed-up on a controlled HTTP-server task; that is *not* the same as a 55% team-throughput increase, because real team work is not that task, real teams are not blocked on single-task throughput, and the self-reported number compounds Hawthorne effects that a quasi-experimental lab setting controls for.

A dashboard that stacks A, B, and C without naming the limits of each is theatre by construction. A dashboard that names the limits of each, and *adds* at least one throughput metric and one quality metric that the audience can independently anchor, is a defensible measurement.

### The four frameworks you need to be fluent in

This track teaches four by name. You do not *use* all four simultaneously; you *pick from* the four with awareness of what each measures and misses. Chapters 2–4 go deep; this is the orientation.

| Framework | What it measures | What it misses | Best use |
|---|---|---|---|
| **DX Core 4** ([DX, 2024](https://getdx.com/research/measuring-developer-productivity-with-the-dx-core-4/)) | A consolidated four-dimension system — *Speed*, *Effectiveness*, *Quality*, *Impact* — explicitly positioned as "the one unified framework" distilled from DORA, SPACE, and SPACE's successor work by the same authors (Forsgren, Storey et al.). | Industry framework, not academic; depends on both system-generated signals and self-reported DX survey responses. | Current-day team-manager dashboard. Chapter 2. |
| **SPACE** ([Forsgren, Storey, Maddila, Zimmermann, Houck, Butler — ACM Queue 2021](https://queue.acm.org/detail.cfm?id=3454124)) | Five dimensions — *Satisfaction & well-being*, *Performance*, *Activity*, *Communication & collaboration*, *Efficiency & flow* — with the explicit guidance that **no single dimension is a complete measure**. | Peer-reviewed research framework; prescriptive about *shape* (multi-dimensional, multi-level), not about *specific metrics* — teams choose their own instrument per dimension. | Research anchor for *why* the dashboard is multi-dimensional. Chapter 2. |
| **DORA** ([Google Cloud DORA, annual *State of DevOps*](https://dora.dev/research/)) | Four keys of software delivery performance — *Deployment frequency*, *Lead time for changes*, *Change failure rate*, *Failed deployment recovery time* (previously MTTR) — plus the reliability dimension. | Delivery-performance, not individual productivity; signal weakens on teams whose *bottleneck is not delivery*. | Delivery-health anchor — survives AI-augmented conditions with care. Chapter 3. |
| **Flow metrics** (Mik Kersten, [*Project to Product*](https://projecttoproduct.org/), the Flow Framework) | Four work-item-flow dimensions — *Flow Velocity*, *Flow Time*, *Flow Load*, *Flow Efficiency* — across four work types (*Features / Defects / Risks / Debts*). | Opinionated about product-oriented work items; needs a disciplined taxonomy of work to compute at all. | Team-to-product-line narrative; how the metric story reads up to a VP who thinks in product value. Chapter 4. |

Chapter 2 treats DX Core 4 as the *default* the market currently expects to see on a manager's dashboard, and uses SPACE as the research anchor that justifies the multi-dimensional shape. Chapter 3 handles DORA under AI-augmented conditions — specifically the question *"does deployment frequency still mean what it used to mean when 40% of my diffs were agent-drafted?"* Chapter 4 is Kersten.

### Why no single framework answers R4

R4 asks you to *separate AI-induced gain from AI theatre and defend the spend*. None of the four frameworks on its own answers that question:

- DX Core 4 tells you whether the team's **overall** productivity moved. It does not isolate the AI-attributable share.
- SPACE tells you that your dashboard should be **multi-dimensional**. It does not tell you which metrics to pick.
- DORA tells you whether the team is still **delivering**. It does not tell you *why*.
- Flow metrics tell you how work-items are **flowing** end-to-end. They do not tell you the *driver*.

The answer is composite. R4-literate measurement is:

1. A **DX Core 4 or SPACE-shaped dashboard** that anchors the team's overall productivity story (Chapter 2).
2. A **DORA band** the team holds at — tracked for regression, especially *change failure rate* (Chapter 3).
3. A **flow lens** on the one or two product lines where the narrative needs to read up (Chapter 4).
4. A **cost lens** — token + seat + budget — that makes the denominator of the ROI number real (Chapter 6).
5. A **qualitative instrument** — retros, 1:1s, pulse surveys — that keeps all of the above honest (Chapter 8).

Five lenses, each thin. A dashboard built by stacking the five is what Chapter 7 teaches you to assemble into a story.

### Why the empirical literature belongs in Chapter 5

A manager who cites "25% productivity gain from Copilot" without naming the study, the task, the population, and the confidence interval is one meeting away from being corrected by an engineer who read the paper. The posting evidence (R4) and the literature (Peng et al., Ziegler et al., Noy & Zhang, Brynjolfsson-Li-Raymond, Dell'Acqua et al.) jointly produce the only defensible version of the ROI narrative: *"the published range is X–Y; our team's own read on the same instrument is Z, for these specific reasons."* Chapter 5 puts you in a position to produce that sentence.

### What this module is *not*

As with every module in this track, the adjacent-but-distinct work matters.

- **Not a dashboard-building course.** The mechanics of pulling signals from GitHub / LinearB / Jellyfish / DX / Swarmia into a shared dashboard — SQL, data-model, warehouse, BI tool — live at [`ai-augmented-analyst`](https://github.com/ai-workforce-curriculum/ai-augmented-analyst-learning) (level 20). You own what goes on the dashboard; the analyst owns how it is plumbed. Chapter 9 draws the line.
- **Not a product-ROI course.** The ROI of an AI *feature* in a product — gross-margin improvement, user retention from an AI-powered capability, feature-attach rate — is owned at [`ai-augmented-product-manager`](https://github.com/ai-workforce-curriculum/ai-augmented-product-manager-learning) (level 30). The manager-of-the-team-that-built-the-feature contributes evidence (via this module) to the product-ROI case; they do not own it. Chapter 9 draws the line.
- **Not a FinOps / cloud-cost course.** Enterprise AI infra cost (GPU reservation, model-hosting cost, contract negotiation posture) is downstream of your partner-function sign-off, not inside this module. Vendor and budget selection at team scope — the narrower, team-manager-sized slice — is [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/).
- **Not a performance-management course.** DX Core 4 and SPACE are *explicit* that these metrics are not for individual performance evaluation. That trap is covered in Chapter 2. Individual performance and feedback with AI in the loop is [`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/).

### The six artifacts a mod-104-literate manager owns

By the end of this module, you have:

1. A **framework-crosswalk** that shows which metrics you have picked from DX Core 4 / SPACE / DORA / Flow, and *why* (Exercise 01).
2. A **literature digest** — one page — summarising what Peng, Ziegler, Noy-Zhang, Brynjolfsson, and Dell'Acqua *did* find, so you can cite responsibly (Exercise 02).
3. A **tool-budget and token-cost tracker** — the spend side of the ROI denominator (Exercise 03).
4. An **AI-ROI exec pre-read** — one page a VP can sign — and the backing dashboard it reads from (Exercise 04).
5. A **qualitative-instrument design** — the retro prompts, 1:1 questions, and pulse survey you run alongside (Exercise 05).
6. A **rollback-criteria doc + "what we got wrong last quarter" drill** — the honesty valve that keeps the measurement calibrated (Exercise 06).

Exercise 06 is the one most teams skip. It is also the one that most clearly separates a mod-104-literate manager from a theatre-prone one.

### Grounding in posting evidence and authoritative references

Two anchors keep this module honest.

- **Posting evidence.** R4 (0.40) in [`JOB_REQUIREMENTS.md`](../../JOB_REQUIREMENTS.md). Treat the recurring vocabulary — *"defend the spend,"* *"adoption vs activation,"* *"ROI narrative,"* *"token / seat cost,"* *"roll back AI tooling,"* *"productivity under AI"* — as the hiring-side signal of what artifacts the market wants to see.
- **Authoritative references.** Primary and public. The DX Core 4 writeup from DX; the SPACE paper in ACM Queue; the DORA research page and *Accelerate* (IT Revolution); Kersten's *Project to Product* and the Flow Framework site; the five empirical papers above. Full list in [`resources.md`](resources.md).

A defensible metric story cites both. The postings establish *what the market expects the manager to measure*; the references establish *the state of the art of measuring it*.

## Example: a two-paragraph sketch of the metric frame

Treat this as calibration for shape, not a template to adopt.

> **Frame.** On this team, we measure AI-induced productivity along four lenses that *compose into* a single quarterly story. (1) **DX Core 4** drives the primary dashboard: a Speed metric (weekly PRs-per-engineer, median), an Effectiveness metric (DX-survey "ease of delivery" score), a Quality metric (change failure rate from DORA), and an Impact metric (features landed against the quarter's OKRs). (2) **DORA** sits inside Core 4 for the Quality lens; we also track deployment frequency and lead time for changes as a regression guard. (3) **Flow metrics** read the top two product lines (checkout, admin-reporting) end-to-end for the VP narrative. (4) **Cost** — Claude + Copilot + Cursor token/seat spend per engineer-week — is the denominator on the ROI slide.
>
> **Honesty valve.** Quantitative is cross-checked against qualitative: three retro prompts and two 1:1 questions ([`exercise-05`](exercises/exercise-05-qualitative-instrument-design.md)) run on a 6-week cadence. When the quantitative and qualitative diverge for two consecutive cycles, we treat the gap as the finding — not as a data problem. The "what we got wrong last quarter" drill ([`exercise-06`](exercises/exercise-06-rollback-criteria-and-what-we-got-wrong-drill.md)) runs at the quarter boundary with written rollback criteria, so the metric story can be *revised* without a political crisis.

Two paragraphs, legible to the team, to a VP, and to an analyst partner.

## Summary

- R4 (0.40) names *measure productivity, cost, and AI ROI* as a distinct manager requirement. The posting language says *measure* and *defend the spend*, not *drive engagement*.
- Three recognisable theatre shapes to avoid: *adoption-count as productivity*, *suggestion-acceptance as output*, *uncorrected self-reported time saved*.
- Four frameworks to be fluent in: **DX Core 4** (default dashboard), **SPACE** (research anchor for multi-dimensional shape), **DORA** (delivery health, with care under AI), **Flow metrics** (product-line narrative). None answers R4 alone.
- R4-literate measurement composes five lenses: DX/SPACE dashboard, DORA band, Flow lens on top product lines, cost lens, qualitative instrument. Chapters 2–8 build the five; Chapter 9 draws the ownership boundaries.
- This module is *not* a dashboard-plumbing course (that is `ai-augmented-analyst`, L20), a product-AI-ROI course (that is `ai-augmented-product-manager`, L30), a FinOps course, or a performance-management course (that is `mod-108`).
- Six artifacts to produce: framework crosswalk, literature digest, tool-budget tracker, exec pre-read, qualitative instrument, rollback-criteria + "what we got wrong" drill. One exercise per artifact.
