# Lab 02 — Fault-Chain Walk and Blameless-Language Calibration

**Duration:** 75–90 minutes.
**Chapters exercised:** Chapter 3 (the frame — model is neither villain nor weather; the five AI-specific fault-chain layers walked outside-in; counterfactual narration with Allspaw's "second story" for humans only, factual narration for the agent; the discipline *"the post-mortem never says 'the agent decided to...'"*; the five systemic questions — standard / standards-as-code / eval / routing-HITL-tool-authorisation / contract; blameless does not mean actionless; the separation from performance management), with side-checks against Chapter 2 (the trace-preservation artifacts Section 10 of the write-up links to) and Chapter 6 (the backfeed-ticket shape Section 7 of the write-up produces — expanded in [Lab 03](lab-03-backfeed-ticket-conversion-from-a-post-mortem.md)).
**Complements, does not duplicate:** [Exercise 02](../exercises/exercise-02-blameless-postmortem-adapted-for-ai.md) asks you to **author a full AI-adapted blameless post-mortem** for a seeded or real incident on your team. This lab hands you a *fixed, deliberately-mixed-signal* post-mortem draft from a fictional team — one in which the first-pass author has leaked exactly the failure modes Chapter 3 names (stopping at "the model hallucinated", "the reviewer missed it" first-story framing, "the agent decided to..." anthropomorphising, Section 7 action items in free text without backfeed-ticket shape, no walk of Layer 3 or 4) — so you can calibrate your reading of the Chapter 3 extensions before you author on a real incident with real stakeholders in the room. A manager whose fault-chain walk stops at Layer 5 or who publishes anthropomorphising language for the executive to read will produce a post-mortem that pattern-matches to the Chapter 3 failure-mode list and does not close the loop.

## Objective

Given a deliberately flawed post-mortem **draft v0** for a fictional Sev-2 incident, (i) produce a **systemic rewrite** of six specific problematic sentences, converting first-story / anthropomorphising / Layer-5-stop phrasings into outside-in systemic framing per Chapter 3's discipline; (ii) **walk the five fault-chain layers outside-in**, producing one paragraph per layer plus the explicit "this layer not in scope for this incident" note where that applies; (iii) **answer the five systemic questions** (standard / standards-as-code / eval / routing-HITL-tool-authorisation / contract) with specific "which artifact changes, who owns, where it lands" answers; and (iv) **compare against the answer key**.

Target: **your systemic rewrites are factual and layer-specific on at least five of the six sentences, your fault-chain walk reaches a non-stop-word Layer 3 or Layer 4 finding as the primary root cause (not Layer 5), your five systemic-question answers each name a specific destination artifact, and you do not collapse the post-mortem into a performance-review of either the IC or the reviewer** (the two specific failure modes Chapter 3 flags as contamination of the blameless frame).

## Prerequisites

- Chapter 3 read end-to-end — especially *"The frame: the model is neither the villain nor the weather,"* *"The fault chain, five AI-specific layers,"* *"The template, extended,"* *"Counterfactual narration,"* *"The five systemic questions,"* *"Blameless does not mean actionless,"* *"The separation from performance management,"* and *"Common failure modes in running the post-mortem."*
- Chapter 2 skimmed — especially Step 4 (trace preservation) and the chapter's seven-step map so you can locate where Section 7 action items feed into Step 7 close-out.
- Chapter 6 lightly skimmed — the backfeed ticket shape is what Section 7's action items will become. (The *conversion* is Lab 03's focus; this lab names the action items in sufficient detail that Lab 03 can take them to ticket shape.)
- A blank file for your rewrites + fault-chain walk.
- A timer.

## The fictional context

