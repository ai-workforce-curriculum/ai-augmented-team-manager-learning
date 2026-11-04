# Chapter 4 — Performance Management with AI in Play: 1:1s, Feedback, and Goal-Setting

> *The 1:1 cadence, the feedback loop, and the goal-set the manager runs have load-bearing structure from before the AI era (Grove, Doerr, the OKR literature). The structure survives; most of the operational detail does not. This chapter is the specific set of adaptations: what changes in the 1:1, what changes in the feedback cadence, and how to write a goal-set that reflects AI leverage without rewarding "used AI" as a KPI.*

## Motivation

Grove's *High Output Management* names the 1:1 as the manager's primary instrument for the IC's development. Doerr's *Measure What Matters* popularised the OKR practice as the specific form of outcome-oriented goal-setting that most engineering organisations have adopted. Both references are still correct and are the methodological anchors here. What changes under AI augmentation is a specific set of questions — what signal the 1:1 should surface, what feedback cadence catches the atrophy pattern mod-107 names, and how OKRs are authored so that *AI leverage* shows up in the *how* rather than in the *what*.

The common failure mode this chapter prevents is a specific one: writing an OKR that reads *"Increase PR throughput by 25% through AI-assisted development."* The OKR is bad for three reasons. It rewards the specific metric Noy & Zhang's research predicts will compress; it reads AI usage as the outcome rather than as the means; and it creates the incentive structure the mod-107 atrophy work is explicitly designed to counter. The chapter writes the alternative.

## Core concepts

### What the 1:1 is for, under AI augmentation

Grove's frame is that the 1:1 is "the time the manager and the IC spend together, with the IC's agenda first." That frame is unchanged. The AI-augmentation adaptation is a specific set of five questions the manager rotates through across 1:1s — not every 1:1, but across the cycle — to surface signal the pre-AI 1:1 did not have to work to surface.

1. **A judgement-move question.** *"Tell me about a time this week you made a different call than the AI suggested, and why."* The question surfaces Axis A signal from the ladder. It is the specific question the mod-107 Chapter 7 1:1 prompts call for; mod-108 Chapter 4 is the same question embedded in the ongoing-performance 1:1 flow.
2. **A pairing question.** *"Who on the team is learning something from your judgement calls? What did they learn this week?"* Surfaces Axis B signal. A senior IC who cannot name an answer is signal to the manager that the ladder's Axis B is not getting evidence built toward it.
3. **A frontier question.** *"Where is the AI not helpful on your current work? What are you doing in that space?"* Surfaces Dell'Acqua's jagged-frontier reality from the IC's seat and gives the manager signal on which task-shapes need routing adjustments (mod-106).
4. **An anti-deference question.** *"Walk me through a recent PR where you accepted the AI's suggestion without overriding. Tell me why you accepted."* The question is not a trap; it is a growth question. If the IC cannot narrate the acceptance decision, the acceptance was likely automatic, and that is the deference pattern Dell'Acqua et al. (2023) name.
5. **A time-and-attention question.** *"What is AI *not* saving you time on? What is costing you more attention than you expected?"* Catches over-reliance and cognitive-load patterns that the throughput metric does not show.

The five questions do not run every 1:1. A reasonable cadence rotates through them across four to six 1:1s, mixed with the IC's own agenda items. The manager keeps a log of which questions ran recently so the rotation is not accidental.

### The feedback cadence that catches the atrophy signal

Feedback under AI augmentation has to arrive quickly enough that the signal is still fresh and often enough that the pattern surfaces. Three rhythms compose:

- **PR-review-moment feedback.** When a PR reviewer flags that an AI-suggested change was accepted without an override that a senior IC would have made, the comment is also a feedback signal for the IC's manager. The review standards from [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) are where the rubric lives; the manager's job is to read the review comments across the IC's PRs and surface patterns at the next 1:1. The rhythm is daily / per-PR for the signal to the reviewer; weekly for the signal to the manager.
- **Monthly 1:1 reflective feedback.** Once a month, one 1:1 is structured specifically around the five questions above. The IC knows this 1:1 is coming; it is not a surprise. The structured 1:1 is where patterns across the previous four weeks of PR-review-moment signal surface explicitly.
- **Quarterly written feedback.** Once a quarter, the manager writes a short (half-page) written feedback artifact that names what the IC did well on the three ladder axes and where the growth moves for the next quarter are. The artifact is the kernel of the eventual performance-review packet — six quarters of these compose into a promotion packet.

The cadence is not an invention. It is the explicit pattern most high-functioning engineering teams run; the mod-108 adaptation is that the content of each rhythm is anchored to the three ladder axes rather than to generic "feedback."

### OKRs or KPIs that reflect AI leverage

Two load-bearing principles, then the pattern.

**Principle 1 — AI usage is the *how*, not the *what*.** The outcome the OKR is tracking is a team outcome or an IC outcome that matters to the organisation. The use of AI is one of the means by which the outcome is achieved. If the OKR reads "Increase AI-assisted PR count by 30%," the goal has confused the means for the end; the team will optimise for the means and the outcome will stop improving.

