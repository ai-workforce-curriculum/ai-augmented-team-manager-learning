# Exercise 01 — DX Core 4 and SPACE, Side by Side

**Estimated effort:** 2 hours.

## Objective

Produce a **dated, team-specific metric crosswalk** that answers three questions: *(a) which DX Core 4 tiles does your team's dashboard carry, (b) what SPACE dimensions does each tile instrument, and (c) what SPACE dimensions is the dashboard thin on — and what, if anything, are you doing about it.* The output is a one-page `docs/metrics-crosswalk.md`-style artifact a peer manager could read and comment on without a follow-up meeting.

This is the first of the six mod-104 artifacts you will produce; Exercises 02–06 each take a different slice of the measurement programme and are internally consistent with this one.

## Prerequisites

- Chapters 1 and 2 of this module.
- Chapter 5 of this module *before* you start on the picks (it will change which metrics you reach for).
- Access to your team's current dashboard (even if it is a Looker board you did not build, or a Google Sheet maintained by a lead on your team).
- Access to the DX / LinearB / Jellyfish / Swarmia / internal-tool instance your team uses, if any. If you have none, work against GitHub + incident-tracker + LLM gateway chargeback as a minimum.
- The data-dictionary (or equivalent definitions doc) from your current measurement setup. If none exists, this exercise will also *produce* its first version as a byproduct.

## Problem statement

Many engineering teams inherit a dashboard that has grown by accretion: a DORA board set up two years ago, a few Jellyfish / LinearB charts added when a new VP arrived, a Google Sheet that tracks tool-spend, a quarterly DX survey run by a platform team. The composite is not a mod-104 dashboard; it is a scrap heap.

Your job is to *name* the current state, *crosswalk* it to DX Core 4 and SPACE, identify the specific thin spots, and propose a v0.1 of the mod-104 dashboard (the "five tiles" from Chapter 2) that is defensible. You do not need to *build* the five-tile dashboard in this exercise — only to justify the picks so that the Exercise 04 one-pager can read from it when it lands.

## Steps

1. **Inventory the current state.** Open your current dashboard (or scrap heap). List every chart / tile / number currently on it. For each: (a) what is the metric, (b) where does the data come from, (c) how frequently does it refresh, (d) who looks at it.
2. **Crosswalk to SPACE.** For each existing metric, write which SPACE dimension it instruments (S / P / A / C / E) — if any. Metrics that do not map to any SPACE dimension are candidates for removal; metrics that map to the same dimension as three others are candidates for consolidation.
3. **Crosswalk to DX Core 4.** For each existing metric, write which Core 4 dimension it maps to (Speed / Effectiveness / Quality / Impact). You will almost always find tiles concentrated on Speed and Activity; Effectiveness and Impact are frequently thin or missing.
4. **Identify the thin spots.** From Steps 2 and 3, write a one-paragraph summary of where the current dashboard is thin against each framework. Be specific: *"Effectiveness is instrumented only by one weekly pulse question; SPACE's Satisfaction and Communication dimensions are not instrumented at all."*
5. **Propose the five-tile v0.1.** Write the Chapter-2 five-tile layout — Speed, Effectiveness, Quality, Impact, AI-cost ratio — specifying for each tile:
   - the specific metric chosen (e.g. "weekly PRs-per-engineer, median, trailing 90 days"),
   - the data source,
   - the trailing-window choice,
   - the known limits of the signal,
   - one sentence on why this metric and not an alternative.
6. **Write the data-dictionary stub.** For each of the five tiles, two or three sentences of operational definition. This is the seed of the data-dictionary your Exercise 04 one-pager will link to.
7. **Name the SPACE dimensions you are deliberately under-instrumenting.** This is the honest version of the crosswalk — the decision that *Communication*, say, is not on the current dashboard because the team's current operating posture does not need it, not because you forgot. Write the reason.
8. **Walk the draft to one analyst-side partner and one engineering-side partner.** Your `ai-augmented-analyst` partner (if you have one) and one senior IC. Specifically ask: *does the metric brief make the SQL buildable without a follow-up meeting? Does the metric brief make the reading of the tile unambiguous?*
9. **Freeze v0.1.** Title: `Metric Crosswalk v0.1 — [team name] — [YYYY-MM-DD]`. Author (you), reviewers, scope-and-caveats paragraph, change log.

