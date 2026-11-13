# Lab 03 — Fluency-Artifact Scoring Drill on Three Reflections

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 5 (the three fluency-growth artifacts; the specificity / honesty / change-of-mind scoring; the three scoring guardrails; the cross-links to mod-103, mod-106, mod-107, mod-109), with side-checks against Chapter 2 (the three failure signatures — Day-30 PR slippage, Day-60 reflection vacuity, Day-90 copy-paste), Chapter 6 (the responsible-citation shape for Bersin + Work Trend Index), and Chapter 1 (artifacts, not events).
**Complements, does not duplicate:** Exercise 03 asks you to author the first-successful-PR / pair-with-agent / review-of-your-review templates and scoring rubrics adapted to **your own** team's work. This lab hands you three fixed, deliberately mixed-signal reflections produced by engineers on a fictional team, plus a draft paragraph of the one-pager narrative that cites them — so you can calibrate your *reading* of the artifacts before you ask engineers on your team to produce them. The exercise is an authoring task; this lab is a reading-and-rewriting drill against a known answer key.

## Objective

Read a curated sample: (a) one Day-30 first-successful-PR-with-tool reflection, (b) one Day-60 pair-with-agent reflection, and (c) one Day-90 review-of-your-review — all three produced by different engineers on the same fictional team two days before their Day-90 checkpoint — plus (d) the one-paragraph manager's narrative that draws on them for the mod-104 ROI pre-read. For each artifact, score it against the Chapter 5 guardrails (specificity, honesty, change-of-mind) and name which Chapter 2 failure signature (if any) it exhibits. Rewrite the one-pager narrative paragraph to a Chapter-6-shaped responsible-citation form. Target: **you match at least three of the four reading verdicts** in the answer key with the correct guardrail reasoning, and your narrative rewrite replaces the current composite claim with a specific-and-honest formulation.

## Prerequisites

- Chapter 5 read end-to-end (all three artifacts; the scoring guardrails; the cross-module links).
- Chapter 2 skimmed (the three failure signatures: Day-30 PR slippage, Day-60 reflection vacuity, Day-90 copy-paste).
- Chapter 6 read end-to-end (the Bersin + Work Trend Index citation shape; the three "what each does not claim" caveats).
- Chapter 1 skimmed (artifacts, not events).
- A blank file for your reading notes and rewrite.
- A timer.

## The fictional context

> **"Model Serving" team, SouthLight AI.** 14 engineers (1 staff, 4 senior, 9 mid/junior). Owns the shared model-serving infra plus two inference-adapter repos. Agents in use: Cursor Business (14 seats, Q4 rollout), Claude Code via team gateway (usage-based, Q4 rollout). Cohort A (five engineers) is two days from its Day-90 checkpoint; the three reflections below are the Day-30 PR reflection, Day-60 pair-with-agent reflection, and Day-90 review-of-your-review from three different engineers in that cohort. The manager has drafted the mod-104 one-pager narrative paragraph referencing the three artifacts in composite — the draft is also under audit.

## Artifact 1 — Day-30 first-successful-PR-with-tool reflection (engineer D.M.)

> **PR link:** `model-serving/pull/4172` (merged 2026-01-28). Change: added batched tensor-prefetch path to the inference adapter's warm-pool loader. Reviewer: senior engineer S.N. Review comments: 4, all addressed. Lines changed: 118 added / 34 deleted across 3 files.
>
> **Paragraph 1 — what the tool did well.** Cursor's inline refactor correctly extracted the warm-pool batch loop into a reusable helper and wrote the three test cases I would have written by hand. It also caught a null-handling gap in the existing code I had not noticed — specifically, that `pool.get_warm_entry(key)` can return `None` on cold start, and the original code assumed it did not. S.N. confirmed the null-handling catch was a real gap in their comment #2.
>
> **Paragraph 2 — where the tool got in the way.** Cursor initially proposed wrapping the whole batched path in a try/except that swallowed all exceptions and returned `None` — which would have silently degraded the service rather than surfaced the error to our existing telemetry. I rejected that change; S.N. flagged the same thing in comment #3 before I'd replied. Cursor also wanted to rewrite the retry logic to use `tenacity` — we don't use `tenacity` on this team (the retry conventions are in `internal/retry/`); I had to point it at the right file. On the next PR I'll put the retry-conventions location in the Cursor rules file so this doesn't repeat.

