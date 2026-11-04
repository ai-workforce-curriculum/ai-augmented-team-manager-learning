# Chapter 3 — Noy & Zhang and the Differentiation Channel

> *When the gap between the best and the worst writer on your team shrinks by half, every signal you were using to decide who to promote — output volume, output polish, speed — is quieter than it was. The career-ladder work in Chapter 6 is the direct response to this. Noy & Zhang's paper is why the response is not optional.*

## Motivation

[Noy & Zhang, *Experimental evidence on the productivity effects of generative artificial intelligence* (Science, July 2023, vol. 381)](https://www.science.org/doi/10.1126/science.adh2586) is a randomised controlled experiment on mid-level professional writing tasks — business memos, emails, short reports — with 453 college-educated professionals (marketers, consultants, HR specialists, grant writers). It is the cleanest experimental identification of the productivity effect of generative AI on realistic knowledge-work writing tasks, and its findings on *dispersion* and *inequality* of output are the most directly load-bearing for how your team's promotion ladder works.

This chapter reads Noy & Zhang at manager-fluency and translates the findings into the second of the three team-level policy moves in the module. The Brynjolfsson chapter asked how junior-IC growth changes; this chapter asks how the *measurement signal* the manager uses to tell ICs apart changes.

## Core concepts

### Reading the paper at manager-fluency

The experiment ran in two stages. Participants were asked to complete two 20–30-minute writing tasks selected to be representative of their day-to-day work. Between the first and second task, roughly half the participants were given access to ChatGPT and a brief instruction on its use; the other half were not. Outputs were graded by experienced evaluators in a specific profession on a 1–7 quality scale, double-blind to the treatment condition. The paper reports three load-bearing results.

**Finding 1 — productivity.** Participants with ChatGPT access completed the writing task in substantially less time than the control group — the time-reduction point estimate is roughly **40%** (the paper reports ~37% depending on the specification). The time saving holds across professions and task types.

**Finding 2 — quality.** Output quality rose on average, with the ChatGPT-treated group's outputs rated roughly **0.4 standard deviations higher** on the 1–7 scale than the control group. Grader inter-rater agreement is within the normal range for professional evaluations. The quality lift is smaller than the time saving but is clearly positive.

**Finding 3 — dispersion, the load-bearing finding for mod-107.** The *gap* between high-skilled and low-skilled participants (where skill is measured by Task-1 quality, pre-treatment) *narrows* under AI access. The lower-skilled participants benefit more than the higher-skilled participants — on quality, not just time. The paper reports the compression as a direct reduction in the standard deviation of output quality in the treatment group relative to the control.

**Finding 4 — adoption dynamics.** Participants reported increased job satisfaction and self-efficacy, and the vast majority reported intent to continue using the tool. The finding is consistent with Brynjolfsson's workforce-dynamics channel.

### Why Finding 3 is the one that reshapes your ladder

A team manager's primary promotion signal, under traditional conditions, is *differentiation*. You compare IC A's output against IC B's output — the artifacts they produce, the decisions they make, the mentorship they provide — and the comparison tells you who is operating at the next level.

Under AI augmentation, Finding 3 says the *output* side of the comparison is less diagnostic. The artifacts converge; the bottom lifts more than the top; the dispersion narrows. The components of the promotion case that look at *output quality and volume* are now compressed signal.

This does not mean promotion becomes impossible. It means the *where the signal lives* moves from output to judgement, from throughput to decisions. Chapter 6 operationalises this as a ladder update; this chapter establishes the empirical grounding. If a reviewer disputes the ladder change on *"why can't we just read the PRs?"*, the sentence to have ready is: *Noy & Zhang (Science 2023) show that AI-mediated writing-task output compresses in quality dispersion — the output you were reading used to differentiate; after AI, it differentiates less, and the ladder has to look at what still does.*

### What the finding does *not* say

- **It does not say output is now useless as signal.** The compression is a reduction in dispersion, not an erasure. A junior IC's output on an outside-frontier problem (Dell'Acqua, Chapter 4) is still a high-signal artifact. A senior IC's teaching work — mentoring, reviewing, architecting — is not in the compressed region because the AI does not do it. You still read PRs; you *also* read other things, and you weight the composite differently.
- **It does not say the compression is uniform across tasks.** Noy & Zhang's tasks are short-to-medium-length writing tasks. On long-form, context-heavy, judgement-dense work, the compression is likely smaller; on short, template-y, lower-context work, likely larger. Chapter 4's jagged-frontier framing is the right companion read — the compression concentrates on the inside-frontier slice.
- **It does not predict a permanent compression.** The data is from mid-2023 generative-AI capability. If the top of the skill distribution learns to use the tool more skilfully than the bottom (the *cyborg* vs. *uncritical consumer* pattern from Dell'Acqua), the dispersion could re-open at the *skilled-use* level even while compressed on raw output. The ladder update should be stated at that level — *judgement of use of the tool*, not *output produced through the tool*.
- **It does not generalise to work the tool does not touch.** Grant writing, business memos, and HR emails are in the paper's sample. If your team's output is heavily domain-specific-code, deep-infra configuration, or incident narrative — all areas where off-the-shelf generative AI is weaker — the compression is likely milder. Cite the pattern with the domain caveat.

### Translating Finding 3 into a team-level policy move

**Policy move 1 — the promotion packet changes shape.** Before AI, a promotion packet leads with representative artifacts: *"here is the design doc X led; here are the three PRs that best show the IC's level."* After AI, the same packet needs to lead with *judgement moves*: *"here are the three decisions X made that the AI would have gotten wrong; here is the mentorship work X did that lifted junior IC B's capacity; here is the review catch X made on PR Y that the diff looked fine on."* Chapter 6 defines the structure of the AI-augmented promotion packet; Exercise 03 produces the draft.

**Policy move 2 — the performance-review rubric weights change.** The rubric your team uses in performance reviews — whichever form (impact + behaviour, 9-box, levels-and-ladders) — needs re-weighting. The *output* axis compresses; the *judgement* and *scope* axes do not. Weighting the output axis the same as before produces promotion decisions that reward AI usage, not IC capability. This is where mod-108's performance-review redesign and mod-107's ladder design meet.

**Policy move 3 — the top-of-distribution ICs need a different growth narrative.** Finding 3 says the top-tier benefits least on raw output. If your senior ICs look at their own measured output year-over-year and see a flat or modest lift while the junior ICs look like they are flying, the resulting narrative risks demoralising the top of the team. The *right* narrative — grounded in the paper — is that the top-tier's work has moved *away from the measured output* into the judgement, review, and teaching layers that the AI cannot do, and those layers need to be surfaced explicitly in 1:1s, retro contributions, and promotion cases. Chapter 7's 1:1 prompts are where this surfaces; Chapter 6's ladder update is where it institutionalises.

### The cross-read with Brynjolfsson

Brynjolfsson (customer-support deployment, Chapter 2) and Noy & Zhang (controlled writing-tasks experiment, this chapter) agree on one pattern — gains concentrate at the bottom of the skill distribution — from two different research designs. The agreement is important: natural-experiment plus RCT, different tasks, different populations, same qualitative finding. It is one of the more replicated findings in the empirical AI-at-work literature as of the 2024–2026 window and is defensible to cite as *a pattern*, not *one study's result*.

The disagreement is on *what it means for senior ICs*. Brynjolfsson says senior agents see little gain (the AI does not improve what they already do well). Noy & Zhang says higher-skilled writers also benefit on quality — just less than lower-skilled writers — and reduce their time spent. The right reading for a team manager: senior ICs *do* benefit, mostly on the *time-to-first-draft* axis rather than the quality axis, which frees capacity for the judgement work. Chapter 5's deliberate-practice carve-outs direct the freed capacity; Chapter 6's ladder update rewards the directed capacity.

### Common mistakes when citing this paper

- **Citing the 40% time reduction as a direct engineering-productivity number.** The study is on mid-length professional writing. Engineering is adjacent but distinct; cite the shape, not the percentage.
- **Citing the compression as if it closes the skill gap permanently.** The compression is of *measured output under this generation of the tool*. It is a signal about where to look, not a prediction about where the distribution will land in 2028.
- **Using the quality lift to argue "AI makes everyone better."** The *average* lifts; the *dispersion* narrows. The two are different findings with different managerial implications. Argue the one you mean.
- **Treating the compression as a reason to flatten the ladder.** The reverse: the compression means the ladder's *rungs* need to be re-defined around judgement, so that the compression does not end up compressing *promotions* too. Chapter 6 is the detail.

## Example: a promotion-packet rewrite grounded in Finding 3

A platform-engineering manager rewrites the standard promotion-packet template. Before:

> *Section 2: Representative output. Three PRs or artifacts that best demonstrate the IC's current level. Reviewer: evaluate quality, scope, and complexity.*

After, citing Finding 3 as the rationale:

> *Section 2: Representative output and representative judgement moves. **2a**: Three PRs or artifacts, each annotated by the IC with two sentences: "what I decided the AI could draft" and "what I decided to write myself." Reviewer evaluates the decision, not only the artifact. **2b**: Two narratable judgement moves — a review catch on another IC's PR where the diff looked clean, a push-back on a design suggestion from a stakeholder, or a redirect of an AI-generated plan. Reviewer evaluates the clarity and correctness of the judgement.*

The rewrite does not remove output from the packet. It *adds a layer* that is specifically designed to surface the signal Noy & Zhang's finding predicts the pure-output section no longer carries alone. Exercise 03 produces this re-write and the version-controlled ladder document that governs it.

## Summary

- [Noy & Zhang (Science 2023)](https://www.science.org/doi/10.1126/science.adh2586) is an RCT of generative AI on realistic professional writing tasks with 453 college-educated participants.
- **Three findings:** ~40% time reduction on average, ~0.4 SD quality lift on average, and — the load-bearing one for mod-107 — **compression of output-quality dispersion** such that lower-skilled participants benefit more than higher-skilled participants.
- **Why the compression matters:** promotion signal based on output volume and polish stops differentiating. The ladder has to look at what still does — judgement, review, mentorship, scope.
- **Three team-level policy moves:** (a) rewrite the promotion-packet template to include judgement moves alongside representative artifacts, (b) re-weight the performance-review rubric away from output axis toward judgement and scope, (c) give top-of-distribution ICs an explicit narrative for where their work has moved.
- **The cross-read with Brynjolfsson:** both studies agree on the bottom-of-distribution-benefits-more pattern across two research designs; this is one of the more replicated findings in the 2023–2026 literature.
- **Cite responsibly:** quote the dispersion compression, not the time-saving percentage, when the audience is a hiring or promotion committee; name the generation-of-tool and tasks-of-study caveats; distinguish *average lift* from *dispersion compression* explicitly.
