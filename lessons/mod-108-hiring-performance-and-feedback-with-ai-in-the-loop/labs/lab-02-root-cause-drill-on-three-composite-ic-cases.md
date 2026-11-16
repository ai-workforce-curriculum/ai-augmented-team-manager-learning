# Lab 02 — Root-Cause Drill on Three Composite IC Cases

**Duration:** 75–90 minutes.
**Chapters exercised:** Chapter 5 (the three root causes — human / workflow / tooling; the six-question drill; the strict ordering that surfaces workflow and tooling before the human cause; the per-cause intervention sequence tooling → workflow → human; the PIP contract with HR), with side-checks against Chapter 4 (the 1:1 signals that surface the pattern in the first place; the quarterly written feedback artifact; "do not use the 1:1 to build a performance-case file"), Chapter 8 (the Handoff-1 conversation with HR as an *open question*; the "do not open an informal PIP" boundary), and the compose points to [`mod-105`](../../mod-105-team-ai-enablement-programs/), [`mod-106`](../../mod-106-workflow-redesign-and-agent-delegation/), and [`mod-107`](../../mod-107-skill-growth-anti-atrophy-and-career-development/).
**Complements, does not duplicate:** Exercise 04 asks you to run the drill on a **real recent underperformance case** on your own team, with peer-manager review and an intervention plan tied to your organisation's routing / enablement / HR shape. This lab hands you three *fixed, deliberately composed* cases from a fictional team — each a different composition of the three root causes — so you can calibrate your drill-reading before you run it on a case where the diagnosis has real consequences for a specific IC. Chapter 5's load-bearing move is the *ordering*; running the drill in the wrong order on your own team's case is the single costliest failure mode the module names, and this lab is the cheap place to catch the ordering error.

## Objective

For each of three composite IC cases, run the six-question drill in Chapter 5's strict order (shape-of-work → tool-access → enablement → pairing → workflow-friction → human-signal), produce a one-paragraph diagnosis naming which of the three root causes are present in what composition, and a per-cause intervention sequence (tooling first → workflow second → human third) with the specific module each intervention composes with. Then compare against the answer key. Target: **all three primary root-cause calls match the key, your intervention sequence orders tooling → workflow → human in every case where more than one cause is present, and on at least two of the three cases you correctly identify the composed (not single-cause) diagnosis**.

## Prerequisites

- Chapter 5 read end-to-end — the three root causes, the six-question drill order, the intervention per cause, the PIP contract with HR, and the "What *not* to do" section.
- Chapter 4 skimmed — the five rotating 1:1 questions, the three feedback rhythms, the "underperformance signals in the 1:1" section.
- Chapter 8 skimmed — the Handoff-1 (open-question to HR) structure and the "do not open an informal PIP" boundary restated for mod-108.
- Optional: a one-page reminder of the modules the drill routes to — [`mod-105`](../../mod-105-team-ai-enablement-programs/) (enablement interventions), [`mod-106`](../../mod-106-workflow-redesign-and-agent-delegation/) (routing matrix), [`mod-107`](../../mod-107-skill-growth-anti-atrophy-and-career-development/) Chapter 5 (paired-review rotation; AI-off artifact; judgment-weighted review pass) and Chapter 8 (HR boundary).
- A blank file for your drill output.
- A timer.

## The fictional context

> **"Pricing Platform" team, Linden Supply.** 8 engineers (1 staff, 2 senior, 5 mid/junior). Owns the pricing engine, the promotion-rules service, and the vendor-pricing ingestion pipeline. Agents in use: Cursor Business (8 seats, rolled out Q1 2026); Claude Code via team gateway (usage-based, Q2 2026). The mod-106 routing matrix exists in v0.2 and flags **two outside-frontier task-types**: *"pricing-rule changes under regulatory-constraint evaluation"* and *"vendor-ingestion schema migrations with downstream-consumer coordination."* The team runs weekly 1:1s, a per-sprint retro, and quarterly written feedback artifacts (Chapter 4). The three ICs below are showing performance signals the manager is weighing.

