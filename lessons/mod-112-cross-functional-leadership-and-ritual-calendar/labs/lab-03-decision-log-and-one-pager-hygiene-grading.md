# Lab 03 — Decision-Log and One-Pager Hygiene Grading on a Composite Operating-System Packet

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 5 (one-pager sections and honesty discipline; ADR-style decision-log template; decisions in-scope vs out-of-scope for the log; successor-readiness check), with side-checks against Chapter 1 (the Monday-morning successor test the whole module optimises for), Chapter 2 (the ritual-calendar changes a decision-log entry captures), Chapter 3 (the decision-rights grid references in one-pager and log entries), Chapter 4 (the pre-read is the quarterly artifact; the one-pager is the standing executive summary), and Chapter 7 (the operating-system retrospective reviews these two artifacts explicitly).
**Complements, does not duplicate:** [Exercise 04](../exercises/exercise-04-one-pager-and-decision-log-hygiene.md) asks you to author **your own team's** one-pager and seed the decision log — real team, real partners, real history. This lab hands you a composite team's one-pager plus five decision-log entries so you can **calibrate your grading reflexes** — spotting marketing voice in a one-pager that otherwise reads well, catching a decision-log entry with no reversal condition, distinguishing material from trivial decisions, recognising scope violations (individual performance, confidential personnel) that should never have landed in the log — before you spend two hours on your own packet whose first successor-readiness test surfaces a drift you had not learned to see.

## Objective

For the "Dunfern Logistics, Rate-Quoting team" composite packet below, produce a grading memo with: (i) a **one-pager grading** against Chapter 5's eleven sections plus the three honesty disciplines — marking each section `present and honest / present but weak / missing` and naming the specific violation per weak section; (ii) a **decision-log grading** on each of five entries — marking each `complete / weak / scope-violation`, verifying the ADR-style field set (ID, title, date, author, status, scope, context, decision, rationale, alternatives, reversal conditions, review date, links), and flagging any entry that should not have landed in the log at all; (iii) a **successor-readiness verdict** — can a competent peer manager read the one-pager in 10 minutes and the log in 30 minutes and pass the Monday-morning test; and (iv) a **named fix list** per weak or scope-violating artifact — specific enough that the drafting manager could execute them without re-reading the chapter. Then compare against the answer key.

Target: **you catch the marketing-voice drift in the one-pager (one glowing bullet with no attribution), the empty "what the team is not" section, the three decision-log drifts (one entry missing reversal conditions; one entry recording a confidential personnel decision; one entry recording a trivial change that could have been one line), and your named fixes are specific enough (section by section, field by field) that a drafting manager could execute them without re-reading the chapter.** The grading drifts this lab is designed to catch — *"a clean-looking one-pager is a trusted one-pager"*, *"any decision in a log is better than no log"*, and *"individual performance is team context so it belongs in the log"* — are the ones Chapter 5 flags as the most common first-pass hygiene misses.

## Prerequisites

- Chapter 5 read end-to-end — especially the eleven one-pager sections, *"The honesty discipline for the one-pager"*, the ADR-style decision-log template, *"Decisions that go in the log"* and *"Decisions that do not go in the log"*, and *"The successor-readiness check"*.
- Chapter 1 skimmed — the Monday-morning successor test.
- Chapter 2 skimmed — ritual-calendar changes are logged under the ADR template.
- Chapter 3 skimmed — grid changes are logged.
- Chapter 7 skimmed — the operating-system retrospective reviews these two artifacts and produces further log entries.
- A blank file for your grading memo.
- A timer.

## The fictional context

> **"Dunfern Logistics, Rate-Quoting team" composite packet.** Team: Rate-Quoting, Dunfern Logistics (6 engineers, 1 manager; UK operation). Manager: L. Nasser. The packet contains (a) the team's one-pager at v0.3 (last updated 2026-10-14) and (b) five decision-log entries from the last six months. The packet is drafted by a manager two months into the role; they have read mod-101 through mod-112 but this is their first pass at the composed artifacts. The company is running an internal operating-system-maturity review in two weeks; the composite peer-manager reviewer (you) is the first external reader.

Grade each artifact as if you are the sister-team peer manager running the Chapter 5 successor-readiness check (not the governance peer or the PM). The question you are applying is: *"Can a competent peer pick this team up cold on Monday and, by end of day, run the week, answer a partner's message, be legible to leadership, and flag the triggers — reading only these two artifacts plus their linked appendices?"*

---

### Artifact A — the team one-pager (v0.3, 2026-10-14)

