# Lab 01 — Programme Diagnostic on a Curated Enablement Plan

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 1 (three failure modes; author-vs-deliver division of labour), Chapter 2 (four checkpoints; cohort sizing and composition; anchoring to the engineer's join date; the three failure signatures), Chapter 3 (bootcamp vs workshop vs CoP; the three Wenger-Trayner structural elements; common first-assembly mistakes), with a side-check against Chapter 7 (the authoring-vs-delivery split in partner interfaces).
**Complements, does not duplicate:** Exercise 01 asks you to author a dated Day 0 / 30 / 60 / 90 plan for **your own** team. Exercise 04 asks you to author the community-of-practice charter for **your own** team. This lab hands you a fixed, deliberately broken enablement plan for a fictional team — a single-page document another manager drafted — so you can calibrate your diagnosis before you spend real authoring hours on your team. The exercises are authoring tasks; the lab is a diagnostic drill against a known answer key.

## Objective

Read a curated sample: (a) the fictional team's current enablement plan, (b) a one-paragraph director's note explaining why it was written the way it was, and (c) the two-line outcome the manager is reporting six weeks in. Identify every Chapter-1 failure mode, every Chapter-2 structural defect, and every Chapter-3 format mistake in the current plan. Then rewrite the three load-bearing sections (the cohort structure, the checkpoint timeline, the delivery-format mix) to the mod-105 four-checkpoint shape. Target: **you identify at least seven of the nine findings in the answer key**, and your rewrite produces a plan an incoming manager could run the next cohort from.

## Prerequisites

- Chapter 1 read end-to-end (the three failure modes; the author-vs-deliver division of labour).
- Chapter 2 read end-to-end (the four checkpoints; cohort size 3–6 mixed-stage-not-mixed-seniority; join-the-programme date anchoring; the three failure signatures).
- Chapter 3 read end-to-end (bootcamp / workshop / CoP; the three Wenger-Trayner elements; the common first-assembly mistakes).
- Chapter 7 skimmed (so you recognise the partnership-contract boundaries when the plan hands authoring off to L&D).
- A blank file for your audit memo and rewrites.
- A timer.

## The fictional context

> **"Platform Infra" team, Meridian Media.** 18 engineers (2 staff, 5 senior, 11 mid/junior). Owns the shared build / deploy / observability platform that four product teams consume. Agents in use: Cursor Pro (18 seats, provisioned Q4), Copilot Business (18 seats, provisioned 18 months ago), Claude Code via team gateway (usage-based, provisioned Q4). The team has one L&D partner (A. Rivera) allocated 20% to the team, a Platform partner who owns the Cursor enterprise contract org-wide, and an HRBP. The director inherited the enablement situation from her predecessor six weeks ago and drafted v0.1 of the plan below on a Sunday afternoon. Audience for this plan: the team itself, the L&D partner, and the VP of Engineering at the Q-review. This is the artifact under audit.

## The director's one-paragraph note (how we got here)

> *"We bought Cursor and Claude Code in Q4 to catch up with the market. The VP wants to see an enablement plan at the Q-review. I pulled together what I remembered from a conference talk I attended and what L&D has in their off-the-shelf curriculum. The one-pager is in two weeks; this is what I have."*

## The current enablement plan (v0.1)

Read the plan end-to-end before taking notes. Do not skip to the answer key.

### Plan v0.1 — Platform Infra AI Enablement, Q1 2026

> **Goal:** Make everyone on the Platform Infra team productive with Cursor and Claude Code by end of Q1.
>
> **Structure.** We will run a half-day Cursor bootcamp on 2026-01-15 for the whole team at the quarterly all-hands. A vendor trainer from Cursor will deliver all four sessions back-to-back (90 min each). Attendance is mandatory. L&D will own the agenda and record attendance in Workday Learning.
>
> **Cohorts.** The team will run as a single cohort of 18. Session groupings will be assigned at the door by seniority — staff + senior engineers in the first half-day session so they can model for the juniors who attend the second half-day session.
>
> **Checkpoints.** One checkpoint, at Day 30. The staff engineer will walk each engineer's Cursor acceptance-rate dashboard with them in a 15-minute 1:1 and flag anyone below 25%.
>
> **Tool budgets.** Staff and senior engineers get the Cursor "Business" tier plus unlimited Claude Code tokens. Mid-level and junior engineers get Cursor "Pro" and a 300k Claude Code token/month cap. This is Finance's recommendation.
>
> **Sustaining layer.** We have created a `#ai-practice` Slack channel. Engineers are encouraged to share wins there. Quarterly, we will book a "lunch and learn" with a different vendor from our stack to keep things fresh.
>
> **Measurement.** Success = 100% Cursor adoption by end of Q1 (defined as "logged in at least once per week"). The VP pre-read will carry adoption + Cursor acceptance rate + engineer-reported time saved from the DX pulse.
>
> **Partner interfaces.** L&D owns the curriculum end-to-end; the manager (me) owns the "exec narrative." HR will co-sign the Day-30 acceptance-rate sheets so engineers know this is tracked.
>
> **Research anchors.** Based on Bersin's finding that AI training produces 30% more capability and Microsoft's Work Trend Index data showing 70% of engineers are more productive with AI.

## The manager's six-weeks-in update (as currently drafted for the Q-review one-pager)

> *"Enablement is tracking well. 94% Cursor adoption (per-week logins). The January 15 bootcamp ran with full attendance. Four engineers are at risk per acceptance-rate dashboard. #ai-practice has 11 messages since launch. Based on industry research (Bersin 30%, Microsoft 70%) we project strong ROI next quarter and recommend full-team expansion of Cursor to the adjacent Developer Experience team under our ownership."*

## Steps

### Step 1 — Set up your audit memo (3 min)

Create a working file `lab-01-plan-diagnostic.md`. Add this header:

```
# Lab 01 — Programme diagnostic (Platform Infra, Q1)

Chapter 1 failure modes:
  F-A  One-shot workshop (vendor-run, no practice loop)
  F-B  Licence drop (seats allocated without cohort structure)
  F-C  Vanity bootcamp (100% attendance, no on-the-job artifacts)

Chapter 2 structural defects:
  S1   No four-checkpoint structure (Day 0 / 30 / 60 / 90)
  S2   Wrong cohort size or composition (3-6, mixed stage not seniority)
  S3   Not anchored to engineer's join-the-programme date
  S4   Day-30 checkpoint misread as performance signal (slippage)

Chapter 3 format mistakes:
  M1   Workshop-as-bootcamp or bootcamp-as-session
  M2   Vendor-roadshow drift (vendor runs whole bootcamp off-the-shelf)
  M3   CoP-as-launch-event or CoP-as-Slack-channel
  M4   Under-authoring (L&D hands manager the curriculum pen)

For each finding record: (a) which plan section, (b) which failure mode /
defect / mistake, (c) one line on what the plan is encouraging, (d) the
mod-105 rewrite target.
```

### Step 2 — Audit the plan section-by-section (25–30 min)

Work through the plan sections in order. For each, ask: *is this a Chapter-1 failure, a Chapter-2 defect, a Chapter-3 mistake, or load-bearing-but-thin?* Write one line per finding. Do not scroll to the answer key until you have at least six findings written down. **Target: no more than 4 minutes per section.**

Specifically, for each section:

- **"Structure" (the half-day Cursor bootcamp).** Which of Chapter 3's bootcamp invariants are violated? (Hint: concentrated, cohort-based, tool-specific, hands-on on real code — which are missing?) Which Chapter 1 failure does this compose with? Note the vendor-authoring issue and the attendance-is-mandatory signal.
- **"Cohorts" (one cohort of 18, grouped by seniority at the door).** Which Chapter 2 cohort guidance is violated? What does "grouped by seniority so seniors can model for juniors" encode as an assumption, and which research anchors (Chapter 4) does it contradict?
- **"Checkpoints" (one checkpoint, Day 30, acceptance-rate dashboard).** How many Chapter-2 checkpoints are missing? Which measurement is being used at Day 30 and what does Chapter 5 say about using a Copilot/Cursor acceptance-rate dashboard as the fluency-growth signal? What does "flag anyone below 25%" mis-read (hint: Chapter 2's "Day-30 PR slippage" diagnostic)?
- **"Tool budgets" (seniority-banded tiers + token cap on mid/junior).** Which Chapter 4 anti-pattern does this match in its purest form? What happens to the stage-1 staff engineer here (there is at least one, implied by the team's six-week-old provisioning)?
- **"Sustaining layer" (Slack channel + quarterly vendor lunch-and-learn).** Which of the three Wenger-Trayner structural elements are present vs. missing (Chapter 3)? Which Chapter 3 common mistake does the lunch-and-learn shape name explicitly?
- **"Measurement" (100% adoption + acceptance rate + self-reported time saved).** Which Chapter 1 and Chapter 5 guardrails does this violate? What is the correct fluency-growth measurement set per Chapter 5?
- **"Partner interfaces" (L&D owns curriculum; HR co-signs acceptance-rate sheets).** Which Chapter 1 / Chapter 7 boundary is violated by "L&D owns the curriculum end-to-end"? What does Chapter 7 specifically say about HR signatures on the stage-pin sheets?
- **"Research anchors" (Bersin 30% + Microsoft WTI 70%).** Which Chapter 6 common mistakes does the sentence combine? Does Bersin publish a quantitative comparative "X% more capability" number? Does WTI's "70%" survive the methodology caveats Chapter 6 names?

### Step 3 — Audit the manager's six-weeks-in update (5 min)

Separately from the plan, write a 4–6 line diagnosis of the update paragraph:

- Which Chapter 1 failure modes does the composite claim (adoption + acceptance + pulse) stack without naming the limits of each?
- Does the "Bersin 30% + Microsoft 70%" cite meet Chapter 6's responsible-citation bar?
- The sentence *"recommend full-team expansion of Cursor to the adjacent Developer Experience team under our ownership"* — per Chapter 8, which graduation trigger is this on the edge of, and what is the correct next artifact (hint: it is not "expand under our ownership")?

### Step 4 — Compare against the answer key (10 min)

Below is the answer key — nine findings. For each, check whether your audit found it. Count hits (same section, same finding) and near-misses (same section but different framing).

#### Answer key — nine findings

1. **"Structure" is Failure A (one-shot workshop) + Failure C (vanity bootcamp) + Chapter 3's vendor-roadshow-drift mistake simultaneously.** A half-day event at the all-hands, delivered by a vendor trainer running four 90-minute sessions off-the-shelf, with 100% mandatory attendance and no follow-up practice loop, is Chapter 1 Failure A ("the programme is a half-day vendor-led Copilot demo … nobody's workflow changes the following Monday because there is no practice loop behind the demo") and Failure C ("three-day bootcamp with no pre-work, no post-work, and no on-the-job artifacts") compressed into one event. It is also Chapter 3's "vendor-roadshow drift" explicitly — "letting the three tool vendors on your team's stack each run their own bootcamp." Rewrite target: replace the half-day with the Chapter 2 Day 0 / 30 / 60 / 90 structure delivered to 3–6-engineer cohorts over 90 days; vendor trainer may run *one* session per cohort, pre-briefed by the manager (Chapter 7's vendor-trainer slot). The curriculum stays with the manager.

2. **"Cohorts" of 18 grouped by seniority is a double Chapter-2 defect.** Chapter 2's cohort sweet spot is 3–6 (so every engineer can speak in a 60-minute session; a cohort of 18 is "not a cohort, it is an all-hands"). Cohort composition should be **mixed stage, not mixed seniority** — the specific Chapter 2 and Chapter 4 move grounded in Brynjolfsson-Li-Raymond ("gains from generative-AI assistance were concentrated at lower-tenure workers") and Dell'Acqua ("performance variance by task, not by seniority"). "Seniors model for juniors" encodes a seniority-shaped assumption the research breaks. Rewrite target: three overlapping cohorts of ~6, each with one stage-1, two stage-2, two stage-3 mix, anchored to each engineer's join-the-programme date (not the all-hands date).

3. **"Checkpoints" (one, at Day 30, acceptance-rate dashboard, flag below 25%) collapses three Chapter-2 and Chapter-5 guardrails.** Chapter 2 calls for *four* checkpoints (Day 0 stage pin + budget; Day 30 first-successful-PR-with-tool; Day 60 pair-with-agent reflection; Day 90 review-of-your-review + graduation decision). The single Day-30 checkpoint also uses *Cursor acceptance rate* as the measurement, not a merged PR + two-paragraph reflection — Chapter 5 is explicit that acceptance rate is a Ziegler-et-al. *leading indicator of self-reported productivity*, not a fluency-growth signal. "Flag anyone below 25%" misreads the Chapter 2 Day-30 PR slippage diagnostic as a performance-management signal, which Chapter 5's first scoring guardrail prohibits ("the artifacts are not for performance management"). Rewrite target: four checkpoints, each producing the Chapter 5 artifact, with the slippage diagnostic read as a programme-design signal (tool-fit / missing pair-with-mentor / review-standard barrier), not a per-engineer rating.

4. **"Tool budgets" is the Chapter 4 seniority-banded anti-pattern in its purest form.** "Staff and senior engineers get Cursor Business + unlimited tokens; mid/junior get Cursor Pro + 300k cap" encodes "seniority maps to AI leverage" — exactly the input Chapter 4's research anchors (Brynjolfsson-Li-Raymond, Dell'Acqua) break. The specific failures this produces: the stage-1 staff engineer (who has never used Cursor at work) consumes the senior-tier spend as dead-weight; a stage-3 mid-level engineer gets throttled mid-task by the 300k cap and shifts back to non-AI workflows. Rewrite target: **everyone gets the same seat tier**; usage expectation varies by stage per Chapter 4's table (soft floor at stages 1–2, team median at stage 3, named ceiling + quarterly review at stage 4). Finance's preference is addressed through the stage-shaped usage projection + the mod-104 AI-cost-ratio tile, not through seat withholding.

5. **"Sustaining layer" has none of the three Wenger-Trayner elements.** A Slack channel is one tool the CoP may use, not the CoP itself. The quarterly vendor lunch-and-learn satisfies none of domain, community, or practice — Chapter 3: "not a Slack channel; not a book club; not a lunch-and-learn." The lunch-and-learn is also named specifically in Chapter 3's "What a workshop is not" section as "the oldest failure mode in corporate L&D." Rewrite target: stand up the CoP with the three elements explicitly (domain = AI-augmented practice on this team's workflows; community = the team + ~5 adjacent-team visitors + rotating ownership among 3–5 engineers; practice = pattern library + bi-weekly show-and-tell + monthly library review + quarterly review-of-your-review session + quarterly cross-team visit). The lunch-and-learn goes away; the Slack channel is a tool the CoP uses, not the CoP.