Score each case against *this team's* current workflow and tooling state, not against an idealised team. The routing-matrix v0.2 flags two outside-frontier task-types; anything outside those categories is in-frontier by the matrix's current coverage. Tool access, enablement, and pairing state matter per-IC and are stated explicitly in each case below.

## Steps

### Step 1 — Set up your drill template (3 min)

Create a working file `lab-02-drill-output.md` with this template, repeated once per case:

```
Case <letter>: <IC name/level>

Q1 SHAPE OF WORK     : <answer with specific evidence>
                       signal: workflow / tooling / human / none
Q2 TOOL ACCESS       : <answer with specific evidence>
                       signal: workflow / tooling / human / none
Q3 ENABLEMENT        : <answer with specific evidence>
                       signal: workflow / tooling / human / none
Q4 PAIRING           : <answer with specific evidence>
                       signal: workflow / tooling / human / none
Q5 WORKFLOW FRICTION : <answer with specific evidence>
                       signal: workflow / tooling / human / none
Q6 HUMAN SIGNAL      : <answer; only after Q1–Q5>
                       signal: human (present / not present / residual-
                       after-workflow-and-tooling-closed)

Diagnosis (one paragraph): which of the three causes are present, in what
  composition. Primary cause named explicitly.

Intervention sequence: tooling → workflow → human.
  Tooling intervention (mod-105 / mod-111): <specific>, owner <X>,
    timeframe <Y>. If none: say "none."
  Workflow intervention (mod-106 / routing matrix / HITL): <specific>,
    owner, timeframe. If none: say "none."
  Human intervention (Ch. 4 1:1 flow / mod-107 Ch. 5 carve-outs /
    quarterly written feedback): <specific>. If none: say "none."

HR route: Handoff-1 open-question conversation NOW / NOT YET + re-eval
  date / N/A. Reasoning per Chapter 5 PIP-contract section.
```

Chapter 5 is explicit: the drill is not a scorecard. Each answer is a specific observation; the composition is what matters.

### Step 2 — Run the drill on Case A (20–25 min)

Read the full case description before running the six questions. Do not read Cases B or C yet.

#### Case A — Mid-level IC D.R., 3 years on the team, 5 years in the industry

> **The signal.** Q3 quarterly written feedback artifact (Chapter 4) reads thin on all three ladder axes. PR throughput: 9 PRs in Q3 vs. a mid-level team median of 16. Two retro cycles have surfaced "I'm not sure the pricing-rule work is going anywhere" from D.R. specifically. D.R.'s 1:1 narration over the last six weeks has included repeated time-and-attention complaints about "spending most of my day correcting Claude's output on the rule-evaluator work — it keeps proposing changes that pass the unit tests but violate the regulatory-constraint checks."
>
> **Work mix (last two quarters).** D.R. was rotated onto the pricing-rule-changes workstream at the start of Q2. The team's three Q3 regulatory-constraint-related features were all assigned primarily to D.R. — the staff engineer did design review on two of the three but did not pair on the implementation. The team's routing-matrix v0.2 lists *"pricing-rule changes under regulatory-constraint evaluation"* as outside-frontier; the matrix's prescribed routing for outside-frontier work is *"paired review (senior + mid) throughout implementation; agent for draft-first on in-frontier slices only."*
>
> **Tool access.** D.R. is on a Cursor Business seat identical to the team's senior ICs; Claude Code gateway access identical. Token budget has not been throttled.
>
> **Enablement.** D.R. completed Day 0 / 30 / 60 of the mod-105 bootcamp. Day 90 (the first paired outside-frontier project with a senior) was scheduled for Q2 but was deferred because the staff engineer who was D.R.'s planned pair was out on paternity leave; the pair was never rescheduled when the staff engineer returned.
>
> **Pairing.** No scheduled paired-review sessions with D.R. in Q2 or Q3. The staff engineer's design review on two of the three features is the only senior-IC touchpoint. The mod-107 paired-review rotation runs on the team but D.R.'s slot has never been active.
>
> **1:1 pattern.** Over the last six 1:1s, D.R. has (i) consistently answered the time-and-attention question with the agent-output-correction frustration cluster above; (ii) been unable to name a specific override of an AI suggestion when asked the anti-deference question; (iii) answered the judgement-move question in generic terms twice and with "I don't think I've had one this week" four times; (iv) described the regulatory-constraint evaluation as "something I'm still trying to build the mental model for."

