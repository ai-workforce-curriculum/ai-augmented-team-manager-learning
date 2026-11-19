# Lab 02 — Stage-Shaped Budget Distribution Drill on a Composite Team Snapshot

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 5 (the three allocation layers — seat, token, enterprise commit; the `mod-105` stage ladder as the distribution driver; floors as review signals not procurement signals; finance-partner-facing projection; monthly/quarterly review cadence; the common mistakes), with a side-check against Chapter 1 (scope — enterprise commit architecture is `ai-enablement-lead`, not the manager) and Chapter 7 (budget distribution as a registry input).
**Complements, does not duplicate:** [Exercise 03](../exercises/exercise-03-tool-budget-and-token-budget-distribution.md) asks you to author the v0.1 budget distribution for **your own** team — real stage pins, real pricing pulls, real finance partner. This lab hands you a composite team snapshot with specific usage signals so you can **calibrate your reading** of what the monthly data is telling you — floor signals vs ceiling signals, stage-shift projections vs drift, three-layer reporting vs one-number collapse — before you spend two hours on a plan whose finance-partner conversation reads as drift because the projection line was missing.

## Objective

Given a team's `mod-105` stage pins per tool, a current month's usage data, published vendor pricing, and the team's existing enterprise-commit shape, produce a budget distribution with: (i) the **three allocation layers** broken out separately (seat, token, enterprise commit); (ii) a **per-stage token-budget projection** per usage-based tool for the next month using the Chapter 5 projection pattern; (iii) a **stage-shift projection** for Q[N+1] anticipating how the `mod-105` cohort will progress; (iv) a **finance-partner-facing narrative** that composes with the `mod-104` AI-cost tile; (v) **monthly review signals** on the current data — floor undershoots, median drift, ceiling-approach — with the correct response per signal (data conversation, not budget cut, not cap); and (vi) **quarterly inputs** for the Chapter 7 tool registry (keep / sunset shortlist; stage-pin changes; commit-shape input). Then compare against the answer key.

Target: **you break out the three layers separately on every tool, you catch the three deliberately planted anti-pattern traps (a stage-2 IC at floor-undershoot that looks like a budget-reduction target but is actually a `mod-105` programme signal; a stage-4 IC running 3x median that looks like overuse but is pattern-building; a single-number roll-up to finance that hides the stage-shift projection), and your projected Q[N+1] total correctly reflects the stage-shift rather than reporting flat.** The three drifts this lab is designed to catch — *"underuse is overspend"*, *"3x median is cap-worthy"*, *"finance likes one number"* — are the Chapter 5 common mistakes the chapter names verbatim.

## Prerequisites

- Chapter 5 read end-to-end — especially *"The three allocation layers"*, *"Token budget distribution"* (floors as review signal; the finance-partner-facing total; the worked projection pattern), *"Enterprise commitment handling"*, *"Monthly and quarterly usage review"*, *"Interaction with the `mod-104` AI-cost tile"*, and *"Common mistakes when first distributing"*.
- `mod-105` Chapter 4 skimmed — the four-stage ladder (stage-1 floor ~50 tasks/month; stage-2 floor ~100; stage-3 team median; stage-4 uncapped with quarterly-review threshold).
- `mod-104` Chapter 2 skimmed — the AI-cost tile shape (cost per 100 PRs merged) that the budget line feeds into.
- Chapter 1 and Chapter 7 skimmed — the scope boundary (enterprise commits are `ai-enablement-lead`, not the manager) and the registry inputs the quarterly review produces.
- A blank file for your distribution plan.
- A timer.

## The fictional context

