# Exercise 04 — Underperformance Root-Cause Drill

**Estimated effort:** 2 hours.

## Objective

Produce **v0.1 of your team's underperformance root-cause drill artifact**: a 2–3-page document containing the six-question diagnostic from [Chapter 5](../05-underperformance-root-cause-drill.md), filled against a *real recent case* on your team (anonymised), plus the intervention plan that flows from the drill's diagnosis and the explicit route to HR if a formal process is warranted.

The deliverable is the diagnostic template the manager runs *before* deciding what to do about an underperformance signal, and a worked example that validates the template against a real case. The primary methodological anchors are Chapter 5's three-root-cause framing (human / workflow / tooling) and [`mod-107` Chapter 8](../../mod-107-skill-growth-anti-atrophy-and-career-development/08-ownership-boundary-with-hr.md)'s HR Handoff 1 boundary.

## Prerequisites

- [Chapter 5](../05-underperformance-root-cause-drill.md) — the three root causes, the six-question drill order, the intervention per cause.
- [Chapter 4](../04-performance-management-with-ai-in-play.md) — the feedback cadence and 1:1 signals that compose with the drill.
- [`mod-105`](../../mod-105-team-ai-enablement-programs/) — the enablement programme that one of the three root causes (tooling / enablement) routes to.
- [`mod-106`](../../mod-106-workflow-redesign-and-agent-delegation/) — the routing matrix that one of the three root causes (workflow) routes to.
- [`mod-107` Chapter 8](../../mod-107-skill-growth-anti-atrophy-and-career-development/08-ownership-boundary-with-hr.md) — the HR handoff boundary.
- One **real recent underperformance case** on your team (anonymised for the artifact), ideally one where you are currently uncertain about the root cause. If you have no live case, pick a resolved one from the past 12 months.

## Problem statement

An IC on your team is signalling below the bar in some way — PR throughput down, feedback artifact for the previous cycle thin on all three ladder axes, peer-signal issues, 1:1 narration generic. The pre-AI diagnostic (is this a skill or a motivation problem?) is insufficient under AI augmentation; there are now three competing root causes, and the common failure mode is treating a workflow or tooling gap as a performance problem and opening an HR escalation that the IC experiences as unfair — because, structurally, it was.

The drill is a short, repeatable set of six questions that forces the manager to surface workflow and tooling causes first, address them if present, and only then consider the human-skill root cause. The artifact is both the template and a worked example on a real case. The worked example is the part that validates the template: if the drill against your real case produces a diagnosis that feels wrong, the drill is miscalibrated for your team's context and needs tuning.

The exercise is not an HR conversation rehearsal. HR partnership comes after the drill, if the drill concludes a human root cause is present and the growth conversation has not shifted the pattern over two quarters. The exercise's output is the manager's diagnosis, not an HR decision.

## Steps

1. **Pick the case.** One IC on your team, anonymised in the artifact. Capture the specific signal: throughput below the team baseline, the feedback artifact from the previous cycle, 1:1 patterns across the last 4–8 weeks, any specific incidents or peer-signal moments. Two or three paragraphs of case description.
2. **Run Question 1 (shape-of-work).** Look at the IC's work assignments over the last two quarters. Is the work in-frontier or outside-frontier for the AI the team uses? For outside-frontier work, is the IC getting the paired-review / human-takes-first-cut routing (mod-106) the matrix calls for? Record the specific answer and the evidence.
3. **Run Question 2 (tool access).** Compare the IC's tool / seat / model / token-budget access against the team's senior ICs. When did their access change last? Did they complete the mod-105 Day 0 / 30 / 60 bootcamp? Are they attending the community-of-practice? Record the specific answer.
4. **Run Question 3 (enablement).** Walk the IC's Day 0 / 30 / 60 / 90 ramp. Any piece that was skipped, deferred, or shortchanged? Is there a specific bootcamp piece the IC never recovered? Record.
5. **Run Question 4 (pairing).** Who on the team has paired with the IC in the last two quarters? If the answer is "nobody" or "one person once," note the pairing gap; the IC is likely isolated from the mod-107 paired-review rotation.
6. **Run Question 5 (workflow friction).** Pull the IC's recent 1:1 narration (from the time-and-attention question in Chapter 4). What are the specific friction points the IC has described? Cluster them: agent-output correction frustration? review-latency issues? confusion about expectations? Record the specific friction cluster.
7. **Run Question 6 (human signal).** *Only after the first five.* What human-side signal is present — specifically on judgement (Axis A), specifically repeated across weeks, specifically unresponsive to the growth conversations already run? If a human signal is present, is it *independent* of the workflow / tooling signals or *composed* with them?
8. **Draft the diagnosis.** One paragraph. Names which of the three root causes are present, in what composition, with what evidence. The diagnosis is almost never single-cause; a composed diagnosis is the common case.
9. **Draft the intervention sequence.** The order is tooling first (fast), workflow second (medium), human third (slow). For each cause present, name the specific intervention (mod-105 enablement piece? mod-106 routing matrix update? Chapter 4 1:1 structural change? mod-107 Chapter 5 carve-out?), the owner, and the specific timeframe.
10. **Decide the HR route (if any).** Is there sufficient evidence that a human root cause is the primary driver, has been present for two quarters despite documented growth work, and has not shifted under the Chapter 4 1:1 flow? If yes, name the specific Handoff-1 conversation agenda ([`mod-107` Chapter 8](../../mod-107-skill-growth-anti-atrophy-and-career-development/08-ownership-boundary-with-hr.md)): the evidence base, the drill output, the open question for HR. If no, document explicitly that the drill does not warrant HR escalation at this point and name the next re-evaluation date.
11. **Peer-review.** Review the artifact with one trusted peer manager (30 minutes). The peer is not there to agree; the peer's job is to challenge the diagnosis. If the peer says "I think you're missing the workflow signal in Question 1," that is the signal you are looking for — the drill works precisely to surface biases the primary manager has.