> **Rate-Quoting Team — One-Pager — v0.3 — 2026-10-14**
>
> **1. The team in one sentence.** The Rate-Quoting team owns the AI-assisted rate-quotation workflow for mid-market freight customers in the UK region.
>
> **2. Composition.** Manager + 6 engineers (1 tech lead, 2 senior, 2 mid, 1 junior). Stage-ladder distribution: 1 at Stage 1, 2 at Stage 2, 2 at Stage 3, 1 at Stage 4. Enablement champ: A. Rourke (Stage 4). Review-standard owner: tech lead.
>
> **3. Workflow mix.** Feature work ~50%; platform / observability ~20%; review-standard and eval investment ~15%; incident response ~10%; discovery ~5%.
>
> **4. Measurement anchor.** [Dashboard URL]. Headline tiles this quarter: DX Core 4 time-to-ship, DORA change-failure rate, AI-cost delta vs projection.
>
> **5. Current roadmap arc.** Q4 commitments: ship v2 of the quote-ranking surface; close two high-priority platform tickets; land the design-system contribution for the confidence-UI pattern. [Roadmap URL].
>
> **6. Tool and governance posture.** Tool registry: 4 active (Cursor Business, Claude for Work Enterprise, GitHub Copilot Enterprise on org commit, a Linear-AI trial) [Registry URL]. Governance crosswalk current; 1 open gap (routed upward). [Gap register URL]. Incident retrospective backlog: 0.
>
> **7. Cross-functional partners.** Product: P. Evert (mid-market-freight PM). Platform/DevEx: K. Shaw (shared-platform EM, two teams over). Design-systems: R. Adeyemi. Data: S. Pandit. AI-Governance peer: M. Varga (`ai-risk-engineer`, freight-pricing cluster). [Decision-rights grid URL].
>
> **8. Ritual calendar at a glance.** Standup daily; sprint planning biweekly; demo biweekly; retrospective biweekly; 1:1s weekly; office hours weekly; roadmap sync with Product weekly; CoP monthly; governance packet sync quarterly; tool-registry review quarterly. [Full calendar URL].
>
> **9. Open loops.** *(none listed)*
>
> **10. What the team is not.** *(section omitted)*
>
> **11. Date, version, change log.** v0.3 — 2026-10-14. [Change log URL].
>
> **Executive-summary bullet (above the sections, as a one-line claim):** The Rate-Quoting team delivered a 31% year-over-year improvement in quote-to-ship time through AI adoption and is tracking to hit all Q4 roadmap commitments.

---

### Artifact B — five decision-log entries

#### Entry B1

> **ID:** DL-2026-05-02-001
> **Title:** Shift Tuesday standup to Monday
> **Date:** 2026-05-02
> **Author:** L. Nasser, team manager
> **Status:** Active
> **Scope:** Team ritual calendar
> **Context:** Tuesday standup conflicts with a new cross-team sync that landed last month.
> **Decision:** Move the standup from Tuesday 10:00 to Monday 10:00. Cadence and slot length unchanged.
> **Rationale:** Avoid conflict with the cross-team sync.

#### Entry B2

> **ID:** DL-2026-06-18-002
> **Title:** Retire the weekly AI tools sync
> **Date:** 2026-06-18
> **Author:** L. Nasser, team manager
> **Status:** Active
> **Scope:** Team ritual calendar
> **Context:** The weekly 60-minute AI tools sync was added in Q4 last year; the team has now stabilised at Stage 2–4 across the ladder; the last five sessions have thinned to vendor-release-note demos and repeat content; the defended tile (novel-workflow adoption rate, `mod-106`) has not moved in two quarters.
> **Decision:** Retire the weekly 60-min slot on 2026-07-01. The forum is not replaced in this entry — a separate CoP proposal is pending.
> **Rationale:** Chapter 2 audit template shows the ritual is no longer defending its tile; ~288 person-hr/yr cost outweighs current value delivered.
> **Alternatives considered:** Keep weekly, reduce to 30 min — rejected because the content, not the duration, is the issue.

#### Entry B3