**Principle 2 — Individual OKRs weight *outcomes* and *growth*, not throughput.** Grove's frame is that the manager's OKR is partly the team's OKR; the IC's OKR is partly the team's OKR and partly their personal development. Under AI augmentation the development side is where the ladder axes live; the outcome side is where the team's work-in-service-of-customers lives. Throughput shows up — but inside outcomes (e.g., "ship migration" rather than "ship 25 PRs"), not as its own objective.

The pattern, stated as a template:

- **Team-scope OKR (one of several).**
  - *Objective:* Ship the service-X-to-service-Y migration with no downstream incident.
  - *Key result 1:* Migration completes by end of Q2. (Outcome.)
  - *Key result 2:* Zero migration-caused incidents in the 60 days post-cutover. (Outcome.)
  - *Key result 3:* Judgement-weighted review pass applied to 100% of migration PRs; review-standard amendments ratified where gaps surfaced. (Mechanism — how the team makes KR2 true.)
- **IC-scope OKR (composed with the team OKR).**
  - *Objective:* Grow into senior-tier Axis A evidence over the cycle.
  - *Key result 1:* Produce three narratable judgement moves on the migration work, documented in 1:1 notes and the quarterly feedback artifact. (Growth; ladder-aligned.)
  - *Key result 2:* Contribute one amendment to the mod-103 review standard where a gap surfaces. (Growth; ladder-aligned.)
  - *Key result 3:* Catch at least one subtle AI-generated error at review that another reviewer would have missed. (Growth; outcome-adjacent.)

The IC-scope OKR reads very differently from a pre-AI OKR. It does not name throughput. It names the specific moves that the ladder weights. It composes with the team-scope OKR because the team OKR is the outcome and the IC OKR is how the IC contributes to the outcome in a way that also grows them.

### What a bad OKR looks like, and why

- *"Increase AI tool adoption to 90% on the team."* Measures the means, not the outcome; incentivises tool usage without reference to whether the usage produced anything. (See mod-105 on adoption-vs-activation framing.)
- *"Reduce PR cycle time by 30% via AI-assisted development."* The outcome is specified as a function of the means; if the team reduces cycle time by 25% via AI *and 5% via workflow changes*, the OKR is confused about whether that is success.
- *"Each engineer writes three AI-assisted PRs per week."* Rewards the mechanical count; the signal it produces is noise under Noy & Zhang's compression.
- *"Master Claude Code / Copilot / Cursor by end of cycle."* Not an outcome, not measurable, not aligned to any ladder axis; it is a training outcome dressed as a goal.
- *"Use AI to eliminate one type of toil."* Moves in the right direction (named outcome: toil reduction) but still names AI as the mechanism; strip the mechanism out and the OKR reads better — "eliminate one type of toil by end of cycle; AI is one of the tools available."

### The 1:1 agenda template, with AI augmentation

A specific structural example; adapt to your team.

- Five minutes: the IC's agenda.
- Ten minutes: ongoing work status — what's shipping, what's blocked.
- Ten minutes (rotating): one of the five questions above. The manager knows which one; the IC may or may not know in advance.
- Five minutes: feedback moment — one specific thing the manager observed in the previous week, named directly (positive or constructive, both over the cycle).
- Five minutes: forward-looking — what the IC is working on next, what help they need.

The fourth and fifth blocks are the parts that typically get collapsed in favour of status updates. They are the parts that produce the signal the ladder reads against. If the 1:1 regularly runs long on status and short on feedback and growth, the manager is not running a 1:1; they are running a standup with one person. Adjust the structure.

### Underperformance signal in the 1:1

The 1:1 is not the right instrument for a formal performance conversation. It is the right instrument for the manager to notice the pattern that would eventually warrant a formal conversation, in time to intervene.

Three specific signals to watch for across 4–8 weeks of 1:1s, any of which is reason to run Chapter 5's root-cause drill:

- **The judgement-move question returns no answer repeatedly.** The IC cannot name a specific moment they overrode the AI. Across four 1:1s, this is a pattern worth drilling on.
- **The narration is persistently generic.** The IC narrates their work in high-level terms that could describe any PR. When pressed for specifics, the detail is still generic. This is often a signal of deference without the IC realising.
- **The time-and-attention question surfaces frustration.** The IC names several areas where they are spending unexpected time. If the areas cluster (always on debugging, always on code review of agent output, always on correcting the agent), the signal may be a workflow or tooling gap rather than a human gap. Chapter 5 is the drill.

### What *not* to do in the 1:1

- **Do not use the 1:1 to build a performance-case file.** The 1:1 is a growth instrument. Repurposing it to build evidence for a formal process corrodes trust and will be visible to the IC within one or two 1:1s. If a formal process is warranted, open it (Chapter 5 and [`mod-107` Chapter 8](../mod-107-skill-growth-anti-atrophy-and-career-development/08-ownership-boundary-with-hr.md)) and do that work separately.
- **Do not ask the five questions as a quiz.** The questions are rotation-prompts the manager uses to shape a conversation. Asking all five in one 1:1 reads as an interrogation.
- **Do not set goals that measure the mechanism.** "Use AI daily" is not a goal. "Ship the migration with zero incidents" is a goal.
- **Do not skip quarterly written feedback because the 1:1s "covered it."** Written feedback is the artifact that compounds; the 1:1 signal is ephemeral. The quarterly artifact is the input to the eventual promotion packet and the input to any formal performance process; not writing it is a loss.
- **Do not let the goal-set live only in a document.** The goal-set is referenced in 1:1s; if the manager and IC do not revisit it monthly, it is not a goal-set, it is a document.

