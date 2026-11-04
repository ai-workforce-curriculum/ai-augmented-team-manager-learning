# Exercise 04 — The Commissioning Rubric for Eval Work

**Estimated effort:** 2 hours.

## Objective

Produce a **concrete, buildable commissioning brief** for an eval the team would benefit from today, plus a **commissioning rubric** you can reuse for future commissions. The brief must be executable by a peer `ai-risk-engineer` / `ai-eval-engineer` / senior IC without a follow-up meeting. The rubric is the general-purpose frame you will use for the next three briefs.

## Prerequisites

- Chapter 4 of this module.
- Chapter 5 of [`mod-101`](../../mod-101-ai-augmented-team-manager-position-and-contract/) (the manager-fluency bar).
- Exercises 01–03 of this module. The commissioning brief references the checklist, AGENTS.md, and standards-as-code stack as inputs — do not do this exercise before the previous three are at v0.1.
- Read, at a scan: Promptfoo quickstart (<https://www.promptfoo.dev/docs/intro>), LangSmith overview (<https://docs.smith.langchain.com/>), Inspect AI docs (<https://inspect.aisi.org.uk/>), and the G-Eval paper abstract (<https://arxiv.org/abs/2303.16634>). You do not need to implement anything in these tools; you need to know their shapes.

## Problem statement

Managers who skip the rubric and dive into writing "let's eval the agent" statements end up with harnesses that either (a) measure the wrong thing, (b) measure the right thing with the wrong judge, (c) produce a report nobody reads, or (d) all three. The rubric is the gating discipline.

You will author:

1. **A general-purpose commissioning rubric** — a short, reusable template with the ten-section shape from Chapter 4 (Decision, Scope, Shape, Dataset, Judge configuration, Pass / fail / regression thresholds, Tool choice, Owner and co-owner, Feedback loop, Review and sunset).
2. **A concrete commissioning brief** — the rubric filled in for a real eval your team would benefit from in the next quarter. Not a toy; a real workflow. Candidates: PR-description drafting, test-skeleton generation, ADR-first-draft generation, incident-summary drafting, SQL-query generation, customer-reply drafting, code-review-feedback-draft generation.
3. **A two-paragraph note on what the eval is *not*** — the risks and workflows explicitly out-of-scope for this commission. (This paragraph prevents scope-bleed in the harness build, and is where you also note any work that is more appropriately commissioned to `ai-risk-engineer` or `ai-eval-engineer`.)

## Steps

1. **Pick the workflow.** Choose one AI workflow your team runs or is about to roll out. Write one sentence describing it; one sentence describing what a "good output" from it looks like.
2. **Answer Q1 — what decision does this eval inform?** Write one sentence. If the sentence is "it will tell us how we are doing," reject it and try again. A decision has a binary or ordinal outcome tied to team action. ("Should this workflow go default-on next quarter?" / "Should we block merges to the agent config without this gate passing?" / "Are we within our pass bar on faithfulness for Q2?")
3. **Pick the eval shape.** Golden-task / LLM-as-judge (G-Eval) / regression / capability (Inspect AI). One primary shape. Note any secondary shape you think you will also need, but keep the brief focused on one.
4. **Define the dataset.** Where does it come from (team's actual history, curated by hand, synthetic, mixed)? Who curates? How many instances? What is the privacy / sensitivity posture — is any data in it something that needs scrubbing before it goes through a third-party judge? (See [`mod-110`](../../mod-110-ai-governance-and-policy-at-team-scope/).) How is the dataset version-controlled and how often does it refresh?
5. **If LLM-as-judge: configure the judge.** Which model (named — e.g., claude-opus-4-7, gpt-5-opus, etc.)? What is the judge rubric (the G-Eval-style structured form the judge fills in)? What is the calibration requirement — what sample size of human-rated instances do you require, and what is the minimum correlation (Spearman, kappa) you require to trust the judge?
6. **Set pass / fail / regression thresholds.** Specific numbers. "Mean judge score ≥ 4.0/5.0 on the full 50-item golden set; regression triggered on ≥ 0.2 drop between consecutive runs or on ≥ 10 pp of items dropping category." Prefer specific over vague; prefer two or three thresholds over one.
7. **Pick the tool.** Promptfoo / LangSmith / Inspect AI / other. Justify in one line — "Promptfoo's CLI + CI integration fits our existing GitHub Actions pipeline"; "LangSmith's trace view is load-bearing because the judge calibration requires inspecting the retrieved context on failing items"; "Inspect AI's structured eval shape fits the OWASP LLM01 capability claim we want to make."
8. **Name the owner and co-owner.** The owner builds the harness. The co-owner curates the dataset and does the human-rated calibration pass. One is likely your `ai-risk-engineer` or `ai-eval-engineer` peer; the other is often a senior IC on your team. If the owner is you, go back to Chapter 7 — this is almost always a delegation failure.
9. **Design the feedback loop.** Where does the report land (channel, dashboard, Q-review slide)? Who reads it? What threshold triggers what action (rollback / block / ADR / escalate)? Who authorises the action?
10. **Define review and sunset.** When do you re-review the commission? What ends the eval (e.g., "when the workflow has been default-on without a regression gate firing for two quarters, this eval sunsets to quarterly cadence").
11. **Write the two-paragraph "what this is not" note.** Which risks / workflows / failure modes are *explicitly out-of-scope* for this commission. Which are better commissioned to `ai-risk-engineer` or `ai-eval-engineer` (see Chapter 7). Which are intentionally deferred to a future commission.
12. **Review the brief with the person who will build it.** Ten minutes. Confirm they can execute without a follow-up meeting. Update any ambiguity.

## Starter guidance

- The brief is not a design doc. Ten short sections, one or two pages total. If it is longer, you are doing the builder's job for them — stop.
- A specific-but-wrong threshold is better than a vague-but-right one. The specific threshold reveals the mismatch quickly; the vague one hides it indefinitely.
- Calibration against human judgement is the single most skipped step in LLM-as-judge commissioning. Require it. The G-Eval paper reports Spearman correlations with human raters as part of the method; the brief should require your harness owner to report theirs.
- Judge choice matters. A judge that is the same family or same size as the model being evaluated introduces bias. Use a different-family or larger judge where feasible, and note the caveat in the brief.
- A regression threshold that triggers on day one of a new model version is doing its job — that is what the gate exists for. Teams often panic the first time a regression fires and relax the threshold. Resist, and treat the first fire as a validation of the gate, not an invitation to recalibrate.
- Not every workflow deserves an eval. The "when the eval would exist to inform no team decision" test is a rejection, not a to-do.

## Acceptance criteria

The deliverable is complete when:

- A general-purpose commissioning rubric exists with all ten sections from Chapter 4.
- A concrete commissioning brief for one real workflow has been filled in using the rubric, with every section containing a specific answer (no "TBD"s).
- The decision the eval informs is one sentence, tied to team action.
- Pass / fail / regression thresholds are specific numbers with specific triggers.
- The owner and co-owner are named human peers (not "the team"); neither is you unless Chapter 7's conditions are met.
- A feedback loop is designed — delivery location, reader, trigger, authoriser.
- A two-paragraph "what this is not" note is attached, with at least one risk or workflow explicitly deferred to a different commissioning owner.
- The brief has been reviewed by (or at minimum shared with) the proposed harness builder, with their feedback either reflected or acknowledged in a change-log entry.
- The brief carries a title, date, authorship, and a change log.

## Stretch goals

- **Two more briefs.** Use the rubric to fill in two additional briefs for different workflows. Compare the three: do the pass thresholds feel comparable? Does the feedback loop converge on a single shared channel? The exercise teaches rubric reuse.
- **Judge calibration pre-flight.** Before the full commission runs, do a 10-item hand-rated calibration pass yourself. Score each on the proposed rubric; have the judge model score the same 10. Compute Spearman. If it is below the threshold you required of the harness owner, reword the rubric and try again. This is a fluency exercise, not a shortcut.
- **Dataset-drift plan.** Document how the golden-task dataset refreshes over time. A dataset that is frozen for a year silently becomes a lagging indicator. Pair with [`mod-104`](../../mod-104-productivity-measurement-and-ai-roi/) if the eval feeds the ROI narrative.
- **OWASP crosswalk row.** For your chosen workflow, identify which OWASP LLM Top 10 risk(s) a complementary capability eval would address. Draft a one-paragraph companion commission for `ai-risk-engineer` with the Chapter 7 boundary respected.
- **Governance roll-up.** Draft the one-paragraph summary of this commission that would appear in your team's quarterly governance snippet (`mod-110`). Note: an eval the team cannot describe to a governance partner in one paragraph is probably not well-scoped.
- **Sunset dry-run.** Ask yourself: if the next three runs of this eval all pass cleanly, what change would you make to the commission? If the answer is "none," the eval has become theatre and you need a reduced cadence or a rotation to a different workflow.