6. **"Measurement" stacks the exact three theatre shapes Chapter 1 names.** 100% adoption + acceptance rate + self-reported time saved from a pulse are the three leading indicators the chapter calls out as theatre when stacked without pairing with throughput, quality, and fluency-growth artifacts. Chapter 5 is explicit that the fluency-growth measurement set is three *artifacts* (first-successful-PR-with-tool, pair-with-agent reflection, review-of-your-review), scored for specificity / honesty / change-of-mind — not pass/fail, not numeric, not routed to performance management. Rewrite target: replace the three adoption-era numbers with the three Chapter 5 artifacts; keep adoption + acceptance + pulse as *secondary* leading indicators in the mod-104 dashboard under the appropriate tiles with known-limit sidebars.

7. **"Partner interfaces" violates the Chapter 1 / Chapter 7 authoring-vs-delivery split in both directions.** "L&D owns the curriculum end-to-end" is Chapter 1's load-bearing boundary breached ("the manager authors the curriculum and the measurement rubric … authoring cannot rotate"). "HR will co-sign the Day-30 acceptance-rate sheets" violates Chapter 7's "who signs" rubric explicitly — stage-pin sheets are signed by *the engineer and the manager; HR does not sign* (because it is not a formal performance record; HR signing drifts the artifact toward merit review and corrupts it). Rewrite target: manager authors curriculum and measurement rubric; L&D owns scheduling / intake / instructional-design review / LMS completion-record-only (Article 4 baseline name + date, not artifact content); HR is cc'd on the exec pre-read, does not sign stage sheets. Write the explicit non-asks per Chapter 7's example contract.

