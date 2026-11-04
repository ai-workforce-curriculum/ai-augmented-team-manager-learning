# Exercise 03 — Tool Budget and Token Budget Distribution

**Estimated effort:** 2 hours.

## Objective

Produce **v0.1 of your team's tool and token budget distribution plan**: the three allocation layers (seat, token, enterprise commit) distributed per [`mod-105` Chapter 4](../../mod-105-team-ai-enablement-programs/04-tool-budgets-by-learning-stage.md)'s stage ladder, with a stage-shift projection for the coming quarter and a finance-partner-facing narrative that composes with the [`mod-104` Chapter 2](../../mod-104-productivity-measurement-and-ai-roi/) AI-cost tile.

The methodological anchor is [Chapter 5](../05-tool-and-token-budget-distribution.md). The budget distribution is the number the team's finance line sees and the number the [`mod-104`](../../mod-104-productivity-measurement-and-ai-roi/) tile divides into PR output; it must be shaped deliberately rather than carrying over from pre-AI budget shapes.

## Prerequisites

- [Chapter 5](../05-tool-and-token-budget-distribution.md) — the three allocation layers and the monthly/quarterly review cadences.
- [`mod-105` Chapter 4](../../mod-105-team-ai-enablement-programs/04-tool-budgets-by-learning-stage.md) — the stage ladder and the stage-shaped distribution rule.
- [`mod-104` Chapter 2](../../mod-104-productivity-measurement-and-ai-roi/) — the AI-cost tile shape that consumes this budget.
- [Exercise 01](exercise-01-copilot-build-vs-buy-matrix.md) and [Exercise 02](exercise-02-agent-framework-selection-matrix.md) — the tool registry contents the budget is distributed across.
- Current stage pins per IC per tool (if any; the exercise re-pins if stale or missing).
- Current vendor pricing: [Cursor pricing](https://cursor.com/pricing), [GitHub Copilot pricing](https://github.com/features/copilot/plans), [Claude Code pricing](https://www.anthropic.com/pricing), [Windsurf pricing](https://windsurf.com/pricing), [Sourcegraph Cody pricing](https://sourcegraph.com/pricing), [JetBrains AI pricing](https://www.jetbrains.com/ai/pricing/), [Zed AI pricing](https://zed.dev/pricing).
- Any org-level enterprise-commitment data the manager has read access to (consolidated spend per vendor, committed usage per quarter). If not available, flag as a gap that routes to [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) / procurement.
- 20 minutes with the team's finance partner (or the equivalent) to confirm the reporting format expected.

## Problem statement

Your team runs the tools from Exercises 01 and 02. Some of those tools are per-seat; some are usage-based; some are on an enterprise commit the org negotiated. The three layers stack; a flat per-IC budget figure obscures what is actually happening.

Chapter 5's stage ladder, drawn from [`mod-105` Chapter 4](../../mod-105-team-ai-enablement-programs/04-tool-budgets-by-learning-stage.md), governs how usage budgets distribute: floors at stages 1–2, median at stage 3, ceiling with review at stage 4. The research anchors — [NBER 31161](https://www.nber.org/papers/w31161), [BCG/HBS Jagged Frontier](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321) — say the signal is stage, not seniority. The failure mode this exercise prevents: a seniority-shaped budget that funds the cohort where returns are smallest, starves the cohort where returns are largest, and reads to finance as drift when the team's enablement programme is actually landing.

## Steps

1. **List every tool in the registry with its pricing model.** For each: per-seat (yes/no, rate), usage-based (yes/no, metering), enterprise-commit (on the org commit, standalone, or n/a), free / open-source. The output of Exercises 01 and 02 is the input list.
2. **Pin stages per IC per tool.** Per [`mod-105` Chapter 4](../../mod-105-team-ai-enablement-programs/04-tool-budgets-by-learning-stage.md)'s rubric: stage 1 (not used in work context in 30 days), stage 2 (used but not shipped production), stage 3 (ships production, judgment), stage 4 (teaching + pattern-contributing). Conduct the stage-pin 1:1s if they are not current. The pin rubric is visible to the IC; the conversation is explicit.
3. **Compute seat budget.** Per tool: number of seats × seat cost. Note any workflow-shaped exceptions (e.g., only the three JetBrains users get JetBrains AI seats). Note any trial seats separately with dates.
4. **Compute token budget per tool.** For each usage-based tool, compute the stage-shaped allocation per Chapter 5's pattern:
   - Stage-1 floor (~50 tasks/month or the vendor-equivalent) × stage-1 count
   - Stage-2 floor (~100 tasks/month or the vendor-equivalent) × stage-2 count
   - Stage-3 median × stage-3 count
   - Stage-4 ceiling (e.g., 3x median) × stage-4 count
   Convert to currency at current vendor rates.
5. **Capture enterprise-commit shape per vendor.** If the org has a commit covering any registry tool, record: total committed per quarter, team's current share, overage terms, exit cost. Where the team cannot read org-level commit data, flag and route to procurement / [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning).
6. **Sum to the three-layer total.** Explicitly separated in the report — one line per layer, one total:
   ```
   Seat budget layer: $X/month
   Token budget layer: $Y/month
   Enterprise-commit team share: $Z/month
   -------
   Total team AI spend: $(X+Y+Z)/month
   ```
7. **Produce a stage-shift projection for the next quarter.** For each IC on the mod-105 cohort, project likely stage movement over the coming quarter — the enablement programme's design predicts some stage-1 → stage-2 and some stage-2 → stage-3 moves. Re-compute the token budget under the projected distribution. Report both numbers (current + projected) side by side.
8. **Draft the finance-partner narrative.** One or two paragraphs. Format:
   - Current state: three-layer total, cohort composition, outlook.
   - Projected state: projected total, stage-shift narrative, explicit framing of the rise as programme-landing rather than drift.
   - Mod-104 tie-in: reference the AI-cost tile, name the direction the ratio moves over the next two quarters and why.
9. **Define the monthly and quarterly review cadence.** Who runs the monthly usage review (usually the manager + a finance partner lite); what signals they watch (floors at stages 1–2, median at stage 3, ceiling at stage 4); what gets escalated; who runs the quarterly stage re-pin + registry integration.
10. **Define the trial seat and trial token handling.** Any trial seat (per Exercise 01) or trial token allocation (per Exercise 02) has a named end date, a review condition at that date, and a budget line separate from production.
11. **File the plan.** Dated. Link from the Chapter 7 tool registry. Share the finance-partner narrative with the actual finance partner for feedback; incorporate.

## Starter guidance

- **Three layers, explicitly separated.** A finance report that rolls seats + tokens + enterprise-share into one line is weaker: when one layer moves, the partner cannot see why. Keep the layers visible.
- **Stage is the input, not seniority.** This is the single most load-bearing move of the exercise. A seniority-shaped allocation inflates the [`mod-104`](../../mod-104-productivity-measurement-and-ai-roi/) ratio and starves the ICs where the mod-105 programme is landing. If you are tempted by a seniority-shaped rule, re-read [`mod-105` Chapter 4](../../mod-105-team-ai-enablement-programs/04-tool-budgets-by-learning-stage.md).
- **Floors are a programme signal.** A stage-2 IC at 20 tasks/month is a 1:1 signal, not a budget cut. Reduce the budget on *data*, not on *underuse*.
- **Stage-4 uncapped with review ≠ uncapped.** The ceiling is a review threshold (quarterly, not monthly), not a hard cap. It exists to catch "one IC runs a side project on the corp licence", not to restrict pattern-building.
- **The stage-shift projection is the whole point.** A budget that reports only current state projects as flat. The programme's design predicts the shift; the shift predicts the next quarter's spend; the shift is the honest narrative to finance. Missing the projection makes the mod-104 ratio look like drift.
- **Stage pins are visible to the IC.** The Chapter 2 rubric from [`mod-105`](../../mod-105-team-ai-enablement-programs/) is shared; the pin conversation is explicit. An opaque stage pin reads as arbitrary and corrupts the budget conversation.
- **Trial seats are named.** Trial seats and trial tokens are a separate line with a dated end. Trial seats silently becoming production seats are a classic drift pattern.
- **Enterprise commit data may not be fully visible.** Where it is not, flag as a gap and route to procurement / [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning). Document the missing data in the plan so the gap is tracked.
- **The finance partner is a partner.** Share the narrative; ask whether the format works; iterate. Finance partners prefer a dated, projected story to a "here's the total" number.

## Acceptance criteria

The plan is complete when:

- Every tool in the registry has its pricing model named (per-seat / usage-based / enterprise-commit / free).
- Stages are pinned per IC per tool, with pin-dates in the last 90 days.
- Seat budget is computed with workflow-shaped exceptions named and trial seats separate.
- Token budget per tool is computed with stage-shaped allocation per Chapter 5.
- Enterprise-commit shape is captured where applicable, or flagged as a gap routed upstream.
- The three-layer total is explicitly separated and summed.
- A stage-shift projection for the next quarter is produced with the re-computed total.
- A finance-partner narrative covers current state, projected state, and the mod-104 tile tie-in.
- Monthly and quarterly review cadences are named with owners and signals watched.
- Trial seats / trial tokens are dated with end conditions.
- The plan is filed at a canonical location with a dated next-review marker.
- A change-log entry names authors, reviewers, and date. v0.1.

## Stretch goals

- **Scenario sensitivity.** Produce two additional scenarios: *rapid advance* (stage-1 → stage-2 → stage-3 moves faster than programme baseline; spend rises ~40%) and *slower advance* (fewer cohort moves; spend rises ~10%). Finance partners read scenario sensitivity as a mature plan.
- **Cost-per-useful-task overlay.** For usage-based tools, compute cost per successful task (useful-task from Exercise 01's Axis 2 × usage cost). This number will decrease as the cohort matures; a cohort-maturity dashboard composes it with the mod-104 ratio tile.
- **Enterprise-commit contribution packet.** Produce a one-page input packet for [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning)'s quarterly commit review: team usage trajectory, stage distribution shift, predicted commit consumption, any stranded-cost risk. Submit even without explicit request — the input is what makes the manager a serious counterparty in commit conversations.
- **Shadow-spend audit.** Audit the team for shadow AI spend — expense reports, personal-card consumer subscriptions, ICs' side-of-desk tools. Any shadow spend above threshold routes to the Chapter 6 due-diligence process or to sunset. The audit is one iteration, not a monthly discipline, but it is a useful first-time pass.
- **Sunset candidate list.** From the usage data, identify tools in the registry whose usage pattern suggests sunset — low usage across the team, demand that did not materialise, or outperformed by a sibling tool. Draft the sunset recommendation for the Chapter 7 quarterly review.
