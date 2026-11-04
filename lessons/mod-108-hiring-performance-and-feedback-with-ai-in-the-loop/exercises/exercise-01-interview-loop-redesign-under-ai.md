# Exercise 01 — Interview Loop Redesign Under AI

**Estimated effort:** 3 hours.

## Objective

Produce **v0.1 of your team's AI-augmented interview-loop redesign**: a 4–6-page artifact that, for each stage of the interview loop your team runs, names the signal the stage is supposed to produce, chooses one of the four AI-use policies, writes the stage-level rubric (including an agent-use criterion and an anti-collapse judgement criterion where applicable), and specifies the rater-calibration protocol you'll run before the redesigned loop goes live.

The deliverable is the loop description the recruiting coordinator, the panel raters, and (where in scope) HR will run against. The structured-interview methodological anchor is [Google re:Work's *Guide to Structured Interviewing*](https://rework.withgoogle.com/guides/interviewing-leverage-work-sample-tests/) composed with the [EEOC adverse-impact framing](https://www.eeoc.gov/laws/guidance/select-issues-assessing-adverse-impact-software-algorithms-and-artificial) for selection-outcome accountability.

## Prerequisites

- [Chapter 1](../01-the-hiring-and-performance-problem-under-ai-augmentation.md) — the hiring pillar scope and what is new under AI augmentation.
- [Chapter 2](../02-interview-loop-redesign-under-ai.md) — the stage-signal method, the four AI-use policies, rubric structure, rater calibration.
- [Chapter 6](../06-ai-in-hiring-legal-and-compliance-framing.md) — the compliance framing you compose with when the loop uses any automated employment decision tool (Exercise 05 produces the full checklist; this exercise flags the triggers).
- Your team's **current interview loop**: the stages, the current rubric (if any), the current AI-use policy (explicit or implicit), and 2–3 recent debriefs you can anonymise and re-read against the redesign.
- Access to a partner recruiter / recruiting coordinator for a 30-minute review of the redesign's logistical implications.

## Problem statement

The loop your team runs today was authored for an unassisted candidate. Under AI augmentation the signal each stage produces is noisier than the rubric assumes, specifically in three places: (a) the live-coding stage's correctness signal is confounded with whether the candidate used an agent; (b) the design-round signal is compressed because many candidates draft comparable surface-quality designs with agent assistance; (c) the implicit AI-use policy ("it's not mentioned, so candidates guess") produces inconsistent candidate experience and inconsistent scoring across raters.

The redesign does not rewrite the loop end-to-end. It is a **targeted refactor** of three things, per stage: the signal statement, the AI-use policy, and the rubric criteria. Rater calibration is the fourth piece; it is not a per-stage artifact but a one-afternoon panel exercise that makes the per-stage work land.

The common failure mode this exercise prevents is specific: redesigning the AI-use policy *before* writing the signal statement per stage. Teams that start with "we'll allow AI because the role is AI-augmented" produce a loop that is permissive but inconsistent across raters because the raters are scoring different things. Writing the signal first is the chapter's load-bearing move; the exercise's step order enforces it.

## Steps

1. **Pull the current loop onto one page.** List every stage in sequence: name, length, rater count, current rubric (even if informal). Include the phone screen, every technical round, the behavioural / cross-functional round, and the final round. If any stage uses an AI tool (resume screening, scheduling, interview-notes assistant, structured scoring), flag it — this is the Chapter 6 compliance trigger and composes into Exercise 05.
2. **Write the stage signal statement for each stage.** Two sentences per stage: what the stage is supposed to measure, and how the stage differentiates between a hire and a no-hire candidate. Write the statements before any discussion of AI-use policy. If a stage's signal statement doesn't differentiate — "we're trying to see if they're a good fit" — the stage is miscalibrated regardless of AI; rewrite the signal.
3. **Choose the AI-use policy per stage.** For each stage, pick one of: AI-permitted (encouraged), AI-permitted (disclosure required), AI-off control, take-home with walk-through. Write the one-sentence reason for the choice, grounded in the signal statement from Step 2. Challenge the choice by asking *"if I ran this stage under the opposite policy, would the signal get stronger or weaker?"* — at least one policy choice usually flips on this check.
4. **Author the stage-level rubric.** Four to six criteria per stage, 1–5 scale, specific behavioural anchors for each anchor level. Rubric criteria must include: (a) an agent-use criterion on every AI-permitted stage; (b) an anti-collapse (judgement) criterion on every stage that measures judgement; (c) a narration criterion on every disclosure-required stage. Anchors at 1, 3, 5 at minimum; anchors at 2 and 4 are useful but can be derived. Write out at least one worked example of a 1-, 3-, and 5-scored answer per criterion on the most load-bearing stage (typically the live-coding or the design round).
5. **Author the rater-calibration protocol.** Three exercises for every rater who will be on the loop: watch-and-score (on a recorded mock or shadow interview), score-a-previous-candidate (on an anonymised recent case), disclosure-stage role-play. One 90-minute panel session the week before the redesigned loop goes live. Write the specific agenda, the materials needed, and the follow-up corrections protocol (what happens when two raters score the same case more than 1 point apart).
6. **Flag Chapter 6 compliance triggers.** For every tool the loop uses that could meet the NYC LL 144 AEDT definition or the EU AI Act Annex III scope (resume screening, scheduling-with-scoring, transcript analysis, structured-interview-scoring automation, video analysis), write a single-sentence trigger note that routes into Exercise 05. If no tool triggers, write "no AEDT trigger in the loop" explicitly.
7. **Document what the loop does not measure.** Short section, five lines max: long-horizon judgement (handled via references), ramp rate (handled via the [`mod-105`](../../mod-105-team-ai-enablement-programs/) ramp plan), mentorship (unless a specific stage measures it), "cultural fit" (replace with behavioural criteria). The explicitness protects against later over-claiming in offer or debrief conversations.
8. **Co-review with the recruiter, HR partner, and one senior IC on the panel.** Thirty minutes each.
   - Recruiter: *"is the loop runnable at the length and complexity authored? Any candidate-side friction I'm not seeing?"*
   - HR partner: *"do any of the stage-level rubric criteria or AI-use policies conflict with our process requirements or compliance posture?"*
   - Senior IC: *"does the rubric match what you would score for, on the stages you run?"*
   - Record feedback and corrections in the artifact's change-log.
9. **Decide rollout.** Default: redesigned loop takes effect for candidates whose first screen is scheduled 4–6 weeks from now. Candidates already in the loop complete under the prior rubric. Announce the rollout to the panel and recruiting; share the artifact and the rater-calibration date.

## Starter guidance

- **Signal first, policy second.** The step order is the chapter's load-bearing move; running the steps in the inverse order produces a loop with inconsistent scoring regardless of the care taken on the rubrics.
- **One AI-off stage at most.** A loop with more than one AI-off stage is measuring unassisted candidates under conditions the job does not reproduce. If the role has two genuinely unassisted-work slices, one AI-off stage can score both via a short sub-exercise inside a larger stage.
- **Behavioural anchors, not aspirational phrases.** *"5: named three trade-offs unprompted, picked one deliberately with a stated rationale, implemented against it, revisited the rationale when a test failed"* beats *"5: strong trade-off thinking."* The rubric's reliability comes from the specificity of the anchors.
- **Narration criterion is scored down for silence, not scored neutrally.** A disclosure-required stage where the candidate runs in silence has produced no signal. Rate it accordingly; do not score as middle.
- **"Cultural fit" is replaced, not retained.** EEOC exposure plus low inter-rater reliability. Replace with specific team-behaviour criteria (feedback-giving and feedback-receiving behaviour, for example) and score those behaviours.
- **The compliance trigger note is a one-sentence flag, not the full checklist.** Exercise 05 produces the full checklist; this exercise just makes sure the loop surfaces every trigger that composes into it.
- **Do not add a "vibe check" round under any name.** Unstructured final rounds are low-validity, high-adverse-impact, and especially bad at reading AI-augmented work. If the organisation insists on a "culture round," bring it under the structured frame with specific behavioural criteria or route it out of your team's loop with the HR partner.
- **Calibrate against your own prior hires.** If the redesigned rubric scores someone the team hired last year as a clear no-hire, re-examine the rubric — the rubric may be calibrated against a different team than the one you are hiring for.
- **Length guidance.** 4–6 pages for the loop description, including stage-level rubrics with anchors. One additional page for the rater-calibration protocol. One additional page for the compliance trigger notes. More than 10 pages total is over-written.

## Acceptance criteria

The artifact is complete when:

- Every stage of the current loop has: a two-sentence signal statement, a one-of-four AI-use policy choice with reason, and a 4–6-criterion rubric with 1–5 anchors.
- Agent-use criterion appears on every AI-permitted stage; anti-collapse (judgement) criterion appears on every stage that measures judgement; narration criterion appears on every disclosure-required stage.
- At least one stage (typically the live-coding or design round) has worked example answers at 1-, 3-, and 5-scores on each criterion.
- A rater-calibration protocol with a specific 90-minute agenda, materials, and follow-up corrections rule.
- Every AI tool in the loop that could trigger NYC LL 144 or EU AI Act Annex III has a one-sentence trigger note that composes into Exercise 05, or an explicit "no AEDT trigger."
- A "what the loop does not measure" section exists and routes the un-measured signal to the right adjacent artifact (references, mod-105 ramp plan, etc.).
- A change-log entry names the recruiter, HR partner, and senior IC reviewers and the corrections produced.
- A rollout date and communication plan are named.
- An IC rater newly added to the panel could read the artifact and score a candidate consistently with another rater who had been on the panel for a year.

## Stretch goals

- **Shadow a candidate through the redesigned loop internally.** Run a senior IC on the team through the redesigned loop as a mock candidate, scoring independently against the new rubric. The exercise surfaces real rater drift before any external candidate is affected.
- **Write a one-page candidate-facing explainer.** What the loop measures, what the AI-use policy per stage is, what the candidate should bring. Candidates who know what the loop measures produce clearer signal than candidates who have to infer.
- **Map the loop to the ladder axes.** For each stage, name which of [`mod-107` Chapter 6](../../mod-107-skill-growth-anti-atrophy-and-career-development/06-career-ladder-under-ai-augmentation.md)'s Axes A / B / C the stage is supposed to produce signal on. Stages that map to no axes are candidates for removal; axes with no stage coverage are a gap.
- **Add one role-specific disclosure-stage prompt.** A single prompt specifically tailored to your team's domain (not a generic "walk me through your use of AI") that produces the narration signal the rubric scores. Your team's domain (data platform, infrastructure, product-eng, research, etc.) suggests the shape.
- **Draft the debrief template.** The specific written form raters submit after the loop. Standardises what gets captured for the hire decision, composes with the Chapter 6 record-retention obligations under EEOC / Title VII.
- **Composes with Exercise 05.** Walk every compliance trigger flagged in Step 6 through the Exercise 05 checklist and produce the composed artifact.
