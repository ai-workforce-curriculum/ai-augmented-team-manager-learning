# Exercise 01 — Authoring the AI PR / Document Review Checklist

**Estimated effort:** 2 hours.

## Objective

Produce a **dated, team-specific, PR-template-shaped** review checklist for AI-generated work, covering the seven sections from Chapter 2 (**Provenance, Scope, Correctness, Verification run, Context fit, Security / data-handling, Accountability**), tailored to at least **three artifact classes** your team actually produces. The output is a `pull_request_template.md`-style artifact you could land in your own repo today, plus a per-class verification-bar table that lives alongside your human/machine contract.

This is the first of the seven mod-103 artifacts you will produce; Exercise 02 encodes the same norms into AGENTS.md and Cursor rules at the point of authorship, and Exercise 03 pushes them into lint policies and ADR templates. Keep the three exercises coherent.

## Prerequisites

- Chapters 1 and 2 of this module.
- Chapter 3 of [`mod-101`](../../mod-101-ai-augmented-team-manager-position-and-contract/) — the human/machine contract. The verification bar per class must end this exercise consistent with the C1 / C2 columns of your contract; if you already have a draft, bring it.
- Access to one month of your team's actual PR history (even if you anonymise it). You need the real artifact shapes and the real scope ranges, not a template.
- The repo your team uses day-to-day. The checklist lands in `.github/pull_request_template.md` (or the equivalent for your VCS); if you cannot reach the repo, work in a scratch repo with representative structure.

## Problem statement

Pick three artifact classes your team ships and whose author could realistically be a model. Common candidates: *production code PRs, test PRs, PR descriptions, ADRs, operational runbooks, dashboard / SQL queries, status updates, customer-facing error messages.* You decide which three — but at least one must be *production code* (because that is where review-compression failures hurt most), and at least one must be *not code* (because the checklist needs to generalise).

For each class, you will author a verification bar; then you will write one unified PR template (or document template, for the non-code classes) that carries the Chapter 2 checklist sections and renders cleanly for a reviewer on submission.

## Steps

1. **Enumerate the three artifact classes.** Write one line per class naming (a) what it is, (b) a typical size (lines-of-code, word-count, number-of-cells), and (c) the current ratio of AI-authored to human-authored instances. If you do not know (c), estimate and flag — the exercise still works.
2. **Draft the verification bar per class.** Use the Chapter 2 table as the scaffold. For each class, answer the seven section questions explicitly:
   - *What counts as adequate Provenance capture for this class?*
   - *What counts as "in-scope" for this class, and what is the scope-bleed failure mode?*
   - *What does "every line read" look like for this class (or the equivalent "every claim verified")?*
   - *What is the Verification run for this class — tests? executed runbook? reconciled query? read-aloud draft?*
   - *What context does the model specifically not have on this class, and how does the reviewer close the gap?*
   - *Which OWASP LLM Top 10 risks are likely to apply to this class (preview for Exercise 06)?*
   - *How is accountability routed on this class — IC and reviewer named? manager signs off on sensitive classes?*
