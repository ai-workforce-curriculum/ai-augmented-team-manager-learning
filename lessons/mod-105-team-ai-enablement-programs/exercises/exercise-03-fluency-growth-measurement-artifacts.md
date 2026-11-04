# Exercise 03 — The Fluency-Growth Measurement Artifact Set

**Estimated effort:** 3 hours.

## Objective

Operationalise the three fluency-growth measurement artifacts for your team — the **first-successful-PR-with-tool**, the **pair-with-agent reflection**, and the **review-of-your-review** — as a coherent, team-specific measurement set that your Day 30 / 60 / 90 checkpoints read from. The output is a `docs/mod-105-measurement-set.md`-style artifact that includes: the three artifact templates adapted to your team; a scoring rubric for each; the cross-links into mod-103 review standards and the mod-104 ROI narrative; and a worked example that another manager on your team could score from without additional calibration.

## Prerequisites

- Chapters 2, 5, and 6 of this module.
- Your team's current mod-103 review standard (or the shape of it in draft, if `mod-103` has not been completed).
- Familiarity with Chapter 2 of `mod-104` (the AI-cost ratio tile) so the measurement-side of your output can cross-link coherently.
- One real agent-generated PR your team has merged in the last 60 days (used as the worked-example input in step 8).

## Problem statement

The three artifacts in Chapter 5 — first-successful-PR-with-tool, pair-with-agent reflection, review-of-your-review — are described at the general level. To actually run them on your team's work, each artifact needs: a concrete template adapted to your repo conventions; a scoring rubric a reviewer can apply consistently; and a clear statement of what the artifact *is* and *is not* so that engineers producing it do not drift it toward a marketing-copy format or a performance-review format. The failure modes Chapter 5 named — vague reflections, uncritical self-reviews, copy-paste change-of-mind — all stem from under-specified templates. Your job is to produce the specific versions.

Two framings to carry through:

- **The set is a *reading* instrument, not a *grading* instrument.** The manager reads the artifacts to form a view of fluency growth; the artifacts do not score engineers on a 1-10 scale. If you catch yourself trying to produce a point total, you are drifting into performance-management territory (Chapter 5's first scoring guardrail).
- **The set must survive your team's real work.** If your team's primary language is unusual, your primary review workflow is unusual, or your team's agent-authoring environment is custom, the templates adapt to those realities. A generic template is a weaker instrument than a team-specific one.

## Steps

1. **Adapt the first-successful-PR-with-tool template.** Write a half-page document that defines, for your team specifically: what counts as a "production" PR (which repos count, which do not); what counts as "with the tool" (any usage? agent-only? more than X% of lines?); what the two-paragraph reflection template looks like (format, where it is attached — PR comment, linked doc, a `reflections/` folder, etc.); and the Day-30 target.
2. **Adapt the pair-with-agent reflection template.** Write a full-page template with Chapter 5's five sections (task, delegation, handback, intervention, judgment) adapted to your team's agent-authoring environment and typical task shape. For "task," specify what counts as *non-trivial* on your team — the word "non-trivial" is where this template most often goes soft.
3. **Adapt the review-of-your-review template.** Write a half-page template with Chapter 5's three sections (original review, what held up, what didn't). Specify: the 30-day gap your team uses (shift if your team's shipping cadence is slower or faster); the agent-generated-PR definition the engineer picks from (same definition as step 1 to keep the artifacts coherent).
4. **Write the scoring rubric for each artifact.** Not a numeric rubric. For each artifact, write a one-paragraph description of what a *high-signal* submission looks like and what a *low-signal* submission looks like, with one or two concrete examples drawn from your team's work if possible. This is the manager's reading instrument.
5. **Write the programme-level read criteria.** From Chapter 5: a programme-level read at the quarter boundary aggregates patterns across the cohort. Write two to three concrete examples of what you would be looking for in the aggregation (e.g. *"if more than 50% of Day-60 reflections name the same ORM-related failure, that is a workshop topic for the next cohort and a rules-file update candidate"*).
6. **Cross-link to mod-103.** For the first-successful-PR artifact: write the one-sentence linkage to the current review standard. Engineers producing the PR and reviewers scoring it should reach for the same standard; if your team's review standard does not yet specifically address AI-authored PRs, note the gap and link to your mod-103 roadmap.
7. **Cross-link to mod-104.** Write the one-paragraph linkage explaining how each artifact's aggregate reading feeds (or doesn't feed) the mod-104 ROI narrative. The aggregate patterns at Day-60 and Day-90 are most likely to feed the Effectiveness tile's qualitative sidebar.
8. **Worked example — score one real PR.** Pick a real agent-generated PR from your team's recent work. Write the first-successful-PR-with-tool reflection *as if you were the engineer who authored it*. Then score it against your step 4 rubric. Capture: where was the template helpful; where did it feel awkward; what would you adjust.
9. **Walk the set with one senior IC.** Share the templates, rubrics, and worked example with one stage-3+ engineer on your team. Ask: *"would you write the Day-60 reflection from this template honestly, or would it push you toward a safe-and-vague response?"* Record their feedback and revise.
10. **Freeze v0.1.** Title: `mod-105 Fluency-Growth Measurement Set v0.1 — [team name] — [YYYY-MM-DD]`. Author (you). Reviewers (the senior IC from step 9; one engineer at a different stage). Scope-and-caveats paragraph. Change log. Review date six months out.

