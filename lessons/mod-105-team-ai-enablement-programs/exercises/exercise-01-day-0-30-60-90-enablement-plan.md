# Exercise 01 — The Day 0 / 30 / 60 / 90 Enablement Plan

**Estimated effort:** 2 hours.

## Objective

Produce a **dated, team-specific Day 0 / 30 / 60 / 90 enablement plan** for your real team (or the team shape you are preparing to inherit). The output is a one-page `docs/mod-105-plan.md`-style artifact that another engineering manager could read and run the first cohort from without a follow-up meeting.

This is the first of the five mod-105 artifacts you will produce; Exercises 02–05 each take a different slice of the programme and are internally consistent with this one.

## Prerequisites

- Chapters 1, 2, and 3 of this module.
- A working mental model of your team's current workflow (primary tools in use; typical PR cadence; review-standard maturity from `mod-103`).
- Read-level familiarity with the Chapter 4 learning-stage rubric — you will reference it here even though Exercise 02 is where you build it in full.
- Optional but useful: [`mod-101 Chapter 5`](../../mod-101-ai-augmented-team-manager-position-and-contract/05-the-manager-ai-fluency-bar.md) for the five-tool fluency vocabulary your stage pins will draw on.

## Problem statement

Many engineering managers inherit an enablement situation that is some combination of (a) a vendor-run workshop someone booked last quarter, (b) "everyone has a Copilot seat now," and (c) a Slack channel called `#ai-practice` with 14 messages in it from February. The composite is not a programme; it is three disconnected interventions. Your job is to turn this into a coherent 90-day structure with four checkpoints, cohorted delivery, and measurement artifacts — without doubling your calendar load.

Specifically, you are writing the plan a *specific cohort* will walk through in a *specific quarter*, not an abstract framework document. The plan names the dates, the people, the delivery hours, the artifact targets, and the partner interfaces.

## Steps

