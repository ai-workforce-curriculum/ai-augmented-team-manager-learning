# Chapter 4 — Tool Budgets Follow Learning Stage, Not Seniority

> *A senior engineer who has never used an agent is a day-5 learner on that agent. Giving them the heaviest token budget on your team is budget allocated against the slope.*

## Motivation

R5 is explicit on the budget-side distribution: *"pick and distribute tool budgets (Cursor seats, Copilot seats, token allowances) in a way that mirrors learning stage, not seniority alone."* This is a non-obvious load-bearing move. The default allocation a manager inherits from pre-AI tooling is seniority-shaped — senior engineers get the top-tier IDE, more compute, more licences. That shape is wrong for AI tooling in a specific way that this chapter makes operational.

Two research anchors ground the rule:

- [Brynjolfsson, Li, Raymond, *Generative AI at Work* (NBER Working Paper 31161)](https://www.nber.org/papers/w31161) found generative-AI productivity gains concentrated at **lower-tenure** workers in a contact-centre deployment — not at the senior cohort. A seniority-shaped budget allocation funds the cohort where returns are smallest.
- [Dell'Acqua et al., *Navigating the Jagged Technological Frontier* (BCG + HBS, 2023)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321) found that top performers who used AI uncritically could **lose ground**, while lower performers who used AI appropriately gained most. Allocation by seniority therefore funds the population most at risk of mis-use alongside the population most likely to benefit — identically, without a learning-stage signal to shape either experience.

The implication is not "junior engineers deserve more tooling than senior engineers." The implication is: *the signal on which to allocate is stage, not title.* A senior engineer at stage 1 on Claude Code needs a different budget shape than a senior engineer at stage 3 on Claude Code, and the Chapter 2 Day-0 stage pin is the input into the shape.

This chapter sketches the budget-side rubric. Exercise 02 lands the rubric for your specific team.

## Core concepts

### The four-stage ladder and what it funds

The Chapter 1 stage ladder (1–4 per tool category) carries into the budget rubric. The four stages and what each stage calls for in budget terms:

| Stage | Description | Budget shape |
|---|---|---|
| **Stage 1 — Never used in a work context** | The engineer has not opened the tool in a real-work setting, or has opened it twice and bounced. | Full seat allocated; usage *budget expected to be low* (they are learning to open the door). Pair with a stage-3 mentor (Chapter 3). No pressure on token spend. |
| **Stage 2 — Used in side projects, exploratory use at work** | The engineer has used the tool but has not shipped production work with it. | Full seat; usage budget *gradually ramping*. First-successful-PR-with-tool (Day 30 of mod-105 cohort) is the leading indicator. |
| **Stage 3 — Shipping production work with the tool, approvingly** | The engineer uses the tool daily in production work, with judgment. | Full seat; usage budget *at team median or above*. Pair-with-mentor volunteer. |
| **Stage 4 — Teaching + pattern-contributing** | Shipping, teaching others, contributing patterns to the CoP's pattern library (Chapter 3). | Full seat; usage budget *uncapped within team policy*. Formal recognition of the pattern work in mod-108 performance framing. |

The shape: everyone gets the seat (or token access). The *expected usage* varies. The budget line to leadership is the sum of seats + the sum of usage; the sum of usage is projected using stage distribution, not a flat per-engineer assumption.

### Why everyone gets a seat even at stage 1

Three reasons:

- **Door-opening friction.** A stage-1 engineer who does not have the seat cannot cross into stage 2. "Earn the seat by proving you'll use it" is a budget policy that mathematically guarantees stage-1 engineers stay there.
- **Cohort coherence.** The Chapter 2 cohort runs through bootcamp together. If two of five cohort members don't have seats, the bootcamp is broken by construction.
- **Equity signal.** Seat allocation is visible. Allocating seats by seniority or by prior usage is a signal engineers read as "the manager thinks the learners don't deserve the tool." That signal corrupts the programme before it starts.

What *does* vary is the **usage budget** (tokens, request volume) when the vendor pricing is usage-based. Chapter 1's Failure B (the licence drop) is prevented by the Day-0 stage pin + the Day-30 PR checkpoint; it is not prevented by withholding seats.

### Handling usage-based pricing (tokens, request volume)

Cursor's business-tier pricing, Claude Code usage, Copilot Enterprise usage, GitHub Models usage all include some usage-based component on top of per-seat fees. A learning-stage-aware budget handles this:

- **Stage-1 and stage-2 engineers get a soft usage floor, not a cap.** They are learning. Burning tokens on exploratory prompts is the practice. A cap here is a Failure-B pattern dressed as responsible spend management.
- **Stage-3 engineers run at the team median.** Their usage is what the rest of the team should be modelling toward.
- **Stage-4 engineers may run above median, with a review threshold.** If their usage is 3x team median, that is a potential signal to look at *why* — are they pattern-building (good, feed into mod-104 narrative) or running a side project on the corp licence (less good).

A monthly usage review that flags *floors* for stages 1–2 and *ceilings* for stages 3–4 is a defensible posture. A monthly review that flags only ceilings for everyone is the wrong signal.

### The anti-pattern: tying budget to seniority bands

A set of allocation policies that each look reasonable but produce the wrong incentive in composite:

- "Staff engineers get the top-tier Cursor plan; everyone else gets the standard plan."
- "Only L25+ engineers get Claude Code agent-mode enabled."
- "Junior engineers are limited to 500k tokens/month; senior engineers to 5M."

Each policy encodes the assumption that *seniority maps to AI leverage*. The research cited above says it doesn't. In practice these policies produce:

- A stage-1 senior who sits at the senior allocation, generates very little real usage, and consumes the team's senior-tier spend as dead-weight.
- A stage-3 junior with a hard cap that throttles them mid-task, so they shift back to non-AI workflows and the team's investment in bringing them up to stage 3 is partially wasted.
- A performative "earn your way up" ladder that engineers correctly read as a status game and disengage from.

The correct shape inverts the input: measure stage first, allocate second. Seniority still shows up — the senior cohort will often *end up* with heavier budgets because they are more often at stages 3–4 — but the *input* is stage, not title.

### The budget-assessment conversation

The Day-0 stage pin from Chapter 2 is also the budget conversation. Its mechanics:

**Format.** 30–45 minute 1:1, scheduled explicitly. Not a form; a conversation. The engineer's self-assessment is the starting point; the manager adjusts based on observed work.

**Script sketch.**

> "I'm doing the Q[N] budget assessment for AI tooling. Four tool categories: AI coding assistant (currently Cursor); general-purpose assistant (Claude for most of us); eval tool at reading level (Promptfoo for us right now); agent-authoring environment at reading level (Claude Code). For each one, we'll pin you at 1 to 4 based on where you are, and I'll use that to set your usage budget and your spot in this quarter's cohort. The scores don't go in your performance review — they go in your mod-105 stage sheet. If you think you're at a 3 on one and I think you're at a 2 based on your work, we'll talk about why — the gap is often the specific skill to drill. Ready?"

**Stage-pin rubric.** The scoring criteria are visible, not secret. A sample rubric (adjust to your tooling):

- **1** — Have not opened the tool in a work context in the last 30 days.
- **2** — Have opened the tool for work but not shipped production work with it; or have shipped only trivial changes.
- **3** — Ship non-trivial production work with the tool; make judgment calls about when to use it and when not to; have at least one case where you declined to use it on a piece of work and can articulate why.
- **4** — Teach other engineers the tool; have contributed at least one pattern to the CoP pattern library; at least one review where another engineer explicitly deferred to you on a tool-usage judgment.

The explicit rubric prevents the "I'm obviously a 3" / "I think you're a 2" conversation from being personal. It is a comparison to a definition.

**What the pin feeds.** Three outputs: (a) cohort placement in Chapter 2's cohort composition; (b) usage-budget shape per the table above; (c) the engineer's own development conversation — what would move them from 2 to 3 on this tool in the next 60 days.

**Cadence.** Quarterly reassessment. A stage pin that never moves is not a budget signal; it is a lapsed instrument.

### The explicit cross-link to the AI-cost tile in mod-104

The AI-cost ratio tile from `mod-104` Chapter 2 depends on the budget-distribution choice this chapter sets. The composed number — *"$X in tool spend per 100 PRs merged"* — is only a defensible ROI number if the spend side is itself allocated deliberately. A seniority-shaped spend allocation inflates the ratio in a way that does not reflect the team's actual learning; a stage-shaped allocation produces a ratio that decreases *as the cohort moves through stages*, which is itself a leading indicator of the programme working.

Chapter 7 of `mod-104` (the AI-ROI narrative) reads from this chapter's spend-shape. Exercise 03 of `mod-104` (tool-budget and token-cost tracking) is where the two artifacts meet operationally.

### What this chapter is *not*

- **Not a vendor-procurement course.** The vendor-side mechanics — DPA, SOC 2, model provenance, contract negotiation posture — live in [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/). Mod-105 distributes a budget once procurement has landed a licence.
- **Not an enterprise FinOps course.** GPU reservation, model-hosting cost structuring, and multi-year commitment framing belong to `ai-enablement-lead` (L45) and the FinOps function. Chapter 8 draws the graduation.
- **Not a DEI or compensation course.** The stage-based allocation is a *learning signal*, not a compensation signal. Keeping the two separate matters: if the stage pin starts influencing merit review or comp, the Chapter 2 Goodhart warning kicks in and the instrument corrupts.

### Common mistakes when first setting the rubric

- **Flat usage budget per engineer.** Easier to defend to finance ("everyone gets $N/month"). Produces the Failure-B licence-drop pattern on half the team and starves the stage-4 engineers who would otherwise pattern-build at scale.
- **Leaving stage-4 uncapped with no review.** Risks the "one engineer runs a side project on the corp licence" scenario. A named ceiling + a review threshold (stage 4 reviewed quarterly, not monthly) handles this.
- **Making the stage pin opaque.** If engineers don't see the rubric, the budget conversation reads as arbitrary. Share the rubric at Day 0.
- **Not reassessing.** A rubric set once per team and never revisited is a pre-AI artifact by Month 6.
- **Conflating stage with performance.** The stage pin says what an engineer knows about a tool, not whether they are a strong or weak engineer. A stage-1 pin on Claude Code says *they have not used Claude Code yet*. It does not say anything about their ability to ship. Guard the distinction verbally and in writing.

## Example: a stage-shaped budget allocation for a 20-person team

Treat as calibration, not a template.

> **Team.** 20 engineers. Primary tools: Cursor (per-seat + usage), Claude Code (usage-based), GitHub Copilot Enterprise (per-seat), Promptfoo (free).
>
> **Stage distribution after Q4 assessment.**
> - Cursor: 3 at stage 1, 8 at stage 2, 7 at stage 3, 2 at stage 4.
> - Claude Code: 11 at stage 1, 5 at stage 2, 3 at stage 3, 1 at stage 4.
> - Copilot: 2 at stage 1, 6 at stage 2, 10 at stage 3, 2 at stage 4.
>
> **Seat allocation.** All 20 engineers get Cursor seats, all 20 get Copilot seats, all 20 have Claude Code access provisioned. Promptfoo is free so no budget.
>
> **Usage-budget shape (Claude Code example — the one with the highest stage-1 count).**
> - Stage 1 (11 engineers): soft floor expectation of ~50 tasks/month. No cap until stage 2. These engineers are in-cohort on the programme.
> - Stage 2 (5 engineers): soft floor of ~100 tasks/month. No cap. Their first-successful-PR-with-tool target is the near-term goal.
> - Stage 3 (3 engineers): run at team median. Monthly review on the mod-104 tile.
> - Stage 4 (1 engineer): no cap; quarterly review of pattern contribution (pair with mod-108's performance conversation for the pattern-contribution recognition).
>
> **Ninety-day projection.** By end of Q1, 4 stage-1 engineers expected to move to stage 2 (those in Cohort A and B of Chapter 2). 2 stage-2 engineers expected to move to stage 3. Stage-4 count flat. Spend projected to rise ~30% as stage-1 engineers move up the usage curve — and this is the correct direction.
>
> **Tie-in to mod-104.** The AI-cost ratio tile for the quarter shows $X tool spend / 100 PRs merged, with a sidebar noting the stage distribution shift as the explanatory variable. The tile *increases* in the first two quarters of the programme (more usage per PR as learners ramp) and *stabilises* as the cohort matures (same usage producing more PRs). The narrative in the mod-104 exec pre-read writes this trajectory up front.

Twenty engineers, four tools, a visible rubric, a projection that moves in the right direction, and a stated tie-in to the productivity narrative.

## Summary

- R5 says *learning stage, not seniority alone*. Brynjolfsson-Li-Raymond and Dell'Acqua explain why.
- Four stages: 1 (never used) → 2 (side-project / exploratory) → 3 (shipping production) → 4 (teaching + pattern-contributing).
- **Everyone gets the seat.** What varies is the *usage expectation*. Chapter 1's Failure B is prevented by Day-0 pins + Day-30 checkpoints, not by withholding seats.
- Usage-based pricing (tokens, request volume): soft floors at stages 1–2; team-median at stage 3; named ceiling + quarterly review at stage 4.
- The Day-0 stage-pin conversation uses an **explicit, shared rubric** and is reassessed quarterly. The pin is a learning signal, not a performance signal.
- Common mistakes: flat per-engineer budget; uncapped stage-4; opaque rubric; no reassessment; conflating stage with performance.
- The chapter cross-links with `mod-104`'s AI-cost ratio tile: a stage-shaped spend profile makes the ROI ratio honest.
- Exercise 02 produces the tool-budget distribution rubric for your team.
