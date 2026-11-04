# Chapter 6 — Vendor Due Diligence with Procurement, Security, and Legal

> *The vendor's trust-centre page is a starting document, not an audit. The due-diligence record is what you can hand to the head of AI governance on Tuesday with a signature from procurement, a sign-off from SecOps, and a dated clause-reader from legal. The failure mode is not "we didn't read the DPA." The failure mode is "the DPA we have doesn't cover the tier we actually use."*

## Motivation

Every tool in the Chapter 7 registry needs a due-diligence record. The record is not produced by the manager alone; it is produced by **three partners each owning a specialty** — procurement, SecOps, legal / privacy office — with the manager as the per-team integrator who files the composed artifact. The record has to be:

- **Specific to the service tier the team uses.** The DPA for Claude for Work is not the DPA for the Anthropic API; the SOC 2 scope for OpenAI Enterprise is not the SOC 2 scope for ChatGPT consumer; Copilot Business and Copilot Enterprise have different data posture. Record the tier explicitly.
- **Dated.** A DPA from 2023 is probably stale by 2026; a SOC 2 report is annual. Dated records trigger re-review on cadence.
- **Composable with [`mod-110` Chapter 6](../mod-110-ai-governance-and-policy-at-team-scope/06-data-ip-and-confidentiality-practice.md).** The data-class × tool-class matrix is where this record's clauses land operationally. Chapter 6 of this module is where the clauses are captured; Chapter 6 of mod-110 is where they are *operated*.

This chapter does four things. First, it names the **three-partner pattern** (procurement + SecOps + legal) and the manager's role in each. Second, it defines the **due-diligence checklist** that produces Exercise 04's filled record per vendor. Third, it describes the **DPA / SOC 2 / model-provenance** specifics that are new or newly load-bearing in the AI-vendor context. Fourth, it defines the **exit plan** that every entry on the registry carries.

## Core concepts

### The three-partner pattern

Due-diligence work does not happen inside the team. Three external partners each own a specialty; the manager routes work to each and files the composed output.

| Partner | What they own | What the manager does | What the record contains |
|---|---|---|---|
| **Procurement** | Contract negotiation, master service agreement, commercial terms, enterprise commit architecture | Produces the business case (fit, cost, projected usage), initiates the vendor-request workflow, signs off on commercial requirements from a team perspective | Contract reference (version + date), signed DPA reference, commercial tier, overage terms, auto-renewal clause, notice period |
| **SecOps / InfoSec** | Vendor security assessment, penetration testing, red-teaming, attack-surface analysis, incident-notification SLAs, subprocessor assessment | Fills the CAIQ or SIG questionnaire responses for the team (what data flows, what identities, which networks), consumes SecOps' assessment report, flags gaps to the manager | SOC 2 Type II report (date, scope, audit firm), ISO 27001 cert if applicable, CAIQ response or SIG / SIG-Lite response (date), pen-test summary if shared, vulnerability disclosure contact |
| **Legal / Privacy Office** | DPA interpretation, cross-border transfer legality, model-provenance clause interpretation, regulated-use-case classification, AI Act applicability | Captures the vendor's DPA, flags the *tier* the team uses, flags the *data classes* the team routes, routes questions back to legal | Signed DPA (with the organisation's name, date), Standard Contractual Clauses if cross-border, data-residency clause, retention clause, deletion-request process, model-provenance clause |

The manager's role in all three columns is the same: **integrator, not re-implementer**. Fill the questionnaires; route the questions; file the record; keep it current. The manager does not re-run a security assessment and does not re-write a DPA.

### The due-diligence checklist

The Exercise 04 deliverable is a filled checklist per vendor on the registry. The checklist sections:

**Section A — Vendor identification and service identification**

