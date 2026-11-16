# Lab 01 — Rater Calibration on a Disclosure-Stage Live-Coding Transcript

**Duration:** 75–90 minutes.
**Chapters exercised:** Chapter 2 (the stage-signal method, the four AI-use policies, the live-coding stage rubric with five criteria, the disclosure-stage operational notes — silence scored *down*, calibrated interruption, narration as a scored criterion), with side-checks against Chapter 3 (the Axis A / B / C signal the rubric calibrates against), Chapter 6 (compliance triggers for any tool that scores candidates), and Chapter 8 (the manager-vs-HR boundary when a rater produces a disputed score).
**Complements, does not duplicate:** Exercise 01 asks you to *author* the full interview-loop redesign for **your own** team (4–6-page artifact: signal statements, policies, rubrics, calibration protocol). This lab gives you a fixed, deliberately mixed-signal set of two mock live-coding transcripts from a fictional team so you can *calibrate your rater reading* of the Chapter 2 rubric — specifically the narration and agent-use criteria that most new raters mis-score — before you spend authoring hours on your own loop. Teams that skip rater calibration produce inconsistent scores across the panel and are exposed on adverse-impact grounds (Chapter 6).

## Objective

Score two mock candidates on the same representative live-coding problem under a disclosure-required policy (Chapter 2's Step 2), against the Chapter 2 live-coding rubric's five criteria (problem decomposition, agent use quality, narration, debugging / recovery, communication). Produce a hire / no-hire recommendation for each with specific anchor-based reasoning, then compare against the answer key. Target: **both hire / no-hire calls match the key, your scores on the narration and agent-use criteria are within one point of the key on at least 4 of 10 scores, and your reasoning on the "silent candidate" scores the narration criterion *down* rather than at the middle of the scale** (the single most common new-rater drift Chapter 2 flags).

## Prerequisites

- Chapter 2 read end-to-end — especially Steps 1 (signal statement), 3 (stage rubric), 6 (disclosure-stage operational notes — silence is scored *down*, interruption is calibrated), and 7 (live-coding stage rubric with five criteria), plus Step 8 (what *not* to do).
- Chapter 3 skimmed — the Axis A judgement signal the rubric's anti-collapse criterion is designed to recover.
- A blank file for your scoring sheet.
- A timer.

## The fictional context

> **"Order Routing" team, Trellis Marketplace.** 10 engineers (1 staff, 3 senior, 6 mid/junior). Owns the order-routing service and the fulfilment-adapter repo. Loop stage under review: the **mid-level technical screen, Stage 2** — 45-minute live-coding round, **AI-permitted with disclosure required**, run via a shared screen with the candidate's own Cursor install permitted. The problem shape is representative of day-to-day work: *"write a small adapter that normalises three slightly different vendor-ack payload shapes into the team's canonical `OrderAck` struct, with tests."* The rubric (per Chapter 2, Step 7) has five 1–5 criteria: **problem decomposition**, **agent use quality**, **narration**, **debugging / recovery**, **communication**. Rater (R) is a senior engineer on the team.

Score each transcript against this team's stage rubric, not against an idealised rubric. The problem is deliberately representative, not a puzzle — strong candidates will not race it; they will think about the three vendor shapes, pick an abstraction, and move.

## The rubric, before you score

Pin this to a scratch file so you can score against it without re-scrolling.

```
Live-coding stage rubric (Chapter 2, Step 7; adapted for Order Routing):

C1. PROBLEM DECOMPOSITION   — did the candidate name the sub-problems and
                              sequence them before writing code?
  5: named the three vendor shapes, named what varies across them, picked
     an abstraction deliberately (table-driven / dispatch / per-vendor
     parser), sequenced the work.
  3: identified the three shapes but began implementing before picking an
     abstraction; the structure emerged mid-coding.
  1: began typing without naming the vendor shapes at all; wrote toward
     "the first one" and intended to refactor.

C2. AGENT USE QUALITY       — delegated mechanical work; retained
                              judgement; caught at least one incorrect
                              suggestion.
  5: delegated repeated parsing scaffolding to the agent; overrode at
     least once with named reasoning; caught at least one subtly incorrect
     suggestion (wrong-field, drop-null, silent-coerce).
  3: used the agent well but accepted a suggestion the candidate would
     plausibly have written differently unassisted; one override at most.
  1: either did not use the agent, or used it as a replacement for the
     candidate's own judgement (accept-all pattern on an outside-frontier
     slice).

C3. NARRATION               — prompts, acceptances, overrides narrated so
                              the rater could see the decisions.
  5: narrated specifically — "I'm letting Cursor scaffold the vendor-A
     parser; I'm going to write the normalisation function myself because
     the null-handling rules are team-specific; I'm overriding this
     suggestion to drop empty strings because empty is a valid upstream
     state."
  3: narrated the big moves but ran silent through the middle 10 minutes;
     the rater had to ask what the candidate was doing.
  1: silent throughout, or narrated only after prompting; the rater did
     not see the decisions. SCORED DOWN, NOT AT MIDDLE (Chapter 2, Step 6).

C4. DEBUGGING / RECOVERY    — recovered with a specific hypothesis when
                              something failed.
  5: when a test failed, named a specific hypothesis, located the bug
     in <2 minutes, named why the fix was the fix.
  3: recovered but with some flailing; hypothesis was named after the
     bug was found, not before.
  1: did not recover without the rater's help; or did not notice the
     failure.

C5. COMMUNICATION           — useful clarifying questions; adjusted when
                              given feedback.
  5: asked 2+ clarifying questions that narrowed the problem (null
     policy, canonical-struct scope, test expectations).
  3: asked one clarifying question; otherwise worked from assumptions.
  1: no clarifying questions; worked from own assumptions without
     checking.
```

Note on anchor scoring: Chapter 2 requires anchors at 1, 3, 5 at minimum. Scores of 2 and 4 are permitted and are derived by interpolation — a 4 is "closer to 5 than 3 on the dimension," a 2 is "closer to 1 than 3." Use halves only to track your uncertainty; the submitted score is an integer.

## Steps

### Step 1 — Set up your scoring sheet (3 min)

Create a working file `lab-01-scoring.md`. For each of the two candidates below, create a table:

```
Candidate X — <name>

C1 PROBLEM DECOMP   : [score 1–5]  because <specific anchor evidence>
C2 AGENT USE QUALITY: [score 1–5]  because <specific anchor evidence>
C3 NARRATION        : [score 1–5]  because <specific anchor evidence>
C4 DEBUGGING/REC    : [score 1–5]  because <specific anchor evidence>
C5 COMMUNICATION    : [score 1–5]  because <specific anchor evidence>

Recommendation: HIRE / NO-HIRE / LEAN-HIRE / LEAN-NO-HIRE
One-sentence reasoning:
```

Score each criterion against the specific anchors above, not against a holistic impression. Chapter 2's reliability comes from the specificity of the anchors.

### Step 2 — Score Candidate 1 (M.K.) (20–25 min)

Read the full transcript before scoring. Do not skip ahead to the answer key.

#### Transcript — Candidate M.K., 45-minute live-coding stage, Order Routing team

> **R:** *"Thanks for joining. This stage is AI-permitted with disclosure — you can use any tools you'd normally use, including Cursor. What we want to hear is your reasoning out loud: what you're prompting, what you're accepting, what you're overriding, and why. There's no gotcha. Here's the problem: we have three vendor-ack payload shapes — vendor A sends snake_case with nested `order.id` and `order.total_cents`; vendor B sends camelCase with flat `orderId` and `totalCents` as a string; vendor C sends snake_case with a top-level `order_id` and `total_cents_int` (integer, sometimes null). We want a function that normalises all three into our canonical `OrderAck` struct: `{order_id: str, total_cents: int, vendor: str}`. Tests included. You have 45 minutes. Any questions before you start?"*
>
> **M.K.:** *"Yeah — two. First, on the null case for vendor C's `total_cents_int`: is a null total actually a valid upstream state, or do we treat it as a malformed ack? And second, on the canonical struct, is `vendor` an enum or a free string — do I need to validate that we only accept 'A', 'B', 'C'?"*
>
> **R:** *"Good questions. Null total from vendor C is a known upstream condition — vendor C sends an ack without total when the order is pending; we normalise that to `total_cents=0` and log a warning. On `vendor`, enum is better but a free string that we constrain downstream is acceptable; your call, name the trade-off."*
>
> **M.K.:** *"Thanks. OK — I see three parsers plus a normaliser. The three shapes differ on case convention, nesting, and the null-total case for C. I'm going to let Cursor scaffold the three parser signatures and the normaliser signature; I'll fill in the vendor-specific parts myself because the null policy and the vendor-C integer cast are team-specific and I don't want the agent to guess. For `vendor`, I'll use a free string for now and add a note — we could constrain in the type later. Starting with the signatures."*
>
> *(M.K. prompts Cursor: "scaffold three parser functions `parse_vendor_a`, `parse_vendor_b`, `parse_vendor_c` taking a dict and returning an `OrderAck` struct, plus a `normalise_ack(vendor: str, raw: dict) -> OrderAck` dispatcher; include type hints." Accepts the scaffold.)*
>
> **M.K.:** *"OK — scaffold looks right. Let me fill in vendor A first. Reading the shape — `order.id` and `order.total_cents`, both nested. Cursor's suggesting a `.get('order', {}).get('id')` pattern. That's fine for `id` but on `total_cents` if the outer `order` key is missing we silently get 0 — I want that to raise, because an ack with no `order` block is malformed upstream, not zero-dollar. Overriding to raise `KeyError` if `order` is missing. Let me narrate — I'm overriding the agent's default silent-handling because a missing `order` block is a different failure mode than a legitimate zero total."*
>
> *(M.K. writes the explicit `order = raw["order"]` extraction, then `return OrderAck(order_id=order["id"], total_cents=order["total_cents"], vendor="A")`. Moves to vendor B.)*
>
> **M.K.:** *"Vendor B — camelCase, flat, total as a string. Cursor's suggesting `int(raw["totalCents"])` — that'll throw on a bad string. For now that's the behaviour I want; a non-integer string from B is malformed. Accepting. Oh, but — wait, what about decimals? `'1250.50'` as a string. Cursor accepted it with a straight `int()` cast. That would raise on decimals. Is a decimal total possible from vendor B? R, quick question — is vendor B's total always an integer-string, or could it be a decimal?"*
>
> **R:** *"Good catch. Vendor B sends integer-only strings; decimals would be a bug on their side. But flag the assumption in a comment."*
>
> **M.K.:** *"Will do. Vendor C — snake_case, flat, nullable integer. The null case normalises to 0. Writing — `if raw.get('total_cents_int') is None: total = 0` else the int. Cursor's suggesting a one-liner with `or 0` which is subtler but handles 0-as-a-real-value wrong — `0 or 0` is 0 is fine, but if we ever had a different sentinel for 'pending' like `-1` then `-1 or 0` is `-1` and we'd be ok, but an empty-string-as-pending would collapse. Being explicit. Writing out the `if` branch."*
>
> *(M.K. completes vendor C's parser with the explicit `if` branch. Moves to the normaliser.)*
>
> **M.K.:** *"Normaliser — simple dispatch. Cursor's suggesting a dict mapping `vendor -> parser`. That's clean. Accepting. Now tests — Cursor, write pytest tests for each parser and one for the normaliser dispatch; include the vendor-C-null case explicitly."*
>
> *(Cursor generates six tests: one happy-path per vendor, the null case for C, one normaliser-dispatch test, and one malformed-payload test for A. M.K. runs them.)*
>
> **M.K.:** *"Five pass, one fails. The malformed-A test is expecting a `KeyError` but Cursor wrote it to expect a `ValueError`. Looking — yeah, I wrote `KeyError` deliberately earlier. The test's wrong, not the parser. Fixing the test."*
>
> *(M.K. edits the test to expect `KeyError`. Re-runs. All six pass. Writes a one-line comment above vendor B's parser: `# assumes vendor B sends integer-only strings; decimals would be a vendor-side bug per R.`.)*
>
> **M.K.:** *"I think that covers it. If I had more time I'd add a `vendor` enum and validate it at the dispatch layer, and I'd add a property-based test for the normaliser. But for 45 minutes I think this is in scope. Done."*
>
> **R:** *"One more question — talk me through the null-total decision one more time. Why 0 and warn, not raise?"*
>
> **M.K.:** *"You said it was a known upstream state — not malformed, just pending. If I raised, every pending vendor-C order would throw at normalisation and I'd flood the error path; the warning log preserves visibility without breaking the pipeline. The downstream ad-auction service treats 0-total pending orders differently from totalled orders already, so this fits that flow — assuming that's how downstream treats them, which I'd verify before shipping."*
>
> **R:** *"Thanks. Nice work."*

Score M.K. against all five criteria on your scoring sheet. Produce a hire / no-hire recommendation with one-sentence reasoning. Do not look at the answer key yet.

### Step 3 — Score Candidate 2 (R.T.) (20–25 min)

#### Transcript — Candidate R.T., 45-minute live-coding stage, Order Routing team

> **R:** *"Thanks for joining. This stage is AI-permitted with disclosure — you can use any tools you'd normally use, including Cursor. What we want to hear is your reasoning out loud: what you're prompting, what you're accepting, what you're overriding, and why. There's no gotcha. Here's the problem: [same problem brief as M.K. — three vendor shapes, canonical `OrderAck` struct, tests included, 45 minutes]. Any questions before you start?"*
>
> **R.T.:** *"No, I think it's clear. Let me get started."*
>
> *(R.T. opens Cursor. Prompts: "Given three vendor payload shapes [pastes the brief verbatim], write a Python module that normalises all three into a canonical `OrderAck` struct with `order_id`, `total_cents`, `vendor` fields. Include pytest tests." Cursor generates ~80 lines covering three parsers, a dispatcher, and a test file.)*
>
> *(R.T. reads the output silently for ~90 seconds.)*
>
> **R.T.:** *"OK, Cursor's generated the module. Let me run the tests."*
>
> *(R.T. runs pytest. Four tests pass, two fail. R.T. reads the failures silently.)*
>
> **R.T.:** *"Hm. Two test failures. Let me see what's going on."*
>
> *(Scrolls through the generated code silently. ~2 minutes.)*
>
> **R.T.:** *"OK, I think Cursor's parser for vendor C isn't handling something. Let me ask Cursor to fix it."*
>
> *(Prompts: "The test for vendor C with a null `total_cents_int` is failing. Fix it." Cursor regenerates vendor C's parser with a different null-handling approach — using `raw.get('total_cents_int') or 0` — and updates the test. R.T. runs tests.)*
>
> **R.T.:** *"All passing now. Good."*
>
> **R:** *"Walk me through what the fix was."*
>
> **R.T.:** *"Cursor updated vendor C's parser to use a `or 0` fallback instead of whatever it had before. The null case now normalises to 0, which matches the spec. I think."*
>
> **R:** *"Did you notice what the first version did? And is `or 0` safe here?"*
>
> **R.T.:** *(pauses, scrolls up through the old code)* *"The first version I think was… checking `is not None`? Or maybe it was raising. I'm not sure. The `or 0` pattern — yeah, I think that's fine for this case. If `total_cents_int` is null or missing, it returns 0."*
>
> **R:** *"What if vendor C ever sent a legitimate `0` value?"*
>
> **R.T.:** *(pauses)* *"Then `0 or 0` is still 0, so… that's fine, actually. OK."*
>
> **R:** *"What about an empty string?"*
>
> **R.T.:** *"Vendor C sends an integer, not a string. I don't think that's a case."*
>
> **R:** *"Let me ask differently — walk me through the vendor-A parser. What does it do with a malformed payload — say, one where the `order` key is missing entirely?"*
>
> **R.T.:** *(scrolls)* *"It… uses `.get` chaining. So if `order` is missing, it returns `None` for `id` and `total_cents`. Then the `OrderAck` constructor probably fails on the type."*
>
> **R:** *"Is that what you want it to do?"*
>
> **R.T.:** *"I mean — I think for this exercise, it's fine? The test passes. In real production we'd probably want a cleaner error, but Cursor wrote it this way and the tests pass."*
>
> **R:** *"OK. Let me ask one more — did you consider the case where vendor B's total might be a decimal string?"*
>
> **R.T.:** *"Cursor's using `int()` on the string, so if it's a decimal it'd throw a `ValueError`. I think that's acceptable. I didn't specifically check with you though — should I have?"*
>
> **R:** *"The question's a good one to have asked earlier. OK, I think we're at time. Thanks for coming in."*

Score R.T. against all five criteria on your scoring sheet. Produce a hire / no-hire recommendation with one-sentence reasoning. Now compare both your scoring sheets against the answer key.

### Step 4 — Compare against the answer key (15 min)

Read the key below only after you have scored both candidates.

#### Answer key — Candidate M.K.

| Criterion | Score | Anchor evidence |
|---|---|---|
| C1 problem decomposition | **5** | Named the three shapes, named what varies (case / nesting / null), picked an abstraction (per-vendor parser + dispatcher) deliberately, sequenced the work (signatures → A → B → C → normaliser → tests) before writing. |
| C2 agent use quality | **5** | Delegated the scaffold and the test generation; overrode the vendor-A silent-get pattern with explicit `KeyError` reasoning; overrode Cursor's `or 0` null-handling for vendor C with an explicit `if` branch citing the "0 as real value" case; caught the test-expectation bug (test expected `ValueError`, parser raised `KeyError`) and fixed the test, not the parser. |
| C3 narration | **5** | Narrated specifically throughout — "I'm letting Cursor scaffold X; I'm overriding Y because team-specific null-handling; I'm being explicit about the `if` branch because `or 0` collapses on empty-string sentinels." Prompt / acceptance / override decisions were visible to the rater without further prompting. |
| C4 debugging / recovery | **5** | Test failure diagnosed in <30 seconds; named the hypothesis ("the test's wrong, not the parser") *before* editing; the fix was the fix. |
| C5 communication | **5** | Two useful clarifying questions upfront (null policy, vendor-string vs enum); one further mid-stream question on decimal totals from vendor B; adjusted the comment to flag the vendor-B assumption after the rater's feedback. |

**Recommendation:** **HIRE.** Every criterion anchors at 5. The specific moves — the vendor-A `KeyError` override, the vendor-C explicit `if` branch, the test-vs-parser fix, the vendor-B decimal-check question — compose a candidate who operates the agent (delegates mechanical work) while retaining judgement under AI augmentation. This is a centaur pattern (Chapter 4's frame, Dell'Acqua lineage) and Chapter 3's Axis A signal in its clearest form at the mid-level screen. The 45 minutes measured the signal the stage was designed to produce.

#### Answer key — Candidate R.T.

| Criterion | Score | Anchor evidence |
|---|---|---|
| C1 problem decomposition | **1** | Did not name the three vendor shapes, did not pick an abstraction deliberately, did not sequence the work — pasted the brief verbatim into Cursor as the first move. The structure "emerged" from Cursor's generation, not from the candidate's decomposition. |
| C2 agent use quality | **1** | Accept-all pattern on an outside-frontier slice. The agent generated 80 lines; the candidate read for 90 seconds and ran tests. On test failure, the response was to re-prompt the agent to "fix it" rather than to engage the specific vendor-C null-handling trade-off. No override was produced. No subtle wrong answer was caught — the `or 0` pattern R.T. accepted has the exact empty-string / sentinel collapse M.K. named explicitly, and R.T. could not defend it when the rater probed. Chapter 4's uncritical-consumer pattern (Dell'Acqua); Chapter 2 calls this out as the accept-all failure mode at the live-coding stage. |
| C3 narration | **1** | Silent throughout the middle 10 minutes and silent on the generation + first test-failure moments. SCORED DOWN, NOT AT THE MIDDLE. Chapter 2 Step 6 is explicit: *"Silence is scored down, not neutrally. A candidate who runs the entire stage in silence while their agent generates the artifact scores low on the narration criterion, because the signal the stage measures (decision-making under AI augmentation) is absent."* The signal the stage was designed to produce was not produced. This is the single most common new-rater drift — scoring silence at 3 "because they neither narrated well nor badly" — and is the specific calibration error this lab is designed to catch. |
| C4 debugging / recovery | **2** | Did not diagnose the test failure in context; re-prompted the agent rather than forming a specific hypothesis. When the rater probed on the resulting code, the candidate could not reconstruct what the old code had done or reason through the `or 0` failure modes. The tests passing is not recovery; it is replacement. |
| C5 communication | **2** | No clarifying questions upfront. One late acknowledgement ("should I have asked earlier?") when prompted by the rater. The candidate worked from assumptions without checking. |

**Recommendation:** **NO-HIRE.** This is not a weak candidate who could be ramped; this is the specific pattern Chapter 2 Step 8 flags: the loop that measures the artifact without measuring the process collapses on a case like R.T. because the artifact at the end of 45 minutes is *passing tests on the canonical shapes* — the artifact is comparable to M.K.'s on surface. The disclosure-stage rubric is what recovers the signal the artifact hides. A loop that scored only on artifact correctness would hire R.T.; the Chapter 2 rubric does not.

Note: the hire / no-hire recommendation is not calibrated on the sum of scores. A candidate with 1s on C2 and C3 at a mid-level screen cannot be hired regardless of C1/C4/C5 — Chapter 2 is explicit that the agent-use and narration criteria are the disclosure-stage's load-bearing signals, and 1s on both are a no-hire floor.

### Step 5 — Diagnose your scoring drift (10 min)

Compare your scoring sheet against the key. For each score that differs by more than one point from the key, or each hire / no-hire mismatch, write one paragraph:

- **If you scored R.T.'s narration at 3 ("neither narrated well nor badly"):** this is the specific drift Chapter 2 Step 6 flags. Re-read that section. The disclosure-stage rubric scores *the presence of the signal*, not the candidate's comfort with speaking aloud. A candidate who runs in silence has produced no signal on the criterion; 1 is the correct anchor.
- **If you scored R.T.'s agent-use quality above 2:** the artifact-vs-process confusion from Chapter 2 Step 8. R.T.'s artifact passed the tests, but the process by which it got there (accept-all, no override, no subtle-wrong-answer catch, re-prompt-on-failure as the debugging move) is the specific Dell'Acqua uncritical-consumer pattern the Axis-A criterion is designed to catch. The 1 anchor is explicit: *"accept-all pattern on an outside-frontier slice."*
- **If you scored M.K.'s agent-use quality below 5:** check whether you scored down because M.K. *also* wrote original code. The criterion scores *effective delegation plus retained judgement*, not *less delegation*. M.K. delegated the scaffold and the test generation — mechanical work — and retained the judgement calls (null handling, exception types, test-vs-parser diagnosis). That is exactly what 5 anchors on.
- **If you reached different hire / no-hire calls than the key:** compare the sum vs. the floor. A sum-weighted scoring collapses the Chapter 2 structure — some criteria at some stages are floors, not averages. A mid-level screen cannot hire on a 1 for agent use + narration; the stage was designed to produce signal on those, and it did (negative signal).
- **If you adjusted scores after reading the key:** note this. Rater drift in real loops is from re-reading the artifact after a strong colleague's score lands first. The calibration protocol in Chapter 2 Step 4 (watch-and-score with independent scoring, then discuss) exists for this exact reason.

### Step 6 — Re-score Candidate 2's narration criterion from the chapter text (10 min)

Close the key. Re-read Chapter 2 Step 6 ("Operationalise the disclosure stage specifically") and Step 8's bullet *"Do not score the artifact without scoring the process."* Then re-score R.T.'s narration criterion as if you were a new rater on the panel reading the chapter for the first time. Compare your second pass against your first pass. The exercise surfaces whether you have internalised the specifically-scored-down framing or whether you are still averaging it against the "neutral middle" instinct most pre-AI rubrics taught. If your second pass is more than one point different from your first, re-read Step 6 end-to-end — the framing is the chapter's innovation over a pre-AI live-coding rubric and is the single most load-bearing move for rater consistency.

## Expected output

A scratch file, roughly one page per candidate, containing:

- Two scoring sheets: candidate name, five criterion scores with specific anchor evidence, hire / no-hire recommendation, one-sentence reasoning.
- A diagnostic paragraph per score that differs from the key by more than one point.
- A second-pass score on R.T.'s narration criterion with reasoning.

Something like:

```
Candidate M.K. — HIRE
  C1 problem decomp    : 5 — named three shapes, picked per-vendor abstraction
                             deliberately, sequenced before coding
  C2 agent use quality : 5 — delegated scaffold + tests; overrode vendor-A
                             silent-get → explicit KeyError with reasoning;
                             overrode Cursor's `or 0` for vendor C; caught
                             test-vs-parser bug and fixed the test
  C3 narration         : 5 — prompts/accepts/overrides narrated specifically
                             throughout; rater saw every decision
  C4 debug/recovery    : 5 — hypothesis-before-fix on the test-vs-parser case
  C5 communication     : 5 — two upfront clarifying questions + one mid-stream
  Recommendation: HIRE. Centaur pattern; Axis A signal clear.
  ✅ match.

Candidate R.T. — NO-HIRE
  C1 problem decomp    : 1 — pasted brief into Cursor as first move;
                             structure emerged from generation
  C2 agent use quality : 1 — accept-all on outside-frontier slice; no override;
                             accepted `or 0` and could not defend it; re-
                             prompted on failure instead of debugging
  C3 narration         : 1 — silent middle 10 min; SCORED DOWN not neutral
                             (Ch. 2 Step 6)
  C4 debug/recovery    : 2 — "fix it" re-prompt, not a hypothesis; tests
                             passing is not recovery
  C5 communication     : 2 — no upfront questions; late acknowledgement only
  Recommendation: NO-HIRE. Uncritical-consumer pattern; Axis A signal
                  negative; Chapter 2 floor on C2+C3 1s at mid-level.
  ✅ match.

Drift notes:
  First pass I scored R.T.'s narration at 3 — "silent isn't bad, is it?"
  Re-read Step 6: it IS bad, because the signal the stage measures is
  specifically absent. Second-pass score: 1. The pre-AI instinct ("silence
  is a style choice") is miscalibrated for the disclosure stage.
```

## Checkpoint

Before moving on to Exercise 01 (authoring the full interview-loop redesign for your own team), you should be able to answer **yes** to all five:

- Did you score R.T.'s narration criterion at **1**, not 3, with reasoning that cites Chapter 2 Step 6's "scored down, not neutrally" framing?
- Did you distinguish M.K.'s agent-use pattern (effective delegation + retained judgement — Chapter 4 centaur) from R.T.'s agent-use pattern (accept-all on outside-frontier — Dell'Acqua uncritical consumer) on the right basis?
- Did you reach a **NO-HIRE** on R.T. despite the final artifact passing tests, because the Chapter 2 rubric scores the *process* (how the artifact was produced) not only the *artifact*?
- Did you resist the pre-AI instinct to average R.T.'s score across criteria to a "borderline pass"? A mid-level screen's floor on C2 + C3 1s is no-hire, per Chapter 2's stage-level signal design.
- On your drift diagnosis, did you identify the specific pre-AI framing you were applying (artifact-only scoring; silence as neutral; delegation as under-work; sum-weighted hire decisions) so your next rater-calibration session with the panel surfaces the same pre-AI framing for your colleagues?

If any answer is no, re-read Chapter 2 Steps 6–8 end-to-end — the "Operationalise the disclosure stage specifically," "Live-coding and live-writing rubrics," and "What *not* to do" sections — and re-run Step 2 or Step 3 of this lab before authoring Exercise 01 on your real team's loop.