8. **"Research anchors" combines three Chapter 6 common mistakes in one sentence.** "Bersin 30% more capability" is the specific over-claim Chapter 6 names ("Bersin does not publish that specific comparative number … a manager who wields a Bersin cite as if it were a controlled trial is over-claiming") — Bersin's research is directional and framework-shaped, not experimental. "Microsoft WTI 70%" cites the headline number without the methodology caveat (self-report, cross-sectional, vendor-authored) that Chapter 6 requires. Pairing a shape-level industry frame with a self-report cross-sectional survey as if both are the same category of evidence is the "conflating industry research with academic research" mistake. Rewrite target: cite the Bersin *frame* ("the capability-academy pattern — cohort-based, artifact-producing, community-sustained"), cite the Work Trend Index with its specific edition year and the "learned in context of real work" finding + caveats, and cite the peer-reviewed productivity studies (Peng, Brynjolfsson, Dell'Acqua) at the *artifact* level per Chapter 5, not at the programme-shape level. Keep citation count to ~4 per one-pager.

9. **The six-weeks-in update stacks Chapter 1 theatre + Chapter 8 trap.** The "94% Cursor adoption + acceptance rate + pulse" composite is the exact three-theatre-shape stack from Chapter 1; the Bersin + WTI cite inherits the mistakes from Finding 8. Separately, the sentence "recommend full-team expansion of Cursor to the adjacent Developer Experience team under our ownership" is the specific Chapter 8 trap: a cross-team request is **Trigger 1 (scope creep across teams)**, which means the correct next artifact is the **Exercise 05 handoff contract to `ai-enablement-lead` (L45)**, not "expand under our ownership." Chapter 8 is explicit: "do not solve the gap by *becoming* the L45 role de facto. Taking on the org-wide programme on top of your L40 role without the role-level authority is unsustainable and creates a precedent future managers inherit." Rewrite target: name the trigger, propose the handoff contract (or an interim-owner Posture B if no L45 role exists), and keep the Platform Infra team-scope programme at its altitude.

