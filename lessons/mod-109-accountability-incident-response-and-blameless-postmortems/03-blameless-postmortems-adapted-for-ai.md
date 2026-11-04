# Chapter 3 — Blameless Post-Mortems Adapted for AI

> *You cannot blame the model. The model is not a person. But the team's post-mortem practice, inherited from SRE, is built around distinguishing "the system allowed this" from "the individual did this." Under AI augmentation there is a third entity that is neither the system nor an individual — and the blameless frame has to handle it without becoming an excuse. This chapter is how.*

## Motivation

The modern blameless post-mortem discipline has two canonical sources:

- **Google SRE, *Postmortem Culture: Learning from Failure*** (`sre.google/sre-book/postmortem-culture/`) — the chapter in *Site Reliability Engineering* (2016) that names the postmortem template, the blameless frame, and the goal of learning over punishment.
- **John Allspaw, *Blameless Post-Mortems and a Just Culture*** (`etsy.com/codeascraft/blameless-postmortems/`, Etsy Code as Craft, 2012) — the essay that articulates the "second story" (what the operator thought was true when they took the action) as the useful object of a post-mortem, as against the "first story" (the proximate error in hindsight).

Both are correct. Both apply to AI-produced incidents. Neither, as written, tells the team how to walk a fault chain that includes an agent harness, a tool authorisation surface, retrieved context the agent consumed, and a model version that silently changed. The gap is not conceptual; it is operational. The practice has to be extended.

The extension is this chapter. The two load-bearing additions are:

1. **The fault chain has five AI-specific layers** that the pre-AI post-mortem template does not name. Chapter 3 names them and gives the specific question the post-mortem asks at each layer.
2. **The counterfactual narration has to be careful with the model**. Allspaw's "second story" is the operator's state of mind at decision time. Under AI augmentation, the "operator" is sometimes a human (IC, reviewer, manager) and sometimes a model acting under a prompt. The chapter is explicit about how to narrate the model's behaviour without either anthropomorphising it (which blames it) or treating it as a weather event (which excuses the humans around it).

The chapter is not a replacement for Google SRE or Allspaw. It is the overlay a team uses when running their already-good blameless post-mortem practice on an AI-produced incident.

## Core concepts

### The frame: the model is neither the villain nor the weather

A common failure mode has two symmetric shapes:

- **"The model hallucinated"** as the conclusion of the post-mortem. This excuses the humans around the system. The question the post-mortem is supposed to answer — *what change to our system reduces the probability of the next incident of this shape?* — has not been engaged with. Calling it hallucination without further interrogation is a stop-word.
- **"The reviewer missed it"** as the conclusion of the post-mortem. This re-introduces individual blame through the back door. The reviewer approving a subtle AI-authored bug under queue pressure in three minutes is a system signal (the queue is too deep, the checklist is not catching this class of bug, the AI-authored content was indistinguishable from the human-authored content at review time). The reviewer's state of mind and bandwidth are the system's responsibility; naming them does not stop the post-mortem, it starts it.

The frame mod-109 uses: *the model is one layer of a system the humans designed and chose to operate*. The humans cannot blame the model, and the humans cannot excuse themselves by pointing at it. The post-mortem asks what the *humans* — through the standard, the standards-as-code stack, the eval, the HITL checkpoint, the tool-authorisation policy, the routing matrix, and the C1 decision in the contract — could have done differently such that the model's behaviour in this case would not have produced the harm.

### The fault chain, five AI-specific layers

The pre-AI post-mortem walks a chain that is roughly *detection → operator action → artifact → environment*. The AI-augmented chain adds five layers between operator action and artifact. Walked in order, outside-in:

1. **The human reviewer.** What did the reviewer see at review time? How much time did they have? What did the checklist require of them? Was the AI-authored content distinguishable from human-authored content, and if not, was that supposed to be caught here? If the reviewer approved without examining the artifact, *why* — queue pressure, checklist silence, trust in the IC, trust in the tests? The *second story* here is the reviewer's state of mind: what were they operating under that made the approval seem reasonable? The post-mortem names it without judging it.
2. **The human IC (prompter).** What did the IC intend? What prompt did they send (preserved from Step 4 of Chapter 2)? What was the IC's prior context — did they just come off a long day, a hard incident, a different task? Did the IC verify the artifact themselves before submitting, and if not, what signal would have told them to? The second story: what was the IC expecting the agent to do, and in what ways did their expectation differ from what happened?
3. **The agent harness and policy.** Which harness was running (Claude Code, Cursor, Copilot, internal agent)? What AGENTS.md / rules files / policy configuration was in effect at the time? Did the harness enforce the review-time guardrails it was supposed to? If a HITL checkpoint was defined for this workflow (mod-106 Chapter 4), did it trigger? If an auto-generated comment was supposed to be surfaced to the reviewer, was it? If the harness was supposed to prohibit a class of edit or a tool call, did it? The harness is a *system layer* the team owns; failures here are mod-106 failures.
4. **The prompt and the retrieved context.** The exact prompt the agent received, including any system prompt, agent-authored planning prompts, and user prompt. The context the agent retrieved from RAG, tool calls, file reads. Was any of it stale, poisoned, inconsistent, or wrong? For prompt-injection cases, this is where the untrusted-content path enters the chain. For hallucination cases, this is where the "did the model make something up when the context did not say it" or "did the context give the model wrong information that it faithfully repeated" distinction is drawn.
5. **The model behaviour.** Given the prompt and the context in Layer 4 and the policy in Layer 3, did the model produce the output the human had reason to expect? If the model version silently changed and the behaviour on the same prompt / context is now different, that is a Layer 5 regression signal — and a vendor-governance signal (mod-111). Layer 5 is the model-level layer; this is where `ai-risk-engineer` runs their reproduction and guardrail work.

The chain is walked outside-in because the outer layers are typically the ones the team owns and can change. By the time the post-mortem reaches Layer 5, most of the actionable changes have already surfaced in Layers 1–4. If the only actionable finding is at Layer 5, the team's primary action is to *extend Layer 3 or Layer 4* (policy or context) so that the model's failure mode is caught before it reaches the human reviewer next time.

The outside-in order matters for the frame: it keeps the humans in the system visible and prevents the "it was the model" dodge. It also keeps the manager's own responsibility — the system owner — visible at Layers 1 (reviewer bandwidth, checklist content) and 3 (harness policy, HITL coverage).

### The template, extended

A template the team can run, composed from Google SRE + Allspaw with the AI-specific extensions. The sections map to the Google SRE postmortem sections; the italics are AI-specific extensions.

**1. Summary.** One paragraph. What happened, when, severity, who was affected.

**2. Impact.** Reach of the wrong output; reversibility; user / partner / customer harm.

**3. Root causes.** The outside-in walk through the five fault-chain layers. Each layer has one paragraph. For layers that are *not* in the chain for this incident (e.g., no prompt injection → Layer 4 does not have an untrusted-content finding), say so explicitly — the layer is still inspected.

**4. Trigger.** The specific event that moved the artifact from latent to active (the deploy, the merge, the model-version flip, the prompt change).

**5. Resolution.** How the incident was contained, when, by whom.

**6. Detection.** Which channel detected, how long after the trigger, whether the detection should have been faster.

**7. Action items.** The backfeed. Each item is owned, has a date, and lists the standard / eval / routing / HITL / tool-authorisation / contract-change-log artifact it updates. [Chapter 6](06-regression-fixture-backfeed.md) is the discipline that makes these land.

**8. Lessons learned.**
- What went well.
- What went wrong.
- *AI-specific: what the trace told us the agent was doing that we did not expect.*
- Where we got lucky.

**9. Timeline.** Every logged event with a timestamp. *Include agent-session events (session start, tool call, model response) as first-class events on the timeline, not footnotes.*

**10. Supporting evidence.** The preserved trace from Step 4 of Chapter 2. Links to the session archive, the prompt chain, the retrieved context, the as-submitted artifact.

Google SRE's template is `sre.google/sre-book/example-postmortem/` (the canonical "Shakespeare Service" example); Allspaw's framing is the "second story" overlay on Section 3. The AI extensions are Sections 3 (five layers), 7 (backfeed into mod-103 and mod-106), 8 (agent behaviour surprise), 9 (agent timeline), 10 (trace preservation).

