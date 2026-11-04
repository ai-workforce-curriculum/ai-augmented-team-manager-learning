# Exercise 01 — Copilot Build-vs-Buy Matrix

**Estimated effort:** 2 hours.

## Objective

Produce **v0.1 of your team's copilot evaluation and build-vs-buy matrix**: the eight copilots in scope ([Cursor](https://www.cursor.com/), [GitHub Copilot](https://github.com/features/copilot), [Claude Code](https://docs.claude.com/en/docs/claude-code), [Windsurf](https://windsurf.com/), [Continue](https://docs.continue.dev/), [Sourcegraph Cody](https://sourcegraph.com/docs/cody), [Zed](https://zed.dev/docs/ai), [JetBrains AI Assistant](https://www.jetbrains.com/ai/)) scored against your team's context on the five evaluation axes, with a build-vs-buy stance per candidate and a dated re-evaluation.

The matrix is the input to Chapter 5's budget distribution, Chapter 6's due diligence (for any tool scored high enough to merit records), and Chapter 7's tool registry. The methodological anchors are [Chapter 2](../02-copilot-landscape-and-evaluation-axes.md) for the axes and [Chapter 3](../03-build-vs-buy-matrix-at-team-scope.md) for the four stances.

## Prerequisites

- [Chapter 1](../01-the-vendor-selection-problem-at-team-scope.md) — the five pieces of mod-111 and the scope boundary.
- [Chapter 2](../02-copilot-landscape-and-evaluation-axes.md) — the three positioning tiers, the five evaluation axes, the bake-off protocol.
- [Chapter 3](../03-build-vs-buy-matrix-at-team-scope.md) — the four stances and the decision checks.
- Prior-module artifacts your team has produced:
  - [`mod-103`](../../mod-103-review-standards-and-eval-commissioning/) review checklist — the Axis 2 output-quality rubric.
  - [`mod-105` Chapter 4](../../mod-105-team-ai-enablement-programs/04-tool-budgets-by-learning-stage.md) — the stage distribution of your team.
  - [`mod-106` Chapter 3](../../mod-106-workflow-redesign-and-agent-delegation/) tool-authorisation policy — the current list of allowed tools.
  - [`mod-110` Chapter 6](../../mod-110-ai-governance-and-policy-at-team-scope/06-data-ip-and-confidentiality-practice.md) data-class × tool-class matrix — the Axis 4 data-handling gate.
- Access to current vendor pricing and trust-centre pages for the eight candidates; links in [`resources.md`](../resources.md).
- 30 minutes with your procurement or [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) contact (or their delegate), if one exists, to confirm which candidates are available under the org's current enterprise framework.
- A representative task list of 10–20 real-backlog items for the bake-off (see Chapter 2).

## Problem statement

Your team runs some AI-coding and AI-assisted-knowledge-work tooling. Whichever tools are in use today, they are probably a mix of deliberate adoption and drift. Chapter 2's three failure modes — default-tool drift, early-lock enterprise commit, governance theatre — apply to most teams. The matrix is the artifact that replaces "whichever tool happens to be installed" with a defensible, dated selection.

The scope is *evaluation and stance*, not procurement — a candidate scored high enough to recommend still has to go through Chapter 6's due-diligence process before it is a production tool. Similarly, a candidate scored *not right now* is not permanently out; the matrix is re-run on the Chapter 7 cadence.

The common failure mode the exercise prevents: a matrix that scores every candidate as "pretty good overall" and makes no sharp recommendation. A matrix with weighted scores, a data-handling gate, and an explicit stance call is what an audit will accept; a vibes-document will not.

## Steps

1. **Pin the five axis weights before the bake-off.** Discuss with the team. Latency weight, output-quality weight, cost weight, extensibility weight. Data handling is a gate, not a weight (per Chapter 2); do not include it in the weight sum. Record the weights with a one-sentence rationale per weight. Pin before the bake-off runs; do not amend during.
2. **Lock the bake-off task list.** 10–20 representative tasks from recent backlog: feature work, bug fixes, refactors, tests, docs, one incident-playbook-style task. The list is the eval set — same discipline as [`mod-103` Chapter 4](../../mod-103-review-standards-and-eval-commissioning/) commissioning. Do not amend during the bake-off.
3. **Pick the bake-off cohort.** 3–5 engineers, deliberately mixed across [`mod-105`](../../mod-105-team-ai-enablement-programs/) stages (not all stage-3+). Stage-1 and stage-2 engineers participating is a load-bearing part of the protocol — a tool that only works for stage-3+ engineers is a Failure-B pattern waiting to happen.
4. **Narrow the candidate list per tier.** All eight candidates do not need to be bake-off'd simultaneously. Pick:
   - Tier 1 — up to 3 candidates (e.g., current Tier 1 + 2 alternatives).
   - Tier 2 — up to 3 candidates.
   - Tier 3 — up to 3 candidates.
   Tools your org has no master agreement with and no path to one (consumer-tier only) are *disqualified* at this stage, not evaluated.