- Vendor legal entity name (the contracting entity may differ from the brand).
- Service name and tier exactly as used (e.g., "Anthropic Claude for Work (Enterprise)" vs "Anthropic Claude API").
- Hosting location and jurisdiction (vendor's or the service's).
- Subprocessors that touch the team's data, with jurisdictions.
- Date of this record and next review date.

**Section B — Contractual posture**

- Master service agreement (MSA) in force; version and date.
- [Data Processing Addendum (DPA)](https://gdpr-info.eu/art-28-gdpr/) in force; version and date. Where the organisation has data subjects in the EU / UK, the DPA covers [GDPR Article 28](https://gdpr-info.eu/art-28-gdpr/) requirements.
- Cross-border transfer mechanism: [Standard Contractual Clauses](https://commission.europa.eu/law/law-topic/data-protection/international-dimension-data-protection/standard-contractual-clauses-scc_en), Binding Corporate Rules, adequacy decision.
- Commercial tier (consumer / business / enterprise) as contracted — *not* "the top-tier we could buy".
- Auto-renewal clause and notice-to-cancel period.
- Overage terms and billing predictability.
- Indemnity and IP-warranty posture (especially relevant for code-generation tools where output-IP questions are live).

**Section C — Security posture**

- [SOC 2](https://www.aicpa-cima.com/topic/audit-assurance/audit-and-assurance-greater-than-soc-2) Type II report: scope, audit firm, report period, opinion (unqualified / qualified).
- [ISO/IEC 27001](https://www.iso.org/standard/27001) certification if held; scope and certificate number.
- [ISO/IEC 42001:2023](https://www.iso.org/standard/81230.html) AI management system certification if held. This is the newer, AI-specific standard; vendors increasingly reference it in trust centres.
- Vulnerability disclosure contact and SLA.
- Incident notification SLA to the customer (for data incidents on the vendor side).
- Vendor questionnaire response: [CSA CAIQ](https://cloudsecurityalliance.org/research/cloud-controls-matrix/) or [Shared Assessments SIG / SIG-Lite](https://sharedassessments.org/sig/). The organisation's SecOps typically runs one of these; the manager files the response.
- Pen-test summary or cert if the vendor shares one (many publish pen-test letters in the trust centre).

**Section D — Data handling clauses**

- **Training-on-your-data** clause — exactly as worded in the DPA / TOS for the contracted tier. For enterprise-tier contracts, this is usually "we do not train our foundation models on customer inputs or outputs"; verify text and tier. Public references of vendor positions include the [GitHub Copilot Trust Center](https://resources.github.com/copilot-trust-center/), [Anthropic Trust Center](https://trust.anthropic.com/), [OpenAI Enterprise privacy page](https://openai.com/enterprise-privacy/), [Cursor security page](https://cursor.com/security), [Microsoft Copilot data protection page](https://learn.microsoft.com/en-us/copilot/microsoft-365/microsoft-365-copilot-privacy). Each publishes *per tier* — capture the clause for the tier the team actually uses.
- **Retention** — how long are inputs and outputs retained; configurable; the team's current configuration.
- **Residency** — physical data location(s); subprocessor locations; cross-border transfer paths.
- **Access and audit** — vendor-side access controls; customer audit rights; audit logs available to the customer.
- **Deletion** — process for requesting deletion; vendor verification; backup / log retention after deletion.
- **Model-provenance** — for model-based services, which foundation models the service uses; whether this is disclosed; whether the model-selection can change silently (and if so, what notice the vendor provides). Model-provenance is the AI-specific clause that most procurement templates were not written for; mod-111 adds it explicitly.

**Section E — Operational integration**

- How the team authenticates: SSO / SAML / OIDC; MFA; SCIM provisioning; service account posture.
- Audit log retention and availability (for the team's own audit of IC usage, not the vendor-side audit).
- Subprocessors added without notice (yes / no; cadence).
- Change-management SLA — does the vendor notify the customer of material changes to data handling, model routing, or defaults?

**Section F — Exit plan**

- Decommissioning path — how to disable access, revoke credentials, delete customer data, retrieve customer-owned artifacts.
- Data-export format and retention window for exports.
- Switch-cost estimate — engineer-weeks to transition workflows to an alternative; data stranded in the vendor's pipelines; retraining cost for ICs.
- Dependency map — which internal systems rely on this vendor; which workflows break if the vendor is unavailable.

**Section G — Sign-offs**

- Procurement sign-off: who, date.
- SecOps sign-off: who, date.
- Legal / privacy sign-off: who, date.
- Manager sign-off: who, date.
- Any open conditions or caveats on sign-off.

### DPA specifics in the AI-vendor context

A few AI-vendor-specific DPA points that earlier procurement templates often missed:

- **Scope of "processing" includes model inference.** The DPA should treat model-inference on customer inputs as *processing* under [GDPR Article 28](https://gdpr-info.eu/art-28-gdpr/), with the vendor as processor. Confirm the DPA language treats it this way; older DPA templates sometimes left inference in an undefined category.
- **Training is a separate processing purpose.** If the vendor uses customer data for foundation-model training (consumer tier typically yes, enterprise typically no), that is a *separate purpose* requiring a separate lawful basis under GDPR. Enterprise-tier contracts usually exclude training; read the specific clause for the tier contracted.
- **Subprocessor change notice.** AI vendors often have long subprocessor lists (CDN, model-hosting provider, observability vendor, infra provider). GDPR requires change notice; the DPA should name the current list and the change-notice mechanism. Vendors frequently publish a subprocessor page (e.g., [OpenAI subprocessors](https://openai.com/policies/data-processing-addendum/), [Anthropic subprocessors](https://trust.anthropic.com/)).
- **Automated decision-making article (GDPR Article 22).** If the vendor's service makes automated decisions with legal or similarly significant effect on data subjects, Article 22 is engaged. Most AI coding assistants are not Article 22 territory (they advise humans, not decide for them), but review workflows that touch employment or customer eligibility can be — check with legal.
- **Cross-border transfer mechanism.** US-hosted AI vendors serving EU customers require SCCs plus a transfer impact assessment post-*Schrems II*, or reliance on the [EU–US Data Privacy Framework](https://commerce.gov/tags/eu-us-data-privacy-framework) adequacy decision where the vendor is certified. Legal owns the position; the manager captures the mechanism named in the vendor's DPA.

### SOC 2 specifics in the AI-vendor context

[SOC 2](https://www.aicpa-cima.com/topic/audit-assurance/audit-and-assurance-greater-than-soc-2) is an AICPA framework reporting on trust-services criteria (Security, Availability, Processing Integrity, Confidentiality, Privacy). AI-vendor-specific points:

- **Type II is what you want.** SOC 2 Type I is a point-in-time; Type II covers an operating period (usually 6–12 months). Treat Type II as the serious artifact; Type I is a weak signal.
- **Scope of the report matters.** The SOC 2 is scoped to specific services; a vendor with a SOC 2 covering "the hosting platform" may not have that report cover the AI service on top of it. Confirm the scope lists the service the team uses.
- **Opinion qualification matters.** An *unqualified* opinion is clean; a *qualified* opinion names exceptions the vendor had and are a conversation. SecOps reads the opinion letter; the manager files the result.
- **Observation period vs report date.** The audit covers a window ending on a date; the report is issued some weeks later. A SOC 2 whose observation period ended 18 months ago is a stale artifact.
- **The newer AI-specific framework.** [ISO/IEC 42001:2023](https://www.iso.org/standard/81230.html) is the AI-management-system standard; vendors beginning to certify to it will add "ISO 42001" to their trust centres. It is not a substitute for SOC 2 but complements it for AI-specific governance.

### Model-provenance clauses — the newer discipline

Model provenance is the AI-specific clause family earlier procurement did not have templates for. Three questions:

- **Which foundation models does the service use?** Vendors who are also model providers (OpenAI, Anthropic, Google, Microsoft) use their own; vendors who are services on top (Cursor, Windsurf, Cody) route to one or more model providers under the hood. The *routing* can change silently.
- **How is the team notified of model changes?** Vendors sometimes change defaults (the model behind a product name changes, the context length changes, the system prompt changes) outside the team's deploy cycle. The clause the team wants: *material changes to model routing or defaults are notified in advance*. Vendors increasingly include this in enterprise agreements; earlier contracts often omitted it.
- **What model-level evidence is available?** Does the vendor publish model cards ([Hugging Face model cards](https://huggingface.co/docs/hub/model-cards), per [Mitchell et al. 2019](https://arxiv.org/abs/1810.03993)) or system cards for the models in the service? Anthropic's and OpenAI's own foundation-model system cards are published at launch and update; Cursor / Windsurf / Cody do not publish model cards because they do not train models, but they can point at the upstream cards for the models they route.

The model-provenance clause composes with [`mod-110` Chapter 6](../mod-110-ai-governance-and-policy-at-team-scope/06-data-ip-and-confidentiality-practice.md)'s model-card discipline — the team's own model-card record references the upstream vendor's.

### The exit plan discipline

Every entry on the Chapter 7 registry has an exit plan. Three components:

- **Decommissioning steps** — a dated, specific list: revoke credentials, disable SSO application, pull data exports, delete customer data per the vendor's deletion process, retain or shred local caches, update [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) tool-authorisation policy.
- **Data-retrieval commitment** — the vendor's commitment on data export (format, retention window, API for export).
- **Switch-cost estimate** — engineer-weeks to transition; stranded-data risk; retraining cost for ICs; dependent systems that need adjustment.

The exit plan is what makes "sunset a tool" a decision the team can actually make. A tool whose exit plan is empty is an asymmetric commitment; the registry marks that explicitly.

### What this chapter deliberately does *not* do

- **Does not re-run SecOps assessments.** The CAIQ or SIG response, the pen-test review, the vulnerability-management review are SecOps' work. The manager files the output.
- **Does not interpret DPAs legally.** Legal / privacy office reads the clause; the manager captures what legal says. Where the manager has an opinion, it is a *flag* to legal, not an interpretation.
- **Does not architect enterprise contracts.** Procurement and [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) do.
- **Does not replace the [`mod-110` Chapter 6](../mod-110-ai-governance-and-policy-at-team-scope/06-data-ip-and-confidentiality-practice.md) data-handling policy.** This chapter *supplies the clauses* the data-handling policy *operates*. The two compose.

## Example: a due-diligence record for one vendor

A composite shaped example — calibration, not a case study.

> **Vendor.** Anthropic. **Service / tier.** Claude for Work (Enterprise).
>
> **A. Identification.**
> - Vendor legal entity: Anthropic PBC (US).
> - Service: Claude for Work, Enterprise plan.
> - Hosting: US primary, EU option contracted.
> - Subprocessors: cloud provider (listed in trust centre); monitoring vendor.
> - Date of record: 2026-11-04. Next review: 2027-02-04.
>
> **B. Contractual.**
> - MSA in force, v2026.03, signed 2026-04-02 by procurement.
> - DPA in force, v2026.03, signed same day.
> - Cross-border mechanism: SCCs with transfer impact assessment on file at legal.
> - Commercial tier: Enterprise plan (contracted; not Business or Pro).
> - Auto-renewal: yes, annual; notice: 60 days.
> - Overage terms: committed-use with metered overage.
> - Indemnity / IP warranty: per MSA (legal filed).
>
> **C. Security.**
> - SOC 2 Type II: scope covers Claude for Work service; auditor [firm]; report dated [date]; opinion unqualified.
> - ISO/IEC 27001: certified; certificate number on file.
> - ISO/IEC 42001: pending as of record date (vendor publicly committed).
> - Vulnerability disclosure contact: security@anthropic.com; SLA per trust centre.
> - Incident notification SLA: 72h for material incidents per DPA.
> - CAIQ response filed by SecOps on 2026-05-11.
>
> **D. Data handling.**
> - Training on customer data: contractually excluded for the Enterprise tier per DPA § [N]. Verified.
> - Retention: zero retention configurable; team configured 0 days. Verification: control panel screenshot on file.
> - Residency: US primary; the team has not opted into EU residency because no team workflows require it.
> - Access and audit: vendor access controls per DPA; customer audit rights per DPA § [N]; audit logs available via console.
> - Deletion: per DPA § [N]; verified process.
> - Model-provenance: service uses Anthropic's Claude family; model changes announced in advance per enterprise agreement. Vendor's [system cards](https://assets.anthropic.com/) referenced per [`mod-110` Chapter 6](../mod-110-ai-governance-and-policy-at-team-scope/06-data-ip-and-confidentiality-practice.md) model-card record.
>
> **E. Operational.**
> - Authentication: SSO via SAML; MFA required; SCIM provisioning enabled.
> - Audit-log retention: per vendor + exported weekly to internal SIEM.
> - Subprocessor change notice: 30 days per DPA.
> - Material-change SLA: contracted; mechanism confirmed in trust centre.
>
> **F. Exit plan.**
> - Decommissioning: disable SSO, pull audit logs, submit deletion request via DPA mechanism, update [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) tool-authorisation policy.
> - Data-retrieval: export via console; 30-day retention window post-deletion for export.
> - Switch-cost estimate: ~3 engineer-weeks to transition active workflows; ~2 ICs need retraining on an alternative Tier 3 agent; low stranded-data risk due to zero-retention.
> - Dependencies: 2 internal MCP servers (team-owned, portable to alternative Tier 3 agents).
>
> **G. Sign-offs.**
> - Procurement: [name], 2026-04-02.
> - SecOps: [name], 2026-05-14.
> - Legal / privacy: [name], 2026-04-30.
> - Manager: [name], 2026-05-20.
> - Open conditions: ISO 42001 certification tracked; re-review when issued.

One vendor, one dated record, three sign-offs, an exit plan. Exercise 04 produces this for every tool in the registry.

## Summary

- Due-diligence is a **three-partner** pattern: procurement, SecOps, legal. The manager is the integrator — filling questionnaires, routing questions, filing the composed record.
- The due-diligence record has **seven sections**: identification, contractual posture, security posture, data-handling clauses, operational integration, exit plan, sign-offs. Exercise 04 fills it per vendor.
- **Tier matters.** The DPA / SOC 2 / data-handling posture of a service's enterprise tier is *not* the same as its business or consumer tier. Capture the tier the team actually uses.
- **DPA specifics in the AI-vendor context**: inference as processing, training as a separate purpose, subprocessor change notice, Article 22 if applicable, cross-border transfer mechanism.
- **SOC 2 specifics**: Type II over Type I; scope covers the actual service; opinion qualification; observation-period freshness; [ISO/IEC 42001:2023](https://www.iso.org/standard/81230.html) as the newer AI-specific complement.
- **Model-provenance** is the AI-specific clause family earlier contracts missed. The clauses: which models, change notice, model-card evidence. Composes with [`mod-110` Chapter 6](../mod-110-ai-governance-and-policy-at-team-scope/06-data-ip-and-confidentiality-practice.md)'s model-card record.
- **Exit plan** is first-class: decommissioning steps, data-retrieval commitment, switch-cost estimate. Makes sunset a decision the team can actually make.
- **Does not** re-run SecOps assessments, interpret DPAs legally, architect enterprise contracts, or replace the operational data-handling policy. Supplies evidence the composed registry needs.
- Exercise 04 produces the filled checklist per vendor; Exercise 05 produces the per-vendor clause reader composed with [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/).