> **ID:** DL-2026-07-30-003
> **Title:** Add decision-rights row for novel AI-interaction UI patterns
> **Date:** 2026-07-30
> **Author:** L. Nasser, team manager (joint with R. Adeyemi, design-systems lead)
> **Status:** Active
> **Scope:** Chapter 3 Design-partnership grid
> **Context:** Team shipped a quote-confidence-UI pattern ahead of the design system in Q2; feedback-to-system did not happen; two sister teams shipped incompatible patterns; a customer-facing consistency issue was raised; design-systems lead and manager held a 30-min joint conversation to locate the missing decision right.
> **Decision:** Add a grid row: *"Novel AI-interaction UI pattern (inside or outside design system)"*. Recommend: Team via tech lead or designer embed. Agree: Design-systems lead. Perform: Team to prototype; Design to formalise. Input: PM; other teams. Decide: Design-systems lead. Ritual: Monthly design-system review (team rotation attends).
> **Rationale:** The joint had no written decision right; the missing row was exposed by the Q2 incident-adjacent conflict.
> **Alternatives considered:** (a) Keep informal: rejected, the Q2 pattern shows informal approval does not compose at multi-team scale. (b) Require pre-approval for *any* AI-interaction UI: rejected, too slow for team pattern velocity.
> **Reversal conditions:** If the monthly design-system review cannot keep up with team pattern velocity, revisit in Q2 2027 with a design-systems-contributor model.
> **Review date:** 2027-02-01.
> **Links:** [Chapter 3 grid URL]; [design-system contribution process]; [Q2 pattern post-mortem].

#### Entry B4

> **ID:** DL-2026-09-11-004
> **Title:** Address IC performance concern on mid-tier engineer
> **Date:** 2026-09-11
> **Author:** L. Nasser, team manager
> **Status:** Active
> **Scope:** Team performance management
> **Context:** Mid-tier engineer [name redacted in this grading extract — but named explicitly in the actual log entry] has shown declining output since Q2; manager has had three 1:1 conversations; HR partnership channel opened on 2026-09-04.
> **Decision:** Place engineer on a performance-improvement plan effective 2026-09-15 with a 60-day review window; specific milestones named; HR to co-manage.
> **Rationale:** Individual performance has not responded to coaching; formal PIP is the next step per `mod-108`.
> **Alternatives considered:** Continue informal coaching — rejected, three cycles of informal coaching have not produced improvement.
> **Reversal conditions:** If milestones are met at the 30-day check-in, PIP is lifted; if not, continue to 60-day decision.
> **Review date:** 2026-10-15 (30-day) and 2026-11-14 (60-day).
> **Links:** [HR partnership record]; [1:1 notes — restricted]; [`mod-108` PIP template].

#### Entry B5

> **ID:** DL-2026-10-02-005
> **Title:** Sunset Linear AI trial; standardise on Jira AI for issue-triage workflow
> **Date:** 2026-10-02
> **Author:** L. Nasser, team manager
> **Status:** Active
> **Scope:** Tool registry, team-scope workflow catalog
> **Context:** Q3 tool-registry review surfaced that the Linear AI trial (admitted 2026-04-15) has not landed for the team: the team's issues live in Jira (Dunfern-wide Jira commit), the Linear AI assumed-workflow does not route through to the team's actual backlog, and the three ICs piloting Linear AI have each independently reverted to manual triage. The Jira AI feature set has matured since the trial admission; the org's Jira AI tier is zero-retention Enterprise on the Atlassian MSA.
> **Decision:** Sunset the Linear AI trial on 2026-10-31. Record as Status=Sunset in the registry with full historical reason. Admit Jira AI (Atlassian Enterprise tier) to the active registry effective 2026-11-01 as the team's Tier-2 agentic issue-triage tool. Named owner: tech lead. Sunset cost: reclaim three Linear AI seats; no wrap-layer to archive.
> **Rationale:** (1) Chapter 2 and Chapter 3 of `mod-111`: the trial did not survive the data-handling gate at the workflow level (the workflow does not run); (2) Chapter 5 of `mod-111`: Jira AI is zero seat-cost (included in the Atlassian commit) and the token distribution is predictable; (3) the three-partner due-diligence pattern from `mod-111` Chapter 6 was completed for Jira AI on 2026-09-20.
> **Alternatives considered:** (a) Extend the Linear AI trial to Q4 — rejected, the workflow mismatch is structural, not a maturity gap. (b) Run both — rejected, two issue-triage tools fragment the team's workflow catalog.
> **Reversal conditions:** If Jira AI's model-provenance clause changes materially (per `mod-111` Chapter 7 off-cycle trigger), revisit. If Linear's Jira-integration roadmap ships in H1 2027 and resolves the structural mismatch, Linear AI may be re-admitted on an explicit new decision-log entry (not silent re-adoption).
> **Review date:** 2027-01-02 (quarterly tool-registry review).
> **Links:** [Q3 tool-registry review notes]; [Jira AI due-diligence packet]; [Linear AI sunset communication]; [`mod-111` Chapter 7 audit entry].

