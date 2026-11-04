# Chapter 4 — Articles 14 and 50: Human Oversight and Transparency at Team Scope

> *A workflow that is high-risk under the AI Act does not become high-risk at team altitude — it is classified upstream by counsel. The manager's work is to run the specific oversight and transparency practices the Act names, in the shape the rest of the team's stack already has, so the classification lands cleanly in operation.*

## Motivation

[EU AI Act Article 14](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) obliges providers of high-risk AI systems to design them for *effective human oversight*, and obliges deployers of high-risk systems to assign the oversight task *"to natural persons who have the necessary competence, training, and authority, as well as the necessary support."* [Article 26](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) extends related deployer obligations. [Article 50](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) sets transparency obligations around AI systems that interact with natural persons, generate synthetic content, perform emotion recognition or biometric categorisation, or produce deep-fakes — some obligations fall on providers, some on deployers.

Both Articles map to *specific team-scope practices* when the team's workflows touch regulated contexts. The manager does not decide whether the workflow is high-risk, whether it is a "limited-risk" interaction under Article 50, or whether an Article 50 exemption applies — those are legal-position questions for counsel. The manager *operates* the practice counsel has set and *flags* workflows that may have drifted out of the classification.

This chapter does three things. First, it reads Article 14 and Article 50 as published, with the deployer-side obligations highlighted. Second, it names the team-scope practices that discharge the obligations and the composition with [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) (HITL design) and [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) (incident flagging). Third, it names the triggers that route specific workflow questions to counsel.

> **Non-lawyer disclaimer.** As with Chapter 3, this is curriculum, not legal advice. Your organisation's counsel sets the classification and interpretation. The practices below are the operational shape team-scope evidence takes once counsel has set the position.

## Core concepts

### Article 14 — the deployer's reading

Article 14 is written primarily for *providers* of high-risk AI systems, with obligations on deployers that attach to running them. The deployer-side obligations include:

- Assigning oversight to *natural persons* (not an automated check; a named human role).
- Those persons must have *competence, training, and authority* — which binds Article 14 compliance to Article 4 literacy training.
- Those persons must have the *necessary support* — organisational backing, time, information, tooling, and, where relevant, access to the risk-engineering and security specialists.

Article 14 also enumerates the *oversight measures* the system must enable: the ability to understand the system's capacities and limitations, to monitor operation and detect anomalies, to remain aware of over-reliance (*"automation bias"*), to correctly interpret outputs, and to decide, in any situation, not to use the system or to override its output. These are *system-design* obligations on providers; the deployer operates them through the team's workflow design.

For the team manager at team scope, the operational translation is:

1. **Named oversight role.** The workflow has a specific named role responsible for oversight at specific decision points. "The reviewer" from [`mod-103` Ch. 5](../mod-103-review-standards-and-eval-commissioning/05-the-accountability-contract-ai-generates-humans-own.md) is usually that role; the workflow documentation cites the role with authority and escalation path.
2. **Competence and training.** The oversight role is tiered at reviewer-level or manager-level in the Article 4 program (Chapter 3). The LMS record evidences competence for the named person.
3. **Authority to override.** The role has a *documented authority* to not use the system or to override its output. The team's HITL checkpoint design from [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) names the override mechanism.
4. **Support.** The role has access to the engineering support needed to understand the output, including the ability to inspect the trace. The mod-109 trace-preservation practice is the support artifact.
5. **Automation-bias mitigation.** The team's practice counters over-reliance explicitly — through the review checklist, the standards-as-code stack, and the fluency training in Module D of the Chapter 3 curriculum.

The manager documents each of the five against the specific workflow and produces an **Article 14 workflow sheet** (defined below).

### Article 14 does not auto-apply to every workflow

Article 14 attaches to AI systems the Act classifies as high-risk. High-risk classification is defined in Articles 6 and 7 and Annex III of the Act: specific use cases such as employment-and-worker-management screening, education access and grading, essential private- and public-service eligibility, law enforcement, migration and border control, administration of justice, and critical infrastructure. Determining whether a specific team workflow falls inside Annex III is a legal question; counsel decides. The manager flags.

Many engineering teams will find *their own workflows are not high-risk* — internal productivity use of AI coding assistants on non-regulated code is typically outside Annex III. The manager's obligation in that case is not to run an Article 14 practice; it is to be able to produce evidence that the classification was considered and to flag any drift. The upward packet in Chapter 7 contains that evidence.