### How this composes with mod-104 and mod-107

- **mod-104 (productivity measurement).** The DX Core 4 / SPACE / DORA dashboards live at team level; the OKR work in Chapter 4 reads from them for the team-scope outcomes but does not use them as individual-OKR instruments. Chapter 4 is explicit on the distinction.
- **mod-107 (skill growth).** The 1:1 prompts in mod-107 Chapter 7 are a specific instrument for the atrophy pattern. mod-108 Chapter 4's five rotating questions include those prompts and extend them into the ongoing performance 1:1. The two chapters are not duplicates; mod-107 is the diagnostic, mod-108 is the integration with performance management.

## Example: a quarter of 1:1s and feedback for a senior IC on a migration project

Composite example; calibration, not a template.

- **Month 1, 1:1 #1.** Status, then the judgement-move question. The IC names a push-back on an agent-suggested schema change — it would have broken a downstream consumer the agent did not have context on. Manager logs the move as Axis A signal and notes it for the quarterly feedback artifact.
- **Month 1, 1:1 #2.** Status, then the pairing question. The IC names a specific moment they walked Junior IC B through why the agent's suggested migration pattern was subtly wrong. Manager logs the move as Axis B signal.
- **Month 1, 1:1 #3.** Status, then the frontier question. The IC names that the agent is unreliable on the specific rollback-script domain and that they have been hand-writing those scripts. Manager routes this upward to the mod-106 routing matrix conversation; this is a routing-matrix update signal, not a performance signal.
- **Month 1, 1:1 #4.** Monthly reflective 1:1, structured. Walk the Axis A / B / C signals from the previous three 1:1s. Agree on the next-month's focus: one more Axis B pairing on an outside-frontier task.
- **Month 2, 1:1 #1.** Status, then the anti-deference question. IC walks through a PR where they accepted the agent's suggestion; the narration is specific, names the alternatives considered, and names why the accepted suggestion was better in context. Manager logs as judgement-under-acceptance signal — strong Axis A evidence that is not a push-back move but still represents active judgement.
- **Month 2, remainder.** Similar rhythm. One 1:1 where the time-and-attention question surfaces that the IC is spending unexpected time correcting agent-generated test code; manager flags for the Chapter 5 drill (is this the right routing? is it an enablement gap? is it the IC?). Not escalated — observed.
- **Month 3, 1:1 #4.** Quarterly reflective 1:1. Manager drafts the half-page written feedback artifact after the 1:1, names the quarter's three strongest Axis A moves, the Axis B pairing with Junior IC B (with artifact pointers), the Axis C review-standard amendment contributed. Shares the artifact with the IC the next day.

The rhythm is steady and does not require heroic time investment. The 1:1s are the manager's existing 1:1 cadence. The structured monthly and quarterly moments are the ~45 minutes of additional work that produce the signal the ladder reads against.

## Summary

- **The 1:1 architecture is unchanged** from [Grove's frame](https://www.hachettebookgroup.com/titles/andrew-s-grove/high-output-management/9780679762881/); the AI adaptation is **five rotating questions** across the cycle (judgement-move, pairing, frontier, anti-deference, time-and-attention).
- **Three feedback rhythms compose:** PR-review-moment (weekly to the manager), monthly reflective 1:1, quarterly written feedback artifact.
- **OKRs reflect AI leverage in the *how*, not the *what*.** Team-scope OKRs name outcomes; IC-scope OKRs name ladder-aligned growth moves. Grounded in [Doerr, *Measure What Matters*](https://www.whatmatters.com/) on OKR structure.
- **Bad OKRs name the mechanism** (tool adoption, AI-assisted PR count, "master Copilot"); good OKRs name the outcome (ship migration, zero incidents) and let AI usage be the means.
- **1:1 agenda template** carves out explicit space for the rotating question and for feedback; the parts that typically get collapsed are the parts that produce signal.
- **Underperformance signals in the 1:1** — judgement-move question returning no answer; narration persistently generic; time-and-attention frustrations clustering — are reason to run [Chapter 5](05-underperformance-root-cause-drill.md)'s root-cause drill, not reason to open a formal process yet.
- **1:1 is a growth instrument, not an evidence-building instrument.** If a formal process is warranted, open it separately per [`mod-107` Chapter 8](../mod-107-skill-growth-anti-atrophy-and-career-development/08-ownership-boundary-with-hr.md).
- **Composes with** [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) (dashboards for team-scope OKRs, not individual OKRs), [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/) (the 1:1 prompts here extend the mod-107 Chapter 7 prompts into performance 1:1 flow), [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) (PR-review-moment feedback reads from the review standards).