Run the six questions on Case A. For each, record the specific answer, the specific evidence, and whether the question's signal points to workflow / tooling / human / none. Then produce a diagnosis paragraph, an intervention sequence, and an HR-route decision. Do not read the answer key yet.

### Step 3 — Run the drill on Case B (20–25 min)

#### Case B — Senior IC S.P., 6 years on the team, 11 years in the industry

> **The signal.** Q3 quarterly written feedback artifact (Chapter 4) reads thin on Axes B (mentorship of judgement) and C (review craft on AI-assisted work); Axis A (judgement under AI augmentation) looks fine. PR throughput: 11 PRs in Q3 vs. a senior-tier team median of 13 — not out of band. Peer feedback from two mid-level engineers in the Q3 retro noted that S.P. is "harder to get time with than used to be" for review and pairing.
>
> **Work mix (last two quarters).** S.P. has been the team's point person on the vendor-ingestion schema migrations — one of the two outside-frontier task-types on the routing matrix. The matrix's prescribed routing for that work is *"human-takes-first-cut for the design; paired-review (two seniors) at each schema cutover; agent for test and migration-script drafting only."* S.P. has been running this correctly and the migrations are landing cleanly.
>
> **Tool access.** S.P. is on the same Cursor Business + Claude Code setup as every other team member. Token usage is modestly above the team median, consistent with migration drafting.
>
> **Enablement.** S.P. completed the mod-105 bootcamp end-to-end. Attended all community-of-practice sessions in Q3.
>
> **Pairing.** S.P. is paired with one other senior for the schema migrations per the routing matrix — that pairing is active. However, S.P. has not run a paired-review rotation with any of the five mid/junior engineers in either Q2 or Q3. The mod-107 paired-review rotation in principle covers all tiers, but S.P.'s mid/junior-facing slot has been unscheduled.
>
> **1:1 pattern.** Over the last six 1:1s, S.P. has (i) named specific judgement moves on the schema migrations — two push-backs against vendor-proposed deprecation timelines, one override of a Claude-proposed migration ordering citing downstream consumer coupling — consistent Axis A signal; (ii) answered the pairing question with "I've been so heads-down on the migrations I haven't had time" every time it has come up; (iii) answered the frontier question specifically, naming the regulatory-constraint evaluator as one place the agent is not helpful; (iv) answered the time-and-attention question with "I'm fine but tired" — no specific cluster.
>
> **Manager's existing observation.** The manager has noticed that S.P.'s migrations are landing well and that S.P. is clearly operating at the senior tier on Axis A, but Axis B is thin — specifically, no junior IC's work visibly reflects S.P.'s mentorship because the pairing has not happened.

Run the six questions on Case B. Then produce diagnosis, intervention sequence, HR-route decision.

### Step 4 — Run the drill on Case C (20–25 min)

#### Case C — Mid-level IC J.N., 2 years on the team, 3 years in the industry

