# Chapter 6 — The Career-Development Ladder Under AI Augmentation

> *A promotion packet that reads "shipped 40% more PRs than the prior level, used AI effectively" is not a promotion case. It is a description of AI's productivity effect. The ladder you author in this chapter reads the IC's judgement, scope, and leverage — the parts of their work AI does not do for them — and promotes on that.*

## Motivation

Noy & Zhang (Chapter 3) showed generative AI compresses the dispersion of measured output. Brynjolfsson (Chapter 2) showed productivity gains concentrate at lower tenure. If a team manager runs the previous career ladder unchanged, three things happen over 12–24 months: junior ICs look ready for promotion earlier than their judgement warrants, senior ICs' output looks flat relative to the team, and the promotion signal the committee uses to differentiate at level transitions becomes quieter.

This chapter is the ladder update. It is not a rewrite of levels or compensation bands — the ladder's *rungs* stay where they are. The *rubric* at each rung changes shape to weight the parts of IC work that AI does not do for them. Exercise 03 produces the updated ladder; Exercise 05 produces the refreshed IDP template that operationalises it in 1:1s.

mod-108's performance-review and promotion-case authoring work uses the ladder authored here as its standard. The division is: mod-107 writes the ladder; mod-108 runs the promotion case against it.

## Core concepts

### What stays, what changes

Your team's existing ladder has three load-bearing components: levels, level descriptors (the "staff engineer does X" paragraph), and a rubric (the axes on which an IC is assessed — impact, scope, craft, leadership, etc.). The mod-107 update:

- **Levels and compensation bands stay as-is.** Ladder design at that scope is HR / compensation-calibration work, not mod-107 work.
- **Level descriptors get a lens shift.** Each descriptor gains an explicit *judgement axis* alongside the existing *output axis*. The output axis is still present; it is no longer the sole differentiator.
- **The rubric adds or re-weights three specific axes.** Judgement under AI augmentation. Mentorship of judgement. Review craft on AI-assisted work. The three are the parts of IC work the research anchors predict will remain diagnostic.