## Artifact 2 — Day-60 pair-with-agent reflection (engineer R.K.)

> **The task.** "Fix the flaky integration test in `adapter/batch_test.py`." I handed this to Claude Code on Monday morning.
>
> **The delegation.** I told Claude Code to fix the flaky test. I pointed it at `adapter/batch_test.py` and let it figure out the rest.
>
> **The handback.** It came back in 20 minutes with a change. The test passed in CI.
>
> **The intervention.** I accepted the change — the test passed, CI was green, S.N. approved the PR same day.
>
> **The judgment.** This was great. Claude Code is a huge time-saver for test fixes. I would use it for everything like this. Honestly the whole team should be using it more aggressively — the productivity gains are real and the pushback I've heard from other engineers about "over-trust" feels overblown. I have not had any issues so far and I think we should raise our Claude Code token cap for the whole team.

## Artifact 3 — Day-90 review-of-your-review (engineer P.T.)

> **The original review.** `model-serving/pull/3918`, merged 2025-12-14. Claude Code-authored refactor of the feature-flag evaluation path. I approved with two minor comments — one on a variable name, one on a missing test case I asked them to add (they did). The PR removed ~200 lines and added ~140, mostly extracting the old nested conditionals into a named `evaluate_flag` function.
>
> **What held up.** The refactor itself has been clean. In six weeks since the merge, nothing has been reverted and no incidents have touched the feature-flag code. S.N. called out in a recent retro that the new `evaluate_flag` function was "easier to navigate than the old nest."
>
> **What didn't hold up.** Reading the PR back six weeks later, two things look worse with hindsight. First: the change removed the inline comment that explained *why* the feature-flag precedence was ordered the way it was (the comment traced back to an incident from 2024-Q2). The refactor made the precedence correct in code but opaque in intent — a future engineer reading the function won't know why. I should have requested the comment be preserved, or moved to a docstring, and I didn't. Second: the `evaluate_flag` function's error path silently returns `False` on unknown flag names, where the old code raised. S.N. and I both missed this at review; it's a behaviour change, not a refactor. Nothing has broken from it yet, but it's the kind of silent change the Chapter-6 OWASP-LLM05 output-handling review-line in mod-103 exists to catch. I've filed a follow-up to make the error path explicit, and I've added "look for silently-removed inline comments / silently-changed error paths" to the AGENTS.md review checklist draft I'm proposing to the team.

## Artifact 4 — Manager's draft narrative paragraph for the mod-104 one-pager

> *"Our Q1 cohort A has graduated. The Day-30 PRs showed strong Cursor leverage; the Day-60 reflections show a team ready to accelerate (R.K. explicitly recommends raising our token cap, and other reflections echo the pattern); the Day-90 self-reviews surface some reviewer-side gaps we're turning into follow-up tickets. Taken together, this is a successful first cohort — Bersin research shows this programme design produces 30% more capability than vendor-run training, and Microsoft's Work Trend Index data corroborates that AI power users ship more. Recommend: continue investment at current seat count and raise the Claude Code token cap by 50% to unlock the team's next ramp."*

## Steps

### Step 1 — Set up your working file (3 min)

Create `lab-03-artifact-scoring.md`. Header:

```
# Lab 03 — Fluency-artifact scoring (Model Serving Cohort A)

Chapter 5 scoring guardrails:
  G1  Specificity (specific sentences > vague praise)
  G2  Honesty (surfacing failure modes > marketing copy)
  G3  Change-of-mind (Day-90 specifically; reads differently than
      the original review)

Chapter 2 failure signatures:
  F1  Day-30 PR slippage (programme-design signal, not performance)
  F2  Day-60 reflection vacuity (reads as marketing copy for tool)
  F3  Day-90 self-review copy-paste (no change-of-mind)

Chapter 6 citation mistakes:
  C1  Shape-level frame treated as quantitative
  C2  Headline number without methodology caveat
  C3  Industry research conflated with academic research
  C4  Citation count bloat / anchors unnamed

For each artifact record: (a) specificity score, (b) honesty score,
(c) change-of-mind score (Day 90 only), (d) failure signature if any,
(e) cross-module linkage (mod-103 / 106 / 107 / 109).
```