---

## Steps

### Step 1 — Set up your grading memo (3 min)

Create a working file `lab-03-grading-memo.md` with these sections:

```
ONE-PAGER GRADING (Artifact A)

Section-by-section (sections 1–11):
<per-section row: present-and-honest / present-but-weak / missing, with one-sentence rationale>

Honesty disciplines:
    Open-loops section non-empty?              y / n
    "What the team is not" section present?    y / n
    AI-ROI claims qualified with attribution?  y / n

Overall one-pager verdict:
    successor-ready / needs revision / marketing-voice / violates honesty discipline

Named fix (one paragraph, section-and-field specific):

---

DECISION-LOG GRADING (Artifact B — five entries)

Per-entry row:
    B1: complete / weak / scope-violation — <one-sentence violation>
    B2: ...
    B3: ...
    B4: ...
    B5: ...

ADR-style template check per entry (pass / fail per field):
    ID, Title, Date, Author, Status, Scope, Context, Decision, Rationale,
    Alternatives, Reversal conditions, Review date, Links

Overall decision-log verdict:
    successor-ready / needs revision / scope violation present

Named fix per weak or scope-violating entry:

---

SUCCESSOR-READINESS VERDICT

Can a competent peer manager:
    Run the week from the one-pager + ritual-calendar link?     y / n
    Answer a partner's message from the log + grid link?         y / n
    Be legible to leadership from the one-pager?                 y / n
    Flag the triggers from the log + gap-register link?          y / n

Overall:
    successor-ready / needs revision / not successor-ready

Named fix list (bulleted; section-and-artifact specific):
```

Time yourself. Target: ~15 minutes on the one-pager, ~25 minutes on the five log entries, ~5 minutes on the successor-readiness block, ~10 minutes on the comparison.

### Step 2 — Grade the one-pager (Artifact A) (12–15 min)

Walk the eleven sections per Chapter 5. Grade each `present-and-honest`, `present-but-weak`, or `missing`. Also check the three honesty disciplines. Chapter 5's binding rules:

- *Open loops section cannot be empty.*
- *What the team is not section exists.*
- *No AI-ROI headline number without the qualifier.*

### Step 3 — Grade the five decision-log entries (20–25 min)

For each entry, verify the ADR-style template fields are present and the entry is in-scope for the log. Chapter 5's binding rules:

- *Decisions that go in the log:* ritual-calendar changes; decision-rights grid changes; pre-read structure changes; tool-registry adds/sunsets; policy amendments; partnership changes; review-standard amendments; enablement-program changes.
- *Decisions that do not go in the log:* individual performance decisions; confidential personnel discussions; sprint-level tactical choices.
- *Material decisions get the full template; trivial decisions get one-line entries.* The template is scaled, not uniform.

Mark any entry that should not be in a team-visible decision log at all as a **scope violation**, not as a weak entry.

### Step 4 — Successor-readiness verdict (5 min)

Apply the Chapter 1 and Chapter 5 Monday-morning successor test to the composite packet. Can a peer manager read the one-pager in 10 minutes and the log (filtered to the five entries) in 30 minutes and answer *yes* to all four readability questions? If any single `n`, the packet is not successor-ready.

### Step 5 — Compare against the answer key (10–15 min)

Read the key only after you have graded both artifacts.

#### Answer key — Artifact A (the one-pager)

**Per-section grading:**