Count your hits. **Seven or more is the pass bar**; five to six means a re-read of Chapter 2's cohort section and Chapter 3's "Common mistakes when first assembling the delivery mix"; four or fewer means re-read Chapters 1, 2, and 3 end-to-end before starting Exercises 01 and 04 on your real team.

### Step 5 — Rewrite the three load-bearing sections (15–20 min)

Rewrite three sections of the plan. Keep each under 10 lines.

- **Cohorts.** Replace the single-cohort-of-18 shape with three overlapping cohorts of 6 over Q1, each 3–6 engineers, mixed-stage-not-mixed-seniority, same cohort for 90 days. Specify who seeds each cohort's stage mix (one stage 1, two stage 2, two stage 3, rough shape).
- **Checkpoints.** Replace the single Day-30 acceptance-rate check with the Chapter 2 four-checkpoint structure. Each checkpoint names the artifact it produces (stage sheet; first-successful-PR-with-tool + two-paragraph reflection; pair-with-agent reflection; review-of-your-review + graduation decision). Reference the Chapter 5 scoring guardrails explicitly (specificity, honesty, change-of-mind; not pass/fail; not routed to performance management).
- **Delivery-format mix.** Replace the half-day vendor roadshow with the Chapter 3 three-format mix — bootcamp (Days 1–10, 5 sessions, cohort-based, tool-specific, manager and senior IC deliver the first three and the retro, vendor trainer may deliver one session pre-briefed, pair-with-mentor on Session 4); workshops (Days 11–60, 60–90 min weekly, topic-specific, delivery rotates among manager / senior IC / cross-team peer); CoP (Days 61–90 and ongoing, Chapter 3 Wenger-Trayner shape).