> **Sev-2 incident at Caldera Analytics**, a 9-engineer platform team (1 staff, 3 senior, 5 mid). Owns the forecast-pipeline service and an agent-authored ETL ingestion flow that ships internal data to a partner-facing dashboard once per day. Agents in use: Claude Code with the team's AGENTS.md; the harness has read / write authorisations on the ingestion repo but not on production data. On **2026-11-04 (a Wednesday)**, a column-aggregation error in a partner-facing dashboard surfaced after the Monday run. A downstream analyst noticed the partner-report number was off by roughly 3× what the prior week's number should have been. The AI-authored pipeline change had merged the prior Thursday evening; the reviewer approved the diff in three minutes. The post-mortem was run the following Friday; the draft below is the **v0 write-up the on-call engineer produced over the weekend** before the manager has reviewed it. The manager's job is to walk the draft against Chapter 3's discipline before it gets published to `#eng-ai-incidents` and summarised upward to the VP.

Score the rewrites against *the Chapter 3 discipline as written*, not against an idealised "professional tone." Chapter 3 is specific: factual narration for the agent, outside-in walk, systemic framing on the humans' second story, five questions each with a destination artifact. A rewrite that smooths the language but preserves "the reviewer missed it" has not fixed what needs fixing.

## The flawed draft, v0

Pin this to a scratch file; you will annotate it in Step 2.

```
# Post-mortem — 2026-11-04 column-aggregation incident (DRAFT v0)

## Summary
On Monday 2026-11-04 the partner-facing weekly dashboard showed a revenue aggregate
that was wrong by roughly a factor of 3. The error originated in an AI-authored
change to the ingestion pipeline that merged on Thursday 2026-10-30. Severity Sev-2.

## Impact
One partner report with the wrong number was sent as part of the Monday weekly
email. We corrected and re-sent at 15:00 Monday. No further external reach.

## Root cause
(1) The model hallucinated the column-aggregation logic in the parser rewrite —
    it chose to aggregate on the `volume_units` column where it should have
    aggregated on `volume_units_scaled`. The agent decided to use the un-scaled
    column because it thought that was the canonical one.
(2) The reviewer missed it. The reviewer approved the PR in three minutes
    without opening the test output. If the reviewer had been more careful
    this would not have shipped.
(3) Also, the IC's prompt was sloppy — the IC should have been more specific
    about which column the aggregation targets.

## Trigger
The Monday pipeline run that fed the weekly partner dashboard.

## Resolution
IC manually re-ran the pipeline with the corrected code; dashboard refreshed;
partner email corrected and re-sent at 15:00 Monday.

## Detection
A partner analyst flagged the number in `#analytics-questions` at 09:40 Monday.
The pipeline team's on-call was pinged at 09:55.

## Action items
- Reviewer to be more careful on AI-authored PRs.
- IC to write better prompts.
- We will add "aggregation" to the review checklist.
- Someone should probably write an eval for this.

## Lessons learned
- What went well: we caught it within one weekly cycle.
- What went wrong: the model made a wrong call and the reviewer did not catch
  it. We need to not trust the agent as much on pipeline work.
- Where we got lucky: the analyst caught it before we sent to more partners.

## Timeline
- Thu 2026-10-30, 18:40 — PR merged.
- Mon 2026-11-04, 09:40 — analyst flagged.
- Mon 2026-11-04, 15:00 — corrected dashboard + email sent.

## Supporting evidence
(TBD — need to find the Claude Code session if the IC still has it)
```

Pin additionally the following **factual record** (the trace the IC has since recovered, which the v0 draft does not use):

```
Preserved trace (recovered Monday afternoon from the IC's laptop before
the session timed out):

- Harness   : Claude Code with team AGENTS.md revision 2026-09-15.
- Model     : claude-sonnet-4-6 (no version pinning).
- Prompt    : "Update the ingestion parser to add the new revenue source.
              Aggregate on the volume_units column and write the output
              to the weekly partner table."
- Retrieved context the agent saw:
    - `ingestion/column-mapping.yaml`  (last modified 2026-05-14,
       references `volume_units` as the aggregation column)
    - `ingestion/parser.py` current version
    - `tests/test_parser.py`
- Agent's tool calls: edit on `ingestion/parser.py`; no shell; no outbound
  tool. No HITL checkpoint triggered.
- As-submitted artifact: diff against `parser.py`, 42 lines, aggregates on
  `volume_units`.
- Reviewer's path: opened the PR at 18:37 Thursday, reviewed-with-approval
  posted at 18:40. CI was green. Review queue depth at that time: 27 open
  reviews. Checklist in effect: review checklist v3.2, which required
  "tests pass + change touches no critical path"; the pipeline column
  aggregation is not currently flagged as critical path on the checklist.