> **The signal.** Q3 quarterly written feedback artifact reads thin on Axis A (judgement under AI augmentation) specifically. PR throughput: 17 PRs in Q3 — in line with the mid-level team median. Three recent PR reviews flagged by the staff engineer with the comment *"agent-generated; the diff looks clean but I'm not sure J.N. would have made these decisions unassisted — the choices don't match how J.N. described the trade-offs in design."*
>
> **Work mix (last two quarters).** J.N. has been on in-frontier mid-level work — promotion-rules service features, mostly. The routing matrix v0.2 does not flag this category as outside-frontier; the prescribed routing is *"agent-takes-first-cut; human review."* J.N. has been operating against this routing. One Q3 project — a feature that touched the regulatory-constraint evaluator at its boundary — drifted into outside-frontier territory partway through but was never re-routed, and J.N. shipped it under the in-frontier routing.
>
> **Tool access.** J.N. is on the standard Cursor Business + Claude Code seat setup.
>
> **Enablement.** J.N. completed Day 0 / 30 / 60 / 90 of the mod-105 bootcamp on schedule. Participated in the Q2 community-of-practice; missed Q3's two sessions because of a planned vacation and a scheduling conflict.
>
> **Pairing.** J.N. has been in the mod-107 paired-review rotation — paired with the staff engineer on two Q2 reviews and with a senior on one Q3 review. The sessions happened.
>
> **1:1 pattern.** Over the last six 1:1s, J.N. has (i) answered the judgement-move question with a count ("I accepted most of what Cursor suggested this week; I don't think I overrode anything") and expanded when prompted with "the suggestions seemed reasonable and I agreed with them"; (ii) answered the anti-deference question with "yes, I accepted suggestion X, and I checked it and it looked right" — the specific sincere-endorsement pattern Chapter 4 names (and that mod-107 Chapter 4 names as Dell'Acqua's hard case); (iii) narrated work in generic terms consistently across six weeks; (iv) when asked to explain the reasoning behind one specific agent-accepted PR design choice in an end-of-quarter 1:1, was unable to re-derive the choice without pointing at the Cursor transcript.
>
> **Manager's existing observation.** The 1:1 anti-deference signal has been consistent. The staff engineer's recent review comments are consistent with the same pattern. The one Q3 project that drifted outside-frontier is the specific case where the rubric-vs-diff gap was clearest.

Run the six questions on Case C. Produce diagnosis, intervention sequence, HR-route decision. Now compare all three cases against the answer key.

### Step 5 — Compare against the answer key (15 min)

Read the key below only after you have completed all three cases.

#### Case A — the workflow + enablement + pairing composition

- **Q1 shape of work — WORKFLOW signal.** D.R. was rotated onto the regulatory-constraint-evaluation workstream (flagged outside-frontier on the routing matrix v0.2) at Q2 start. The matrix's prescribed routing is *paired review throughout implementation + agent for draft-first on in-frontier slices only.* The actual routing was *design review by the staff engineer on two of three features; no paired-review implementation.* This is a workflow mismatch — the IC is being routed outside-frontier work without the paired-review the matrix calls for.
- **Q2 tool access — NONE.** Cursor seat, Claude Code gateway, token budget all identical to seniors. No signal.
- **Q3 enablement — TOOLING/ENABLEMENT signal.** Day 90 (the first paired outside-frontier project with a senior) was deferred when the planned pair went on leave and *was never rescheduled.* This is the specific Chapter 5 failure mode — "a bootcamp piece [that] was skipped for a hire during a busy quarter and the IC never recovers the missing scaffolding."
- **Q4 pairing — WORKFLOW signal (composes with Q1 and Q3).** Nobody has paired with D.R. in two quarters. D.R.'s mod-107 paired-review rotation slot has never been active. Isolation from the paired-review rotation is a workflow failure (per Chapter 5's "Isolation is a workflow failure, not an IC failure").
- **Q5 workflow friction — WORKFLOW signal.** Time-and-attention 1:1 narration has specifically clustered on agent-output-correction frustration on the rule-evaluator work — consistent with outside-frontier work being routed under in-frontier conditions. The IC is experiencing what the routing matrix exists to prevent.
- **Q6 human signal — RESIDUAL-AFTER-WORKFLOW-AND-TOOLING-CLOSED.** After Q1–Q5, the residual human-side observation is that D.R. is unable to name a judgement move, says "I'm still trying to build the mental model," and has described the regulatory-constraint evaluation as something they are *becoming* able to do. This is *consistent with* the four workflow/tooling/enablement/pairing signals, *not independent of them*. The residual is the growth work that is downstream of closing the workflow/tooling gaps — not an isolable human-skill deficit.

