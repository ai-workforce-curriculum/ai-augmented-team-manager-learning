# Chapter 5 — Tool and Token Budget Distribution Aligned with Enablement Stage

> *A team budget is three allocations layered — seat budgets, token budgets, and enterprise commitments. Each of them has to answer to the stage ladder, not seniority. [`mod-105` Chapter 4](../mod-105-team-ai-enablement-programs/04-tool-budgets-by-learning-stage.md) made the case; this chapter operates the composed allocation across the three layers and ties the bottom line into the [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) cost tile a finance partner can read.*

## Motivation

Budget distribution is where every prior chapter becomes a line item. The Chapter 2 bake-off said which tools are in; Chapter 3 said how deep the ownership on each goes; Chapter 4 said which framework and environment to standardise on. Chapter 5 is the allocation: who gets which seat, who gets which token allowance, which tools consume the team's share of an enterprise commit, and what the team's finance-partner-facing total looks like.

Two upstream constraints frame the work:

- **[`mod-105` Chapter 4](../mod-105-team-ai-enablement-programs/04-tool-budgets-by-learning-stage.md) set the distribution shape**: everyone gets the seat (even stage-1); usage budgets vary by stage; stage-3 runs at team median; stage-4 is uncapped with a quarterly review. The research anchor — [Brynjolfsson, Li, Raymond, *Generative AI at Work* (NBER 31161)](https://www.nber.org/papers/w31161) — found productivity gains concentrated in lower-tenure workers, which maps to stage ladder, not seniority ladder. [Dell'Acqua et al., *Navigating the Jagged Technological Frontier* (BCG + HBS, 2023)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321) adds the symmetric warning: top performers who used AI uncritically could lose ground.
- **[`mod-104` Chapter 2](../mod-104-productivity-measurement-and-ai-roi/) AI-cost tile consumes this chapter's numbers.** The composed metric — *$X in tool spend per 100 PRs merged* — reads from Chapter 5's distribution. A seniority-shaped allocation inflates the ratio; a stage-shaped allocation produces a ratio that decreases *as the cohort moves through stages*. The tile narrative is honest only if the spend side is honest.

This chapter does three things. First, it names the **three allocation layers** (seat, token, enterprise commit) and how each is distributed. Second, it walks through the **finance-partner-facing projection** that makes the bottom line defensible. Third, it names the **monthly usage review** and the signals it watches — the opposite-direction signals for stages 1–2 (floors) and stages 3–4 (ceilings).

## Core concepts

### The three allocation layers

The budget is not one number. It is three allocations that stack:

| Layer | What it is | How it scales | Primary input |
|---|---|---|---|
| **Seat budget** | Per-IC per-month per-tool licence fees for tools that charge per seat (Cursor, Copilot, JetBrains AI, some Cody tiers) | Linear in headcount; everyone gets the seats they need | Chapter 2 matrix + Chapter 4 framework / environment choice |
| **Token (usage) budget** | Per-IC per-month allowance for usage-based pricing (Claude Code, OpenAI API usage behind Codex / custom agents, Cursor usage overage, GitHub Models usage) | Varies by stage; uncapped at stage 4 with review | [`mod-105` Chapter 4](../mod-105-team-ai-enablement-programs/04-tool-budgets-by-learning-stage.md) stage ladder |
| **Enterprise commitment** | Multi-month or multi-year committed-spend and committed-seats contracts that lower per-unit cost at the cost of commitment risk | Multi-quarter planning; team-share of org commit | [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) at L45; the team is a consumer, not an architect |

A clean budget plan expresses all three layers separately and sums them. A plan that expresses only one layer (e.g., "the team is $8k/month on AI tools") is a line item, not a plan.

### Seat budget distribution

Seat budget is the easiest layer because the rule from `mod-105 Ch. 4` is clean:

- **Everyone on the team gets the seats the tool registry requires for their work.** No earn-the-seat ladder. The Chapter 2 bake-off may have determined that the stack is Cursor + Copilot Enterprise + Claude Code; each of those that requires a seat gets one per IC that uses the tool.
- **Role-shaped exceptions are explicit.** If three ICs are on IntelliJ and the rest on VS Code, the JetBrains AI seats go to the three — this is a workflow-shaped allocation, not a stage one. Record the shape in the registry.
- **Headcount changes cascade automatically.** New hire = seats on the stack. Rotation off the team = seats reclaimed within a named window (e.g., two weeks). The reclamation discipline is the main source of seat-budget drift if it is not named.
- **Trial seats are a named sub-category.** During a Chapter 2 bake-off, 3–5 engineers get a time-boxed seat on a candidate tool. The seat is categorised as *trial*, not *production*, so the finance line tracks it separately and the trial has an end date.

### Token budget distribution

Token budget is where [`mod-105` Chapter 4](../mod-105-team-ai-enablement-programs/04-tool-budgets-by-learning-stage.md)'s stage ladder lands. Repeating the ladder here because this chapter operates against it:

| Stage | Description | Token-budget shape |
|---|---|---|
| **Stage 1** — Never used in work context | Soft floor (~50 tasks/month or vendor-equivalent). No cap. Engineer in-cohort on the mod-105 programme. |
| **Stage 2** — Side-project / exploratory use at work | Soft floor (~100 tasks/month). No cap. First-successful-PR-with-tool target in Day 30. |
| **Stage 3** — Shipping production work | Run at team median usage. Monthly review on the [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) tile. |
| **Stage 4** — Teaching + pattern-contributing | No cap, quarterly review threshold (e.g., 3x team median triggers a conversation). |

The chapter's specific operating detail: **floors are a review signal, not a procurement signal**. If a stage-2 engineer is at 20 tasks/month instead of 100, that is not a budget-reduction trigger; it is a 1:1 signal that the engineer may be stuck on Failure-B ([`mod-105` Chapter 1](../mod-105-team-ai-enablement-programs/)) — the tool is in the way, the engineer has turned it off, the mod-105 programme is not landing for them. Reduce the budget on *data*, not on *underuse*.

**Per-tool token budget vs per-IC token budget**: most vendors meter per-seat, not per-tool across a team. The budget is defined per IC per tool. A stage-3 engineer at team median on Claude Code and running Cursor agent mode heavily will have usage on both; the per-tool accounting is what rolls up into the Chapter 7 registry.

**The finance-partner-facing total** is the sum of expected-usage-at-median times stage distribution plus a stage-1-and-2 floor allowance. A worked projection pattern:

```
Team size: 12 engineers
Tool: Claude Code (usage-based)
Stage distribution: 3 at stage 1, 4 at stage 2, 4 at stage 3, 1 at stage 4
Team median monthly spend at stage 3: $120/engineer
Stage-1 floor: $40/engineer (vendor-equivalent of 50 tasks)
Stage-2 floor: $80/engineer (vendor-equivalent of 100 tasks)
Stage-3 running: $120/engineer (median)
Stage-4 ceiling: $360/engineer (3x median; review beyond)

Projected monthly spend:
  3 × $40 (stage 1) = $120
  4 × $80 (stage 2) = $320
  4 × $120 (stage 3) = $480
  1 × $360 (stage 4 ceiling) = $360
  Total: $1,280/month

Narrative to finance:
  "Stage distribution will shift over Q[N] as the mod-105 cohort progresses.
   Expect spend to rise ~25% in Q[N+1] as 3 stage-1 ICs move to stage 2 and
   2 stage-2 ICs move to stage 3. The rise is the enablement programme working,
   not budget drift. The ratio of spend to PRs-merged is tracked in the
   mod-104 AI-cost tile; it will decrease as the cohort matures."
```

The *projected rise* is the honest signal and the narrative that makes it defensible. A budget that only reports current spend without the stage-shift projection will produce a finance conversation every quarter that reads as drift when it is actually the programme landing.

### Enterprise commitment handling

Enterprise commitments — multi-month or multi-year committed-use agreements with volume pricing — are not team-scope decisions. They are org-scope decisions owned by [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) at L45 and procurement. The team is a *consumer* of the commitment and a *contributor of usage evidence* to it.

The team-scope deliverables around enterprise commits:

- **Reading the commitment.** The team knows which vendors have enterprise commits, what the committed spend and committed seats are, what the overage clause looks like, and what the exit cost is. The information lives in the Chapter 7 tool registry; the source is procurement.
- **Honouring the shape.** If the org has committed to $X of OpenAI usage per quarter, the team's token budget distribution should land inside that shape rather than fighting it. If the team's budget distribution would systematically under- or over-consume the commit, the manager flags upstream for renegotiation input.
- **Contributing usage evidence.** The quarterly commitment review by [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) reads from each team's usage patterns. The team contributes clean, dated per-tool usage figures (not "roughly how much we spent") into that review.
- **Flagging the exit risk at commit time.** If procurement is negotiating a new commit the team will consume, the manager contributes a pilot evaluation (Chapter 2) and a sunset-cost reading (Chapter 3) into the pre-sign conversation. The manager does not sign; the manager does not abstain from informing the sign.

The failure mode this prevents: a team that silently uses zero of a committed vendor's product because the org committed to it a year ago and the team's workflow has moved on. That is an $X/quarter stranded cost. The commit review is where the stranded-cost conversation happens.

### Monthly and quarterly usage review

Two cadences on different axes:

**Monthly** — the usage review the manager reads. Three signals:

- **Floor signal** on stages 1–2. Are stage-1 and stage-2 engineers landing on the floor or undershooting it? Undershoot is a mod-105 programme signal, not a budget signal.
- **Median signal** on stage 3. Is stage-3 spend tracking team-median? Significant drift (e.g., one stage-3 engineer at 3x median) is a conversation, not a cap.
- **Ceiling signal** on stage 4. Is stage-4 usage inside the quarterly-review ceiling? Breach is a conversation — pattern-building (good, feed into [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) narrative) or a side project on the corp licence (less good).

**Quarterly** — the registry review (Chapter 7) that reads from the monthly data. Three decisions:

- **Stage re-pin.** Every IC's stage per tool is reassessed per [`mod-105` Chapter 4](../mod-105-team-ai-enablement-programs/04-tool-budgets-by-learning-stage.md). The usage data is one input; the IC's judgement conversation is another. A stage pin that never moves is a lapsed instrument.
- **Tool keep / sunset decision.** For each tool in the registry, does the usage pattern justify keeping the seats and token allowance for next quarter? A tool with half the team at stage-1-floor and no stage-3 or -4 users is a candidate for sunset — the demand did not materialise.
- **Enterprise-commit shape input.** The team's usage figures feed into the org-level commitment review.

### Interaction with the `mod-104` AI-cost tile

The [`mod-104` Chapter 2](../mod-104-productivity-measurement-and-ai-roi/) AI-cost tile reads from this chapter's budget. The connection is explicit:

- The tile is **cost per 100 PRs merged** (or whatever PR-equivalent unit the team uses).
- The *cost* numerator is Chapter 5's monthly spend (seat + token, rolled up).
- The *PRs merged* denominator is the team's output signal.
- The *trajectory* the tile tells is the one Chapter 5's stage-shift projection anticipates — the ratio *rises* in the first two quarters of a mod-105 programme (more usage per PR as learners ramp) and *stabilises* as the cohort matures (same usage producing more PRs).

A finance partner reading the tile without the stage-shift projection sees a ratio moving against the team in Q1-Q2. With the projection, the partner sees the programme landing. The Chapter 5 budget distribution is what makes the tile's story honest.

### What this chapter deliberately does *not* do

- **Does not re-derive the stage ladder.** The ladder is in [`mod-105` Chapter 4](../mod-105-team-ai-enablement-programs/04-tool-budgets-by-learning-stage.md). This chapter operates it against the composed budget.
- **Does not architect enterprise commits.** Multi-year committed-use architecture belongs to [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) and procurement.
- **Does not cover self-hosted inference economics.** If the team runs agents against a self-hosted open-weight model, the cost model collapses into GPU-time rather than per-token; that is a `ai-infra-engineer` conversation and a Chapter 3 *extend* stance.
- **Does not integrate with comp or performance review.** The stage pin is a learning signal, not a performance signal (per [`mod-105` Chapter 4](../mod-105-team-ai-enablement-programs/04-tool-budgets-by-learning-stage.md)). Keeping the two separate is a load-bearing discipline.

### Common mistakes when first distributing

- **Seniority-shaped token caps.** "Juniors capped at 500k tokens/month, seniors at 5M" is the single most common anti-pattern. Reinstates Failure-B on the junior cohort and funds the stage-1 senior cohort against the slope. See [`mod-105` Chapter 4](../mod-105-team-ai-enablement-programs/04-tool-budgets-by-learning-stage.md).
- **One-number-to-finance.** Rolling seats + tokens + enterprise-share into one line without the three-layer breakdown is a finance-partnership weakness; when one layer moves, the partner cannot see why.
- **No stage-shift projection.** A budget that reports only current state projects as flat. The Chapter 5 projection is what makes the mod-104 tile's narrative defensible.
- **Opaque stage pins.** If ICs do not see the rubric and the pin, the budget conversation reads as arbitrary. The pin conversation is explicit per [`mod-105` Chapter 4](../mod-105-team-ai-enablement-programs/04-tool-budgets-by-learning-stage.md).
- **Caps on stages 1–2.** Caps on learning-stage ICs starve the mod-105 programme of the exploratory time it needs. The right signal here is *floors*, not ceilings.
- **Uncapped stage 4 with no review.** The quarterly review threshold is the guard against "one engineer runs a side project on the corp licence."
- **No trial category.** Bake-off seats that silently become production seats drift the budget. Category and date the trial seats.

## Example: a composed budget for a 12-person team

A composite shaped example — calibration, not a template.

> **Team.** 12 engineers at a mid-sized SaaS.
>
> **Tool registry (from Chapter 2, 3, 4).** Cursor Business (Tier 2, wrap), Copilot Enterprise (Tier 1, buy), Claude Code (Tier 3, extend — includes an internal MCP server). Framework: LangGraph standard. Authoring environment: Claude Code standard + Cursor permitted.
>
> **Stage distribution after Q[N] pins (per [`mod-105`](../mod-105-team-ai-enablement-programs/) ladder, per tool).**
> - Cursor: 2 stage-1, 5 stage-2, 4 stage-3, 1 stage-4.
> - Claude Code: 5 stage-1, 4 stage-2, 2 stage-3, 1 stage-4.
> - Copilot: 1 stage-1, 4 stage-2, 6 stage-3, 1 stage-4.
> - LangGraph: 8 stage-1, 2 stage-2, 1 stage-3, 1 stage-4. (The framework is newer to the team.)
>
> **Seat budget layer.**
> - 12 × Cursor Business seats.
> - 12 × Copilot Enterprise seats.
> - Claude Code is usage-based (no per-seat).
> - LangGraph is open-source (no seats).
> - Trial seats: 1 × Windsurf (parked from Chapter 2 re-eval).
>
> **Token budget layer (Claude Code, as the most usage-dominant).**
> - Stage-1 floor ($40 × 5): $200.
> - Stage-2 floor ($80 × 4): $320.
> - Stage-3 median ($120 × 2): $240.
> - Stage-4 ceiling ($360 × 1): $360.
> - Total Claude Code projected: $1,120/month.
>
> **Cursor usage overage projection.** Business seats include usage but overage is possible; conservative projection ~$200/month total across stage-3 and -4 users.
>
> **Enterprise commitment handling.** Copilot Enterprise is on the org's annual commit ([`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) owned). Team's share: 12 seats × $N/month. Usage telemetry contributed to the quarterly commit review.
>
> **Finance-partner-facing total.** Three layers broken out separately. One-paragraph narrative referencing the stage distribution and the projected shift over Q[N+1].
>
> **Monthly review.** Floor-and-ceiling signals; three ICs flagged for mod-105 programme attention (stage-2 undershoot); no stage-4 ceiling breach.
>
> **Quarterly inputs to Chapter 7 registry.** All three tools retained. Windsurf sunset (parked candidate did not materialise demand after one quarter). Stage distribution shift documented; expected to produce ~25% usage rise in Q[N+1], correctly framed as programme-landing in the mod-104 narrative.

Twelve engineers, three tools, three allocation layers broken out separately, a dated projection, a finance-partner-readable narrative, a monthly and quarterly cadence.

## Summary

- Budget is **three layers**: seat budget (linear in headcount), token budget (stage-shaped per [`mod-105` Chapter 4](../mod-105-team-ai-enablement-programs/04-tool-budgets-by-learning-stage.md)), enterprise commitment (org-scope; team consumes). Each layer is reported separately to finance.
- **Seat budget**: everyone gets the seats their workflow requires. No earn-the-seat ladder. Trial seats are a named sub-category with a dated end.
- **Token budget**: distributed by stage per the [`mod-105` Chapter 4](../mod-105-team-ai-enablement-programs/04-tool-budgets-by-learning-stage.md) ladder — floors at stages 1–2, median at stage 3, quarterly-reviewed ceiling at stage 4. Floors are a programme signal, not a procurement signal.
- **Enterprise commits** are owned by [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) at L45. The team *reads* the commit shape, *honours* it, *contributes usage evidence* to its review, and *flags exit-risk* at commit time.
- The **finance-partner-facing total** includes a stage-shift projection; the projected rise is the programme working, not budget drift. The [`mod-104` Chapter 2](../mod-104-productivity-measurement-and-ai-roi/) AI-cost tile narrative is defensible only with this projection.
- **Monthly review** watches floor signals (stages 1–2), median signals (stage 3), ceiling signals (stage 4). **Quarterly review** re-pins stages, decides tool keep / sunset, contributes commit-shape input.
- **Common mistakes**: seniority-shaped caps; one-number-to-finance; no stage-shift projection; opaque pins; caps on stages 1–2; uncapped stage 4 without review; silently-production trial seats.
- Exercise 03 produces the composed budget distribution for your team.
