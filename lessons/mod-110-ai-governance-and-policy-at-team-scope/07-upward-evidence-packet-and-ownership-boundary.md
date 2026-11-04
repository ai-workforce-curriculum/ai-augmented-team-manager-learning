# Chapter 7 — The Upward Evidence Packet and the Ownership Boundary

> *A level-40 manager produces evidence; a level-50 architect designs the control library the evidence feeds; a level-60 head of AI governance owns the program the control library serves; counsel owns the legal position the program defends. If the evidence packet is clean, the four layers compose; if it is not, the whole thing improvises on the day it is tested.*

## Motivation

The four prior content chapters each produce an artifact — the NIST crosswalk, the Article 4 training record, the Article 14 / 50 workflow sheets, the Microsoft-RAI / Google-AIP mapping, the data-and-IP policy. In isolation each is defensible; together they must compose into a single evidence packet the governance program consumes.

This chapter does three things. First, it names the upward evidence packet — the single quarterly artifact the manager produces for [`senior-ai-governance-architect`](https://github.com/ai-governance-curriculum/senior-ai-governance-architect-learning) (L50), [`head-of-ai-governance`](https://github.com/ai-governance-curriculum/head-of-ai-governance-learning) (L60), and, through them, [`chief-ai-officer`](https://github.com/ai-governance-curriculum/chief-ai-officer-learning) (L70) and the board. Second, it draws the ownership boundary against the roles above and beside the manager: `senior-ai-governance-architect`, `head-of-ai-governance`, `chief-ai-officer`, `ai-risk-engineer` (sideways), and counsel (out of scope). Third, it names the retrospective the team runs on its own governance practice at the module cadence and how that retrospective lands on the [`mod-112`](../mod-112-cross-functional-leadership-and-ritual-calendar/) ritual calendar.

## Core concepts

### The upward evidence packet — shape and cadence

A workable shape for the packet. **Default cadence: quarterly**, with triggered off-cycle updates on material changes (new regulated workflow, new vendor, incident with program-wide implications, framework-update event).

**Sections, in order:**

1. **Executive summary (one page).**
   - Team name, scope, period covered.
   - What changed since last packet (new workflows in scope, new vendors, resolved gaps, new gaps).
   - Three to five bullets of material facts the governance program should know.
   - Named sign-off (manager; and, where joint sign-off is the firm's practice, the `ai-risk-engineer` peer and the `head-of-ai-governance` delegate).
2. **NIST AI RMF GOVERN crosswalk (Exercise 01 output).**
   - The table from Chapter 2, filled, versioned.
   - Gap register with owner and date for every unfilled or route-upward cell.
3. **Article 4 AI-literacy evidence (Chapter 3 output).**
   - Current curriculum version with change-log.
   - Role-tier segmentation table.
   - Per-tier completion rate for the period (percent of role on current curriculum; next-refresh date).
   - LMS link for per-person records (not embedded; referenced).
   - New-hire onboarding compliance (count of hires in period; count completed; outliers).
5. **Article 14 workflow sheets (Chapter 4 output).**
   - One sheet per in-scope workflow (high-risk, adjacent, or any workflow counsel has specifically asked for a sheet on).
   - Summary table: workflow, classification, oversight role, last review, next review.
6. **Article 50 interaction sheets (Chapter 4 output).**
   - Where applicable. Summary table as above.
7. **Microsoft RAI / Google AIP mapping (Chapter 5 output).**
   - One mapping table per framework the organisation has committed to.
   - Gap register with upward routing notes.
8. **Data-and-IP policy snapshot (Chapter 6 output).**
   - Current matrix version with change-log.
   - Vendor clause-reader summary (reference to the [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) registry).
   - Model-card index.
   - IP sidecar version.
   - Data-leak incidents in period (count; severity; link to retrospective).
9. **Incident and retrospective index ([`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) output).**
   - Count of AI-produced incidents in period by class (hallucination, prompt-injection, unauthorised-tool-use, model-regression, other).
   - Links to retrospectives.
   - Regression-fixture-backfeed status (incidents closed; fixtures landed; routing-matrix amendments).
10. **Gap register (consolidated).**
    - Every unfilled or route-upward cell from sections 2–8.
    - Owner (named role, named person where possible), due date, routing trigger.
11. **Change-log.**
    - Material changes since last packet.
    - Policy, matrix, workflow-sheet, mapping updates.
12. **Appendices.**
    - Full crosswalk, full mapping tables, full workflow sheets, full matrix, full training-record CSV exports — attached as links to the source-of-truth artifacts, not duplicated.

The packet is ~15–25 pages when printed, with most of that being the appendices and tables. The executive summary and the gap register are the two sections the audience reads first.

### Who reads which section

Different audiences read different sections of the same packet.

- **[`senior-ai-governance-architect`](https://github.com/ai-governance-curriculum/senior-ai-governance-architect-learning) (L50)** reads the **crosswalk**, the **gap register**, and the **mapping tables**. Their interest is control-library coherence: do the team's artifacts fit into the organisation's control library cleanly? What gaps imply a program-architecture change?
- **[`head-of-ai-governance`](https://github.com/ai-governance-curriculum/head-of-ai-governance-learning) (L60)** reads the **executive summary**, the **gap register**, the **incident index**, and the **Article 4/14/50 sections**. Their interest is program accountability: does the team's practice support the program's regulator- and board-facing narrative? Are there triggers that need program action?
- **[`chief-ai-officer`](https://github.com/ai-governance-curriculum/chief-ai-officer-learning) (L70)** does not usually read the packet directly; they read the program-level roll-up that `head-of-ai-governance` produces from multiple teams' packets. The packet's shape must support that roll-up.
- **Counsel** reads the **Article 14/50 sections** and anything in the gap register flagged "legal routing". Their interest is the legal position: are new triggers surfacing that need legal action?
- **[`ai-risk-engineer`](https://github.com/ai-governance-curriculum/ai-risk-engineer-learning)** (peer L25) reads the **crosswalk sections tied to engineered risk** (GOVERN 1.3, 4.3) and the **incident index**. Their interest is specification: what risk commissioning does the manager need from them this quarter?
- **The team itself** reads the whole packet at the quarterly retrospective. It is calibration: here is what we evidence; here is what we do not.

### Structuring the gap register

The gap register is the most load-bearing section after the executive summary. One row per gap:

| Gap | Source | Owner (role) | Owner (person) | Due date | Routing | Notes |
|---|---|---|---|---|---|---|
| Example: Workflow X does not have an Article 14 sheet | Chapter 4, Section 5 | Manager | J. Doe (team manager) | 2027-01-15 | — | Counsel has classified; sheet in progress |
| Example: No upstream program policy on confidential-data retention periods | Chapter 6, Section 8 | `senior-ai-governance-architect` (L50) | L. Chen | — | Upward | Blocks matrix row R3 from "conditional" to "allowed" |
| Example: GPT-model fairness eval dataset not yet commissioned | Chapter 2, GOVERN 1.3 | `ai-risk-engineer` (L25) | S. Mwangi | 2027-02-01 | Sideways | Commissioning brief in draft |

The point of the register is to be *actionable*: the owner knows it is theirs; the due date is real; the routing is explicit; the notes explain what has been tried.

A gap register that only lists gaps and does not route them is a wish-list. A gap register with routing and owners is a plan.

### The team-scope governance retrospective

Independent of the quarterly packet, the team runs a **governance retrospective** at the module cadence — typically semiannually, or after any material event (a landed packet with a non-trivial gap, an incident that implicates governance, a significant policy update). The retrospective asks four questions:

1. *Where did our practice hold?* — the artifacts and workflows that worked.
2. *Where did our practice break or bend?* — the places an IC had to improvise, counsel had to interpret under pressure, or the audit had to ask twice.
3. *What does the program need from us that we are not yet producing?* — surfaced gaps requiring team action.
4. *What do we need from the program that we are not getting?* — surfaced gaps requiring upward action.

The retrospective is 60–90 minutes with the team; the output is a one-page retro note and a set of amendments to the four backing artifacts (crosswalk, training record, policies, mapping). The retro cadence lands on the [`mod-112`](../mod-112-cross-functional-leadership-and-ritual-calendar/) calendar.

### The ownership boundary, precisely

The following is the boundary the manager operates to. *Each row names the role; the *responsibility at scope*; and *where the manager's evidence feeds into the role*.*

| Role | Responsibility at their scope | Manager's contribution |
|---|---|---|
| **IC** on the team | Doing AI-augmented work per team policy | Operates against the policy; reports incidents; completes training |
| **Reviewer / tech lead** on the team | Signing off on AI-produced artifacts | Operates against review standards; raises concerns; reviewer-tier training |
| **Team manager (this role, L40)** | Operating the governance practice at team scope; producing the evidence packet | — |
| **[`ai-risk-engineer`](https://github.com/ai-governance-curriculum/ai-risk-engineer-learning) (L25, peer)** | Engineered risk — red-team, guardrails, systematic model-level evaluation | Commissions eval work; flags incidents requiring engineered root cause; receives output; routes between the eval backlog and the standards stack |
| **SecOps / DFIR peer** | SOC-side incident chain — data exposure, intrusion, credential compromise | Routes incidents per the [`mod-109` Ch. 5](../mod-109-accountability-incident-response-and-blameless-postmortems/05-routing-contract-with-risk-engineer-and-secops.md) trigger line; coordinates team-scope participation in SOC IR |
| **Counsel** (through GC, DPO, CISO as appropriate) | Legal interpretation; regulator engagement; disclosure; formal vendor engagement | Flags triggers per the Chapter 4 list and the Chapter 6 data-leak trigger list; does not interpret statute; does not communicate externally on regulated matters |
| **[`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) (L45)** | Org-wide enablement programs; multi-team coordination | Contributes team training data and feedback; consumes org-wide curricula and modifies for team context |
| **[`ai-engineering-manager`](https://github.com/ai-engineering-curriculum/ai-engineering-manager-learning) (L50)** | Engineering-manager-of-managers scope; cross-team engineering management | Participates in cross-team practice-sharing; raises systemic issues |
| **[`senior-ai-governance-architect`](https://github.com/ai-governance-curriculum/senior-ai-governance-architect-learning) (L50)** | Control-library architecture; policy structure; tooling choice | Produces the upward packet consumed by the architect; surfaces control-library gaps |
| **[`head-of-ai-governance`](https://github.com/ai-governance-curriculum/head-of-ai-governance-learning) (L60)** | Program accountability; board and regulator reporting; multi-team governance roll-up | Produces the upward packet; participates in regulator-facing evidence production when requested |
| **[`chief-ai-officer`](https://github.com/ai-governance-curriculum/chief-ai-officer-learning) (L70)** | Executive scope; public commitments; board governance; cross-program accountability | Contributes evidence through the program roll-up; does not communicate executively |

Two lines matter beyond the table.

- **The manager is not a lawyer.** Interpretation of statute, formal legal opinion, and regulator communication are not the manager's job — not even "a little bit". The triggers in Chapter 4 and Chapter 6 route to counsel, who decides.
- **The manager is not a risk engineer.** Engineering-grade risk work — adversarial testing, guardrail design, model evaluation — is `ai-risk-engineer`'s discipline. The manager commissions and acts on the evidence; the manager does not re-run the engineering. The commissioning brief is the interface, authored per [`mod-103`](../mod-103-review-standards-and-eval-commissioning/).

### Where the module ends

The level-40 manager who completes mod-110 has:

- A GOVERN crosswalk filled in for their team's artifacts, with a routing-ready gap register.
- An Article 4 AI-literacy program sized, segmented, documented, and operating with evidence capture.
- Article 14 and (if applicable) Article 50 workflow sheets for each in-scope workflow.
- A Microsoft RAI and/or Google AIP mapping table pointing at team evidence.
- A one-page data-and-IP matrix with vendor clause citations, a model-card index, and an IP sidecar.
- A quarterly upward packet shape the governance program consumes.
- A retrospective cadence on the [`mod-112`](../mod-112-cross-functional-leadership-and-ritual-calendar/) calendar.
- Clear routing contracts to counsel (legal), `ai-risk-engineer` (engineered risk), SecOps (SOC-side), and upward (L45, L50, L60, L70).

This is the practical shape of team-scope AI governance. It is not the full field of AI governance; it is the slice the team manager is personally accountable for.

### What the module does not produce

- The organisation's AI policy. (That is `head-of-ai-governance` and counsel.)
- The control library architecture. (That is `senior-ai-governance-architect`.)
- Engineering-grade risk evidence at model / system level. (That is `ai-risk-engineer`.)
- The organisation's legal position on anything in Chapters 3, 4, or 6. (That is counsel.)
- The organisation's public responsible-AI commitments or board reporting. (That is `head-of-ai-governance` and `chief-ai-officer`.)
- The team's performance-management decisions. (That is [`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/).)

The manager who tries to produce any of these from inside the mod-110 scope is over-reaching. The manager who flags triggers cleanly, routes crisply, and keeps the team-scope evidence in good shape is doing their L40 job in full.

## Example: a packet the governance program actually uses

Composite — calibration.

The financial-services team's second quarterly packet (the first, in Q4, established the shape and surfaced ~30 gaps). The Q1 packet has 22 gaps on the register — 8 resolved from Q4, 14 new (mostly from new workflows entering scope as Chapter 1's underwriting-assist rollout expanded).

The architect at L50 reads the crosswalk and the gap register:

- Notes two gap patterns: three teams' packets flag the absence of an upstream data-retention policy for *confidential* class. Routes to the architect's Q2 backlog.
- Notes one architectural implication: the Article 14 workflow sheets have evolved slightly different structures across teams. Authors a program-wide Article 14 template for Q2.

The head of AI governance at L60 reads the executive summary, the gap register, and the incident index:

- Notes that the team has had zero data-leak incidents in Q1; two in Q4. Attributes to the Chapter 6 matrix being adopted properly after Q4's audit.
- Notes the underwriting-assist workflow's Article 14 sheet has been renewed; schedules a cross-team review with sister teams in Q2.

Counsel reads the Article 14/50 sections and one gap register entry marked "legal routing":

- The gap: a new workflow proposed on the team's roadmap touches employment-screening; needs classification before pilot can start.
- Counsel schedules the classification review.

The team retrospective (semiannual, held at Q1/Q2 boundary):

- Holds: the matrix is used (one IC story about the Tuesday-afternoon decision).
- Bends: the quarterly refresh cadence missed by two weeks due to end-of-year scheduling; counsel-trigger response time is slower than wanted.
- Program-needs-from-us: the architect asked for a structured gap-source field; added for Q2 packet.
- We-need-from-program: faster counsel-trigger response and an updated data-retention policy (both routed upward).

This is what a working system looks like: evidence flows, gaps get owned, the retrospective improves the packet.

## Summary

- The **upward evidence packet** is the single quarterly artifact that composes the four content chapters' outputs into something the governance program consumes. ~15–25 pages, with the executive summary and the gap register as the headline sections.
- **Different audiences read different sections**: `senior-ai-governance-architect` reads structure; `head-of-ai-governance` reads program impact; counsel reads legal-routing triggers; `ai-risk-engineer` reads engineered-risk sections.
- The **gap register** is the register of unfilled or route-upward cells from every other section, with owner, due date, and routing explicit. Without routing, it is a wish-list.
- The **team-scope governance retrospective** runs semiannually (or triggered) and asks four questions: where practice held, where it bent, what the program needs from us, what we need from the program.
- The **ownership boundary** is precise: manager owns practice; `ai-risk-engineer` owns engineered risk (peer); SecOps owns SOC-side chain (peer); counsel owns legal interpretation (out of scope); `senior-ai-governance-architect` owns program architecture (upward); `head-of-ai-governance` owns program accountability (upward); `chief-ai-officer` owns executive scope (upward); `ai-enablement-lead` and `ai-engineering-manager` own org-wide and cross-team coordination (upward-adjacent).
- **The manager is not a lawyer, and not a risk engineer.** Triggers route; the engineering is commissioned; the legal position is set by counsel.
- The module ends with **seven artifacts** on the team's wiki: crosswalk, training record, Article 14 sheets, Article 50 sheets, framework mapping, data-and-IP matrix with model-card index and IP sidecar, upward packet template.
- The retrospective cadence and the packet cadence land on the [`mod-112`](../mod-112-cross-functional-leadership-and-ritual-calendar/) ritual calendar.
