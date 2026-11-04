# Chapter 4 — Dell'Acqua et al. and the Deference Channel

> *Of the three research anchors this module reads, Dell'Acqua et al. is the one that names the specific deskill mechanism. On the inside-frontier work the AI is good at, humans + AI outperform. On the outside-frontier work the AI is subtly wrong at, humans + AI underperform the control. The second finding is the one you have to design around.*

## Motivation

[Dell'Acqua et al., *Navigating the Jagged Technological Frontier: Field Experimental Evidence of the Effects of AI on Knowledge Worker Productivity and Quality* (HBS WP 24-013, September 2023)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321) is the research anchor mod-106 Chapter 1 reads for the *routing* decision. mod-107 reads the same paper for a different finding — the one that fewer summaries carry — about the human-behaviour change that produces the outside-frontier failure. The paper's authors call the failing pattern the *uncritical consumer* and the *falling asleep at the wheel* effect. This chapter is the manager-fluency read of that finding and its translation into the third team-level policy move in this module.

If Chapter 2 asked *"what do junior ICs no longer learn when AI carries their first drafts?"* and Chapter 3 asked *"what do we lose on promotion signal when the output compresses?"*, Chapter 4 asks the sharpest question: *"what does the IC do when faced with a problem the AI is subtly wrong about, and what is the manager's intervention?"* The answer the paper gives is uncomfortable: on average, the IC defers to the AI and ships the wrong output. The intervention is Chapter 5's deliberate-practice carve-outs.

## Core concepts

### Reading the paper at manager-fluency (for the deskill finding)

The study was run with 758 consultants at Boston Consulting Group. Participants were randomised into three conditions — control (no AI), AI-only (GPT-4 access), and AI + prompt-engineering overview — and asked to complete a battery of 18 realistic consulting tasks. Some tasks were *inside* GPT-4's frontier — summarisation, structured-content production, synthesis — and some were *outside* the frontier — judgement grounded in numeric data where the model's confident-looking output was subtly wrong, strategic recommendations on bespoke contexts the model had no training signal on.

mod-106 Chapter 1 reads the two findings about the frontier itself: inside-frontier AI access improved speed, completion, and quality; outside-frontier AI access hurt correctness by ~19 percentage points. This chapter reads a separate finding the authors foreground and the posting language rarely cites.

**Finding — the uncritical consumer pattern.** Among AI-augmented consultants, a subset interacted with the AI as *uncritical consumers*: they prompted the model, received an answer, and shipped the answer without applying significant judgement. On outside-frontier tasks, the uncritical consumers' output was both (a) more confident-seeming and (b) more often wrong than the control group's output. The authors describe the pattern as *falling asleep at the wheel* — participants' attention disengaged after the AI produced plausibly-structured output.

Two patterns of effective collaboration — *centaurs* (divide work; route sub-tasks to AI based on fit; keep judgement on the human side) and *cyborgs* (interleave with AI turn-by-turn; edit, redirect, and recover from AI errors) — are distinguished by the behaviour of *applying judgement*, not by the tool. The uncritical consumer pattern is the failure mode; the centaur and cyborg patterns are the successful adaptations.

**The quality finding, stated plainly.** On outside-frontier tasks, AI-augmented consultants were ~19 percentage points less likely to produce correct answers than control-group consultants. This is the number this module cares about most. It is the empirical measurement of the deference-and-deskill risk.

### Why this is the sharpest finding of the three

Compared to Brynjolfsson's growth-path channel (slow-moving; hard to measure without a multi-year longitudinal study) and Noy & Zhang's differentiation channel (compresses signal rather than degrading output), Dell'Acqua's deference channel is an immediate, measurable, *negative* effect: AI-augmented workers on the wrong kind of task produce worse output than they would have without AI. It is the only one of the three findings in which the direct consequence is a *degradation* in work quality, not a lag or compression effect.

This is why mod-107 treats it as the load-bearing anchor for the carve-out design. The manager who only reads Brynjolfsson and Noy & Zhang might reasonably conclude that AI makes the team unambiguously better in the near term (lifts the bottom, compresses output in a managerially-awkward but net-positive way) and worry mostly about multi-year effects. Reading Dell'Acqua, the near-term concern sharpens: the degradation is present *now*, on *outside-frontier tasks that look like normal work*, and the only intervention that reliably prevents it is a human-judgement mechanism that the uncritical-consumer pattern bypasses.

### What the finding does *not* say

- **It does not say AI is bad on outside-frontier tasks in all conditions.** Centaurs and cyborgs on outside-frontier tasks did well. The failure mode is *uncritical consumption*, not AI-plus-human in general. The intervention is behavioural (human stays in the loop and applies judgement), not categorical (never use AI here).
- **It does not say which tasks are outside the frontier for *your* team's domain.** The frontier is domain- and generation-specific. Generalising BCG's consulting-task frontier placements to a platform-engineering team is an extrapolation. mod-106 Chapter 2's routing matrix is the operational response to the domain-specificity; this chapter grounds why the routing matrix needs to exist at all.
- **It does not predict a permanent frontier.** The frontier moves as models improve. A task outside the frontier in 2023 may be inside the frontier in 2026; a task inside the frontier in one model generation may be outside the frontier for a different-shaped task. The routing matrix is a *living artifact* with explicit re-check dates (mod-106 Exercise 01); the carve-out schedule (Chapter 5) is also re-checked quarterly.
- **It does not ask managers to detect the uncritical-consumer pattern directly in output.** The paper's identification depends on a randomised control group — you cannot see the "falling asleep at the wheel" effect in production output without an unassisted baseline. This is why Chapter 5's AI-off carve-out exists: it *creates* the unassisted baseline so the manager has signal.

### Translating the finding into a team-level policy move

**Policy move 1 — the AI-off carve-out is a mandatory periodic artifact, not a stretch.** At least once per quarter, each IC produces one *named* artifact without AI assistance. The artifact is pre-chosen (not retrofitted), low-stakes relative to critical production work (not a release-day PR), and visible to a reviewer whose job is to evaluate *not* the artifact's polish but *whether the IC's judgement muscle is intact on the task-shape*. Chapter 5 is the operational detail; Exercise 02 produces the schedule.

**Policy move 2 — the review standard adds a judgement question.** The team's existing review standard (mod-103) asks correctness and quality questions. Chapter 5's amendment adds one judgement-weighted question to the review, applied at the reviewer's discretion where it applies: *"If you were writing this from scratch, would you have made the decisions this artifact makes?"* The question is asked *before* the reviewer looks at the diff, so the artifact's appearance does not anchor the judgement. The purpose is to surface the cases in which the output *looks fine* but the underlying decision is not one the reviewer would have endorsed.

**Policy move 3 — paired-review rotations on the outside-frontier task-types.** For the task-types the routing matrix (mod-106 Exercise 01) has routed to *AI + human pair (variant A: AI drafts, human verifies)*, Chapter 5 overlays a paired-review rotation: the review is done by *two* reviewers — one senior IC and one junior IC — who discuss the decision the artifact makes before signing off. The paired-review is not for *every* review; it is for the outside-frontier task-types where the deference risk is highest. Exercise 02 schedules the rotation.

### The hard case: the IC who sincerely believes the AI's output is correct

One realistic edge case to walk through, because it is the one managers encounter most. An IC produces an artifact. The reviewer asks the judgement question. The IC answers: *"yes, I would have written it this way; I checked the AI's suggestion carefully, and I agree with it."* The IC is sincere. The AI's output on the particular case is actually subtly wrong, in a way the IC cannot see because the IC's judgement muscle has not been built on this task-shape.

The failure mode of the review is to accept the IC's sincere endorsement as evidence that judgement was applied. It is not. The sincere endorsement is evidence that *review-the-AI's-output* was applied; it is not evidence that *re-derive-the-decision-from-scratch* was applied. The two produce different outputs in exactly the cases the paper flags.

The reviewer's response in this case is to ask *"which parts of this did you actually produce yourself, and which parts did you accept?"* and then to look specifically at the accepted parts for whether the IC can defend them without pointing at the AI's suggestion. This is a cognitively costly review move. Chapter 5 is explicit: you cannot do it on every review. You do it on the outside-frontier task-types, on a rotation, as a specific deliberate-practice intervention. Exercise 02 schedules which reviews get this treatment.

### Common mistakes when citing this paper

- **Citing the 19-percentage-point result as "AI makes people worse."** It is a narrower finding than that. AI makes uncritical consumers worse on outside-frontier tasks specifically. The right cite is to the behavioural pattern, not to an all-things-equal degradation.
- **Citing centaurs and cyborgs as patterns to adopt without a mechanism to check.** The paper distinguishes patterns by behaviour; the manager's work is to create the mechanism that *verifies* which pattern an IC is actually in. The pattern is not self-reported; it is observed in the review.
- **Treating the frontier as self-evident.** The frontier is domain-specific and generation-specific. mod-106 Chapter 2's routing matrix is where the frontier gets named for *your team's work*; do not skip that step.
- **Reading the paper only for the routing finding and missing the deference finding.** The routing finding is the mod-106 anchor. The deference finding is the mod-107 anchor. Both come from the same paper; reading it for only one is leaving signal on the table.

## Example: what the judgement question looks like in a review conversation

Composite example; treat as calibration, not a case study.

> **Reviewer (pre-reading the PR):** *"Before I look at the diff — I want to understand the decision. You chose to handle the edge case by routing through the existing retry logic rather than adding a bespoke timeout. Walk me through why."*
>
> **IC:** *"I asked Claude Code and it suggested the retry route — it mentioned the pattern was already in the codebase and said we should prefer reuse."*
>
> **Reviewer:** *"That's what the tool said. What's your reason?"*
>
> **IC (pauses):** *"Actually — I think the retry logic retries on a wider set of errors than we want here. If I'd written it without the tool I'd probably have added the timeout — the reuse argument is weaker in this specific case because the failure modes aren't the same shape."*
>
> **Reviewer:** *"Can you rewrite the explanation in the PR description to say that, and then we'll decide whether to change the code? The PR might be right as it is — I want to check the reasoning, not necessarily the code."*

The conversation is not an interrogation. It is a review pattern that surfaces whether judgement was applied *before* the reviewer looks at the diff and gets anchored. It costs ~90 seconds. Chapter 5's carve-out schedule is where this review pattern gets slotted into the week on the outside-frontier task-types.

## Summary

- [Dell'Acqua et al. (2023)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321) is a 758-participant RCT at BCG; inside-frontier tasks saw AI access improve speed, completion, and quality; outside-frontier tasks saw AI access degrade correctness by ~19 percentage points.
- **The load-bearing finding for mod-107:** the *uncritical consumer* pattern — IC accepts AI output without judgement, fails on outside-frontier tasks — is the direct deskill mechanism the module's interventions respond to.
- **Why this finding is the sharpest of the three:** the degradation is immediate, measurable, and negative, not lagged or compressed. Managers who read only Brynjolfsson and Noy & Zhang under-weight the near-term risk.
- **Three team-level policy moves:** (a) make the AI-off carve-out a mandatory periodic artifact, (b) add the judgement question to the review standard, applied on outside-frontier task-types, (c) paired-review rotations on outside-frontier task-types to surface deference in the review conversation.
- **The hard case:** the sincerely-endorsed uncritical-consumer output. The reviewer's response is a specific re-derive-from-scratch probe, not more diff-reading. This is cognitively costly and must be rotated; Chapter 5 is the schedule.
- **Cite responsibly:** quote the behavioural pattern (uncritical consumer vs. centaur / cyborg), not an all-things-equal degradation; name the frontier as domain- and generation-specific; link the paper to both mod-106's routing matrix (routing finding) and mod-107's carve-outs (deference finding) — they are two reads of the same study.
