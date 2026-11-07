# Lab 03 — Exec Pre-Read Rewrite from a Broken Draft

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 6 (the four artifacts; the exec pre-read's seven sections; the "why this and not that" paragraph; the writing failure modes), with side-checks against Chapter 4 (survey discipline, four-question check) and Chapter 3 (kill criteria, adoption mode).
**Complements, does not duplicate:** Exercise 06 asks you to assemble the **full artifact set** for your real team — roadmap one-pager, decision log, and exec pre-read — and share it with a named audience. This lab hands you a deliberately broken exec pre-read draft for a fictional team and asks you to diagnose every failure mode in it, rewrite the two sections that matter most (industry context and "why this and not that"), and test the rewrite against three scripted exec questions. You run the fix on a fixed input here so you can calibrate your edit before you write under real exec pressure in Exercise 06.

## Objective

Read a broken exec pre-read draft. Diagnose every writing failure mode — marketing voice, hedging, undated/un-owned claims, missing alternatives, survey-headline copying, and drift from the task sort. Rewrite the **industry context** paragraph (Chapter 4 discipline) and the **"why this and not that"** section (Chapter 6 differentiator). Then pressure-test the rewritten draft against three exec questions, exactly as Exercise 06 step 7 asks you to do on your own pre-read.

## Prerequisites

- Chapter 6 read (four artifacts; the pre-read's seven sections; "why this and not that"; the writing failure modes; the cross-link map).
- Chapter 4 read (survey failure modes; four-question check; ranges-not-point-estimates; non-engineering disciplines).
- A blank file for your diagnosis and rewrites.

Useful but not required: Chapter 3 (so you can test whether the kill-criteria language in the draft is operational); Chapter 2 (so you can test whether the task-sort claims in the draft match the stated buckets).

## The fictional team (for grounding)

> **"Checkout Payments" team, GlobeShop Retail.** 12 engineers (1 staff, 4 senior, 7 mid/junior). Discipline: payments platform. Current horizon: Q1 2027. Three pilots and one opt-out rollout proposed. Audience of the pre-read: a VP of Engineering (name `@vp-eng`) who, per the manager's note, asks about cost every quarter and uses the word "throughput" rather than "velocity."

The exact details of the sort and sequence are not the point of the lab — the point is to diagnose how the draft is written and rewrite the two sections that matter most. Treat the team context as a frame.

## Steps

### Step 1 — Read the broken draft (5 min)

Below is "Checkout Payments — Q1 2027 AI Adoption Pre-Read v0.1." Read it once end-to-end before taking notes. Deliberately broken. Do not scroll past it until you are done reading.

```
CHECKOUT PAYMENTS — Q1 2027 AI ADOPTION PRE-READ v0.1

Executive summary
-----------------
We are embarking on a transformative journey to unlock the full potential
of AI-augmented engineering on the Checkout Payments team. We aim to
explore multiple innovative workflows this quarter and will be measuring
velocity to demonstrate value.

Industry context
----------------
Microsoft reports that 75% of knowledge workers use AI at work. McKinsey
says enterprise GenAI is "scaling rapidly." The Stack Overflow Developer
Survey shows developers love AI tools. We should be moving faster.

Risk
----
We will manage risk through careful rollout. No tasks are considered
dangerous.

ROI
---
This program will drive significant productivity improvements and
transform how the team works.

Why this plan
-------------
We looked at several options and this is the best one.

Partners
--------
We will coordinate with Platform and DevEx.

Ask
----
We ask for leadership's support for the plan.

Decisions so far
----------------
We've made several decisions this quarter.
```

### Step 2 — Diagnose failure modes, by section (15 min)

Chapter 6 names three writing failure modes (marketing voice, hedging, undated / un-owned) and describes seven required pre-read sections. Open your scratch file and, under a top-level heading **Diagnosis**, grade the draft section by section.

For each of the seven sections — Executive summary, Industry context, Risk, ROI, Why this plan, Partners, Ask, plus Decisions-so-far — write:

- **Marketing voice.** Which phrases? (Hint: "transformative journey," "unlock the full potential," "innovative," "drive significant," "transform how the team works" are the easy ones; find at least five.)
- **Hedging.** Which phrases? (Hint: "aim to explore," "will be measuring," "demonstrate value," "scaling rapidly" without a number, "should be moving faster," "manage risk through careful rollout," "best one," "will coordinate," "support for the plan," "several decisions.")
- **Undated / un-owned.** Which claims? (Hint: every statement in the draft; not a single ISO date, not a single `@name`, not a single falsifiable commitment.)
- **Specific Chapter 6 bar missed.** One line per section.

A worked example for the Ask section:

```
Ask
  Marketing voice: — (none; just vague.)
  Hedging: "ask for leadership's support for the plan" — not an ask.
  Undated / un-owned: no decision requested, no date, no owner.
  Chapter 6 bar: "A pre-read with no ask is a status update."
  The ask must name a specific resource, coverage, signal, or decision
  from the reader.
```

### Step 3 — Diagnose the industry-context failure modes (10 min)

The industry-context section is where Chapter 4's discipline either lands or does not. Under a heading **Industry context — Chapter 4 check**, run the Chapter 4 four-question check against each claim:

- **"Microsoft reports 75% of knowledge workers use AI at work."** Who is in the sample? How is "uses AI at work" defined? Compared to what? Does it match the other sources? (All four fail — the headline is a point estimate quoted out of methodology.)
- **"McKinsey says enterprise GenAI is 'scaling rapidly.'"** This is a direct quote with no number, no date, no edition, no methodology link.
- **"Stack Overflow Developer Survey shows developers love AI tools."** "Love" is not a survey finding; it is a mood. Sentiment ≠ intent-to-use ≠ trust (which Stack Overflow splits deliberately, per Chapter 4).
- **"We should be moving faster."** Chapter 4 names this exact move — "copy the headline into the plan" — as the standard first failure mode.

Write a one-paragraph verdict: this section does none of the four things Chapter 4 says the industry-context paragraph has to do. Note each failure explicitly; the fix in Step 5 depends on knowing what is broken.

### Step 4 — Diagnose the "why this plan" failure modes (5 min)

Chapter 6 names the "why this and not that" section as the **differentiator** — the section the exec reads most carefully, written in the voice of the question the exec will ask. Under heading **Why this plan — Chapter 6 check**:

- Does the section name any alternative that was *considered and not picked*?
- Does it give a reason — specific, falsifiable, in the vocabulary of the exec?
- Does it carry a trigger-to-revisit (Chapter 6 shape: "we revisit X if Y under Z duration")?

Expect to find: none of the three. The section is one sentence of pure assertion. Chapter 6: "A plan that cannot name its alternatives is a plan that has not been thought through — and leadership can usually smell it."

### Step 5 — Rewrite the industry-context paragraph (15 min)

Under a new heading **Industry context, rewritten**, write a 120–180 word paragraph (same budget as Exercise 04) that meets the Chapter 4 bar:

- Uses **ranges**, not point estimates.
- Names each source with the release date (use `<!-- needs-research: ... -->` for any specific percentage you would want to pull from the live survey rather than inventing one).
- Triangulates — a signal is "reasonably stable" only where two or three surveys agree.
- Names one specific place where this team's plan is **consistent** with the industry baseline and one where it **diverges**, with the reason for the divergence.
- Flat voice. No "we should be moving faster," no "scaling rapidly."
- Uses the exec's vocabulary (this VP uses "throughput" rather than "velocity"; leads on cost).

A calibration (not a template to copy verbatim) — your paragraph should carry this *shape*, not these specific numbers:

```
Industry context (Q1 2027). The most recent Microsoft Work Trend Index
<!-- needs-research: pull current edition date and the "uses AI at work"
range --> reports broad knowledge-worker AI usage in a range consistent
with the prior year's reading. The Stack Overflow Developer Survey 2026
<!-- needs-research: AI section citation --> shows developer trust in AI
tools continuing to lag intent-to-use. McKinsey State of AI 2026 reports
enterprise GenAI deployment growing, with cost and governance maturity
the most-cited challenges in the current round. Academic work (Peng et
al.; Dell'Acqua et al.) corroborates the inside-the-frontier
productivity-gain pattern for the specific task classes in our sort.
Consistent with baseline: AI-first routing of PR descriptions, test
skeletons, and ADR first drafts. Diverges from baseline: we do not
mandate this quarter. Reason: review-bar bandwidth and change-fatigue
from the Q4 reorg; we revisit in Q2.
```

**Target length: 120–180 words.** Longer and you are rebuilding too much of Exercise 04 inside this lab.

### Step 6 — Rewrite the "why this and not that" section (15 min)

Under a new heading **Why this and not that, rewritten**, replace the one-sentence stub with two or three alternatives you considered and did not pick. Each alternative in two to four lines:

- Name the alternative in a single sentence.
- State why you did not pick it — specific, falsifiable, in the exec's vocabulary.
- Add a trigger-to-revisit (Chapter 6 shape).

Minimum two alternatives; three is better. Use the Checkout Payments team context (12 engineers, post-Q4-reorg, VP leads on cost) to ground the reasons.

A calibration (one example alternative, in shape):

```
Why we are NOT mandating this quarter.
  Considered: mandate-mode adoption across all four AI-first task
  families, cutting change-management time in half.
  Not chosen: team is three months post-reorg; reviewer bandwidth
  cannot carry a mandate-scale review load without a reviewer-burnout
  signal; cost per IC under mandate exceeds the per-seat budget we
  committed to at Q4 planning.
  Revisit in Q2 if adoption > 70% under opt-out AND reviewer quality
  bar holds for 6 weeks AND cost per IC stays under $X/week.
```

**Target: six to twelve lines total across two or three alternatives.** Terse. Flat voice. Falsifiable triggers.

### Step 7 — Pressure-test the rewritten draft against three exec questions (10 min)

Chapter 6 says the pre-read is written in the voice of the question the exec will ask; Exercise 06's step 7 scripts three standard exec questions. Under heading **Pressure test**, write a 2–4 sentence response to each, drawing *only* on what you have rewritten in Steps 5 and 6:

1. *"Aren't we behind — I keep reading that 75% of workers use AI daily and we are only moving four workflows this quarter?"*
2. *"What's the cost if we are wrong on one of these pilots?"*
3. *"Why not mandate across the whole team? We did that for the SSO rollout."*

For each response, note whether your rewritten sections carry the answer or whether you had to invent new material. Where you had to invent, the rewrite has a gap — fix the rewrite rather than the response.

A worked shape for question 3:

```
Response to Q3: Chapter 6 shape — reference the "Why not mandate"
alternative directly, name the reviewer-bandwidth and cost triggers,
and give the trigger-to-revisit. "We considered mandate — in the
pre-read's alternatives section. We did not pick it because reviewer
bandwidth cannot carry mandate-scale review and because cost per IC
exceeds the per-seat budget. We revisit in Q2 against the three-part
trigger named in the alternatives section."
```

### Step 8 — Write the grading memo (5 min)

At the top of your file, under heading **Grading memo**, write a 6–10 line memo addressed to the fictional author:

- One-sentence verdict (ship / revise / rewrite). This one is a rewrite.
- Three-bullet summary of the most load-bearing gaps (one on marketing voice / hedging; one on the Chapter 4 industry-context failure; one on the missing alternatives in "why this and not that").
- One line pointing to Chapter 6's seven required sections and the writing-failure-modes list as the calibration.
- One line stating what the pre-read has to carry that the current draft does not — in the voice of the specific exec reading it ("@vp-eng asks about cost every quarter and says 'throughput' not 'velocity'").

## Expected output

A single file, roughly two pages, containing:

1. The grading memo at the top (6–10 lines).
2. Section-by-section diagnosis under heading **Diagnosis** (seven sections, each with marketing / hedging / undated-or-un-owned / Chapter 6 bar missed).
3. Industry-context failure mode diagnosis under **Industry context — Chapter 4 check**.
4. "Why this plan" failure mode diagnosis under **Why this plan — Chapter 6 check**.
5. A rewritten **Industry context** paragraph, 120–180 words, meeting the Chapter 4 bar.
6. A rewritten **Why this and not that** section, 6–12 lines across two or three alternatives, each with a trigger-to-revisit.
7. Three 2–4-sentence responses under **Pressure test**, each drawing only on the rewrites.

If your output is much longer than two pages, you are drifting into rewriting the whole pre-read — which is Exercise 06's job, not this lab's. If much shorter, you are probably skipping either the full seven-section diagnosis or the three-question pressure test.

## Checkpoint

Before moving on to Exercise 06 (where you assemble **your own** team's full artifact set and ship it to a named exec), you should be able to answer **yes** to all four:

- Did you flag at least five phrases in marketing voice, five hedges, and every un-dated / un-owned claim in the draft?
- Did your rewritten industry-context paragraph use ranges rather than point estimates, name the sources with dates (or `<!-- needs-research: ... -->` markers), and carry at least one consistent-with-baseline and one diverges-from-baseline line?
- Does your rewritten "why this and not that" section name at least two alternatives, with a falsifiable reason each and a trigger-to-revisit in the Chapter 6 shape ("revisit X if Y for Z duration")?
- Did your pressure-test responses draw *only* on the rewritten sections — and where they did not, did you go back and fix the rewrite rather than the response?

If any answer is no, re-read Chapter 6's "Artifact 4 — The exec pre-read" and "The failure modes to notice in yourself," and Chapter 4's "Four questions to ask of any survey before quoting it" and "What goes into the roadmap, and in which voice," before assembling the real artifact set in Exercise 06.
