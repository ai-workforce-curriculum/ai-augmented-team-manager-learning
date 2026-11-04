# Exercise 02 — Deliberate-Practice Carve-Out Schedule

**Estimated effort:** 2 hours.

## Objective

Produce **the quarterly carve-out schedule** for your team: a one-page artifact that names, for the upcoming quarter, (a) which outside-frontier task-types are on the paired-review rotation and in what order, (b) which named AI-off artifacts each IC will produce and by when, and (c) which reviews on which task-types get the judgement-weighted review pass. The schedule is calibrated to ~2–4 hours of overhead per IC per quarter and lives on the team ritual calendar.

This is the operational artifact that gives Chapter 5's three carve-outs a running cadence. It is the artifact a new IC can read on their second day and know what the team's anti-atrophy practice actually looks like in motion.

## Prerequisites

- [Chapter 5](../05-deliberate-practice-carve-outs.md) — the three carve-outs, the Ericsson grounding, and the common failure modes.
- The policy memo from [Exercise 01](exercise-01-empirical-research-into-team-policy.md) — the rationale that justifies the schedule's existence to the team and to leadership.
- A current **task-routing matrix** from [`mod-106` Exercise 01](../../mod-106-workflow-redesign-and-agent-delegation/exercises/exercise-01-task-routing-matrix-for-your-team.md). The routing matrix names which task-types are outside-frontier or on-the-frontier-edge; those are the task-types the schedule focuses on. If your routing matrix is still TBD, the schedule will be guesswork — complete mod-106 Exercise 01 first.
- A current **team review standard** from [`mod-103`](../../mod-103-review-standards-and-eval-commissioning/). Carve-out 3 is an amendment to the review standard, not a replacement.
- Access to the team's shared calendar or ritual-calendar artifact (mod-112). The schedule lands on that calendar at the end.

## Problem statement

The three carve-outs — paired-review rotation, periodic AI-off artifact, judgement-weighted review pass — are only interventions if they *actually happen on a cadence*. Carve-outs that live in an unscheduled intention document get displaced by production work in the first pressured quarter and then never recover. This exercise produces the specific schedule that makes them happen.

The schedule has to balance two forces. If it is too ambitious — too many rotations, too-frequent AI-off artifacts, judgement-weighted reviews on every PR — the team will lose it to production pressure and come away believing anti-atrophy work is a fantasy. If it is too anemic — one AI-off artifact per year, no rotation — it will not produce signal and will not justify itself to leadership. The target is ~2–4 hours of overhead per IC per quarter: enough to generate signal and growth, not enough to displace production work.

## Steps

1. **Pull the three outside-frontier task-types from your routing matrix.** Your mod-106 Exercise 01 matrix will have ~2–4 outside-frontier or on-the-frontier-edge task-types. Pick the three most load-bearing for the quarter — the task-types with the highest consequence if judgement is weak on them, or the task-types where the retro has been surfacing concern. Write them down with a sentence each on why they are on the list.
2. **Design Carve-out 1: the paired-review rotation.** For each of the three task-types, decide the pairing frequency (default: one paired review per fortnight across the three task-types, so each task-type is paired ~twice per quarter). Build a rotation grid: for each pairing slot, which senior IC + which junior IC. Rotate so every junior IC pairs with every senior IC at least once over two quarters. Three pieces of discipline:
   - The pairing is scheduled on the calendar *and in the review assignment tool* (whatever your team uses). If the pairing is not visible in the review assignment workflow, it will not happen.
   - The pairing is the *review*, not a separate meeting. The two reviewers do the review together; they do not schedule a separate retro of the review.
   - If a scheduled pairing falls through (one of the reviewers is out, the task-type did not come up this fortnight), the pairing gets rescheduled, not skipped. The schedule tracks slip.
