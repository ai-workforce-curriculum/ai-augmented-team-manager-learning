# Chapter 6 — Token Cost, Tool-Budget, and Adoption-vs-Activation

> *The denominator of the ROI number is the number you own. If you cannot answer "what did we spend on AI tooling last quarter" in two sentences, every productivity claim you make upward is defenceless.*

## Motivation

R4 names *"per-engineer token cost, tool-budget, adoption-vs-activation"* as explicit measurement surface area for the role. The subtext is straightforward: the market has learned that AI tool-budget conversations go wrong when the team manager cannot reconcile seat spend, usage-based token spend, and actual activation into a single defensible number.

This chapter answers four operational questions:

1. *What are the three components of AI tool-spend at team scope, and how do I reconcile them?*
2. *What does "adoption vs activation" mean and why does the distinction matter?*
3. *What does the per-engineer / per-PR / per-feature cost ratio look like on the dashboard?*
4. *When do I escalate to [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) (vendor / budget) rather than handle it inside mod-104?*

## Core concepts

### The three components of AI tool-spend at team scope

Most teams have *at least two* of the following three; often all three. Reconciling them into one number is the mod-104 work.

**Component 1 — Seat spend.** Flat per-user licences. Copilot Business / Copilot Enterprise, Cursor Pro, GitHub Enterprise's AI add-ons, Tabnine, Codeium team plans, in-IDE assistants. Sits in the SaaS-spend line of your budget; typically negotiated once-a-year.

**Component 2 — Usage-based token spend.** Claude API usage, OpenAI API usage, internal LLM gateway consumption that chargebacks to the team, Claude Code / Claude for Enterprise usage, any agentic tool whose cost scales with calls. Variable by week; can double in a release crunch and halve when the team is in planning.

**Component 3 — Platform / infra spend.** Internal LLM gateway infra, shared vector-DB cost, agent-orchestration platform cost that the platform team passes back to you. Usually the smallest line for the typical team manager; sometimes the largest if your team is the one running the agent that the rest of the org uses — in which case you have a cross-boundary problem (`mod-111` territory).

A **unified spend line per quarter** is the deliverable. The reconciliation should fit in one table:

| Source | Quarter spend | Unit | Notes |
|---|---|---|---|
| Copilot Business | $— | per-seat × N seats | Annual contract; year-fraction allocated |
| Cursor Pro | $— | per-seat × N seats | Monthly |
| Claude API (team gateway) | $— | usage-based | From platform chargeback |
| LLM gateway infra (allocated) | $— | allocated | From platform |
| **Total** | **$—** | | |
| **Per engineer per quarter** | **$—** | ÷ N engineers | |
| **Per 100 PRs merged** | **$—** | ÷ (PRs merged / 100) | Links to dashboard Tile 5 |

This table, not a Google Sheet buried in an analyst's folder, is what you own. Exercise 03 produces the first version.

### Adoption vs activation: the distinction that separates theatre from substance

**Adoption** is *has this engineer been provisioned the tool*. A yes/no state; a count. "95% adoption" means 95% of engineers have access.

**Activation** is *is this engineer getting measurable value from the tool*. A continuous state; always depends on an operational definition. Candidate definitions you should pick one of:

- **Weekly-active-use** — "used Copilot in at least three distinct sessions this week." Cheap to measure, easy to game, modest signal.
- **Suggestion-acceptance-threshold** — "accepted at least K% of Copilot suggestions over the trailing 30 days." Grounded in [Ziegler et al.](https://cacm.acm.org/research/measuring-github-copilots-impact-on-productivity/) (Chapter 5); better signal than weekly-active.
- **Material-use** — "landed at least N PRs this quarter where agent-authored content was a declared contributor (per the `mod-103` provenance line)." High signal, requires `mod-103` discipline to measure, is the right instrument if you have it.
- **Flow-time contribution** — "the team's Flow-Time improvement for this engineer's workstream is attributable to agent contribution in >X% of items." Rarely practical at team scope; a stretch instrument.

Pick **one** per tool. Document the definition in the data-dictionary sidebar. Apply consistently.

**Why the distinction matters.** The gap between adoption and activation is almost always larger than first-time-measuring managers expect. A typical first measurement might show *adoption ~95%, activation ~40%* under a material-use definition. The remaining 55% breaks down further:

- *Never-tried* — minimal; usually ≤ 5%.
- *Tried-and-stopped* — significant; the honest signal of fit issues, friction, or wrong-tool-wrong-task mismatch.
- *Passive-use* — has the tool open; rarely engages substantively.

The *tried-and-stopped* cohort is the diagnostic. These are the engineers who gave it a real try and concluded, for their current work, it is not helping. Treat them as a signal, not as a rollout failure.

### What the cost denominator should look like on the dashboard

Chapter 2's Tile 5 — the AI-cost ratio tile — needs a *shape* that reads up to a VP without further explanation. Three shapes that work:

**Shape A — dollars per unit of output.** "$X in combined AI tool-spend per 100 PRs merged this quarter." Simple; the unit is tangible. The weakness is that PR count under-represents larger changes; use median-PR-size or feature-count as a sanity check.

**Shape B — AI spend as percentage of fully-loaded engineering cost.** "AI tool-spend was Y% of the team's fully-loaded headcount cost this quarter." The right denominator for a CFO audience; makes the tool-spend conversation a budget conversation, which is what it actually is.

**Shape C — AI spend per feature landed.** "$Z per feature closed in the Impact tile this quarter." Rarely the cleanest first number — feature count is noisy at team scope — but useful when the narrative is specifically about ROI on *new capability*.

Pick **one** as the top-line; carry the other two as supplements. The quarter-over-quarter trend is far more interpretable than the absolute number — your audience's intuition about "is $1,430 per 100 PRs a lot" is non-existent; their intuition about "$1,430 is ↑12% from last quarter and PR volume is ↑15%" is immediate.

### Token-cost tracking at team scope: what to actually instrument

The specific telemetry depends on your tool stack. Three patterns that cover most team setups.

**Pattern 1 — platform chargeback.** Your organisation has an internal LLM gateway (home-grown or via a vendor like LiteLLM, AWS Bedrock proxy, Azure OpenAI gateway). The gateway emits per-user / per-team usage events; the finance / platform function already produces a chargeback report. Your work: *read it; sanity-check it; reconcile it into the table above.* Do not rebuild the pipeline.

**Pattern 2 — vendor-side team dashboards.** The vendor exposes usage telemetry at team scope — Anthropic's console, OpenAI's org dashboards, Cursor's team console, Copilot's org admin, etc. Your work: assign a team-admin surface, bookmark the dashboards, add them to the Monday pre-read.

**Pattern 3 — DIY via engineer self-report.** Your team pays for tools individually and you reconcile via a monthly self-report. This is the weakest pattern and the one you should be moving *away* from — it is error-prone, under-counts, and does not scale beyond ~5 engineers.

**Instrumentation gotchas:**

- *Shared accounts.* Treat as a measurement failure. You cannot attribute cost; you cannot make activation decisions; roll back to per-user authentication.
- *Free-tier usage from personal accounts.* Hard to measure and often worth not measuring — the work is personal and the spend is the engineer's. But if a team member is routing company work through a personal Claude or ChatGPT account, that is a `mod-110` (governance) issue, not a mod-104 cost one.
- *Token-count vs. dollar-cost drift.* Token prices change; a 100k-token-per-week usage profile costs differently in 2025 vs 2026. Prefer dollar-cost as the primary number because that is what finance speaks; keep token-count as a secondary number for capacity planning.

### When to roll back the AI tool investment

A specific R4 phrasing — *"defend the AI tooling spend to leadership — including when to roll back"* — requires an explicit position. Rollback is not a failure state; it is a legitimate outcome of the measurement programme working. Four conditions, any one of which should trigger an explicit rollback conversation:

- **Activation below floor for two consecutive quarters.** If activation (material-use definition) has been below ~30% of adopted seats for six months, you are paying for licences the team is not using. Either re-validate the tool fit (`mod-102` jagged-frontier sort) or reduce the licence count.
- **Cost ratio moving the wrong way while quality tile is flat.** If the AI-cost tile is rising faster than output volume while the Quality tile is flat or degrading, the spend is not landing on the product line (Flow Efficiency, Chapter 4).
- **Change failure rate rising with agent-attributable incidents.** If change failure rate has risen for two consecutive measurement windows and the incident-attribution analysis in [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) consistently points at agent-generated work, rolling back the specific workflow (not the tool) is the right action. See Exercise 06.
- **Qualitative signal diverging from quantitative for two consecutive cycles.** If retro signal and 1:1 signal (Chapter 8) is persistently negative while the dashboard looks fine, the metric is lying. Investigate before celebrating.

A rollback-criteria document is a mod-104 deliverable. Exercise 06 produces it. The document's purpose is **not** to make rollback likely; it is to make rollback *possible* without a political crisis. Written criteria convert the question from *"are we rolling back"* (identity-laden) to *"did the pre-agreed condition fire"* (procedural).

### What this hands off to `mod-111`

Chapter 6 handles the *measurement* of tool-spend. Vendor selection, contract negotiation, and budget-category positioning are [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/)'s depth. The handoffs:

- *This chapter → mod-111:* you produce the reconciled spend-and-value table; mod-111 uses it for next year's budget planning and vendor-review cycle.
- *mod-111 → this chapter:* the vendor contract structure (seat count, usage caps, procurement cycle) determines what the "spend" line even is.

If you do not have a vendor-review mechanism yet, the artifact set in Exercise 03 is also the *seed* for it, and the mod-111 work flows naturally from the first time the reconciled number is produced.

### Common mistakes

- **Treating adoption as the top number.** Adoption is a provisioning metric; it has almost no ROI information. Dashboards that lead with adoption are theatre by Chapter 1's definition.
- **Inventing an activation definition that is easy to measure and low-signal.** If your activation metric is "opened Cursor this week," the number will always be flattering and never actionable.
- **Hiding the usage-based line because it is noisy.** Usage-based spend is noisy. Report it anyway; name the noise; the audience is smart enough to understand a trailing-30-day average.
- **Holding the cost line while headcount changes.** The cost ratio should normalise on engineer-weeks, not absolute spend. A team that doubled in size will see absolute AI spend double regardless of productivity; the ratio is what travels.
- **Treating the "tried-and-stopped" cohort as a rollout problem.** It is diagnostic. The right response is a 1:1 question (Chapter 8), not a nudge or a reminder email.

## Example: a two-paragraph spend reconciliation

Treat as calibration.

> **Q2 AI tool-spend reconciliation (engineering team, N = 14).** Combined spend: $19,860. Breakdown: Copilot Business ($4,620, 14 seats annual allocated), Cursor Pro ($2,520, 12 seats), Claude API via team gateway ($10,180, usage-based), LLM gateway infra allocated ($2,540). Per engineer per quarter: $1,419. Per 100 PRs merged: $1,432 (PRs merged Q2: 1,386). Fraction of fully-loaded engineering headcount cost: 1.1%.
>
> **Adoption vs activation.** Adoption (provisioned seats / engineers): 93%. Activation under the *material-use* definition (at least 3 PRs this quarter with declared agent-authored content): 64% for Copilot (9/14), 50% for Cursor (6/12), 71% for Claude via the team gateway (10/14). The "tried-and-stopped" cohort is 3 engineers, two of whom are on the data-pipeline workstream where the current tool choice does not fit the task mix (Dell'Acqua-style outside-frontier observation from Chapter 5); the third is a recent joiner who has not yet landed enough work to trip the material-use bar. No rollback criteria fired this quarter; see [`exercise-06`](exercises/exercise-06-rollback-criteria-and-what-we-got-wrong-drill.md) for the full criteria list.

Two paragraphs. Numbers are reconciled; activation is distinguished from adoption; the tried-and-stopped cohort is treated as a signal.

## Summary

- Three cost components to reconcile at team scope: **seat spend**, **usage-based token spend**, **platform / infra spend**. The reconciliation table is a mod-104 deliverable.
- **Adoption** (provisioned) and **activation** (measurably using) are different metrics. The gap is almost always larger than first-measurement managers expect. The *tried-and-stopped* cohort is the diagnostic.
- Dashboard shapes for the cost ratio: **$ per 100 PRs**, **% of fully-loaded eng cost**, **$ per feature**. Pick one top-line; report trend rather than absolute.
- Token-cost instrumentation patterns: platform chargeback (best), vendor team dashboards (good), self-report (minimal — move away from it).
- Four explicit **rollback triggers**: activation floor; cost ratio rising with flat quality; change failure rate rising with agent-attributable incidents; qualitative / quantitative divergence. Exercise 06 writes them down.
- Handoff to [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) is for vendor contract / budget-category work; mod-104 produces the reconciled spend-and-value number.
- Common traps: adoption as the top number; easy-but-low-signal activation definition; hiding noisy usage-based spend; non-normalised cost line; treating tried-and-stopped as a rollout failure.