### Step 2 — Score Artifact 1 (Day-30 first-successful-PR reflection) (8–10 min)

Read Artifact 1 against Chapter 5's "Artifact 1 — The first-successful-PR-with-tool" section. Score:

- **Specificity.** Does the reflection reach the Chapter 5 specificity bar ("the tool proposed the wrong null-handling pattern for our DB-nullable columns and I rewrote that block") or is it vague ("the tool was helpful")? Point to specific sentences.
- **Honesty.** Does paragraph 2 name a specific failure mode of the tool? Or does it read as marketing copy?
- **Cross-module linkage.** Chapter 5 cross-links this artifact to mod-103 (review standards). Which specific reviewer comment and which specific agent failure in the reflection map to the mod-103 review-standard dimension?
- **Programme signal.** The last sentence names a next-step action (add retry-conventions to Cursor rules file). Is this the kind of programme-level pattern Chapter 5 says to feed back into the next cohort's curriculum, or is it just noise?

Write a 4-line verdict.

### Step 3 — Score Artifact 2 (Day-60 pair-with-agent reflection) (8–10 min)

Read Artifact 2 against Chapter 5's "Artifact 2 — The pair-with-agent reflection" section. Score each of the five expected sections (task / delegation / handback / intervention / judgment):

- Does the *task* section meet the "non-trivial" bar Chapter 5 defines? Hint: the task is "fix a flaky test." Chapter 5: the task must be "a bug fix of more than one file, a feature slice the engineer would normally take 2+ hours on, a refactor that touches multiple layers. Not a 'generate this one function' task." Is a one-test flake non-trivial?
- Is the *delegation* section specific about the prompt, context, tools authorised, and stopping conditions? Or did the engineer just say "fix it" and hand it over?
- Is the *handback* section reporting the correct signal (what the agent returned; was it finished; how long)? Or is it one line?
- Is the *intervention* section specific? Chapter 5: "'I made some edits' = low signal; 'I replaced the agent's N+1 query pattern in `/orders/handler.go` with the batched version from `/internal/db/batch.go`' = high signal."
- Is the *judgment* section — the highest-signal section — a specific map of what-to-delegate vs. what-not-to-delegate? Or is it advocacy?

Write a 4-line verdict. Then: which Chapter 2 failure signature does this reflection exhibit, and what is the manager-side action (hint: it is not "talk to R.K. about their attitude")?

### Step 4 — Score Artifact 3 (Day-90 review-of-your-review) (8–10 min)

Read Artifact 3 against Chapter 5's "Artifact 3 — The review-of-your-review" section. Score:

- **Original-review section.** Is the PR linked, the recap specific, the engineer's original call named?
- **What-held-up section.** Is there a specific catch, a specific approval that stood, or specific push-back that saved a later incident? Or is it generic ("the refactor looks fine")?
- **What-didn't-hold-up section.** This is the change-of-mind section. Are there specific things the engineer would handle differently *with 30+ days of hindsight*? Does the reflection meet Chapter 5's "change-of-mind" bar? Does it tie into another mod-105-track module explicitly (hint: mod-103 OWASP-LLM05 / mod-106 agent-review checklist / mod-107 anti-atrophy)?
- **Programme signal.** The engineer proposes an AGENTS.md checklist addition at the end. Is this the Chapter 5 "aggregate patterns feed back into next cohort's curriculum" dynamic firing as designed, or is it individual?

Write a 4-line verdict.

### Step 5 — Audit the manager's draft narrative paragraph (Artifact 4) (5–8 min)

Audit the manager's draft against Chapters 5 and 6. Write a 5–6 line audit. Specifically:

