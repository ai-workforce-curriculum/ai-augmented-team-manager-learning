# Lab 01 — Ritual Calendar Audit on a Composite Team's Fifteen-Ritual Calendar

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 2 (the ritual inventory; Lencioni's four meeting types; tile-anchor discipline; calendar-budget math; audit cadence), with side-checks against Chapter 1 (scope — the calendar is a team-scope artifact; cross-functional rituals the team attends but does not own are time costs, not audit targets), Chapter 5 (ADR-style decision-log entries for material retirements), and Chapter 7 (the ritual calendar as layer 2 of the composed operating system).
**Complements, does not duplicate:** [Exercise 01](../exercises/exercise-01-ritual-calendar-audit-and-refresh.md) asks you to audit **your own team's** calendar — real rituals, real tiles, real partners, real retirements. This lab hands you a pre-baked calendar from a composite team so you can **calibrate your audit reflexes** — tagging each ritual with exactly one Lencioni type, catching the overloaded-slot smell before it hides as efficiency, treating tile anchors as binding, computing calendar-budget % honestly, and making retirement decisions concrete enough to produce a Chapter 5 decision-log entry — before you spend two hours on your own team's audit whose first conversation with a partner about a retired cross-functional ritual exposes a classification you had not fully worked through.

## Objective

Given the composite "Riverline" team's fifteen-ritual calendar below, produce an audit packet with: (i) a **per-ritual Lencioni classification** (daily check-in / weekly tactical / monthly strategic / quarterly off-site review / overloaded); (ii) a **defended-tile check** (named tile or "no tile — judgement call" with one-sentence justification); (iii) a **signal-of-decay check** (does the raw observation show the ritual is earning its slot?); (iv) a **per-ritual annual cost** using Chapter 2's `attendees × slot length × annual frequency` formula and a **calendar-budget %** against the team's ~2,000 person-hr/yr/head capacity; (v) a **retirement / right-size / split / keep decision** per ritual with a one-sentence rationale citing the Chapter 2 anchor that produced it; and (vi) two **Chapter 5 ADR-style decision-log entries** for the two material changes the audit should produce. Then compare against the answer key.

Target: **you match the Lencioni classification on at least twelve of fifteen rituals, you catch the three deliberately-planted traps (an overloaded slot disguised as a "weekly team meeting"; a ritual with no defended tile that reads as "keep because we always do it"; a cross-functional ritual the manager cannot unilaterally retire), you compute calendar-budget % within 2 percentage points of the key, and your retirement decisions are specific enough that a successor reading your decision-log entries could reconstruct the audit's reasoning.** The reading drifts this lab is designed to catch — *"a weekly team meeting that covers blockers, strategy, and open discussion is efficient"*, *"we don't need a defended tile for the ritual that's always been there"*, and *"the calendar doesn't actually cost that much because each meeting is short"* — are the ones Chapter 2 flags as the most common audit shortcuts.

## Prerequisites

- Chapter 2 read end-to-end — especially the ritual inventory, *"Lencioni's four meeting types"* (including the four common mis-classifications), *"Every ritual justifies itself against a dashboard tile"*, the *"calendar budget"* arithmetic, and the audit cadence (annual full / quarterly spot / event-triggered).
- Chapter 5 skimmed — the ADR-style decision-log template fields.
- Chapter 1 skimmed — the ritual calendar as layer 2 of the operating system and the Monday-morning successor test.
- Chapter 7 skimmed — the ownership boundary (what the manager owns versus what the manager attends).
- A blank file for your audit packet.
- A timer.

## The fictional context

> **"Riverline" team, Glenthorpe Health (a mid-market US digital-health company, Boston-headquartered).** Nine people: one manager, eight engineers (2 stage-1, 3 stage-2, 2 stage-3, 1 stage-4 on the `mod-105` ladder). Primary codebases: a patient-portal web app (React / TypeScript) and a care-coordination services tier (Python / FastAPI). Work mix: feature work (~55%), platform / observability (~20%), eval and review-standard investment (~15%), incident response (~10%). The team handles **PHI (HIPAA scope)** in the services tier, flagged **Restricted** on the inherited `mod-110` data-class × tool-class matrix. Delegation-ladder (`mod-106` Ch. 2): 85% human-with-AI-support, 10% review-required agent, 5% scheduled fully-automated. The team is five quarters into the mod-101–111 track; this is the **first** annual calendar audit.
>
> **Dashboard tiles in scope** (from the team's `mod-104` dashboard): DORA lead-time, DORA change-failure rate, DX Core 4 time-to-ship, SPACE collaboration index, flow efficiency, AI-cost tile, AI-adoption curve, review-rejection rate, eval-regression count, review-latency, novel-workflow adoption rate (from `mod-106`), stage distribution (from `mod-105`), gap-register open count (from `mod-110`), incident count by class (from `mod-109`), AI-cost delta vs projection (from `mod-111`).
>
> **Partnerships** per the Chapter 3 grid: Product partner (J. Alvarez, PM); Platform / DevEx counterpart (K. Owusu, EM — two teams over); Design-systems lead (R. Mehta); Data / Analytics partner (S. Lin); AI-Governance peer (M. Kowalski, `ai-risk-engineer`, care-coordination cluster).
>
> **Calendar snapshot** (recurring events from the last four weeks; cadence, slot length, attendees, defended-tile claim-as-written-in-the-invite, and the manager's recollection of the last 4–8 sessions):

```
# RITUAL                    CADENCE / SLOT       ATTENDEES         INVITE'S "DEFENDED TILE"              RAW OBSERVATIONS (last 4–8 sessions)

 1 Standup                  Daily, 15 min        9 (team)          Flow blocker count / WIP              Runs 22–28 min most days; last 6 of 8 ended with
                                                                                                         a technical sidebar; the manager runs the
                                                                                                         sidebars rather than defer them.

 2 Sprint planning          Biweekly, 60 min     9 (team)          DORA lead-time; flow efficiency       Runs to time; agenda tight; stories are refined.
                                                                                                         Most recent 4 sessions produced the sprint commit
                                                                                                         without overflow.

 3 Sprint review / demo     Biweekly, 45 min     9 + 2 (team + PM) Product-outcome tile; demo attend.    PM attends; last 4 demos had material stakeholder
                                                   + 1 designer                                          feedback; one shipped feature changed scope as a
                                                                                                         result.

 4 Retrospective            Biweekly, 60 min     9 (team)          Amendment land-rate; repeat-inc. rate Last 6 retros produced 2–4 action items each; 70%
                                                                                                         of action items have landed within the following
                                                                                                         sprint.

 5 Weekly team meeting      Weekly, 60 min       9 (team)          "Alignment"                           Agenda in order: 20 min this-week blockers; 20 min
                                                                                                         Q1 strategy discussion; 20 min open discussion.
                                                                                                         Manager considers "efficient use of time."

 6 1:1s                     Weekly, 30 min each  Manager × 8 ICs   mod-107 growth-plan progress          Four of eight run on cadence; four skip ~30% of
                                                                                                         sessions. Growth-plan referenced in 5 of 8.

 7 Dashboard review         Weekly, 30 min       5 (lead + 4 ICs)  Variance vs expected on headline      3 of last 4 sessions ended "nothing to flag, see
                                                                     tiles                               you next week"; one caught a review-latency
                                                                                                         regression that led to a Chapter 5 decision-log
                                                                                                         entry.

 8 Eval-set review          Monthly, 60 min      4 (lead + 3 ICs)  Eval-regression count; review-rej.    Monthly cadence held. Last 6 sessions added 2–4
                                                                                                         eval tasks each, retired 1–3 regressions each.

 9 Office hours             Weekly, 60 min       3 (lead + 2 ICs)  mod-103 review-standard adoption;     Attendance variable (0–5 ICs drop in). Lead reports
                                                                     mod-105 stage progression            "always someone with a real question"; 3 ICs
                                                                                                         reached stage-3 exit via office-hours coaching
                                                                                                         in the last two quarters.

10 "AI tools sync"          Weekly, 60 min       9 (team)          Novel-workflow adoption rate          Last 4: a vendor release-note demo, a repeat of
                                                                     (mod-106)                            an earlier demo, a general-chat session, and a
                                                                                                         cancelled meeting. Stage distribution has been
                                                                                                         stable for two quarters.

11 Roadmap sync (with PM)   Weekly, 45 min       Manager + J.A.    Roadmap-vs-delivered variance;        Runs to time; priority-swap decisions executed
                                                                     outcome tile                         here per Chapter 3 grid; no missed decisions this
                                                                                                         quarter.

12 Platform / DevEx sync    Monthly, 60 min      Manager + K.O.    DX Core 4; shared-infra investment    Runs on cadence; last 3 sessions produced one
                                                                                                         tool-standardisation discussion that routed to the
                                                                                                         Chapter 3 grid's "tool standardisation disputes"
                                                                                                         row; the row has been dormant since.

13 Governance packet sync   Quarterly, 90 min    Manager + M.K.    Gap-register open count; routing      Last 2 cycles: packet lands on time; one gap
                                                                     latency                              closed, one opened and routed upward.

14 Tool-registry review     Quarterly, 120 min   Manager + K.O.    AI-cost tile; usage-per-seat;         Last 2 quarters: one sunset (a `competitor-tool`),
                                                   + 2 ICs           stage-aligned budget distribution    one trial admission, registry entries re-dated.

15 Company all-hands        Monthly, 60 min      9 (team)          — (not owned by team)                 Standing attendance; manager does not own the
                                                                                                         ritual; team does not control cadence or content.
                                                                                                         Included on the calendar as a time cost only.
```

Grade each ritual *as if you are the Riverline team manager running the first annual audit*, following Chapter 2's discipline. Do not invent facts beyond the snapshot; score only what the snapshot names.

## Steps

### Step 1 — Set up your audit packet (3 min)

Create a working file `lab-01-audit-packet.md` with this per-ritual template, repeated fifteen times:

```
Ritual #<n>: <name>
Cadence / slot: <from snapshot>

(i)   Lencioni type:
      daily check-in / weekly tactical / monthly strategic / quarterly off-site / overloaded
      Rationale (one sentence citing Chapter 2):

(ii)  Defended tile:
      <named tile> OR "no tile — judgement call: <one-sentence justification>"

(iii) Signal-of-decay check:
      earning / at-risk / decaying — <one sentence citing the raw observation>

(iv)  Annual cost:
      attendees × slot × annual frequency = <person-hr/yr>

(v)   Audit decision:
      retire / right-size / split / keep / not-in-scope
      Rationale (one sentence citing Chapter 2):
```

Also add two final sections to the file:

```
CALENDAR-BUDGET MATH
    Sum of annual costs for team-owned rituals: <person-hr/yr>
    Team capacity (9 × ~2,000):                 <person-hr/yr>
    Ritual load as % of capacity:               <%>
    Overspend threshold (Ch. 2):                sustainable ≤ ~10%; overspent 15–20%; meeting-augmented 25%+

DECISION-LOG ENTRIES
    Two ADR-style entries for the two material changes this audit should produce.
```

Time yourself. Target: ~3 minutes per ritual for the per-ritual template, ~5 minutes for the budget math, ~10 minutes for the two decision-log entries.

### Step 2 — Classify, defend, decay-check, cost every team-owned ritual (35–40 min)

Walk the fifteen rituals in order. For each, fill all five fields. Apply the Chapter 2 rules verbatim:

- *Overloaded slot:* a ritual that attempts more than one Lencioni type is overloaded; split or re-scope. Watch for weekly-tactical-pretending-to-be-monthly-strategic.
- *No defended tile:* a ritual without a specific tile is a judgement call made in the open; justify in one sentence or retire.
- *Signal-of-decay:* three consecutive sessions with weak content or a defended tile that has not moved in a year is a decay signal.
- *Not-in-scope:* cross-functional rituals the team attends but does not own are time costs, not audit targets — you cannot retire a ritual you do not own.

Do not fold cost into the Lencioni classification or into the retirement decision — the classification is about *purpose shape*, not cost; the decision is about *earning the slot*, not just about budget.

### Step 3 — Compute the calendar-budget % (5–8 min)

Sum the annual costs of the *team-owned* rituals (exclude #15 all-hands as attended-only; include 1:1 time). Divide by the team's annual capacity (9 × ~2,000 = 18,000 person-hr/yr). Compare the number to Chapter 2's thresholds: ~10% sustainable, 15–20% overspent, 25%+ meeting-augmented. Write a one-sentence read of what the number says about the current calendar shape.

### Step 4 — Write two ADR-style decision-log entries (10–15 min)

Pick the two most material changes from your Step 2 decisions. For each, write a Chapter 5 ADR-style entry with the full field set: ID, title, date (use `2026-11-20`), author (use "team manager"), status (Active), scope, context, decision, rationale, alternatives considered, reversal conditions, review date, links (plausible stubs). Each entry is 150–250 words.

### Step 5 — Compare against the answer key (10–15 min)

Read the key only after you have filled all fifteen per-ritual templates, computed the budget %, and drafted two decision-log entries.

#### Answer key — per-ritual classifications and decisions

- **#1 Standup.** Lencioni: **daily check-in**, but currently running as a hybrid weekly-tactical because of the 22–28-minute slip and the technical sidebars the manager runs inside the slot. Defended tile: **flow blocker count / WIP** — earning the slot *as a defended tile* but **decaying as a Lencioni type**. Chapter 2's Lencioni discipline: *"Standup as tactical. The standup becomes 30 minutes of problem-solving. Problem-solving belongs to the weekly tactical or the sidebar it triggers. The daily check-in exists to synchronise, not resolve."* Annual cost (as run): 9 × 25 min × 48 wk × 4 days ≈ **~720 person-hr/yr** (vs budgeted ~288 at a strict 10 min). **Decision: right-size** — enforce 10-minute discipline; sidebars moved to a 30-minute optional problem-solving block right after standup, opt-in for involved ICs only. No decision-log entry needed (standup-length discipline is not material at Chapter 5 threshold); note in the audit template.

- **#2 Sprint planning.** Lencioni: **weekly tactical** (biweekly cadence; operational commitment-level work). Defended tile: **DORA lead-time; flow efficiency** — earning. Annual cost: 9 × 60 min × 26 ≈ **~234 person-hr/yr**. **Decision: keep.**

- **#3 Sprint review / demo.** Lencioni: **weekly tactical** (biweekly; review-of-current-work; cross-functional attendance). Defended tile: **product-outcome tile + demo attendance as a stakeholder-alignment proxy** — earning (PM attendance; material stakeholder feedback). Annual cost: 12 × 45 min × 26 ≈ **~234 person-hr/yr**. **Decision: keep.**

- **#4 Retrospective.** Lencioni: **weekly tactical** (biweekly; inspect-and-amend). Defended tile: **amendment land-rate; repeat-incident rate** — earning (70% action-item land-rate). Annual cost: 9 × 60 min × 26 ≈ **~234 person-hr/yr**. **Decision: keep.**

- **#5 "Weekly team meeting."** Lencioni: **overloaded — the deliberately-planted trap.** The slot attempts (a) weekly tactical (this-week blockers), (b) monthly strategic (Q1 strategy), and (c) unclassified (open discussion). Chapter 2 names this verbatim: *"Weekly tactical pretending to be monthly strategic. 'We'll discuss the roadmap this week' — one weekly tactical in a quarter does not do the work of a monthly strategic session. The roadmap discussion needs its own slot or it does not happen."* Defended tile: none in the invite — *"alignment"* is not a tile. Annual cost: 9 × 60 min × 48 ≈ **~432 person-hr/yr**. **Decision: split and right-size** — the this-week-blockers content is already covered by standup (#1) + retro (#4); the Q1 strategy content needs a monthly strategic slot of its own (2–3 hr, monthly, deliberation-shaped); the open-discussion third is retired or moved to office hours (#9). Net: retire the weekly 60-min slot; add one monthly 120-min strategic slot (9 × 2 hr × 12 = ~216 person-hr/yr). **Net reclaim: ~216 person-hr/yr.** **This is decision-log entry #1 (material).**

- **#6 1:1s.** Lencioni: **weekly tactical** (coaching-shaped, not status-reporting). Defended tile: **`mod-107` growth-plan progress; `mod-108` calibration input** — mixed signal (half of the directs skip ~30%; growth plan referenced in 5 of 8). Annual cost: 1 × 30 min × 8 × 48 ≈ **~192 person-hr/yr**. **Decision: right-size (per-direct, not as a team standard)** — Chapter 2's starter guidance: *"1:1 cadence is not a team-calendar choice alone. Individual direct reports' needs vary (`mod-107` growth plans drive cadence); do not standardise 1:1 cadence in the audit without the directs' input."* The audit flags the skipping pattern as a 1:1 topic, not as a calendar choice. No decision-log entry from the audit; individual cadence changes get logged as `mod-107` growth-plan amendments.

- **#7 Dashboard review.** Lencioni: **weekly tactical** (variance-vs-expected inspection). Defended tile: **variance against expected on headline tiles** — at-risk (3 of last 4 sessions produced no action items). Chapter 2's starter guidance: *"The defended tile of a dashboard review is usually 'variance against expected', with signal-of-decay being 'three consecutive reviews with no action items.'"* Annual cost: 5 × 30 min × 48 ≈ **~120 person-hr/yr**. **Decision: right-size** — drop to biweekly cadence (consistent with `mod-104` dashboard review cadence Chapter 2 names for most teams); keep a weekly "look at the dashboard before standup" async habit. Biweekly cost: 5 × 30 min × 26 ≈ **~65 person-hr/yr**. **Net reclaim: ~55 person-hr/yr.** Not quite at material threshold alone; log as a cadence-change note in the audit template.

- **#8 Eval-set review.** Lencioni: **monthly strategic** (deliberation on eval-set composition; deeper than a weekly tactical). Defended tile: **eval-regression count; review-rejection rate** — earning (2–4 tasks added, 1–3 regressions retired per session). Annual cost: 4 × 60 min × 12 ≈ **~48 person-hr/yr**. **Decision: keep.**

- **#9 Office hours.** Lencioni: **weekly tactical** (open coaching surface, not strategic deliberation). Defended tile: **`mod-103` review-standard adoption; `mod-105` stage progression** — earning (3 ICs reached stage-3 exit via coaching). Annual cost: 3 × 60 min × 48 ≈ **~144 person-hr/yr** (modelled at the regular attendee set; variable drop-ins add ~20%). **Decision: keep.**

- **#10 "AI tools sync."** Lencioni: **monthly strategic drifting into weekly tactical.** Defended tile: **novel-workflow adoption rate** — decaying (stage distribution stable for two quarters; last 4 sessions are demos and a cancelled meeting). This is Chapter 2's **worked example scenario** — the chapter prescribes the retirement: *"The sync earned its slot in Q1–Q2 while the team was moving through enablement stages. In Q3 the stage distribution stabilised; the content thinned to repeats and demos; the defended tile is not moving. Retiring the weekly recurring slot. Replacing with a monthly 45-minute CoP session owned by the enablement champ."* Annual cost: 9 × 60 min × 48 ≈ **~432 person-hr/yr**. Replacement cost: 9 × 45 min × 12 ≈ **~81 person-hr/yr**. **Decision: right-size (retire weekly; replace with monthly CoP).** **Net reclaim: ~351 person-hr/yr.** **This is decision-log entry #2 (material).**

- **#11 Roadmap sync (with PM).** Lencioni: **weekly tactical** (cross-functional; mid-sprint priority swap row from the Chapter 3 grid runs here). Defended tile: **roadmap-vs-delivered variance; outcome tile** — earning. Annual cost: 2 × 45 min × 48 ≈ **~72 person-hr/yr**. **Decision: keep.** Chapter 2 starter guidance: *"Cross-functional rituals are harder to retire. You do not unilaterally retire a ritual your PM or Design partner owns half of."* The ritual is also *earning*, so retirement is not the question.

- **#12 Platform / DevEx sync.** Lencioni: **monthly strategic** (joint deliberation on platform direction; one Chapter 3 grid row has been dormant since last fired). Defended tile: **DX Core 4; shared-infra investment** — earning (produces at least one tool-standardisation discussion per session). Annual cost: 2 × 60 min × 12 ≈ **~24 person-hr/yr**. **Decision: keep.** Per Chapter 3 guidance in Chapter 7's retrospective: *"The platform-partnership grid row on 'tool standardisation disputes' has never fired… Decision: keep the row, it is cheap to have; add an open-loops note that the row is dormant."* Same discipline applies to the ritual itself.

- **#13 Governance packet sync.** Lencioni: **monthly strategic** (quarterly cadence; deliberation-shaped; cross-functional). Defended tile: **gap-register open count; routing latency** — earning. Annual cost: 2 × 90 min × 4 ≈ **~12 person-hr/yr**. **Decision: keep.** Chapter 2 starter guidance: *"Governance and tool-registry rituals are infrequent but load-bearing. A governance retro at semi-annual cadence and a tool-registry review at quarterly cadence are both legitimate; do not retire them because they are rare."*

- **#14 Tool-registry review.** Lencioni: **quarterly off-site review** (the quarterly `mod-111` Ch. 7 ritual; reset-shaped; wider attendee set). Defended tile: **AI-cost tile; usage-per-seat; stage-aligned budget distribution** — earning (one sunset, one trial admission per quarter in the recent record). Annual cost: 4 × 120 min × 4 ≈ **~32 person-hr/yr**. **Decision: keep.**

- **#15 Company all-hands.** **Not in scope for the audit.** Chapter 2 and Chapter 1 are explicit: *"Cross-functional rituals your team attends but does not own are in scope only as attended-time costs, not as audit targets — you cannot retire a ritual you do not own."* Note the attended time cost (9 × 60 min × 12 ≈ **~108 person-hr/yr**) as an operating-system overhead line, but do not propose a change.

#### Answer key — calendar-budget math

**Sum of team-owned ritual costs (at current shape):**

| Ritual | Current cost (person-hr/yr) |
|---|---|
| 1 Standup (as-run at 25 min) | ~720 |
| 2 Sprint planning | ~234 |
| 3 Sprint review | ~234 |
| 4 Retrospective | ~234 |
| 5 Weekly team meeting | ~432 |
| 6 1:1s | ~192 |
| 7 Dashboard review | ~120 |
| 8 Eval-set review | ~48 |
| 9 Office hours | ~144 |
| 10 AI tools sync | ~432 |
| 11 Roadmap sync | ~72 |
| 12 Platform sync | ~24 |
| 13 Governance packet sync | ~12 |
| 14 Tool-registry review | ~32 |
| **Subtotal (team-owned)** | **~2,930 person-hr/yr** |
| 15 All-hands (attended cost, out of scope) | ~108 |
| **Total ritual time on team calendar** | **~3,040 person-hr/yr** |

Team capacity: 9 × ~2,000 = **18,000 person-hr/yr**. Team-owned load: ~2,930 / 18,000 = **~16.3% of capacity.**

Per Chapter 2: *"This is a sustainable number; teams with calendars at 15–20% of capacity in rituals have crossed into overspend."* Riverline sits at the low-end of the overspend band. The one-sentence read: *"The calendar is in the overspend band primarily because of the overloaded 'weekly team meeting' (#5), the standup running at 25 minutes rather than 10 (#1), and the AI tools sync (#10) whose defended tile has decayed — the audit's two material retirements (#5, #10) plus the standup right-size reclaim ~800 person-hr/yr and move the team to ~12% of capacity, inside the sustainable band."*

The Step 4 decision-log entries should pick #5 (split + right-size weekly team meeting) and #10 (right-size AI tools sync, mirroring Chapter 2's worked example). The standup right-size is a note in the audit template, not a decision-log entry — the material-threshold line is a judgement call; Chapter 5's guidance is *"a trivial decision (adding a new eval task to the eval-set review) gets a one-line log entry; a material decision (retiring a ritual, amending a decision-rights row, changing the pre-read structure) gets the full template."*

#### Answer key — decision-log entry shapes

**DL-2026-11-20-001 — Split and right-size the "weekly team meeting" (#5).**

- **Scope:** team ritual calendar.
- **Context:** First annual audit (Exercise 01) of the Riverline ritual calendar. Slot #5 is a 60-min weekly running 20/20/20 across this-week blockers, Q1 strategy, and open discussion. Chapter 2 names the pattern verbatim as weekly-tactical-pretending-to-be-monthly-strategic; the slot has no defended tile and is overloaded by Lencioni classification.
- **Decision:** Retire the weekly 60-min slot on 2026-12-01. Add one monthly 120-min strategic slot (first Thursday, 10:00–12:00), Lencioni type *monthly strategic*, defended tile *outcome tile + quarterly roadmap variance*, owner manager + tech lead. Open-discussion content moves to office hours (#9); this-week blockers are already covered by standup (#1) and retro (#4).
- **Rationale:** Chapter 2 overloaded-slot discipline; the slot defends no specific tile; the strategic content has been structurally starved by the tactical minutes in the same slot.
- **Alternatives considered:** (a) keep and shorten to 30 min — rejected, the content mix is the problem, not the duration; (b) split into two weekly slots — rejected, weekly tactical is already covered; (c) retire outright with no replacement — rejected, the strategic deliberation is a real need.
- **Reversal conditions:** If the monthly strategic produces no decisions for two consecutive sessions, revisit — the strategic content may be better served by the quarterly tool-registry review (#14) or the quarterly off-site.
- **Review date:** 2027-03-01 (quarterly spot audit).
- **Links:** Chapter 2 audit template entry for #5; previous calendar invite; office-hours charter.

**DL-2026-11-20-002 — Right-size the AI tools sync (#10).**

- **Scope:** team ritual calendar; `mod-105` CoP schedule.
- **Context:** First annual audit. The weekly AI tools sync was added in Q1 after `mod-105` adoption; Riverline is now at stable stage distribution (2/3/2/1 across stages 1–4) for two quarters; last 4 sessions of the sync have been release-note demos, repeats, general chat, and a cancellation; the defended tile (novel-workflow adoption rate per `mod-106`) has not moved in the last two quarters.
- **Decision:** Retire the weekly 60-min slot on 2026-12-04. Replace with a monthly 45-min CoP session owned by the enablement champ (stage-4 engineer A.F.); each session has an explicit purpose (one novel-workflow demo per session, rotating demo owner); first session 2026-12-17.
- **Rationale:** Chapter 2 worked example; signal-of-decay ("four consecutive weeks of weak content; stage distribution stable for two quarters") met; cost (~432 person-hr/yr) is the second-largest team-owned ritual line after standup-as-run.
- **Alternatives considered:** (a) retire outright, no replacement — rejected, stage progression could regress if the CoP forum disappears; (b) biweekly rather than monthly — rejected, demo pipeline will not sustain biweekly novel content at current stage distribution; (c) keep weekly, reduce slot to 30 min — rejected, the content, not the duration, is the issue.
- **Reversal conditions:** If the `mod-106` novel-workflow-adoption-rate tile drops in Q1 2027, or if `mod-105` stage distribution regresses by two quarters, revisit with potential bi-weekly cadence.
- **Review date:** 2027-03-04 (quarterly spot audit).
- **Links:** Chapter 2 audit template entry for #10; previous ritual invite; CoP charter draft; `mod-105` stage-ladder current state; `mod-106` novel-workflow-adoption-rate tile URL.

### Step 6 — Diagnose your audit drift (5 min)

Tally your audit against the key. For each miss, write one sentence:

- **If you classified #5 "weekly team meeting" as a weekly tactical rather than overloaded:** this is the *efficiency-looks-like-classification* drift. Chapter 2's four common mis-classifications include this pattern by name; the manager's own description of the slot as *"efficient"* is a tell — efficient-looking slots that serve two Lencioni types are the archetype of overloaded.
- **If you kept #10 AI tools sync without a right-size because the stage distribution might regress later:** this is the *loss-aversion* drift. Chapter 2's worked example addresses it: right-size with a reversal condition; retirement is rarely elimination at team scope.
- **If you marked #15 all-hands for retirement:** this is the *scope-creep* drift Chapter 1 and Chapter 2 flag — *"you cannot retire a ritual you do not own."* Note the attended cost; do not propose a change.
- **If your calendar-budget % missed by >2 pp:** you probably used the as-invited standup length rather than the as-run length, or did not include 1:1 time, or included #15 all-hands in the team-owned subtotal. The arithmetic drifts when the inputs are generous to the calendar rather than honest about what the calendar costs.
- **If one or both decision-log entries omitted reversal conditions or review date:** this is the Chapter 5 *change-log-without-reversal* drift — the entry becomes a change-of-state note rather than a decision a successor can read in context. Add the reversal and review-date fields even when the decision feels obvious.
- **If you tried to classify #6 1:1 cadence as a team-wide audit decision:** this is the *standardise-what-is-personal* drift Chapter 2 flags — 1:1 cadence belongs to the directs' growth plans, not the team's audit output.

## Expected output

A file `lab-01-audit-packet.md` with fifteen per-ritual rows in the Step 1 template, the Step 3 calendar-budget math section, two Step 4 ADR-style decision-log entries, and a diagnosis section covering every classification or decision that differed from the key. Roughly 0.5–1 page per ritual on dense rows, less on quick ones; ~1 page for the budget section; ~0.5 page per decision-log entry.

Something like:

```
Ritual #5: Weekly team meeting
Cadence / slot: Weekly, 60 min

(i)   Lencioni type: overloaded — attempts weekly tactical + monthly strategic +
      unclassified in a single slot. Ch. 2: "a ritual that is more than one is a
      sign the slot is overloaded and should be split."
(ii)  Defended tile: none — "alignment" is not a tile.
(iii) Signal-of-decay: at-risk — the strategic third is structurally starved
      by the tactical minutes.
(iv)  Annual cost: 9 × 60 min × 48 = ~432 person-hr/yr.
(v)   Audit decision: split + right-size — retire weekly 60-min; add monthly
      120-min strategic; this-week content covered by #1 + #4; open discussion
      moves to #9. Net reclaim: ~216 person-hr/yr. Chapter 5 decision-log
      entry required.

✅ caught the overloaded-slot trap on first pass; initial reflex was to call
   it a weekly tactical because "it covered blockers" — Ch. 2's "one Lencioni
   type per slot" caught it.
```

## Checkpoint

Before moving on to [Lab 02](lab-02-pre-read-triage-on-three-composite-drafts.md) (pre-read triage) or starting [Exercise 01](../exercises/exercise-01-ritual-calendar-audit-and-refresh.md) on your own team's calendar, you should be able to answer **yes** to all six:

- Did you classify each ritual as **exactly one** Lencioni type (or overloaded) — not as a mix of two — and specifically catch #5 as overloaded rather than weekly tactical?
- Did you treat the defended-tile field as **binding** — flagging #5 (no tile) and #10 (tile decayed) as separate audit signals rather than folding them into a general "feels stale" judgement?
- Did you catch #15 all-hands as **not in scope** for the audit — noting the attended cost but making no retirement proposal — per the Chapter 1 / Chapter 2 scope boundary?
- Did your calendar-budget % land within 2 percentage points of the ~16% key figure — using the as-run standup length, including 1:1 time, excluding attended-only rituals from the team-owned subtotal?
- Did your two Chapter 5 decision-log entries name **reversal conditions** and **review dates** explicitly — making them readable by a successor six months later, not just change-of-state notes?
- Did you make at least one retirement or right-sizing decision — the Chapter 2 discipline that *"A calendar audit that produces zero retirements has not applied the discipline"* — rather than revalidating every ritual as "we always do it"?

If any answer is no, re-read the relevant Chapter 2 section (*"Lencioni's four meeting types"*, *"Every ritual justifies itself against a dashboard tile"*, *"The calendar budget"*, *"The audit cadence"*), Chapter 5's ADR-style template fields, or Chapter 7's ownership-boundary rows before running [Lab 02](lab-02-pre-read-triage-on-three-composite-drafts.md) or starting [Exercise 01](../exercises/exercise-01-ritual-calendar-audit-and-refresh.md) on your real team.
