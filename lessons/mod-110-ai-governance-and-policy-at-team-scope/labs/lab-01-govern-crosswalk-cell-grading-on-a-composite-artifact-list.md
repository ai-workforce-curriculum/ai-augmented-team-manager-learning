# Lab 01 — NIST GOVERN Crosswalk Cell Grading on a Composite Artifact List

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 2 (the in-scope GOVERN subcategories at team altitude; the crosswalk artifact's four columns; using the Playbook's *Transparency and documentation* questions as acceptance criteria; what NIST intentionally does not prescribe), with a side-check against Chapter 1 (what practice vs. policy ownership means at team scope) and Chapter 7 (how gap-register rows are routed).
**Complements, does not duplicate:** [Exercise 01](../exercises/exercise-01-nist-ai-rmf-govern-to-team-practice.md) asks you to author the v0.1 GOVERN crosswalk for **your own** team, with your own artifact paths, your own architect sign-off, and your own gap register. This lab hands you a deliberately composite artifact inventory from a fictional team so you can **calibrate your reading** of what makes a cell *evidence* vs. *a wave at an artifact* vs. *an upstream-owned row* vs. *a routable gap* — before you spend authoring hours on a crosswalk that cites "the team wiki" and gets rejected on first read by the architect. A manager who can grade a cell against the Playbook's transparency questions in under a minute is a manager whose own crosswalk will survive the architect review.

## Objective

For each of twelve composite artifact entries on a fictional team's inventory, produce a grading row with: (i) the **GOVERN subcategory** it most directly evidences (team-grain) — or the notation *"upstream-only"* / *"out-of-module"*; (ii) a **completeness grade** — `evidence` (specific URI + answers the Playbook's transparency question for that subcategory), `wave` (named but not specific; needs tightening), or `gap` (missing, with routing); (iii) **what to change** in one sentence, if anything; (iv) **gap-register routing** (`upward`, `sideways`, `team-backlog`, or `n/a`). Then compare against the answer key.

