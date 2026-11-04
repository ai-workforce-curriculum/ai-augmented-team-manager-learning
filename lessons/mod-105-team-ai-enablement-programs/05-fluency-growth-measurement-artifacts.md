# Chapter 5 — Measuring Fluency Growth with Practical Artifacts

> *A fluency score is a slogan. A merged PR with a reflection, a pair-with-agent write-up, and a self-review of your own prior review are the evidence the slogan should have come from.*

## Motivation

R5 is explicit on the measurement side: *"measure fluency growth with practical artifacts (first-successful-PR-with-tool, pair-with-agent-reflection, review-of-your-review) grounded in Josh Bersin AI-in-L&D research and Microsoft Work Trend Index data."* The three named artifacts are the module's load-bearing measurement instruments; Chapter 6 details the research anchors behind the choice.

Why artifacts, not scores: a stage pin (Chapter 4) is a snapshot. It captures where the engineer is on a scale; it does not capture how they are *moving*. A programme that measures only stage pins ends up with a stage distribution that updates once a quarter and no visibility into whether the intermediate interventions (bootcamps, workshops, CoP) are producing fluency or just activity. The three artifacts are the movement instrument.

Why *these* three artifacts and not others: each targets a distinct failure mode of AI-tooling adoption that the research literature has specifically documented. Chapter 6 maps them one-to-one. This chapter specifies the artifacts operationally — how to produce them, how to score them, how they feed into the mod-104 narrative.

## Core concepts

### Artifact 1 — The first-successful-PR-with-tool

**What it is.** The engineer's first merged PR in the production repository, authored *with* the team's primary AI coding assistant (Cursor / Copilot / Claude Code / equivalent), reviewed by a human, and merged on the normal review path. Not a demo-repo PR; not a sandbox change; not a "hello world" PR squeezed through to check a box.

**When it lands.** Between Day 14 and Day 30 of the engineer's cohort cycle. If it has not landed by Day 30, Chapter 2's "Day-30 PR slippage" diagnostic kicks in.

