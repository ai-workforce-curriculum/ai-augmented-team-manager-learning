# Chapter 2 — DX Core 4 as the Dashboard, SPACE as the Research Anchor

> *SPACE is the paper the smart engineer on your team will cite back at you. DX Core 4 is the dashboard the VP expects to see. If you treat the two as rivals you will choose badly; if you treat them as a layered pair you will defend both.*

## Motivation

R4 names *"DX Core 4 / SPACE / DORA under AI-augmented conditions"* as the vocabulary expected of the role. Of the four frameworks surveyed in Chapter 1, **DX Core 4** is the one the market has converged on for the *dashboard* and **SPACE** is the one the research community has converged on for the *shape*. Both come from substantially the same authorship lineage — Nicole Forsgren and Margaret-Anne Storey appear on the SPACE paper (ACM Queue 2021) and on the DX Core 4 writeup (DX, 2024) — which is why this chapter treats them as a pair rather than as competing frameworks.

This chapter answers three operational questions a mod-104 manager will be asked within the first quarter on the job:

1. *What exactly goes on the team dashboard?*
2. *What do I say when someone asks whether a given metric is a performance-management instrument?*
3. *How do I write the rubric that explains why the chosen metrics are these and not others?*

The answer to (3) is Exercise 01 — the DX Core 4 / SPACE side-by-side crosswalk.

## Core concepts

### SPACE: the multi-dimensional shape, and why it matters

