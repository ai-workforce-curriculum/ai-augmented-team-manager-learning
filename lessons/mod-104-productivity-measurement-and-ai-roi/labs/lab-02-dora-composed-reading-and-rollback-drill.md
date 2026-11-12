# Lab 02 — DORA Composed Reading and Rollback-Trigger Drill

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 3 (DORA under AI-augmented conditions; the two caveats on throughput and change failure rate; the "shipped more, broke no more" vs "appearances vs reality" compositions; recovery time as a leading indicator), Chapter 6 (the four rollback triggers; adoption vs activation), Chapter 7 (the one-pager's Section 4 "risks and what we got wrong"; the three decisions continue / grow / roll back), with a side-check against Chapter 8 (the four quant-vs-qual patterns).
**Complements, does not duplicate:** Exercise 04 asks you to author your real team's AI-ROI one-pager for one real quarter. Exercise 06 asks you to produce your real team's rollback-criteria document. This lab gives you four fixed quarterly snapshots for a fictional team and asks you to read each snapshot against the Chapter-3 composition patterns, check each against the Chapter-6 rollback triggers, assign the Chapter-7 decision, and write the Section-4 paragraph for one of them. You run the reading drill on a pre-scored input here so you can calibrate your pattern-recognition before you write under real review-cycle pressure.

## Objective

Read four quarterly snapshots of a fictional team's DORA + cost + qualitative signal. For each snapshot: (a) name the Chapter-3 composition pattern (A "shipped more, broke no more" vs B "appearances vs reality" vs a non-standard pattern you name), (b) list every Chapter-6 rollback trigger that has fired or is near-firing, (c) assign the Chapter-7 decision (continue / grow / roll back a specific thing), (d) name the Chapter-8 quant-vs-qual pattern. Then rewrite one quarter's Section 4 ("Risks and what we got wrong") in Chapter 7's shape. Target: **you match the answer key on composition pattern and decision for at least three of the four quarters**, and your Section-4 rewrite names at least one specific miss in dated, non-softening language.

## Prerequisites

- Chapter 3 read end-to-end (the four keys; the three caveats; Composition A vs Composition B; what *doesn't* change about DORA; common mistakes).
- Chapter 6 read end-to-end (the three cost components; adoption vs activation; the four rollback triggers; the two paragraphs on tried-and-stopped as diagnostic).
- Chapter 7 read end-to-end (the three decisions; the five sections; what *not* to put on the one-pager; the "what we got wrong" retro).
- Chapter 8 skimmed (so you can name the four quant-vs-qual patterns on the fourth snapshot).
- A blank file for your diagnosis and the Section-4 rewrite.
- A timer.

Optional but useful: Chapter 5 skimmed (so you can flag where the fourth snapshot's workstream pattern maps to a Dell'Acqua frontier reading).

## The fictional context

> **"Scheduling Core" team, HealthRouting Medical Software.** 14 engineers (1 staff, 3 senior, 10 mid/junior). Owns the scheduling engine used by the company's two flagship products (clinic-side scheduling + patient-facing booking). Agents in use: Copilot Business (14 seats; Q1 adoption), Claude Code via team gateway (usage-based; Q2 rollout), Cursor Pro (6 seats; Q3 pilot on the frontend-heavy patient-booking repo). Horizon: Q4 close of 2026; decision cycle is quarterly. The team's rollback-criteria document (Chapter 6, Exercise 06) is the four defaults: *activation below 30% for two consecutive quarters; cost ratio rising while Quality tile flat; change failure rate rising with agent-attributable incidents; qualitative / quantitative divergence for two consecutive cycles*. The DORA definition of "change failure" in the data-dictionary is the Chapter-3 broadened definition (any rollback / any hotfix ≤ 24h / any S2+ incident attributed to the deploy, independent of who filed it).

## The four quarterly snapshots

Read all four end-to-end before taking notes. Each snapshot is the Monday-pre-read-level summary a manager would carry into the Q-review.

### Snapshot Q1 (post-Copilot rollout)

```
DORA
  Deployment frequency     median 2.4 / engineer / week   (Q0: 2.1)
  Lead time for changes    median 2.3 days                (Q0: 2.8)
                           90th   7.1 days                (Q0: 8.4)
  Change failure rate      11%  (broadened definition)    (Q0: 11%)
  Recovery time            median 1.3 h                   (Q0: 1.3)

Cost
  Combined AI tool-spend $1,210 / 100 PRs merged (first measurement)
  Fraction of fully-loaded eng cost: 0.9%

Adoption / activation
  Copilot adoption 100% (14/14)
  Copilot activation (material-use): 71% (10/14)
  "Tried-and-stopped": 1 engineer (data-adjacent workstream)

Qualitative
  Pulse survey (12/14 respondents, 86%):
    "AI helped me ship my most meaningful work" = 3.9 / 5
    Tenure segmentation: early 4.2, mid 3.9, senior 3.5
    "Felt pressure to use AI tooling for work where it did not help" = 2.0 / 5
  Retro themes: review-latency as top bottleneck (4 mentions);
    PR-description quality markedly improved (5 mentions).
```

### Snapshot Q2 (post-Claude Code rollout)

```
DORA
  Deployment frequency     median 2.9 / engineer / week   (Q1: 2.4)
  Lead time for changes    median 1.9 days                (Q1: 2.3)
                           90th   6.8 days                (Q1: 7.1)
  Change failure rate      14%  (broadened definition)    (Q1: 11%)
  Recovery time            median 1.5 h                   (Q1: 1.3)
                           two S2 incidents in weeks 7 and 10, both
                           on agent-drafted feature-flag changes

Cost
  Combined AI tool-spend $1,640 / 100 PRs merged           (Q1: $1,210)
  Fraction of fully-loaded eng cost: 1.3%

Adoption / activation
  Copilot activation (material-use): 71% (10/14) flat
  Claude Code adoption: 93% (13/14); activation 64% (9/14)
  "Tried-and-stopped": 2 engineers total, both on data-adjacent workstreams

Qualitative
  Pulse survey (11/14 respondents, 79%):
    "AI helped me ship my most meaningful work" = 4.0 / 5   (Q1: 3.9)
    Tenure segmentation: early 4.4, mid 4.1, senior 3.3
    "Felt pressure to use AI tooling for work where it did not help" = 2.4 / 5  (Q1: 2.0)
  Retro themes: feature-flag change review as emerging risk (3 mentions);
    the two S2 incidents raised by multiple ICs as a review-bar concern (5 mentions).
```

### Snapshot Q3 (post-Cursor pilot on patient-booking)

```
DORA
  Deployment frequency     median 3.1 / engineer / week   (Q2: 2.9)
  Lead time for changes    median 1.8 days                (Q2: 1.9)
                           90th   6.4 days                (Q2: 6.8)
  Change failure rate      11%  (broadened definition)    (Q2: 14%)
  Recovery time            median 1.3 h                   (Q2: 1.5)
                           zero S2 incidents attributed to agent-drafted
                           changes this quarter (Chapter-3 Caveat-2
                           broadened definition applied consistently)

Cost
  Combined AI tool-spend $1,590 / 100 PRs merged           (Q2: $1,640)
  Fraction of fully-loaded eng cost: 1.3%

Adoption / activation
  Copilot activation (material-use): 71% (10/14) flat
  Claude Code activation: 71% (10/14)  (Q2: 64%)
  Cursor pilot: adoption 6/6 on patient-booking subteam; activation 5/6
  "Tried-and-stopped": 1 engineer (data-adjacent workstream)

Qualitative
  Pulse survey (12/14 respondents, 86%):
    "AI helped me ship my most meaningful work" = 4.2 / 5   (Q2: 4.0)
    Tenure segmentation: early 4.5, mid 4.3, senior 3.6
    "Felt pressure to use AI tooling for work where it did not help" = 1.9 / 5  (Q2: 2.4)
    "Confidence in review bar for AI-generated work" = 4.0 / 5   (new)
  Retro themes: mod-103 review-checklist v0.2 landed week 2, credited
    by 7 ICs with the CFR improvement; patient-booking Cursor pilot
    rated strongly by 5 of 6 engineers.
```

### Snapshot Q4 (data-pipeline workstream, Cursor rollout to full team)

```
DORA
  Deployment frequency     median 3.0 / engineer / week   (Q3: 3.1)
  Lead time for changes    median 1.9 days                (Q3: 1.8)
                           90th   6.6 days                (Q3: 6.4)
  Change failure rate      12%  (broadened definition)    (Q3: 11%)
  Recovery time            median 1.4 h                   (Q3: 1.3)

Cost
  Combined AI tool-spend $1,910 / 100 PRs merged           (Q3: $1,590)
  Fraction of fully-loaded eng cost: 1.6%

Adoption / activation
  Copilot activation (material-use): 71% (10/14)
  Claude Code activation: 71% (10/14)
  Cursor adoption extended to full team (14/14); activation 43% (6/14)
    — of the 8 non-activated, 4 are on the data-adjacent workstreams
      and 2 are the "tried-and-stopped" cohort from Q2 and Q3 (still)
  Rolling activation on Cursor across Q3 + Q4 (two quarters): 46% average

Qualitative
  Pulse survey (10/14 respondents, 71% — response-rate DOWN):
    "AI helped me ship my most meaningful work" = 3.9 / 5    (Q3: 4.2)
    Tenure segmentation: early 4.4, mid 4.2, senior 2.9  (senior ↓ sharply)
    "Felt pressure to use AI tooling for work where it did not help" = 3.2 / 5  (Q3: 1.9)
    "Confidence in review bar for AI-generated work" = 3.8 / 5  (Q3: 4.0)
  Retro themes (across the two Q4 retros):
    data-pipeline Cursor fit poor (6 mentions — second consecutive quarter);
    senior-cohort skill-atrophy concern (3 mentions — new);
    "pressure to appear AI-fluent at promotion time" (2 mentions — new).
```

## Steps

### Step 1 — Set up your diagnosis memo (3 min)

Create a working file `lab-02-dora-reading.md`. Add this header:

```
# Lab 02 — DORA composed reading and rollback drill (Scheduling Core)

Chapter 3 compositions:
  A  "shipped more, broke no more"   — frequency ↑, CFR flat-or-↓, cost ↑
  B  "appearances vs reality"        — frequency ↑, CFR ↑, recovery ↑
  (or a non-standard pattern you name explicitly)

Chapter 6 rollback triggers:
  R1  activation < 30% for two consecutive quarters
  R2  cost ratio ↑ while Quality tile flat
  R3  CFR ↑ with agent-attributable incidents
  R4  qual / quant divergence for two consecutive cycles

Chapter 7 decisions:
  continue / grow (specify what) / roll back (specify what)

Chapter 8 patterns:
  P1 aligned-up / P2 quant↑ qual flat / P3 quant flat qual↓ / P4 quant↓ qual↑

For each quarter, record:
  (a) composition pattern + 1-line evidence,
  (b) rollback triggers fired or near-firing + 1-line evidence,
  (c) decision asked (continue/grow/roll-back) + the specific thing,
  (d) Chapter 8 pattern + 1-line evidence.
```

### Step 2 — Diagnose each snapshot (25–30 min)

Work through Q1, Q2, Q3, Q4 in order. **Target: no more than 7 minutes per quarter.** Do not scroll to the answer key until all four are done. For each quarter, write the four items from the header above.

Specific prompts to help:

- **Q1.** Frequency and lead-time both improved; CFR flat; recovery flat; qualitative aligned-up with modest senior-cohort tenure gap. Which composition pattern? Any rollback triggers on the Chapter-6 list? What is the decision ask?
- **Q2.** Frequency, lead-time, *and* CFR all moved — in which combination? The two S2 incidents on agent-drafted feature-flag changes — which Chapter-3 caveat does this specifically map to? The qualitative "pressure" number ticked up by 0.4 — is this a Chapter-8 pattern?
- **Q3.** CFR improved; recovery improved; cost ratio flat-to-down; qualitative aligned-up; the mod-103 review-checklist v0.2 landed. Which composition pattern — and what does Chapter 7 say about *not celebrating the first-quarter improvement* in a way that applies here? Which decision?
- **Q4.** Frequency and quality both held; cost ratio rose sharply; Cursor activation on the full team is 43% (single quarter) and the rolling two-quarter average is 46%. The senior-cohort pulse dropped from 3.6 to 2.9; the "pressure" number jumped from 1.9 to 3.2. Response rate dropped. Which rollback triggers fire or near-fire? Which Chapter-8 pattern (hint: check all four, not just the obvious one)? What is the decision — and what specifically is being rolled back?

### Step 3 — Compare against the answer key (10 min)

Below is the answer key. For each quarter, check whether your diagnosis matches. Count hits (same composition + same decision) and near-misses (correct composition but different decision, or vice versa).

#### Answer key — four quarters

**Q1 — Composition A ("shipped more, broke no more"), decision: continue, no rollback trigger near-firing, Chapter-8 Pattern 1 (aligned-up) with a watch note on the senior-tenure gap.**

Frequency ↑, lead-time ↓, CFR flat at 11%, recovery flat, cost ratio first-time measurement (baseline, not trend). Qualitative aligned-up with tenure segmentation consistent with Brynjolfsson literature (early-tenure benefits most). No rollback trigger fired; the one "tried-and-stopped" engineer is a Chapter-6 diagnostic signal to raise in the next 1:1, not a rollout failure. The one-pager's decision ask: continue the Copilot investment; schedule the Q2 Claude Code rollout as planned. Watch note: the senior-cohort pulse (3.5) is lower than early and mid; this is the expected Brynjolfsson pattern but worth surfacing in the Chapter-8 qualitative narrative.

**Q2 — Composition B ("appearances vs reality"), decision: continue but hold the Claude Code expansion; Chapter-3 Caveat 2 and Caveat 3 both apply; Chapter-8 Pattern 2 (quant ↑ qual flat with a specific emerging concern).**

Frequency ↑, lead-time ↓ — but CFR rose from 11% to 14% and recovery ticked from 1.3 to 1.5 hours with two S2 incidents on agent-drafted feature-flag changes (Chapter 3 Caveat 3: "agent-drafted changes often touch surface area the author does not know is risky — config files, feature-flag definitions"). Chapter 3 is explicit: "a team shipping faster that is also shipping more broken is almost always revealing a review-bar failure (`mod-103`), not an inherent AI trade-off." The qualitative "pressure" number ticking up (2.0 → 2.4) with retro themes naming feature-flag review as emerging risk is Chapter-8 Pattern 2 with an action item (the review-bar intervention). No Chapter-6 rollback trigger has fired yet — R3 is *near-firing* (CFR rose once; agent-attributable incidents identified). Decision: continue baseline, hold Claude Code expansion into new workstreams until the review-bar intervention lands, commission the mod-103 checklist v0.2 for Q3. Not a rollback; an intervention. Chapter 7: "the measurement programme working." The common-mistake trap to avoid: celebrating lead-time improvement in Section 2 while Section 4 has not named the two S2 incidents.

**Q3 — Composition A (clean this time), decision: continue + grow (expand Cursor pilot to the full team based on patient-booking signal), Chapter-8 Pattern 1 (aligned-up).**

Frequency held high, lead-time edged down further, CFR recovered to 11% from Q2's 14% after the mod-103 review-checklist v0.2 landed, recovery back to 1.3 hours, zero S2 agent-attributable incidents, cost ratio ticked down slightly. Qualitative pulse rose to 4.2; pressure number dropped; new "confidence in review bar" item debuted at 4.0 — explicitly attributable by 7 ICs to the review-checklist work. This is the defensible AI-productivity story. Chapter 7's caveat applies: the one-pager should credit the mod-103 intervention explicitly (not the AI tooling alone) and should *not* claim a published-study-sized gain. The Cursor pilot on patient-booking rated strongly by 5 of 6 — Chapter 7 "grow" decision with a specific target (expand Cursor seat count onto the full team or onto the frontend-heavy workstreams, specifying which). No rollback trigger fired or near-firing. Chapter-5 note: this quarter's story is *consistent with* Noy & Zhang's quality-and-speed-together pattern on well-specified tasks, and Section 3 should cite the range honestly, not claim a 55% Peng-style number.

**Q4 — non-standard composition (quant flat-to-weak, cost ↑, qual segmented), multiple rollback triggers near-firing (R1 and R2), decision: ROLL BACK the Cursor-on-data-pipeline-workstream specifically; Chapter-8 Pattern 3 (quant flat, qual down) in the senior / data-pipeline cohort.**

This is the quarter the drill is designed around. Several things are moving simultaneously and the composition pattern is not A or B — it is a *flat* quantitative read with a *segmented* qualitative decline. The specific findings:

- **Rollback trigger R1 fired on Cursor-on-data-pipeline.** Cursor activation on the data-pipeline cohort is well under 30% across Q3 and Q4 (6/14 team-wide in Q4 is 43% but the 4 non-activated on data-pipeline + 2 chronically tried-and-stopped are specifically the cohort you expanded onto in Q4). Rolling two-quarter activation of 46% on Cursor is technically above 30%, so a naive reading says "no trigger fired" — but Chapter 6 is explicit that the segment matters, and the Chapter-6 "common-mistake" trap of "treating the tried-and-stopped cohort as a rollout problem" is the exact mistake the Q4 Cursor expansion made. The rollback target is the *data-pipeline expansion specifically*, not Cursor as a whole.
- **Rollback trigger R2 near-firing.** Cost ratio rose from $1,590 → $1,910 per 100 PRs merged (20% ↑ QoQ) while the Quality tile is flat and the Speed tile is flat. Chapter 6: "the spend is not landing on the product line (Flow Efficiency, Chapter 4)."
- **Rollback trigger R4 near-firing.** The senior pulse dropped 0.7 (3.6 → 2.9) and the pressure number jumped 1.3 (1.9 → 3.2); this is the first cycle of qual↓ quant-flat, but it is a *single* cycle so R4 ("for two consecutive cycles") has not technically fired. Chapter 8 names this as **Pattern 3** — the signal to catch early. The "senior-cohort skill-atrophy concern" and "pressure to appear AI-fluent at promotion time" are new themes; Chapter 8 names the second as the specific question the 1:1 instrument surfaces and the dashboard never will.
- **The response-rate drop** (86% → 71%) is itself a qualitative signal — engineers stopping responding to the pulse is Chapter-8 "instrument degrading" and should be named in the one-pager.
- **Chapter 5 Dell'Acqua reading.** The data-pipeline workstream repeatedly showing poor Cursor fit across Q2, Q3, and Q4 is the jagged-frontier pattern — pull back agent scope on outside-frontier workstreams rather than push training; the ICs have consistently identified the fit problem for three quarters.

Decision: **roll back Cursor on data-pipeline specifically** (narrow the pilot to the frontend / patient-booking workstreams that showed the Q3 Composition A signal); hold Copilot and Claude Code baseline; commission a dedicated qualitative-instrument review next quarter because R4 is on-watch; name the senior-cohort skill-atrophy concern as a `mod-107` hand-off in Section 5. Chapter 7: "Rollback is not a failure state; it is a legitimate outcome of the measurement programme working."

Count your hits. **Three or four correct on composition AND decision together is the pass bar**; two means a re-read of Chapter 3's composition patterns and Chapter 6's rollback triggers; one or zero means re-read Chapter 3 end-to-end and Chapter 6's "When to roll back" section.

### Step 4 — Rewrite Q4's Section 4 "Risks and what we got wrong" (15–20 min)

Pick Q4 and write the Chapter-7 Section-4 paragraph that would land honestly on the VP. Chapter 7 Section 4 is explicit:

- "One short paragraph, honest. Include at least one specific thing that went differently from Q-1's prediction, whether positively or negatively."
- Non-softening language. "Everything went well" is not acceptable.
- Named misses, dated, in the exec's vocabulary.

Use the Q3 one-pager's implied prediction — *"we expect the Cursor expansion to the full team in Q4 to show activation above 60% within the quarter based on the patient-booking pilot signal"* — as the Q-1 prediction to measure against.

Constraints on your rewrite:

- 5–8 sentences. One paragraph.
- Name the two S2 incidents from Q2 only if they are relevant to Q4's story (they are, as the review-bar backdrop against which the data-pipeline expansion was decided).
- Name the Q3 → Q4 activation delta specifically (48% / 43% / 46% rolling, not "activation disappointed").
- Name the rollback target specifically ("Cursor on the data-pipeline workstream") not vaguely ("the rollout").
- Name the senior-cohort pulse drop as a specific signal, not a sentiment.
- Credit the Q3 mod-103 intervention explicitly (it is part of the quarter-over-quarter story and relevant to the read).
- Do *not* reference the dashboard tiles — this is prose, not tile labels.

Example shape for one sentence (not a template to copy):

```
We expanded Cursor from the Q3 patient-booking pilot (strong signal,
5 of 6 engineers rating positively) to the full team in Q4; activation
on the data-pipeline cohort came in at 43% single-quarter / 46% rolling
across Q3+Q4, well below our implied 60% prediction, and the two
chronically-tried-and-stopped engineers we flagged in Q2 and Q3 did
not activate.
```

### Step 5 — Reconcile Q4's decision ask against Chapter 7's "what *not* to put on the one-pager" (5 min)

Write a 3–4 line reconciliation naming what your Section-4 rewrite and the Q4 decision ask *do not* include, with reference to Chapter 7's list:

- Not a chart of PR-count-per-engineer.
- Not a screenshot of the full dashboard.
- Not every empirical study you read.
- Not operational detail that belongs in the retro.
- Not hedged, non-committal language.

Example shape:

```
My Section 4 names the activation delta, the senior pulse drop, and
the specific rollback target (Cursor on data-pipeline). It does NOT
cite Peng et al.'s 55% number; that would belong in Section 3 as a
range against Brynjolfsson and Dell'Acqua, not here. It does NOT
describe the rollback mechanism at operational depth; that is retro
work (Exercise 06). It does NOT soften the 43% activation number;
"disappointed" is the hedge Chapter 7 names.
```

### Step 6 — Name the Q4 Chapter-8 next-cycle action (3 min)

Chapter 8 is explicit that Pattern 3 is the signal to catch early and that the qualitative instrument's job is to feed the narrative. Write one line on the specific Chapter-8 action for Q+1:

- The retro prompt set runs on 6-week cadence; the next retro should include the senior-cohort skill-atrophy theme as a specific prompt or follow-up.
- The 1:1 standing-question pair should be run with every senior IC in Q+1 rather than every 2nd or 3rd 1:1 (temporary cadence lift until the Pattern-3 signal is understood or dismissed).
- The pulse response-rate drop itself is an instrument-decay signal; the next pulse should be checked against the Chapter-8 "declaring the instrument working on the first run" common mistake and revised if response-rate drops further.

Pick one or two of the three and write a specific one-line action.

## Expected output

A single scratch file, roughly two pages, containing:

- A four-quarter diagnosis table with composition pattern, rollback triggers, decision, and Chapter-8 pattern per quarter — cross-referenced to the answer key (hit / near-miss / missed).
- A Chapter-7 Section-4 rewrite for Q4, 5–8 sentences.
- A 3–4 line reconciliation naming what the Section-4 rewrite does not include, with specific Chapter-7 anchors.
- A one-to-two line Chapter-8 next-cycle action for Q+1.

Something like:

```
Q2 diagnosis
  Composition: B ("appearances vs reality") — frequency ↑, CFR ↑ 11→14,
    recovery 1.3→1.5 with two S2 agent-attributable incidents.
  Rollback triggers: R3 near-firing (CFR ↑ with agent-attributable
    incidents, one cycle so far); R2 is *not* firing (cost ratio ↑
    but the Quality tile also moved — not a Chapter-6 R2 shape).
  Decision: continue baseline; hold Claude Code expansion; commission
    mod-103 review-checklist v0.2 for Q3 landing.
  Chapter-8 pattern: P2 (quant ↑ qual flat) with an emerging-concern
    theme on feature-flag review.
  ✅ match.
```

## Checkpoint

Before moving on to Exercises 04 and 06 (where you author **your real team's** one-pager for one real quarter and your rollback-criteria document), you should be able to answer **yes** to all five:

- Did you correctly identify Q1 and Q3 as Composition A, Q2 as Composition B, and Q4 as a non-standard "flat quant, segmented qual" shape that is not captured by A or B alone?
- Did you pin Q4's rollback decision to the *specific* target (Cursor on the data-pipeline workstream) rather than to "the AI investment" or "Cursor as a whole"?
- Did you name at least one Chapter-6 rollback trigger as near-firing on Q4 (R1 on the cohort-segmented reading, R2 on cost-flat-quality, R4 on qual↓ for one cycle) and *not* claim all four fired?
- Did your Q4 Section-4 rewrite include the 43% activation number, the senior pulse drop (3.6 → 2.9), and the specific rollback target — in dated, non-softening language — without citing an empirical study number that belongs in Section 3?
- Did your Q+1 Chapter-8 action name a specific instrument change (retro prompt, 1:1 cadence lift, or pulse response-rate check) rather than a general "do more qualitative work"?

If any answer is no, re-read Chapter 3's "Composing DORA with the rest of the dashboard" and the three Caveats, Chapter 6's "When to roll back the AI tool investment," and Chapter 7's "Section 4 — Risks and what we got wrong" and "What *not* to put on the one-pager," before authoring Exercise 04 and Exercise 06 for your real team.