Teams operating workflows that sit *adjacent* to a high-risk system (producing outputs a downstream team's high-risk system consumes; routing decisions that feed a high-risk classification) often inherit practice from the downstream system's compliance envelope. Counsel decides; the manager runs the practice counsel sets.

### Article 50 — the transparency obligations

Article 50 is a separate obligation structure focused on *transparency to affected persons*. It applies more broadly than Article 14 — not only to high-risk systems — and splits obligations between providers and deployers:

- **Interaction with natural persons (Article 50(1))** — providers of AI systems intended to interact directly with natural persons must design them so that the person is informed they are interacting with AI, unless the context makes it obvious or specific exemptions apply.
- **AI-generated or manipulated content (Article 50(2))** — providers of generative AI must mark outputs as artificially generated or manipulated, in a machine-readable format, with technical feasibility caveats.
- **Emotion recognition and biometric categorisation (Article 50(3))** — deployers must inform natural persons of operation of such systems.
- **Deep-fakes (Article 50(4))** — deployers must disclose that image, audio, or video content is artificially generated or manipulated.
- **Text published to inform the public on matters of public interest (Article 50(4))** — deployers must disclose that text is artificially generated or manipulated, with certain exemptions (e.g., human-reviewed editorial content).

For team-scope operational practice, the two most commonly live obligations for a deployer are Article 50(3) and Article 50(4). If the team's AI touches either, the workflow has a transparency step with specific wording counsel approves.

Article 50 also has exemption pathways (e.g., law enforcement under conditions, obvious contexts). Whether an exemption applies is a legal-position question. Counsel decides.

### The Article 14 workflow sheet

For any workflow counsel has classified as high-risk or adjacent, the team's documentation includes an **Article 14 workflow sheet**. One sheet per workflow, one page. Fields:

1. **Workflow name and counsel classification.** The workflow's identifier (link to the mod-106 routing-matrix entry), the legal classification (high-risk per Annex III category X; adjacent; limited-risk), and the sign-off date from counsel.
2. **Named oversight role.** The specific role (not person) accountable for oversight, plus the current named person(s), with LMS curriculum link.
3. **Decision points.** The specific points in the workflow where oversight is exercised. For each: what is being oversighted, what information the overseer sees, what decisions they can take, and the time budget.
4. **Override mechanism.** How the overseer declines or overrides an AI output, documented and tested. Reference the mod-106 delegation ladder and tool-authorisation policy.
5. **Automation-bias mitigation.** The specific practices (review checklist items, standards-as-code enforcements, training modules) that counter over-reliance on this workflow.
6. **Trace preservation.** Reference to the mod-109 trace-preservation checklist as it applies.
7. **Escalation path.** Who the overseer calls when the decision is beyond their authority, with reference to the mod-109 routing contract.
8. **Change log.** Date of last review; date of next review; what changed.

The sheet is the single artifact the audit asks for when Article 14 comes up. If a workflow does not have a sheet and should, that is a gap routed upward in the Chapter 7 packet.

### The Article 50 interaction sheet

For workflows subject to Article 50(3), 50(4), or 50(1) deployer-side disclosures (where the deployer is responsible for passing through the provider's disclosure), the team's documentation includes an **Article 50 interaction sheet**. Fields:

1. **Workflow name and the Article 50 subparagraph that applies.** With counsel's sign-off.
2. **The disclosure text.** Exact wording, approved by counsel.
3. **Where the disclosure appears.** Specific UI, document, or communication, with screenshot or link.
4. **Verification.** How the team confirms the disclosure is present on every output. Automated check, periodic sampling, or process gate.
5. **Exemption basis, if any.** Counsel-approved rationale if an exemption applies.
6. **Change log.** As for the Article 14 sheet.

### Composition with the rest of the track

The two sheets are composed artifacts, not new work for the team.

- **The named oversight role** inherits from the [`mod-103` Ch. 5](../mod-103-review-standards-and-eval-commissioning/05-the-accountability-contract-ai-generates-humans-own.md) accountability contract.
- **The decision points** inherit from the [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) HITL checkpoint design and the delegation ladder.
- **The override mechanism** inherits from the mod-106 tool-authorisation policy and the mod-103 review-checklist stop criteria.
- **The automation-bias mitigation** inherits from the mod-103 review checklist, the mod-105 AI-literacy training (Chapter 3 here), and the [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/) anti-atrophy practice.
- **The trace preservation** inherits from the mod-109 trace-preservation checklist.
- **The escalation path** inherits from the mod-109 routing contract.

The sheet is a *mapping* of existing artifacts to Article 14 language. If any field cannot be filled from existing artifacts, that is a gap in the team's stack and the exercise flags it.

### The triggers for routing to counsel

The manager routes a workflow question to counsel when:

- A new workflow enters the team's roadmap that is **plausibly within Annex III** — any workflow touching employment, education, credit decisions, essential-service access, law enforcement, border control, justice, or critical infrastructure. The default is "flag and ask"; counsel's "no, this is not high-risk" is the artifact that lets the workflow proceed without Article 14 practice.
- A workflow **changes** in a way that could change its classification — new data sources, new decision authority delegated to the AI, new population of affected persons, expansion from pilot to production.
- A **vendor change** could affect the classification — a model swap, a new provider in the chain, a change to a vendor's own disclosure.
- The team receives a request from an **affected person** that implicates Article 50 (e.g., "is this generated by AI?"). Counsel decides the response.
- Any **regulator-facing communication** or request. The manager does not respond to regulators directly; counsel does.

The trigger list is one page in the team's governance pack; Exercise 01 produces it as part of the GOVERN 1.4 row.

### GPAI deployer practice — brief note

The Act and the [AI Office General-Purpose AI Code of Practice](https://digital-strategy.ec.europa.eu/en/policies/ai-code-practice) place most obligations on providers of general-purpose AI models. Deployers consume. The main deployer-side practice touching GPAI at team scope is:

- Preferring GPAI providers who have signed the Code of Practice and who publish systemic-risk assessments where applicable (a vendor-choice input — see [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/)).
- Tracking model-card and system-card information from the provider as part of the team's data/IP policy (Chapter 6).
- Flagging to counsel any workflow where the team's use of a GPAI model could place the organisation in a provider role (e.g., fine-tuning that creates a materially new system placed on the market).

## Example: an underwriting-assist workflow

Composite — calibration, not case study.

The financial-services team from Chapter 1 operates an *underwriting-assist* workflow where an AI agent drafts preliminary assessments that an underwriter reviews, modifies, and submits for a credit decision. Counsel's classification: *adjacent to high-risk under Annex III category 5(b) — AI systems used to evaluate the creditworthiness of natural persons*. Counsel's position: the workflow inherits Article 14 practice from the firm's high-risk envelope because the AI output materially influences the final decision, even though the final decision is made by the underwriter.

The Article 14 workflow sheet, filled:

- **Workflow:** Underwriting-assist v3.2 (routing matrix entry link). Classification: adjacent-high-risk, counsel sign-off 2026-07-02.
- **Oversight role:** Underwriter-reviewer. Named persons: U. Patel, J. Han, M. Okafor. LMS curriculum: `#AI-FLUENCY-UNDRW-REV-V2` (manager-tier content plus a module-specific credit-decision addendum).
- **Decision points:** (a) initial draft generation — reviewer verifies all variables used; (b) risk-flag emission — reviewer may add, remove, or recategorise flags; (c) final submission — reviewer signs with explicit "I am accountable" prompt.
- **Override mechanism:** The reviewer's submit button is distinct from the draft button; the system cannot submit without reviewer sign-off; delegation ladder excludes auto-submission.
- **Automation-bias mitigation:** Review checklist has an explicit "cross-check the top-weighted variable against source" item; standards-as-code enforces per-variable source citation; Module G of the Article 4 curriculum covers the automation-bias-in-credit-decisions literature.
- **Trace preservation:** Prompt chain, retrieved context (applicant file, external data sources), model + version, reviewer actions all logged to the compliance-grade trace store; 7-year retention per credit-decision records policy.
- **Escalation path:** Tier 1 — underwriting-team lead; Tier 2 — risk-and-governance partner; Tier 3 — counsel (for applicant-facing disputes).
- **Last review:** 2026-10-12. Next review: 2027-01-12.

The Article 50 interaction sheet: not applicable here; the workflow is internal-facing. If the applicant received an AI-generated communication, Article 50(1) would attach and a separate sheet would be required.

## Summary

- [Article 14](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) obliges deployers of high-risk AI systems to assign oversight to natural persons with competence, training, authority, and support. [Article 26](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) extends related obligations.
- [Article 50](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) sets transparency obligations around AI interactions, generated content, emotion recognition, biometric categorisation, deep-fakes, and public-interest text. Some fall on providers; some on deployers.
- Whether a specific workflow is high-risk, adjacent, or limited-risk is a **legal-position question** counsel decides. The manager flags and routes.
- For in-scope workflows the manager maintains two one-page artifacts: the **Article 14 workflow sheet** (role, decision points, override, automation-bias mitigation, trace, escalation, change-log) and the **Article 50 interaction sheet** (disclosure text, placement, verification, exemption, change-log).
- The sheets **compose existing artifacts**, not new work: oversight role from [`mod-103` Ch. 5](../mod-103-review-standards-and-eval-commissioning/05-the-accountability-contract-ai-generates-humans-own.md); decision points from [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/); automation-bias mitigation from the review checklist, Chapter 3 literacy, and [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/); trace from [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/).
- A one-page **trigger list** routes workflow questions to counsel: new Annex-III-adjacent workflows, classification-changing modifications, vendor changes, affected-person requests, regulator-facing communication.
- The Article 14 and Article 50 practice inherits from the firm's GPAI procurement decisions — see [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) and Chapter 6 here for the data/IP end.
- The two sheets feed the Chapter 7 upward packet as the Article 14 and Article 50 evidence sections.