### Counterfactual narration — the Allspaw "second story" under AI augmentation

Allspaw's core move is to narrate *what the operator thought was true at decision time* rather than *what hindsight now says was true*. The move is correct and it extends cleanly:

- For the **reviewer**, the second story is their state of mind at approval: queue, time pressure, what the checklist required, what the AI-authored content looked like, whether anything flagged for attention. The post-mortem reconstructs this from the reviewer's own account, from the review-tool timestamps, and from the artifact as it appeared at review time.
- For the **IC / prompter**, the second story is what they expected the agent to do. Reconstructed from their account, from the prompt they sent, from their prior prompts in the session (did they iterate towards the output, suggesting they were correcting a prior attempt?), from whether they ran the agent's output themselves before submitting.
- For the **agent**, there is no second story — the agent is not an operator with a state of mind. What there is instead is a factual narration: *given this prompt, this context, this policy, this model version, the agent produced this output*. The question for the post-mortem is not *why did the agent do that?* (which is a model-behaviour question that belongs to the vendor and to `ai-risk-engineer`) but *was the system that constrained the agent sufficient?*. The latter is the humans' question.

The team practises a specific discipline here: **the post-mortem never says "the agent decided to..." or "the agent thought..."**. The language is factual: "given X, the agent produced Y." Anthropomorphising the agent sneaks blame onto it; de-humanising it does not require euphemism, just precision. The language choice is small but consistent.

### The five systemic questions the post-mortem answers

Every blameless post-mortem for an AI-produced incident answers five systemic questions, no matter which incident class it is:

1. **Standard.** Was there a review standard for this class of artifact? If yes, was it followed? If no, which mod-103 Chapter 2 row should exist now?
2. **Standards-as-code.** Did the standards-as-code stack enforce the subset that the checklist specifies? If a Cursor rule or AGENTS.md section was supposed to catch this at author-time and did not, which mod-103 Chapter 3 rule is being added or changed?
3. **Eval.** Did a commissioned eval cover this class of regression? If yes, why did it not catch this? If no, what is the mod-103 Chapter 4 eval brief for the new eval?
4. **Routing / HITL / tool-authorisation.** Did the routing matrix (mod-106 Chapter 2) route this workflow correctly? Did the HITL checkpoints (mod-106 Chapter 4) include the point this incident would have triggered? Did the tool-authorisation policy (mod-106 Chapter 6) authorise more than was warranted? Which mod-106 artifact is being amended?
5. **Contract.** Does the accountability contract (mod-103 Chapter 5) need an amendment? Is there a C1 scope decision ("AI may draft X") or a C2 verification-bar line that this incident proves wrong?

The five questions are the structural backbone of the post-mortem. An incident whose write-up does not answer any of them has not closed the loop; an incident whose write-up answers all five with "no change needed" is either very small or has not been engaged with seriously.

### Blameless does not mean actionless

A specific failure mode to prevent: blameless is read as "no consequence anywhere." The correct reading is **no individual punishment for surfacing the fault; yes systemic change in response to the fault**.

- The IC who submitted the artifact is not punished, but the review standard is tightened.
- The reviewer who approved under queue pressure is not punished, but the queue-budget problem that produced the pressure is fixed at the manager level.
- The agent harness that failed to enforce a guardrail is not "blamed," but the harness configuration is updated.
- The manager who authored the C1 scope decision that was wrong in retrospect is not punished, but the C1 decision is updated and the team is told.

The post-mortem is blameless; the standards stack is not. The next incident of the same shape is caught because the standards changed.

### The separation from performance management

A specific separation that is frequently violated: **the blameless post-mortem does not become a performance review**.

If the fault chain surfaces an IC-side pattern — repeated inadequate review, systematic bypass of HITL checkpoints, consistent AI-deference despite coaching — the manager carries that pattern into a 1:1 conversation per [`mod-108` Chapter 4](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/04-performance-management-with-ai-in-play.md). The pattern conversation is *separate from* and *follows* the post-mortem; it does not belong in the write-up.