## Starter guidance

- **Run the questions in order.** The order prevents the specific failure mode of jumping to the human root cause first. The chapter is explicit on this.
- **Evidence is specific, not general.** "The IC's throughput is low" is not evidence; "the IC shipped 7 PRs in Q3 vs. the team median of 15" is. Same for every answer in the drill — specific, with sources.
- **The drill is not the IC's conversation.** Run the drill privately; share the diagnosis and the intervention plan with the IC in a specific growth-framed 1:1. The drill output itself is a manager-side document, not an IC-facing one.
- **A composed diagnosis is the common case.** Expect two or three causes present together. The intervention sequence addresses them in order.
- **Do not skip Question 1 even when the pattern "obviously" looks like a human signal.** The failure mode this exercise prevents is manager intuition under AI augmentation, which is miscalibrated.
- **Tooling gaps close in the week they surface.** A diagnosis that names a tooling gap and then says "we'll address that next cycle" is the manager failing the IC. Close the tooling gap in week one.
- **The drill is re-run.** Workflow and routing conditions change. Re-run the drill when the signal re-surfaces.
- **If you are uncertain about whether to open the Handoff-1 conversation with HR, default to opening it as a framed question, not a recommendation.** HR's answer is often *"continue in 1:1s another quarter"* — which is useful for the manager and harmless to the IC.
- **If the case involves protected-class considerations, leave, a recent complaint, or other employment-law-visible circumstances**, HR coordination is required regardless of the drill's technical diagnosis. The drill is a technical diagnostic; the legal exposure path runs separately through HR and counsel.
- **Length: 2–3 pages for the worked case; one page for the template extracted from it.** More than five pages is over-written.

## Acceptance criteria

The artifact is complete when:

- A case description (anonymised) is present with specific evidence.
- All six questions are answered in order, each with specific evidence (not general impressions).
- A one-paragraph diagnosis names which of the three root causes are present, in what composition.
- An intervention sequence names specific interventions per cause, with owners and timeframes, in the tooling → workflow → human order.
- An HR-route decision is named, with either the Handoff-1 conversation agenda or an explicit "no HR escalation at this point" with re-evaluation date.
- A peer-review entry records the peer's challenge and any resulting corrections.
- The template (the six questions as a reusable form) is extracted on one page so it can be re-run on future cases.
- A new manager on the team could read the artifact and run the drill on a case of their own.
- The drill's output on the worked case *feels right* to you as the manager — a diagnosis that lands.

## Stretch goals

- **Run the drill on a second, resolved case.** Pick a case from the past 12 months that was resolved (either the IC improved, the IC left, or a formal process ran). Walk the drill against the case with the benefit of hindsight. Does the drill produce the diagnosis the hindsight supports? If not, the drill is miscalibrated.
- **Compose with [`mod-106`](../../mod-106-workflow-redesign-and-agent-delegation/).** If the drill surfaces workflow root causes consistently across multiple ICs, the routing matrix likely needs a broader update, not case-by-case fixes. Draft the matrix amendment.
- **Compose with [`mod-105`](../../mod-105-team-ai-enablement-programs/).** If the drill surfaces enablement root causes consistently, the Day 0 / 30 / 60 / 90 ramp has a systematic gap. Draft the ramp amendment.
- **A "bias audit" of the manager's own drill runs.** Over the first quarter of running the drill, track across all cases: how often is the primary root cause human vs. workflow vs. tooling? If the primary cause is always human, the manager is likely still running pre-AI intuition and the drill is not being engaged with substantively.
- **A decision-tree variant of the template.** If / then flow that walks through the six questions programmatically. Useful for teams where multiple managers will run the drill and consistency matters.
- **An HR-facing one-pager.** The specific artifact the manager brings to the Handoff-1 conversation: the pattern observed, the drill output excluding workflow / tooling causes, the two-quarter documentation, the open question. Half a page.
