# Chapter 2 — Interview Loop Redesign Under AI

> *The question is not "do we allow AI in the technical screen." The question is "what are we measuring?" Once you answer that at the stage level, the AI-use policy writes itself — some stages allow unrestricted agents, some stages require disclosure, and some stages — a small minority — genuinely benefit from a disallowed-AI control. The mistake most teams make is to answer the AI-use question first; the mistake this chapter prevents.*

## Motivation

The strongest meta-analytic evidence on interview validity is unambiguous: structured interviews — same questions, same scoring rubric, independent rater calibration — outperform unstructured interviews on job-performance prediction and reduce adverse impact on protected classes. This finding predates the AI era and is the foundation for Google re:Work's *Guide to Structured Interviewing*, the primary open reference on the practice.

Structured interviews do not become less valid when candidates have agents on hand. They become harder to score if the rubric was written against a signal — unassisted output — that half of the role no longer produces. The redesign is not a rewrite from zero. It is a re-anchoring of the rubric to the signal that matters: *can the candidate do the job as the job is actually done, which includes operating an AI agent well*, and a stage-level decision on when AI access shifts what the stage measures. Exercise 01 produces the redesigned loop.

## Core concepts

### Step 1 — Name the signal each stage is supposed to produce

Most teams' interview loops have four to six stages — a phone screen, one or two technical screens, a system-design or case-study round, a behavioural / cross-functional round, and a final round. Before the AI-use question, write down for each stage **what signal it is supposed to produce** and **how that signal differentiates between a hire and a no-hire**.

A worked example for an engineering team's technical screen:

- *Signal the stage is supposed to produce:* can this candidate, on a representative problem shape in our domain, construct a working solution and articulate the design trade-offs?
- *How it differentiates:* a strong candidate names the trade-offs, picks one deliberately, implements it, tests their own work, and recovers gracefully when something doesn't go as expected. A weak candidate skips the trade-offs, picks arbitrarily, implements something that partly works, and either does not notice the gaps or is unable to recover.

Doing this for every stage before touching the AI-use question is the chapter's load-bearing move. The common failure mode — deciding "we'll allow AI because the role uses AI" or "we'll disallow AI because we want to see the real candidate" without first naming what the stage measures — produces a loop whose scoring is inconsistent across raters because the raters are scoring different things.

### Step 2 — Decide AI-use policy per stage

Four categories of AI-use policy are useful at stage scope. Pick one per stage; document the choice and the reason.

- **AI-permitted, encouraged.** The stage explicitly rewards effective agent use. Appropriate for stages that measure *real-world job performance* — pair-programming on a representative task, writing a design doc against a vague brief, producing an ADR. The rubric for the stage includes agent-use quality alongside output quality. Example rubric criterion: *"the candidate used the agent effectively — delegated the mechanical work, retained the judgement, and caught at least one incorrect suggestion."*
- **AI-permitted, disclosure required.** The stage allows AI but asks the candidate to narrate what they are prompting, what they are accepting, and what they are overriding. Appropriate for stages where the manager wants to see the candidate's *decision-making* explicitly — a live-coding round where the candidate talks through "I'm going to let the agent scaffold this, I'm going to write the error-handling myself because the context matters, I'm overriding this suggestion because X." The rubric scores the narration as part of the signal.
- **AI-off control.** The stage disallows AI to measure a specific unassisted capability the role requires. Appropriate only when the role has a genuine unassisted-work slice — reviewing an AI-produced artifact and judging it, debugging on a system where the agent has no context, operating during an incident when the agent is unreliable. The rubric is explicit that AI-off is scoring a specific sub-capability; it is not scoring "the real candidate" versus the AI-assisted candidate being somehow unreal.
- **Take-home with full AI access.** An asynchronous assignment with the explicit framing that AI is permitted and the output will be reviewed in a follow-up walk-through. Appropriate for stages that measure *the artifact at the quality bar the team expects to ship*. The follow-up walk-through — a live round where the candidate walks a reviewer through the artifact, the choices, and the rejected alternatives — is the scoring instrument; the artifact alone is not.