3. **Set a honest review-time budget per class.** One number per class: "a model-authored instance of this class, of typical size, should take a reviewer at least N minutes to review to the stated bar." If the number is less than the comparable human-review number, re-check your bar.
4. **Write the unified PR template.** Use the Chapter 2 PR-template shape (ten or so checkboxes) and tailor the section wording for your team. Keep it on one screen. Name the file `pull_request_template.md` for a code repo, or `doc-template.md`/equivalent for a non-code repo. Ensure the load-bearing sections (Correctness, Verification run, Accountability) are clearly non-skippable.
5. **Produce the per-class verification-bar table as a separate doc.** `docs/ai-review-checklist.md` (or your team's wiki equivalent). Three rows minimum, one per class. Include the review-time budget column.
6. **Dry-run on a real recent PR.** Pick a recently-merged PR from your team that was (or plausibly could have been) AI-authored. Open your draft PR template against it. Does the template catch what the original review missed (if anything)? Does it demand something the review already did? Note both.
7. **Walk the draft to two reviewers.** Not for approval — for feedback. Specifically ask: *does the checklist feel like it would make your review slower? If yes, is the slowness honest (reflecting real work) or theatre (checkbox noise)?* Record the pushback and decide, per item, whether to keep, cut, or reword.
8. **Freeze v0.1.** Title it `AI Review Checklist v0.1 — [team name] — [YYYY-MM-DD]`. List the author (you) and the two reviewers who pushed back. Add a two-sentence scope-and-caveats note. Add a change log.

## Starter guidance

- The Chapter 2 PR-template example is a shape, not a template to copy. Your team's classes and model failure modes will differ; the sections should not.
- For the non-code class, resist translating "read every line" as "read every line" — the operational verb may be *verify every claim*, *execute every step*, *reconcile every number*. Pick the right verb for the artifact.
- The review-time budget is the single most load-bearing number in the artifact. Set it from a sample of real review timings on your team, not from wishful thinking. If no reviewer currently takes that long, the standard has not been adopted yet and part of this exercise is to notice that.
- A checklist that renders as "many unchecked boxes a reviewer must tick" invites checkbox-skimming. Favour the structure where each box is a *question* the reviewer answers in writing rather than a checkbox they click, for the three load-bearing sections (Correctness, Verification run, Accountability). The friction is the point.
- Resist adding a section that duplicates what the linter / type-checker / CI already does. The PR template is for what the humans do, not what the tools do. Your Exercise 03 work will carry the tool-enforced side.
- Keep an explicit "we have decided this does *not* apply here" option for any section where some classes legitimately skip. "N/A" with a one-line reason is better than silent skip.

## Acceptance criteria

The checklist is complete when:

- Three artifact classes are enumerated with (a) description, (b) typical size, (c) AI-authorship ratio (estimated if unknown).
- A verification-bar table lives at `docs/ai-review-checklist.md` with one row per class, covering all seven Chapter 2 sections, with an explicit review-time budget column.
- At least one class is *production code* and at least one class is *not code*.
- A unified PR template exists at `.github/pull_request_template.md` (or your VCS equivalent) with no more than ~12 checkboxes / short-answer prompts, covering Provenance, Scope, Correctness, Verification run, Context fit, Security, Accountability.
- The PR template has been dry-run against at least one real recent PR, with findings documented.
- At least two reviewers on your team have given feedback; the feedback is either reflected in v0.1 or logged as a counter-argument.
- The artifact is titled, dated, lists contributors, carries a scope-and-caveats paragraph, and carries a change log.
- Review-time budget per class is specified numerically and is ≥ the comparable human-authored review time.

## Stretch goals

- **Scope-bleed autopsy.** For each of the three classes, pull one actual AI-authored artifact from your team's history and mark every instance of scope bleed (changes outside the stated task). Compile the failure-mode profile per class and feed it into the Scope section wording.
- **Reviewer-licence draft.** Write a one-paragraph "reviewer-licence" requirement for approving AI-authored diffs on each class (per Chapter 2's reviewer-competence floor). Decide what tenure / experience is required. Pair with [`mod-107`](../../mod-107-skill-growth-anti-atrophy-and-career-development/) and [`mod-108`](../../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/).
- **Checklist telemetry.** Design (not implement) a lightweight telemetry hook on the PR template: which sections are filled in, which are skipped, which classes have the highest skip rate. Use the data to tune v0.2 of the checklist. Pair with the eval work in Exercise 04 / 05.
- **Cross-team comparison.** Share your v0.1 with one peer manager on a different team. Compare bars, scope-bleed profiles, and review-time budgets. Note divergences without resolving them — the divergences are themselves data about team variance.
- **One-reject walkthrough.** Walk a reviewer through what *rejecting* a model-authored PR on this checklist looks like socially — not what the PR-template renders, but what the reviewer says in the review thread, and what the author (human) does next. The socio-technical half of the checklist is what makes it stick.