Use the Chapter 2 example 20-engineer plan and the Chapter 3 three-format table as the reference shapes, not templates to copy verbatim.

### Step 6 — Rewrite the six-weeks-in update as a Chapter 8 graduation signal (5 min)

Rewrite the manager's update paragraph. Three lines maximum. The rewrite should:

- Lead with a *decision ask*, not a status statement.
- Identify Trigger 1 (scope creep across teams) as the load-bearing signal from the Developer Experience request.
- Propose the correct next artifact (the Exercise 05 handoff contract to L45, or Posture A / Posture B if no L45 exists) — *not* "expansion under our ownership."
- Drop the composite research cite; carry at most one framework cite and one peer-reviewed cite if any.

Example shape:

```
Decision asked: start the Exercise 05 handoff-contract draft to
`ai-enablement-lead` for the Developer Experience team's inclusion
(Chapter 8 Trigger 1 fired). Platform Infra programme stays at team
scope through end of Q1 under current cohort structure; full roll-up
proposal to VP at Q-review 2026-04-01.
```

If your rewrite reads as "we'll scale it ourselves" or carries the Bersin 30% number, it has drifted; revise.

## Expected output

A single scratch file, roughly two pages, containing:

- Nine-bullet audit of the plan sections plus the three-line update-paragraph audit, cross-referenced to the answer key (hit / near-miss / missed).
- Three-section rewrite (cohorts, checkpoints, delivery-format mix) each under 10 lines.
- A three-line Chapter-8-shaped update paragraph.

