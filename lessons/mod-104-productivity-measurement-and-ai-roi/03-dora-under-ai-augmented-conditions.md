# Chapter 3 — DORA Under AI-Augmented Conditions

> *The four keys still read; the denominator has moved. A deployment-frequency chart with no AI-attribution sidebar is now an incomplete sentence.*

## Motivation

DORA — the four keys of software-delivery performance, long-running research by DevOps Research & Assessment at Google Cloud, summarised annually in the [State of DevOps report](https://dora.dev/research/) and in [Forsgren, Humble & Kim, *Accelerate*](https://itrevolution.com/product/accelerate/) — is the measurement framework most engineers already have a position on. The four keys:

1. **Deployment frequency** — how often the team ships to production.
2. **Lead time for changes** — commit → production, median.
3. **Change failure rate** — fraction of production changes that cause a failure.
4. **Failed-deployment recovery time** — previously MTTR; how fast the team recovers from a failed deploy.

DORA sits inside DX Core 4 as the Quality anchor (Chapter 2); it also stands on its own as a delivery-health scorecard that executives above you likely already read. This chapter answers the specific question R4 raises: *what happens to DORA when the author of a growing fraction of diffs is a model?*

The answer, in short: **DORA still reads, with three caveats you must call out in writing.** Two caveats move the *interpretation* of the signal; one moves what you *do* when the signal drifts.

## Core concepts

### The four keys, by what they measure

A brief refresher so the AI-augmented layer lands cleanly. The *elite / high / medium / low* cluster descriptions come from the annual DORA report (bands change year-over-year; consult the latest report, not stale blog-era numbers).

| Key | What it is | What the signal tells you |
|---|---|---|
| Deployment frequency | How often code reaches production | Batch size + release discipline; smaller is better |
| Lead time for changes | Commit → production median | Pipeline health + review latency + rework |
| Change failure rate | % of production changes that fail | Shipping quality at the batch size you ship at |
| Recovery time | Time to restore from a failed deploy | Operational maturity + rollback readiness |

Two pairs: *throughput* (frequency, lead time) and *stability* (failure rate, recovery). DORA's long-running finding is that elite teams score high on *both* pairs simultaneously — the two are not a trade-off. This finding predates AI augmentation; Chapter 5 will discuss what the AI literature does and does not say about it.

### Caveat 1 — the throughput signal is now harder to attribute

Under pre-AI conditions, a quarterly jump in deployment frequency could reasonably be attributed to a specific change: a pipeline improvement, a batch-size reduction, a new team member. Under AI-augmented conditions, at least three new drivers exist simultaneously:

- *Agent-drafted scaffolding* reduces the per-PR authoring time, which can raise both frequency and lead-time-median even when nothing else changed.
- *Agent-drafted tests* can raise frequency by lowering the perceived risk of shipping — sometimes legitimately (coverage really did improve), sometimes not (tests are present but the test design is wrong — see `mod-103` Chapter 2 on the verification bar).
- *Agent-drafted PR descriptions* can shrink review-latency by making review *easier*, which again raises frequency without necessarily changing output quality.

None of these drivers is bad. They do, however, make the raw frequency / lead-time number less interpretable than it was. The mod-104 posture:

- **Keep DORA throughput on the dashboard.** The signal is still real.
- **Pair it with a sidebar** in the one-pager (Chapter 7) that names the drivers you believe are contributing. Honest attribution is a sentence, not a number.
- **Compose with Quality (Chapter 3 caveat 2 below).** The only reading of DORA that survives is the composed one: *frequency ↑ while failure rate stable or ↓* is the signal to seek; *frequency ↑ while failure rate also ↑* is a warning.

### Caveat 2 — change failure rate is now the load-bearing key

If one key becomes *more* important under AI-augmented conditions, it is change failure rate. Three reasons.

- **Agent-drafted diffs can look correct and ship wrong.** Chapter 2 of [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) is the whole treatment; here the implication is only that *the volume of plausible-looking-wrong diffs* has risen. Change failure rate is the dashboard instrument that will register this first.
- **The review bar (per `mod-103`) is itself an intervention that should move this number.** If your team instituted an AI-review checklist in Q1 and change failure rate did not move in Q2, the intervention is not working or the signal is masked. Either way, you want to know.
- **Executives already read this number.** Under AI-augmented conditions, change failure rate is the single most defensible answer to *"are we shipping worse?"* that a VP will accept.

Two operational notes on the measurement:

- **Define "change failure" explicitly.** The DORA guidance is a change that *results in degraded service or requires remediation*. In practice teams need an operational definition: *any rollback, any hotfix within 24h, any incident-ticket raised with severity ≥ S2 attributed to the deploy*. Write the definition down; apply it consistently; name it in the data-dictionary sidebar.
- **Trend matters more than the current point.** Change failure rate on a 20-PR/week team is a noisy statistic. A 30-day trailing window with the operational definition above is the readable signal.

### Caveat 3 — recovery time is now a leading indicator of agent-generated incidents

Recovery time is the key that is almost never thought about in advance and is the first to buckle when AI-generated work ships broken. Two specific failure modes [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) will cover in depth; here they bear on how you read DORA.

- **The responder-of-record ambiguity.** When a human authored the broken change, incident response has a clear human to pull in. When an agent drafted the change and a human approved it, the on-call triage runs slower because the mental model of "who knows this code" is weaker. Recovery time quietly climbs.
- **The rollback-readiness mismatch.** Agent-drafted changes often touch surface area the author (the agent) does not know is risky — config files, feature-flag definitions, inherited code with undocumented invariants. Rollback paths that were adequate for human-authored changes can be inadequate for agent-authored ones, and the first incident reveals it.

Operational implication for the dashboard: *recovery time is a leading indicator of agent-generated incident-response gaps*. A recovery-time trend that quietly rises while frequency / lead-time look fine is the signal to catch early.

### What *doesn't* change about DORA under AI-augmented conditions

To avoid overcorrection:

- **The four keys are still the right four keys.** AI augmentation is not a reason to redesign the delivery-performance scorecard. The scorecard is well-established research (*Accelerate*) and the four-key shape survives.
- **The elite / high / medium / low bands still apply** (consult the current year's DORA report for the exact thresholds). Your team's membership in those bands is still a defensible comparison point.
- **The anti-correlation hypothesis is still wrong.** DORA has long established that throughput and stability improve together; the AI literature does not overturn this. A team shipping faster that is also shipping more broken is almost always revealing a review-bar failure (`mod-103`), not an inherent AI trade-off.
- **DORA is still team-shaped, not individual-shaped.** The anti-individual-performance-management posture of Chapter 2 applies to DORA keys as well.

### Composing DORA with the rest of the dashboard

DORA never sits on the dashboard alone; it sits inside Core 4's Quality tile and composes with the other tiles. Two composition patterns to internalise.

**Composition A — the "shipped more, broke no more" story.** *Deployment frequency ↑ and change failure rate flat-or-↓, over two quarters, while the AI-cost ratio tile also ↑.* This is the defensible AI-productivity narrative. It survives scrutiny because it is throughput *and* quality *and* cost, read together.

**Composition B — the "appearances vs. reality" story.** *Deployment frequency ↑ and change failure rate ↑ and recovery time ↑.* This is a team that has adopted AI tooling without landing the review bar from `mod-103`. The composed signal is more diagnostic than any one of the three alone — and the manager-side action is almost always a `mod-103` checklist review, not a DORA investigation.

A dashboard that reads A vs. B at a glance is doing its job. A dashboard that reports "deployment frequency up 15%" without surfacing failure-rate and recovery-time together is set up to tell story A even when story B is happening.

### Common mistakes with DORA under AI

- **Celebrating the first-quarter lead-time improvement.** Lead time will often *improve* in the first quarter of AI adoption for the simple reason that agent-drafted PR descriptions and scaffolding shorten the authoring half of the cycle. The improvement may not persist, and it is not necessarily the number worth celebrating — change failure rate and impact are. Wait for the trend.
- **Not re-defining change failure for the agent era.** A team whose definition of "change failure" is "the author raised a rollback" will miss the case where an agent-authored change broke something nobody noticed to roll back. Widen the definition to include *any* incident attributed to a deploy, independent of who filed it.
- **Reading DORA on an individual.** Never a good idea; especially not now.
- **Using DORA bands as the top-line AI ROI claim.** DORA bands move slowly and are not primarily an AI-attribution instrument. "We are now a high-DORA team *because* of our AI investment" is a sentence that will not survive scrutiny. "We held our DORA band through the quarter we rolled out the agent, and our change-failure-rate trend is stable" is a sentence that will.

### What you own vs. what the delivery-engineering function owns

The DORA pipeline itself — instrumentation, dashboard plumbing, deployment-event capture, incident-ticket joining — is **not** a mod-104 artifact. The DORA *reading posture* is.

- The plumbing is owned at [`ai-augmented-analyst`](https://github.com/ai-workforce-curriculum/ai-augmented-analyst-learning) (L20) when the team's DORA data lives in a BI warehouse, or by the platform / DevEx team when they publish a shared dashboard (see [`mod-102`](../mod-102-team-ai-adoption-and-roadmap/) Chapter 5 on platform partnership).
- The reading — what the trend means, what to do about it, how to narrate it to leadership — is mod-104 work.

Chapter 9 draws the full ownership boundary.

## Example: a two-paragraph DORA narrative, AI-augmented

Treat as calibration for shape.

> **DORA, Q2.** Deployment frequency held at the "high" band (median 2.4 deploys / engineer / week; prior quarter 2.3). Lead-time-for-changes median 2.3 days, 90th percentile 7.1 days (prior 2.4 / 7.9). Change failure rate 11% on a 30-day trailing window using the broadened definition (any rollback / any hotfix ≤ 24h / any S2+ incident attributed to the deploy); prior quarter 12%. Recovery time median 1.4 hours (prior 1.3 — slight rise; see note).
>
> **Attribution and caveats.** The lead-time improvement in Q1 did not continue in Q2; Q2's gains came from scaffolding reduction in authoring time that has now plateaued. Change failure rate is stable on the broadened definition — the `mod-103` AI-review checklist landed in week 3 of the quarter; we attribute some of the stability to it but cannot isolate the contribution without a counterfactual. Recovery time's slight rise correlates with the two S2 incidents in weeks 7 and 10, both involving agent-drafted config changes that touched feature flags; incident-response adjustments are tracked in the `mod-109` follow-up log.

Two paragraphs; frequency / lead-time / failure-rate / recovery read together; honest about attribution.

## Summary

- DORA's four keys — deployment frequency, lead time for changes, change failure rate, recovery time — still read under AI-augmented conditions. The framework is stable; the interpretation layer has new work to do.
- **Caveat 1:** throughput signals (frequency, lead time) are harder to attribute cleanly — agent-drafted scaffolding, tests, and PR descriptions can move them without the underlying work changing. Pair with a sidebar.
- **Caveat 2:** change failure rate is the *load-bearing* key under AI-augmented work. Define it explicitly and widen the definition. It is the first signal the `mod-103` review bar is or is not holding.
- **Caveat 3:** recovery time is a leading indicator of agent-generated incident-response gaps (responder-of-record ambiguity, rollback-readiness mismatch). Rising recovery time deserves early attention.
- The *composed* reading — frequency ↑, failure-rate stable-or-↓, cost ↑ — is what's defensible as an AI-productivity story. Frequency alone is not.
- What stays the same: four keys, elite-to-low bands, team-shape, throughput-and-stability-together finding.
- DORA plumbing is owned at `ai-augmented-analyst` (L20) or the platform team; the reading posture is mod-104. Chapter 9 draws the line.