Context note (from the staff engineer, added Tuesday):
    - The `volume_units` column was renamed in a schema migration on
      2026-09-02 to `volume_units_scaled` to reflect the new scaling
      applied upstream. The migration PR updated most downstream readers
      but the `column-mapping.yaml` file was not updated as part of the
      migration — it still references `volume_units` as of the incident.
    - No commissioned eval covers "aggregation on the correct column
      post-schema-migration."
```

## Steps

### Step 1 — Read the draft and the trace (10 min)

Read the v0 draft once. Read the trace twice. You will annotate the draft against Chapter 3's discipline in Step 2; the trace is what makes the fault chain walkable past Layer 5.

The specific thing to notice before the timer starts: the draft's "Root cause" section stops at Layer 5 (*"the model hallucinated"*) and bolts on a first-story Layer 1 (*"the reviewer missed it"*) and a first-story Layer 2 (*"the IC's prompt was sloppy"*). The draft does not touch Layer 3 (harness / policy / HITL) or Layer 4 (retrieved context — the stale `column-mapping.yaml`). The trace shows that **Layer 4 is actually the primary root cause** (stale context faithfully executed by the model) and Layer 3 is the system-level missing-HITL / missing-staleness-detection story. This is the Chapter 1 running example in post-mortem form, and it is the specific case Chapter 3 names as a *stale-context Class 1* (per Chapter 4) that the draft has misdiagnosed as *confabulation*.

Do not fix the draft yet. Just notice.

### Step 2 — Rewrite six problematic sentences (25 min)

The v0 draft contains six sentences that violate Chapter 3's discipline. Your job is to produce a systemic rewrite of each. Create a file `lab-02-rewrites.md`. For each of the six sentences, write:

```
Original (v0 draft):
  "<exact sentence>"

Chapter 3 violation:
  <which specific discipline this violates — first-story framing / anthro-
   pomorphising / Layer-5 stop-word / performance-review contamination /
   vague action item / "what went wrong" blame leakage>

Rewrite:
  <systemic, factual rewrite that walks the right layer and names the
   second story for the human role or the factual narration for the
   agent>
```

The six sentences to rewrite:

1. *"The model hallucinated the column-aggregation logic in the parser rewrite — it chose to aggregate on the `volume_units` column where it should have aggregated on `volume_units_scaled`."*
2. *"The agent decided to use the un-scaled column because it thought that was the canonical one."*
3. *"The reviewer missed it. The reviewer approved the PR in three minutes without opening the test output. If the reviewer had been more careful this would not have shipped."*
4. *"Also, the IC's prompt was sloppy — the IC should have been more specific about which column the aggregation targets."*
5. *"Reviewer to be more careful on AI-authored PRs."*
6. *"What went wrong: the model made a wrong call and the reviewer did not catch it. We need to not trust the agent as much on pipeline work."*

Target: each rewrite is **factual** on the agent (no "decided / thought / chose"), **second-story** on the humans (names what they were operating under, not what they should have done), **layer-specific** (states which of the five layers the finding sits in), and **action-oriented** at the system layer (names the standard / standards-as-code / eval / routing / HITL / tool-authorisation / contract artifact that will change, even if briefly — the full backfeed-ticket conversion is Lab 03).

### Step 3 — Walk the fault chain outside-in (20 min)

In `lab-02-rewrites.md`, produce five paragraphs, one per Chapter 3 layer, walked outside-in. The template:

```
Layer 1 — The human reviewer.
  Second story: <what the reviewer was operating under at approval time — queue,
                checklist, what they saw, what was visible vs. invisible>
  Finding    : <systemic — not "the reviewer failed," but "the system allowed
               this to look like a routine approval">
  Action item: <which mod-103 / mod-106 artifact changes, briefly>

Layer 2 — The human IC (prompter).
  Second story: <what the IC expected the agent to do; iteration history if
                relevant; whether the IC spot-checked>
  Finding    : <systemic — the IC's workflow, not the IC's character>
  Action item: <...>