If your team has no written ladder, the mod-107 update is premature — write the ladder first (`mod-108` or your HR partner's template is the starting point) and apply the update to it. The exercises assume the ladder exists.

### The three new axes, named

**Axis A — judgement under AI augmentation.** Can the IC tell when the AI's suggestion is wrong, make the alternative call, and defend it? The axis is scaled with level: a junior IC's bar is *"catches obvious wrong AI suggestions when flagged by review"*; a senior IC's bar is *"predicts where the AI will be wrong in advance, routes around it, and leaves a trail of reasoning that another IC can learn from"*; a staff IC's bar is *"sets the team's frontier placement on new task-shapes — decides which routing decisions the matrix should make"*. The axis maps directly to Dell'Acqua's centaur / cyborg distinction (Chapter 4).

**Axis B — mentorship of judgement.** Does the IC build the judgement capacity of other ICs on the team? Scaled: junior IC — *"shares at least one decision-vs-AI story per quarter in retros"*; senior IC — *"pairs with a junior IC on an outside-frontier task-type and the junior IC's work on that task-type improves"*; staff IC — *"designs and leads the team's deliberate-practice carve-out (Chapter 5) and the retro mechanism feeds into the next quarter"*. This axis is where Noy & Zhang's differentiation finding (Chapter 3) finds its promotion signal — senior ICs' leverage shows up in other ICs' growth curves, not in their own output.

**Axis C — review craft on AI-assisted work.** Can the IC run the judgement-weighted review pass (Chapter 5) well? Scaled: junior IC — *"applies the review checklist including the judgement question when assigned"*; senior IC — *"runs the paired-review conversation with a junior IC and names at least one decision-vs-AI learning per rotation"*; staff IC — *"reshapes the review standard itself when the retro surfaces a gap — the mod-103 standard is version-controlled; staff ICs edit it"*. This axis is where the deference channel's intervention lives on the ladder.

### What a promotion packet looks like after the update

The before/after structure of a promotion packet, specifically for a level transition where judgement is the differentiator (e.g., senior → staff on an engineering team):

**Before (pre-AI-augmentation packet):**

- Section 1: Impact summary (the IC's contributions to the team's goals this performance cycle).
- Section 2: Representative artifacts (three design docs or PRs that show the level).
- Section 3: Leadership and mentorship (what the IC did beyond their own work).
- Section 4: Peer feedback (quotes from peers and reviewers).

**After (AI-augmented packet):**

- Section 1: Impact summary (unchanged structure, but impact is now measured in terms of *decisions*, not throughput — *"led the decision to route schema migrations through the human-reviewed path; avoided one incident caught at review time"* rather than *"shipped 25 PRs"*).
- Section 2a: Representative artifacts, with the IC's annotation on *"what I decided the AI could draft, what I decided to write myself, and why."* The reviewer evaluates the decision, not only the artifact.
- Section 2b: Three narratable judgement moves — a review catch another reviewer missed, a push-back on a stakeholder's AI-generated plan, a redirect of a routing-matrix classification. Grounded in Dell'Acqua's centaur / cyborg distinction; the moves demonstrate the IC's judgement has been active, not deferred.
- Section 3: Mentorship of judgement specifically — not generic mentorship. Named ICs whose judgement capacity grew under the IC's pairing. Chapter 5's paired-review rotation produces the evidence.
- Section 4: Peer feedback, with one specific prompt added to the standard feedback form: *"name a decision this IC made that you would not have expected from someone at the prior level."*

The *after* packet is not longer than the *before* packet. It is structured to surface the signal the paper-grounded axes predict will still differentiate.

### Where this hits compensation calibration

Compensation calibration is HR / exec work and is out of scope for this track beyond the handoff. Two load-bearing points for the manager:

- **The compensation bands do not shift under this update.** The ladder's rung heights are the same; the rubric at each rung changes. A senior IC does not get paid differently because of the mod-107 update; the committee is simply evaluating whether they are a senior IC on a sharper set of criteria.
- **The manager's advocacy in calibration meetings changes shape.** When another manager compares two ICs' output volumes in a calibration discussion, the mod-107-literate manager is prepared to say: *"compare on Axis A and Axis B, not on volume — volume compresses under AI, as Noy & Zhang's work documents."* The citation is in your pocket; use it when the calibration debate drifts to volume.

### How the ladder prevents three failure modes

**Failure mode 1 — the fast-shipping junior IC promoted too early.** Under the old ladder, a junior IC who ships at 1.3× the prior level's throughput looks promotion-ready. Under the updated ladder, the question is whether their Axis A (judgement) has grown to match the output. If the IC has not yet made a *narratable* judgement move — not yet caught an AI-wrong decision in review, not yet pushed back on an AI suggestion in a design discussion — they are not ready, regardless of throughput. The ladder gives the manager a specific, defensible conversation to have in the 1:1 that pushes back on the ambition without being dismissive.

**Failure mode 2 — the senior IC who looks flat.** Under the old ladder, a senior IC whose throughput looks similar to the prior year appears to be stagnating. Under the updated ladder, the question is whether their Axis B (mentorship of judgement) has grown. If a junior IC who paired with them is now visibly running the judgement move independently, the senior's leverage has actually *increased*; the leverage just lives in another IC's growth curve. The ladder makes this visible.

**Failure mode 3 — the staff IC whose scope you cannot name.** Staff-level work has always been hard to assess because it is diffuse by nature. Under AI augmentation, the diffusion gets worse — staff ICs' contribution frequently comes through shaping the team's AI-use decisions, the routing matrix updates, the review-standard amendments. The ladder names these as Axis C (review craft on AI-assisted work) at the staff tier. The staff IC's work on the mod-103 review standard, on the mod-106 routing matrix, on the mod-107 carve-outs schedule — these are not "besides their day job." They are the day job.

### What the ladder is *not*

- **Not a replacement for level descriptors your HR or exec partner has standardised.** If your organisation runs a company-wide ladder, the update is an *amendment* that lives in your team-scope ladder document or your team's one-pager appendix to the company ladder. Compose, do not fork.
- **Not a scorecard.** The axes are not numerical. The judgement axis in particular does not reduce to a checklist count. The rubric is used to shape the conversation, not to generate a score the IC is above or below.
- **Not an anti-AI ladder.** Promoting on judgement is not promoting on *not using AI*. The axes reward ICs who use AI well — centaur / cyborg patterns — and are explicit about the fact that uncritical-consumer use does not clear the bar.
- **Not a universal ladder.** The specific wording of Axes A/B/C in this chapter is suggestive. Your team's ladder authors the wording in context. Exercise 03 produces the version that sticks for your team.

### Common failure modes in authoring the ladder

- **Adding six new axes.** The research supports three. Adding more dilutes the signal and overwhelms the promotion committee.
- **Making the judgement axis so stringent that nobody clears it.** The axis is scaled with level — the junior IC's bar is accessible. The staff IC's bar is aspirational by design. A ladder where no junior IC ever clears Axis A is not calibrated.
- **Collapsing Axes A, B, and C into one "AI judgement" axis.** The three measure different things on different levers. Collapsing them hides the mentorship and review-craft signals, which are the parts that most differentiate senior and staff work.
- **Authoring the ladder in private and launching it as a decree.** The ladder is more legitimate if the team saw it being drafted. One peer-review round with the senior ICs on the team catches tone and scope mistakes before they are shipped.
- **Deferring the update indefinitely.** The ladder update is awkward; it is easier to write the carve-out schedule and leave the ladder for next quarter. The next quarter never comes. Write the ladder in the quarter you write the carve-outs, even if only v0.1.

## Example: a level-descriptor amendment, before and after

Composite example; treat as calibration, not a template.

**Before (senior engineer, pre-AI-augmentation):**

> *A senior engineer owns features and systems end-to-end, makes technical decisions that trade off correctness, delivery speed, and maintainability, mentors junior engineers, and contributes to team technical direction.*

**After (senior engineer, AI-augmented):**

> *A senior engineer owns features and systems end-to-end, makes technical decisions that trade off correctness, delivery speed, and maintainability, mentors junior engineers, and contributes to team technical direction. In an AI-augmented team context, this includes:*
> - *(Axis A) Routinely identifying where AI-drafted output is subtly wrong for the specific context, documenting the reasoning, and making the alternative call.*
> - *(Axis B) Pairing with a junior IC on at least one outside-frontier task-type per quarter and visibly building the junior's capacity to make the same judgement independently next time.*
> - *(Axis C) Running the judgement-weighted review pass on outside-frontier work and contributing proposed amendments to the team's mod-103 review standard when retros surface a gap.*

Three bullets. The original descriptor is preserved. The amendment makes the AI-augmentation layer explicit and tied to specific operational artifacts the IC can point at in their promotion packet.

## Summary

- The mod-107 ladder update **keeps levels and compensation bands intact** and changes the **rubric and the level-descriptor amendments** at each rung.
- **Three new axes:** (A) judgement under AI augmentation, (B) mentorship of judgement, (C) review craft on AI-assisted work — each scaled with level, each grounded in a specific research anchor from Chapters 2–4.
- **The promotion packet after the update** includes annotated artifacts (section 2a), narratable judgement moves (section 2b), named mentorship-of-judgement outcomes (section 3), and one additional peer-feedback prompt (section 4).
- **Three failure modes the updated ladder prevents:** the throughput-promoted junior IC, the apparently-flat senior IC, the hard-to-assess staff IC.
- **Not a replacement for HR-standardised level descriptors, not a scorecard, not an anti-AI ladder, not a universal template.** Author in context; one peer-review round with senior ICs before launch.
- **Handoff to mod-108:** mod-108's promotion-case and performance-review mechanics run against the ladder authored here. The two modules compose; do not write both at once from scratch.
