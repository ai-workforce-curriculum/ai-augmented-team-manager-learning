# Lab 03 — Due-Diligence Record Grading on Composite Vendor Packets

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 6 (the three-partner pattern — procurement, SecOps, legal; the seven-section due-diligence checklist; DPA specifics in the AI-vendor context; SOC 2 specifics; model-provenance clauses; the exit-plan discipline; what the chapter deliberately does *not* do), with side-checks against Chapter 7 (ownership boundary — manager does not interpret DPAs legally or re-run SecOps assessments; registry retention of sunsets; off-cycle amendment triggers) and Chapter 1 (scope — manager owns selection and evaluation, not negotiation, signature, security depth, or clause interpretation).
**Complements, does not duplicate:** [Exercise 04](../exercises/exercise-04-vendor-due-diligence-checklist.md) asks you to author the filled checklist for each tool in **your own** team's registry with real procurement / SecOps / legal sign-offs; [Exercise 05](../exercises/exercise-05-data-handling-dpa-and-soc2-posture-review.md) asks you to produce the per-vendor clause reader composed with `mod-110` Chapter 6. This lab hands you four composite vendor packets with deliberate failure modes so you can **calibrate your grading reflexes** — recognising a Type I posing as adequate, a tier-mismatched DPA, a missing model-provenance clause, a manager over-reach into clause interpretation, an empty exit plan — before you spend three hours on a checklist that an audit will reject because the DPA you filed is for the wrong tier.

## Objective

For each of four composite vendor packets on a fictional team's registry, produce a grading row with: (i) a **section-by-section completeness grade** per Chapter 6's seven sections (identification, contractual, security, data-handling, operational, exit plan, sign-offs) — `complete` / `gap` / `scope-violation` per section; (ii) a **specific fix** per gap in one sentence (what to add; who to route to — procurement / SecOps / legal); (iii) an **overall registry-admission decision** (admit; conditional-admit with named condition; reject-until-closed); (iv) an **off-cycle amendment trigger assessment** — does the packet imply a trigger the manager must act on now, not next quarter; and (v) a **boundary check** — the manager's draft of the packet must not contain scope violations (interpreting a DPA, re-running a SecOps assessment, drafting a model-provenance commitment). Then compare against the answer key.