The mix across a loop is typically one or two "AI-permitted" stages, one "disclosure" stage, and at most one "AI-off" stage. A loop in which every stage is AI-off is measuring the wrong candidate; a loop in which every stage is AI-permitted with no disclosure is measuring something but the signal is murky.

### Step 3 — Write the rubric at the stage level, not the loop level

Structured interviewing prescribes same-rubric scoring. The rubric lives at the stage level — one rubric per stage, four to six scoring criteria, 1–5 scale with anchors. Two additions for AI-augmented loops:

- **One AI-use criterion per rubric when AI is permitted.** Not a global axis; a criterion specific to the stage. For a pair-programming stage: *"agent use was deliberate — the candidate delegated well, overrode at least once with reasoning, caught at least one incorrect suggestion."* For a design round: *"the candidate used agent assistance to accelerate but not to replace the design judgement — the trade-offs named were the candidate's."*
- **An anti-collapse criterion.** For every stage that measures judgement, a criterion that explicitly scores the candidate's reasoning rather than the artifact. *"The candidate articulated the trade-off before implementing — can we hear the thinking?"* The criterion fires regardless of AI-use policy and is the rubric element Noy & Zhang's dispersion-compression finding predicts will remain diagnostic.

The 1–5 anchors are specific, behavioural, and written down. *"5: named three trade-offs unprompted, picked one deliberately with a stated rationale, implemented against it, revisited the rationale when a test failed."* *"1: did not articulate a trade-off; implementation was arbitrary; did not recover when a test failed."*

### Step 4 — Calibrate raters on the new rubric before the first candidate runs through it

The biggest source of adverse impact in interview loops is rater drift — different raters scoring the same signal differently. The calibration move is three exercises for every rater who will be on the loop:

- **Watch-and-score.** Two raters watch a recorded mock interview (or the organisation's shadow-interview video, if it has one) and score independently against the new rubric. Compare scores afterwards. Discrepancies are the calibration work.
- **Score a previously-run candidate.** Pick a candidate the team hired (or declined) in the last 12 months. Each rater scores the candidate against the new rubric from the available notes. Compare. The exercise surfaces where the new rubric produces a different signal than the one the team actually read before.
- **Role-play the disclosure stage.** The disclosure-required stage is the hardest one to score consistently because the raters have to listen for the narration pattern. Role-playing with a peer who deliberately runs one strong pattern and one weak pattern teaches the rater what to listen for.

This is one afternoon of work for the whole panel. The organisations that skip it produce inconsistent scores and are exposed on adverse-impact grounds; see Chapter 6.

### Step 5 — Document what is *not* measured

The loop measures a specific signal. Several things it does *not* measure well, and the hiring manager is better off being explicit than pretending otherwise:

- **Long-horizon judgement.** The interview sees two to four hours of the candidate. Judgement over months — the kind of pattern that shows up in mod-109 post-mortems — is not visible in a loop. A reference check is the right instrument, not an extra interview stage.
- **Learning rate on this team's specific stack.** Even a strong stage-level screen does not predict the candidate's ability to ramp up on your specific systems. The 30 / 60 / 90-day plan from mod-105 is where that signal materialises; the offer and ramp plan are the instruments.
- **Mentorship ability.** Observable in a loop only through a specific exercise (e.g., "walk a junior engineer through this review"), which many loops do not include. If it is a load-bearing requirement at the level, add the stage; otherwise do not pretend the behavioural round measures it.
- **"Cultural fit."** The phrase is a failure mode under adverse-impact analysis (EEOC, 2023). Replace with specific behavioural criteria tied to actual team behaviours (e.g., *"gives feedback that is specific and non-personal; receives feedback without becoming defensive"*) and score those behaviours directly.

### Step 6 — Operationalise the disclosure stage specifically

The disclosure stage is the mod-108 innovation over a pre-AI structured interview and the one that is hardest to run well. Three operational notes:

- **The rater explains the stage before it begins.** *"We use AI assistance on this team day-to-day. For this stage, you can use any tools you would use normally. What we want to hear is your reasoning out loud — what are you prompting, what are you accepting, what are you overriding, why. There is no gotcha."*
- **Silence is scored down, not neutrally.** A candidate who runs the entire stage in silence while their agent generates the artifact scores low on the narration criterion, because the signal the stage measures (decision-making under AI augmentation) is absent. The rater is not scoring *refusal to disclose*; the rater is scoring *the signal was absent*.
- **Interruption is calibrated.** Raters interrupt when the agent produces a subtle wrong answer and the candidate accepts it silently. *"Pause — I want to understand your thinking there. Why that approach?"* The interruption is part of the stage design, not a courtesy.

### Step 7 — What the live-coding and live-writing rubrics look like under AI

A concrete structural example for two of the most common stages.

**Live-coding stage rubric (AI-permitted, disclosure):**

- **Problem decomposition.** Did the candidate name the sub-problems and sequence them before writing code? (1–5; anchors specific.)
- **Agent use quality.** Did the candidate use the agent effectively — delegated the mechanical work, retained judgement on correctness, caught at least one incorrect suggestion? (1–5.)
- **Narration.** Were the candidate's prompts, acceptances, and overrides narrated so the rater could see the decisions? (1–5.)
- **Debugging / recovery.** When something failed — a test, an unexpected error — did the candidate recover with a specific hypothesis, or did they flail? (1–5.)
- **Communication.** Did the candidate ask the rater useful clarifying questions? (1–5.)

**Live-writing stage rubric (AI-permitted, disclosure; a design-doc or ADR exercise):**

- **Scope understanding.** Did the candidate ask the questions that narrow the problem? (1–5.)
- **Trade-off articulation.** Were trade-offs named and scored, not just listed? (1–5.)
- **Agent use quality.** Was the agent used to accelerate drafting without ceding judgement — are the choices in the doc the candidate's choices? (1–5.)
- **Narration.** Could the rater see the reasoning as the doc took shape? (1–5.)
- **Self-critique.** When the candidate re-read what the agent drafted, did they catch at least one thing to improve? (1–5.)

The rubrics are suggestive, not canonical. Exercise 01 writes the rubric for your team's specific signal.

### Step 8 — What *not* to do

- **Do not run an "AI-off" entire loop.** A loop with every stage disallowing AI measures something, but the thing it measures is only a slice of the real work and the hire that results is calibrated against that slice. The organisations that have tried this report that the hired IC is strong on the unassisted slice and under-calibrated on the agent-use slice that is 70% of the job.
- **Do not add a "vibe check" stage.** Unstructured rounds are low-validity, high-adverse-impact, and especially bad at reading AI-augmented work. The structured-interview literature is clear.
- **Do not ask candidates to disclose which specific AI products they prefer.** The question is adverse-impact-exposed (favours candidates whose preferred vendor matches the interviewer's, which correlates with demographic variables in ways that are hard to defend) and uninformative. Ask about *how* the candidate uses AI, not *what they use*.
- **Do not use generic AI-assessment vendor tools without a bias audit review.** If the organisation uses an automated employment decision tool (resume screening, video analysis, structured-interview scoring) that falls under the NYC Local Law 144 definition or the EU AI Act Annex III scope, Chapter 6 is the compliance framing and legal counsel is the approver. Default to not using the tool until the compliance review is complete.
- **Do not promise "AI is allowed" and then penalise the candidate for using it.** The signal the loop measures is the signal the loop should score against. If the rubric scores the candidate down for using AI, the rubric is doing something different than the stated policy — and the inconsistency reads as a gotcha to the candidate. Rewrite the rubric or the policy.

### Common failure modes in authoring the loop

- **Writing the policy before writing the signal.** Chapter 2's load-bearing step is Step 1 — the signal each stage is supposed to produce — and skipping it is the most common failure.
- **Forcing all stages into one policy.** The stages measure different things; the policies can differ. Uniform policy is a comfort, not a design.
- **Scoring the artifact without scoring the process.** Under AI augmentation, two candidates can produce indistinguishable artifacts through very different decision-making processes. The stages that only inspect the artifact lose signal that the narration criterion recovers.
- **Over-rotating on live-coding at the expense of design.** Design rounds under AI augmentation are the rounds where judgement is most visible, not least visible. If the loop cuts the design round to save time and keeps three live-coding stages, it is measuring the thing AI compresses the most.
- **Leaving the loop unchanged and hoping.** The pre-AI loop produces a candidate pool with an ambiguous signal under AI augmentation. The loop will drift to over-hiring on throughput and under-hiring on judgement, and the drift will not show up until 12–18 months in. Chapter 3 is the ladder-side intervention that catches late signal; the loop-side intervention is this chapter.

## Example: a two-stage loop redesign, before and after

Composite example; treat as calibration, not a template.

**Before (an engineering team's technical-screen stage):**

- Stage: 60-minute live-coding, two rounds.
- Policy: AI not mentioned; candidates assume AI is not allowed and most ask before using it.
- Rubric: implementation correctness (1–5), code quality (1–5), communication (1–5).
- Scoring drift: raters score high-throughput candidates highly on "correctness" even when the implementation choices were ones a senior IC on the team would have questioned.

**After (redesigned under AI augmentation):**

- Stage 1: 45-minute live-coding, AI-permitted with disclosure. Rubric: problem decomposition, agent use quality, narration, debugging / recovery, communication (five criteria, 1–5 each, specific anchors).
- Stage 2: 45-minute design round, AI-permitted with disclosure. Rubric: scope understanding, trade-off articulation, agent use quality, narration, self-critique.
- AI-off criterion added as a separate 15-minute exercise *inside* Stage 2: "review this AI-produced artifact and tell us what you would change" — the sub-stage measures the capability to judge AI output, which is Pillar 1 of the role and is not well-measured anywhere else in the loop.
- Rater calibration: one 90-minute panel session the week before the stage goes live. Three mock candidates, independent scoring, discussion of discrepancies.

The redesigned stages are the same length as the pre-AI stages. The difference is in the signal they produce, not in the time they consume.

## Summary

- **Write the stage-level signal before writing the AI-use policy.** Step 1 is the chapter's load-bearing move.
- **Four stage-level AI-use policies:** AI-permitted (encouraged), AI-permitted (disclosure), AI-off control, take-home with walk-through. Most loops run one or two permitted, one disclosure, at most one AI-off.
- **Rubric lives at stage level**, with one AI-use criterion when AI is permitted and one anti-collapse (judgement) criterion on every stage that measures judgement — grounded in [Google re:Work's structured-interview guide](https://rework.withgoogle.com/guides/interviewing-leverage-work-sample-tests/).
- **Calibrate raters** with watch-and-score, previous-candidate-scoring, and disclosure-stage role-play before the redesigned loop goes live.
- **Document what the loop does not measure** — long-horizon judgement (references), ramp rate (30/60/90), mentorship (specific exercise), "cultural fit" (replace with behaviour criteria).
- **Live-coding and live-writing rubrics** add agent-use and narration criteria alongside the correctness / quality / communication criteria.
- **Common failure modes:** policy-before-signal, uniform policy, artifact-only scoring, over-rotation on live-coding, leaving the loop unchanged.
- **Handoff to Chapter 6:** if the loop uses any automated employment decision tool (resume screening, video analysis, scoring-automation), the NYC LL 144 / EEOC / EU AI Act compliance framing in Chapter 6 applies and legal counsel is the approver.
- **Handoff to [`mod-107` Chapter 6](../mod-107-skill-growth-anti-atrophy-and-career-development/06-career-ladder-under-ai-augmentation.md):** the ladder authored there is the standard the "levelling signal" criteria in the interview rubric calibrate against.