Layer 3 — The agent harness and policy.
  Finding    : <what the harness enforced / failed to enforce; which HITL
               checkpoints from mod-106 Ch. 4 were in scope and whether they
               triggered; AGENTS.md coverage>
  Action item: <...>

Layer 4 — The prompt and the retrieved context.
  Finding    : <was content stale / poisoned / inconsistent / wrong; the
               staleness or poisoning source; injection? (if not, say so)>
  Action item: <...>

Layer 5 — The model behaviour.
  Finding    : <given the prompt and context, did the model produce the output
               the system had reason to expect; is this a model-level issue
               or a context-level one?>
  Action item: <typically none at Layer 5 for this incident; if none, say
               so explicitly — the layer is still inspected>
```

The primary action should land at Layer 4 (staleness detection on retrieved context) and Layer 3 (HITL on pipeline column-aggregation changes + routing-matrix / review-checklist for critical-path flagging). Layer 5 should name explicitly that the model's behaviour was *context-faithful* (not confabulation) — the model did not hallucinate; it faithfully executed the stale context. This is a Chapter 4 Class 1 *"often mistaken for this class"* case where the fix is stale-context detection, not citation-tightening.

### Step 4 — Answer the five systemic questions (15 min)

In `lab-02-rewrites.md`, answer each of Chapter 3's five systemic questions with a specific "which artifact / who owns / where it lands" answer. The template:

```
Q1 — Standard.
  Was there a review standard for this class of artifact?  <Y/N>
  Was it followed?                                           <Y/N>
  Which mod-103 Ch. 2 row changes?                           <specific row>
  Owner, date.

Q2 — Standards-as-code.
  Did the standards-as-code stack enforce the checklist subset here?  <Y/N>
  Which mod-103 Ch. 3 artifact changes?                               <specific
   artifact — AGENTS.md section, Cursor rule, lint policy, ADR rule>
  Owner, date.

Q3 — Eval.
  Did a commissioned eval cover this regression?  <Y/N>
  What is the mod-103 Ch. 4 eval brief for the new eval?  <golden task /
   mutation test / LLM-as-judge rubric — specific, demonstrates red-to-green>
  Owner (likely ai-risk-engineer per Chapter 5 if method requires it), date.

Q4 — Routing / HITL / tool-authorisation.
  Which mod-106 artifact is being amended?  <routing matrix, HITL checkpoint,
   tool-authorisation, AGENTS.md — specify which + the change>
  Owner, date.

Q5 — Contract.
  Does the mod-103 Ch. 5 contract need amendment?  <Y/N>
  If no amendment: what change-log entry is filed?  <one line>
  If yes: which of C1 / C2 / C3 / C4 / C5 changes, and what?
  Owner, date.