The reasons are two. First, collapsing them makes the post-mortem unsafe, and the team stops surfacing incidents. Second, a single incident is not a performance signal — a pattern across several incidents is. The post-mortem names what the system did; the 1:1 names what the IC does across many weeks.

[`mod-108` Chapter 5](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/05-underperformance-root-cause-drill.md)'s underperformance drill is the companion template; it separates workflow / tooling / human root causes for performance signals. The incident post-mortem and the underperformance drill are two different instruments.

### Common failure modes in running the post-mortem

- **Stopping at "the model hallucinated."** Layer 5 is not an answer; it is the start of the question. If the write-up terminates at Layer 5 with no action items in Layers 1–4, the write-up is incomplete.
- **Letting the vendor off the hook when they should own it.** If the model version silently changed and the vendor's documented behaviour was violated, the vendor is in the chain and the vendor's SLA is relevant. [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) is where the vendor-side artifact lands; mod-109's post-mortem names the trigger.
- **Attributing fault to an individual.** "The reviewer missed it" is first-story framing. Rewrite into system-and-second-story framing: "the reviewer approved in three minutes under queue pressure of 40 open reviews; the AI-authored content was indistinguishable from human-authored content at review time; the checklist did not require a diff-vs-prior check on this workflow."
- **Running the post-mortem in a punitive meeting.** The meeting culture signals whether the post-mortem is safe. Google SRE's practice is explicit about this; the meeting should be run by someone trained in post-mortem facilitation (not necessarily the manager), and the published write-up should be reviewed for first-story language before it is distributed.
- **Writing the post-mortem for upward audience first.** The audience of the post-mortem is the team. The upward summary (one paragraph for the VP) is a derivative of the post-mortem, not the post-mortem itself. Writing for upward audience first produces defensive language and buries the systemic findings.
- **Treating the post-mortem as a sunk cost.** If the action items in Section 7 do not land within two weeks, the post-mortem has not delivered value. The backfeed discipline in [Chapter 6](06-regression-fixture-backfeed.md) is how the action items land; [Exercise 05](exercises/exercise-05-regression-fixture-backfeed-ritual.md) is the ritual that makes the backfeed survive.

## Example: the fault chain walked outside-in

Illustrative composite; carries forward the Chapter 2 example (wrong number reached an executive dashboard through an AI-authored pipeline change).

**Layer 1 — The human reviewer.** The reviewer approved the diff in three minutes. The review queue at the time contained 34 open reviews; the reviewer was coming off two prior approvals and had a 1:1 scheduled 15 minutes later. The checklist required *"tests pass + the change touches no critical path"*; the AI-authored change touched a pipeline column aggregation, which the checklist did not flag as critical path. The reviewer did not open the diff's prior-version comparison; the checklist did not require it. *Second story*: the reviewer was operating under a checklist that did not surface this class of change as critical. **Action item:** add *"AI-authored pipeline changes include a diff-vs-prior-run snapshot in the PR; reviewer must open the snapshot"* to the review checklist. (Updates mod-103 Chapter 2.)

**Layer 2 — The human IC (prompter).** The IC sent a 180-token prompt asking the agent to "update the column aggregation to include the new revenue source." The IC's prior four messages to the agent that session show iteration on a different pipeline, which did not share the column-mapping file. The IC did not spot-check the agent's output against a prior run of the pipeline before submitting; the IC's workflow did not include spot-checks for this kind of change. *Second story*: the IC expected the agent to produce a straightforward column-aggregation update based on the file it was reading from. The IC did not realise the agent was reading from a stale column-mapping doc. **Action item:** add *"agent must flag when retrieved context's last-modified timestamp is older than the referenced upstream schema's last-modified timestamp"* to the agent's retrieval configuration. (Updates mod-106 Chapter 6 agent configuration.)

**Layer 3 — The agent harness and policy.** The harness was Cursor with the team's standard AGENTS.md. No HITL checkpoint existed for pipeline column-aggregation changes in the mod-106 Chapter 4 checkpoint set. The harness did not surface the staleness signal because it did not have one. *Finding*: mod-106 Chapter 4's HITL checkpoint set was authored for workflows where the human reviewer is the primary catch; this class of change does not surface to the reviewer in a way that a human catches without a tool. **Action item:** add a mid-run gate HITL checkpoint for pipeline aggregation changes that requires the agent to produce the diff-vs-prior-run snapshot before the human sees the PR. (Updates mod-106 Chapter 4.)