> **"Harborlink" team, Cove Logistics (US-headquartered logistics SaaS, Boston).** 10 engineers (1 staff, 2 senior, 4 mid, 3 junior), 1 manager. Primary codebases: a Python shipment-routing service (`harborlink-router`) and a React carrier-portal (`carrier-portal`). Data classes are Internal and Confidential; no PCI or HIPAA; `mod-110` Chapter 6 matrix allows Enterprise-tier Cursor Business, Copilot Enterprise, and Claude Code for all team workflows.
>
> **Tool registry (coming out of a Chapter 2 bake-off from last quarter).**
>
> - **Cursor Business** — Tier 2 agentic IDE — stance: Wrap — all 10 ICs have seats.
> - **Copilot Enterprise** — Tier 1 — stance: Buy — all 10 ICs have seats, on the org's annual commit.
> - **Claude Code** — Tier 3 terminal agent — stance: Extend (with a team-owned MCP server) — usage-based, no seats.
> - **Windsurf** — parked candidate from the last bake-off; 1 trial seat held for Q[N].
>
> **Published pricing (list prices for this lab; your Exercise 03 pulls current prices):**
>
> - Cursor Business: $40/seat/month (list).
> - Copilot Enterprise: $39/seat/month on the org's annual commit (list).
> - Claude Code: usage-based; Chapter 5's illustrative figures used here — $40/engineer/month at stage-1 floor; $80 at stage-2 floor; $120 at stage-3 team median; $360 at stage-4 ceiling (3x median).
> - Windsurf trial seat: $20/seat/month on trial pricing.
>
> **`mod-105` stage pins per tool** (set at last quarter's `mod-105` Ch. 4 review):
>
> | IC          | Role   | Cursor stage | Copilot stage | Claude Code stage |
> |-------------|--------|--------------|---------------|-------------------|
> | Alex (staff)  | staff  | 4            | 4             | 4                 |
> | Blake (sr)    | senior | 3            | 4             | 3                 |
> | Chen (sr)     | senior | 3            | 3             | 3                 |
> | Dalia (mid)   | mid    | 3            | 3             | 2                 |
> | Esen (mid)    | mid    | 2            | 2             | 2                 |
> | Felix (mid)   | mid    | 2            | 3             | 1                 |
> | Gita (mid)    | mid    | 2            | 2             | 1                 |
> | Harper (jr)   | junior | 1            | 2             | 1                 |
> | Ingo (jr)     | junior | 1            | 2             | 1                 |
> | Jun (jr)      | junior | 2            | 2             | 1                 |
>
> **Current month usage (actuals pulled from vendor consoles):**
>
> | IC        | Claude Code spend ($/mo) | Notes                                                   |
> |-----------|--------------------------|---------------------------------------------------------|
> | Alex    | $380                     | Running a pattern-building effort on a scheduled eval pipeline; wrote 4 shared slash commands last month. |
> | Blake   | $115                     | At team median.                                         |
> | Chen    | $140                     | Slightly above team median; working on a refactor.      |
> | Dalia   | $85                      | Near stage-2 floor.                                     |
> | Esen    | $78                      | Near stage-2 floor.                                     |
> | Felix   | $20                      | Far under stage-1 floor expectation (vendor-equivalent of ~25 tasks/month). |
> | Gita    | $45                      | At stage-1 floor.                                       |
> | Harper  | $42                      | At stage-1 floor.                                       |
> | Ingo    | $38                      | At stage-1 floor.                                       |
> | Jun     | $44                      | At stage-1 floor.                                       |
>
> Team median Claude Code spend (middle quintile of the stage-3 cohort for calibration): **$120/engineer/month** at stage-3; stage-4 ceiling at 3x median = $360.
>
> **Enterprise-commit shape (owned by `ai-enablement-lead` and procurement; the team is a consumer):**
>
> - Copilot Enterprise: annual commit, team's 10 seats × $39 = $390/month allocated to the team's cost-centre.
> - Claude for Work Enterprise (Claude Code's contracted tier): org has a committed-use agreement; team's projected share for Q[N] is ~$1,200/month; overage billable.
>
> **Stage-shift pins expected over Q[N+1]** (set in the `mod-105` Chapter 4 quarterly review):
>
> - Harper (Cursor 1→2; Claude 1→2).
> - Ingo (Claude 1→2).
> - Jun (Cursor 2→3; Claude 1→2).
> - Felix: `mod-105` programme intervention scheduled — stage pin not expected to advance this quarter until the undershoot is diagnosed.
> - Dalia (Claude 2→3).
>
> **Finance-partner cadence.** Monthly line review; quarterly narrative review; the `mod-104` AI-cost tile is read as "cost per 100 PRs merged" with the stage-shift projection as the context narrative.

Grade the distribution *as if you are the team manager building the Q[N+1] plan*. Do not invent IC names, usage figures, or commit shapes not in the snapshot; project only on what the snapshot provides.

## Steps

### Step 1 — Set up your distribution plan (3 min)

Create a working file `lab-02-distribution-plan.md` with these sections:

```
Section I — Seat budget layer (linear in headcount)
   Per-tool seat line; total; trial-seat sub-category with end date.

Section II — Token budget layer (stage-shaped per mod-105 Ch. 4)
   For each usage-based tool:
       Per-stage sum; total.
       Per-IC projection (the next month's expected Claude Code spend).

Section III — Enterprise-commit layer (consumer of org-owned commits)
   Per-committed-vendor: team share, overage posture, usage telemetry contributed.

Section IV — Three-layer monthly total (not one number)
   Three lines; sum; one-paragraph narrative.

Section V — Stage-shift projection for Q[N+1]
   Per-tool projected change; narrative tying the change to the mod-105 cohort
   progression; the projected new monthly total.

Section VI — Monthly review signals
   For each IC with a signal (floor undershoot, median drift, ceiling approach):
       Signal type; interpretation (data conversation / mod-105 signal /
       pattern-building / cap); response.

Section VII — Quarterly inputs to Chapter 7 registry
   Tool keep/sunset shortlist; stage-pin changes; commit-shape input to upstream
   review; flagged risks.
```

Time yourself. Target per section: ~8 minutes. If you spend more than 12 minutes on a section, note the drift and move on; you will diagnose in Step 5.

### Step 2 — Fill Sections I–III (seat, token, enterprise-commit layers) (20–25 min)

Build the three layers against the snapshot. Keep them visibly separate; do *not* roll into a single number yet. For Section II, use the Chapter 5 worked-projection pattern verbatim — floor × count for stages 1 and 2, median × count for stage 3, ceiling × count for stage 4 with the quarterly-review posture noted.

### Step 3 — Fill Sections IV–V (three-layer total + stage-shift projection) (10–15 min)

For Section IV, show the three lines then the sum, plus a one-paragraph narrative. Resist the one-number-to-finance shortcut; it is the archetypal Chapter 5 common mistake. For Section V, apply the pinned stage-shifts to the tool-specific projection and show the projected rise — *"the rise is the enablement programme working, not budget drift"*.

### Step 4 — Fill Sections VI–VII (monthly signals; quarterly inputs) (10–15 min)

For each IC in the usage table, decide whether the usage is a signal and if so what kind. **Two of the ICs are deliberately planted traps** — one whose undershoot looks like a budget-reduction target but is actually a `mod-105` programme signal, and one whose 3x+-median spend looks cap-worthy but is pattern-building. Do not label either as a budget action.

### Step 5 — Compare against the answer key (10–15 min)

Read the key below only after you have filled Sections I–VII.

#### Answer key — Section I (seat budget)

- Cursor Business: 10 seats × $40 = **$400/month**.
- Copilot Enterprise: 10 seats × $39 = **$390/month**, on the org's annual commit (allocated line, not team-side negotiated).
- Claude Code: **$0 seats** (usage-based).
- Windsurf trial: **1 seat × $20 = $20/month**, categorised as **Trial** with a dated end (Chapter 5: *"Trial seats are a named sub-category…so the finance line tracks it separately and the trial has an end date."*). The parking date from the Chapter 2 bake-off is the trial end.
- **Seat budget total: $810/month** (production: $790; trial: $20).

#### Answer key — Section II (token budget)

Claude Code (the usage-based tool):

| Stage | ICs at stage | Per-IC budget ($/mo) | Sub-total ($/mo) |
|-------|--------------|----------------------|------------------|
| Stage 1 | 5 (Felix, Harper, Ingo, Jun, and Gita at Claude-stage-1 — see below) | $40 floor | $200 |
| Stage 2 | 2 (Dalia, Esen) | $80 floor | $160 |
| Stage 3 | 2 (Blake, Chen) | $120 median | $240 |
| Stage 4 | 1 (Alex) | $360 ceiling (quarterly-reviewed) | $360 |
| **Total projected** | 10 | | **$960/month** |

*Note on stage classification per tool.* The lab's stage table has Gita at *Cursor stage 2* but *Claude stage 1*; per Chapter 5, budgets are *per IC per tool* (*"The budget is defined per IC per tool"*) — Gita counts as stage-1 for Claude Code. This is the right discipline; a team that rolls up stage across tools loses the signal shape.

(The current-month actuals are $987 — slightly over projection, driven by Alex's $380 at the stage-4 ceiling and Chen's $140 above median. Both are within the Chapter 5 posture; see Section VI.)

#### Answer key — Section III (enterprise-commit layer)

- **Copilot Enterprise** on org annual commit: team share $390/month; overage posture n/a (seat-based, not usage-based); usage telemetry contributed to `ai-enablement-lead`'s quarterly commit review per Chapter 5 *"Contributing usage evidence"*.
- **Claude for Work Enterprise** on committed-use agreement: team's projected share $1,200/month; overage billable to team cost-centre; Chapter 5: *"If the team's budget distribution would systematically under- or over-consume the commit, the manager flags upstream for renegotiation input."* Current projection ($960) is under the $1,200 share — *flag upstream as commit-shape input*, do not silently absorb (the stranded-cost failure mode Chapter 5 names: *"a team that silently uses zero of a committed vendor's product because the org committed to it a year ago and the team's workflow has moved on"*).

#### Answer key — Section IV (three-layer monthly total)

- Seat budget: **$810/month** (production $790 + trial $20).
- Token budget: **$960/month** (Claude Code projected).
- Enterprise-commit share: Copilot $390 already counted in seat; Claude for Work $1,200 projected consumer cap, actual team-paid $960 (the commit is org-owned; the team is a consumer).

The right reporting shape (Chapter 5: *"A clean budget plan expresses all three layers separately and sums them. A plan that expresses only one layer is a line item, not a plan."*):

```
Harborlink team monthly AI-tooling budget — Q[N]:

  Seat budget                    : $790 (production) + $20 (Windsurf trial)
                                   = $810
  Token budget (usage, Claude)   : $960 projected
  Enterprise-commit (team share) : Copilot $390 included above;
                                   Claude for Work $1,200 commit, $960
                                   consumed (ongoing commit-shape input
                                   to ai-enablement-lead)
  TOTAL                          : $1,770/month projected
```

The one-paragraph narrative (the sentence pattern Chapter 5 names):

> *"Stage distribution will shift over Q[N+1] as 4 ICs advance (3 Claude stage 1→2, 1 Claude stage 2→3, 1 Cursor stage 2→3). Expect Claude Code token-budget rise ~17% in Q[N+1] (~$160/mo) as the cohort progresses; team monthly total rises ~8% once the Windsurf trial seat sunsets. The rise is the enablement programme working, not budget drift. The ratio of spend to PRs-merged is tracked in the `mod-104` AI-cost tile; it will decrease as the cohort matures. Felix (stage-1 undershoot) is in a `mod-105` programme intervention; no stage advancement pinned until the signal is diagnosed."*

#### Answer key — Section V (stage-shift projection for Q[N+1])

Apply the pinned stage advancements:

- Harper: Claude 1→2 (+$40/mo).
- Ingo: Claude 1→2 (+$40/mo).
- Jun: Claude 1→2 (+$40/mo); Cursor 2→3 (no Cursor usage-cost change — seat-based).
- Dalia: Claude 2→3 (+$40/mo).
- Felix: no advancement (programme intervention; stage-1 floor remains).

Claude Code sub-total shift: **+$160/month**. New projected Claude Code: $1,120/month.

Full projected Q[N+1] total:
- Seat budget: unchanged at $790 (Windsurf trial likely sunset by Q[N+1] — confirm in Section VII).
- Token budget: $1,120.
- Enterprise-commit share: $1,120 consumed vs $1,200 commit — commit-shape still under, continue flagging upstream.
- **Projected Q[N+1] total: $1,910/month** (≈ 8% rise from Q[N]'s $1,770; the rise reflects advancement of 4 ICs, correctly framed as programme-landing).

#### Answer key — Section VI (monthly review signals)

Walk the usage table, IC by IC. The signals and correct responses:

- **Alex — $380/mo at stage-4 ceiling.** Chapter 5: *"ceiling signal on stage 4. Is stage-4 usage inside the quarterly-review ceiling? Breach is a conversation — pattern-building (good, feed into `mod-104` narrative) or a side project on the corp licence (less good)."* $380 is within 10% of the ceiling. Interpretation: **pattern-building** (the snapshot notes Alex wrote 4 shared slash commands and is running a scheduled eval pipeline). Response: **quarterly-review conversation, not a cap**; feed into the `mod-104` tile narrative as evidence of the enablement programme producing patterns for the team to adopt.
- **Blake — $115/mo at stage-3 median.** No signal; team-median usage is the target shape.
- **Chen — $140/mo slightly above stage-3 median.** Chapter 5: *"median signal on stage 3. Is stage-3 spend tracking team-median? Significant drift (e.g., one stage-3 engineer at 3x median) is a conversation, not a cap."* $140 is ~17% above median — not significant drift. Interpretation: **within normal variance**. Response: **note; no action**.
- **Dalia — $85/mo near stage-2 floor.** Within the stage-2 posture. Response: **note; stage advancement pinned for Q[N+1]**.
- **Esen — $78/mo near stage-2 floor.** Similar to Dalia but no advancement pin this quarter. Response: **note; continue `mod-105` cohort placement**.
- **Felix — $20/mo far under stage-1 floor expectation.** Chapter 5 is explicit: *"If a stage-2 engineer is at 20 tasks/month instead of 100, that is not a budget-reduction trigger; it is a 1:1 signal that the engineer may be stuck on Failure-B — the tool is in the way, the engineer has turned it off, the `mod-105` programme is not landing for them. Reduce the budget on data, not on underuse."* (Note: Felix is Claude-stage-1 per the pin table, so the floor is ~$40 and the undershoot is ~50%; the Chapter 5 reasoning applies identically to stage-1 and stage-2 undershoots.) Interpretation: **`mod-105` programme signal, not a budget-reduction trigger**. Response: **1:1 to diagnose** (wrong tool fit, missing training, task mix that does not invite AI use, etc.); route the finding to the `mod-105` cohort owner; **no budget change**. **The deliberately planted trap:** a manager who writes *"Felix is at 50% of floor — reduce his Claude budget to $20/mo and reallocate"* is reproducing the archetypal Chapter 5 common-mistake pattern (*"caps on stages 1–2"*) and starving the enablement programme of the exploratory time it needs.
- **Gita, Harper, Ingo, Jun — at stage-1 floor.** Stage-1 floor is working as designed. No signal.

**Summary for Section VI:** two conversation-worthy signals (Alex pattern-building at stage-4 ceiling; Felix stage-1 undershoot routing to `mod-105`), neither of which is a budget action. The two deliberately planted traps — *"Alex is at 3x median, cap him"* and *"Felix is at 50% of floor, cut his budget"* — are the symmetric pair Chapter 5 names.

#### Answer key — Section VII (quarterly inputs to Chapter 7 registry)

- **Tool keep decisions:** Cursor Business, Copilot Enterprise, Claude Code — all retained; usage patterns justify.
- **Sunset shortlist:** **Windsurf.** The parked candidate from the last bake-off — one quarter on trial, no materialised demand, no eval evidence that it outperforms Cursor Business on the team's workflows. Chapter 5: *"A tool with half the team at stage-1-floor and no stage-3 or -4 users is a candidate for sunset — the demand did not materialise."* Chapter 7's sunset discipline: status change to Sunset-pending; communication to the team; execution of the exit plan; retention in the registry for ≥ 4 quarters.
- **Stage-pin changes** (from the pinned Q[N+1] shifts): Harper, Ingo, Jun, Dalia advance; Felix stays.
- **Commit-shape input to `ai-enablement-lead`** quarterly commit review: team is consuming ~$960 of a $1,200 committed Claude for Work share — under-consumption to flag at the Q[N+1] org commit review as commit-shape input (may inform renegotiation or re-allocation across teams).
- **Flagged risks:** Alex at stage-4 ceiling (pattern-building, feeding `mod-104` tile narrative); Felix stage-1 undershoot (routing to `mod-105` programme — not a budget risk).

### Step 6 — Diagnose your drift (10 min)

Tally your plan against the key. For each miss, write one paragraph:

- **If you proposed cutting Felix's budget:** this is the *underuse-as-overspend* drift — the exact Chapter 5 common mistake the chapter names: *"Caps on stages 1–2. Caps on learning-stage ICs starve the `mod-105` programme of the exploratory time it needs. The right signal here is floors, not ceilings."* Felix's undershoot is a `mod-105` programme signal — route it to the cohort owner, run a 1:1 to diagnose Failure-B, leave the budget alone.
- **If you proposed capping Alex:** this is the *3x-median-as-cap-trigger* drift. Chapter 5 is explicit: *"Is stage-4 usage inside the quarterly-review ceiling? Breach is a conversation — pattern-building (good, feed into `mod-104` narrative) or a side project on the corp licence (less good)."* Alex's pattern-building (shared slash commands, scheduled eval pipeline) is the *good* half of that signal; capping would prevent the team from producing the patterns the rest of the team will adopt.
- **If you rolled seats + tokens + enterprise-share into one number for finance:** this is the *one-number-to-finance* drift — the second Chapter 5 common mistake the chapter names. When Q[N+1]'s number is 8% higher than Q[N]'s because 4 ICs advanced stage, the finance partner cannot see the programme landing from a single line. The right shape is three layers broken out separately plus a projection narrative.
- **If your Q[N+1] projection was flat or ignored the stage-shifts:** this is the *no-stage-shift-projection* drift. Chapter 5: *"A budget that reports only current state projects as flat. The Chapter 5 projection is what makes the `mod-104` tile's narrative defensible."* A projection that anticipates the ~17% token rise (~8% on the total line once the Windsurf trial sunsets) *as programme-landing* is the narrative that survives the finance conversation; one that reports Q[N] forward is the narrative that reads as drift.
- **If you did not flag the Claude for Work under-consumption:** this is a quieter drift — the stranded-cost failure mode Chapter 5 names. $240/month under-consumed against an org commit, unflagged, becomes an $X/quarter stranded cost that the org commit review eventually surfaces; the manager's responsibility is to flag it as commit-shape input, not to absorb it silently.
- **If you aggregated stage across tools** (e.g., called Gita "stage 2 overall"): the discipline is per IC per tool per Chapter 5 (*"The budget is defined per IC per tool. A stage-3 engineer at team median on Claude Code and running Cursor agent mode heavily will have usage on both; the per-tool accounting is what rolls up into the Chapter 7 registry."*). Rolling up loses the tool-specific signal that stage-shift projections depend on.
- **If your time-per-section was over 12 minutes on more than two:** you are probably re-deriving the stage ladder rather than operating against it (Chapter 5 is explicit: *"Does not re-derive the stage ladder. The ladder is in `mod-105` Chapter 4. This chapter operates it against the composed budget."*).

## Expected output

A file `lab-02-distribution-plan.md` with seven sections in the Step 1 template, plus a diagnosis section covering every drift from the key. Roughly 2 pages total; 1 page for the diagnosis.

Something like:

```
Section II — Token budget layer (Claude Code)
  Stage 1 (5 ICs: Felix, Gita, Harper, Ingo, Jun) × $40 floor = $200
  Stage 2 (2 ICs: Dalia, Esen)                    × $80 floor = $160
  Stage 3 (2 ICs: Blake, Chen)                    × $120 median = $240
  Stage 4 (1 IC: Alex)                            × $360 ceiling (reviewed) = $360
  Total projected: $960/month
  Actual current month: $987 (within Ch. 5 posture)

  ✅ Per-IC per-tool stage respected (Gita stage-1 for Claude despite stage-2
     Cursor pin).

Section VI — Monthly review signals
  Alex   $380/mo  — stage-4 ceiling-approach — pattern-building (shared slash
                    commands, scheduled pipeline) — quarterly conversation,
                    not cap.  ✅
  Felix  $20/mo   — stage-1 undershoot ~50% — mod-105 programme signal — 1:1
                    to diagnose Failure-B, no budget cut.  ✅ caught the trap;
                    initial reflex was to cut budget — Ch. 5 "floors are a
                    review signal, not a procurement signal" caught it.
  Chen   $140/mo  — ~17% above median — within normal variance.
  (No other ICs produce actionable signals.)
```

## Checkpoint

Before moving on to Lab 03 (due-diligence grading) or starting [Exercise 03](../exercises/exercise-03-tool-budget-and-token-budget-distribution.md) on your own team's budget, you should be able to answer **yes** to all six:

- Did you break out **all three layers** (seat, token, enterprise commit) separately — rather than rolling into a single team-AI line for finance?
- Did you catch Felix's **undershoot as a `mod-105` signal**, not a budget-reduction target — recognising that caps on stages 1–2 are one of the Chapter 5 common mistakes?
- Did you catch Alex's **3x-median spend as pattern-building**, not a cap trigger — recognising that stage-4 ceiling-approach can be the good half of the signal, feeding the `mod-104` tile narrative?
- Did you produce a **stage-shift projection** for Q[N+1] that anticipates the 8% rise *as programme-landing*, not as drift — and expressed the narrative in the one-paragraph pattern Chapter 5 names?
- Did you honour per-IC per-tool stage pins — recognising that an IC at Cursor-stage-2 and Claude-stage-1 is budgeted separately per tool?
- Did you **flag the Claude for Work under-consumption** as commit-shape input to `ai-enablement-lead`, rather than absorbing it silently — recognising that stranded commit share is a failure mode Chapter 5 names?

If any answer is no, re-read the relevant Chapter 5 section (*"Token budget distribution"*, *"Enterprise commitment handling"*, *"Monthly and quarterly usage review"*, or *"Common mistakes when first distributing"*) before running [Lab 03](lab-03-due-diligence-record-grading-on-composite-vendor-packets.md) or starting [Exercise 03](../exercises/exercise-03-tool-budget-and-token-budget-distribution.md) on your real team's budget.