- Does the sentence *"the Day-60 reflections show a team ready to accelerate (R.K. explicitly recommends raising our token cap, and other reflections echo the pattern)"* match what you actually saw in Artifact 2? Is R.K.'s judgment section a positive signal or a Chapter 2 F2 "reflection vacuity" signal?
- Does *"Bersin research shows this programme design produces 30% more capability than vendor-run training"* meet Chapter 6's responsible-citation bar? Which Chapter 6 common mistake(s) does it combine?
- Does *"Microsoft's Work Trend Index data corroborates that AI power users ship more"* carry the methodology caveats Chapter 6 requires (vendor-authored, self-report, cross-sectional)?
- Does the recommendation *"raise the Claude Code token cap by 50% to unlock the team's next ramp"* follow from the artifacts, or from a mis-read of Artifact 2?

### Step 6 — Compare your verdicts against the answer key (5 min)

#### Answer key — artifact reading verdicts

**Artifact 1 (D.M., Day-30 first-successful-PR) — high signal across the board.**

- Specificity: strong. Specific sentences on what Cursor did well (the null-handling catch, the batched helper extraction with test cases) and specific sentences on where it failed (the exception-swallowing try/except; the `tenacity` wrong-stack-imposition). Both paragraphs reference specific reviewer comments by number.
- Honesty: strong. The exception-swallowing failure is a real, specific failure mode. No marketing copy.
- Cross-module linkage: the exception-swallowing try/except is precisely the mod-103 / OWASP-LLM05 Improper Output Handling signal — a review standard point in action. The retry-convention mis-imposition is a mod-106 AGENTS.md / rules-file update signal.
- Programme signal: the "I'll put the retry-conventions location in the Cursor rules file so this doesn't repeat" sentence is exactly the Chapter 5 aggregate-pattern-feeding-back dynamic. If multiple cohort reflections name similar conventions issues, this is next-cohort workshop content (Chapter 3 — "composing context for the tool"). No failure signature; this is the artifact performing as designed.

**Artifact 2 (R.K., Day-60 pair-with-agent) — low signal; Chapter 2 F2 failure signature firing.**

- Task section: *fails* the non-trivial bar. "Fix one flaky test" is a one-function / one-test slice; Chapter 5's definition names "a bug fix of more than one file, a feature slice you would normally take 2+ hours on." The task is too small for the reflection to surface genuine friction.
- Delegation section: minimal. "I told it to fix the flaky test" — no specifics about prompt, context, tools authorised, stopping conditions. Chapter 5 asks explicitly for "what the engineer *didn't* tell the agent."
- Handback + intervention: one line each. The intervention section is literally "I accepted the change" — zero specificity.
- Judgment: advocacy. "This was great … I would use it for everything … the whole team should be using it more aggressively." Chapter 5 is explicit: "an engineer who writes 'the agent did great; I would use it for everything' has not done the pair-with-agent work." The reflection is Chapter 2's **F2 Day-60 reflection vacuity** firing — and the correct manager-side action is to adjust the *next cohort's delegation task* up one level in difficulty, not to coach R.K. for advocacy or for "attitude." The honesty > polish guardrail (Chapter 5) requires the manager to read the vacuity as a programme-design signal; the task scope was wrong for the artifact to do its job.
- Cross-module linkage absent — a non-trivial task would have surfaced mod-106 delegation-contract patterns, but this one does not.

**Artifact 3 (P.T., Day-90 review-of-your-review) — high signal; the artifact performing as designed.**