3. **Design Carve-out 2: the AI-off artifact per IC.** For each IC on the team, pre-choose one specific artifact they will produce without AI assistance during the quarter. Selection criteria:
   - *Scoped to 2–4 hours of work.* Not a sprint-sized project.
   - *Low-stakes relative to production work.* Not a release-day PR or a customer-blocking fix.
   - *Representative of the IC's level and growth arc.* A junior IC's AI-off artifact looks different from a senior IC's.
   - *Pre-chosen, not retrofitted.* The artifact is named at the start of the quarter so the IC can plan for it and so the comparison with their AI-assisted baseline is meaningful.
   - Examples (your team's version will be specific): a migration script, a design doc, an on-call runbook update, a short post-incident narrative, a new tool integration — pick an artifact that lives at the edge of the IC's current capability.
   - Schedule the 30-minute 1:1 retrospective of the artifact on the calendar at quarter-end. The retro conversation is the deliberate-practice feedback step; it is where the growth happens.
4. **Design Carve-out 3: the judgement-weighted review pass.** For which task-types and at what cadence does the reviewer apply the pre-diff judgement question? Default: on the same three outside-frontier task-types as Carve-out 1, on *every* review of those task-types for the quarter (not only on the paired reviews). The overhead is ~90 seconds per review; the volume on three outside-frontier task-types for a 5–8-engineer team is typically 3–6 reviews per fortnight. Document the amendment to the review standard so the reviewer-on-call knows the pass is expected.
5. **Annotate the schedule with the rationale.** For each carve-out, add a one-sentence pointer back to the Exercise 01 memo: *"Carve-out 2 addresses the deference channel (Dell'Acqua et al. 2023) and the growth-path channel (Brynjolfsson, Li, Raymond 2023)."* The annotation keeps the schedule tied to the memo so when a senior IC asks *"why are we doing this,"* the answer is on the artifact.
6. **Check the budget.** Tot up the overhead per IC per quarter. Target: 2–4 hours. If the sum is over 5 hours per IC, you are over-designed — strip back Carve-out 3's scope (apply to fewer task-types) or Carve-out 1's frequency (one paired review per month, not per fortnight). If the sum is under 1 hour, you are under-designed — add the one Carve-out 2 artifact that was missing, or tighten the Carve-out 1 rotation.
7. **Land it on the team ritual calendar.** The schedule goes on the mod-112 ritual calendar or the team's weekly-plans tool. The schedule is only real when it is on the calendar.
8. **Co-review with one senior IC and one junior IC.** Senior IC: *"does the paired-review rotation pair you with the right ICs, and does the frequency match the actual flow of outside-frontier work?"* Junior IC: *"is the Carve-out 2 artifact scoped so it feels like growth, not like a test?"* Record the feedback and adjust.
9. **Write the two-sentence opening paragraph.** A new IC reading the schedule should understand *in two sentences* why these carve-outs exist and how they relate to the IC's growth. Point at Exercise 01 for the research grounding.

## Starter guidance

- **The schedule is one page.** If it is longer, you are over-designing. The point is to be read and run, not to be comprehensive.
- **The three carve-outs are the floor, not the ceiling — but the ceiling comes later.** Do not add a fourth carve-out this quarter even if it feels like a good idea. Run the three for a full quarter, see how they work, then iterate.
- **Scope Carve-out 2 for growth, not for difficulty.** The artifact is the IC's chance to see what the AI does for them. If it is too hard, the IC produces something unusable and the comparison is noise; if it is too easy, there is no comparison because it is well within their unassisted capability. Pick something at the edge.
- **The paired-review rotation is the hardest to sustain.** It involves coordinating two people's schedules on a specific kind of work that may not arrive on schedule. Build slack into the rotation — if a task-type does not come up in a given fortnight, do not force it.
- **Communicate the schedule in the team channel, not only in 1:1s.** A junior IC who hears about Carve-out 2 only in their 1:1 may read it as individual-performance signal. A junior IC who sees the schedule in the shared docs space, with the whole team's rotation visible, reads it as a team practice. The framing matters for psychological safety (Chapter 7).
- **Default to the AI-off artifact in the middle of the quarter, not at the end.** An end-of-quarter AI-off artifact gets squeezed by quarter-end deadlines. A middle-of-quarter artifact has room to breathe.
- **For a very small team (≤3 engineers)**, scale down — one paired review per month, one AI-off artifact per IC per quarter (still), judgement-weighted pass on the one or two outside-frontier task-types. The structure is the same; the volume is proportional.

## Acceptance criteria

The schedule is complete when:

- Three outside-frontier task-types are named, with a one-sentence rationale each.
- The paired-review rotation grid is complete for the quarter: slot, task-type (or task-type candidate), senior IC, junior IC. Rotation ensures every junior pairs with every senior over two quarters.
- Each IC on the team has one named AI-off artifact for the quarter, pre-chosen, with the 30-minute retro 1:1 on the calendar.
- The judgement-weighted review pass has a documented amendment to the review standard naming the affected task-types.
- Every carve-out has a one-sentence rationale pointing at Exercise 01.
- Total overhead budget: 2–4 hours per IC per quarter; the schedule carries the tot-up.
- The schedule lands on the ritual calendar.
- A new IC reading the one-page artifact can identify, in under a minute, which carve-out applies to them in which week.
- A change-log entry naming the senior-IC co-reviewer, the junior-IC co-reviewer, and the adjustments produced.

## Stretch goals

- **A measurement appendix.** Add a half-page naming the leading-indicator signals you expect to see over the quarter (specific retro content, specific 1:1 answers, specific review outcomes). Reference the Exercise 04 prompts as the measurement site.
- **An AI-off artifact per role, not per IC.** For teams with clear role diversity (platform, product, infra, data), author a *role-specific* AI-off artifact template that each IC in that role takes from the template. This reduces per-IC design overhead at the manager's end.
- **A fallback plan.** Author a 1-paragraph plan for what happens if the team hits a production crisis in week 4 that pulls the carve-outs off the calendar. The plan names *which* carve-outs are deferred and *by when they return*. The plan is where the "run them for a year" discipline is encoded.
- **Second-order instrumentation — a baseline measurement.** At the start of the quarter, each IC rates themselves (private to them) on Axis A of the Chapter 6 ladder for a specific task-type. At quarter-end, they rate themselves again. The private delta, viewed in the end-of-quarter 1:1, is a soft signal on whether the deliberate practice is building the capacity it is meant to build.
- **Cross-team schedule compare.** If a peer manager in your organisation is running mod-107, trade schedules and discuss where they differ. Differences surface what is contextual vs. what is universal in carve-out design.