- **Section 1 — The team in one sentence:** *present and honest*. Specific scope (AI-assisted rate-quotation workflow), domain (mid-market freight customers), region (UK). Matches Chapter 5's example shape.
- **Section 2 — Composition:** *present and honest*. Headcount, stage distribution, specialist roles.
- **Section 3 — Workflow mix:** *present and honest*. Percentages present; totals ~100%.
- **Section 4 — Measurement anchor:** *present and honest*. Dashboard URL plus three headline tiles.
- **Section 5 — Current roadmap arc:** *present and honest*. One sentence summarising Q4; roadmap URL.
- **Section 6 — Tool and governance posture:** *present and honest*. One line each; URLs present; specific tool names; gap count stated.
- **Section 7 — Cross-functional partners:** *present and honest*. Named people, specific scopes, grid URL.
- **Section 8 — Ritual calendar at a glance:** *present and honest*. The most load-bearing rituals and cadences; full calendar URL.
- **Section 9 — Open loops:** **present but weak — empty section.** This is a **deliberately-planted trap**. Chapter 5 is explicit: *"Open loops section cannot be empty. A team with no open loops is either at an unusual moment of steady state (one quarter per year, if ever) or is hiding things. Peers who see an empty open-loops section stop trusting the document."* The surrounding content — Q4 commitments in flight, an open governance gap, a design-system contribution, a tool trial underway — makes it very unlikely the team genuinely has zero open loops. The fix repopulates with three to five dated items with named owners: *"(1) Confidence-UI design-system contribution: joint with Design, 2026-11-30 target. (2) Governance gap on [specific workflow]: routed to governance peer, Q4 close target. (3) Linear AI trial: owner tech lead, decision 2026-10-31. (4) Confidence-UI rollout to v2 quote-ranking surface: owner stage-3 engineer, Q4 ship."* If the team genuinely is at steady state, state so with the explicit Chapter 5 phrasing: *"No open loops this period; next scheduled triggers: Q4 tool-registry review, Q4 governance retrospective."*
- **Section 10 — What the team is not:** **missing — the second deliberately-planted trap.** Chapter 5 is explicit: *"What the team is not section exists. A team that does not know what it is not has not scoped itself. Peers reading this section learn what not to escalate to the team, which is more useful than learning what to escalate."* The fix adds one sentence naming the scope boundary: *"The team does not own the underlying freight-pricing model (owned by the Pricing-ML team) or the long-haul-contract-pricing workflow (owned by the Enterprise-Pricing team); we own the mid-market rate-quoting assist layer only."*
- **Section 11 — Date, version, change log:** *present and honest*. v0.3, 2026-10-14, URL.

**Honesty-discipline check:**

- Open-loops section non-empty? **N** (empty).
- "What the team is not" section present? **N** (missing).
- AI-ROI claims qualified with attribution? **N — the third deliberately-planted trap.** The executive-summary bullet reads *"delivered a 31% year-over-year improvement in quote-to-ship time through AI adoption"*. Chapter 5: *"No AI-ROI headline number without the qualifier. If the one-pager cites a productivity gain, cite the [`mod-104` Ch. 1](../../mod-104-productivity-measurement-and-ai-roi/01-metrics-that-separate-gain-from-theatre.md) anti-theatre framing in one sub-clause… '22% faster with AI' is marketing and will be read as marketing."* The claim *"through AI adoption"* names AI as the sole driver, which is marketing voice. The fix: rewrite as *"Quote-to-ship time trend is ↓ 31% year-over-year; attribution across AI adoption, platform investment, and roadmap-composition is in the backing dashboard. Qualitative-signal caveats are in the Q3 pre-read anti-theatre paragraph."*

**Overall one-pager verdict:** *marketing-voice violates honesty discipline*. Nine of eleven sections are present and honest; the two missing / weak sections and the unqualified AI-ROI claim mean the artifact fails the Chapter 5 trust test. *"Marketing-shaped one-pagers teach peers to read around them rather than from them — which is exactly what Chapter 5's honesty discipline exists to prevent."*

**Named fix for the one-pager:** Add the open-loops section with 3–5 named-owner dated items; add the "what the team is not" section with one specific scope-boundary sentence; rewrite the executive-summary bullet to separate the 31% trend from the driver attribution and route attribution to the dashboard. Keep everything else. Re-publish as v0.4.

#### Answer key — Artifact B (the five decision-log entries)

**Entry B1 (Shift Tuesday standup to Monday):** **weak — missing fields, also probably trivial.**

- **ADR field check:** ID ✓, Title ✓, Date ✓, Author ✓, Status ✓, Scope ✓, Context ✓ (thin), Decision ✓, Rationale ✓, **Alternatives ✗ (missing), Reversal conditions ✗ (missing), Review date ✗ (missing), Links ✗ (missing).**
- **Violation:** The entry is a trivial cadence change (moving a standup from one day to another). Chapter 5: *"The template is scaled. Not every decision is a six-field ADR — a trivial decision (adding a new eval task to the eval-set review) gets a one-line log entry; a material decision (retiring a ritual, amending a decision-rights row, changing the pre-read structure) gets the full template."* B1 should be either (a) a one-line entry (*"DL-2026-05-02-001: Moved standup from Tuesday 10:00 to Monday 10:00 to resolve conflict with the new cross-team sync. — L. Nasser, 2026-05-02."*) or (b) amended to the full template with reversal conditions (e.g., *"if the cross-team sync moves, revisit the standup slot"*) and review date. The current entry is in the awkward middle — half the fields, not readable to a successor who might wonder "what else was considered?" and not concise enough to be the one-line scaled version.
- **Fix:** Collapse to a one-line entry. The scaled template exists so trivial decisions do not consume the full ADR shape.