```

Chapter 3 is explicit that *"an incident whose write-up does not answer any of the five questions has not closed the loop; an incident whose write-up answers all five with 'no change needed' is either very small or has not been engaged with seriously."* This incident is not very small; expect at least four of the five to have a specific destination.

### Step 5 — Compare against the answer key (15 min)

Read the key below only after Steps 2, 3, and 4 are complete.

#### Answer key — the six sentence rewrites

**Sentence 1 — "The model hallucinated the column-aggregation logic..."**

- *Violation.* Layer-5 stop-word (Chapter 3 *"stopping at 'the model hallucinated'"*) **plus** a misdiagnosis: the model did not hallucinate — it faithfully executed what the stale `column-mapping.yaml` told it. Chapter 4 names this as a case *"often mistaken for this class"* — a stale-context Class 1, not a confabulation Class 1.
- *Rewrite.* "Given the stale `column-mapping.yaml` (last modified 2026-05-14; the schema migration on 2026-09-02 renamed `volume_units` → `volume_units_scaled` but did not update this mapping file), and given the prompt asking for aggregation on `volume_units`, the model produced a parser edit that aggregated on `volume_units` — faithful to the stale context. This is a stale-context Layer-4 finding, not Layer-5 confabulation. The Chapter 4 class is Class 1 hallucination-driven-harm, specifically context-faithful."

**Sentence 2 — "The agent decided to use the un-scaled column because it thought that was the canonical one."**

- *Violation.* Anthropomorphising the agent (Chapter 3 *"the post-mortem never says 'the agent decided to...' or 'the agent thought...'"*). Sneaks blame onto the model; de-humanises the systemic finding.
- *Rewrite.* "Given the prompt's reference to `volume_units` and the retrieved `column-mapping.yaml` naming `volume_units` as the aggregation column, the agent produced an edit using `volume_units`. No 'decision' or 'belief' is attributed to the agent; the systemic finding is that the retrieval context was out of sync with the actual upstream schema post-migration."

**Sentence 3 — "The reviewer missed it. The reviewer approved the PR in three minutes without opening the test output. If the reviewer had been more careful this would not have shipped."**

- *Violation.* First-story framing with individual-blame counterfactual (Chapter 3 *"attributing fault to an individual"*). The *"if the reviewer had been more careful"* counterfactual is exactly what Allspaw's "second story" discipline is designed to replace.
- *Rewrite.* "Layer 1. The reviewer approved the PR at 18:40 Thursday with review queue depth of 27 open reviews. The checklist (v3.2) in effect required *'tests pass + change touches no critical path'*; pipeline column-aggregation changes are not currently flagged as critical path on the checklist, so the checklist did not direct additional scrutiny. CI was green (the stale tests also referenced `volume_units`, so they passed). Second story: the reviewer was operating under a checklist that did not surface this class of change as critical and a test suite that was consistent with the stale context, which made the diff appear routine. Finding: the checklist's critical-path classification does not cover AI-authored pipeline column-aggregation changes; the test suite's coverage does not detect the post-migration column-rename class. Action item: add the critical-path row to the review checklist (mod-103 Ch. 2) and the schema-vs-mapping staleness check to the agent's retrieval configuration (mod-106 Ch. 6)."

**Sentence 4 — "Also, the IC's prompt was sloppy — the IC should have been more specific about which column the aggregation targets."**

- *Violation.* First-story framing with individual-character attribution (*"sloppy"*). Also suggests the fix is "tell the IC to prompt better," which is a performance-review tone creeping into the post-mortem (Chapter 3 *"the separation from performance management"*).
- *Rewrite.* "Layer 2. The IC's prompt referenced `volume_units` because that was the column name in the mapping file they consulted during the task. The IC did not spot-check the agent's output against the live schema before submitting; the IC's workflow did not include spot-checks for post-migration column references. Second story: the IC was operating against the same stale `column-mapping.yaml` the agent consulted, which produced a consistent-looking end-to-end flow. Finding: the IC's workflow lacks a cheap prompt-time schema-check; this is a mod-106 Chapter 4 HITL-checkpoint candidate for pipeline column-aggregation changes (require the agent to produce a diff-vs-prior-run snapshot before human review). The IC's prompt is not the root cause; the absence of the HITL checkpoint is."

**Sentence 5 — "Reviewer to be more careful on AI-authored PRs."**

- *Violation.* Vague action item that cannot become a backfeed ticket per Chapter 6 (no destination artifact, no owner-as-person, no close-out criterion). Also re-introduces individual blame as a "fix."
- *Rewrite.* "Action item: add row 14 to `/docs/ai-review-checklist.md` — *'AI-authored pipeline column-aggregation changes include a diff-vs-prior-run snapshot in the PR; reviewer must open the snapshot and verify column names against the live upstream schema.'* Owner: team manager. Close-out criterion: PR merged with the new row; next AI-authored pipeline PR exercises the row. Date: two weeks from post-mortem."

**Sentence 6 — "What went wrong: the model made a wrong call and the reviewer did not catch it. We need to not trust the agent as much on pipeline work."**

- *Violation.* Collapses Layers 1 + 5 into a single first-story + Layer-5 stop-word framing, and the "not trust the agent as much" conclusion is a *routing decision expressed in moral language* when the correct frame is a routing-matrix / HITL decision per mod-106. Chapter 3 is explicit: *"blameless does not mean actionless — no individual punishment, yes systemic change."*
- *Rewrite.* "What went wrong: a post-schema-migration column rename (`volume_units` → `volume_units_scaled`) was not propagated to the retrieval configuration's `column-mapping.yaml`, the test suite's expected-column assertions, or the review-checklist's critical-path classification for pipeline aggregation changes. The agent faithfully executed the stale context; the review process, which was consistent with the stale context, approved without additional scrutiny. The systemic action is a staleness-detection layer on retrieved context (Layer 4 fix), a HITL checkpoint on pipeline column-aggregation changes (Layer 3 fix), a checklist row flagging this class as critical path (standard fix), and a canary eval that catches post-migration column drift (eval fix). 'Not trusting the agent on pipeline work' is a routing-matrix question (mod-106 Ch. 2) that this incident does not independently justify — the fix is at Layer 3 / Layer 4, not at the routing level."

#### Answer key — the fault-chain walk

**Layer 1 — The human reviewer.** Second story: the reviewer approved at 18:40 Thursday under a review queue depth of 27 open reviews; CI was green; the checklist (v3.2) required *"tests pass + change touches no critical path,"* and pipeline column-aggregation is not currently on the critical-path list; the test suite was itself consistent with the stale context so the green-tests signal did not help. Finding (systemic): the checklist does not direct additional scrutiny on AI-authored pipeline aggregation changes, and the test suite's coverage does not detect post-migration column-rename drift. Action item: review-checklist row 14 (critical-path row for AI-authored pipeline column-aggregation changes requiring a diff-vs-prior-run snapshot).

**Layer 2 — The human IC (prompter).** Second story: the IC's prompt referenced `volume_units` because the mapping file the IC consulted during the task still names that column; the IC's workflow does not currently include a schema-check step for post-migration column references. Finding: the IC was operating on the same stale context the agent was operating on, which is a system-design finding (both humans and agents consulting the same stale file), not an IC-character finding. Action item: HITL checkpoint before pipeline column-aggregation changes reach review (mod-106 Chapter 4) — the agent produces the diff-vs-prior-run snapshot that both the IC and the reviewer must examine.

**Layer 3 — The agent harness and policy.** Finding: no HITL checkpoint existed for pipeline column-aggregation changes in the mod-106 Chapter 4 checkpoint set — the checkpoint set was authored for workflows where the human reviewer is the primary catch, and this class does not surface to the reviewer in a way that a human catches without a tool. The harness did not flag the staleness of `column-mapping.yaml` because the harness has no staleness signal in scope. Action items: add a mid-run gate HITL checkpoint for pipeline aggregation changes (mod-106 Ch. 4); update the harness's retrieval configuration to compare the `column-mapping.yaml` `last-modified` against the upstream schema's `last-modified` and flag the stale condition to the agent (mod-106 Ch. 6).

**Layer 4 — The prompt and the retrieved context.** Finding: `column-mapping.yaml` was last modified 2026-05-14 and references the pre-migration `volume_units` column; the actual upstream schema changed to `volume_units_scaled` on 2026-09-02; the staleness was not flagged to the agent or to the IC. The prompt did not include an explicit "verify column names against the live schema" instruction, and the retrieval configuration had no staleness check. This is the primary root-cause layer. Action item: staleness-signal in the retrieval configuration (Layer 3 + Layer 4 joint fix).

**Layer 5 — The model behaviour.** Finding: given the prompt and the stale context in Layer 4, the model produced an output that was *correct relative to the stale context* — the model faithfully executed what the mapping file implied. This is a Chapter 4 Class 1 case of the *"often mistaken for this class"* kind — a stale-context failure, not a confabulation failure. **No Layer 5 action item is warranted.** The fix is at Layer 3 and Layer 4 (policy + context); the model's behaviour under the correct context is not in question. (A reproduction by `ai-risk-engineer` against the current schema would confirm the model behaves correctly post-fix; the reproduction is a verification artifact, not an action item on the model itself.)

#### Answer key — the five systemic questions

- **Q1 Standard.** *Was there a review standard?* Yes (checklist v3.2). *Was it followed?* Yes. *Which row changes?* New row 14 — *"AI-authored pipeline column-aggregation changes include a diff-vs-prior-run snapshot in the PR; reviewer must open the snapshot and verify column names against the live upstream schema."* Owner: team manager. Date: +2 weeks.
- **Q2 Standards-as-code.** *Did the stack enforce the checklist subset?* No section currently. *Which artifact changes?* New AGENTS.md section on staleness detection in retrieval: *"when retrieving mapping files or schema documents, compare the file's `last-modified` against the referenced upstream schema's `last-modified`; surface a staleness warning to the user and refuse to proceed without confirmation when staleness > 30 days."* Owner: senior IC on the platform team. Date: +3 weeks.
- **Q3 Eval.** *Did a commissioned eval cover this?* No. *Eval brief:* a golden-task mutation test that renames a column in a fixture schema and runs the agent against the fixture mapping file, verifying the agent either (a) uses the new name or (b) raises a staleness warning. The test lands red (reproduces the incident) → the fix lands green (Layer 3 + Layer 4 fix) → the row goes into the regression gate. Owner: `ai-risk-engineer` (method requires the fixture framework the engineer maintains per Chapter 5). Date: +5 weeks.
- **Q4 Routing / HITL / tool-authorisation.** *Routing-matrix amendment?* Not warranted — the routing (AI-first for pipeline changes) is not independently wrong; the fix is at the HITL / retrieval layer. *HITL checkpoint?* New checkpoint in mod-106 Ch. 4 — *"pipeline column-aggregation changes trigger a mid-run gate requiring the agent to produce a diff-vs-prior-run snapshot before submitting the PR."* Owner: senior IC. Date: +3 weeks. *Tool-authorisation?* No change; the authorisation surface is correct.
- **Q5 Contract.** *Contract amendment?* No — C1 (AI may draft pipeline changes) is correct; C2 verification bar is being tightened via the checklist row and the HITL addition. *Change-log entry:* *"2026-11-14: verification bar tightened — AI-authored pipeline column-aggregation changes now require a diff-vs-prior-run snapshot and a HITL checkpoint before reviewer-approval; related: staleness detection added to retrieval config."* Owner: team manager (the contract's authored owner). Date: same week as post-mortem publication.

### Step 6 — Diagnose your drift (10 min)

Compare your rewrites, your fault-chain walk, and your five-question answers against the key. For each miss, write one paragraph:

- **If any of your rewrites preserved "the model hallucinated" or "the agent decided / thought":** re-read Chapter 3's *"Common failure modes"* (specifically *"stopping at 'the model hallucinated'"*) and *"Counterfactual narration"* (the factual-narration discipline for the agent). The specific drift to catch: writing a *smoother* version of anthropomorphising (e.g., *"the agent's reasoning led it to..."*) instead of a *factual* version (*"given X, the agent produced Y"*). Linguistic precision, not euphemism.
- **If your Layer 5 finding was a Layer-5 action item:** the model's behaviour under the actual (post-fix) context was never in question; the whole incident is a Layer 3 + Layer 4 story. A Layer 5 action item here is a sign you have missed the stale-context diagnosis and are still running on the "model hallucinated" draft framing.
- **If you preserved any variant of "the reviewer missed it" or "the IC was sloppy":** Chapter 3's *"attributing fault to an individual"* failure mode is the single most common contamination of the blameless frame. The second-story discipline reconstructs what the operator was *operating under*, not what they *should have done*. If your rewrite still contains an implicit counterfactual aimed at the individual, it has not landed the systemic frame.
- **If your Section 7 action items read as "be more careful" or "write better prompts":** these are vague by Chapter 6's ticket-shape standard and are performance-conversation leakage by Chapter 3's separation-from-performance-management discipline. The correct shape is *destination-artifact + named-owner + close-out-criterion + date* (Lab 03 is the full conversion).
- **If your five-question answers all have "no change needed":** Chapter 3 is explicit that *"an incident whose write-up answers all five with 'no change needed' is either very small or has not been engaged with seriously."* This incident is not small; you have under-walked.
- **If your rewrite of Sentence 6 recommends "not trusting the agent" as a routing decision:** this collapses a mod-106 Chapter 2 routing-matrix question (*which workflows route AI-first vs. paired-review vs. human-first*) into a vague posture of distrust. Routing decisions are specific; distrust is not a backfeed destination. The correct action is the HITL and retrieval fixes at Layer 3 / Layer 4 — not a routing-matrix amendment this incident does not independently justify.

## Expected output

A file `lab-02-rewrites.md`, roughly 3–4 pages, containing:

- Six sentence-rewrite blocks in the Step 2 template.
- Five fault-chain-walk paragraphs in the Step 3 template.
- Five systemic-question answers in the Step 4 template.
- A diagnostic paragraph per drift against the key.

Something like:

```
Sentence 3 — "The reviewer missed it..."
  Violation : first-story framing + individual-blame counterfactual
  Rewrite   : "Layer 1. The reviewer approved at 18:40 Thursday under
              queue depth 27; checklist v3.2 required 'tests pass + no
              critical path,' and pipeline column-aggregation isn't flagged
              as critical path; tests were green because they also referenced
              the pre-migration column. Second story: the reviewer was
              operating under a checklist that did not direct scrutiny on
              this class of change and a test suite that was consistent
              with the stale context. Finding (systemic): checklist's
              critical-path classification doesn't cover AI-authored
              pipeline aggregation changes; test suite does not detect
              post-migration column-rename drift."
  ✅ match.