Something like:

```
Finding 4 (Tool budgets — seniority-banded tiers + token cap)
  Failure mode: Chapter 4 "seniority bands" anti-pattern in its
    purest form.
  What it is encoding: "seniority maps to AI leverage" — breaks the
    Brynjolfsson-Li-Raymond and Dell'Acqua research anchors.
  Likely outcome: the stage-1 staff engineer sits on senior-tier
    spend as dead-weight; a stage-3 mid-level engineer gets
    throttled at 300k mid-task.
  Rewrite: everyone gets the same seat tier; usage expectation
    varies by stage (soft floor 1-2, team median 3, named ceiling
    + quarterly review 4). Finance addressed via stage-shaped
    projection + mod-104 cost-ratio tile.
  ✅ match.
```

## Checkpoint

Before moving on to Exercise 01 (where you author the dated Day 0 / 30 / 60 / 90 plan for **your own** team) and Exercise 04 (where you author the CoP charter for **your own** team), you should be able to answer **yes** to all five:

- Did you identify at least seven of the nine findings in the answer key, with the correct section attribution?
- Did you correctly flag the "Cohort of 18 grouped by seniority" as the Chapter-2 size defect *and* the composition defect, with the Brynjolfsson-Li-Raymond / Dell'Acqua grounding?
- Did you identify that the single Day-30 checkpoint uses the wrong measurement (acceptance rate, not merged-PR + reflection) *and* that "flag anyone below 25%" misreads the slippage as a performance signal — and did your rewrite restore the Chapter-2 four-checkpoint structure with the Chapter-5 artifacts?
- Did your delivery-format rewrite distinguish bootcamp (concentrated, cohort-based, tool-specific, Days 1–10) from workshop (focused, skill-specific, 60–90 min, Days 11–60) from CoP (sustaining, Wenger-Trayner three-element, Days 61–90 and ongoing) — and keep the manager on authoring, not full delivery?
- Did your update-paragraph rewrite identify Trigger 1 (scope creep across teams) as the load-bearing Chapter-8 signal from the Developer Experience request, propose the Exercise-05 handoff contract (or Posture A / B), and drop the Bersin-30%-and-WTI-70% composite cite?

If any answer is no, re-read Chapter 1's "What 'team-scope AI enablement' actually means" (the three failure modes), Chapter 2's "The four checkpoints" and "Cohort sizing: 3 to 6 is the sweet spot," and Chapter 3's "Common mistakes when first assembling the delivery mix" before starting Exercise 01 on your real team's plan.