**Entry B2 (Retire the weekly AI tools sync):** **weak — missing reversal conditions, review date, and links; also mis-scoped replacement.**

- **ADR field check:** ID ✓, Title ✓, Date ✓, Author ✓, Status ✓, Scope ✓, Context ✓ (specific), Decision ✓, Rationale ✓, Alternatives ✓ (one), **Reversal conditions ✗ (missing), Review date ✗ (missing), Links ✗ (missing).**
- **Violation:** The decision is material (retiring a ritual with ~288 person-hr/yr cost); it earns the full template. The missing reversal conditions and review date are exactly the Chapter 5 failure mode: *"A log of 'we decided X on date Y' without why X and what would reverse it is a log that cannot be read. The successor sees that a decision was made; they do not know whether the conditions that justified it still hold."* Chapter 2's worked example on this exact retirement includes the reversal condition verbatim (*"if novel-workflow adoption tile drops in Q1 next year, or if stage distribution regresses, revisit with potential bi-weekly cadence"*) and the review date (quarterly spot audit). The *"the forum is not replaced in this entry — a separate CoP proposal is pending"* line is a smell: Chapter 2's discipline is *"Retirement is usually right-sizing, not elimination."* The right shape is one entry that retires-and-replaces, not two entries one of which is still pending.
- **Fix:** Add the reversal conditions, review date, and links (Chapter 2 audit template, Chapter 5 template reference, the pending CoP proposal URL). Fold the pending CoP replacement into the same entry (or supersede-link the forthcoming CoP entry to this one). Add a second alternative considered (retire outright with no replacement — rejected because stage progression could regress).

**Entry B3 (Add decision-rights row for novel AI-interaction UI patterns):** **complete.**

- **ADR field check:** ID ✓, Title ✓, Date ✓, Author ✓ (joint — a legitimate shape), Status ✓, Scope ✓, Context ✓ (specific, includes the trigger), Decision ✓ (full RAPID-shape row), Rationale ✓, Alternatives ✓ (two), Reversal conditions ✓, Review date ✓, Links ✓.
- **Verdict:** Model entry. Mirrors Chapter 3's worked example on this exact scenario — the Q2 pattern post-mortem that produced the missing decision-rights row. Successor-readable in under two minutes.

**Entry B4 (Address IC performance concern on mid-tier engineer):** **scope violation — the deliberately-planted trap.**

- **ADR field check:** ID ✓, Title ✓, Date ✓, Author ✓, Status ✓, Scope ✓ (technically — "Team performance management"), Context ✓, Decision ✓, Rationale ✓, Alternatives ✓, Reversal conditions ✓, Review date ✓, Links ✓.
- **Violation:** The template is *complete*; the entry is *out of scope for a team-visible decision log*. Chapter 5 is explicit: *"Decisions that do not go in the log: Individual performance decisions. Belong to [`mod-108`](../../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/) private records. Confidential personnel discussions. Belong to HR partnership channels."* An IC-named PIP in the team-visible log is both a breach of confidentiality (the engineer's PIP state is visible to peers, successors, and anyone else reading the log) and a Chapter 5 scope violation (*"The log is team-visible and successor-readable. A log that is secretly selective is worse than no log; peers learn to read around it"* — the inverse also applies: a log that is *insecurely non-selective* breaks trust in the artifact's scope). The 1:1-notes link marked "restricted" is a signal the author knew the content was sensitive and tried to compensate with an access restriction on the sub-link — but the entry itself is in the team-visible log.
- **Fix:** **Remove from the team-visible decision log entirely.** Move to the `mod-108` private PIP record. Do not leave a placeholder referencing the move (that itself re-exposes the content). The team-visible log does not record that a team member was PIP'd; the private performance record does.

**Entry B5 (Sunset Linear AI trial; standardise on Jira AI):** **complete.**

- **ADR field check:** ID ✓, Title ✓, Date ✓, Author ✓, Status ✓, Scope ✓, Context ✓ (specific — the structural workflow mismatch, not a maturity gap), Decision ✓ (specific — sunset-date, admission-date, owner, sunset-cost), Rationale ✓ (three numbered reasons citing `mod-111` chapters), Alternatives ✓ (two), Reversal conditions ✓ (two conditions, both specific), Review date ✓, Links ✓ (four links including Chapter 7 audit entry).
- **Verdict:** Model entry. Mirrors Chapter 5's worked example on `competitor-tool` sunset. Successor-readable in under three minutes; a new engineer joining the team could read it and understand not just the current state but the trajectory of decisions that got there.

