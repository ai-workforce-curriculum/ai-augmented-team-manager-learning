# Chapter 2 — The Copilot Landscape and the Evaluation Axes

> *A copilot bake-off that scores every tool on "do engineers like it" is a preference survey, not an evaluation. The five axes in this chapter — latency, output quality against your review standards, cost per seat, data handling against your inherited policy, extensibility against your real workflows — are what make the matrix defensible on a Tuesday when someone asks why you picked what you picked.*

## Motivation

The eight AI coding and knowledge-work copilots in scope — [Cursor](https://www.cursor.com/), [GitHub Copilot](https://github.com/features/copilot), [Claude Code](https://docs.claude.com/en/docs/claude-code), [Windsurf](https://windsurf.com/), [Continue](https://docs.continue.dev/), [Sourcegraph Cody](https://sourcegraph.com/docs/cody), [Zed](https://zed.dev/docs/ai), [JetBrains AI Assistant](https://www.jetbrains.com/ai/) — are positioned differently along several axes at once. Any single-dimension comparison ("which is fastest?", "which is cheapest?", "which engineers prefer?") produces a misleading ranking because the dimension it hides is the one that will matter for your team.

This chapter defines the five evaluation axes the module uses — chosen because each maps to a concrete team-scope artifact an audit will ask for — and describes the bake-off pattern that produces the Exercise 01 matrix without turning into a six-month-long comparative review.

The chapter does three things. First, it names the eight copilots and places them in three positioning tiers so the matrix is apples-to-apples per tier. Second, it defines the five evaluation axes precisely enough that two reasonable people would score the same tool the same way. Third, it specifies the bake-off protocol: how to run a one- or two-week trial that produces real evidence without drifting into a project in its own right.

## Core concepts

### Three positioning tiers

Comparing Claude Code to JetBrains AI Assistant on "how good is the completion quality" is a category error. They are not competing in the same slot. A sensible matrix separates tools into the tier they live in and scores within tier.

| Tier | What it is | Tools in scope |
|---|---|---|
| **Tier 1 — IDE-native assistant** | Code completion, inline edit, chat, ask-across-file; lives inside the editor and is used continuously while coding | [GitHub Copilot](https://docs.github.com/en/copilot) (plugin or IDE-integrated); [Sourcegraph Cody](https://sourcegraph.com/docs/cody); [JetBrains AI Assistant](https://www.jetbrains.com/ai/); [Continue](https://docs.continue.dev/) (open-source extension pattern) |
| **Tier 2 — Agentic IDE / IDE fork** | Full IDE with agent mode, multi-file edits as a first-class pattern, repo-wide planning, headless runs | [Cursor](https://www.cursor.com/) (VS Code fork); [Windsurf](https://windsurf.com/) (VS Code fork); [Zed](https://zed.dev/docs/ai) (native IDE with agent mode); [Claude Code](https://docs.claude.com/en/docs/claude-code) in IDE mode where provided |
| **Tier 3 — Terminal-native / headless agent** | CLI or API-driven agent; runs long-horizon tasks; can be scripted into CI, scheduled, or orchestrated; see Chapter 4 for overlap with agent-authoring environments | [Claude Code](https://docs.claude.com/en/docs/claude-code) (terminal); [OpenAI Codex CLI](https://github.com/openai/codex); the agentic runners inside [Cursor](https://docs.cursor.com/) and [Windsurf](https://windsurf.com/) when invoked headlessly |

Several tools straddle tiers. [Claude Code](https://docs.claude.com/en/docs/claude-code) ships both terminal and IDE-integrated modes; [Cursor](https://www.cursor.com/) is a Tier 2 IDE that exposes a headless Tier 3 pattern; [Zed](https://zed.dev/docs/ai) is a Tier 2 IDE with agent-mode features. Treat these as separate rows in the matrix *per tier the team actually uses them in* — the latency, quality, and data-handling profile differs between modes on the same product.

### The five evaluation axes

The axes are chosen because each one maps to a specific upstream policy or team artifact. An axis score that cannot be defended against the mapped artifact is not a score.

#### Axis 1 — Latency

**What to measure.** Two kinds: *completion latency* (time from keystroke pause to visible suggestion in Tier 1 tools) and *agent-turn latency* (time from prompt submission to usable output in Tier 2 and 3). For completion latency, the floor is perceptually ~200 ms; above ~600 ms the completion is competing with the engineer having already typed the line.

**How to measure.** Median and p95 over at least 100 representative requests per engineer per candidate — not vendor marketing figures. Recent public work on IDE-latency measurement from [JetBrains](https://blog.jetbrains.com/idea/2024/10/measuring-ai-assistant-performance/) and [Continue](https://docs.continue.dev/) documents conventions for logging; most mature tools now expose a telemetry panel that reports these.

**Why it maps.** Latency is the dimension *users* feel most directly. A completion assistant whose p95 is too slow is a Failure-B pattern from [`mod-105` Chapter 1](../mod-105-team-ai-enablement-programs/): the IC turns it off because it is in the way. The axis also surfaces vendor backend changes between evaluations — a quarterly re-measurement often shows the previous winner has regressed.

**Caveats.** Latency is not simply "the model." It is routing + model selection + context assembly + network + rendering. A tool that lets the team swap models (Continue, Cursor via custom API keys, Cody) can be tuned where a locked product cannot.

#### Axis 2 — Output quality against your review standards

**What to measure.** The rate at which the tool's output passes the team's own [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) review checklist on a fixed task set *without human iteration*. Pick ten to twenty representative tasks from the team's recent backlog (bug fixes, features, refactors, test writing, doc writing); run each candidate tool on each task; score the result against the checklist.

**How to measure.** Blind-score if possible — strip vendor identifiers from outputs before review. One rubric per task (checklist adherence, correctness, style compliance, test inclusion if required, no-hallucination-of-APIs). The team's existing checklist from [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) is the rubric; this is the whole point of standards-as-code. Public benchmarks ([SWE-bench Verified](https://www.swebench.com/), [LiveCodeBench](https://livecodebench.github.io/)) are *context*, not substitutes — they tell you what the ceiling looks like under optimised conditions; they do not tell you what performance your team sees on your codebase.

**Why it maps.** Review-standard adherence is the audit-grade quality signal. If the tool produces output your team has to rewrite to pass [`mod-103`](../mod-103-review-standards-and-eval-commissioning/), its real cost per useful PR is much higher than its headline per-token cost.

**Caveats.** On any given task, model quality is a moving target — vendors route and update continually. Lock the measurement window (one week), lock the model version where the product exposes selection, and document the measurement conditions.

#### Axis 3 — Cost per seat and cost per useful task

**What to measure.** *Headline cost per seat per month*, *projected token or usage cost per IC at your team's median*, and — the number that actually matters — *cost per useful task at your current success rate*. A cheap tool that produces half the useful tasks per hour of a tool twice as expensive is the more expensive tool.

**How to measure.** Public price lists for headline cost: [Cursor pricing](https://cursor.com/pricing), [GitHub Copilot pricing](https://github.com/features/copilot/plans), [Claude Code pricing](https://www.anthropic.com/pricing), [Windsurf pricing](https://windsurf.com/pricing), [Cody pricing](https://sourcegraph.com/pricing), [JetBrains AI pricing](https://www.jetbrains.com/ai/pricing/), [Continue](https://docs.continue.dev/) itself free with underlying model API cost, [Zed AI pricing](https://zed.dev/pricing). Token-based cost is projected from the bake-off's actual usage × the public per-token rate for the model routed. Cost per useful task comes out of Axis 2 (tasks that pass) divided by the cost of producing them.

**Why it maps.** The cost figure Chapter 5 distributes is the one the finance line sees. The AI-cost tile in [`mod-104` Chapter 2](../mod-104-productivity-measurement-and-ai-roi/) reads from this. A per-seat quote with no useful-task-per-seat context is a ROI-tile hazard; the tile will look bad in the second quarter when the headline cost is up and no narrative explains it.

**Caveats.** Enterprise tier pricing is often negotiated and non-public. The matrix assumes list prices for a first pass; after a procurement-led discussion the numbers often shift substantially, especially on multi-year commits (which this module *does not* decide — [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) at L45 does).

#### Axis 4 — Data handling against your inherited policy

**What to measure.** Each candidate's position against the organisation's [`mod-110` Chapter 6](../mod-110-ai-governance-and-policy-at-team-scope/06-data-ip-and-confidentiality-practice.md) data-class × tool-class matrix. Specifically:

- **Training on your data.** Does the vendor train or fine-tune foundation models on your inputs? Under which tier? With which opt-out? [GitHub Copilot's trust centre](https://resources.github.com/copilot-trust-center/), [Anthropic Enterprise](https://www.anthropic.com/enterprise), [OpenAI Enterprise privacy](https://openai.com/enterprise-privacy/), [Cursor privacy and security](https://cursor.com/security), [Sourcegraph Cody's data handling](https://sourcegraph.com/docs/cody/faq#does-cody-train-on-my-code) each publish a contractual position — but they publish it *per tier*, and the team's tier is the one that applies.
- **Retention.** How long are inputs and outputs retained? What is configurable? What is the team's configured retention? Zero-retention is contractually common at the Enterprise tier for Copilot, Claude Code, and Cursor; verify, do not assume.
- **Residency.** Where does the data physically live? Which jurisdictions have access? Subprocessors (see Chapter 6) on file?
- **Access and audit.** Who at the vendor can access the data? What logs are available? What audit rights are contracted?
- **Deletion.** How is deletion requested? Verified?

**How to measure.** Pull the vendor's published trust centre (GitHub, Anthropic, OpenAI, Cursor, Sourcegraph, JetBrains, Zed all publish one) and compare line-by-line to the inherited policy. For each clause, score *allowable / conditional / prohibited* per the data-class × tool-class matrix. A candidate that cannot be used for your most common restricted-data workflow is a candidate the matrix must score honestly, even if other axes look good.

**Why it maps.** Data-handling is the axis an audit will read first. If the registry entry has a green cell on data handling without a vendor-clause citation, the cell is unverified.

**Caveats.** Trust-centre pages change. Date the citation (quote the URL and the date you read it). The quarterly re-evaluation in Chapter 7 re-reads them.

#### Axis 5 — Extensibility against your real workflows

**What to measure.** Whether the candidate can be *composed* with the team's existing patterns, not just used as the vendor shipped it. Five specific sub-questions:

- **Custom-rules / standards-as-code support.** Can the tool read `.cursor/rules/`, `AGENTS.md`, `.github/copilot-instructions.md`, `continue.dev` rules, or equivalent, so the team's [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) standards flow into every prompt automatically? Rule-system support documentation: [Cursor rules](https://docs.cursor.com/context/rules), [GitHub Copilot custom instructions](https://docs.github.com/en/copilot/customizing-copilot/about-customizing-github-copilot-chat-responses), [Claude Code `AGENTS.md`](https://docs.claude.com/en/docs/claude-code/common-workflows), [Continue customization](https://docs.continue.dev/customize/overview), [Cody context](https://sourcegraph.com/docs/cody/core-concepts/context).
- **Tool / plugin / MCP support.** Does the candidate support the [Model Context Protocol](https://modelcontextprotocol.io/) or a comparable extension mechanism, so the team's internal tooling (CI, ticket system, data catalog, observability) can be plugged in? MCP support is now standard-ish across Claude Code, Cursor, Windsurf, Continue, Zed and others — confirm per vendor.
- **Model routing and selection.** Can the team pick which model routes to which task? Can the team bring its own key or its own hosted model? [Continue](https://docs.continue.dev/customize/model-providers/) is the most liberal here; vendor-locked products (JetBrains AI Assistant, Copilot default) are the most restrictive.
- **Headless / CI mode.** Can the tool be invoked non-interactively, from a script or CI job? Claude Code, Cursor's headless mode, and Codex CLI are the most mature here.
- **Observability.** Does the tool emit usage telemetry the team can read without vendor-dashboard-walled-garden friction? Usage is a Chapter 5 and `mod-104` input.

**Why it maps.** Extensibility is the axis that determines whether the tool is *yours* or *the vendor's*. A product that cannot be composed with the team's standards, tools, and patterns is a product the team is adapting to rather than using.

**Caveats.** The Chapter 3 *wrap* and *extend* stances live in this axis: a low-extensibility candidate may still be the right buy if wrapping it is cheap, or may be the wrong buy if wrapping would be expensive.

### Scoring and weighting

A matrix with five axes needs a scoring convention or the matrix becomes narrative.

- **Score per axis: 1–5.** 1 = disqualifying for this team; 3 = acceptable; 5 = best-in-class for your context.
- **Weight per axis: set in advance, not after.** A team doing long-horizon refactors weights extensibility and output-quality above latency. A team doing high-velocity feature work with many small iterations weights latency above extensibility. *Set the weights before running the bake-off* — otherwise the weights get pulled toward the preferred answer.
- **Data handling is a gate, not a weight.** If a candidate fails Axis 4 for your data classes, no amount of latency and quality score fixes it. The matrix marks it *out of scope* for workflows handling the failing data class and marks it available *only* for workflows handling data classes it satisfies.
- **Cost is a *post-score threshold*, not a weight.** Rank by the weighted score first, then ask "is the best option affordable?" and "would the second option be good enough at ⅔ the cost?" A composite score that bakes cost into the number washes out the real trade-off.

### The bake-off protocol

A bake-off is not a six-month evaluation project. The failure mode here is *the evaluation becomes the work*. The protocol:

**Duration.** Two weeks maximum per cohort of tools. If you cannot evaluate in two weeks, you have too many candidates — cut to three per tier.

**Cohort.** Three to five engineers, picked across stages per [`mod-105` Chapter 4](../mod-105-team-ai-enablement-programs/04-tool-budgets-by-learning-stage.md) (not all stage-3 engineers — a tool that works only for stage-3 users is a Failure-B pattern waiting to happen). Each engineer uses each candidate on a fixed task list drawn from the team's real backlog.

**Task list.** Ten to twenty tasks, pre-selected, across the team's representative workflow mix. Lock the list before the bake-off starts; do not amend during the bake-off. The task list is the eval set for this evaluation — same discipline as [`mod-103` Chapter 4](../mod-103-review-standards-and-eval-commissioning/) eval commissioning.

**Logging.** Each engineer logs, per task per candidate: completion latency (anecdotal is fine), agent-turn latency where relevant, whether the output passed the review checklist on first try (Axis 2), any data-handling flag that came up (e.g., "would have needed to paste restricted data"), and any extensibility friction (e.g., "the tool could not read our AGENTS.md").

**Review.** One 90-minute session at the end. Each engineer scores each candidate on the five axes using the predefined weights. Scores are visible; disagreements are discussed; the median or consensus score goes in the matrix.

**Output.** The Exercise 01 matrix, dated, with a recommendation for each tier and a re-evaluation date (default: one quarter out).

### What the chapter deliberately does *not* do

- **Does not rank the eight tools.** The ranking is team-specific and time-specific. A matrix published in curriculum would be out of date before the second cohort read it. The chapter supplies the axes; the Exercise 01 matrix supplies the ranking *for your team*.
- **Does not publish seat-cost numbers.** Prices move; multi-year enterprise rates differ from list; the matrix pulls current numbers from the pricing pages cited above at the time the evaluation runs.
- **Does not evaluate IDE-level engineer ergonomics beyond latency.** "Which IDE's keyboard shortcuts feel better" is a reasonable preference signal but not an evaluation axis. The chapter treats ergonomics as absorbed into Axis 1 (if slow enough to push the IC off) or Axis 5 (if the extension model breaks).
- **Does not cover self-hosted model economics.** Running [Continue](https://docs.continue.dev/) on a self-hosted open-weight model changes the Axis 3 cost model; the chapter notes it as a Chapter 3 *extend* stance and defers the deeper economics to `ai-infra-engineer` conversations.

## Example: a two-tier bake-off that produced a three-tool stack

A composite shaped example — calibration, not a case study.

> **Team.** 12 engineers at a mid-sized SaaS company. Primary workflows: feature work in a TypeScript / Go codebase; incident firefights; periodic large refactors.
>
> **Starting position.** Cursor Pro seats across the team; ad-hoc ChatGPT and Claude.ai use (no enterprise contract); one engineer "has been playing with Claude Code on the side."
>
> **Weights.** Discussed and pinned before the bake-off: Latency 0.15, Output quality 0.30, Cost 0.15, Data handling (gate, not weight), Extensibility 0.25, Ergonomics (bundled into Latency and Extensibility). Note weights are < 1 because data handling is a gate.
>
> **Task list.** 15 tasks: 5 feature additions of typical ticket size, 3 bug fixes, 2 refactors across ≥ 5 files, 2 test-writing tasks against existing code, 2 documentation tasks, 1 incident-playbook writing task.
>
> **Tier 1 candidates.** Cursor (as current baseline), GitHub Copilot Enterprise (available under org MSA), JetBrains AI Assistant (for the three engineers on IntelliJ).
>
> **Tier 2 candidates.** Cursor Business (current), Windsurf (new eval).
>
> **Tier 3 candidates.** Claude Code (terminal), OpenAI Codex CLI.
>
> **Results after two weeks (single-team scores — these are shaped illustrations, not published benchmarks).**
>
> - Tier 1: Copilot Enterprise and Cursor's inline completion score closely on Axis 1 (latency); Copilot's `copilot-instructions.md` support plus GitHub's SOC 2 and DPA posture gives it the Axis 4 and Axis 5 edge for standard feature work; JetBrains AI Assistant scores well for the three JetBrains users but does not change the team-wide answer.
> - Tier 2: Cursor's agent mode scores higher on Axis 5 extensibility (rules, MCP, model-swap) than Windsurf's at the time of evaluation; latency parity; Cursor wins the Tier 2 slot. Windsurf is parked with a one-quarter re-eval.
> - Tier 3: Claude Code wins on long-horizon agent tasks (Axes 2 and 5); Codex CLI scores well on scripted refactors, slightly behind on `AGENTS.md` adherence at time of eval. Claude Code takes the Tier 3 slot; Codex CLI is parked.
>
> **Decision.** Standardise on Cursor (Tier 2) + Copilot Enterprise (Tier 1) + Claude Code (Tier 3). JetBrains AI Assistant stays as an *IC-optional* for the JetBrains users (per the Chapter 4 standardise-vs-let-ICs-pick framing). Windsurf and Codex CLI re-evaluated in Q[N+1].
>
> **Budget and composition.** See Chapter 5 for distribution; Chapter 6 for due-diligence sign-offs on each.

Three tools in the stack, one re-evaluation booked, two parked candidates, a dated matrix.

## Summary

- The eight copilots in scope sit in three positioning tiers: **Tier 1 IDE-native assistants**, **Tier 2 agentic IDEs**, **Tier 3 terminal-native / headless agents**. Scoring compares within tier, not across.
- Five evaluation axes, each mapped to a concrete artifact: **latency** (user-ergonomics gate), **output quality** (review-standards adherence per [`mod-103`](../mod-103-review-standards-and-eval-commissioning/)), **cost** (seat + token + per-useful-task, consumed by [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/)), **data handling** (per [`mod-110` Chapter 6](../mod-110-ai-governance-and-policy-at-team-scope/06-data-ip-and-confidentiality-practice.md); a gate, not a weight), **extensibility** (rules, MCP, model routing, headless, observability).
- Scoring convention: 1–5 per axis; weights pinned before the bake-off; data handling is a disqualifier, not a tiebreaker; cost is a post-score threshold.
- The bake-off is **two weeks, a stage-mixed cohort of three to five engineers, ten to twenty real-backlog tasks, one 90-minute scoring review**. Longer evaluations become their own project and still produce stale results.
- The chapter **does not rank the tools**. The ranking is team-specific and time-specific; Exercise 01 produces the dated matrix for your team.
- The matrix output composes with Chapter 3 (build-vs-buy call per candidate), Chapter 5 (budget distribution per tool kept), Chapter 6 (due-diligence record per tool kept), and Chapter 7 (registry and re-evaluation cadence).