## Starter guidance

- The crosswalk is a *justification artifact*, not a plumbing artifact. SQL does not go in here. Metric *definitions* and *reading* do.
- Chapter 2's SPACE-to-Core-4 table is a starting mapping, not the final mapping. Your team's instruments may map differently; the specific mapping you pick is a defensible choice, not a derivation.
- Favour metrics whose definition fits on one line. "Trailing-90-day median of weekly PRs merged per engineer" is a one-line metric. "A composite index of X, Y, Z weighted by a confidential formula" is a yellow flag.
- Do not try to instrument every SPACE dimension. The *point* of the crosswalk is to make deliberate choices about what to under-instrument; a dashboard that tries to carry everything will carry nothing well.
- The AI-cost ratio tile (Tile 5) is not a DX Core 4 dimension. Chapter 2 is explicit that this tile is *added* by mod-104 because R4 requires it. Name it as an additional tile rather than trying to shoehorn it into Core 4.
- For the "known limits of the signal" column, each tile should have *one specific* named limit, not a general hedge. "Includes agent-authored PRs" is specific; "noisy metric" is not.

## Acceptance criteria

The crosswalk is complete when:

- Every metric currently on the team dashboard is crosswalked to SPACE (any of the five dimensions, or explicit "none") and to DX Core 4 (any of the four dimensions, or explicit "none").
- A thin-spots paragraph names the specific SPACE dimensions under-instrumented and specific Core 4 dimensions under-instrumented.
- A five-tile v0.1 proposal exists with specific metric picks for each of Speed / Effectiveness / Quality / Impact / AI-cost, each with source, trailing window, known limit, and one-sentence rationale.
- A data-dictionary stub exists with 2–3 sentences of operational definition per tile.
- A deliberate-under-instrumentation paragraph names what you have chosen not to instrument and why.
- At least one analyst-side reviewer and one engineering-side reviewer has reviewed; their feedback is reflected or logged.
- The artifact is titled, dated, lists contributors, carries scope-and-caveats, carries a change log.
- Each metric definition fits on one line. Composite indices with opaque weights are either unpacked or flagged for replacement.
- The AI-cost tile (Tile 5) is named explicitly as an addition rather than shoehorned into Core 4.

## Stretch goals

- **Cross-team comparison.** Share your v0.1 with one peer manager on a different team in your organisation. Compare the five-tile picks. Note divergences without resolving them — the divergences are themselves data about cross-team variance that will matter in [`mod-112`](../../mod-112-cross-functional-leadership-and-ritual-calendar/).
- **One-tile-per-week walk-through.** For each of the five tiles, spend one Monday writing a three-sentence reading of the tile in your Monday pre-read. By week five you will have exercised the full reading posture on real data and the Exercise 04 one-pager will be measurably easier.
- **Thin-spot action plan.** For each SPACE dimension you deliberately under-instrument, write *under what conditions would we instrument it*. Communication might come onto the dashboard when cross-team work rises above X% of capacity; Collaboration when the team grows above size Y.
- **Six-month sunset check.** Add a line at the top of the artifact: *"this crosswalk is reviewed on [date six months from today]."* Put it in your calendar. A metric programme that does not sunset drifts.
- **Non-code work slice.** If your team has non-engineering members (PM-embedded, design-embedded, ops-embedded) and their work is on the same dashboard, do the crosswalk for their work separately. The DX / SPACE frameworks are code-centric; forcing non-code work onto a code-shaped dashboard is a common mis-use.