**Overall decision-log verdict:** *scope violation present* (B4); two further entries need the full ADR template or a scaled version (B1, B2); two are model entries (B3, B5). The log fails the successor-readiness check because the scope violation on B4 undermines trust in the log as an artifact a successor can read without worrying about what else is incorrectly recorded.

**Named fix per entry:**

- **B1:** Collapse to a one-line scaled entry.
- **B2:** Amend to full ADR: add reversal conditions, review date, links; fold in or supersede-link the pending CoP replacement; add the "retire outright without replacement" alternative.
- **B3:** No change.
- **B4:** Remove from the team-visible log entirely; move to `mod-108` private record; do not leave a placeholder.
- **B5:** No change.

#### Answer key — successor-readiness verdict

Apply the four readability questions:

- **Run the week from the one-pager + ritual-calendar link?** Mostly yes — Section 8 names the load-bearing rituals and links the full calendar. The empty open-loops section means the peer does not know which in-flight work needs immediate attention. **Marginal — y with caveats.**
- **Answer a partner's message from the log + grid link?** Mostly yes for most topics, but the scope violation on B4 raises a trust question — if B4 is in the log, what else is in the log that shouldn't be? And the empty open-loops section means a Product-partner message about the confidence-UI design-system contribution does not have an obvious hook in the one-pager. **Marginal — y with caveats.**
- **Be legible to leadership from the one-pager?** Not well — the marketing-voice AI-ROI claim ("31% improvement through AI adoption") is exactly the kind of statement a VP will question, and the empty open-loops plus missing scope-boundary section mean the one-pager presents as a sales deck. **No.**
- **Flag the triggers from the log + gap-register link?** Mostly yes — Entry B5 names reversal conditions and review dates; the gap-register URL is in Section 6. But B2's missing reversal conditions are a trigger-flagging failure — the peer manager will not know when to revisit the AI-tools-sync retirement. **Marginal.**

**Overall:** *needs revision*. Not failing catastrophically; the model entries (B3, B5) show the manager has the discipline; the specific violations are correctable. The packet is **not successor-ready as-is** but is one revision cycle away from being so.

**Named fix list:**

- Revise the one-pager: add open-loops section with 3–5 named-owner dated items; add "what the team is not" section; rewrite the executive-summary bullet to separate the 31% trend from driver attribution.
- Revise B1 to a one-line scaled entry.
- Revise B2 to the full ADR template; fold in the CoP replacement.
- Remove B4 from the team-visible log and relocate to the `mod-108` private record.
- Keep B3 and B5 as model entries.
- Add a change-log line noting the one-pager version bump to v0.4 and the log entries revised, with rationale pointing to the Chapter 5 honesty discipline and the scope-of-log rules.

### Step 6 — Diagnose your grading drift (5 min)

Tally your grading against the key. For each miss, write one sentence:

- **If you graded the one-pager as successor-ready because nine of eleven sections were present and honest:** this is the *most-sections-pass* drift. Chapter 5's honesty discipline is binding — the three disciplines (open-loops non-empty; "what the team is not" present; AI-ROI qualified) are not three out of eleven sections, they are three trust gates the whole artifact runs through. Failing any one of the three turns the one-pager into a marketing-shaped artifact.
- **If you graded the executive-summary bullet as honest because it cites a specific number (31%):** this is the *specificity-looks-like-honesty* drift. Chapter 5: *"'22% faster with AI' is marketing and will be read as marketing."* Specific numbers *without attribution* are the exact failure mode. The fix is not to make the number vaguer; it is to route attribution to the backing dashboard and qualify with the anti-theatre caveat.
- **If you graded B4 as complete because every ADR field is populated:** this is the *template-completion-looks-like-fit* drift. Chapter 5 separates scope-in from scope-out explicitly; an entry that is in-template-shape but out-of-scope (individual performance; confidential personnel) is worse than a weak-but-in-scope entry. B4 should never have been written in the team-visible log in the first place; template completeness does not save a scope violation.
- **If you graded B2 as complete because it names the retirement and the rationale:** this is the *action-and-reason-is-enough* drift. Chapter 5 is explicit on the template fields a material decision requires; reversal conditions and review date are the fields a successor needs to decide whether the decision still holds. An entry without them is a change-of-state note, not a decision log entry.
- **If you graded B1 at the full ADR template as weak-because-missing-fields:** this is the right verdict for the wrong reason. The real issue is template over-use on a trivial decision — B1 should be one line, not half of a full template. Chapter 5's template scaling is the discipline; forcing every entry to the full shape is its own failure mode.
- **If you missed the scope-violation flag on B4 and instead flagged it as "excellent template adherence":** this is the drift the lab is specifically designed to catch. The template is *shape*; the log scope is *policy*. Both must pass.