[Forsgren, Storey, Maddila, Zimmermann, Houck, Butler, *The SPACE of Developer Productivity* (ACM Queue, 2021)](https://queue.acm.org/detail.cfm?id=3454124) argues two things more loudly than it argues any one metric:

- **Developer productivity cannot be reduced to a single dimension.** The paper's central move is to reject the single-metric framing (lines of code, bugs fixed, story points) in favour of a multi-dimensional lens. A *single-dimension dashboard* is the signature of a measurement programme that has not read the research.
- **Measurement should happen at multiple levels** — individual, team, system — with the explicit guidance that *individual-level metrics should not be used for performance evaluation*, because the measurement will corrupt the behaviour it measures (Goodhart's law is cited by implication throughout).

The five SPACE dimensions:

| Dimension | What it captures | Typical team-level instrument |
|---|---|---|
| **S — Satisfaction & well-being** | Developer sentiment, burnout risk, sense of psychological safety | DX-style quarterly survey; eNPS; retro signal |
| **P — Performance** | Outcomes of the work — reliability, quality, user-visible impact | DORA change failure rate; incident rate; customer-impact proxy |
| **A — Activity** | Volume of what gets done — commits, PRs, reviews, builds | Weekly PR-count; code-review participation; **caveat: activity ≠ output** |
| **C — Communication & collaboration** | Knowledge sharing, review-latency, cross-team work | Review turnaround; number of distinct reviewers per PR; doc-contribution |
| **E — Efficiency & flow** | Ability to do work without interruption — flow state, context switches | Time-to-first-review; interrupt rate; focus-time blocks |

SPACE is **prescriptive about the shape** (pick across multiple dimensions, never use a single metric) and **non-prescriptive about the specific metric** (the team picks its instrument per dimension). This is a feature, not a bug — the paper exists to prevent single-metric reductionism, not to standardise the metric choice.

### DX Core 4: the dashboard shape the market now expects

[DX, *Measuring Developer Productivity with the DX Core 4*](https://getdx.com/research/measuring-developer-productivity-with-the-dx-core-4/) is the current-day industry standard the market has coalesced around for the *team-manager dashboard*. The DX Core 4 writeup explicitly positions itself as a **consolidation of DORA, SPACE, and the subsequent DevEx framework** into a four-dimension system teams can execute on:

| Core 4 dimension | What it measures | Example instruments |
|---|---|---|
| **Speed** | How quickly software is delivered | PRs-per-engineer per week (median); lead time for changes (from DORA) |
| **Effectiveness** | Developer experience — how much friction is in the path | DX-survey "ease of delivery" / "developer experience index"; self-reported time in flow |
| **Quality** | Quality of what is delivered | Change failure rate (from DORA); escaped defects; post-release incident count |
| **Impact** | Business outcomes the work drove | % engineering time on new capability; OKR-attainment share; feature-adoption proxy |

Three observations about Core 4 that matter for mod-104:

1. **Core 4 is opinionated about *dashboard real estate*.** Four dimensions, one or two metrics per dimension, is a tile count a VP can take in. SPACE's five dimensions were never designed as a dashboard; they were designed as a research anchor. Core 4's contribution is making the research executable at the altitude a manager lives at.
2. **Core 4 keeps DORA alive as the Quality anchor.** You do not have to choose between Core 4 and DORA; Core 4 *absorbs* DORA. Chapter 3 goes deep on what breaks and what holds in DORA under AI-augmented conditions; Core 4's Quality tile is where the DORA signal lives on the manager's dashboard.
3. **Core 4 does not solve the AI-attribution problem on its own.** Core 4 tells you whether the team's productivity moved. It does not tell you *whether the AI investment drove the move*. That is a layering question — Chapters 6 and 7 — and no framework resolves it; you resolve it by *composing* the Core 4 numbers with the cost numbers (Chapter 6) and with the qualitative signal (Chapter 8).

### The Core-4 ↔ SPACE crosswalk

The crosswalk is the single artifact most worth internalising. It is also the deliverable of Exercise 01.

| SPACE dimension | Where it maps in Core 4 | What the mapping loses |
|---|---|---|
| Satisfaction & well-being (S) | **Effectiveness** (DX survey picks it up) | Burnout-specific signal is coarser in Core 4 — add a dedicated burnout item in your DX survey if the team has a history of pace crises |
| Performance (P) | **Quality** + **Impact** | Impact is the business-outcome anchor Core 4 names explicitly; SPACE P leaves this looser |
| Activity (A) | **Speed** | SPACE warns activity ≠ output — Core 4's Speed metrics (PRs/engineer, lead time) are *closer* to output than raw commit counts, but the caveat survives |
| Communication & collaboration (C) | **Effectiveness** (indirect) + **Speed** (review latency proxy) | The *explicit* collaboration signal is weaker in Core 4; if cross-team work is a strategic concern this quarter, add a dedicated instrument |
| Efficiency & flow (E) | **Effectiveness** (DX survey picks up self-reported flow) | Objective flow-state measurement (interrupt rate, focus-time analytics) is thinner in Core 4 — supplement if needed |

Reading the right-hand column: *Core 4 is not SPACE*, and the places where Core 4 is *thinner* are where the manager composes in additional instruments. The DX-survey instruments SPACE's S and E dimensions through self-report, which is defensible when combined with the Speed and Quality system signals but not on its own.

### The "do not use for performance management" clause, and how to enforce it

Both SPACE (explicitly, in the paper's discussion section) and Core 4 (explicitly, in DX's own guidance) warn against using these dimensions for individual performance evaluation. This is not advisory for mod-104; it is load-bearing. Two reasons:

- **Goodhart effect.** Any metric used for performance management becomes a target engineers optimise for; the measurement corrupts the behaviour. A team that discovers you are using PR-count for ratings will produce more, smaller, lower-quality PRs within a quarter. The signal you are measuring is now gone and you have degraded the work.
- **Attribution.** Many of the Core 4 instruments are team-shaped (lead time, change failure rate, deployment frequency). Decomposing them to the individual is a methodological error, not just a cultural one.

Three enforcement moves:

1. **Name it, in writing, on the dashboard.** The one-pager (Exercise 04) carries a line: *"these metrics are for team-productivity measurement; individual performance evaluation is covered in [`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/) via different instruments."*
2. **Refuse the decomposition in 1:1 contexts.** When an upward manager or a skip-level asks *"who on your team has the lowest PR-count,"* answer: *"I don't decompose this metric to the individual for the reasons the authors of the framework explicitly flag — but I'm happy to walk the team-level signal and the specific coaching conversations I'm already having."*
3. **Watch for the *other* decomposition.** Someone will try to compute "AI-attributable productivity per engineer" from the same instruments. Same error, same answer.

The posture is not evasive; it is methodological. Engineers who see you defend it earn trust you will draw on later.

### What goes on the dashboard, and in what shape

An executable mod-104 dashboard has roughly five tiles, not thirty. Favour a small number of tiles that read quickly over a comprehensive data warehouse view.

**Tile 1 — Speed.** One trend-line metric. *Weekly PRs merged per engineer (median)*, or *lead time for changes (median and 90th percentile)*. The median is almost always the right statistic; the mean is pulled by outliers in both directions.

**Tile 2 — Effectiveness.** The DX-survey or equivalent developer-experience index, refreshed quarterly. Supplement with a one-question weekly pulse ("rate this week's ease of shipping, 1–5") if you need higher-cadence signal (Chapter 8).

**Tile 3 — Quality.** Change failure rate (the DORA quality anchor). Chapter 3 discusses how this signal behaves under AI-augmented work. A supplementary *escaped-defect count per sprint* adds context.

**Tile 4 — Impact.** The hardest tile to populate honestly. Defensible instruments: *% of engineer-weeks spent on new capability vs. keeping-the-lights-on*; *OKR-attainment share* (what fraction of this quarter's committed OKRs is this team closing); *feature-adoption proxy* (if your product has an attach metric, reuse it; you do not own it — [`ai-augmented-product-manager`](https://github.com/ai-workforce-curriculum/ai-augmented-product-manager-learning) does — but you can read it).

**Tile 5 — AI-cost ratio.** Not a DX Core 4 dimension; added because R4 requires it. See Chapter 6 for the construction. Shape: a single ratio like *"$X in tool spend per 100 PRs merged"* or *"cost per engineer-week in the top-performing cohort"*.

Five tiles. Two or three charts each at most. A sidebar that names the known limits of the signal honestly. Chapter 7 teaches the authoring of the one-pager that references this dashboard.

### Common mistakes when first assembling the dashboard

- **Over-indexing on Activity (A).** PRs, commits, and lines-of-code are the easiest signals to pull and the lowest-signal metrics on the dashboard. A dashboard dominated by activity reads as a theatre dashboard to engineers; keep activity to one Speed tile at most.
- **Confusing Effectiveness with Satisfaction.** Effectiveness is about the friction *in the path of the work*. Satisfaction is about how engineers *feel*. They correlate; they are not the same. If you only instrument satisfaction, you will miss the specific friction a changed toolchain introduces.
- **Treating the DX survey as ground truth.** The DX survey is self-report. It is a legitimate instrument with known Hawthorne effects — see Chapter 5 on Ziegler et al. for the developer-productivity-self-report literature. Compose self-report with system signals; do not replace one with the other.
- **Letting "AI-attributable" become a column on every tile.** Attribution should happen in the narrative (Chapter 7), not inside every tile. A column labelled "AI contribution %" on Change Failure Rate is theatre; a paragraph in the exec pre-read that walks the composed signal is substance.

## Example: a five-tile dashboard sketch

Treat as calibration, not a template.

> **Tile 1 — Speed.** Median weekly PRs-per-engineer, four-quarter trend. Current quarter: 4.1 (↑ from 3.6 in the prior four quarters' baseline). Lead-time median (commit→prod): 2.3 days (flat). *Caveat line: PR-count includes agent-drafted PRs; see Chapter 3 and the data-dictionary note.*
>
> **Tile 2 — Effectiveness.** DX developer-experience index, quarterly. Current: 72/100 (↑ from 68). Weekly ease-of-shipping pulse: 3.8/5 (flat).
>
> **Tile 3 — Quality.** Change failure rate, trailing 90 days. Current: 11% (flat; target ≤ 15%). Escaped defects / sprint: 1.8 (↓ from 2.4).
>
> **Tile 4 — Impact.** Engineer-weeks on new capability: 62% (target ≥ 60%). OKR-attainment share: 3 of 4 team OKRs on track.
>
> **Tile 5 — AI-cost ratio.** Combined tool-spend per 100 PRs merged: $1,430 (first-time measurement — baseline). Breakdown: 61% Claude usage-based, 24% Copilot seats, 15% Cursor seats. See [`exercise-03`](exercises/exercise-03-tool-budget-and-token-cost-tracking.md) for construction.
>
> **Known limits of the signal.** Speed excludes reverts; Effectiveness is self-report with a 32-respondent sample; Impact's "new capability" classification is manual and reviewed at the quarter boundary.

Five tiles. The honest limits sidebar is non-optional.

## Summary

- **SPACE** (Forsgren et al., ACM Queue 2021) is the research anchor — multi-dimensional, multi-level, explicit anti-single-metric posture. Five dimensions: Satisfaction, Performance, Activity, Communication, Efficiency/Flow.
- **DX Core 4** (DX 2024) is the current-day industry-standard dashboard — four dimensions: Speed, Effectiveness, Quality, Impact. Treat as a consolidation of DORA + SPACE + DevEx into dashboard shape.
- Core 4 ↔ SPACE is a crosswalk, not a competition. Where Core 4 is thinner (explicit collaboration, objective flow signal), supplement from SPACE.
- The framework authors are explicit: **these metrics are not for individual performance evaluation**. Enforce in writing, refuse the decomposition upward, watch for the equivalent AI-attribution decomposition.
- A defensible dashboard is ~five tiles: Speed, Effectiveness, Quality, Impact, AI-cost ratio. A "known limits" sidebar is non-optional.
- Exercise 01 produces the DX Core 4 ↔ SPACE side-by-side crosswalk that justifies your dashboard picks.