1. **Pick the cohort.** A specific group of 3–6 engineers from your team who are starting the programme on a specific Day 0. If your team is larger than 6, pick one of the overlapping cohorts; the other cohorts follow the same shape.
2. **Pin each engineer's starting stage.** For each cohort member, write a 1–4 stage pin on each of four tool categories: AI coding assistant, general-purpose assistant, eval tool (reading level), agent-authoring environment (reading level). Use the Chapter 4 rubric sketch; Exercise 02 will flesh the rubric out formally. For this exercise, a first-pass set of pins is enough.
3. **Set the Day 0 event.** A dated 60-minute cohort kickoff + three to six dated 30–45 minute 1:1 budget conversations. Specify: who attends, where/how, what each engineer leaves with (a signed stage sheet + a cohort placement).
4. **Lay out the bootcamp (Days 1–10).** Chapter 3 sketches a 5-session shape. For your cohort, specify: which tool is the bootcamp's subject (the team's primary AI coding assistant); who delivers each session (manager, senior IC name, vendor trainer, L&D partner); specific dates and durations; which real-repo artifacts each session produces or edits.
5. **Set the pair-with-mentor window (Days 11–20).** Specify: which stage-3+ engineer on your team is paired with each cohort member; the mechanism (in-the-flow pair sessions vs. scheduled; async review turnaround expectation); the first-successful-PR-with-tool target date for each engineer.
6. **Set the Day 30 checkpoint.** Dated 45-minute 1:1 per engineer. Specify: artifact walked (the PR + its reflection); the diagnostic you run if the PR has slipped (Chapter 2 names three causes); what the output of the 1:1 is (confirm stage pin, flag any at-risk engineer, book Day 60).
7. **Lay out the workshop phase (Days 31–60).** Specify: ~4–6 workshop topics from Chapter 3's candidate list (adjusted to your team's gaps); who delivers each; dates; co-attendance by any overlapping cohort.
8. **Set the Day 45–60 delegation task.** A specific *non-trivial* work item each engineer will delegate to an agent and produce a pair-with-agent reflection on. Specify: how the task is chosen (engineer picks? manager assigns? backlog slot?); the reflection template (Chapter 5's five sections); the Day 60 checkpoint 1:1 date.
9. **Fold the cohort into the community of practice (Days 61–90).** Specify: when the cohort starts attending CoP sessions; who facilitates each session they attend; whether the cohort contributes a show-and-tell; the review-of-your-review target lands between Day 75 and Day 90.
10. **Set the Day 90 graduation 1:1.** 60-minute per engineer. Specify: all four artifacts walked (stage sheet, Day-30 PR + reflection, Day-60 pair reflection, Day-90 self-review); one of three graduation decisions made (graduate to CoP as peer; extend 30 days in a specific lane; off-ramp the tool for this engineer). Document the decision in writing.
11. **Write the partner interfaces.** One line each for HR, L&D, Platform: what they do during this 90-day period. Reference Exercise 04's / Chapter 7's partnership contract where relevant.
12. **Freeze v0.1.** Title: `mod-105 90-Day Enablement Plan v0.1 — [team name] — Cohort [N] — [Day 0 date]`. Author (you). Reviewers (one senior IC on the team; your L&D partner if one is assigned). Scope-and-caveats paragraph. Change log.

## Starter guidance

- The plan is *dated*, not generic. "Day 1" is a specific calendar date. "Wednesday week 3" is not.
- A 90-day plan for a 5-person cohort typically fits on one printed page if you keep each step to 2–3 lines. If your draft is running past two pages, you are over-specifying content instead of the structure — content belongs in the curriculum docs each workshop session references, not in the plan itself.
- The *authoring-vs-delivery split* from Chapter 1 and 3 should be visible in the plan: for each session that has a delivery owner, the plan references a curriculum doc (which you, the manager, author). The plan itself is not the curriculum.
- For a cohort that is all stage-1 on the primary tool, the bootcamp is the heaviest week; for a cohort that is mostly stage-2+ on the primary tool, the bootcamp compresses and the workshop phase expands.
- The partner interfaces (step 11) can be one-liners. Exercise 04 and Chapter 7 are where you work them out in depth; the plan just references.
- Treat the plan as something the senior IC running Sessions 2 and 3 should be able to read and work from. If the IC would need a 30-minute explainer to execute from the plan, add specificity to the plan.
- If your team is 5 engineers, "cohort" = whole team, one time. The plan is still the same shape; the cohort section just names everyone.

## Acceptance criteria

The plan is complete when:

- A specific cohort (3–6 engineers by name or role) is named, with a specific Day 0 date.
- Each cohort member has a first-pass stage pin on all four tool categories.
- The Day 0 event is dated, has an attendance list, and produces signed stage sheets.
- The bootcamp (Days 1–10) has 4–5 sessions scheduled, each with a delivery owner, a date, a duration, and a real-repo artifact.
- The pair-with-mentor window (Days 11–20) names which stage-3+ engineer is paired with each cohort member.
- The Day 30 checkpoint is dated per engineer, with an artifact (PR + reflection) that the 1:1 walks.
- The workshop phase (Days 31–60) names 4–6 workshop topics with delivery owners and dates.
- A specific Day 45–60 delegation task is specified (either picked individually by each engineer or assigned by the manager; both are acceptable).
- The Day 60 checkpoint is dated per engineer and walks the pair-with-agent reflection.
- CoP attendance (Days 61–90) is specified; if your team does not yet have a CoP, the plan names the stand-up (and links to Exercise 04).
- The Day 90 graduation 1:1 is dated per engineer and walks all four artifacts; the three possible graduation decisions are listed.
- Partner interfaces (HR / L&D / Platform) are one-lined per partner; references cross to Exercise 04 / Chapter 7.
- The artifact is titled, dated, lists contributors, carries scope-and-caveats, carries a change log.
- The plan fits on one to two pages when printed, and the IC delivering Sessions 2–3 can work from it.

## Stretch goals

- **Multi-cohort overlay.** If your team is >6 engineers, overlay a second and third cohort on the same 90-day window, staggered by 4–6 weeks (Chapter 2's rolling-cohort pattern). Flag which weeks have two cohorts' events running concurrently and verify your manager delivery load stays under 5 hours/week sustained.
- **Shared-infrastructure line item.** If you share the Platform / L&D delivery pool with other teams, add a one-line statement of what you are drawing on (e.g. "L&D partner is 20% allocated to this programme this quarter; shared with Developer Experience team"). Shared infrastructure that is not named becomes shared infrastructure that is overbooked.
- **One at-risk pathway.** For the plan's lowest-stage engineer, write a one-paragraph "if the Day 30 PR doesn't land" branch. What is the signal, what is the manager-side response, and what does the extension look like.
- **Six-month sunset check.** Add a line at the top: *"this plan is reviewed six months from Day 0."* Put it in your calendar. A plan that does not sunset drifts.
- **Pre-bootcamp pre-read.** Write (or draft the shape of) a one-page pre-read each cohort member reads before the Day 0 kickoff. Known-good items: a short team-specific tool-overview, a link to the current review standard, the first-successful-PR definition.