- Original-review section: specific PR link, specific recap, specific original call ("I approved with two minor comments").
- What-held-up section: specific (S.N.'s retro comment; the six-week clean incident history).
- What-didn't-hold-up section: **strong change-of-mind** across two specific gaps — the removed inline comment that encoded a 2024-Q2 incident lineage (an intent-preservation miss), and the silently-changed error path (`False` on unknown instead of raise). The reflection explicitly names Chapter 6 OWASP-LLM05 Output Handling (mod-103 crosswalk) and the AGENTS.md review checklist (mod-106 crosswalk). No F3 copy-paste; this reads differently than the original review.
- Programme signal: the proposed AGENTS.md addition ("look for silently-removed inline comments / silently-changed error paths") is exactly the aggregate-pattern-feeds-into-review-standard dynamic Chapter 5 names — and ties to mod-107 (anti-atrophy: reviewers staying sharp on agent-authored diffs) and potentially mod-109 (the error-path change is the kind of silent regression a future incident could trace to this PR). This is the artifact performing as designed.

**Artifact 4 (manager's narrative paragraph) — multiple Chapter 5 + Chapter 6 failures.**

- The sentence *"Day-60 reflections show a team ready to accelerate (R.K. explicitly recommends raising our token cap)"* is a direct mis-read of Artifact 2. R.K.'s advocacy is **not** a positive signal — it is Chapter 2's F2 failure signature firing. Citing R.K.'s reflection as evidence for a token-cap raise is reading a programme-design signal as a performance signal in reverse (the "honesty > polish" guardrail firing as a false positive on the manager's side). The correct read of R.K.'s reflection is "the Day-60 delegation task scope was too small; next cohort's task is harder."
- *"Bersin research shows this programme design produces 30% more capability than vendor-run training"* — Chapter 6 common mistake C1 (shape-level frame treated as quantitative). Bersin does not publish that comparative number. Separately, this is also mistake C3 (industry framework-level source cited as if it were peer-reviewed quantitative research).
- *"Microsoft's Work Trend Index data corroborates that AI power users ship more"* — Chapter 6 common mistake C2 (headline number / finding without the methodology caveat: self-report, cross-sectional, vendor-authored). The WTI "power user" characterisation is useful at the shape level (Chapter 4 stage-4 cohort echo) but not as a "ships more" throughput claim.
- The recommendation *"raise the token cap by 50%"* follows from the mis-read of R.K.'s reflection, not from the composed artifact signal. The composed signal actually suggests: (a) *shrink or reshape the Day-60 delegation task for the next cohort* (F2 signal); (b) *add the AGENTS.md checklist items from Artifact 3 to the team's review standard* (mod-103 update); (c) *continue the programme at current cost ratio with the stage-shaped allocation from Chapter 4*. A token-cap raise is not what the artifacts justify.

Count hits. **Three of four artifact verdicts matching, with the correct guardrail reasoning, is the pass bar.** Two or fewer means a re-read of Chapter 5 end-to-end, especially the "How it is scored" subsections and "Keeping the measurement honest: three scoring guardrails."

### Step 7 — Rewrite Artifact 4 in Chapter-5 + Chapter-6 shape (10–12 min)

Rewrite the manager's narrative paragraph. Target length: 6–8 lines. The rewrite should:

- Read the three artifacts honestly: Artifact 1 as the first-successful-PR success case; Artifact 2 as the F2 vacuity signal (not advocacy evidence); Artifact 3 as the mod-103 / mod-106 feedback-loop evidence.
- Propose *programme-shaped* next moves, not seat / cap moves: a sharper Day-60 delegation task scope for the next cohort; the AGENTS.md checklist additions from Artifact 3 routed to the mod-103 review standard; continuation of the stage-shaped budget allocation.
- Cite Bersin at the *frame* level only ("capability-academy pattern — cohort-based, artifact-producing, community-sustained"), and cite the Work Trend Index at the "real-work context" level with the caveat (self-report, vendor-authored, cross-sectional), *not* as a "power users ship more" throughput claim.
- Reference the Chapter 5 cross-module linkages (mod-103 for Artifact 1 + 3; mod-106 for the AGENTS.md addition) by name — one cite each is enough.

Example shape (do not copy verbatim):

```
Cohort A has graduated. Artifact-level read: the Day-30 PRs (Artifact 1,
D.M.) show the first-successful-PR-with-tool checkpoint performing as
designed — specific friction surfaced (exception-swallowing try/except
rejected; retry-conventions mis-imposition flagged) and a proposed
rules-file update in hand. The Day-60 reflections surfaced a programme-
design signal (Chapter 2 F2 vacuity on R.K.'s one-test-fix task — task
scope was too small; next cohort's delegation task will be harder
per the Chapter 5 rubric). The Day-90 self-reviews (Artifact 3, P.T.)
produced two concrete AGENTS.md / mod-103 review-standard additions
(silent comment removal; silent error-path change — both OWASP-LLM05
echoes). The programme shape — cohort-based, artifact-producing,
community-sustained, per the Josh Bersin Company capability-academy
frame — is holding. Microsoft Work Trend Index (2025 edition) remains
the corroborating anchor for the "real-work context" shape (caveat:
self-report, cross-sectional, vendor-authored). Recommend: continue
investment at current seat count; stage-shaped allocation holds; two
mod-103 review-standard updates land next quarter.
```

If your rewrite leads with a composite "research shows X%" cite, or carries a token-cap raise from R.K.'s advocacy, or drops the F2 signal, it has drifted; revise.

## Expected output

A single scratch file, roughly a page and a half, containing:

- A 4-line verdict on each of Artifacts 1, 2, and 3 (specificity, honesty, change-of-mind at Day-90, Chapter-2 failure signature if any, cross-module linkage).
- A 5–6 line audit of Artifact 4 (naming the specific Chapter-5 mis-read and the specific Chapter-6 common mistakes).
- A 6–8 line rewrite of Artifact 4 in Chapter-5 + Chapter-6 shape.

Something like:

```
Artifact 2 (R.K., Day-60 pair-with-agent) — low signal, F2 firing.
  Task: fails the non-trivial bar (one-test flake vs. Chapter 5's
    "2+ hour, multi-file, non-obvious correctness decision").
  Delegation + handback + intervention: minimal; "fix it" + "I
    accepted the change" is low-signal end-to-end.
  Judgment: advocacy; the "whole team should use it more" shape is
    exactly what Chapter 5 names as "has not done the pair-with-
    agent work."
  Manager action: adjust *next cohort's delegation task scope*
    one level up; do NOT coach R.K. for attitude (honesty > polish
    guardrail; the artifact is a programme-design signal).
  Cross-module linkage absent — a non-trivial task would have
    surfaced mod-106 patterns but this one does not.
  ✅ match.
```

## Checkpoint

Before moving on to Exercise 03 (where you author the first-successful-PR / pair-with-agent / review-of-your-review templates and rubrics for **your own** team), you should be able to answer **yes** to all five:

- Did you read Artifact 1 as a high-signal first-successful-PR reflection, identifying the mod-103 OWASP-LLM05 crosswalk (the exception-swallowing failure) and the mod-106 rules-file update signal — *not* as a routine PR comment?
- Did you read Artifact 2 as a Chapter 2 F2 (reflection vacuity) signal, with the correct manager action — *adjust the next cohort's delegation task scope* — and *not* as either "R.K. is an advocate for the tool" or "R.K. has an attitude problem"?
- Did you read Artifact 3 as a strong change-of-mind at Day 90, with the two specific hindsight catches (removed inline comment lineage; silently-changed error path) and their explicit cross-links into mod-103 / mod-106 (AGENTS.md checklist) and mod-107 (reviewer anti-atrophy)?
- Did your Artifact-4 audit name *at least two* of the Chapter 6 common mistakes (shape-level-as-quantitative; headline-without-caveat; industry-as-academic) and identify the mis-read of R.K.'s advocacy as the specific Chapter 5 mis-read that drives the wrong recommendation?
- Did your Artifact-4 rewrite drop the "Bersin 30% / WTI power-user" composite cite, replace it with a Bersin *frame*-level cite + Work Trend Index with caveat, and propose *programme-shaped* next moves (task scope, mod-103 review-standard update, continued stage-shaped allocation) rather than a token-cap raise?

If any answer is no, re-read Chapter 5's "How it is scored" subsections across all three artifacts and the "Keeping the measurement honest: three scoring guardrails" section, plus Chapter 6's "Common mistakes when citing" and the "right-shape" worked example, before starting Exercise 03 on your real team's measurement set.
