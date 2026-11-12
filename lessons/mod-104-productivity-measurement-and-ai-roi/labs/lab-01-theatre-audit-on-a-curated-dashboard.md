# Lab 01 — Theatre Audit on a Curated Dashboard

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 1 (the three theatre shapes; the two-audience artifact), Chapter 2 (the five-tile dashboard; the SPACE ↔ Core 4 crosswalk; the "do not use for performance management" clause; the common first-assembly mistakes), with a side-check against Chapter 6 (adoption vs activation; the cost-ratio tile shapes).
**Complements, does not duplicate:** Exercise 01 asks you to crosswalk **your own** team's current dashboard to SPACE and DX Core 4 and propose a five-tile v0.1. This lab hands you a fixed, deliberately broken dashboard for a fictional team — eight tiles, two theatre shapes, one mis-attributed metric, no cost line — so you can calibrate the diagnosis before you spend a real 2-hour session on your actual team. The exercise is an authoring task; the lab is a diagnostic drill against a known answer key.

## Objective

Read a curated sample: (a) the current eight-tile "AI Productivity" dashboard of a fictional team, (b) a one-paragraph note from the team's director explaining why they built it, and (c) the two-line Monday pre-read the manager writes from it. Identify every Chapter-1 theatre shape and every Chapter-2 first-assembly mistake in the current dashboard. Then rewrite the dashboard to the Chapter-2 five-tile shape — Speed, Effectiveness, Quality, Impact, AI-cost ratio — with specific metric picks, a known-limits sidebar, and a one-line reading-posture note for each tile. Target: **you identify at least six of the eight findings in the answer key**, and your rewrite produces a tile set that reads as a decision instrument rather than as a theatre slide.

## Prerequisites

- Chapter 1 read end-to-end (the three theatre shapes; the two-audience claim).
- Chapter 2 read end-to-end (the five-tile dashboard; the SPACE ↔ Core 4 crosswalk; the "do not use for performance management" clause; the common first-assembly mistakes; the Impact tile honest-instruments list).
- Chapter 6 skimmed (so you recognise the cost-ratio tile shapes — $/100 PRs, % of fully-loaded eng cost, $ per feature).
- A blank file for your audit memo and rewrites.
- A timer.