5. **Run the bake-off.** Two weeks maximum. Each engineer uses each candidate on the locked task list, logs per task: completion latency (anecdotal fine), agent-turn latency, pass-on-first-try against [`mod-103`](../../mod-103-review-standards-and-eval-commissioning/) checklist, any data-handling flag, any extensibility friction.
6. **Score Axis 4 (data handling) per candidate.** Pull the vendor's current trust-centre page and DPA position for the tier you would contract on. Score each candidate as *allowable / conditional / prohibited* per data class in your [`mod-110` Chapter 6](../../mod-110-ai-governance-and-policy-at-team-scope/06-data-ip-and-confidentiality-practice.md) matrix. Any candidate prohibited for your most common workflow's data class is a *gated-out* candidate even if other axes look strong.
7. **Run the scoring review.** One 90-minute session. Each engineer scores each candidate 1–5 per axis using the pre-pinned weights. Discuss disagreements. Median or consensus score per cell. Produce the weighted total per candidate per tier; the data-handling result is a gate overlay.
8. **Make the stance call per candidate** per Chapter 3's four-check decision tree: Buy / Wrap / Extend / route upward for Build. Candidates that lose on the matrix exit as *parked* (re-evaluated next quarter) or *disqualified* (not coming back without a specific signal).
9. **Draft the per-tier recommendation.** Which tool for Tier 1, Tier 2, Tier 3. Any tools kept as *IC-optional* parallel per the Chapter 4 standardise-vs-let-ICs-pick framing. Any tools in *trial* state going forward.
10. **File the matrix.** Dated. Link to the task list, the per-engineer score sheets, the vendor-clause screenshots (not just URLs — vendor pages change). Register the Chapter 7 next-review date (default: one quarter).
11. **Validate with one worked prompt.** Pick one candidate recommended for *buy* or *wrap*. For one task on the bake-off list, re-run the task against the candidate *with the proposed stance's config* (e.g., if the stance is wrap, with the planned `.cursor/rules/` or `AGENTS.md` in place). Confirm the stance actually closes the gap the evaluation identified.

## Starter guidance

- **Weights must be pinned before the bake-off.** If weights move after the scores come in, the matrix is retroactively justifying a preferred answer, not evaluating. Pin, record the rationale, do not amend.
- **Data handling is a gate, not a weight.** A candidate that fails Axis 4 for your common workflow's data class does not get rescued by high scores on latency and quality. Mark gated-out explicitly.
- **Cite the tier, not the brand.** "Claude Code (Pro consumer tier)" and "Claude for Work (Enterprise)" have different data postures. The matrix row is the *tier*, not the product name.
- **Vendor-clause screenshots.** Trust-centre pages change. For every Axis 4 citation, capture a dated screenshot or page-archive link alongside the URL. The Chapter 7 next-review re-reads from the current page; the screenshot is what the audit reads.
- **The task list is the eval set.** Treat it with eval-commissioning discipline: representative, locked, not amended mid-run. A matrix whose task list changed mid-bake-off is not a defensible matrix.
- **Stage-mixed cohort is mandatory.** A tool evaluated only by stage-3+ engineers tends to score well and then land badly for the stage-1 and -2 cohort. The Chapter 1 Failure B trap is exactly this.
- **Candidates your org cannot contract with.** Consumer-tier-only candidates (a vendor your org has no enterprise path for) are *disqualified* before the bake-off, not evaluated. Record the disqualification so the matrix shows why that candidate is not in scope.
- **The stance call is per candidate, not per team.** You may Buy one and Wrap another and route a Build request upward for a third. The stance diversity is normal and defensible.
- **Do not duplicate due-diligence work.** For every candidate recommended for Active status, the full due-diligence record (Exercise 04) is produced next; the matrix's Axis 4 cites Exercise 04's draft where available.

## Acceptance criteria

The matrix is complete when:

- Weights for latency, output quality, cost, extensibility are pinned with a one-sentence rationale each; data handling is handled as a gate.
- The bake-off task list is locked, dated, representative across the team's workflow mix.
- At least three candidates per tier (or an explicit note on why fewer) were scored by a stage-mixed cohort over no more than two weeks.
- Axis 4 cites the specific vendor-clause URL *plus* a dated screenshot per candidate, for the tier the team would contract on.
- A weighted score per candidate per tier is produced, with the data-handling gate overlay.
- A stance call per candidate exists per Chapter 3's four-check tree — Buy / Wrap / Extend / route upward.
- A per-tier recommendation is written with at least one line of rationale citing specific scores.
- Any IC-optional tool (per Chapter 4 framing) is explicitly named.
- Any Trial-status candidate is dated with a deadline.
- The matrix is filed at a canonical location in the team's wiki or registry with the dated next-review marker.
- A change-log entry names authors, reviewers, and the date. v0.1.

## Stretch goals

- **Workflow-aware Axis 2 scoring.** Where the team has distinct workflow categories (feature work, refactor, incident, docs), score Axis 2 per category rather than as one average. Different candidates often win different categories; the matrix result can drive a multi-tool stack rather than one-tool-fits-all.
- **Pilot the recommended stance.** For the top-ranked Tier 2 candidate under a Wrap stance, author the *actual* wrap artifacts (rules file, `AGENTS.md`, slash commands) and run a one-week post-matrix pilot with 2–3 ICs. The pilot evidence feeds the Chapter 7 registry entry and tightens the Chapter 5 budget projection.
- **Cross-reference with [Exercise 02](exercise-02-agent-framework-selection-matrix.md).** Any Tier 3 candidate overlaps with the agent-authoring-environment matrix in Exercise 02. Ensure the two matrices agree on Tier 3 — if Exercise 01 recommends Claude Code and Exercise 02 recommends Codex, resolve the conflict explicitly before filing both.
- **Published-benchmark overlay.** For Axis 2, add a column with the most relevant public benchmark result for each candidate's underlying model ([SWE-bench Verified](https://www.swebench.com/), [LiveCodeBench](https://livecodebench.github.io/)). Treat the benchmark as *context on the ceiling*, not a substitute for your team's task-list score. Document the discrepancy if your team's score and the public benchmark diverge.
- **Finance partner read-out.** Produce a one-page finance-partner-facing version of the matrix: tier choice, headline cost per tier, projected cost per 100 PRs merged (composed with the [`mod-104` Chapter 2](../../mod-104-productivity-measurement-and-ai-roi/) tile). Use it to pre-align the Chapter 5 budget distribution.
