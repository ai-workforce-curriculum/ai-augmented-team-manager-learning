# Chapter 2 — Manager-Output Fundamentals as the Assumed Baseline

> *This track layers AI-augmentation onto a manager-output model you already have. If you don't, four canonical texts are the shortest path to it.*

## Motivation

The rest of this track assumes you already think about managerial work the way Grove, Fournier, Larson, and Zhuo describe it: as **leverage over team output**, not as individual contribution. Every chapter that follows — the human/machine contract, review standards, ROI narrative, delegation ladder, incident post-mortem, governance crosswalk — is a leverage move applied to AI-augmented work. If the underlying model is fuzzy, the AI-augmentation layer on top will feel arbitrary.

This chapter does three things. First, it names the four texts you are expected to have read (or be reading in parallel). Second, it extracts the half-dozen ideas from them this track leans on directly, so you can spot them when they show up later. Third, it tells you what we do **not** re-teach, so you know where to go if any of it is new.

## Core concepts: the four texts and what they give you

### Grove — *High Output Management*

The foundational book on the output model. Four ideas this track leans on by name:

- **Managerial output = output of your organisation + output of neighbouring organisations under your influence.** The AI-augmentation layer does not change the equation; it changes the terms. "Your organisation" is a 5–30 person team using AI. "Neighbouring organisations" includes the platform team shipping the shared Cursor rules, the enablement lead running the org-wide Copilot rollout, the risk-engineer commissioning your evals, and the governance analyst drafting your impact assessment. Every sibling-track hand-off in Chapter 4 is a Grove neighbouring-org relationship.
- **High-leverage activities.** A manager's time is spent on activities that affect many people or that change the outcome long after the activity itself. **Setting the team's human/machine contract (Chapter 3) is a textbook high-leverage activity** — you do it once per quarter and it shapes every PR, every eval, every incident review for the rest of the quarter. So is picking the team's review standard, the enablement curriculum, the vendor shortlist.
- **One-on-ones and the meeting taxonomy.** Grove's taxonomy (process-oriented vs. mission-oriented; one-on-ones; staff meetings; operation reviews) is unchanged by AI. What AI changes is the input — some artifacts you review in a 1:1 were drafted by a model — and the review cost — judging a model-authored artifact takes a different attention budget than judging a human-authored one. Mod-104 and mod-107 return to this.
- **Task-relevant maturity (TRM) and situational leadership.** TRM governs how you delegate. AI-augmentation shifts TRM downward on some tasks (a junior IC with a model can take on a scope they could not have taken on alone) and upward on others (judgment calls on ambiguous prompts need more tenure, not less). Mod-106 and mod-107 return to this in depth.

### Fournier — *The Manager's Path*

Fournier's book is a chronological playbook from tech lead through CTO. Two things from it are load-bearing here:

- **The line-manager chapters** — "Managing People," "Managing a Team," "Managing Multiple Teams" — are the prerequisite picture of the day-to-day work this track adds AI onto. 1:1 cadence, feedback loops, dealing with underperformance, hiring, running a project meeting. We do not re-teach these; we reach for them in mod-108 (performance), mod-109 (incident response), mod-112 (ritual calendar) as common vocabulary.
- **The transition framing** — what changes going from IC to manager, from manager to manager-of-managers — tells you where you *are* on the ladder, and therefore which chapters apply to you today vs. two years from now. If you are a brand-new manager, mod-101 to mod-104 are your immediate kit; mod-108 and mod-109 should be read once and revisited when the situation presents.

### Larson — *An Elegant Puzzle*

Larson frames engineering management as **systems** — team sizing, hiring loops, planning systems, migrations, re-orgs. Two ideas from it carry directly into AI-augmented team work:

- **Team sizing and shape.** Larson's rule of thumb (six to eight direct reports, grow via sub-managers) gives you the 5–30 range this track uses. Below six, you are a tech lead; above eight, you are shaping work through others; past the mid-twenties you are on the glide path to L50. The AI-augmentation layer sharpens the question — AI changes the **effective** team size by shifting who can do which tasks — but the structural rule holds.
- **Systems for the recurring work.** Planning, hiring, promoting, migrating, firing — each is a system with a cadence, inputs, outputs. Every mod in this track adds AI-related systems alongside the existing ones (standards-as-code, eval commissioning, enablement cadence, delegation review). If Larson's framing of recurring work as systems is not natural to you yet, every subsequent mod will feel like a one-off.

### Zhuo — *The Making of a Manager*

Zhuo's book is the first-time manager's playbook. Three things from it we lean on:

- **The purpose of the manager** — "a group of people who work together to achieve a specific outcome" and your job is to make that outcome happen. Every decision in this track reduces to this: does this move make the team's outcome better, at acceptable cost? The AI-augmentation layer does not change the test.
- **Trust is the substrate.** Zhuo's framing of trust — how you build it in 1:1s, feedback, hiring — is the precondition for the human/machine contract in Chapter 3. If the team does not trust that you will back them when a model-drafted artifact goes wrong, they will not honestly flag model failures.
- **Feedback that is useful.** Zhuo's practical feedback framework (specific, timely, kind, actionable) is how mod-108 asks you to handle AI-related performance signals — someone leaning on AI too hard, someone refusing to adopt, someone over-shipping with reviews that do not hold up.

## What this track does NOT re-teach

Given the four texts are the baseline, this track skips:

- 1:1 structure and cadence fundamentals.
- Feedback-conversation structure fundamentals.
- Hiring process fundamentals (job-ladder authoring, interview-loop structure at generic level, reference checks, offer calibration).
- Planning cadence fundamentals (weekly, sprint, quarterly, annual).
- Delegation theory at generic level (TRM, RACI-style ownership, decision records).
- Team-size and shape heuristics.

If any of these is new, read the four texts before starting mod-102, or pair the track with them chapter-by-chapter.

What we **do** teach, in each of those areas, is the AI-augmentation layer:

- 1:1s where one party used a model to draft the status, the prep, the growth plan (mod-108, mod-107).
- Feedback conversations where the performance signal is partly a model's output (mod-108).
- Interview loops redesigned for candidates who use AI in-loop (mod-108).
- Planning cycles that have to account for AI tool budget, adoption stage, pilot vs. rollout (mod-102, mod-111).
- Delegation extended to include agents and jagged-frontier routing (mod-106).
- Team sizing recalibrated under AI-augmented leverage (mod-107 reads the research; mod-104 instruments the effect).

## Example: the four-text lens on one weekly artifact

Consider a weekly team status your team sends to a stakeholder, drafted by an IC with a model and reviewed by you before it ships.

- **Grove lens:** reviewing it is a high-leverage activity — one hour of your attention shapes what a VP believes about your team's progress for the next week.
- **Fournier lens:** this is manager work, not IC work. You are not expected to write the status; you are expected to make sure the status is honest and useful.
- **Larson lens:** the weekly status is a *system* with an input (team activity), a cadence (weekly), a consumer (stakeholder), and failure modes (over-claim, under-claim, missing dependencies). AI drafting changes the input and the failure modes; you adjust the system, not the cadence.
- **Zhuo lens:** the IC who drafted it needs feedback that is specific, timely, and actionable — the review is a coaching moment as well as a QA pass.

Every artifact in every subsequent module answers to the same four lenses. Hold them.

## Summary

- Grove, Fournier, Larson, Zhuo are the assumed baseline. We do not re-teach them.
- From Grove: leverage, neighbouring organisations, high-leverage activities, task-relevant maturity.
- From Fournier: the chronological line-manager picture and the transition framing.
- From Larson: team sizing and the systems view of recurring work.
- From Zhuo: trust as substrate and useful feedback.
- Every AI-augmentation move in subsequent chapters is one of these fundamentals applied to a new input. If the fundamentals are hazy, read the texts before mod-102; the track will feel disjointed otherwise.
