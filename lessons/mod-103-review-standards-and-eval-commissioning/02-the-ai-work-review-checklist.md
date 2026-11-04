# Chapter 2 — The AI-Work Review Checklist and the Verification Bar

> *The reviewer's job on a model-authored diff is not to check the diff. It is to check the things the model could not.*

## Motivation

The most common complaint from teams six months into AI-augmented work is not that the model drafts bad code. It is that the review is now the bottleneck, and the reviewers do not know what they are supposed to be looking for.

Two symptoms, both from the posting sample and from working-team reports:

- *"Our PR queue doubled, our review time per PR dropped, our on-call pages for merge-related regressions tripled."* The team compressed the review step because the diff *felt* easier. The diff was not easier; the reviewer was answering a different question than the one the model made important.
- *"Our senior ICs refuse to review model-authored PRs, so the junior IC approves them."* Seniors (correctly) sense that the reviewer is now holding the risk, and (incorrectly) opt out, which concentrates the risk on the least-experienced reviewer.

A written, class-specific **review checklist** is the standard defence. The checklist does not need to be long. It needs to be anchored on the right questions, honest about the review-time budget required, and enforced by the team's tooling where enforceable. This chapter is the manager-owned version of that checklist.

Chapter 3 encodes it into the standards-as-code stack. Chapter 5 attaches it to the accountability contract. Chapter 6 maps the OWASP LLM Top 10 risks into it. Chapter 4 sets up the eval that will tell you whether the checklist is actually catching what it should.

## Core concepts

### The question the reviewer is actually answering

On a human-authored PR, the reviewer answers roughly: *does this change, as written, do what the author says it does — and are they the right person to be making the call?* Intent is the dominant question; the author is on the hook for intent because they are a known colleague with a known mental model.

On a model-authored PR, the reviewer answers a different question: *is this change correct, safe, scoped, and contextually appropriate — and does it match the context the model could not see?* Intent is not meaningfully present; the "author" is a stateless function of the prompt and the retrieved context. The reviewer is effectively acting as the model's missing judgment about team norms, downstream consumers, political context, in-flight work, security posture, and data boundaries.

That is more work, not less. A review checklist that pretends model-authored diffs are a lower-scrutiny class has already lost. Honest planning starts from: *review of model-authored work takes **at least** as long as review of comparable human-authored work on the same topic*, and often longer because the reviewer has to replicate the mental model from scratch.

### The seven checklist sections

A workable AI-work review checklist has seven sections. It is deliberately boring. Boring is the point — a surprising checklist is one that is being skimmed.