Optional but useful: Chapter 5 skimmed (so you can flag the one place in the draft dashboard where a published-study effect size is quoted as if it were this team's number); Chapter 8 skimmed (so you recognise where the qualitative circuit breaker is missing).

## The fictional context

> **"Order Platform" team, LedgerNorth Retail.** 16 engineers (1 staff, 4 senior, 11 mid/junior). Owns `order-service` and three related repos — payments adapter, inventory adapter, order-state machine. Agents in use: Copilot Business (16 seats), Cursor Pro (12 seats), Claude Code via team gateway (usage-based). Agent rollout landed in late Q4; this is the first Q-review with any AI-era data. The team has a Jellyfish dashboard inherited from the prior VP plus one home-grown Google Sheet maintained by the staff engineer. The data-dictionary does not exist yet. Reviewer-of-record on the dashboard: the manager (you, in the lab). Dashboard audience: a VP of Engineering who will sign the Q1 tool-budget renewal in six weeks.

## The director's one-paragraph note (how we got here)

> *"We bought Copilot and Cursor in Q4 to catch up with the market. The VP wants to see productivity numbers at the Q-review. I pulled together what we have from Jellyfish and the staff engineer's Google Sheet — mostly adoption, acceptance, and the DX survey we ran in December. The one-pager is next week; what's on the dashboard is what I've got."*

## The current eight-tile dashboard

Read all eight tiles end-to-end before taking notes. Do not skip to the answer key.

### Tile A — AI Adoption

> **94% of engineers used Copilot or Cursor in the last 7 days.** (Weekly refresh. Trend: ↑ from 71% four weeks ago. Headline on the dashboard.)

### Tile B — Suggestion Acceptance Rate

> **38% of Copilot suggestions accepted (trailing 14 days).** (Breakdown by engineer in the appendix; top performer flagged in green, bottom three in red.)

### Tile C — Self-Reported Time Saved

> **Engineers report saving 7.2 hours/week with agents (DX pulse, December).** N = 11 respondents. Trend arrow: ↑ (first-time measurement).

### Tile D — Lines of Code per Engineer per Week

> **+32% QoQ in lines of code shipped per engineer.** (Includes agent-drafted lines; appendix has the breakdown by repo.)

### Tile E — Weekly PRs Merged (Team Total)

> **74 PRs/week, trailing 4-week average.** (Up from 61 four weeks ago. Trend: ↑. Caveat line: *"includes agent-drafted PRs"* in 8-point font below.)

### Tile F — Change Failure Rate

> **Change failure rate: 9% (trailing 30 days).** Definition: *"PRs that the author rolled back within 24 hours."*

### Tile G — "Research-Published Gains"

> **"Industry research shows AI delivers a 25% productivity improvement."** (Static sidebar, cites "GitHub research + McKinsey State of AI 2024.")

### Tile H — Per-Engineer AI-Attributable Productivity %

> **Per-engineer column added last week.** Each engineer's row has an "AI contribution %" computed as *(acceptance-rate × self-reported-time-saved) ÷ team mean*. Ranges from 0.3 to 1.8. The staff engineer's row is 0.4; one senior IC's row is 1.8.

## The Monday pre-read (as currently drafted)

> *"Team AI productivity this week: 94% adoption, 38% acceptance, 7.2 hours/week self-reported time saved, +32% LOC per engineer QoQ, 74 PRs/week. Research shows 25% productivity improvement; our team is in line with this. Recommend continuing current investment."*

## Steps

### Step 1 — Set up your audit memo (3 min)

Create a working file `lab-01-dashboard-audit.md`. Add this header:

```
# Lab 01 — Dashboard theatre audit (Order Platform, Q1)

Chapter 1 theatre shapes:
  T-A  Adoption-count as productivity
  T-B  Suggestion-acceptance as output
  T-C  Self-reported time saved, uncorrected

Chapter 2 first-assembly mistakes:
  M1   Over-indexing on Activity
  M2   Confusing Effectiveness with Satisfaction
  M3   Treating the DX survey as ground truth
  M4   "AI-attributable" column on every tile / per engineer
  M5   No "known limits of the signal" sidebar

For each finding, record:
  (a) which tile(s), (b) which shape or mistake, (c) one line on what
  the dashboard is encouraging the audience to conclude, (d) the
  Chapter 2 rewrite target.
```

### Step 2 — Audit the eight tiles against Chapter 1 and Chapter 2 (25–35 min)

Work through tiles A through H in order. For each tile, ask: *is this a theatre shape (Chapter 1), a first-assembly mistake (Chapter 2), a methodologically-fine-but-thin instrument, or a load-bearing signal?* Write one line per finding. Do not scroll to the answer key until you have at least six findings written down. **Target: no more than 4 minutes per tile.**

Specifically, for each tile:

- **A — Adoption.** Which Chapter 1 theatre shape is this? What is the Chapter 2 crosswalk — does adoption instrument any SPACE dimension or any Core 4 tile?
- **B — Suggestion acceptance.** Ziegler et al. (Chapter 5) found acceptance correlates with *self-reported* productivity. Is this therefore a throughput number, an effectiveness number, or a leading indicator? What does putting it on the top row of the dashboard, with per-engineer breakouts and traffic-light colours, communicate about what the manager thinks it is?
- **C — Self-reported time saved.** Which Chapter 1 shape? What does the N = 11 respondents detail say about how to read the 7.2 hours/week number?
- **D — Lines of code per engineer per week.** Chapter 2 names LOC specifically as a *low-signal* activity metric. What is it measuring? What does "+32% QoQ" tell you about the team's productivity when the denominator includes agent-drafted lines?
- **E — Weekly PRs merged.** This is a defensible Speed metric if composed with others. What is missing from the surrounding tiles that would make it load-bearing vs. theatre?
- **F — Change failure rate.** The definition is *"PRs the author rolled back within 24 hours."* Which Chapter 3 Caveat 2 principle does this violate under agent-era conditions?
- **G — "Research-published gains" sidebar.** Which Chapter 5 mis-cite pattern is this? Which specific papers does it conflate? Would a mid-level engineer who read Peng et al. 2023 accept the sentence as written?
- **H — Per-engineer AI-attributable productivity %.** Two separate Chapter 2 clauses apply. Which two? What does the staff-engineer-at-0.4 / one-senior-IC-at-1.8 split likely represent (hint: Chapter 5 Brynjolfsson, Dell'Acqua)?

### Step 3 — Audit the Monday pre-read as a composed artifact (5 min)

Separately from the tiles, write a 4–6 line diagnosis of the Monday pre-read:

- Which Chapter 1 shapes does the pre-read's *composite* claim stack (adoption + acceptance + self-report + LOC + PRs) without naming the limits of each?
- Does the "research shows 25% productivity improvement; our team is in line with this" sentence meet Chapter 5's responsible-citation bar?
- Is "recommend continuing current investment" a Chapter 7 decision ask or a status statement?

### Step 4 — Compare against the answer key (10 min)

Below is the answer key — eight findings. For each, check whether your audit found it. Count hits (same tile or same location, same finding) and near-misses (same tile but different framing).

#### Answer key — eight findings

1. **Tile A (Adoption) is Theatre A.** Chapter 1 is explicit: "78% of engineers used Copilot this week" is an adoption number, not a productivity number. Leading the dashboard with adoption, with a trend arrow, communicates that the manager believes adoption *is* the productivity story — which is the exact VP non-answer the chapter opens with. Rewrite target: adoption belongs in the Exercise 03 adoption-vs-activation report, not on the top row of the productivity dashboard. Load an *activation* number (material-use definition from Chapter 6) on the AI-cost-ratio tile's companion if you need the adoption-adjacent signal at all.

2. **Tile B (Suggestion acceptance) is Theatre B, made worse by the per-engineer traffic-light colouring.** Acceptance rate is a defensible Ziegler-et-al. leading indicator of *self-reported* productivity — not of shipped output. Putting it on the top row with per-engineer green/red flags converts it into a performance-management instrument (the exact Chapter 2 trap: Goodhart + wrong-altitude attribution). Rewrite target: remove from the top-level dashboard; if kept at all, keep team-level only, no per-engineer traffic lights, and name it explicitly as a leading indicator of developer-felt experience.

3. **Tile C (Self-reported time saved) is Theatre C.** The 7.2 hours/week is a legitimate signal with named limitations (Hawthorne effects, self-report bias, N = 11 respondents → 69% response rate on a 16-person team — fine for a pulse but not ground truth). The dashboard treats it as a *throughput* number. Chapter 2's "Treating the DX survey as ground truth" mistake (M3). Rewrite target: self-reported time-saved belongs in the qualitative instrument (Chapter 8, pulse survey) with distribution surfaced — *not* as a top-level throughput tile.

4. **Tile D (Lines of code) is the Chapter 2 M1 trap in its purest form.** LOC is the lowest-signal activity metric and is specifically called out in Chapter 2's "Over-indexing on Activity." Under agent-era conditions a +32% QoQ in LOC where the denominator includes agent-drafted lines may reflect *less* productivity (agent-drafted code is often verbose; the real work is reading and verifying what the agent produced). Rewrite target: remove the tile entirely. If you need a Speed proxy, use median weekly PRs-per-engineer (not LOC, not commits).

5. **Tile F (Change failure rate) uses the pre-agent-era definition and will miss the agent-era failure mode.** The definition is "PRs the author rolled back within 24 hours." Chapter 3 Caveat 2 is explicit that this definition will miss "the case where an agent-authored change broke something nobody noticed to roll back." Rewrite target: broaden to *any rollback, any hotfix within 24h, any incident-ticket raised with severity ≥ S2 attributed to the deploy, independent of who filed it*. Name the definition in the data-dictionary sidebar. The 9% number as reported is almost certainly understating the real rate.

6. **Tile G (Research-published gains) is the Chapter 5 composite-rough mis-cite.** "25% productivity improvement" is not a finding from any single anchor study; it is a rounded-and-flattened number that conflates several incompatible effect sizes (Peng's 55% on a bounded single task; Brynjolfsson's 14% in customer support averaged with 34% for juniors; Dell'Acqua's +40%/-19% split by frontier side). "Industry research + McKinsey State of AI" also crosses Chapter 5's "do not cite industry surveys as if they were peer-reviewed research" posture. Rewrite target: the one-pager cites the range specifically (Peng 2023: ~55% on bounded tasks; Brynjolfsson 2023: ~14% avg in support with 34% for juniors; Dell'Acqua 2023: positive inside the frontier, negative outside) — *not* a single flattened number. Static sidebar on the dashboard: literature-anchor paragraph with specific citations, no composite claims.

7. **Tile H (Per-engineer AI-attributable productivity %) violates both Chapter 2 clauses.** First: "do not use for performance management" — per-engineer decomposition of a composite of acceptance-rate and self-reported-time-saved converts the dashboard into a performance-management instrument (Goodhart + methodological error). Second: "do not let AI-attributable become a column on every tile" — attribution happens in the narrative paragraph of the one-pager, not as a per-engineer percentage. The staff-engineer-at-0.4 / senior-IC-at-1.8 split likely reflects the Dell'Acqua jagged frontier (the staff engineer is working on outside-frontier architectural work where agents add negative value) and the Brynjolfsson tenure distribution (seniors benefit less than juniors in the literature) — which is exactly the *distribution* a team-average number masks. The tile encodes a distribution that will be read as a *ranking* and used in performance conversations within a quarter. Rewrite target: delete the tile entirely. Surface the distribution in the Chapter 8 qualitative instrument's tenure-segmented reading; attribute composite signal in the Chapter 7 one-pager's narrative paragraph.

8. **The dashboard is missing the five Chapter-2 tiles and the known-limits sidebar.** None of Speed (as a Core 4 tile, with median — Tile E is unreliable alone), Effectiveness (DX developer-experience index refreshed quarterly — the pulse exists but is not promoted to a tile), Quality (the broken CFR is a draft but the escaped-defect-per-sprint companion is missing), Impact (no new-capability % or OKR-attainment or Flow-work-type split), AI-cost ratio ($ per 100 PRs merged, % of fully-loaded eng cost, $ per feature — all three missing — the reconciled Chapter-6 spend table is the missing denominator). No "known limits of the signal" sidebar on any tile. No data-dictionary link. The dashboard reads as a theatre collage because what it is *missing* is the composed-signal shape; Chapter 2: "five tiles, two or three charts each at most. A sidebar that names the known limits of the signal honestly. … Five tiles. The honest limits sidebar is non-optional." Rewrite target: replace all eight tiles with the Chapter 2 five-tile layout plus the known-limits sidebar.

Count your hits. **Six or more is the pass bar**; four to five means a re-read of Chapter 2's "What goes on the dashboard, and in what shape" section and Chapter 1's theatre-shapes section; three or fewer means re-read Chapter 1 end-to-end and Chapter 2's first half.

### Step 5 — Rewrite the dashboard to the Chapter 2 five-tile shape (15–20 min)

Write the Chapter-2 five-tile v0.1 for the Order Platform team. Each tile gets:

- The specific metric chosen (one line; one-line definitions only — see Exercise 01's starter guidance).
- The data source (Jellyfish, GitHub, DX survey, Claude gateway chargeback, etc.).
- The trailing-window choice.
- **One specific** known limit (Chapter 2's "known limits" column — one specific named limit, not a general hedge).
- One sentence on why this metric and not an alternative.

Use the Chapter 2 example dashboard shape as a reference, not a template to copy verbatim. Favour metrics whose definition fits on one line.

Example shape for one tile:

```markdown
## Tile 1 — Speed
- Metric: median weekly PRs merged per engineer, trailing 90 days.
- Source: GitHub + Jellyfish.
- Window: trailing 90 days; trend line shown over the prior 4 quarters.
- Known limit: includes agent-drafted PRs (per Chapter 3 Caveat 1);
  companion data-dictionary line names the agent-attribution caveat
  explicitly.
- Why this and not LOC-per-engineer: LOC is the lowest-signal activity
  metric (Chapter 2 M1); median PRs normalises against outliers in
  both directions (median preferred over mean per Chapter 2's
  "common mistakes" section).
```

Do all five tiles. Keep each tile under eight lines.

### Step 6 — Add the known-limits sidebar and the data-dictionary stub (5 min)

Chapter 2 is explicit that the known-limits sidebar is non-optional. Under a heading **Known limits of the signal**, write four to six lines naming:

- The three or four most load-bearing limits across the five tiles (e.g. *"Speed includes agent-authored PRs; Effectiveness is self-report with N = 11 respondents last quarter; AI-cost ratio is a first-time measurement — treat as baseline, not as trend"*).
- The single line that states *"these metrics are for team-productivity measurement; individual performance evaluation is covered in `mod-108` via different instruments"* (Chapter 2 enforcement move 1).
- A link placeholder to the data-dictionary stub (which does not exist yet — Exercise 01 produces it).

### Step 7 — Rewrite the Monday pre-read as a Chapter-7 decision ask (5 min)

Rewrite the manager's two-line pre-read into a Chapter-7-shaped Section-1 headline: the ask (continue / grow / roll back), the TL;DR of the metric picture, and the rollback-criteria-fired statement. Three lines maximum. Use the actual VP context (tool-budget renewal in six weeks).

Example shape:

```
Decision asked: continue Copilot + Cursor investment at current seat
count into Q2 pending the full Q-review on [date]. TL;DR: median PRs
per engineer +18% QoQ, change failure rate 11% on the broadened
definition (first-time measurement — treat as baseline), combined
AI-cost ratio $X / 100 PRs merged. No rollback criteria fired; one
near-miss on activation (staff-engineer workstream — see Section 4).
```

If your rewrite leads with "research shows 25%" or with adoption or with LOC, it has drifted; revise.

## Expected output

A single scratch file, roughly two pages, containing:

- Eight-bullet audit of the current tiles plus the three-line Monday pre-read audit, cross-referenced to the answer key (hit / near-miss / missed).
- A five-tile rewrite — Speed, Effectiveness, Quality, Impact, AI-cost ratio — each with the five-line structure above.
- A four-to-six-line known-limits sidebar with the "not for individual performance evaluation" line.
- A three-line Monday pre-read rewrite in Chapter-7 decision-ask shape.

Something like:

```
Finding 7 (Tile H — per-engineer AI-attributable %)
  Shapes violated: Chapter 2 "do not use for performance management" +
    "do not let AI-attributable become a column on every tile."
  What it is encouraging: converts the dashboard into a performance-
    management instrument; staff-engineer-at-0.4 will be read as a
    ranking within a quarter.
  Underlying distribution: likely Dell'Acqua frontier (staff is on
    outside-frontier architectural work) + Brynjolfsson tenure
    (seniors gain less); the tile hides both as a composite ratio.
  Rewrite: delete the tile. Surface the distribution in the Chapter 8
    pulse (tenure-segmented reading). Attribute composite signal in
    the Chapter 7 one-pager's narrative paragraph, not on a tile.
  ✅ match.
```

## Checkpoint

Before moving on to Exercise 01 (where you crosswalk **your own** team's dashboard to SPACE and DX Core 4 and propose a five-tile v0.1), you should be able to answer **yes** to all five:

- Did you identify at least six of the eight findings in the answer key, with the correct tile / location attribution?
- Did you correctly identify Tiles A, B, C as the three Chapter-1 theatre shapes (adoption-count, suggestion-acceptance, uncorrected self-report), *not* confuse any of them with each other?
- Did you flag Tile F's change-failure-rate definition as the pre-agent-era definition that misses the agent-era failure mode per Chapter 3 Caveat 2 — and specify the broadened definition (any rollback / any hotfix ≤ 24h / any S2+ incident attributed, independent of who filed it) in the rewrite?
- Did your five-tile rewrite include a one-line AI-cost ratio tile using one of the Chapter 6 shapes ($/100 PRs, % of fully-loaded eng cost, $ per feature), name it explicitly as an addition rather than shoehorn it into Core 4, and include one specific known limit per tile?
- Did your Monday pre-read rewrite open with a Chapter-7 decision ask (continue / grow / roll back), lead with throughput then quality then cost, and *not* cite a composite "research shows 25%" number?

If any answer is no, re-read Chapter 1's "What 'AI theatre' looks like in a metrics dashboard," Chapter 2's "What goes on the dashboard, and in what shape" and "Common mistakes when first assembling the dashboard," and Chapter 7's "The one-pager structure," before starting Exercise 01 on your real team's dashboard.