**What accompanies the PR.** A two-paragraph reflection attached to the PR (as a comment, a linked doc, or a dedicated doc in the engineer's `mod-105/` folder — whatever your team uses):

> *Paragraph 1 — what the tool did well.* Specific sentence on what the tool contributed: a scaffolded function, a test case the engineer would have missed, a refactor suggestion that landed.
>
> *Paragraph 2 — where the tool got in the way.* Specific sentence on where the tool over-reached, hallucinated, pulled wrong context, or produced code the engineer rewrote. Specific references to the reviewer's comments that caught the issues.

**How it is scored.** Not pass/fail. Three readings:

- *Reviewer reading.* The reviewer's comments on the PR are themselves the primary evidence. A PR with zero meaningful review comments either had no review or had a reviewer who was not engaged; both are signals the programme should correct (not the engineer).
- *Reflection reading.* The reflection should be specific. "The tool was helpful" is not specific; "the tool proposed the wrong null-handling pattern for our DB-nullable columns and I rewrote that block" is specific. Vague reflections are a programme-signal to adjust the next cohort's workshop content (per Chapter 3).
- *Composite reading at Day 30 checkpoint.* The 1:1 (Chapter 2) walks the PR, the review, and the reflection together. The manager is reading *whether the engineer can honestly describe how the tool contributed and where it fell short*. That honesty is the fluency signal — not the number of lines accepted, not the Copilot acceptance rate.

**What it is grounded in.** [Peng et al. (arXiv:2302.06590)](https://arxiv.org/abs/2302.06590) measured productivity on a specific real task (an HTTP-server implementation) and found a ~55% speedup for Copilot-assisted developers. mod-105 inherits the shape — *measure on a real task, not on a synthetic benchmark* — while rejecting the extrapolation (the ~55% number cannot be projected onto team-throughput, per mod-104 Chapter 1). The artifact is Peng's methodology at the individual level: the real task is the team's production repo, the measurement is the PR itself.

### Artifact 2 — The pair-with-agent reflection

**What it is.** A one-page reflection written by the engineer after they have delegated a scoped, non-trivial work item to an agent (Claude Code, Cursor agent mode, Devin, the team's own agent, etc.). The task must be *non-trivial* — a bug fix of more than one file, a feature slice the engineer would normally take 2+ hours on, a refactor that touches multiple layers. Not a "generate this one function" task.

**When it lands.** Between Day 45 and Day 60 of the cohort cycle.

**Reflection structure.** One page, five sections:

1. *The task.* One paragraph on what the work item was and why it was chosen (non-trivial, scoped, real).
2. *The delegation.* What instructions the engineer gave the agent at the start (the prompt, the context, the tools authorised, the stopping conditions). Including what they *didn't* tell the agent.
3. *The handback.* What the agent returned. Was it finished? Partially? Went in the wrong direction? How long did it take?
4. *The intervention(s).* Where the engineer stepped in — what caught their eye in review, what they rewrote, what they accepted after reading, what they rolled back.
5. *The judgment.* Would the engineer delegate the same shape of task again? With what changes to the prompt / tools / context / stopping conditions? What shape of task would they *not* delegate?

**How it is scored.** Again not pass/fail. The scoring is a reading at the Day-60 checkpoint:

- *The judgment section is the highest-signal section.* An engineer who writes "the agent did great; I would use it for everything" has not done the pair-with-agent work. An engineer who writes specifically "for this kind of migration, I'd keep the agent; for the next one with the stored-procedure interface I'll go back to hand-writing" is demonstrating the pair-with-agent fluency the artifact targets.
- *The intervention section's specificity.* Vague ("I made some edits") = low signal. Specific ("I replaced the agent's N+1 query pattern in /orders/handler.go with the batched version from /internal/db/batch.go") = high signal.

**What it is grounded in.** [Dell'Acqua et al. (BCG + HBS, 2023)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321) found the "jagged frontier" — AI capability is spiky across tasks, and the humans who out-performed were the ones who had *internalised which tasks to delegate*. The pair-with-agent reflection is the tool for building that internal map on the team's own work.

The reflection is also the operational echo of [Bersin's "capability academy" framing](https://joshbersin.com/) — Bersin's research on AI-in-L&D stresses that capability lands when learners explicitly articulate what they can and cannot do with the tool in their own words. Section 5 of the reflection template is that articulation.

### Artifact 3 — The review-of-your-review

**What it is.** The engineer re-reads one of their *own prior reviews* of an agent-generated PR — specifically, a review they wrote 30 or more days earlier — and writes a short reflection (half a page) on what they would do differently.

**When it lands.** Between Day 75 and Day 90 of the cohort cycle. If the engineer has not accumulated 30 days of distance from an agent-generated review by Day 75, substitute the longest gap they have; if they have never reviewed an agent-generated PR, that is itself a signal that the programme is not connecting to the team's actual work.

**Reflection structure.** Half a page, three sections:

1. *The original review.* Link to the PR; one-sentence recap of what the agent proposed and what the engineer approved, requested changes on, or rejected.
2. *What held up.* What of the original review reads well with 30+ days of hindsight — a specific catch, a specific approval that stood the test of landed code, a specific push-back that saved a later incident.
3. *What didn't hold up.* What, with hindsight, the engineer would have handled differently — an over-approval, an under-approval, a missed pattern. If the code downstream of the review has caused a bug, revert, follow-up ticket, or re-review, name it.

**How it is scored.** The reading is less about the review itself and more about the *change-of-mind*. Chapter 2 named the failure signature: a Day-90 self-review that reads identically to the original review ("I still agree with everything I said") is the signal the artifact did not do its job. Causes to check per Chapter 2 — most commonly a too-short gap for the engineer's shipping cadence.

**What it is grounded in.** [Brynjolfsson, Li, Raymond (NBER 31161)](https://www.nber.org/papers/w31161) found that the productivity gains from generative-AI assistance compounded unevenly across workers over time. The review-of-your-review surfaces the engineer's *own* trajectory — are their reviews getting sharper on agent-generated work, or are they drifting into over-approval as they get used to the tool? That trajectory is the fluency signal, and it is not visible from a cross-sectional stage pin.

The review-of-your-review also absorbs the specific risk Dell'Acqua et al. documented: top performers who used AI uncritically could lose ground. The self-review is the instrument for catching uncritical approval before it compounds into a review-quality regression.

### Composing the three artifacts into a fluency growth read

A single engineer's four-checkpoint artifact set (stage pin + three artifacts) is **not a dashboard**. It is a case study. The read happens at two levels:

**Per-engineer read at Day 90.** The manager and engineer walk the four artifacts together in the Day-90 1:1. The questions:

- Is the stage pin on the primary tool at least one stage higher than on Day 0?
- Does the Day-30 PR reflection show specific knowledge of what the tool does and doesn't do well on this team's code?
- Does the Day-60 pair-with-agent reflection show a developing map of what to delegate?
- Does the Day-90 self-review show a change-of-mind?

The graduation decision (Chapter 2) is the composite answer.

**Programme-level read at the quarter boundary.** The manager aggregates patterns across the cohort(s) that completed this quarter:

- Are Day-30 PRs landing by Day 30, or slipping? If slipping, which tools, which engineers' cohorts, which workflows?
- Are Day-60 reflections showing *shared* friction points — e.g. every engineer writing that the agent gets the ORM wrong — that suggest a workshop or rules-file update?
- Are Day-90 self-reviews showing *shared* review-quality drift — e.g. multiple engineers writing "I over-approved on test coverage changes" — that suggest a review-standard update (mod-103)?

The programme-level read is the one that feeds back into the next cohort's curriculum and into the mod-104 narrative. It is also the one the graduation-to-L45 decision reads (Chapter 8).

### Keeping the measurement honest: three scoring guardrails

- **The artifacts are not for performance management.** Chapter 2 of `mod-104` and Chapter 5 of `mod-101` named this restriction for productivity and fluency metrics respectively; the same applies here. If the three artifacts show up in merit review or promo packets, engineers will optimise the artifacts (longer reflections, safer PRs) and the measurement will die. The artifacts live in the mod-105 stage sheet and the manager's operational reading; they do not route to HR.
- **Vague reflections are a programme signal, not a learner signal.** Chapter 2 named this; worth repeating. If a cohort's reflections are uniformly vague, the problem is the prompt / scope / cohort-composition / mentor-pairing, not the engineers.
- **Honesty > polish.** Reflections that read like marketing copy for the tool are negative signals. Reflections that name specific failure modes — the tool pulled a stale doc, the agent went in circles, I accepted a change I now regret — are positive signals. Make this explicit at the Day-0 kickoff: the goal is calibration, not advocacy.

### Linking the artifacts across modules

Each of the three artifacts cross-links to other modules in this track, which is why the artifact definitions matter beyond mod-105:

- First-successful-PR-with-tool ↔ `mod-103` (review standards). The review that happened on the PR is itself the review-standard-under-AI in action. A cohort where Day-30 PR reviews are uniformly shallow is a signal the mod-103 review standard needs reinforcement.
- Pair-with-agent reflection ↔ `mod-106` (workflow redesign and agent delegation). The pair-with-agent reflections aggregated across the cohort are the richest evidence base for authoring the delegation contract and the AGENTS.md revisions in mod-106.
- Review-of-your-review ↔ `mod-107` (skill growth and anti-atrophy) and `mod-109` (incident response). Self-reviews that uncover a shared over-approval pattern are leading indicators for both the anti-atrophy curriculum in mod-107 and the fault-chain coverage in mod-109.

The artifacts are not isolated L&D deliverables; they are the connective tissue of the track.

### What this chapter is *not*

- **Not a competency framework.** SFIA, Pragmatic Institute, or vendor-issued "AI fluency levels" are competency frameworks. This chapter does not propose one. A competency framework is a longer-lived artifact than a team-manager-owned fluency measurement; if your organisation has one, cross-reference it, but do not try to replace it inside mod-105.
- **Not a certification programme.** The artifacts produce evidence; evidence is not a certificate. Chapter 1's Failure-C bootcamp-with-certificate pattern is specifically what this chapter rejects.
- **Not a LMS integration.** The artifacts live where your team's work lives — the PR, the engineer's folder in the team repo, the CoP pattern library. Trying to put them in a learning-management system corrupts them (the reflections drift toward LMS-formatting). Chapter 7 handles the L&D partnership without routing the artifacts through an LMS.

## Example: a Day-60 pair-with-agent reflection reading

Treat as calibration, not a template.

> **Reflection (engineer J.M., Day 54 of Cohort A, pair-with-Claude-Code on a migration task).**
>
> *The task.* Add a `soft_deleted_at` column to `orders` and `order_items`, backfill nulls appropriately, update the three queries in `orders/repository.go` to filter it out. Normally 3–4 hours for me.
>
> *The delegation.* I pointed Claude Code at `docs/db-conventions.md`, `migrations/`, and `orders/repository.go`. I told it to use the team's one-step migration pattern, to not rewrite the queries beyond adding the filter, and to stop if it needed to touch anything outside `orders/`. I did not tell it to run the test suite — I ran that myself at the end.
>
> *The handback.* Finished in 40 minutes. Produced a migration + the three query updates + a test. Did not touch anything outside the scope I set.
>
> *The intervention.* The migration name used a date format we don't use. I renamed it. The filter clause in one of the queries was added to a subquery instead of the outer query, which would have worked but reads worse — I rewrote. The test was comprehensive for the happy path but had no cleanup, which would have poisoned the next integration-test run — I added the cleanup block. I also noticed the agent did not read `docs/db-conventions.md` closely — the file has a sentence about preferring `TIMESTAMPTZ` and the migration used `TIMESTAMP`. I asked it to re-read and fix; it did.
>
> *The judgment.* I would delegate this *exact* shape again — small schema change, bounded repo scope, clear conventions file. For the next migration, I'd put the `TIMESTAMPTZ` convention into the Cursor rules file so the agent doesn't miss it (will file that as a pattern-library item). I would *not* delegate a cross-service migration or anything that touches the stored-procedure interface in `billing/` — the conventions there are implicit in the code and the agent won't find them. I'd also not delegate tests without explicitly asking for cleanup — "add a test" without that turned out to be a hidden failure mode here.

Specific, honest, change-of-mind-shaped, and immediately useful for the next cohort's workshop (the `TIMESTAMPTZ` rules-file pattern is a workshop topic) and the mod-104 narrative (concrete evidence that pair-with-agent work is ramping on the team).

## Summary

- Three artifacts, three jobs. **First-successful-PR-with-tool** (Day 30, real merged PR + two-paragraph reflection, grounded in Peng et al.). **Pair-with-agent reflection** (Day 60, one-page five-section delegation reflection, grounded in Dell'Acqua et al. + Bersin). **Review-of-your-review** (Day 90, half-page self-review of a 30+-day-old agent-PR review, grounded in Brynjolfsson-Li-Raymond).
- Not pass/fail. Scored by *specificity*, *honesty*, and (for the self-review) *change-of-mind*.
- Three scoring guardrails: artifacts are not for performance management; vague reflections are a programme signal; honesty > polish.
- Per-engineer read at Day 90 produces the graduation decision (Chapter 2); programme-level read at the quarter produces the feedback into next cohort's curriculum and into the mod-104 narrative.
- Each artifact cross-links across the track: PR + reflection ↔ mod-103; pair reflection ↔ mod-106; self-review ↔ mod-107 and mod-109.
- The chapter is *not* a competency framework, a certification, or an LMS integration.
- Exercise 03 produces the fluency-growth measurement artifact set operational for your team.
