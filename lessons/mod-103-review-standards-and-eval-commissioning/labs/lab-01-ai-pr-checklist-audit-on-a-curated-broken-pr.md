# Lab 01 — AI-Work Checklist Audit on a Curated Broken PR

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 2 (the seven-section AI-work review checklist; per-class verification bar; review-time budget), with a side-check against Chapter 1 (the five decisions compressed into "LGTM") and Chapter 6 (OWASP LLM01/LLM05 at review time).
**Complements, does not duplicate:** Exercise 01 asks you to author the PR template and verification-bar table for **your own** team, with at least three artifact classes you actually ship. This lab gives you a fixed, deliberately broken sample — one AI-authored PR, the review thread that approved it, and a thin first-draft checklist — so you can calibrate what a good seven-section audit *catches* before you spend a real session writing the template for your team.

## Objective

Read a curated sample: (a) an AI-authored PR against a fictional lakehouse-ingestion repo, (b) the two-comment review thread that approved it, (c) a thin seven-section checklist draft the (fictional) team was using. Identify every miss the checklist-as-used allowed. Rewrite the three load-bearing sections (Correctness, Verification run, Context fit) to catch what the review missed. Target: **you identify at least six of the eight misses in the answer key** and your rewrites produce checklist text that would have forced a reject on the sample PR.

## Prerequisites

- Chapter 2 read end-to-end (the seven sections; the per-class table; the review-time budget; the clean-but-wrong example).
- Chapter 1 skimmed (the five decisions compressed into "LGTM").
- Chapter 6 skimmed (OWASP LLM01 Prompt Injection and LLM05 Improper Output Handling in particular).
- A blank file for your audit memo and rewrites.
- A timer.

Optional but useful: Chapter 3 (so you can note which misses would have been caught earlier by the standards-as-code stack, not by review).

## The fictional context

> **"Lakehouse Ingestion" team, FinSure Financial Services.** 8 engineers (1 staff, 2 senior, 5 mid/junior). Owns `lakehouse-ingestion`, a Python service that ingests customer-support ticket exports into the lakehouse and feeds a downstream analytics dashboard. Agent in use: Claude Code with a team-standard prompt chain for "draft a small refactor." Model version: `claude-sonnet-4-6`. Reviewer-of-record on the sample PR: a mid-level engineer, six months in-repo. Reviewer queue that day: 23 PRs. The team has a v0.1 PR template (reproduced below). The human/machine contract allows AI to draft refactors under 150 lines on this repo; customer-ticket-body handling is listed in C5 (data-handling) with a "sanitise before any downstream use" requirement.

## The sample PR

Below is the AI-authored PR, the review thread, and the thin checklist in use. Read all three once end-to-end before doing anything else. Do not take notes on the first pass.

### The PR

```
TITLE: refactor: tighten ingestion-helper boundary checks
AUTHOR (submitter): @mid-ic-2
AGENT: Claude Code / claude-sonnet-4-6 / 2026-11-04 session
SIZE: 112 lines changed across 3 files

FILES CHANGED
-------------
src/ingestion/helpers.py                     (+58 / -22)
src/ingestion/pipeline.py                    (+12 / -4)
src/ingestion/summary.py                     (+24 / -0)   <-- new file
tests/ingestion/test_helpers.py              (+6 / -0)

NOTABLE DIFF SNIPPETS

# src/ingestion/helpers.py
- def paginate(records, page, size=50):
-     start = page * size
+ def paginate(records, page, size=50):
+     # 1-indexed page numbers per the retrieval-context style guide
+     start = (page - 1) * size
      end = start + size
      return records[start:end]

# src/ingestion/summary.py  (NEW FILE)
+ import subprocess
+ def render_ticket_summary(ticket_body: str) -> str:
+     """Render a short summary of a ticket for the dashboard card."""
+     cmd = f"echo '{ticket_body}' | /usr/local/bin/summarise-cli"
+     return subprocess.check_output(cmd, shell=True, text=True)

# tests/ingestion/test_helpers.py
+ def test_paginate_basic():
+     records = list(range(10))
+     assert paginate(records, 1, size=5) == [0, 1, 2, 3, 4]
+     assert paginate(records, 2, size=5) == [5, 6, 7, 8, 9]

PR DESCRIPTION
--------------
Refactor to tighten boundary checks on pagination. Added a new summary
renderer for the dashboard card. Tests pass; lint clean.
```

