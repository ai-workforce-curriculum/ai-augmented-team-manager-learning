# Chapter 2 — The Day 0 / 30 / 60 / 90 Structure for a 5–30 Person Team

> *The 30/60/90 is not a Gantt chart. It is a four-checkpoint contract between the learner, the manager, and the team — "here is where we expect you to be, here is how we will know, here is what we do if you aren't."*

## Motivation

R5 is explicit on the structural shape: *"Day 0 / 30 / 60 / 90 structure for a 5-30 person team, running internal bootcamps, workshops, communities of practice."* The 30/60/90 template is a staple of the engineering-manager playbook (every new-hire onboarding doc, every mid-year reset, every post-reorg re-grounding uses some version of it). What is distinctive to mod-105 is that the four checkpoints are **cohorted**, **artifact-producing**, and **anchored to each engineer's join-the-programme date**, not the calendar quarter.

Why cohorted and not individual-track: enablement is a *social* intervention. [Etienne and Beverly Wenger-Trayner's *Communities of Practice* framing](https://www.wenger-trayner.com/introduction-to-communities-of-practice/) is the research anchor for Chapter 3's sustaining format, and it carries into the structure here — fluency grows through mutual engagement around a shared repertoire, not through solitary self-study. A cohort of four engineers on Day 20 learning Cursor together will outrun four engineers on Day 20 learning Cursor alone, even if you give them identical materials.

Why artifact-producing and not event-driven: see [`Chapter 1 § Failure C`](01-team-enablement-as-a-manager-artifact.md) — a programme is measured by the artifacts produced on the real codebase, not by events completed. Every one of the four checkpoints produces or reviews a concrete artifact.

Why anchored to the join-the-programme date and not the calendar quarter: new engineers, re-orged engineers, and engineers on a new tool join the programme on different dates. A calendar-locked programme stalls them; a date-anchored programme keeps the cohort cadence meaningful.

This chapter sketches the four checkpoints and the structural choices behind them. Chapter 3 goes deep on the *delivery formats* (bootcamp, workshop, community of practice) that fill the time between the checkpoints. Chapter 5 goes deep on the *measurement artifacts* each checkpoint produces.

## Core concepts

### The four checkpoints

The programme is four dated events, not 90 continuous days of content.

**Day 0 — Stage pin + budget assignment.** A 45-minute conversation with the engineer (and, in cohorts, a 60-minute cohort kickoff). Scores each engineer 1–4 on each of the four tool categories from [`mod-101 Chapter 5`](../mod-101-ai-augmented-team-manager-position-and-contract/05-the-manager-ai-fluency-bar.md) — coding assistant, general-purpose assistant, eval tool (reading level), agent-authoring environment (reading level). The scoring is the input into Chapter 4's budget allocation. Produces **one artifact** per engineer: a dated stage sheet signed by the engineer and the manager.

**Day 30 — First-successful-PR-with-tool checkpoint.** By Day 30, every engineer should have at least one *merged* PR that they authored *with* the team's primary AI coding assistant, reviewed by a human, in the production repo. Not a demo repo, not a training sandbox. Chapter 5 details the artifact definition. Produces **one artifact** per engineer: the PR itself plus a two-paragraph reflection (what the tool did well, where it got in the way, what the reviewer caught).

**Day 60 — Pair-with-agent reflection.** By Day 60, every engineer has completed one *delegation-to-agent* task — a scoped work item (not a trivial one) that was authored by the engineer, handed to an agent (Claude Code, Cursor agent mode, Devin, whatever your team uses), reviewed on return, and either merged or explicitly rejected. The reflection is a one-page write-up on what delegating looked like and where the engineer intervened. Chapter 5 details the format. Produces **one artifact** per engineer.

**Day 90 — Review-of-your-review + graduation decision.** By Day 90, the engineer re-reads their *own* review of an agent-generated PR they merged 30+ days earlier, and writes a short reflection on what they would do differently. The manager and engineer meet, walk the four artifacts (Day 0 stage sheet, Day 30 PR + reflection, Day 60 pair reflection, Day 90 self-review), and make one of three graduation decisions: *(a) graduate into the community of practice as a participating peer; (b) extend the programme by 30 days in a specific lane; (c) off-ramp the engineer's expectation on a specific tool if the tool is not fit for their work.* Chapter 5 details the self-review template.

Four checkpoints, four artifacts. The programme between checkpoints — the bootcamps, the workshops, the pair-with-mentor sessions, the community-of-practice attendance — is the *support structure*. The checkpoints are where fluency is read.

### Why those four specifically

Each checkpoint is chosen to be *specific enough to produce evidence* and *generic enough to apply across stacks*. The research anchors from Chapter 6 underwrite the picks:

- The **first-successful-PR-with-tool** is the operational echo of Peng et al. (arXiv:2302.06590) — the earliest and most-cited quantitative result on AI-coding-assistant productivity measured real task completion, not hours-logged-in-IDE. Your team's equivalent to "real task completion" is "a merged PR on the production repo"; that is the artifact.
- The **pair-with-agent reflection** is the operational echo of Dell'Acqua et al.'s jagged-frontier framing — Dell'Acqua's experimental design had consultants *reflect* on where the AI helped and where they over-trusted it. A reflection on a real task is a stronger instrument than a tool-usage dashboard, because it surfaces the specific *failure modes* the engineer encountered.
- The **review-of-your-review** is the operational echo of Brynjolfsson-Li-Raymond's finding that gains compound unevenly across tenure — the self-review surfaces the engineer's *own trajectory*, which a snapshot cannot. It is also where [Bersin's AI-in-L&D framing](https://joshbersin.com/) pays off: Bersin's "capability academy" model stresses that capability lands when learners explicitly articulate what they now know that they didn't before, in their own words. The review-of-your-review is that artifact.

Chapter 5 specifies the templates.

### Cohort sizing: 3 to 6 is the sweet spot

For a 5–30-person team, you do not run one programme with everyone at once. You run cohorts.

- **Cohort size 3–6.** Small enough for every engineer to speak in a 60-minute session. Large enough that a quieter engineer can learn by listening, not just by producing.
- **Cohort composition: mixed stage, not mixed seniority.** Mix engineers with different *learning stages* on the primary tool — e.g. two at stage 1 (never used), one at stage 2 (used in side projects), one at stage 3 (used in production). This is the Brynjolfsson-Li-Raymond finding operationalised: the stage-2 engineer learns from the stage-3 engineer *specifically*, and the stage-1 engineer learns the questions to ask by hearing stage-2 ask them. A cohort of four stage-1 engineers learns slower than a mixed cohort.
- **Cohort cadence: launch every 4–6 weeks.** For a 20-person team, you might run three overlapping cohorts across a quarter, with the first cohort hitting Day 90 the same month the third cohort hits Day 0.
- **Cohort continuity: same cohort for all 90 days.** The social-capital investment in a cohort is wasted if you reshuffle at Day 30.

For a 5-person team, "cohort" = the whole team, once. For a 30-person team, "cohort" = roughly 5–6 overlapping groups of 5 over the first half year.

### Anchoring to the engineer's date, not the calendar

Two logistical traps to name:

- **The "we'll start on Jan 2" trap.** A programme that locks to the fiscal year will push every new hire (and every re-tooling existing engineer) to wait until next quarter. Fluency does not survive six weeks of waiting. The engineer forms their own habits, which you now have to break.
- **The "we'll run it when we have time" trap.** The programme has no schedule, so it never runs. The team's "AI enablement" is a Slack channel nobody reads.

The fix is the **rolling cohort**: Day 0 is anchored to each engineer's start on the programme. A given calendar week typically sees one cohort at Day 7, one at Day 30, one at Day 75. The manager's calendar carries the schedule; the programme does not wait for a calendar quarter to kick off.

### What goes on the four-checkpoint timeline

The space between checkpoints is not filler. A workable 90-day timeline for one cohort (see Chapter 3 for the format specifications):

| Day | Event | Format | Chapter |
|---|---|---|---|
| 0 | Cohort kickoff + individual stage pins | 60-minute group + 45-min 1:1s | this chapter, Ch 4 |
| 1–10 | Tool bootcamp (primary AI coding assistant) | 3–4 half-day sessions over two weeks | Ch 3 |
| 11–20 | Pair-with-mentor on real-work tasks | In-the-flow, not scheduled | Ch 3 |
| 14–30 | First-successful-PR-with-tool lands | Produced artifact | Ch 5 |
| 30 | Day 30 checkpoint 1:1 | 45 minutes | Ch 5 |
| 31–45 | Topic workshops: review-of-agent-PRs, prompt authoring, context composition | 60–90 min, weekly | Ch 3 |
| 45–60 | Agent-delegation practice session | 2-hour scheduled session + follow-up | Ch 3 |
| 50–60 | Pair-with-agent reflection lands | Produced artifact | Ch 5 |
| 60 | Day 60 checkpoint 1:1 | 45 minutes | Ch 5 |
| 61–89 | Community of practice attendance (bi-weekly) | Community cadence | Ch 3, Ch 7 |
| 75–90 | Review-of-your-review lands | Produced artifact | Ch 5 |
| 90 | Day 90 checkpoint + graduation decision | 60-minute 1:1 | Ch 5, Ch 8 |

This is one shape. A team whose primary tool is different, or whose density of work does not sustain the pair-with-mentor phase in that window, will ship a different shape. The four checkpoints are the invariant; the content between is the dial.

### Who is *in* the programme — and who is not

A mod-105 programme runs on **everyone on the team**, not just new hires. Three populations:

- **New hires joining the team.** Day 0 is literally their first week. Pair with onboarding.
- **Existing engineers starting on a new tool the team has rolled out.** Day 0 is the rollout date for that tool. A programme that excludes existing engineers from new-tool enablement is the "licence drop" failure mode from Chapter 1.
- **Existing engineers who stage-pinned below 2 on a core tool at the Chapter 4 budget assessment.** Day 0 is the date you had the budget conversation. You do not leave a stage-1 engineer on the Cursor rollout to figure it out.

Who is *not* in the programme: engineers who stage-pinned at 3+ on all core tools. They graduate directly into the community of practice (Chapter 3), act as pair-with-mentor volunteers (Chapter 3), and contribute to the pattern library. They are the programme's leverage.

### When the programme breaks and how to notice

Three failure signatures that show up in the first two cohorts:

- **Day-30 PR slippage.** The first cohort's engineers are at Day 30 and only one of four has a merged PR with the tool. Causes to check: (a) the primary tool does not fit the team's work (if the work is in an unusual framework, the tool may be stage-blocked); (b) the pair-with-mentor phase (Days 11–20) did not actually happen; (c) the production repo has review-standard barriers that prevent an in-progress learner from merging. The manager owns the remediation — potentially an extension or a tool-fit reconsideration (Chapter 8's graduation decision scale), not a shaming conversation.
- **Day-60 reflection vacuity.** The pair-with-agent reflections read as marketing copy for the tool. Cause to check: the delegation-to-agent task was *too small or too script-like* for the reflection to surface genuine friction. Move the next cohort's delegation task up one level in difficulty.
- **Day-90 self-review is a copy-paste.** The review-of-your-review reads identically to the original review, with no change-of-mind. Cause to check: the 30-day gap is too short for a specific engineer's work cadence (a once-a-month shipper may need a 60-day gap). Adjust next cohort; keep the artifact.

Each failure signature is a programme-design signal, not a performance signal on the engineer. Chapter 5 builds in the rubric for distinguishing the two.

## Example: a 20-person platform team's 90-day calendar sketch

Treat as calibration, not a template.

> **Team shape.** 20 engineers, platform infra, mixed seniority (3 L25-equivalent, 12 L20-equivalent, 5 L15/new-grad-equivalent), rolling out Cursor as the primary AI coding assistant Q1 2026, Claude Code as agent-authoring environment Q2 2026.
>
> **Q1 cohort plan.** Three overlapping cohorts of 5 engineers each (one stage-1, two stage-2, two stage-3 mix per cohort per Chapter 4's budget rubric), starting at weeks 1, 5, and 9 of the quarter. Remaining five engineers join Q2 cohorts.
>
> **Shared programme calendar.**
> - *Cohort A* (weeks 1–13): Day 0 kickoff week 1; bootcamp sessions weeks 1–2; pair-with-mentor weeks 2–3; first-successful-PR by end of week 4; Day 30 checkpoint week 4; topic workshops weeks 5–7; delegation session week 8; Day 60 checkpoint week 8; community of practice starts week 9; Day 90 week 13.
> - *Cohort B* (weeks 5–17): same shape, 4-week offset.
> - *Cohort C* (weeks 9–21): same shape, 8-week offset.
>
> **Shared delivery load.** Manager authors curriculum (~6 hours up-front, ~1 hour/week during delivery). Senior IC volunteers run two of five topic workshops per cohort (~3 hours/cohort). L&D partner handles intake, scheduling, calendar logistics (~2 hours/cohort). Platform runs the tool-onboarding for each cohort's first week (~1 hour/cohort). Community of practice from week 9 onward is self-sustaining (Ch 3).
>
> **Dashboard tie-in.** All four checkpoint artifacts link into the mod-104 ROI narrative. The Day-30 PR count per cohort is a leading indicator in the Speed tile (Ch 2 of mod-104); the Day-60 pair-with-agent reflections feed into the Effectiveness tile's qualitative sidebar.

This shape is one week of up-front authoring time plus ~2 hours/week of manager delivery time per cohort, for a programme that moves 15 engineers through to graduation inside a quarter. The remaining 5 engineers enter the Q2 cohorts.

## Summary

- Four checkpoints — Day 0 (stage pin + budget), Day 30 (first-successful-PR-with-tool), Day 60 (pair-with-agent reflection), Day 90 (review-of-your-review + graduation decision). Each produces one artifact.
- The *programme* is the artifacts and the checkpoints; the *delivery* between is the bootcamp / workshop / community-of-practice mix from Chapter 3.
- Cohort sizing: 3–6 engineers, **mixed stage not mixed seniority**, same cohort for 90 days.
- Anchor to the engineer's join-the-programme date, not the calendar quarter. Launch a new cohort every 4–6 weeks for larger teams.
- Everyone on the team is in some version of the programme; stage-3+ engineers graduate directly into the community of practice as pair-with-mentor volunteers.
- Three common failure signatures — Day-30 PR slippage, Day-60 reflection vacuity, Day-90 self-review copy-paste — each is a programme-design signal, not a performance signal.
- Exercise 01 produces the dated 90-day plan for your actual team.