Target: **you catch at least three of the four deliberately-planted failure modes (tier-mismatched DPA; SOC 2 Type I passing as adequate; missing model-provenance clause in a vendor whose model routes silently; an empty exit plan on a tool with internal MCP dependencies), you catch the two planted scope violations (the manager interpreting a DPA clause; the manager drafting a model-provenance commitment in place of the vendor's), and you route every gap to the correct partner (procurement / SecOps / legal) rather than filling it yourself.** The reading drifts this lab is designed to catch — *"same vendor, same DPA"*, *"SOC 2 is SOC 2"*, *"model-provenance is nice-to-have"*, *"exit plan is handled when we need it"*, *"I'll interpret the clause because legal is slow"* — are the Chapter 6 and Chapter 7 failure patterns the chapters name directly.

## Prerequisites

- Chapter 6 read end-to-end — the three-partner pattern; the seven-section checklist (A identification, B contractual, C security, D data-handling, E operational, F exit plan, G sign-offs); the DPA specifics (inference as processing, training as separate purpose, subprocessor notice, Article 22, cross-border transfer); the SOC 2 specifics (Type II over Type I, scope, qualification, freshness, ISO 42001); the model-provenance clause family; the exit-plan discipline; *"What this chapter deliberately does not do"*.
- Chapter 7 skimmed — the registry structure fields, the off-cycle amendment triggers (material data-handling change, material model-routing change, new subprocessor), the ownership-boundary table (legal interprets clauses; SecOps owns security depth; procurement owns signature; `ai-enablement-lead` owns org-wide framework).
- Chapter 1 skimmed — the scope boundary (*"The manager captures the clause state, records sign-off, and routes questions; counsel decides the legal position"*).
- `mod-110` Chapter 6 skimmed — data-class × tool-class matrix; the composition of this chapter's clauses with the operational policy.
- A blank file for your grading sheet.
- A timer.

## The fictional context

> **"Northline" team, Granite Aerospace (US-headquartered aerospace engineering firm, Seattle).** 14 engineers, 1 manager. Primary codebases: a C++ flight-controls simulation library (`flight-sim`) and a Python mission-data pipeline (`mission-data`). Data classes: `flight-sim` is **Restricted** (ITAR-adjacent; US-persons-only review scope); `mission-data` is **Confidential** (customer mission manifests; no ITAR scope). `mod-110` Chapter 6 matrix allows Enterprise-tier Copilot and Claude Code for Confidential-class work only; Restricted-class workflows require US-only hosting, no cross-border transfer, and a specific ITAR-compliance clause in the DPA. Current registry (coming out of the last Chapter 2 bake-off): four tools scheduled for due-diligence review this quarter.
>
> **Partner roster.** Procurement partner: Procurement Analyst for Engineering (routable). SecOps partner: InfoSec Vendor-Risk team (runs CAIQ assessments; publishes a dated report). Legal partner: General Counsel's AI/Privacy Counsel (reads DPA clauses; produces a dated clause reader). `ai-enablement-lead` reachable via the quarterly commit review.
>
> **This quarter's due-diligence refresh.** Four vendor packets, filled by the manager as the per-team integrator, submitted to procurement/SecOps/legal for sign-off. Each packet is a draft; this lab is the pre-submission grading pass.

Grade each packet *as if you are the team manager running the pre-submission check against Chapter 6's seven sections and Chapter 7's boundary*. Do not invent facts outside the packets; grade only what each packet contains.

## The four composite vendor packets

### Packet 1 — Cursor Business

```
A. Identification
   Vendor: Cursor (brand). Legal entity: not recorded.
   Service / tier: "Cursor" (tier not recorded — the team has Business
     tier seats purchased six months ago).
   Hosting: not recorded.
   Subprocessors: not recorded.
   Date of record: 2026-11-04. Next review: 2027-02-04.

B. Contractual
   MSA: "signed by procurement, 2026-05-02". Version not recorded.
   DPA: "signed; version 2025.08 on file".
   Cross-border transfer mechanism: not recorded.
   Commercial tier: "Business — same as the DPA we signed with their
     Enterprise tier a year ago, same company."
   Auto-renewal: not recorded.
   Notice period: not recorded.
   Overage terms: not recorded.
   Indemnity / IP warranty: "per MSA".

C. Security
   SOC 2: "Type II, on file".
   Scope: not recorded.
   Report period: not recorded.
   ISO/IEC 27001: not recorded.
   ISO/IEC 42001: not recorded.
   CAIQ response: not filed yet.

D. Data handling
   Training on your data: "Cursor Business is zero-retention mode on by
     default; training excluded".
   Retention: "0 days".
   Residency: "US primary; EU available on Enterprise, we are on
     Business."
   Model-provenance: "Cursor routes to frontier models — OpenAI, Anthropic,
     and others as they add them. They control the routing."
   Deletion: not recorded.

E. Operational
   Authentication: SSO via SAML; MFA required.
   Audit-log retention: 90 days vendor-side.
   Subprocessor change notice: not recorded.

F. Exit plan
   "Cancel the subscription; nothing to decommission."

G. Sign-offs
   Procurement: [name], 2026-05-02.
   SecOps: not yet.
   Legal: not yet.
   Manager: [name], 2026-05-04.
```

### Packet 2 — Claude Code (via Claude for Work Enterprise)

```
A. Identification
   Vendor: Anthropic PBC (US-registered).
   Service / tier: "Claude for Work (Enterprise), via Claude Code CLI."
   Hosting: US primary; the team has NOT opted into EU residency.
   Subprocessors: current list pulled from trust centre 2026-10-28; three
     subprocessors (cloud, monitoring, logging), all US.
   Date of record: 2026-11-04. Next review: 2027-02-04.

B. Contractual
   MSA: v2026.03, signed 2026-04-02 by procurement.
   DPA: v2026.03, signed same day; covers Claude for Work Enterprise.
   Cross-border transfer mechanism: SCCs with transfer impact assessment
     filed by legal on 2026-04-15.
   Commercial tier: Enterprise (contracted; not Pro or Business).
   Auto-renewal: yes, annual; 60-day notice.
   Overage terms: committed-use with metered overage.
   Indemnity / IP warranty: per MSA; legal has the clause reader.

C. Security
   SOC 2 Type II: scope covers Claude for Work service; auditor [firm];
     report period 2025-04-01 to 2026-03-31; opinion unqualified.
   ISO/IEC 27001: certified; certificate number on file with SecOps.
   ISO/IEC 42001: pending as of record date (vendor publicly committed).
   Vulnerability disclosure contact: security@anthropic.com.
   Incident notification SLA: 72h per DPA § 7.
   CAIQ response filed by SecOps on 2026-05-11.

D. Data handling
   Training on your data: contractually excluded for the Enterprise tier
     per DPA § 4.2. Verified by legal clause reader.
   Retention: zero retention configurable; team configured 0 days.
     Verification: control panel screenshot on file 2026-05-14.
   Residency: US primary; team has not opted into EU residency because
     no team workflows require it.
   Access and audit: vendor access controls per DPA § 5; customer audit
     rights per DPA § 11.
   Deletion: per DPA § 8; verified process.
   Model-provenance: service uses Anthropic's Claude family; model changes
     announced in advance per enterprise agreement § 6.3 (material change
     SLA = 30 days).

E. Operational
   Authentication: SSO via SAML; MFA required; SCIM provisioning enabled.
   Audit-log retention: vendor 90 days; exported weekly to internal SIEM.
   Subprocessor change notice: 30 days per DPA.
   Material-change SLA: contracted; confirmed at trust-centre check.

F. Exit plan
   Decommissioning: disable SSO application, submit deletion request via
     DPA § 8 mechanism, update mod-106 tool-authorisation policy, retire
     team-owned MCP server and archive config.
   Data-retrieval: export via console; 30-day retention window post-
     deletion for export.
   Switch-cost estimate: ~3 engineer-weeks to transition active workflows;
     ~2 ICs need retraining on alternative Tier 3 agent; low stranded-data
     risk due to zero-retention.
   Dependencies: 1 team-owned MCP server; portable to alternative Tier 3
     agents.

G. Sign-offs
   Procurement: [name], 2026-04-02.
   SecOps: [name], 2026-05-14.
   Legal / privacy: [name], 2026-04-30.
   Manager: [name], 2026-05-20.
   Open conditions: ISO 42001 certification tracked; re-review when issued.
```

### Packet 3 — GitHub Copilot Enterprise

```
A. Identification
   Vendor: GitHub, Inc. (Microsoft subsidiary).
   Service / tier: GitHub Copilot Enterprise.
   Hosting: US primary; EU residency available on Enterprise (team has
     opted in for mission-data work).
   Subprocessors: current list pulled from GitHub trust centre 2026-10-18;
     includes Azure (model hosting), one monitoring vendor.
   Date of record: 2026-11-04. Next review: 2027-02-04.

B. Contractual
   MSA: v2025.11, signed by procurement 2025-12-03.
   DPA: v2025.11, signed same day; covers Copilot Enterprise.
   Cross-border transfer mechanism: SCCs on file; EU-US Data Privacy
     Framework certification noted in DPA preamble.
   Commercial tier: Enterprise (contracted).
   Auto-renewal: yes, annual; 90-day notice.
   Overage terms: n/a (seat-based, not usage-based).
   Indemnity / IP warranty: per MSA; specifically includes code-generation
     output indemnification per Copilot Enterprise terms.

C. Security
   SOC 2: "Type I, on file" — observation period: point-in-time 2024-09-30;
     report dated 2024-10-15.
   Scope: "GitHub Enterprise Cloud" — does not explicitly list Copilot
     Enterprise as a separate service in the scope statement reviewed.
   ISO/IEC 27001: certified; certificate number on file.
   ISO/IEC 42001: not recorded.
   CAIQ response filed by SecOps on 2026-01-18.

D. Data handling
   Training on your data: contractually excluded for Copilot Enterprise
     per DPA § 3.1.
   Retention: configurable; team configured 0 days for prompts and
     suggestions.
   Residency: EU opt-in enabled for mission-data engineers; US for
     flight-sim engineers.
   Access and audit: per DPA § 5; customer audit rights per DPA § 10.
   Deletion: per DPA § 7.
   Model-provenance: service uses "GitHub-hosted foundation models"; the
     model behind the product is "subject to GitHub's routing decisions
     and may change with Copilot product updates." No notice SLA for
     model routing changes recorded.

E. Operational
   Authentication: SSO via SAML; MFA required; SCIM provisioning enabled.
   Audit-log retention: GitHub audit log; 6-month vendor retention;
     exported to internal SIEM.
   Subprocessor change notice: 30 days per DPA.

F. Exit plan
   Decommissioning: disable Copilot in GitHub org settings, revoke seats,
     ensure settings propagate, update mod-106 tool-authorisation policy.
   Data-retrieval: n/a (zero retention).
   Switch-cost estimate: ~1 engineer-week to transition.
   Dependencies: .github/copilot-instructions.md in each repo; portable.

G. Sign-offs
   Procurement: [name], 2025-12-03.
   SecOps: [name], 2026-01-25.
   Legal / privacy: [name], 2026-01-10.
   Manager: [name], 2026-02-02.
   Open conditions: ITAR-compliance clause for flight-sim data path
     confirmed by legal as separate letter 2026-01-12.
```

### Packet 4 — "ClipMate" (hypothetical cheap IDE assistant that the manager piloted on three mission-data engineers in Q[N-1])

```
A. Identification
   Vendor: ClipMate Technologies (private company; no public legal entity
     name recorded in the packet).
   Service / tier: "ClipMate Pro — the mid tier; cheaper than their
     Enterprise which is 5x the price."
   Hosting: "US" (per trust-centre page screenshot in packet).
   Subprocessors: not recorded.
   Date of record: 2026-11-04. Next review: not set.

B. Contractual
   MSA: individual-seat terms-of-service accepted by each pilot engineer
     via the product sign-up flow.
   DPA: "the vendor's standard DPA is attached to the TOS; in the
     manager's reading of it, § 4 commits them to no training on inputs
     for Pro-tier customers."
   Cross-border transfer mechanism: not recorded.
   Commercial tier: Pro (not Enterprise).
   Auto-renewal: monthly per TOS.
   Notice period: cancel-anytime via console.
   Overage terms: unlimited usage per TOS.
   Indemnity / IP warranty: not recorded.

C. Security
   SOC 2: "Type I in progress per sales; no report yet."
   ISO/IEC 27001: not recorded.
   ISO/IEC 42001: not recorded.
   CAIQ response: not run (SecOps backlogged; manager did not file a
     vendor-risk ticket).

D. Data handling
   Training on your data: "manager's reading is that § 4 excludes training
     for the Pro tier."
   Retention: "logs retained 30 days per vendor TOS § 7; ClipMate claims
     to anonymise inputs after 30 days."
   Residency: US per trust-centre screenshot.
   Access and audit: not recorded.
   Deletion: "console has a 'delete my account' button; vendor states
     verification within 30 days."
   Model-provenance: "the manager's note: ClipMate commits in this packet
     to using only Anthropic Claude Sonnet and OpenAI GPT-4 class models
     for mission-data engineers and to 30-day advance notice on any model
     change. This matches what the vendor's sales engineer said on the
     call; the manager wrote the commitment into the packet so we have it
     on file."

E. Operational
   Authentication: SSO via SAML — Pro tier upgrade only (sales said
     available on request); currently: individual password + email MFA.
   Audit-log retention: not recorded.
   Subprocessor change notice: not recorded.

F. Exit plan
   "Cancel via console."

G. Sign-offs
   Procurement: not yet.
   SecOps: not yet.
   Legal / privacy: not yet.
   Manager: [name], 2026-10-15.
   Notes: "Three-engineer pilot ran Q[N-1]; outcomes positive; proposing
     team-wide seat purchase next quarter."
```

## Steps

### Step 1 — Set up your grading sheet (3 min)

Create a working file `lab-03-grading-sheet.md` with this template, repeated once per packet:

```
Packet #: <N>
Vendor + tier: <from the packet's Section A>

(i) Section-by-section grade (complete / gap / scope-violation):
    A Identification     : <grade> — <one-sentence rationale>
    B Contractual        : <grade> — <one-sentence rationale>
    C Security           : <grade> — <one-sentence rationale>
    D Data handling      : <grade> — <one-sentence rationale>
    E Operational        : <grade> — <one-sentence rationale>
    F Exit plan          : <grade> — <one-sentence rationale>
    G Sign-offs          : <grade> — <one-sentence rationale>

(ii) Specific fixes (one per gap; include partner to route to):
    <list>

(iii) Overall decision:
    admit / conditional-admit (with named conditions) / reject-until-closed
    <one-sentence rationale>

(iv) Off-cycle amendment trigger assessment:
    Does this packet imply a trigger that requires action now (not next
      quarter)?
    <y/n; list of triggers>

(v) Boundary check:
    Scope violations in the manager's draft?
    <y/n; list of violations with what the correct action should be>
```

Time yourself. Target per packet: ~12 minutes. If you spend more than 15 minutes, note the drift and move on.

### Step 2 — Grade Packets 1–2 (25–30 min)

Grade Packet 1 (Cursor Business, light draft) and Packet 2 (Claude Code, the "good" draft) first. Packet 2 is close to the Chapter 6 worked example; Packet 1 is a thin draft with gaps. Scoring Packet 2 as a gold standard first calibrates your reading for the others.

### Step 3 — Grade Packets 3–4 (25–30 min)

Grade Packet 3 (Copilot Enterprise — contains at least one deliberately planted trap in the SOC 2 section and one in the model-provenance section) and Packet 4 (ClipMate — contains multiple deliberately planted traps including two scope violations in the manager's draft). Watch specifically for the boundary check in Section (v).

### Step 4 — Compare against the answer key (10–15 min)

Read the key below only after you have graded all four.

#### Answer key — Packet 1 (Cursor Business)

- **Section A — gap.** Legal entity name missing (brand ≠ entity; Chapter 6 Section A requires *"Vendor legal entity name (the contracting entity may differ from the brand)"*). Hosting not recorded. Subprocessors not recorded. Tier *is* recorded but the packet's claim "same as the Enterprise DPA" is an anti-pattern — see Section B.
- **Section B — gap, with a planted trap.** DPA v2025.08 is on file but the packet notes the DPA was *"signed with their Enterprise tier a year ago"* and the team is on *Business* tier now. **The deliberately planted trap:** Chapter 6 is explicit that the DPA / SOC 2 / data-handling posture of a service's enterprise tier is *not* the same as its business or consumer tier (*"The DPA for Claude for Work is not the DPA for the Anthropic API; the SOC 2 scope for OpenAI Enterprise is not the SOC 2 scope for ChatGPT consumer; Copilot Business and Copilot Enterprise have different data posture. Record the tier explicitly."*). A DPA signed for a different tier does not automatically cover the current tier. Fix: route to legal to confirm the DPA scope language — does the v2025.08 DPA cover Business tier explicitly, or is a tier-specific addendum needed? The packet's own claim ("same company, same DPA") is a scope violation if it is being used as a legal interpretation rather than a question routed to legal.
- **Section C — gap.** SOC 2 Type II on file but scope and report period not recorded. Chapter 6 is explicit: *"Scope of the report matters. The SOC 2 is scoped to specific services; a vendor with a SOC 2 covering 'the hosting platform' may not have that report cover the AI service on top of it."* Also *"Observation period vs report date. The audit covers a window ending on a date… A SOC 2 whose observation period ended 18 months ago is a stale artifact."* CAIQ not filed yet — SecOps action.
- **Section D — gap.** Zero-retention and training exclusion recorded but deletion process not recorded. Model-provenance recorded at vendor level but no change-notice SLA captured — Chapter 6 names this as the *"AI-specific clause family earlier contracts missed"*: *"How is the team notified of model changes?"* and *"the clause the team wants: material changes to model routing or defaults are notified in advance"*. For a vendor that routes to multiple frontier models (OpenAI, Anthropic, and others), the model-change notice is live.
- **Section E — gap.** Subprocessor change notice not recorded (Chapter 6 Section E).
- **Section F — gap (asymmetric-commitment anti-pattern).** *"Cancel the subscription; nothing to decommission"* ignores the Chapter 3 anti-pattern Chapter 6 operates against: data-retrieval format, data-export window, switch-cost estimate, dependencies. For Cursor Business specifically, if the team has a `.cursor/rules/` repo and prompt pack built against the product, those are *portable* (that is the right answer) — but the exit plan must *say* that, not elide it. For a Chapter 7 registry, a tool whose exit plan is empty is marked as asymmetric.
- **Section G — gap.** Procurement signed six months ago; SecOps and legal not yet signed; manager signed before the other two. Chapter 6 Section G requires all four sign-offs or named open conditions; this packet is under half-done.
- **Fixes (route list).** Legal entity name (procurement to pull); hosting detail (vendor trust centre; manager pulls); subprocessor list (vendor trust centre; manager pulls, SecOps verifies); DPA scope-to-Business-tier confirmation (**legal**, not manager); MSA version (procurement); cross-border transfer mechanism (legal); auto-renewal and notice (procurement); overage terms (procurement); SOC 2 scope + report period (SecOps); CAIQ (SecOps); deletion process (vendor docs; legal reads); model-change notice SLA clause (legal reads; procurement may negotiate for it); subprocessor change notice (legal); exit-plan: data-retrieval, switch-cost, dependencies (manager fills from Chapter 6 Section F pattern); SecOps and legal sign-offs.
- **Overall decision.** **Conditional-admit** at best — the vendor is clearly on the Chapter 2 matrix for Tier 2, but the record is not yet admissible to the Chapter 7 registry as filed. Named conditions: legal confirms DPA tier scope; SecOps CAIQ response; SOC 2 scope confirmation; exit plan expanded. Target: closed within 4 weeks before next quarterly review.
- **Off-cycle trigger.** Not an off-cycle trigger yet — this is the pre-registry due-diligence, not an in-service incident.
- **Boundary check.** **Yes — one scope violation.** The packet's claim *"Business — same as the DPA we signed with their Enterprise tier a year ago, same company"* is the manager making a legal determination about DPA scope. Chapter 7 is explicit: *"Legal / Privacy Office owns clause interpretation; the manager files the clause and routes questions."* The packet should say *"tier mismatch between current (Business) and signed DPA (Enterprise); routed to legal 2026-11-05"* — not state a conclusion the manager is not authorised to state.

#### Answer key — Packet 2 (Claude Code / Claude for Work Enterprise)

- **Section A — complete.** Legal entity, service + tier, hosting, subprocessors, date, next review all present.
- **Section B — complete.** MSA + DPA + cross-border transfer mechanism all dated and tier-specific; commercial tier contracted explicitly ("Enterprise; not Pro or Business" — the exact discipline Chapter 6 names).
- **Section C — complete.** SOC 2 Type II with scope + report period + opinion; ISO 27001 recorded; ISO 42001 pending and tracked as an open condition; CAIQ filed by SecOps with a date.
- **Section D — complete.** All five Chapter 6 Section D clauses present with vendor-clause citations (DPA § numbers), model-provenance including the change-notice SLA (*"material change SLA = 30 days"*), tier-specific.
- **Section E — complete.** SSO/SAML/SCIM, log retention + SIEM export, subprocessor change notice, material-change SLA.
- **Section F — complete.** Decommissioning steps (specific; ties into `mod-106` policy and the MCP server retirement), data-retrieval window, switch-cost estimate (3 engineer-weeks, 2 ICs retraining), dependencies (1 team-owned MCP server, portable).
- **Section G — complete.** All four sign-offs with named dates; open condition tracked (ISO 42001).
- **Fixes.** None required at this review. Open condition (ISO 42001) is correctly a tracked condition, not a gap.
- **Overall decision.** **Admit.** This packet is close to the Chapter 6 worked-example shape and is the shape Exercise 04 targets.
- **Off-cycle trigger.** Not triggered. If the ISO 42001 certification is issued during the quarter, Chapter 7's registry change-log gets a dated entry; not a full off-cycle re-review.
- **Boundary check.** **No scope violations.** The packet captures what legal wrote in the clause reader (*"Verified by legal clause reader"*) without the manager re-interpreting it. The model-provenance clause cites the enterprise agreement section number, not the manager's drafting.

#### Answer key — Packet 3 (GitHub Copilot Enterprise)

- **Section A — complete.** Legal entity, tier, hosting with EU opt-in, subprocessors dated.
- **Section B — complete.** MSA + DPA dated; SCCs + DPF noted; tier contracted; auto-renewal, notice, overage, indemnity (with Copilot-specific code-generation IP coverage — which Chapter 6 flags as *"especially relevant for code-generation tools"*).
- **Section C — gap with a planted trap.** **The deliberately planted trap:** the SOC 2 is *Type I* (point-in-time 2024-09-30; report dated 2024-10-15), not Type II. Chapter 6 is explicit: *"Type II is what you want. SOC 2 Type I is a point-in-time; Type II covers an operating period (usually 6–12 months). Treat Type II as the serious artifact; Type I is a weak signal."* The report is also *two years old* at record date (2026-11-04) — Chapter 6: *"A SOC 2 whose observation period ended 18 months ago is a stale artifact."* And the scope *"GitHub Enterprise Cloud"* does not explicitly list Copilot Enterprise — Chapter 6: *"Scope of the report matters. The SOC 2 is scoped to specific services; a vendor with a SOC 2 covering 'the hosting platform' may not have that report cover the AI service on top of it."* All three failures compound. Fix: pull GitHub's current SOC 2 Type II report (which GitHub does publish for Copilot via their trust portal) and confirm scope lists Copilot Enterprise; route the review to SecOps; flag if current report also fails scope.
- **Section D — gap with a second planted trap.** **The second deliberately planted trap:** model-provenance states the service uses *"GitHub-hosted foundation models"* with routing *"subject to GitHub's routing decisions and may change with Copilot product updates"* — **and no notice SLA is recorded**. Chapter 6 names this exact gap: *"vendors sometimes change defaults (the model behind a product name changes, the context length changes, the system prompt changes) outside the team's deploy cycle. The clause the team wants: material changes to model routing or defaults are notified in advance."* For an ITAR-adjacent team with Restricted flight-sim data, silent model routing changes are a Chapter 7 off-cycle trigger waiting to happen. Fix: procurement to pursue a model-change notice clause at next renewal; legal to read any existing notice-of-material-change language in the MSA; manager updates the packet when procurement reports back.
- **Section E — complete.** SSO, MFA, SCIM, audit log, subprocessor notice recorded.
- **Section F — complete** (for a Buy stance; `.github/copilot-instructions.md` is the portable artifact).
- **Section G — complete** with the ITAR-compliance clause as a separate open condition (handled by legal as a letter — the correct discipline for an ITAR carve-out).
- **Fixes (route list).** SOC 2 Type II current report + scope confirmation (SecOps); model-change-notice SLA clause (procurement to negotiate at renewal; legal to read existing language).
- **Overall decision.** **Conditional-admit** — tool stays in the registry pending (a) refreshed SOC 2 Type II with Copilot Enterprise explicitly in scope, and (b) model-change-notice SLA confirmation at renewal. Named conditions with dates.
- **Off-cycle trigger.** **Yes — one.** A stale SOC 2 in the record is a Chapter 7 off-cycle trigger: *"Vendor announces material data-handling change"* and related. Here it is not a vendor announcement; it is a *manager-discovered stale artifact* — route to SecOps now, not at the Q[N+1] review.
- **Boundary check.** No scope violations by the manager. The DPA sections cited reference legal's clause reader; the SOC 2 scope question is routed to SecOps rather than interpreted by the manager.

#### Answer key — Packet 4 (ClipMate — the "cheap pilot" packet)

This packet is the lab's primary teaching case — multiple compounded failure modes, two of which are scope violations in the manager's draft.

- **Section A — gap.** No public legal entity recorded; tier is Pro (not Enterprise); next review not set.
- **Section B — gap, with planted trap #1.** DPA covered only by *"the vendor's standard DPA is attached to the TOS; in the manager's reading of it, § 4 commits them to no training on inputs for Pro-tier customers."* **The deliberately planted trap:** this is the manager interpreting a DPA clause. Chapter 6 Section D includes *"Training-on-your-data clause — exactly as worded in the DPA / TOS for the contracted tier"*; Chapter 6 is explicit about the boundary: *"Does not interpret DPAs legally. Legal / privacy office reads the clause; the manager captures what legal says. Where the manager has an opinion, it is a flag to legal, not an interpretation."* Chapter 7 reinforces: *"Legal / Privacy Office owns clause interpretation; the manager files the clause and routes questions."* The manager's own reading of § 4 is not a DPA record; it is a flag that needs legal. Also, no signed-by-the-organisation MSA — click-through TOS by each engineer is not an organisation-level contractual record and does not create procurement/legal/SecOps sign-off leverage.
- **Section C — gap.** SOC 2 Type I in progress is *not* a report on file; it is a vendor claim. No report; no ISO 27001; no CAIQ run. Chapter 6: *"Type I is a weak signal"* (and an unfinished Type I is not even that). CAIQ not filed is a SecOps gap the manager did not route — a process failure, not just a missing field.
- **Section D — gap with planted trap #2.** **The second deliberately planted trap:** the model-provenance section reads *"the manager's note: ClipMate commits in this packet to using only Anthropic Claude Sonnet and OpenAI GPT-4 class models for mission-data engineers and to 30-day advance notice on any model change. This matches what the vendor's sales engineer said on the call; the manager wrote the commitment into the packet so we have it on file."* **This is the manager drafting a vendor commitment the vendor has not made in writing**, based on a sales-call recollection. Chapter 6 is explicit: the model-provenance clause must be *the vendor's contractual commitment*, not a manager-authored summary. Sales-call commitments are not contract; writing them into the packet "so we have them on file" is a scope violation (drafting vendor terms is procurement + legal work, not the manager's), and a weak artifact for the audit (the vendor will not be bound by the manager's packet). The right action is to route to procurement for a written commitment in the contract, and until it is written, the packet reflects *the vendor's actual published position*, not the manager's summary. Residency and retention also missing or thin.
- **Section E — gap.** Individual password + email MFA on a Pro tier is not SSO/SAML at an organisation level; SCIM not available on Pro per packet. For a team doing mission-data work, this is not acceptable operational posture.
- **Section F — gap (asymmetric commitment).** *"Cancel via console"* elides data-retrieval, deletion verification, switch-cost, and the fact that three engineers' pilots have produced prompt packs and workflow habits that are *not portable* without being named.
- **Section G — gap.** No procurement, SecOps, or legal sign-off. Manager-only sign-off is not a complete Section G.
- **Fixes (route list).** The entire packet needs re-shaping before registry admission. Specifically: (a) procurement to pursue an org-level MSA + DPA + SOC 2 Type II report with Enterprise-tier terms if the team is serious about the vendor — not continue on individual TOS click-through; (b) legal to read the actual DPA (not the manager's reading of it); (c) SecOps CAIQ; (d) withdraw the manager's model-provenance drafting and replace with the vendor's actual contractual position (or note "no vendor commitment on record" if there is none); (e) authentication must move to SSO/SAML (Enterprise tier required); (f) complete the exit plan or acknowledge the asymmetric commitment.
- **Overall decision.** **Reject-until-closed.** The packet is not admissible to the Chapter 7 registry. The three-engineer pilot has run, but the data-handling and security posture is not at a level the registry can admit for a team-wide seat purchase. This is also an off-cycle trigger case — the pilot has been running on a tier the team's data classes cannot defend; the right action is to *end the pilot on the Pro tier immediately* and route the vendor conversation through procurement if the team wants to continue evaluating.
- **Off-cycle trigger.** **Yes — two.** First: a running pilot on a tier the team's data classes cannot defend (Chapter 7's *"new tool appears in team usage without entry"* trigger applies — the pilot is effectively shadow adoption because the due-diligence record was never filed). Second: the manager-drafted vendor commitment is an audit-risk artifact that should be withdrawn now.
- **Boundary check.** **Yes — two scope violations in the manager's draft.** (1) The manager interpreting the DPA § 4 clause ("commits them to no training on inputs for Pro-tier customers") instead of routing to legal. (2) The manager drafting a vendor commitment on model-provenance from a sales-call recollection. Both are Chapter 7 ownership-boundary violations (*"the manager is not a lawyer"*; model-provenance commitments are procurement+legal+vendor contractual work, not a manager's packet entry). The **correct action** for each: withdraw the manager's interpretation / drafting from the packet; route the open questions to legal (DPA read) and procurement (vendor commitment negotiation); update the packet when those partners report back.

### Step 5 — Diagnose your drift (10 min)

Tally your grades against the key. For each miss, write one paragraph:

- **If you accepted Packet 1's tier-mismatched DPA as adequate:** this is the *same-vendor-same-DPA* drift. Chapter 6 is explicit that *"Business and Enterprise tiers have different data posture; record the tier explicitly."* The DPA is *tier-specific*; the manager's claim that the Enterprise DPA covers the Business tier is a legal determination the manager is not authorised to make. Route to legal.
- **If you accepted Packet 3's SOC 2 Type I as adequate:** this is the *SOC-2-is-SOC-2* drift. Chapter 6 is explicit: *"Type II is what you want. Type I is a weak signal."* A two-year-old Type I with a scope that does not explicitly cover Copilot Enterprise fails on three independent axes (type, freshness, scope). The fix is to pull the current Type II.
- **If you accepted Packet 3's silent-model-routing clause:** this is the *model-provenance-is-nice-to-have* drift. Chapter 6 names model-provenance as *"the AI-specific clause family earlier contracts missed"*; for an ITAR-adjacent team, silent model routing is a Chapter 7 off-cycle trigger waiting to happen. The fix is a notice-of-material-change clause.
- **If you graded Packet 4 as `conditional-admit` or green-with-fixes:** you are missing the scope violations, which are the lab's primary teaching case. The manager interpreting DPA § 4 and drafting a vendor model-provenance commitment are both ownership-boundary violations Chapter 7 names explicitly. The packet is reject-until-closed, and the pilot should stop until the shape is fixed.
- **If you missed the fact that Packet 4 is also an off-cycle-trigger case (shadow pilot on an inadequate tier):** this is the *due-diligence-is-pre-registry-only* drift. Chapter 7's off-cycle amendment triggers include *"new tool appears in team usage without entry"* — a pilot that runs without a filed due-diligence record is that trigger. The pilot is live; the trigger is live; action is now, not Q[N+1].
- **If you filled a gap on any packet by having the manager draft the missing content** (e.g., "I'll write a model-change notice SLA, legal can approve it later"): this is the *initiative-mistaken-for-authority* drift from Chapter 3's R6 reading and Chapter 7's ownership boundary. Legal reads the clause; the manager routes. The packet is better empty than full of manager-authored legal content that an audit will later surface.
- **If your time-per-packet was over 15 minutes on more than two:** you are probably re-reading Chapter 6 instead of applying it. Chapter 6's seven sections give the grading rubric in ~2 pages; a trained reader applies them in 8–10 minutes per packet. If grading is slow, the quarterly registry refresh (four to eight packets) will be slower than it needs to be.

## Expected output

A file `lab-03-grading-sheet.md` with four grading rows in the Step 1 template, plus a diagnosis section covering every grade that differed from the key. Roughly 1 page per packet; 1 page for the diagnosis.

Something like:

```
Packet 4 — ClipMate (Pro tier)

(i) Section-by-section:
    A Identification     : gap — legal entity missing; tier is Pro not
                           Enterprise; next review not set.
    B Contractual        : gap + scope-violation — click-through TOS not
                           an org-level contract; manager interpreting
                           DPA § 4 (route to legal).
    C Security           : gap — SOC 2 Type I "in progress" is not a
                           report; no CAIQ run.
    D Data handling      : gap + scope-violation — manager drafting
                           vendor model-provenance commitment from sales-
                           call recollection (route to procurement for
                           contractual commitment).
    E Operational        : gap — individual password + email MFA on Pro
                           tier; no SSO at org level.
    F Exit plan          : gap — "cancel via console" elides data
                           retrieval, switch-cost, and three pilots'
                           prompt packs.
    G Sign-offs          : gap — manager-only; no procurement, SecOps,
                           or legal sign-off.

(ii) Fixes (route list):
    - Legal: read the actual DPA; withdraw manager's reading.
    - Procurement: org-level MSA + DPA + Enterprise tier if continuing.
    - Procurement: written vendor commitment on model-provenance; withdraw
      manager's packet-drafted version.
    - SecOps: file CAIQ; await Type II.
    - Operational: SSO/SAML (Enterprise tier required).
    - Manager: expand exit plan per Ch. 6 Section F pattern.

(iii) Overall decision: reject-until-closed. End the pilot on Pro tier
      immediately; route to procurement if continuing evaluation.

(iv) Off-cycle amendment trigger: yes — two.
     1. Shadow pilot on an inadequate tier (Ch. 7 "new tool appears in
        team usage without entry" trigger).
     2. Manager-drafted vendor commitment in the packet is an audit-risk
        artifact; withdraw now.

(v) Boundary check: yes — two scope violations.
    1. Manager interpreting DPA § 4 — route to legal.
    2. Manager drafting model-provenance commitment from sales call —
       route to procurement.

✅ caught both scope violations; initial reflex on (v.2) was to treat
   "we have it on file" as a legitimate capture — Ch. 6 "manager captures
   what legal/vendor says, not what the manager thinks they should have
   said" caught it.
```

## Checkpoint

Before moving on from Lab 03 to [Exercise 04](../exercises/exercise-04-vendor-due-diligence-checklist.md) and [Exercise 05](../exercises/exercise-05-data-handling-dpa-and-soc2-posture-review.md) on your own team's registry, you should be able to answer **yes** to all six:

- Did you catch Packet 1's **tier-mismatched DPA** — recognising that a signed Enterprise DPA does not automatically cover a Business-tier deployment — and route the question to legal rather than accept the manager's claim?
- Did you catch Packet 3's **SOC 2 Type I passing as adequate** — recognising the three compounded failures (Type I, two-year stale, scope does not explicitly cover Copilot Enterprise) and route to SecOps for the current Type II?
- Did you catch Packet 3's **missing model-change notice SLA** and recognise it as a Chapter 7 off-cycle trigger risk for an ITAR-adjacent team — routing to procurement for the renewal clause?
- Did you catch **both of Packet 4's scope violations** — the manager interpreting DPA § 4, and the manager drafting a vendor model-provenance commitment from a sales call — and withdraw both from the packet rather than treat them as legitimate captures?
- Did you catch Packet 4's **running pilot on an inadequate tier** as an active off-cycle trigger (shadow adoption under Chapter 7's trigger list) — requiring action now, not at Q[N+1]'s review?
- On every gap you identified, did you route to the correct partner (procurement / SecOps / legal) rather than filling the gap yourself — recognising Chapter 7's *"the manager files the result and routes flags; does not re-run the assessment or interpret the clause"*?

If any answer is no, re-read the relevant Chapter 6 section (*"The three-partner pattern"*, *"The due-diligence checklist"*, *"DPA specifics in the AI-vendor context"*, *"SOC 2 specifics in the AI-vendor context"*, *"Model-provenance clauses"*, or *"What this chapter deliberately does not do"*) or Chapter 7 (*"The ownership boundary"*, *"Off-cycle amendment triggers"*) before starting [Exercise 04](../exercises/exercise-04-vendor-due-diligence-checklist.md) on your real team's registry.