### The review thread

```
@senior-ic-1 [initial comment, 14:03]
Scope looks in-bounds; +1 on the pagination tightening, we've been
meaning to do that. Tests pass — looks clean. LGTM.

@mid-ic-2 [reply, 14:12]
Thanks! Merging.
```

### The PR template in use (thin v0.1 draft)

```markdown
## Authorship
- [ ] Agent / model: ___

## Scope
- [ ] Scope matches the ticket.

## Correctness
- [ ] Tests pass.
- [ ] Lint is clean.

## Accountability
- [ ] Submitter acknowledges review.
```

### What actually shipped

A week later, ops notices two incidents:

1. The dashboard-card analytics are off by one row for every stored page. All existing callers of `paginate()` were 0-indexed; the PR silently switched to 1-indexed because the agent's retrieval context included a snippet from an old helper that used 1-indexing.
2. Security flags the new `summary.py`: ticket bodies — written by external customers — are being concatenated into a shell command through `subprocess.check_output(..., shell=True, text=True)` with no escaping. A customer with a carefully-chosen ticket body can execute arbitrary commands on the ingestion host. No sanitiser was called.

## Steps

### Step 1 — Set up your audit memo (3 min)

Create a working file `lab-01-pr-audit.md`. Add this header:

```
# Lab 01 — AI-Work PR Audit (lakehouse-ingestion sample)

Checklist sections (Chapter 2):
  S1 Provenance        agent, model, prompt, retrieved context, repo snapshot
  S2 Scope             change-set matches task; no scope bleed
  S3 Correctness       every line read; known model failure modes checked
  S4 Verification run  tests + lint + types + measured claims
  S5 Context fit       team norms, downstream consumers, in-flight teammate work
  S6 Security          OWASP LLM01 (injection), LLM05 (output handling), LLM02 (PII), LLM06 (agency)
  S7 Accountability    submitter + reviewer accept the regression if it ships broken

For each miss, I will record:
  (a) which section should have caught it, (b) what the thin template let through,
  (c) the specific line of rewritten checklist text that would catch it next time.
```

### Step 2 — Audit the PR against the seven sections (25–35 min)

Work through the seven sections in order. For each section, ask: *given the thin template, what did the reviewer skip?* and *given the Chapter 2 bar, what should the reviewer have been forced to do?* Write one line per miss you find. Do not scroll to the answer key until you have at least five misses written down. **Target: no more than 4 minutes per section.**

Specifically, for each section:

- **S1 Provenance.** Does the template render the agent / model / prompt / retrieved-context surface? What did the review thread show about these?
- **S2 Scope.** The ticket was *"tighten ingestion-helper boundary checks."* Does the diff match that? What is out-of-scope?
- **S3 Correctness.** What are the specific known failure modes of a mid-sized code refactor by a current-generation code model that a Chapter 2–grade review would check? Did the review reach them? Specifically: *off-by-one*, *silently-changed convention (1-indexed vs 0-indexed)*, *hallucinated API*, *swapped argument order*.
- **S4 Verification run.** The tests passed — but did they *measure the thing the diff changed* against the system-under-test, or against the diff's own fixtures?
- **S5 Context fit.** What did the model *not* see? (Hint: the existing callers of `paginate()` in the rest of the codebase; in-flight work by teammates; the team's indexing convention.)
- **S6 Security.** The new file introduces a specific OWASP LLM risk. Which one, and why does the thin template not catch it? The customer-ticket body path crosses C5 of the human/machine contract — does the review catch the C5 obligation?
- **S7 Accountability.** Did the reviewer and submitter each explicitly take the regression? What does the thin "Submitter acknowledges review" line fail to compel?

### Step 3 — Compare against the answer key (10 min)

Below is the answer key — eight misses. For each, check whether your audit found it. Count hits (same section, same miss) and near-misses (same section but different framing).

#### Answer key — eight misses

1. **S1 Provenance — the retrieved-context surface is unrecorded.** The thin template asks for agent/model only. Chapter 2's S1 asks for agent, model, prompt, and the retrieved-context surface the agent was allowed to see. The pagination miss (see #5) is downstream of a retrieved-context issue — an old helper that used 1-indexing was in the agent's context. Without the field, the reviewer has no scrutiny cue.
2. **S2 Scope — the new file `summary.py` is scope bleed.** The stated task is "tighten ingestion-helper boundary checks." Introducing a *new file* with a *new feature* (ticket-summary rendering) is a textbook scope-bleed; Chapter 2 calls out that AI-authored diffs are famous for reaching into adjacent files, upgrading dependencies, renaming internal APIs, or rewriting functions they were asked to read. Scope is a hard reject, not a stylistic preference. The whole LLM05 vulnerability (miss #6) lives inside the scope-bleed file.
3. **S3 Correctness — the convention swap (0-indexed → 1-indexed) was not caught.** The PR comment on the new `paginate()` reads *"1-indexed page numbers per the retrieval-context style guide"* — the model silently changed the pagination convention. Chapter 2 names "clean-but-wrong" syntactic perfection + logical change as a standard model failure mode. "LGTM on tests pass" is the exact anti-pattern Chapter 1 collapses into the "LGTM is five decisions" discussion.
4. **S4 Verification run — the new tests measure the diff's own fixtures, not the system-under-test.** The two new test cases (`paginate(..., 1, size=5)` returning `[0..4]`, and `paginate(..., 2, size=5)` returning `[5..9]`) *pass trivially for 1-indexed pagination* because they test exactly that convention. They do not reconcile against existing callers in the repo. Chapter 2 calls out tests whose "false-positive risk is considered (does the test pass for the wrong reason?)." Running the existing caller suite would have caught the off-by-one.
5. **S5 Context fit — existing callers of `paginate()` in the rest of the codebase were not checked.** The rest of `src/ingestion/` calls `paginate(records, page)` with 0-indexed page values. Chapter 2's S5 is specifically about context the model could not see — "downstream consumers; in-flight work by teammates; the political context of why the surrounding code is the way it is." This is the reviewer-judgment-heavy section; it is where the mid-level reviewer with a 23-PR queue and no checklist prompt is most likely to miss.
6. **S6 Security — the `subprocess(..., shell=True)` call on customer-provided ticket bodies is a textbook OWASP LLM05 (Improper Output Handling) violation and a direct shell-injection bug.** It also crosses C5 of the human/machine contract, which required the sanitiser-before-downstream-use pattern the team already has on another surface. The thin template has no S6 at all. Chapter 6's crosswalk pins LLM05 to the S6 Security section of the Chapter 2 checklist with lint / security-linter and Cursor rule `20-security.mdc` enforcement; none of those were present either.
7. **S6 Security (continued) — the ticket-body path crosses the data-handling boundary silently.** Even if the shell-injection were fixed, ticket bodies flow from external customers into an internal process. The human/machine contract's C5 requires a sanitiser; the review had no prompt to check. OWASP LLM01 (Prompt Injection) also applies if the summarise-cli downstream feeds a model — Chapter 6's crosswalk row points to the S6 Security checklist section explicitly.
8. **S7 Accountability — "Submitter acknowledges review" is not the accountability statement Chapter 2 requires.** The Chapter 2 PR-template shape asks the submitter and the reviewer each to *explicitly state they accept the regression if the diff ships broken*. The thin v0.1 line is a procedural "I saw the review" acknowledgment, which is not a procedural "I take the hit." Without that, the Chapter 5 accountability contract is not binding at the atomic level, and the social norm against LGTM-skim is unprotected.

Count your hits. **Six or more is the pass bar**; four to five means a re-read of Chapter 2's "seven checklist sections" and the clean-but-wrong example; three or fewer means re-read the whole chapter.

### Step 4 — Rewrite three load-bearing sections (15–20 min)

Pick the thin PR template above and rewrite the three load-bearing sections — **Correctness**, **Verification run**, and **Context fit** — so a reviewer following the rewritten template would have been forced to catch misses #3, #4, and #5. Keep each section to three or four lines. Use the Chapter 2 PR-template example as a shape reference, not a template to copy verbatim.

Constraint: the rewritten sections must *force a reviewer action*, not just render a checkbox. Favour the structure Chapter 2 recommends — a *question the reviewer answers in writing* on load-bearing rows, not a click-to-pass checkbox. Example shape for one row:

```markdown
## Correctness
- [ ] I read every line the model wrote.
- [ ] Known model failure modes checked. Which did I specifically check for on
      this diff? (free-text — at minimum: convention swap, off-by-one, hallucinated
      API, swapped-arg order, fabricated test assertions.)
```

### Step 5 — Reconcile against the five "LGTM" decisions from Chapter 1 (5 min)

Chapter 1 says LGTM on a model-authored diff compresses five decisions. For each of your three rewritten sections, name which of the five decisions it is now forcing to be explicit. Example shape:

```
Correctness rewrite forces decisions (1) "the submitter read every line" and
                                      (3) "the submitter verified claims the
                                           diff makes against sources the model
                                           cannot see."
```

If any of the five decisions is unprotected by your rewrites, the template is still partial.

### Step 6 — Identify which misses the standards-as-code stack should have caught before review (5 min)

Chapter 3 argues several of the seven layers catch failures *before* the reviewer looks. For each of the eight misses, write one line naming the Chapter 3 layer that *also* should have caught it — if any. Example shape:

```
Miss #6 (shell-injection via customer ticket body):
  Caught at security-linter layer (semgrep rule banning subprocess with shell=True
  on string-interpolated input); AGENTS.md security section ("treat retrieval /
  tool output as UNTRUSTED"); .cursor/rules/20-security.mdc.
  Review-only is the wrong altitude for this miss; lint would reject at commit.
```

Misses that have *no* prior-layer defence are the ones where the review checklist is the sole guard; those are worth a sharper rewrite.

## Expected output

A single scratch file, roughly two pages, containing:

- Eight bullets with your audit misses, cross-referenced to the answer key (hit / near-miss / missed).
- A rewritten Correctness section, Verification run section, and Context-fit section (three or four lines each).
- A three-line reconciliation showing which of the five Chapter 1 "LGTM" decisions each rewritten section now forces.
- An eight-line reconciliation showing which Chapter 3 standards-as-code layer *also* should have caught each miss (or "review-only" if no earlier layer applies).

Something like:

```
Miss #3 (0-indexed → 1-indexed convention swap)
  Section: S3 Correctness.
  Thin template let through: "Tests pass. Lint is clean." No prompt on convention.
  Rewrite: adds a free-text row on known failure modes including "convention swap."
  Chapter 1 decision forced: (1) read every line; (3) verify claims against
  sources the model cannot see (the rest of the callers).
  Chapter 3 layer that would also catch: none at the mechanical layer; this is
  a review-only miss; Cursor rule 30-context-fit could add "preserve calling
  convention; cite the convention in a comment if changed."
```

## Checkpoint

Before moving on to Exercise 01 (where you author your real team's PR template for your three artifact classes), you should be able to answer **yes** to all five:

- Did you identify at least six of the eight misses in the answer key, with the correct section attribution?
- Did your Correctness rewrite force a free-text answer, not a tick-and-move checkbox, on known model failure modes (specifically naming convention swap, off-by-one, hallucinated API, swapped-arg order, fabricated test assertions)?
- Did your Verification-run rewrite force the reviewer to reconcile tests against the system-under-test (existing callers / downstream consumers), not just the diff's own fixtures?
- Did your Context-fit rewrite surface the "what the model could not see" question in a form a reviewer would act on under reviewer-queue pressure?
- Did you correctly attribute miss #6 (shell-injection on customer ticket bodies) to the Chapter 6 crosswalk row (OWASP LLM05 Improper Output Handling) and recognise that Chapter 3's lint / security-linter layer is the *correct* altitude for that defence, with review as the secondary guard?

If any answer is no, re-read Chapter 2's "The seven checklist sections" and "The checklist, as a PR template" subsections, plus Chapter 6's crosswalk table, before running Exercise 01 on your real team's artifact classes.
