# Chapter 5 — Deliberate-Practice Carve-Outs

> *If the atrophy signal is lagged and the dashboards do not surface it, the only intervention that works is a scheduled, named carve-out that keeps the judgement muscle active. The carve-out is not a wellness initiative. It is a managerial production decision about what work the humans still do and under what conditions.*

## Motivation

Chapters 2, 3, and 4 established the three channels — growth path (Brynjolfsson), differentiation (Noy & Zhang), deference (Dell'Acqua). This chapter is the first of the operational responses. It takes the three findings and turns them into a scheduled set of carve-outs the team runs on a quarterly cadence: paired-review rotations, periodic AI-off artifacts, and the judgement-weighted review pass that amends the mod-103 review standard.

The managerial framing is important. The carve-outs are not optional enrichment. They are not slack. They are not a wellness programme. They are the mechanism by which the manager ensures the team's human skill base does not quietly erode while the output numbers improve. Exercise 02 produces the quarterly schedule that operationalises them.

## Core concepts

### The anchor: Ericsson on deliberate practice

Anders Ericsson's research on expert performance (summarised in his book *Peak*, and across the review articles cited in [`resources.md`](resources.md)) distinguishes *naive practice* (doing the task) from *deliberate practice* (doing a scoped sub-task at the edge of current capability, with immediate feedback, in a way designed to extend the capability). The distinction matters here because AI-augmented work is, by default, *less* deliberate: the AI reduces the cognitive effort at exactly the points where the effortful deliberate work would have built the capability.

The carve-outs in this chapter are designed to re-introduce the three ingredients Ericsson names — a scoped sub-task at the edge of capability, immediate feedback, explicit extension of capability — into the team's week on a cadence that is small enough to be sustainable and visible enough to be defensible to leadership.

Two caveats before the detail:

- **Ericsson's research is on expert performance, not on preventing deskill.** The framing is adjacent — the same mechanisms that build expertise, kept active, prevent its erosion — but the deliberate-practice literature is not a direct test of anti-atrophy interventions in AI-augmented work. Cite carefully.
- **Deliberate practice is costly.** Each hour of deliberate practice is more taxing than the equivalent hour of normal work. The carve-outs are deliberately *small* and deliberately *spaced* because sustaining deliberate practice as the team's default state is not realistic and would burn the team out. The schedule in Exercise 02 is calibrated to ~2–4 hours per IC per quarter, not per week.

### The three carve-outs

mod-107 teaches three specific carve-outs. They are not the only carve-outs a team might run; they are the minimum set that addresses the three channels.

**Carve-out 1 — paired-review rotation (addresses the deference channel).** For task-types routed to AI + human pair per mod-106's routing matrix *and* classified as outside-frontier or on-the-frontier-edge, reviews are done by two reviewers on a rotation: one senior IC and one junior IC. The paired reviewers discuss the decision the artifact makes before signing off. The purpose is two-fold: the senior IC models judgement for the junior, and the junior IC's questions force the senior's model to be articulate rather than tacit.

The rotation is scheduled, not ad-hoc. A rotation that happens *when there is time* happens once; a rotation that is on the calendar happens quarterly. Exercise 02 is the calendar.

**Carve-out 2 — periodic AI-off artifact (addresses the deference and growth-path channels together).** Once per quarter, each IC produces one *named* artifact without AI assistance. The artifact is pre-chosen at the start of the quarter, scoped to be completable in 2–4 hours, and specifically low-stakes relative to critical production work — not a release-day PR, not a customer-blocking bug fix, not something whose quality would cause harm if the IC's unassisted capability has degraded.

The artifact is reviewed, but the review's purpose is not to grade the output. It is to surface the *comparison*: *"what was harder than you expected, what was easier, where did you reach for the AI reflexively and have to stop yourself?"* The conversation after the artifact is the deliberate-practice feedback step.

**Carve-out 3 — judgement-weighted review pass (addresses the differentiation channel).** For a subset of reviews — scheduled, not every review — the reviewer applies an amendment to the team's mod-103 review standard: before looking at the diff, ask the IC the judgement question from Chapter 4. *"If you were writing this from scratch, would you have made the decisions this artifact makes?"* The review then proceeds normally, but with the judgement-answer on the record alongside the diff-level comments.

This carve-out costs ~90 seconds per review and does not need to be applied to every review. Exercise 02 schedules which task-types and which cadence. The schedule is explicit so the overhead is bounded.

### Why three and not twelve

A long list of interventions is easy to write and impossible to sustain. The three carve-outs are the three the research anchors most directly support, and are *all three* small enough that a team can actually run them quarterly without displacing production work. Teams that add more carve-outs at the start — morning deliberate-practice katas, book clubs, deep-dive learning Fridays — tend to lose them to the first production-pressure quarter and then lose faith in the entire anti-atrophy move.

The right growth pattern is: run the three for a year, prove to the team and to leadership that they stick and produce value, then layer on the next carve-out from a known-honest base. Chapter 7's retro prompts are the mechanism by which the team itself proposes the fourth carve-out, grounded in signal the retros surface.

### What makes the carve-outs defensible to leadership

Three framings carry well in exec conversation:

- **The lagged-signal argument.** The dashboards in mod-104 will not show the atrophy until it is too late. The carve-outs are the leading-indicator intervention — Chapter 1's framing, worth repeating when the exec asks *"why can't we measure the problem first?"*. You cannot; by the time you can, the ladder below your senior ICs is thinner than it should be.
- **The cost-of-the-alternative argument.** Dell'Acqua's 19-percentage-point degradation on outside-frontier tasks, cited with the domain caveat, is an *immediate* risk, not a future one. One incident per year caused by deference is a worse outcome than three hours of carve-out per IC per quarter. The arithmetic is specific to the team but usually favours the carve-out.
- **The retention argument.** The Brynjolfsson workforce-dynamics finding and the Noy & Zhang job-satisfaction finding both suggest that ICs who feel their skill is growing are more likely to stay. The carve-outs surface and support growth. A visible growth pathway is a retention lever that is cheaper than a counter-offer.

The *wrong* framing is "we're worried about AI making the team lazy." It reads as unmoored anxiety and invites the response "do you have evidence?" You have evidence — the three research anchors — but you have to name them as the evidence, not vaguely imply they exist.

### What the carve-outs are *not*

- **Not training.** Training is a mod-105 artifact — bootcamps, workshops, communities of practice. The carve-outs are *production work done under modified conditions*. Confusing the two produces the wrong thing in both places.
- **Not a mandate against AI use.** Carve-out 2 (AI-off artifact) is a specific, scoped, time-bounded intervention. It is not a signal that AI use is discouraged. The team's default is still AI-assisted; the AI-off slot is a *comparison instrument*, not a return to pre-AI practice.
- **Not a surveillance programme.** The carve-outs are collaborative and discussed openly in retros. Monitoring AI tool telemetry to *catch* ICs using AI inappropriately is a different (and worse) intervention — see Chapter 7 on why the signal lives in 1:1s and retros, not in dashboards.
- **Not deliberate practice of AI usage.** The carve-outs are specifically designed to practise *judgement* about AI output, not to practise prompting. mod-105 teaches prompting fluency; mod-107 teaches the judgement around it.

### The interaction with the mod-103 review standard

The judgement-weighted review pass (Carve-out 3) is an *amendment* to the existing mod-103 review standard, not a replacement. The amendment adds one question, applied at the reviewer's discretion where the routing matrix flags the task as outside-frontier. The mod-103 standard still governs correctness, code-level quality, test coverage, documentation — all the things it already governs. The amendment adds the judgement axis.

If the team's mod-103 standard has not been written yet, the carve-out is premature. Write the mod-103 standard first; add the mod-107 amendment to it. An amendment to a non-existent standard is a document nobody uses. mod-103 is the prerequisite here.

### How the carve-outs compose with the carve-outs in adjacent modules

- **mod-105 enablement.** The Day 0 / 30 / 60 / 90 enablement path produces tool-fluent ICs. The mod-107 carve-outs then *sustain* the human-judgement capacity of those ICs across the rest of their tenure. The two compose; they do not overlap.
- **mod-106 routing matrix.** The carve-outs assume a routing matrix exists — Carve-out 1 and Carve-out 3 specifically apply to task-types the matrix has classified. Running the carve-outs without a routing matrix means running them on arbitrary task-types, which produces less signal.
- **mod-109 incident response.** When an incident happens that traces to the deference pattern — an IC shipped AI output on an outside-frontier task — the post-mortem is in scope there. The *response* in mod-107 is to add the specific task-type to the paired-review rotation, not to blame the IC. mod-109's blameless posture is the frame.
- **mod-112 ritual calendar.** The quarterly schedule produced in Exercise 02 lands on the team's ritual calendar in mod-112. The carve-outs are *rituals*, not ad-hoc interventions.

### Common failure modes when running the carve-outs

- **Carve-out 2 happens once, is informally excellent, then never happens again.** The fix is to put the next quarter's AI-off artifact on the schedule the day the current quarter's is reviewed. Momentum is scheduled, not hoped for.
- **Carve-out 1's paired reviews become a bottleneck.** If the senior IC is on every paired review, the senior becomes the constraint. The rotation must rotate — every senior IC participates in some, every junior IC paired with multiple seniors over a year.
- **Carve-out 3 becomes performative.** The reviewer asks the judgement question, the IC gives a plausible answer, the reviewer nods, the diff is approved unchanged. The fix is Chapter 7's retro — once per quarter, surface in retro one case where the judgement question changed the answer. If the retro cannot name one, the question is being asked rhetorically, not substantively.
- **ICs feel the AI-off slot is a test.** It is not; it is a comparison instrument. The manager's language about it matters. Frame it as *"what did you learn about what the AI is doing for you?"* not as *"let's see if you can still do this."*
- **The carve-outs are applied uniformly to all task-types.** The research anchors specifically say the deference risk is on outside-frontier tasks. Running the paired-review rotation on inside-frontier tasks produces overhead without signal. The routing matrix is the gatekeeper.

## Example: one quarter of carve-outs on a seven-engineer team

Composite example; treat as calibration, not a template.

- **Carve-out 1 (paired-review rotation).** Three outside-frontier task-types from the routing matrix: *"design a schema migration under uncertain consumer traffic patterns,"* *"write the incident narrative for an incident involving an upstream vendor,"* *"author the quarterly architecture-direction memo."* Each of these task-types is paired-reviewed on the rotation. Six paired reviews across the quarter, one per fortnight. Each pairing is one senior + one junior, rotating so every junior pairs with every senior over the quarter.
- **Carve-out 2 (AI-off artifact).** One artifact per engineer: a specific, pre-chosen, scoped task from the quarterly backlog. Three examples: *"author the postgres migration for the X feature; no AI assistance; present in the IDP review,"* *"write the design doc for the Y internal tool; AI may be used only for proofreading,"* *"author the on-call handbook update; no AI, 3-hour budget."* Review in a 30-minute 1:1 at the end of the quarter; the conversation is about the comparison, not the output.
- **Carve-out 3 (judgement-weighted review pass).** Applied on the three outside-frontier task-types above, every review. Not applied on the twelve other task-types. ~90 seconds per review; ~15 minutes of overhead per fortnight across the team.

Total scheduled overhead: ~3 hours per IC per quarter. The schedule is a page; the artifact is a one-pager with the rotation and the AI-off artifacts listed. Exercise 02 produces this document in your team's context.

## Summary

- The three carve-outs — **paired-review rotation**, **periodic AI-off artifact**, and **judgement-weighted review pass** — are the operational response to the three research anchors; each responds to a specific channel.
- Grounded in **Anders Ericsson's deliberate-practice framing**, with the explicit caveat that Ericsson's research is on expertise formation, not on preventing AI-induced atrophy.
- The carve-outs are **scheduled, not ad-hoc**; the schedule is the Exercise 02 artifact and lives on the mod-112 ritual calendar.
- **Three defences** against the "why are we doing this" question: the lagged-signal argument, the cost-of-the-alternative (Dell'Acqua 19-point degradation) argument, the retention argument.
- **Composes with** mod-103 (amendment, not replacement), mod-105 (sustains what enablement starts), mod-106 (routing matrix is the gatekeeper), mod-109 (blameless post-mortem is the frame), mod-112 (rituals land on the calendar).
- **Failure modes to watch:** the one-time Carve-out 2; the senior-IC-as-bottleneck Carve-out 1; the performative Carve-out 3; the IC-feels-tested framing; uniform application across all task-types.
- The quarterly overhead is ~2–4 hours per IC. If the schedule looks heavier than that, it is over-designed; strip it back.
