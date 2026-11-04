# Chapter 4 — Flow Metrics: Reading the Team as a Value Stream

> *DX Core 4 tells the VP whether this team is healthy. Flow metrics tell the VP what this team's work is worth to the product line. Different question, different audience.*

## Motivation

[Mik Kersten, *Project to Product* (IT Revolution, 2018)](https://projecttoproduct.org/) introduced the **Flow Framework** — a set of metrics for reading a software-producing organisation as a value stream rather than as a project-delivery pipeline. The framework lives at a different altitude than DORA or DX Core 4: not *how is this team shipping* but *what is this team shipping, in what mix, and how is work flowing through it to the product*.

For R4, this altitude matters specifically because the ROI conversation often collapses when "productivity" and "product value" fail to connect. A VP sign-off on a one-pager that reads *"we shipped 15% more PRs this quarter"* is harder to get than one that reads *"we shipped 15% more feature work — and 20% less debt work — into the checkout product line this quarter."* The first is a technical statement; the second is a value statement. Flow metrics are the instrument that makes the second one legible.

This chapter is shorter than Chapters 2 and 3 because the flow instrument is thinner at team scope than at org scope; you use it for the *narrative* lens, not for the daily dashboard.

## Core concepts

### The four Flow metrics

Kersten's Flow Framework (also documented at <https://flowframework.org/>) defines four metrics, computed over a defined **value stream**:

| Metric | What it measures | Shape |
|---|---|---|
| **Flow Velocity** | Count of work items completed per unit time | Count / week or / sprint |
| **Flow Time** | End-to-end elapsed time from work-start to work-done | Days, median and 90th percentile |
| **Flow Load** | Count of work items in progress at any time | Count (WIP) |
| **Flow Efficiency** | Active-work time ÷ total elapsed time | Percentage |

And four **work types** work items must be classified into:

- **Features** — new value for the user.
- **Defects** — fixes to existing value.
- **Risks** — security, compliance, regulatory work.
- **Debts** — tech-debt and refactoring work that enables future value.

The Flow Framework's prescription is: measure each of the four *metrics* across each of the four *work types*, as the primary lens on *where this value stream's capacity is going*.

### Why Flow matters at team scope even if you don't adopt the full framework

A team manager will not usually stand up the full Flow Framework; it is an organisational instrument, often sponsored at VP-of-engineering altitude or higher. But two of its concepts are directly useful at team scope and worth stealing even without the rest of the framework:

- **Work-type classification** — the Features / Defects / Risks / Debts split is the single most useful rubric for answering *"what did this team actually do this quarter?"* at a VP altitude. The DX Core 4 Impact tile often reads back to a Flow-shaped answer whether or not you call it Flow.
- **Flow Efficiency** — active-time ÷ elapsed-time — is a strong instrument for noticing *wait states* in your team's pipeline. A team whose Flow Efficiency is 15% (typical for software work) is being held up by waiting-on-reviews, waiting-on-deps, waiting-on-specs for 85% of the clock time. AI tooling changes the active-work half; it does not automatically change the wait half, and only the composed read tells you that.

The posture: adopt the *work-type split* on your dashboard's Impact tile; use *Flow Efficiency* as a diagnostic when the team feels slow despite throughput looking fine. Do not try to be the team that owns the full Flow Framework if your organisation has not committed to it.

### Flow Efficiency under AI-augmented conditions

Flow Efficiency is the Kersten metric that most directly interacts with the AI question. A rough mental model:

- *Active work* is the time an engineer is doing the work — thinking, typing, testing.
- *Wait time* is the time the work is sitting — in review, in a staging queue, in a blocked state.

AI tooling almost entirely changes the *active* side. A model can draft a PR description, write a test, propose a refactor; these reduce the active-time duration of the task. AI tooling does **not** inherently change the wait side — review latency, staging queues, cross-team dependency blocks are unchanged by Copilot or Claude Code.

Operationally this means:

- A team that adopts AI tooling and sees *no improvement in Flow Time* is probably bottlenecked on wait, not on active work. The AI investment is landing; the Flow improvement is not. The right action is **not** more AI; it is removing the wait state.
- A team that adopts AI tooling and sees Flow Time improve *only in the first week* is probably riding a Hawthorne effect — the novelty wore off, the review-latency bottleneck reasserted itself, and Flow Time recovered to its pre-adoption level.
- A team that adopts AI tooling and sees Flow Efficiency *drop* while Flow Velocity rises is a specific warning: the team is now producing work faster than the review pipeline can absorb it, Flow Load is climbing, and work is accumulating in a waiting state. This is a common real pattern and it is bad.

Flow Efficiency is thus an unusually sensitive diagnostic for whether the AI investment is reaching the product line at all, versus being absorbed into the wait states of the pipeline.

### Work-type mix: the Impact tile in disguise

The DX Core 4 Impact tile asks *"how much of this team's work landed on new capability vs. keeping-the-lights-on."* Kersten's work-type split is a sharper version of the same question with four categories instead of two.

A Flow-shaped Impact tile reads as a stacked chart of Features / Defects / Risks / Debts, trending over quarters. The claims it supports are strong:

- *"This team spent 58% of its capacity on Features and 22% on Debts this quarter; the Debt share rose from 14% in Q1, which we did deliberately to pay down the checkout-service observability gap we flagged in the Q1 retro."*
- *"The Defect share held at 12% quarter-over-quarter despite a 30% increase in Feature shipping, which is a `mod-103` review-bar signal."*

Both sentences are the kind of answer a VP can sign. "PRs per engineer up 20%" is not.

### Where Flow and DX Core 4 compose

Flow and Core 4 are not rivals; they pick up different lenses.

| Question | Framework |
|---|---|
| Is this team healthy? | DX Core 4 |
| Is this team shipping quickly? | DX Core 4 (Speed) / DORA (Lead time) |
| Is this team shipping without breaking things? | DX Core 4 (Quality) / DORA (Change failure rate) |
| Is this team's work reaching the product line in the right mix? | Flow (work-type split) |
| Is this team's pipeline bottlenecked on active work or on wait? | Flow (Flow Efficiency) |
| What did this team achieve for the quarter's OKRs? | DX Core 4 (Impact) + Flow (work-type) |

Compose; do not duplicate. The Impact tile on your dashboard can display a Flow-shaped work-type chart, and the narrative on the one-pager can draw the composed story.

### Common mistakes

- **Adopting the full Flow Framework as a single team.** The framework is designed for value-stream-across-teams instrumentation. Standing it up without org-level sponsorship creates a maintenance burden that rarely pays back at the team-manager altitude.
- **Mis-classifying work.** The Features / Defects / Risks / Debts classification is subjective at the margin. A refactor can be a Debt (pays down existing tech-debt) or a Feature (enables a new capability). Pick a convention, document it in the data-dictionary sidebar, apply consistently. The *consistency* is more important than the *correctness*.
- **Letting Flow Load grow silently.** Flow Load (WIP) climbing while Flow Velocity is flat is a *starting-too-much* signal. Under AI-augmented conditions this is a real risk — the ease of starting new PRs with an agent lowers the activation energy for starting work and does not lower the activation energy for finishing it.
- **Using Flow metrics for performance evaluation.** Same trap as Chapter 2. Flow metrics are work-stream signals; decomposing them to the individual is a methodological error.

### The ownership boundary — again

Flow Framework instrumentation at full depth — Jira integration, work-item taxonomy, cross-team Flow dashboard — is **not** mod-104 work. Depending on org posture:

- The Flow Framework proper is often owned at VP-engineering altitude (above you) or inside the Platform / DevEx / PMO function (adjacent to you).
- Team-scope borrow-the-concept work (adopting the work-type split on the Impact tile, computing Flow Efficiency as a diagnostic) is yours.
- The BI-plumbing to compute either of the above is [`ai-augmented-analyst`](https://github.com/ai-workforce-curriculum/ai-augmented-analyst-learning) (L20).

Chapter 9 draws the boundary.

## Example: two-paragraph Flow-lens for the exec pre-read

Treat as calibration.

> **Where this team's capacity went, Q2.** Work-type mix: 58% Features, 12% Defects, 8% Risks, 22% Debts (prior Q1: 61 / 14 / 7 / 18). The Debt share lift was deliberate and absorbed the observability work on checkout-service flagged in the Q1 retro; see decision log [D-2026-04-18]. Feature share is slightly down but Feature volume is up (Flow Velocity for Features: 14 / sprint, prior 11) because total capacity rose.
>
> **Flow Efficiency, and what it tells us about the AI investment.** Flow Efficiency held at 19% (prior 17%) — modest improvement. The composed read: the AI tooling is landing on the active-work half of the pipeline (Flow Time median down from 9 to 7 days), but the wait half is still absorbing most of the clock time. Review-latency-median is the bottleneck we will target in Q3; see `mod-102` graduation-hand-off work with the DevEx platform team.

Two paragraphs; work-type mix *and* efficiency; connected to decisions and to adjacent modules.

## Summary

- Kersten's **Flow Framework** ([*Project to Product*, 2018](https://projecttoproduct.org/); [flowframework.org](https://flowframework.org/)) reads software work as a value stream. Four metrics (Velocity, Time, Load, Efficiency) × four work types (Features / Defects / Risks / Debts).
- At team scope, you usually do **not** adopt the full framework. You *borrow* the **work-type split** (for the Impact tile) and **Flow Efficiency** (as a diagnostic).
- Flow Efficiency is the single most sensitive metric to whether an AI investment is *reaching* the product line (active-work improvement that is absorbed by wait-states is invisible to Velocity alone).
- Flow and DX Core 4 compose: Core 4 answers *is this team healthy*; Flow answers *what is this team shipping into the product line, in what mix.*
- Common traps: adopting the full framework solo, mis-classifying work inconsistently, Flow Load rising silently under agent-eased authoring, decomposing to the individual.
- Full Flow Framework ownership is above/beside you (VP / Platform / PMO); the team-borrow is yours; the plumbing is `ai-augmented-analyst` (L20).