**S1. Provenance.** Which agent produced this, with which model version, from which prompt (or prompt-chain), with which retrieved context, against which repo / doc snapshot. Not for the reviewer to audit verbatim — for the reviewer to know when to add scrutiny (a new model version is worth more care than a known one) and for the incident process to have a trace later ([`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/)). The minimum: *who was the agent, what was the task, what was the surface area it was allowed to touch*.

**S2. Scope.** Does the change-set match the stated task? AI-authored diffs are famous for *scope bleed* — the agent reaches into an adjacent file, upgrades a dependency, renames an internal API, or rewrites a function it was asked to read. The reviewer calls out and removes anything not in-scope. Scope is a hard reject, not a stylistic preference.

**S3. Correctness.** Every line read; the logic walked; the specific failure modes the model type is known to produce (off-by-one, swapped-arg, hallucinated API, wrong import target, confused library-version) checked. No "LGTM" on a diff that was not read line by line — this is the single hardest social norm to hold and the single most important.

**S4. Verification run.** What is runnable has been run — tests pass locally and in CI; linters and type-checkers are clean; benchmarks (if the diff claims a perf implication) actually measured; queries (if the diff claims a result) executed against the environment it is intended for, not only against the model's imagined one. If something that *should* have been runnable was not run, the diff is not reviewable.

**S5. Context fit.** Does the change match context the model could not see — team norms, naming conventions, downstream-consumer expectations, the in-flight work the author's two teammates are doing on the same files, the political context of why the surrounding code is the way it is. This is the most reviewer-judgment-heavy section. It is where the human review earns its keep and where a less-senior reviewer will miss what a senior reviewer would catch.

**S6. Security and data-handling.** The OWASP LLM Top 10 reading (Chapter 6). At minimum: prompt-injection surface is audited where the diff touches an agent's instruction surface; sensitive data is not getting into prompts or tool outputs; untrusted output is not interpolated into downstream shell / SQL / HTML without handling; new tool / MCP connections are authorised. Short-form; the depth is in Chapter 6.

**S7. Accountability.** The submitter and the reviewer each explicitly note that they take the regression if this ships broken. Not a performative line — a procedural one. It is what makes the accountability contract (Chapter 5) binding at the atomic level.

Seven sections is the floor. Tailor per artifact class (code vs. ADR vs. runbook vs. report) with the same shape. Any shortening below seven should be a deliberate, written decision — not a drift.

### Verification requirements per artifact class

Not every artifact class is a code PR. The verification bar changes with the shape of the artifact. A workable per-class spec (the C2 column of the human/machine contract from [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) Chapter 3, reduced to its operational form):

| Artifact class | Verification bar |
|---|---|
| Production code (library/service/CLI) | Every line read; tests run; types pass; scoped; one reviewer approval; accountability line signed. |
| Tests (unit/integration) | Every assertion read and understood; test runs against the system-under-test, not a mocked one unless deliberately; false-positive risk considered (does the test pass for the wrong reason?); accountability line signed. |
| PR description | Read; any claims about why the change is needed checked against the ticket / spec; auto-generated rationales treated as drafts, not statements. |
| ADR (architecture decision record) | Decision read; alternatives section stress-tested; consequences section edited by a human; downstream-consumer list verified; linked back to the originating discussion. |
| Runbook / operational doc | Steps executed end-to-end in the environment they describe, not reasoned about. An un-executed model-written runbook is a hazard, not a doc. |
| Dashboard / SQL query | Query run; result reconciled against a known-good alternate source; data-handling boundary checked (is the output allowed to leave the warehouse?). |
| Status update / weekly / exec pre-read | Edited heavily enough that the output is yours, not the model's. Tone, honesty about risk, and no model-produced flattery. |
| Employee feedback / promo / performance input | *Not AI-drafted at all* on most teams. If allowed, drafted + rewritten end-to-end by the manager; no part of the model draft is kept verbatim. |
| Incident post-mortem | *Not AI-drafted at all* on most teams. If allowed, first draft only; human rewrites before publishing. Chapter 5 is strict on this. |
| Customer-facing comms (error msg, email, docs) | Human-rewritten for voice; legal / brand review where applicable. |

This table lives in your team's wiki as part of the review standard. Chapter 3 encodes the subset that is encodable.

### The review-time budget is part of the standard

A checklist that assumes infinite reviewer time is theatre. Name the budget:

- *How long is a reviewer expected to spend on a model-authored PR of size N?* Honest answer: proportional to the diff size, times a factor ≥ 1 relative to a comparable human-authored PR. On most teams this is *at least* the same amount of time; initial-use teams often report longer.
- *Who holds the budget?* The manager — you — when the reviewer queue grows past what the team can absorb. If the team cannot review every model-authored PR to the stated bar in the stated budget, the response is *throttle production*, not *lower the bar*. Options: reduce the number of agent-authored PRs per IC per day, require two submitters per model PR, or restrict the classes the model is allowed to draft.
- *What happens if the budget is blown?* The PR waits. There is no fast-path for "it was drafted by a model." The queue is the team's defence against the review-compression failure mode.

An unstated review budget is a hidden tax paid by whichever reviewer is least likely to say no.

### The reviewer competence floor

Reviewing model-authored work is a skill that is not identical to reviewing human-authored work. The relevant skills:

- Recognising the specific failure modes of the model type being used (hallucinated APIs, off-by-one at boundaries, fabricated test assertions, wrong library-version idioms, retrieval-contaminated reasoning).
- Reading the trace / context window that was available to the model, where the eval tool exposes it (Chapter 4).
- Judging context fit — which improves with seniority and team tenure.
- Holding the social norm against "LGTM-skim" culture.

A rough floor: the reviewer-of-record should have at least six months of human-authored review experience in this codebase, and should have produced, read, and approved at least ten model-authored PRs under supervision before approving unsupervised. Teams sometimes codify this as a *reviewer's licence* — managed in the team's HR-adjacent tracking and threaded into [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/) and [`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/).

### The checklist, as a PR template

The form that works best on most teams is a PR template (`.github/pull_request_template.md` for GitHub, equivalent for GitLab / Gerrit / Phabricator) that the author fills in on submission and the reviewer uses as the review scaffold. The template is rendered on every PR; the standards-as-code stack (Chapter 3) blocks merges when load-bearing sections are blank.

One concrete shape:

```markdown
## Authorship

- [ ] Agent / model / version: <!-- e.g. Claude Code 2026-10-14 / claude-sonnet-4-6 -->
- [ ] Prompt / task spec linked: <!-- link to doc, ticket, or in-repo prompt -->
- [ ] Retrieved context surface: <!-- which files/docs the agent was allowed to see -->

## Scope

- [ ] Change-set matches the stated task; no scope bleed.
- [ ] If any file outside the task boundary is touched, justified below.

## Correctness

- [ ] I read every line the model wrote.
- [ ] Known model failure modes for this task class considered (hallucinated APIs, wrong versions, off-by-one, fabricated tests).

## Verification run

- [ ] Tests pass locally and in CI.
- [ ] Linters / type-checkers clean.
- [ ] If the diff claims a perf or data result, the result has been measured in the intended environment.

## Context fit

- [ ] Change matches team conventions (AGENTS.md, Cursor rules, lint).
- [ ] Downstream consumers / in-flight work by teammates considered.

## Security and data-handling

- [ ] Prompt-injection surface audited where applicable (OWASP LLM01).
- [ ] No sensitive data in prompts, logs, or outputs (OWASP LLM06).
- [ ] Any new tool / MCP connection authorised (OWASP LLM08).

## Accountability

- [ ] Submitter accepts the regression if this ships broken.
- [ ] Reviewer accepts the approval if this ships broken.
```

Ten or so checkboxes. Not thirty. A checklist people will not do is worse than a shorter one they will.

## Example: the "clean-but-wrong diff" an AI-work checklist is designed to catch

Treat this as an illustrative calibration, not a verified incident:

> A model-drafted diff rewrites a pagination helper. The syntax is clean, the tests pass, the lint is green. The diff reads well on skim. The reviewer notices the model has silently switched the pagination from 0-indexed to 1-indexed because that was the convention in the retrieval-context snippet the agent happened to see. The existing callers are 0-indexed. The CI tests happen to be shaped around the helper's own fixtures, so they still pass. The reviewer catches this in the **Context fit** section — specifically the "in-flight work by teammates" line — because they recall a teammate was adjusting a caller yesterday. Without the checklist row, the reviewer would have approved on "tests pass + diff reads clean." The row was the defence.

The point: the checklist's value is not in the easy catches. It is in the ones where the diff *looks* fine and the review has to be deliberate to catch what the model could not know.

## Summary

- The reviewer on a model-authored diff is answering *a different question* than on a human-authored one — *does this match what the model could not see?* — and the review takes at least as long.
- Seven checklist sections: **Provenance, Scope, Correctness, Verification run, Context fit, Security / data-handling, Accountability.** Short, boring, non-negotiable.
- Verification bar varies by artifact class — code and tests are bounded, runbooks and queries demand execution, feedback / post-mortems are usually *not* AI-drafted at all.
- The review-time budget is part of the standard. Throttling production is the right response to a blown budget; lowering the bar is the wrong one.
- The checklist lives as a PR template so every submission renders it; standards-as-code (Chapter 3) enforces the load-bearing sections at merge gate.
- Exercise 01 is where you author the checklist for your team's actual artifact classes.