Layer 4 — The prompt and the retrieved context.
  Finding    : column-mapping.yaml last modified 2026-05-14, pre-migration;
               schema moved to volume_units_scaled on 2026-09-02; staleness
               not flagged. PRIMARY root-cause layer for this incident.
  Action item: staleness-signal on retrieval config (joint with Layer 3).
  ✅ match.

Layer 5 — The model behaviour.
  Finding    : given prompt + stale context, model produced the stale-
               consistent output. Context-faithful, NOT confabulation —
               stale-context Class 1 per Ch. 4's "often mistaken" note.
  Action item: NONE at Layer 5; verification reproduction by ai-risk-
               engineer is a verification artifact, not a model-level fix.
  ✅ match.

Drift notes:
  My first-pass Sentence 2 rewrite was "the agent's retrieval-aware behaviour
  led it to..." — still anthropomorphising in a smoother wrapper. Re-read
  Ch. 3 counterfactual-narration section: the discipline is FACTUAL ("given
  X, the agent produced Y"), not SMOOTHER. Fixed second pass.
```

## Checkpoint

Before moving on to [Lab 03](lab-03-backfeed-ticket-conversion-from-a-post-mortem.md) (converting a post-mortem's Section 7 into Chapter 6 backfeed tickets) or [Exercise 02](../exercises/exercise-02-blameless-postmortem-adapted-for-ai.md) (authoring a full post-mortem on a seeded or real incident), you should be able to answer **yes** to all six:

- Did you diagnose the incident as a **stale-context** Class 1 (Chapter 4's *"often mistaken for this class"* case), not as confabulation, so Layer 4 is the primary root-cause layer and Layer 5 has no action item?
- Did every rewrite remove anthropomorphising language ("the agent decided / thought / chose") in favour of factual narration ("given X, the agent produced Y") — not smoother anthropomorphising?
- Did every rewrite of a first-story sentence ("the reviewer missed it", "the IC was sloppy") land a *second-story* reconstruction of what the human was operating under, and a *systemic* finding of what the system allowed to look routine?
- Did your fault-chain walk reach a primary finding at Layer 3 or Layer 4 (HITL + retrieval staleness), not at Layer 5?
- Do your five systemic-question answers each name a **specific destination artifact** (which file / which checklist row / which AGENTS.md section / which eval row), a **named human owner**, and a **date** — not a free-text "we will"?
- Did you resist the two performance-contamination drifts — (a) the Sentence 5 "reviewer to be more careful" vagueness, (b) the Sentence 6 "not trust the agent as much" distrust-as-fix framing — in favour of specific HITL / checklist / eval / staleness-detection artifacts?

If any answer is no, re-read Chapter 3 *"Common failure modes"* end-to-end, and re-run Step 2 before authoring Exercise 02 on a real-stakeholder incident.