Target: **you match the subcategory on at least ten of twelve entries, your completeness grades match the key on at least nine of twelve, and on the two deliberately-planted scope-violation entries (where the manager's draft overreaches into counsel-owned or architect-owned work) you catch *both* of them and route them correctly rather than grading them green.** These are the two reading drifts Chapter 2 and Chapter 7 flag most often — grading a generic wave ("see the team wiki") as green because the team "has the artifact somewhere," and grading a scope-violation green because "the team did the work" without noticing that the work was not theirs to do.

## Prerequisites

- Chapter 2 read end-to-end — especially the subcategory table (GOVERN 1.2, 1.3, 1.4, 2.1, 2.2, 2.3, 3.2, 4.1, 4.2, 4.3, 5.1, 6.1, 6.2), *"The crosswalk artifact"*, *"Using the Playbook, not just the framework"*, and *"Where NIST intentionally does not prescribe"*. Keep the subcategory list on a scratch page; you will score against it.
- Chapter 1 skimmed — the shorthand *"manager owns practice; architect owns policy structure; head of governance owns program accountability; counsel owns legal position"* is the test you apply on the two scope-violation entries.
- Chapter 7 skimmed — the gap-register structure (gap, source, owner (role), owner (person), due date, routing, notes) and the ownership-boundary table.
- Access to the [NIST AI RMF Playbook](https://airc.nist.gov/AI_RMF_Knowledge_Base/Playbook) — specifically the *Transparency and documentation* question list per subcategory. For this lab you can work from Chapter 2's paraphrase of the questions (e.g., GOVERN 2.1: *"who is accountable for the AI system? what is the escalation path if the system behaves unexpectedly?"*); for your own crosswalk, pull the current live Playbook.
- A blank file for your grading sheet.
- A timer.

## The fictional context

> **"Claims Intelligence" team, Northstar Mutual (EU-headquartered personal-lines insurer, Dublin).** 10 engineers (1 staff, 2 senior, 7 mid/junior), 1 manager. Owns `claims-router`, `claims-intelligence-platform`, and two AI agents: **`ClaimsPilot`** (internal RAG over policy/coverage docs, used by the claims-handler team to answer coverage questions during claim adjudication) and **`UWCopilot`** (underwriting-assist agent drafting preliminary assessments for personal-lines underwriters; the final underwriting decision is a human underwriter's — counsel has classified this workflow as *adjacent-to-high-risk under Annex III category 5(b)* as of 2026-07-02). Tools in use: Claude Code via team gateway (Q1 2026 rollout), Cursor Business (team-wide), bespoke orchestrator for both agents, self-hosted embedding model. The firm's AI-governance program is 18 months old and has an active policy registry, a control library in progress, and a nominated `senior-ai-governance-architect` (L50) reachable through the program. `ai-risk-engineer` peer at L25 in central governance; SecOps via `#security-ir` PagerDuty. Pinned artifacts the team has from prior modules: mod-103 accountability contract, mod-103 review checklist, mod-103 standards-as-code stack, mod-103 eval commissioning backlog; mod-105 enablement curriculum; mod-106 routing matrix, HITL checkpoints, delegation ladder, tool-authorisation policy; mod-109 incident runbook, routing contract, two Q3 retrospectives on file.

Grade each entry *as if you are the team manager building the v0.1 crosswalk*. Do not invent artifacts not in the inventory; grade only what the inventory names. If the inventory does not reference a specific URI, the cell is at best a **wave**.

## The twelve composite inventory entries

These are what the manager's first draft of the crosswalk points at. Each is one row in the draft.

```
ENTRY #   TEAM-SCOPE INTERPRETATION                                            CITED ARTIFACT

1   "Our review checklist operationalises trustworthy-AI               "see the team wiki"
    characteristics (reliability, safety, fairness, privacy,
    explainability, security) at review time."

2   "Every AI-produced incident is written up and shared               "the mod-109 incident runbook at
    team-wide at the Thursday retro; patterns roll into the             drive://northstar-claims/runbooks/
    eval backlog."                                                      ai-incident-runbook-v2.1.md and
                                                                        the Q3 retrospectives at
                                                                        drive://northstar-claims/
                                                                        retrospectives/2026-Q3/"

3   "For UWCopilot (adjacent-to-high-risk per counsel                  "Article 14 workflow sheet at
    2026-07-02), we operate a named oversight role, documented         drive://northstar-claims/
    decision points, a documented override mechanism, and               article-14-sheets/uwcopilot-v3.2.md
    automation-bias mitigation."                                        with counsel sign-off on file"

4   "Every member of the team completes the firm's AI-fluency          "the LMS"
    curriculum by tier (awareness / operational / reviewer /
    manager) with quarterly refresh and incident-driven
    micro-sessions."

5   "The firm's acceptable-risk threshold for the UWCopilot            "manager's judgement; we review
    workflow is calibrated to the underwriting error-rate                each quarter in the retrospective"
    baseline from the human-only era."

6   "Every AI tool on the team's stack has a current data-use          "the mod-111 vendor registry at
    clause-reader (training-on-your-data, retention, residency,         drive://northstar-governance/
    access, deletion); the data-class × tool-class matrix               vendors/ (shared with 4 other
    references the registry row per vendor."                            teams) and the team's data policy
                                                                        matrix at drive://northstar-claims/
                                                                        policies/data-matrix-v1.3.md"

7   "Roles and lines of communication are documented: IC,              "see the accountability contract and
    reviewer, manager, ai-risk-engineer peer, SecOps peer,              the mod-109 routing contract"
    counsel partner."

8   "Contingency for vendor-side failures (silent model                 "we have mod-109 Class 4 practice
    rotations, deprecations, outages) is documented and                 and the Q3 regression retrospective"
    tested."

9   "External AI-actor feedback — from the claims-handler team,         "the claims-handler team sends us
    from downstream consumers of UWCopilot outputs, and from            Slack messages in #claims-feedback
    partner reinsurers who consume our risk reports —                   and we track them in a spreadsheet
    is collected and considered."                                       at drive://northstar-claims/
                                                                        feedback/log.xlsx"

10  "Our team has authored the firm's position on whether               "manager-drafted memo at
    UWCopilot's output materially influences a decision for             drive://northstar-claims/
    Annex III category 5(b) purposes; we are proceeding on              policies/annex-iii-classification-
    the interim classification pending counsel confirmation."           uwcopilot-manager-interim.md"

11  "Fairness evaluation for UWCopilot: the team's eval backlog         "two eval rows in the mod-103
    includes two fairness-rowed evals (disparate-impact on               commissioning backlog; red/green
    protected classes, outcome-parity on the postcode-risk              gating in CI; sideways to
    feature) that red/green-gate in CI."                                 ai-risk-engineer who commissioned
                                                                        them 2026-09-14"

12  "Workforce diversity, competencies, and performance                 "we handle this well; see HR"
    management for AI risk work."
```

## Steps

### Step 1 — Set up your grading sheet (3 min)

Create a working file `lab-01-grading-sheet.md` with this template, repeated once per entry:

```
Entry #: <N>
(i)   GOVERN subcategory       : GOVERN <X.Y>  (or: upstream-only / out-of-module)
                                 Rationale: <one sentence tying the entry to the subcategory>
(ii)  Completeness grade       : evidence / wave / gap
                                 Playbook transparency question checked:
                                    <paraphrase of the specific question from the Playbook / Ch. 2>
                                 Does the cited artifact answer it?  YES / NO / PARTIAL
(iii) What to change           : <one sentence — or "nothing, ship as-is">
(iv)  Gap-register routing     : upward / sideways / team-backlog / n/a
                                 Owner (role): <role>
                                 Notes: <one line>
```

Time yourself. Target per entry: 4–6 minutes. If you spend more than 8 minutes, note the drift and move on; you will diagnose it in Step 4.

### Step 2 — Grade entries 1–6 (25–30 min)

Grade entries 1 through 6 against the template. Do not look at the key yet. If an entry seems ambiguous, pick the subcategory you think is *primary* and note the secondary in your rationale; the key will show both.

### Step 3 — Grade entries 7–12 (25–30 min)

Grade entries 7 through 12 against the template. Two of the twelve entries are *deliberately planted scope violations* where the manager's draft has overreached into counsel-owned or architect-owned work; graders who do not notice will mark them `evidence` and miss the point. Watch for this specifically.

### Step 4 — Compare against the answer key (10–15 min)

Read the key below only after you have graded all twelve.

#### Answer key — Entry 1 (review checklist operationalising trustworthy-AI characteristics)

- **(i) Subcategory.** **GOVERN 1.2** (policies and procedures to define characteristics of trustworthy AI). Secondary: GOVERN 4.1 (critical thinking / safety-first mindset) if the checklist is the mechanism; both are legitimate citations. Chapter 2's crosswalk names *"mod-103 review checklist; mod-106 AGENTS.md conventions"* as the 1.2 backing artifact.
- **(ii) Completeness grade.** **Wave.** Chapter 2 is explicit: *"Not 'Slack'; not 'the team wiki'; the specific URL."* "See the team wiki" is the archetypal wave. The Playbook's transparency questions for GOVERN 1.2 include *"what are the characteristics of trustworthy AI the system supports, and how are they operationalised?"* — a reader cannot answer that from a wave.
- **(iii) What to change.** Replace "see the team wiki" with the specific URI for the mod-103 review-checklist artifact (e.g., `drive://northstar-claims/standards/review-checklist-v2.3.md`) plus the mod-103 standards-as-code stack path.
- **(iv) Routing.** **Team-backlog.** Owner: manager. Fix in-draft before the architect review; no upstream routing needed.

#### Answer key — Entry 2 (incident runbook + retrospectives)

- **(i) Subcategory.** **GOVERN 4.3** (organisational practices to enable AI testing, incident identification, information sharing). Secondary: GOVERN 1.3 (communication of risk-management processes and outcomes) via the retrospective-as-communication path; both legitimate. Chapter 2's crosswalk names *"mod-109 runbook + retrospective; mod-103 eval regression gate"* as the 4.3 backing.
- **(ii) Completeness grade.** **Evidence.** Specific URIs for the runbook (versioned at v2.1) and the Q3 retrospective directory. The Playbook's transparency question for GOVERN 4.3 is *"how are AI incidents tracked and communicated?"* — the cited artifacts answer this (runbook describes tracking; retrospectives are the communicated outputs).
- **(iii) What to change.** Nothing; ship as-is for v0.1. (Possible tightening: when the Q4 retrospective closes, update the citation range.)
- **(iv) Routing.** **n/a.**

#### Answer key — Entry 3 (Article 14 workflow sheet for UWCopilot)

- **(i) Subcategory.** **GOVERN 3.2** (roles and responsibilities for human-AI configurations and oversight). Secondary: GOVERN 1.4 (legal / regulatory alignment) via the counsel-classified status. Chapter 2's crosswalk names *"mod-106 delegation ladder and HITL checkpoints; Chapter 4 Art. 14 mapping"* as the 3.2 backing.
- **(ii) Completeness grade.** **Evidence.** Specific URI for the sheet, versioned (v3.2), with counsel sign-off on file. Chapter 4 defines the sheet's eight required fields; this entry asserts five of them (named oversight role, decision points, override mechanism, automation-bias mitigation, and — implicitly — change log via the versioning). A thorough graders' pass would ask to verify trace-preservation and escalation-path fields are also populated in the sheet itself, but the inventory cell is at `evidence` density.
- **(iii) What to change.** Nothing on the crosswalk row; verify when reviewing the sheet artifact itself that all eight Chapter 4 fields are populated.
- **(iv) Routing.** **n/a.**

#### Answer key — Entry 4 (AI-fluency curriculum by tier)

- **(i) Subcategory.** **GOVERN 2.2** (personnel receive AI risk-management training appropriate to their roles). Secondary: GOVERN 3 workforce / competencies subcategories via the role-tier mechanism. Chapter 2's crosswalk names *"Chapter 3 training record; mod-105 enablement artifacts"* as the 2.2 backing.
- **(ii) Completeness grade.** **Wave.** "The LMS" is the generic version of "the team wiki." Chapter 3's *"Evidence capture"* section is explicit about what the record has to show: who is on the team by role tier; what modules completed by whom with date; curriculum version with change-log; sign-off; next refresh dates. "The LMS" names the system, not the record.
- **(iii) What to change.** Replace with the specific LMS curriculum ID (e.g., `lms://northstar/curricula/AI-FLUENCY-CLM-V2`), a link to the current per-tier completion-rate export, the segmentation table (Chapter 3 Role-segmentation shape), and the curriculum sign-off record. Chapter 3's audit question — *"can you produce the per-person training record on demand?"* — is the acceptance test.
- **(iv) Routing.** **Team-backlog.** Owner: manager. Chapter 3 Exercise 02 is the authoring work; this crosswalk cell just points at its output.

#### Answer key — Entry 5 (acceptable-risk threshold for UWCopilot)

- **(i) Subcategory.** **GOVERN 1.3** (risk-management processes and outcomes communicated; implicitly, acceptable-risk thresholds set). Chapter 2 is explicit: *"Risk thresholds are not in the framework. NIST does not say what constitutes 'acceptable' AI risk; it says the organisation must set and justify thresholds. At team scope, the manager inherits the organisation's thresholds; if none exist, the crosswalk routes GOVERN 1.3 upward as a gap."*
- **(ii) Completeness grade.** **Gap** — and worse, a **scope-violation gap**. "Manager's judgement; we review each quarter in the retrospective" is not a documented threshold inherited from an upstream policy; it is the manager doing threshold-setting work they do not own. Chapter 1's shorthand (*"the manager owns practice, the architect owns policy structure"*) and Chapter 2's silence on thresholds both route this question *upward*. The deliberate planted-failure in this entry: a grader who marks this `evidence` because "the manager has a process" is missing that the manager is operating without the upstream policy the process should inherit from.
- **(iii) What to change.** Remove the "manager's judgement" line. Fill the backing-team-artifact column with what the team *does* evidence (eval backlog, retrospective records, UWCopilot error-rate monitoring — specific URIs). Leave the backing-upstream-artifact column empty and open a gap-register row.
- **(iv) Routing.** **Upward.** Owner (role): `senior-ai-governance-architect` or `head-of-ai-governance`. Owner (person): the architect or program lead who owns the policy registry. Notes: *"Team operates practice but has no inherited threshold policy; blocks GOVERN 1.3 from evidence; UWCopilot is adjacent-to-high-risk so threshold urgency is elevated."*

#### Answer key — Entry 6 (data-class × tool-class matrix + clause-reader)

- **(i) Subcategory.** **GOVERN 6.1** (third-party AI risks — vendor and tool list with data-use clauses). Secondary: GOVERN 1.2 (trustworthy-AI characteristics, specifically the privacy/security characteristic) and GOVERN 4.2 (team documents risks and impacts) via the matrix as the operational form of the C5 data-handling clause. Chapter 2's crosswalk names *"mod-111 tool registry; Chapter 6 data-handling policy"* as the 6.1 backing.
- **(ii) Completeness grade.** **Evidence.** Specific URIs for both the vendor registry (shared with four other teams — an inheritance pattern the governance program will appreciate) and the team's data-policy matrix (versioned v1.3). The Playbook's GOVERN 6.1 transparency questions (*"what third-party AI components are in use? what is the organisation's position on their data use?"*) are answered.
- **(iii) What to change.** Nothing; ship as-is.
- **(iv) Routing.** **n/a.**

#### Answer key — Entry 7 (roles and lines of communication)

- **(i) Subcategory.** **GOVERN 2.1** (roles, responsibilities, lines of communication for AI risks documented). Chapter 2's crosswalk names *"mod-103 Ch. 5 accountability contract; mod-109 Ch. 5 routing contract"* as the 2.1 backing — exactly the artifacts this entry names.
- **(ii) Completeness grade.** **Wave.** The artifacts are the right ones, but the citation is not specific — no URIs, no versions. Playbook transparency questions for 2.1 include *"who is accountable for the AI system?"* and *"what is the escalation path if the system behaves unexpectedly?"* — both are answerable from the cited artifacts if the reader can find them, and not otherwise.
- **(iii) What to change.** Replace with specific URIs for both: e.g., `drive://northstar-claims/contracts/accountability-contract-v2.1.md` and `drive://northstar-claims/runbooks/routing-contract-v1.4.md`.
- **(iv) Routing.** **Team-backlog.** Owner: manager. 5-minute fix.

#### Answer key — Entry 8 (vendor-side contingency practice)

- **(i) Subcategory.** **GOVERN 6.2** (contingency for failures in third-party data or AI systems). Chapter 2's crosswalk names *"mod-109 vendor-side detection category; mod-111 continuity clauses"* as the 6.2 backing.
- **(ii) Completeness grade.** **Wave.** The entry names mod-109 Class 4 practice generically and references a Q3 retrospective but gives no URIs. The Playbook's 6.2 transparency questions include *"what happens if a third-party model or data source changes or fails?"* — the team has practice here but the citation does not evidence it.
- **(iii) What to change.** Add the specific URIs for the mod-109 Class 4 section of the runbook and for the Q3 regression retrospective; cross-link to the mod-111 continuity clause for the affected vendor(s).
- **(iv) Routing.** **Team-backlog.** Owner: manager.

#### Answer key — Entry 9 (external AI-actor feedback)

- **(i) Subcategory.** **GOVERN 5.1** (policies and practices to collect and integrate feedback from external AI actors). Chapter 2's crosswalk names *"mod-109 detection channels"* as a 5.1 backing; the team's own feedback channels extend that.
- **(ii) Completeness grade.** **Evidence** (borderline — see below). Specific channel (`#claims-feedback`) and specific log path (`drive://northstar-claims/feedback/log.xlsx`) are cited. The Playbook's 5.1 transparency questions include *"how is feedback from AI actors collected, prioritised, and integrated?"* — the log answers collection; integration into the eval backlog or the runbook is the step that completes the practice. If the log is only a collection log and never integrates into the backlog, this borders on `wave`.
- **(iii) What to change.** Add a sentence citing *how* feedback moves from the log into either the eval backlog (mod-103) or the routing-matrix amendment pipeline (mod-106) — e.g., *"monthly review integrates items into the mod-103 eval commissioning backlog; three items in Q3 became eval rows."*
- **(iv) Routing.** **Team-backlog** for the tightening. Possible **upward** gap if the organisation lacks a program-level external-stakeholder feedback programme — flag as a secondary note.

#### Answer key — Entry 10 (manager-drafted Annex III classification)

- **(i) Subcategory.** **GOVERN 1.4** (risk-management-process alignment with legal and regulatory requirements). Chapter 2's crosswalk names *"Chapter 4 (Articles 14 & 50) workflow triggers"* as the 1.4 backing; the upstream artifact is *"Counsel-owned legal mapping."*
- **(ii) Completeness grade.** **Gap, and a scope violation.** This is the *second* deliberately planted entry. Chapter 7's ownership-boundary table is unambiguous: *"The manager is not a lawyer. Interpretation of statute, formal legal opinion, and regulator communication are not the manager's job — not even 'a little bit'."* An Annex III classification is a legal-position question; the "manager-drafted interim classification" is the manager doing counsel's work, and *"proceeding on the interim pending counsel confirmation"* is operating a pilot without approved classification — a self-inflicted audit flag. Chapter 4's trigger list routes new Annex-III-adjacent workflows *to counsel*, not to the manager's drafting queue. The deliberate planted-failure here: the entry sounds *responsible* (the manager has drafted a memo; the memo is at a specific URI; the team is proceeding carefully) and a grader who marks this `evidence` is giving credit to the wrong kind of initiative. The correct read is: the manager has created an artifact that should not exist.
- **(iii) What to change.** **Withdraw the manager-drafted interim classification.** Replace the entry with: *"UWCopilot classification was obtained from counsel on 2026-07-02 (adjacent-to-high-risk under Annex III category 5(b)); see Article 14 workflow sheet at `drive://northstar-claims/article-14-sheets/uwcopilot-v3.2.md`. New workflows pending counsel review: {list with trigger-flag dates}."*
- **(iv) Routing.** **Upward (legal).** Owner (role): counsel (via GC). Owner (person): the firm's Privacy & AI counsel. Notes: *"Manager over-reached; withdraw interim memo; existing counsel classification from 2026-07-02 is the authoritative record for UWCopilot; future workflows route via the Chapter 4 trigger list."* (A secondary **sideways** gap routes to the manager's own training if the overreach pattern recurs.)

#### Answer key — Entry 11 (fairness evaluation for UWCopilot)

- **(i) Subcategory.** **GOVERN 1.3** (risk-management processes and outcomes communicated — specifically the eval-outcome communication) and **GOVERN 4.2** (team documents risks and potential impacts). Secondary cross-reference to Microsoft RAI Fairness and Google AIP Principle 2 under Chapter 5's framework-mapping. Chapter 2's crosswalk names *"mod-103 eval commissioning records; mod-109 retrospective artifacts"* as the 1.3 backing.
- **(ii) Completeness grade.** **Evidence.** Two specific eval rows, red/green CI gating, commissioned by `ai-risk-engineer` on a specific date. The *sideways-commissioning* pattern is exactly what Chapter 2 means by *"Do not duplicate `ai-risk-engineer` evidence. GOVERN subcategories that cover engineered risk point at `ai-risk-engineer` commissioning records. The manager cites; the manager does not re-run."* This entry is the shape to aim for.
- **(iii) What to change.** Nothing on the row. The architect may want to cross-reference the eval row IDs explicitly in the backing-team-artifact column for maximum traceability — nice-to-have.
- **(iv) Routing.** **n/a.** (A latent **upward** gap exists if the organisation has no program-level fairness policy — Chapter 5's Microsoft RAI Fairness row notes this as a typical upward gap. Flag in the gap register as a secondary note; owner is `senior-ai-governance-architect`.)

#### Answer key — Entry 12 (workforce diversity, competencies, performance management)

- **(i) Subcategory.** **GOVERN 3** workforce / competencies subcategories. Chapter 2 names this as *part-organisational, part-team* with the explicit routing: *"The team's hiring, levelling, and performance-management practices under AI augmentation sit in [`mod-108`](../../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/); the manager cross-references to that module rather than re-authoring here."*
- **(ii) Completeness grade.** **Wave** — *"we handle this well; see HR"* is the archetypal non-citation. Chapter 2's acceptance rule for GOVERN 3 is a specific chapter-and-artifact cross-reference to mod-108.
- **(iii) What to change.** Replace with a specific cross-reference: e.g., *"See mod-108 Chapter 4 (hiring rubric and AI-augmentation framing) and mod-108 Chapter 5 (performance-management shape under AI augmentation). Team artifacts: {specific URIs if the manager has them from mod-108 completion}. Organisation-level hiring-compliance framing: mod-108 Chapter 6 (EEOC / NYC LL144) — upstream-owned."*
- **(iv) Routing.** **Team-backlog** for the citation tightening. If the team has not completed mod-108, that is a separate backlog item at the manager's level — not a governance-architect gap.

### Step 5 — Diagnose your grading drift (10 min)

Tally your grades against the key. For each miss, write one paragraph:

- **If you marked Entry 1 or Entry 7 `evidence` because "the team has the artifact":** this is the *wave-vs-evidence* drift. Chapter 2 is explicit that the citation must be a specific URI, not a wave at where the artifact lives. The Playbook's transparency questions are the acceptance test — a reader must be able to answer them from the cited artifact. If the citation is "the team wiki," the reader has to go hunting; the cell is not yet evidence. The architect review will catch this on first pass; the team's fix cost is 5–10 minutes per cell, so it is worth catching before the review, not during.
- **If you marked Entry 5 `evidence` because the manager has a process:** this is the *practice-without-policy* drift. Chapter 2's *"Where NIST intentionally does not prescribe"* and Chapter 1's shorthand both route threshold-setting *upward*. A team-grain practice that operates without the upstream threshold it should inherit from is not evidence of a working control; it is evidence of the team filling a gap that should be filled above. Route upward.
- **If you marked Entry 10 `evidence` because the manager's memo is a specific URI and sounds responsible:** this is the *initiative-mistaken-for-authority* drift — the second scope-violation pattern. Chapter 7's ownership-boundary table is explicit; Chapter 4's trigger list routes Annex III classification *to counsel*, not to the manager's drafting queue. A specific-URI memo can still be a scope violation. The test is not "is the artifact well-authored" but "is the manager authorised to author it." Re-read Chapter 7's *"The ownership boundary, precisely"* and the two closing lines (*"the manager is not a lawyer, and not a risk engineer"*).
- **If you marked Entry 11 `wave` because the artifact is engineered-risk evidence not team evidence:** this is the inverse mis-grading — not every cell has to point at a team artifact; cells for engineered-risk subcategories should point at `ai-risk-engineer` commissioning records. Chapter 2's *"Do not duplicate `ai-risk-engineer` evidence"* is explicit. The sideways-commissioning pattern is a feature of the crosswalk, not a bug.
- **If you missed the subcategory on more than three entries:** re-read Chapter 2's table of the 12 team-grain subcategories. Each entry in the inventory above was designed to map to one (sometimes two) of them cleanly; the exercise calibrates your ability to recognise which subcategory a given team artifact evidences. Your own crosswalk will have the same cross-mapping problem — one artifact evidencing multiple subcategories, multiple artifacts needed for one subcategory — and the discipline is to pick the *primary* subcategory and cite secondary ones in the row's notes.
- **If your time-per-entry was over 8 minutes on more than three:** you are probably re-reading the chapter instead of applying it. The lab is designed for 4–6 minutes per entry; the field is 2–3 minutes per cell once practised. If grading is slow, the live crosswalk cycle will be slower.

## Expected output

A file `lab-01-grading-sheet.md` with twelve grading rows in the Step 1 template, plus a diagnosis section covering every grade that differed from the key. Roughly 0.5 page per entry; 1 page for the diagnosis.

Something like:

```
Entry 1 — review checklist operationalising trustworthy-AI characteristics
(i) GOVERN subcategory       : GOVERN 1.2 (primary); 4.1 (secondary via the checklist-
                               as-critical-thinking mechanism)
                               Rationale: Ch. 2 names mod-103 review checklist as the
                               1.2 backing; checklist is also the 4.1 mechanism.
(ii) Completeness grade      : wave
                               Playbook transparency question: "what are the
                               characteristics of trustworthy AI the system supports,
                               and how are they operationalised?"
                               Does the cited artifact answer it? NO — "see the team
                               wiki" is not findable.
(iii) What to change         : replace "see the team wiki" with the specific URI for
                               the mod-103 review-checklist artifact and the
                               standards-as-code stack path.
(iv) Gap-register routing    : team-backlog. Owner: manager. Notes: 5-minute fix
                               before architect review.
✅ match on subcategory and grade.

Entry 10 — manager-drafted Annex III classification
(i) GOVERN subcategory       : GOVERN 1.4 (regulatory alignment)
                               Rationale: Ch. 2 routes 1.4 to Ch. 4 trigger list /
                               counsel-owned legal mapping.
(ii) Completeness grade      : gap + scope violation
                               Playbook transparency question: "what legal and
                               regulatory requirements apply to this AI system?"
                               Does the cited artifact answer it? NO — manager is
                               not authorised to answer; counsel owns the answer.
(iii) What to change         : withdraw the interim memo; replace with the counsel
                               classification from 2026-07-02 as the authoritative
                               record; add a trigger-flag log for future workflows.
(iv) Gap-register routing    : upward (legal). Owner: counsel (via GC). Notes:
                               manager over-reach; future workflows route per Ch. 4
                               trigger list, not manager drafting.
✅ caught the scope violation; initial reflex was to grade `evidence` because the
   memo had a specific URI — re-reading Ch. 7 ownership-boundary caught it.
```

## Checkpoint

Before moving on to Lab 02 (Article 14 / 50 triage) or starting [Exercise 01](../exercises/exercise-01-nist-ai-rmf-govern-to-team-practice.md) on your own team's crosswalk, you should be able to answer **yes** to all six:

- Did you catch **both** deliberately planted scope-violation entries (Entries 5 and 10) and route them upward rather than grading them green?
- Did you grade waves as `wave` (not `evidence`) on Entries 1, 4, 7, 8, and 12, and name the specific-URI fix for each in one sentence?
- Did you grade the correctly-cited entries (Entries 2, 3, 6, 11) as `evidence` without over-tightening — recognising that the sideways-commissioned eval citation in Entry 11 is the shape to emulate, not duplicate?
- On every `gap` grade, did you name the owner (role and person where possible), the routing (upward / sideways / team-backlog), and one sentence of notes — so that the gap register is runnable, not a wish list?
- Did you distinguish *subcategory membership* (which GOVERN number the entry evidences) from *completeness* (whether the cell is evidence yet) — recognising that an entry can have the right subcategory and still be a wave, and an entry can be a scope violation at a correctly-identified subcategory?
- On your own time per entry, did you stay close to 4–6 minutes — or diagnose why you drifted (re-reading the chapter instead of applying it; over-thinking the subcategory when primary/secondary is acceptable; etc.)?

If any answer is no, re-read the relevant Chapter 2 section (*"The in-scope GOVERN subcategories at team altitude"*, *"The crosswalk artifact"*, *"Using the Playbook, not just the framework"*, or *"Where NIST intentionally does not prescribe"*) or Chapter 7 (*"The ownership boundary, precisely"*) before running [Lab 02](lab-02-article-14-and-50-triage-on-four-composite-workflows.md) or starting [Exercise 01](../exercises/exercise-01-nist-ai-rmf-govern-to-team-practice.md) on your real team's crosswalk.