## Expected output

A file `lab-03-grading-memo.md` with the Step 1 template filled: eleven one-pager section grades plus the three honesty-discipline checks plus overall one-pager verdict plus named one-pager fix; five decision-log entry grades plus the ADR field check plus overall log verdict plus named fix per entry; successor-readiness verdict with the four readability questions; diagnosis section covering every grade that differed from the key. Roughly 1.5–2 pages total.

Something like:

```
ONE-PAGER GRADING (Artifact A)

Sections 1–8: present and honest.
Section 9 Open loops: present but weak — empty section. Ch. 5 "Open loops
    section cannot be empty."
Section 10 What the team is not: missing. Ch. 5 "What the team is not
    section exists… peers reading this section learn what not to escalate
    to the team."
Section 11: present and honest.

Honesty disciplines:
    Open-loops non-empty: N
    "What the team is not": N
    AI-ROI qualified: N — executive-summary bullet reads "31% YoY improvement
        through AI adoption"; Ch. 5 "'22% faster with AI' is marketing".

Overall one-pager verdict: marketing-voice; violates honesty discipline.

Named fix: Add open-loops section with 3–5 dated items with named owners
(confidence-UI contribution, governance gap, Linear AI trial, v2 quote-
ranking rollout); add "what the team is not" section (does not own
freight-pricing model; does not own long-haul-contract pricing); rewrite
executive-summary bullet to separate the 31% trend from the attribution
(route attribution to the dashboard; add anti-theatre caveat sub-clause).

---

DECISION-LOG GRADING

B1 Shift Tuesday standup to Monday: weak — trivial decision over-templated;
   fix: collapse to one-line scaled entry.
B2 Retire the weekly AI tools sync: weak — missing reversal, review date,
   links; replacement CoP mis-scoped as a separate pending entry;
   fix: full ADR + fold CoP replacement in.
B3 Add decision-rights row for novel AI-interaction UI: complete — model entry.
B4 Address IC performance concern: SCOPE VIOLATION — individual performance
   in team-visible log; Ch. 5 "Individual performance decisions… Belong to
   mod-108 private records";
   fix: remove entirely from team-visible log; relocate to mod-108 private
   record; no placeholder.
B5 Sunset Linear AI trial: complete — model entry.

Overall log verdict: scope violation present; needs revision.

---

SUCCESSOR-READINESS: needs revision.

✅ caught the B4 scope violation on first read — initial reflex was "every
   field is populated so it's complete" — Ch. 5 "Decisions that do not go
   in the log: individual performance" caught it.
```

## Checkpoint

Before returning to [Exercise 04](../exercises/exercise-04-one-pager-and-decision-log-hygiene.md) on your own team's one-pager and decision log, you should be able to answer **yes** to all six:

- Did you catch the **three one-pager honesty-discipline violations** (empty open loops; missing *what the team is not*; unqualified AI-ROI bullet) and flag all three, not just one or two?
- Did you grade **B4 as a scope violation** rather than as a complete entry — recognising that template completeness does not save an entry that should not have been written in a team-visible log?
- Did you grade **B1 as over-templated for a trivial decision** and **B2 as under-templated for a material one** — applying Chapter 5's scaling discipline in both directions rather than treating every entry as needing the full shape?
- Did your named fixes name **specific actions on specific fields** (add reversal conditions, remove from team-visible log, collapse to one-line entry) rather than general comments (*"improve honesty"*, *"tighten the log"*)?
- Did you apply the **Monday-morning successor test** as four discrete readability questions — surfacing the empty-open-loops impact on *running the week* and the B4 scope violation's impact on *log trust generally* — rather than a one-line "feels successor-ready" judgement?
- On your one-pager verdict, did you treat *"nine of eleven sections are fine"* as **not enough** — the honesty disciplines are gates, not weights, exactly as Chapter 2's Axis 4 data-handling gate is in `mod-111`?

If any answer is no, re-read the relevant Chapter 5 section (*"The one-pager"*, *"The honesty discipline for the one-pager"*, *"The decision log"*, *"Decisions that do (not) go in the log"*, *"The successor-readiness check"*) before starting [Exercise 04](../exercises/exercise-04-one-pager-and-decision-log-hygiene.md) on your real team's packet.