## Starter guidance

- Keep each artifact template short. The first-successful-PR reflection is *two paragraphs*, not two pages. The pair-with-agent reflection is *one page*, not four. The review-of-your-review is *half a page*, not two. A template that goes long will produce vague, long submissions.
- The *non-trivial task* definition in step 2 is the single most important sentence in this exercise. Write it carefully. A workable shape: *"non-trivial on this team means a work item the engineer would normally take 2+ hours on, touching more than one file, with a non-obvious correctness decision somewhere inside."*
- For step 4's scoring rubric, start with the *low-signal* example and work backward. The failure mode (marketing copy, copy-paste self-review, uncritical approval) is easier to describe than the success. The success is roughly: *not that*.
- The templates live where your team's work lives — the repo, the engineer's folder, the PR itself. They do not live in an LMS. Chapter 5's third scoping note is the reason.
- The worked example in step 8 is *your own writeup of someone else's PR*. Doing this yourself rather than asking the engineer to produce the first one calibrates you to the template before you send it to the team. Managers who skip this step underwrite low-signal first submissions.
- For teams that have never produced any of these artifacts, start with artifact 1 only. Get it running in one cohort cycle before layering artifacts 2 and 3. Chapter 2's four checkpoints are the ideal; sequencing matters when you are introducing the practice.

## Acceptance criteria

The set is complete when:

- A first-successful-PR-with-tool template is written with specific definitions of *production*, *with the tool*, *reflection format*, and *Day-30 target* for your team.
- A pair-with-agent reflection template is written with Chapter 5's five sections adapted to your team's agent environment and a specific *non-trivial task* definition.
- A review-of-your-review template is written with Chapter 5's three sections, a specific 30-day gap, and a specific agent-PR picking criterion.
- A one-paragraph high-signal / low-signal rubric is written for each of the three artifacts.
- Two to three programme-level read criteria are written with specific examples of aggregate patterns the manager will look for.
- Cross-links to the current mod-103 review standard and the mod-104 ROI narrative are written.
- A worked example exists: one real agent-generated PR, a reflection written by the manager, a score against the step 4 rubric, and a note on what the exercise surfaced about the template.
- One senior IC has reviewed the set and given feedback on whether the template would produce honest or guarded submissions; their feedback is recorded and the templates revised.
- The artifact is titled, dated, lists contributors, carries scope-and-caveats and a change log, and has a six-month review date.
- Each template fits within its target length (two paragraphs / one page / half a page respectively).
- The scoring rubrics are explicitly non-numeric; no 1-10 scale, no point total.

## Stretch goals

- **Cross-team template comparison.** Share the three templates (not the submissions) with another team-manager running a mod-105 programme. Compare the *non-trivial task* definitions, the reflection formats, and the scoring rubrics. Divergences are useful signal for the L45 handoff (Chapter 8).
- **Review-of-the-review at the manager level.** Once your first cohort has produced Day-90 self-reviews, write your own *manager-level* review-of-your-reading: given the artifact set the cohort produced, what would you adjust about the templates themselves? This is one of the most durable artifacts of the programme year-over-year.
- **Artifact decay check.** Three months after the first cohort has graduated, pull five of the Day-60 reflections and score them again against the step 4 rubric. Are the recent ones sharper or softer than the first cohort's? Which direction is a programme-signal to adjust?
- **Honest-signal pact.** Add a half-page "honest-signal pact" to the kickoff material — a written statement from you to the team that reflections that name specific failure modes of the tool are the ones you read as positive signals, and that the opposite shape (praise without specifics) reads as a programme-signal, not as a disqualification. Mention explicitly that the artifacts do not route into performance review.
- **Edge-case engineer.** For one engineer on your team who is operating at an unusual altitude (a staff+ engineer using AI tools you don't personally have fluency in, for example), write a one-paragraph note on how you intend to read their artifacts honestly despite the capability gap. The posture matters more than the mechanic.
