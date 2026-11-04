# Chapter 9 — Ownership Boundaries: Analyst Plumbing and Product-ROI

> *The dashboard is yours; the data pipeline is not. The team-productivity narrative is yours; the product-feature ROI narrative is not. A manager who cannot draw these two lines ends up either doing an analyst's work or taking credit a PM owes.*

## Motivation

R4 names team-productivity measurement as the manager's deliverable. Two adjacent roles own work that is often confused with it, and the confusion costs the manager time and credibility:

- [`ai-augmented-analyst`](https://github.com/ai-workforce-curriculum/ai-augmented-analyst-learning) (**level 20**) — the IC data-and-analytics role that owns the *plumbing* of dashboards. When your team-productivity dashboard pulls data from GitHub + LinearB / Jellyfish / DX + the LLM gateway chargeback + the incident tracker, the SQL/warehouse/BI-tool work to join those sources and render the tiles is analyst work, not manager work.
- [`ai-augmented-product-manager`](https://github.com/ai-workforce-curriculum/ai-augmented-product-manager-learning) (**level 30**) — the peer product-manager role that owns the *product-feature* ROI story. When your team ships an AI-powered feature (a Copilot-style suggestion in your product, an agent-in-the-loop workflow for your users), the business-outcome ROI of that *feature* (attach rate, retention delta, gross-margin impact, LTV contribution) is product-manager work, not team-manager work.

Both boundaries are routinely crossed in practice. This chapter is where you set them explicitly for your own role, your own team, and your own narrative.

## Core concepts

### Boundary 1 — the analyst / dashboard-plumbing line

A mod-104-literate manager owns four things on the dashboard:

1. **What goes on it.** Which metrics are picked, from which frameworks (Chapters 2–4), and why.
2. **What the metrics mean.** The data-dictionary — operational definitions, trailing-window choice, cohort segmentation — is a manager artifact.
3. **What the trend says.** The reading posture (Chapters 3, 7, 8).
4. **What decisions follow from it.** The one-pager (Chapter 7) and the rollback criteria (Chapter 6).

A mod-104-literate manager does *not* own:

- **The ETL / data pipeline.** Pulling GitHub events, LinearB telemetry, incident tickets, LLM gateway usage events into a warehouse; schema design for the warehouse tables; incremental refresh scheduling.
- **The SQL / join logic that produces the tile values.** The specific queries behind "weekly PRs-per-engineer median trailing-90-days" are analyst work.
- **The BI tool configuration.** Whether the team uses Looker / Mode / Preset / Tableau / a custom React-plus-chart-library is below your altitude.
- **Data-quality monitoring.** The watch for a broken join, a missing refresh, a schema change on the source system is analyst work.

The handoff conventions worth writing down:

| Artifact | You produce / provide | Analyst produces |
|---|---|---|
| Metric brief (definition of each tile) | Yes — one sentence per tile, trailing window, operational definition, known exclusions | — |
| SQL that computes the tile | Review-and-approve only | Yes |
| Data-source-to-tile mapping | Identify the source | Implement the mapping |
| Tile mock / wireframe | Yes — on paper or a sketch | — |
| Dashboard in the BI tool | Review and feedback | Yes |
| Refresh schedule | Specify (e.g. "daily 6am") | Implement + monitor |
| Pipeline break escalation | Receive and read | Investigate + fix |
| Data-dictionary wiki page | Yes — the business meaning | Co-author — the source lineage |

The manager who writes the metric brief and reads the resulting dashboard is doing R4 work. The manager who writes the SQL is doing someone else's.

**The exception.** On teams without a dedicated analyst partner (which is many teams at mid-size organisations), the manager often has to do some of the plumbing themselves to get to a first version. That is pragmatic, not strategic — the right move once the dashboard exists is to *hand it off* to a partner (your platform/DevEx team, your business-intelligence team, your [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) sponsor's analyst resource), not to accrete the ongoing maintenance.

### Boundary 2 — the product-manager / product-feature-ROI line

The distinction here is between two related but different ROI questions:

- **Team-productivity ROI (yours).** "Did the AI investment in *this engineering team* produce more / better / cheaper-per-unit output this quarter?" Composed from DX Core 4 + DORA + Flow + cost + qualitative. Audience: engineering leadership, finance, your direct sponsor.
- **Product-feature ROI (not yours).** "Did the AI-powered *feature we built* produce user, business, or margin value?" Composed from attach rate, retention delta, gross-margin impact, LTV, cost of inference-per-active-user. Audience: product leadership, revenue leadership, GTM.

The two questions touch each other — a product-feature launch takes team-productivity signal to decide whether the team can take on the next one; a team-productivity narrative is harder to land if the team has not shipped any product features — but they are not the same question and they belong to different roles.

The handoff conventions:

- **The team-manager provides engineering-side evidence** to a product-feature ROI case: "this feature took X weeks of engineer-time; the agent-infra for it costs $Y / month at expected load; the feature's change-failure-rate was Z." These are inputs to the PM's product-ROI narrative.
- **The team-manager does not author** the product-ROI narrative. Attach rate, retention delta, user-visible quality metrics, and product-strategy framing are PM work. The PM may *ask* you to co-sign on an engineering-cost claim; that is co-signing, not authoring.
- **The team-manager's one-pager (Chapter 7) is about the team's productivity, not about the products it ships.** A one-pager that reads "the AI investment in this team drove $N ARR" is almost always claiming someone else's work. A one-pager that reads "the AI investment in this team let us ship Feature-X in 9 weeks instead of the estimated 13" is claiming the team's work.

### Where the two boundaries interact with other mod-104 chapters

The ownership-boundary map, chapter-by-chapter:

| Chapter | Analyst role | PM role |
|---|---|---|
| 2 (DX Core 4 / SPACE) | Owns the plumbing of each tile | — |
| 3 (DORA) | Owns the DORA pipeline | — |
| 4 (Flow) | Owns the Flow-metric data (if captured) | — |
| 5 (Empirical literature) | — | — (this is your reading) |
| 6 (Cost / adoption vs. activation) | Owns the chargeback pipeline + the tool-usage joins | — |
| 7 (One-pager / dashboard / retro) | Owns the dashboard; does not author the one-pager | Owns the product-ROI counterpart one-pager (if there is a shipped AI feature) |
| 8 (Qualitative instrument) | — | — (this is your signal; HR partner may support anonymity tooling) |

The analyst and PM boundaries are the two most frequently blurred; other boundaries (vendor to [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/), governance to [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/), incident to [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/), enablement to [`mod-105`](../mod-105-team-ai-enablement-programs/) and [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning)) are covered in those respective modules.

### Three operational rules of thumb

If a decision is reversible with a conversation and the role boundary is unclear, three rules apply.

**Rule 1 — if it is a SQL query, it is not yours.** The moment you are writing a trailing-90-day window query against a warehouse table, you are doing analyst work. Even if you can do it well, this is not the job the postings pay you to do. Pair with an analyst or escalate to your platform / BI partner.

**Rule 2 — if the primary audience is product / revenue / GTM, it is not yours.** A dashboard built for the CPO's staff is a PM artifact. A dashboard built for the CTO's staff about engineering productivity is yours. When in doubt, ask who signs off on the artifact — the sign-off chain tells you who owns it.

**Rule 3 — if the number is "did the user do more X," it is PM; if the number is "did the engineer ship more X," it is you.** The simplest operational version of the boundary.

### How the boundaries travel in a hiring loop

[`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/) covers hiring; for mod-104 the relevant observation is that interview panels for level-40 AI-augmented-team-manager roles are *explicitly* testing whether candidates confuse the boundary. Two common interview probes:

- *"Walk me through a dashboard you built."* The calibration question is whether you reach for the metric brief / data-dictionary / reading-posture conversation or whether you reach for the SQL. The former signals R4 fluency; the latter signals you are interviewing for an analyst role.
- *"What was the ROI of the AI investment on your last team?"* The calibration question is whether you answer in team-productivity terms ("DORA held, cost was X% of engineering spend, Flow Efficiency improved by Y") or product-outcome terms ("the feature we shipped drove Z% retention lift"). The former answers the asked question; the latter answers someone else's.

Preparing to answer both the right way in a hiring loop is itself a mod-104 exercise. The one-pager (Exercise 04) is the artifact that most directly rehearses it.

### What happens when the boundary is wrong

Three recognisable failure modes when the boundary slips:

- **Manager-as-analyst.** You spend quarter-over-quarter time polishing SQL, debugging the pipeline, maintaining the dashboard. The team's work does not benefit; the analyst function is understaffed because you are doing some of its work; your own level-40 responsibilities drift.
- **Manager-as-PM.** You frame team-productivity in product-outcome terms. Works short-term; fails on the first quarter where the product outcome is driven by factors unrelated to your team (marketing, pricing, a competitor's exit) — now your productivity claim moves with factors you do not control.
- **Manager-takes-credit-for-product.** An AI feature launches and performs well; the one-pager claims the lift. The PM notices. Trust is spent that was more valuable than the slide.

Each is reversible with an explicit conversation at the start of the next quarter. The chapter is written so that conversation is possible without ambiguity.

## Example: a two-paragraph boundary statement for the team's Q-review

Treat as calibration.

> **What this team-productivity narrative covers.** This one-pager is about the engineering team's productivity: throughput, delivery quality, cost ratio, developer experience. It uses the DX Core 4 framework (Chapter 2), DORA (Chapter 3), and Kersten Flow Efficiency (Chapter 4) in the shape documented in the data-dictionary at `docs/metrics-dictionary.md`. The dashboard is plumbed by `@analyst-partner-name` ([`ai-augmented-analyst`](https://github.com/ai-workforce-curriculum/ai-augmented-analyst-learning), L20); the metric brief and reading posture are mine.
>
> **What this narrative does not cover.** The product-feature ROI case for the AI-powered scheduling assistant launched this quarter lives in `@pm-partner-name`'s one-pager ([`ai-augmented-product-manager`](https://github.com/ai-workforce-curriculum/ai-augmented-product-manager-learning), L30). Our one-pager contributes engineering-cost and delivery-quality inputs to that case; the product-outcome narrative (user attach, retention, revenue) is the PM's. The two one-pagers are designed to be read together at the Q-review.

Two paragraphs. Boundaries named. Partner roles credited. No ambiguity about what the manager is and is not claiming.

## Summary

- Two adjacent roles own work frequently confused with R4:
  - [`ai-augmented-analyst`](https://github.com/ai-workforce-curriculum/ai-augmented-analyst-learning) (**L20**) owns **dashboard plumbing** — ETL, SQL, warehouse joins, BI configuration, data-quality monitoring.
  - [`ai-augmented-product-manager`](https://github.com/ai-workforce-curriculum/ai-augmented-product-manager-learning) (**L30**) owns **product-feature ROI** — attach, retention, gross-margin, LTV of AI features shipped by your team.
- The manager owns: **what goes on the dashboard**, **what the metrics mean** (data-dictionary), **what the trend says** (reading posture), **what decisions follow** (one-pager, rollback criteria). The manager does **not** own: ETL, SQL, BI config, product-feature-ROI narrative.
- Three operational rules of thumb: *if it is a SQL query, it is not yours; if the primary audience is product/revenue, it is not yours; if the number is "did the user do X," it is PM, if "did the engineer ship X," it is you.*
- The exception: on teams without an analyst partner, the manager may do first-version plumbing, but should hand it off once the dashboard exists.
- The two one-pagers — your team-productivity one-pager and the PM's product-feature ROI one-pager — are designed to be read together, not substituted for each other.
- Hiring loops ([`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/)) explicitly test whether candidates confuse these boundaries. Prepare to answer both the right way.
- Three failure modes when the boundary slips: manager-as-analyst, manager-as-PM, manager-takes-credit-for-product. All reversible with an explicit next-quarter conversation.