**Diagnosis (one paragraph).** Composed workflow + enablement + pairing root cause, with a residual Axis-A growth signal that is downstream of (not independent of) the operational gaps. Primary cause is **workflow** (outside-frontier work routed as in-frontier; no paired review during implementation; no paired-review rotation slot active). Composed with a specific **enablement** gap (the deferred Day 90 piece that was never rescheduled). The thin ladder-axis evidence and the time-and-attention complaints are the *consequences* of the composed workflow/enablement/pairing gaps; treating D.R. as a primary human-performance case would be the exact Chapter 5 failure mode the drill is designed to prevent.

**Intervention sequence.**

- **Tooling / enablement (fast):** reschedule the missed Day-90 pairing in week 1 with a current senior as the pair; close the enablement gap.
- **Workflow (medium):** week 1, amend the routing matrix (or confirm the existing routing) and re-route D.R.'s next regulatory-constraint feature to paired-review-throughout per the matrix prescription; activate D.R.'s mod-107 paired-review rotation slot immediately.
- **Human-growth (slow):** across weeks 2–12, use Chapter 4's 1:1 flow to track whether the judgement-move narration starts to surface under the new routing. If after one quarter under corrected routing + pairing the Axis-A moves still do not surface, re-run the drill.

**HR route.** **NOT YET**, with re-eval at end of next quarter. Chapter 5's "PIP contract with HR" is explicit: formal escalation requires two quarters of documented growth work *after workflow/tooling causes were excluded or addressed.* In Case A, the workflow and tooling causes have been identified but not yet addressed — opening HR now would be the specific *"Do not escalate before the workflow/tooling fixes have had a chance to work"* failure. Also: opening an informal weekly-check-in "growth plan" is an informal PIP (Chapter 5's "What *not* to do") and must not be done. The Chapter 4 1:1 flow continues as the growth instrument.

#### Case B — the pairing + Axis-B composition, not an underperformance case

- **Q1 shape of work — NONE.** S.P. is on an outside-frontier task-type (vendor-ingestion schema migrations); the routing matrix prescribes human-takes-first-cut + paired-review + agent-for-drafting; S.P. is running this correctly.
- **Q2 tool access — NONE.** Identical setup; modestly above-median token usage consistent with drafting; no signal.
- **Q3 enablement — NONE.** Bootcamp complete; CoP engaged.
- **Q4 pairing — WORKFLOW signal, specifically on the mentorship axis.** S.P. is paired with another senior on the migrations (correct per matrix) but is *not* paired with any of the five mid/junior engineers in either Q2 or Q3. The mod-107 paired-review rotation's mid/junior-facing slot is unscheduled. This is the specific Axis-B mechanism gap: the senior's leverage into other ICs' growth curves is the primary way Axis B evidence is produced, and the mechanism has not been running.
- **Q5 workflow friction — NONE on the IC side; a scheduling / calendar signal on the management side.** S.P.'s "heads-down on migrations, no time to pair" is the signal — the manager has not protected S.P.'s pairing time on the ritual calendar (mod-112 compose point).
- **Q6 human signal — NOT PRESENT as underperformance.** S.P. is performing at the senior tier on Axis A (named judgement moves on two push-backs and one override, with specific evidence). The *thinness on Axis B* is not an underperformance signal; it is a signal that *the mechanism by which Axis B evidence is produced has not been running for this IC in this cycle.* Chapter 5 is explicit: "conflating 'the IC is slower than the team baseline' with underperformance" and "the drill is about *underperformance*, not about *slower throughput*" — a senior IC whose Axis A is strong but whose Axis B is thin because the pairing hasn't been scheduled is *not* an underperformance case.

**Diagnosis (one paragraph).** This is **not an underperformance case**. The primary signal is a workflow / scheduling gap on the Axis-B mechanism — S.P.'s mid/junior paired-review rotation slot has been unscheduled for two quarters while S.P. operates correctly at the senior tier on Axis A and runs the migrations per the routing matrix. The thin Axis-B evidence in the Q3 feedback artifact is the *consequence* of the mechanism not running, not evidence of a capability gap. Chapter 5's "What *not* to do" explicitly flags treating slower-than-baseline (or thinner-on-one-axis) as underperformance; the drill correctly surfaces that this is not that.

**Intervention sequence.**

