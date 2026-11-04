# Exercise 03 — Tool Budget and Token-Cost Tracking

**Estimated effort:** 2 hours.

## Objective

Produce a **reconciled quarterly AI tool-spend table + adoption-vs-activation report** for your team, as specified in Chapter 6. The output is two short artifacts that live alongside the dashboard:

- `docs/ai-tool-spend-reconciliation.md` — the three-component spend table (seat / usage / platform), normalised per engineer and per 100 PRs merged.
- `docs/ai-tool-activation.md` — the adoption-vs-activation report with one operational-definition picked per tool and the cohort breakdown.

Together they produce the denominator of the ROI number in the Exercise 04 one-pager.

## Prerequisites

- Chapter 6 of this module.
- Finance / procurement contact who can tell you the SaaS-licence cost for each AI tool your team uses (Copilot, Cursor, Claude Code, etc.).
- Access to the usage-based telemetry: your organisation's LLM gateway chargeback (if any); vendor consoles (Anthropic console, OpenAI org dashboard, Cursor team console, Copilot admin, etc.).
- One month of PR-merge history for your team.
- The data-dictionary stub from Exercise 01 (the Tile 5 definition you proposed lives here).

## Problem statement

Most teams at the first mod-104 attempt discover one or more of the following:

- The procurement / finance view of AI spend is partial — it covers the seat lines but not the usage-based lines.
- The usage-based lines are in three different vendor consoles with inconsistent reporting periods.
- Nobody has previously attempted a per-engineer or per-PR normalisation, so there is no baseline.
- "Adoption" has been reported upward as a proxy for productivity, and nobody has defined "activation."

Your job is to produce the first reconciled version of the number *and* the first defensible activation definition. This is almost certainly a first — the artifact itself is often the first time the question has been posed at your team.

## Steps

1. **Enumerate every AI tool your team pays for.** One row per tool: name, licence type (seat / usage-based / hybrid), owner (procurement line or team budget line), whose console or report shows the spend. Include free-tier tools only if the team's work routes through them at a meaningful rate (if so, this is also a `mod-110` governance flag).
2. **Pull the Q-to-date spend for each tool.** From procurement for seats; from vendor consoles or LLM-gateway chargeback for usage; from platform-team allocation for infra. Record in a single table.
3. **Compute the reconciled total and the two normalised ratios.** Total quarterly spend; per engineer per quarter; per 100 PRs merged. See Chapter 6's reconciliation table for the shape.
4. **Compute the third ratio if your audience is finance-facing.** AI tool-spend as a fraction of fully-loaded engineering headcount cost. If you do not know the fully-loaded cost, your finance partner does; ask.
5. **Pick an activation definition per tool.** One of the Chapter 6 candidates (weekly-active-use, suggestion-acceptance-threshold, material-use, flow-time contribution), or an equivalent your team's tooling actually measures. Pick *one per tool*; document the definition on the page.
6. **Compute the adoption and activation counts.** For each tool: adopted (seats provisioned) / N engineers; activated (meets your definition) / N engineers. Note the delta.
7. **Segment the activation data.** By tenure band (early / mid / senior) and by workstream (your team's natural work-splits). Do not segment at a level that de-anonymises (see Chapter 8's governance note).
8. **Identify the tried-and-stopped cohort.** Adopted but not activated. This is the diagnostic cohort from Chapter 6. List their count and — without naming individuals in the artifact — one sentence on the pattern (e.g. *"the three tried-and-stopped engineers are concentrated in the data-pipeline workstream"*).
9. **Write the summary paragraph.** 4–6 sentences summarising: total spend, per-engineer and per-100-PR ratios, the quarter-over-quarter trend (if second-run; label as baseline if first-run), adoption / activation deltas, the tried-and-stopped signal.
10. **Walk the artifact to a finance / procurement partner for the spend half, and your `ai-augmented-analyst` partner (or senior IC) for the activation half.** Specifically check: do the numbers reconcile against their view? Do the operational definitions match what their data model supports?
11. **Freeze v0.1.** Dated, titled, author listed, reviewers listed, change log.

## Starter guidance

- The exercise is *not* to measure perfectly; it is to measure *defensibly*. First-time measurement has gaps. Name the gaps in a known-limits section rather than papering over them.
- Prefer platform chargeback over self-report wherever available. If you are currently on self-report, make moving off it a Q+1 action item and name it in the artifact.
- The per-engineer ratio and the per-100-PR ratio are different signals. Per-engineer travels well in finance conversations; per-100-PR travels well in engineering conversations. Report both.
- For activation, resist picking "opened the IDE extension" even though it is the easiest number to pull. That measure degrades to adoption + survival over time, and gives you no actionable signal. Pick a definition that distinguishes material use.
- The tried-and-stopped cohort is treated as a signal, not as a rollout failure (Chapter 6). Your note on this cohort should be diagnostic (what pattern surfaces), not corrective (how to push them back onto the tool).
- Normalise against engineer-weeks if headcount changed in-quarter. A 14→16-person team mid-quarter should carry a note that the ratios are computed against average-headcount rather than end-of-quarter headcount.
- For the quarterly-trend reading, ratios are more interpretable than absolute spend. "+12% QoQ in the per-100-PR ratio" is a sentence; "$4,320 more than last quarter" invites the follow-up "is that a lot," which the per-100-PR trend answers.

## Acceptance criteria

The two artifacts are complete when:

- Every AI tool the team pays for is enumerated with licence type, owner, and data source for spend.
- The reconciled spend table carries a total, per-engineer, per-100-PR, and (if available) % of fully-loaded eng cost.
- A known-limits section names at least two specific limits of the reconciliation (e.g. *"personal-account usage is not included,"* *"usage-based chargeback has a one-week reporting lag"*).
- An activation definition per tool is explicitly documented.
- Adoption and activation counts are computed against N engineers with the delta visible.
- Segmentation by at least tenure and workstream is computed — or an explicit note that the segmentation is withheld to preserve anonymity on this team size.
- The tried-and-stopped cohort is called out with a one-sentence pattern note.
- The summary paragraph is 4–6 sentences and uses the numbers in context.
- Finance / procurement has reviewed the spend half; an analyst or senior IC has reviewed the activation half.
- The artifacts are titled, dated, list contributors, carry known limits, and carry a change log.

## Stretch goals

- **Rollback-criteria prep.** Pre-compute whether any of the four Chapter 6 rollback triggers is at risk this quarter. Feed any that are into [`exercise-06`](exercise-06-rollback-criteria-and-what-we-got-wrong-drill.md).
- **Activation quality check.** For a 5-engineer random sample from your "activated" cohort, walk one of their agent-authored PRs and confirm the activation definition is picking up what you believe it is. The one-off check is cheap and surfaces definition drift early.
- **Build-vs-buy honest accounting.** If your team runs any internal AI infra (a home-grown agent orchestrator, an internal RAG pipeline), include the amortised engineer-time cost as a line on the spend table. The build-side cost is often the largest and the most invisible. Chapter 6's platform-chargeback pattern covers it; the honest version reports it here.
- **Projection for the next quarter.** With one or two quarters of data, project the next quarter's spend ratio and the activation delta. Feed into the Exercise 04 one-pager's decision ask.
- **Tool-level ROI ratio.** If your team pays for more than one tool (common), compute the per-100-PR ratio by *tool* as well as in aggregate. The per-tool ratio sometimes surfaces that the aggregate ratio is hiding one high-cost / low-activation tool that should be rolled back. Chapter 6's rollback discussion applies.