**Layer 4 — The prompt and retrieved context.** The prompt is captured; it does not include an explicit "verify against prior run" instruction. The retrieved context includes a file (`column-mapping.yaml`) that was last modified five months ago and references a prior schema; the actual upstream schema changed three weeks ago. The staleness was not flagged to the agent. *Finding*: the retrieval configuration did not include a staleness check. **Action item:** same as Layer 2 — staleness-signal flag in retrieval configuration.

**Layer 5 — The model behaviour.** Given the prompt and the stale context in Layer 4, the model produced an output that was correct *relative to the stale context* — that is, the model did not hallucinate; it faithfully executed what the stale context implied. This is a **hallucination-driven harm class incident** (Chapter 4) in the broad sense that the system produced a confidently wrong output, but the specific failure mode here is *stale context*, not model confabulation. *Finding*: no model-level action item; the engineered-risk reproduction by the risk-engineer confirmed the model behaves correctly on the current schema.

**The five systemic questions.**

1. **Standard.** Review checklist did not cover this class of artifact as critical path. → New row.
2. **Standards-as-code.** No AGENTS.md section on staleness detection in retrieval. → New section.
3. **Eval.** No eval existed that would catch an aggregation regression against the prior run. → New eval row (commissioned through risk-engineer per Exercise 05).
4. **Routing / HITL / tool-authorisation.** HITL checkpoint missing for pipeline aggregation changes. → Checkpoint added.
5. **Contract.** No contract change — the C1 scope ("AI may draft pipeline changes") is correct; the C2 verification bar is being tightened via the checklist update. Change-log entry on the contract notes the tightening.

Write-up published Friday following the Thursday post-mortem meeting. Three action items in flight; one owner each; two-week close-out date. The eval row lands five weeks later via the Exercise 05 ritual.

## Summary

- The blameless post-mortem discipline from [Google SRE](https://sre.google/sre-book/postmortem-culture/) and [Allspaw](https://www.etsy.com/codeascraft/blameless-postmortems/) holds under AI augmentation. The chapter extends it; it does not replace it.
- **The frame:** the model is neither the villain nor the weather. It is one layer of a system the humans designed and chose to operate. The team cannot blame the model and cannot excuse itself by pointing at it.
- **The fault chain has five AI-specific layers**, walked outside-in: (1) reviewer, (2) IC/prompter, (3) agent harness and policy, (4) prompt and retrieved context, (5) model behaviour. Outside-in keeps the humans visible and prevents the "it was the model" dodge.
- **The template** composes Google SRE sections with AI extensions: Section 3 walks the five layers; Section 7 names backfeed action items; Section 8 names what the agent did that was not expected; Section 9's timeline includes agent-session events; Section 10 links the preserved trace.
- **The counterfactual (Allspaw's "second story")** is reconstructed for reviewer and IC; it is not applied to the agent. The agent is narrated factually: "given X, the agent produced Y." The post-mortem never says "the agent decided" or "the agent thought."
- **Five systemic questions** every post-mortem answers: standard, standards-as-code, eval, routing / HITL / tool-authorisation, contract.
- **Blameless does not mean actionless.** No individual punishment; yes systemic change. The next incident of the same shape is caught because the standards changed.
- **Separation from performance management** is strict. The post-mortem does not become a performance review. [`mod-108` Chapter 5](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/05-underperformance-root-cause-drill.md)'s underperformance drill is the companion template.
- **Common failure modes:** stopping at "the model hallucinated"; letting the vendor off the hook when they should own it; attributing fault to an individual; punitive meeting culture; writing for upward audience first; treating the post-mortem as a sunk cost.
- **Composes with** [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) (standards, standards-as-code, evals, contract — the backfeed targets), [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) (routing, HITL, tool-authorisation — the backfeed targets), [`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/) (the separation from performance management), and [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) (vendor-side trigger when the vendor is in the chain).