- **Tooling / enablement:** none.
- **Workflow (medium):** week 1, schedule S.P.'s mod-107 paired-review rotation slot for the quarter with named mid-level engineers (two rotations over 8 weeks); protect the pairing time on the ritual calendar; make the rotation visible to the team.
- **Human-growth:** none required as remediation. The Chapter 3 pre-cycle conversation script can be used in the next 1:1 to name that Axis-B evidence is the growth move for the next promotion window — but this is a growth conversation, not a performance conversation.

**HR route.** **N/A.** This is not a case that warrants the Handoff-1 conversation. Opening one would be the exact failure mode Chapter 8 names as "the manager escalates to HR as venting, not as partnership." The quarter-end written feedback artifact should name the Axis-B gap and the Q4 mechanism change, not flag the IC to HR.

#### Case C — the human-primary case with a small workflow residual, Dell'Acqua's deference pattern

- **Q1 shape of work — WORKFLOW signal (small, specific).** J.N.'s in-frontier mid-level work mix is matrix-correct, with one exception: the Q3 feature that drifted into outside-frontier territory partway through was never re-routed. This is a workflow signal but a small one — one feature over one quarter, not a sustained misrouting.
- **Q2 tool access — NONE.**
- **Q3 enablement — MINOR signal (two missed CoP sessions in Q3).** Not a Day-90-skipped-piece scale of gap; J.N. completed the bootcamp fully. The missed sessions are worth noting but are not a load-bearing enablement gap.
- **Q4 pairing — NONE.** J.N. is in the mod-107 paired-review rotation; three sessions happened. The rotation is running as designed.
- **Q5 workflow friction — NONE named.** J.N.'s 1:1 narration does not surface specific friction clusters; the narration is generic.
- **Q6 human signal — PRESENT, and it is Dell'Acqua's deference pattern specifically.** The composite signal across weeks is distinctive: *unable to name a specific override* (accept-all at the micro-level), *sincere endorsement of accepted suggestions* ("I checked it and it looked right"), *consistently generic narration*, and — most diagnostically — *unable to re-derive an accepted agent decision without pointing at the Cursor transcript.* The last item is mod-107 Chapter 4's "hard case": the IC who sincerely believes the AI's output is correct, where sincere endorsement is evidence that *review-the-AI's-output* was applied, not that *re-derive-the-decision-from-scratch* was applied. The staff engineer's PR-review comments corroborate from the artifact side.

**Diagnosis (one paragraph).** **Human-primary** root cause: Axis-A deference pattern on the Dell'Acqua / uncritical-consumer lineage, surfacing specifically on the outside-frontier moment (the drifted Q3 feature) and consistent in the 1:1 anti-deference and judgement-move questions over six weeks. Composed with a **small workflow** residual (the one feature that drifted outside-frontier without re-routing) and a **minor enablement** signal (two missed CoP sessions). The workflow and enablement signals are small enough that they are not themselves driving the pattern — they will be closed as housekeeping — but the primary cause is the human-growth deference pattern that the Chapter 5 drill is designed to distinguish from the workflow-primary case (Case A).

**Intervention sequence.**

- **Tooling / enablement (fast):** rebook J.N. into the Q4 CoP sessions in week 1; close the minor enablement signal before it compounds.
- **Workflow (medium):** week 2, update the routing matrix (or confirm) on outside-frontier-drift detection — this is a mod-106 matrix amendment that benefits the whole team, not a J.N.-specific fix. Re-route J.N.'s next outside-frontier-adjacent feature to paired-review per the matrix.
- **Human-growth (primary, slow):** across weeks 1–12, Chapter 4's 1:1 flow with the anti-deference and judgement-move questions in rotation; add a mod-107 Chapter 5 Carve-out 2 (periodic AI-off artifact) scheduled on an in-level, outside-frontier-representative task, framed as a comparison instrument not a test (per mod-107 Chapter 5's framing-is-load-bearing note); add a mod-107 Chapter 5 Carve-out 3 (judgement-weighted review pass) applied to J.N.'s next outside-frontier PR with the staff engineer; draft the Q4 quarterly written feedback artifact naming the pattern specifically and what J.N.'s Q1 2027 artifact should show.

**HR route.** **NOT YET**, with explicit re-eval at end of Q4 2026. Chapter 5's PIP contract requires *two quarters* of documented growth work with workflow/tooling causes addressed before the Handoff-1 conversation. Q3 is Quarter 1 of the documented growth pattern; Q4 is Quarter 2. If Q4's carve-outs + 1:1 flow produce no shift in the anti-deference signal — J.N. still cannot name a specific override, the Q4 AI-off artifact is not closer to baseline than expected, paired-review surfaces the same gaps — the Handoff-1 conversation opens in Q1 2027 *as an open question*, not a recommendation. HR assesses; "continue in 1:1s with sharpened structure" is also a common outcome.

Also: do **not** cite Dell'Acqua et al. (or Noy & Zhang, or Brynjolfsson) as justification in any HR conversation about J.N. specifically. The research is about populations; the evidence for J.N. is J.N.'s specific PRs, J.N.'s specific 1:1 narration, and the specific feedback-artifact history (mod-107 Chapter 8 "What *not* to do" + Chapter 5 "Do not cite research about AI deference as evidence against a specific IC").

### Step 6 — Diagnose your drill drift (10 min)

Compare your diagnosis per case against the key. For each primary-cause mismatch, each wrongly-ordered intervention sequence, and each HR-route disagreement, write one paragraph:

- **If you called Case A primary-human:** this is the specific failure mode Chapter 5 is designed to prevent. The pre-AI intuition reads D.R.'s pattern as "underperforming mid-level" and the drill's purpose is to surface the workflow + enablement + pairing composition that is *driving* the thin ladder-axis evidence. Re-read Chapter 5's "Example: a drill that caught a workflow problem" — Case A is composed deliberately against that example's shape.
- **If you called Case B primary-human or opened HR:** this is Chapter 5's "conflating 'the IC is slower than the team baseline' with underperformance" failure, extended to a one-axis-thin pattern. A senior with strong Axis A whose Axis B is thin because the mechanism has not been running is not an underperformance case; the drill correctly surfaces the manager-side scheduling / ritual-calendar failure.
- **If you called Case C primary-workflow or primary-tooling:** the small workflow and enablement signals in Case C are real but not load-bearing. The distinctive signal is the composite Dell'Acqua deference pattern across six weeks of 1:1s *and* the staff engineer's artifact-side corroboration. Case C is the case where the drill correctly concludes the human cause *is* primary — the ordering has not caused the manager to find a workflow cause that isn't there, but it has caused the manager to close the small workflow and enablement housekeeping before the growth work starts.
- **If you ordered interventions human-first on Case A or Case C:** the tooling → workflow → human ordering is Chapter 5's load-bearing move. Even when the primary cause is human (Case C), the housekeeping tooling / workflow closes first — not to minimise the human work but to give it a clean baseline from which growth is observable. An IC still working under a wrong routing matrix *while* in a growth conversation is in the position Chapter 5's "fairness" note flags as "specifically unfair."
- **If you opened Handoff-1 with HR on Case A or Case C's Q3:** Chapter 5's two-quarter requirement is explicit, and the Chapter 8 boundary restates it. Opening before two quarters of documented growth work (with workflow/tooling addressed) is the informal-PIP-equivalent failure. The drill's "NOT YET" with named re-eval date is the correct output.

### Step 7 — Re-run Case A from memory (10 min)

Close your file for a minute; re-run Case A's drill from memory. Which answer to which question are you least confident on? The question you are least confident on from memory is the question most likely to drift under production pressure. If the question is Q1 (shape of work) or Q4 (pairing), re-read Chapter 5's six-question checklist before running Exercise 04 on your real case — these two questions are the specific ones under which the *"workflow is driving what looks like underperformance"* pattern collapses or is correctly surfaced.

## Expected output

A scratch file, roughly one page per case, containing:

- Three drill outputs: Q1–Q6 answers with specific evidence, signal classification per question, diagnosis paragraph, intervention sequence in the tooling → workflow → human order, HR-route decision with reasoning.
- A diagnostic paragraph per primary-cause mismatch, mis-ordered intervention sequence, or HR-route disagreement.
- A re-run of Case A's drill from memory with a note on the question you were least confident on.

Something like (abbreviated):

```
Case A — D.R., mid-level.
  Q1 shape of work      : WORKFLOW — outside-frontier work on routing-matrix-flagged
                          task-type routed under in-frontier conditions (no paired-
                          review implementation; staff-engineer design review only
                          on 2/3 features).
  Q2 tool access        : NONE — same seat/model/budget as seniors.
  Q3 enablement         : TOOLING/ENABLEMENT — Day 90 deferred when planned pair went
                          on leave; never rescheduled. Chapter 5's "skipped bootcamp
                          piece never recovered" failure.
  Q4 pairing            : WORKFLOW — no paired sessions in 2 quarters; mod-107 paired-
                          review rotation slot never active for D.R.
  Q5 workflow friction  : WORKFLOW — agent-output-correction frustration clustered on
                          rule-evaluator work; consistent with outside-frontier work
                          under in-frontier routing.
  Q6 human signal       : RESIDUAL — generic judgement-move narration, "still building
                          the mental model" phrasing. Downstream of operational gaps,
                          not independent of them.
  Diagnosis: composed workflow + enablement + pairing primary; residual Axis-A
             growth signal is consequence of operational gaps. NOT primary-human.
  Intervention: TOOLING — reschedule Day 90 in wk 1. WORKFLOW — matrix-correct
                routing on next rule-evaluator feature in wk 1; activate paired-
                review rotation slot immediately. HUMAN — Ch. 4 1:1 flow across
                weeks 2–12; re-run drill end of next quarter.
  HR route: NOT YET; re-eval end of Q4. Ch. 5 two-quarter requirement post workflow-
            and-tooling-close has not started.
  ✅ match.

[Case B, Case C similar shape]

Drift notes:
  First pass I called Case B a performance case because of the Axis-B thinness.
  Re-read Ch. 5 "What *not* to do": the drill is about underperformance, not
  slower-than-baseline. A senior with strong Axis A whose Axis B mechanism hasn't
  been running is not an underperformance case — it's a scheduling / ritual-
  calendar gap. Second pass: not underperformance; workflow-scheduling fix.
```

## Checkpoint

Before moving on to Exercise 04 (running the drill on a real recent case on your team) and Exercise 05 (compliance checklist) or Exercise 06 (headcount pre-read), you should be able to answer **yes** to all six:

- Did you reach a **composed-workflow primary** diagnosis on Case A — not a human-primary one — with a residual human-growth signal that the drill correctly identified as *downstream of* the operational gaps?
- Did you reach a **not-an-underperformance-case** diagnosis on Case B, recognising that thin Axis-B evidence from an un-scheduled mentorship mechanism is distinct from an underperformance pattern?
- Did you reach a **human-primary** diagnosis on Case C (Dell'Acqua deference pattern) with the small workflow and enablement signals correctly closed as housekeeping rather than treated as the primary cause?
- In every case where more than one cause was present, did you sequence the intervention **tooling → workflow → human** per Chapter 5?
- Did you default to **"NOT YET" or "N/A"** on the HR route for all three cases, with Case C's Handoff-1 opening correctly deferred to the end of Q4 (post-second-quarter of documented growth work with workflow/tooling addressed)?
- On every primary-cause mismatch, did you identify whether the drift was (a) pre-AI intuition reading workflow as a performance problem, (b) conflating thin-on-one-axis with underperformance, (c) under-weighting the composite Dell'Acqua signal across 1:1 and artifact sources, or (d) ordering interventions human-first because the human case felt "obvious"?

If any answer is no, re-read Chapter 5 end-to-end (the drill order, the common failure modes, the PIP contract with HR), re-read Chapter 8's "The three handoffs that are specifically mod-108" for Handoff B's shape, and re-run the affected case before starting Exercise 04 on your real team's context.
