# Chapter 5 — Microsoft Responsible AI Standard and Google AI Principles, Mapped to Team Practice

> *An audit that only reads NIST and EU AI Act is one audit. A market-facing responsible-AI commitment often cites Microsoft's standard or Google's principles. The team manager's job is defensive: show, against the frameworks the organisation has already publicly committed to, that team practice supports the commitment.*

## Motivation

Two industry frameworks dominate the public responsible-AI literature and show up most often in organisations' external commitments:

- **[Microsoft Responsible AI Standard v2](https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-Responsible-AI-Standard-v2-General-Requirements-3.pdf)** — published June 2022 as Microsoft's internal standard for building AI systems, organised around six *AI principles* (fairness, reliability and safety, privacy and security, inclusiveness, transparency, accountability) and translated into *goals* with specific requirements. Referenced heavily in public commitments by organisations that build on Azure OpenAI and in responsible-AI vendor relationships.
- **[Google AI Principles](https://ai.google/responsibility/principles/)** — Google's seven AI principles, first published in 2018 and updated periodically, are the most commonly cited industry responsible-AI principle set after Microsoft's. They state what AI applications Google will pursue, won't pursue, and require review for. Referenced heavily by organisations consuming Google / Vertex AI products.

For a team manager at a level-40 role, neither framework is the primary compliance driver — NIST AI RMF and the EU AI Act are. But a team whose organisation has publicly committed to either (or both) frameworks has an **operational obligation to support the commitment**. The audit that reads NIST and the AI Act is the regulator audit; the audit that reads Microsoft RAI or Google AI Principles is often the enterprise customer's security questionnaire, the partner-facing responsible-AI commitment, or the internal review of the organisation's own public statements.

This chapter does three things. First, it names the two frameworks as published and the principles / goals each enumerates. Second, it maps each principle onto team-scope evidence the manager already produces (or should) in other mod-10x chapters. Third, it names the *defensive* framing: the manager does not restructure team practice around industry frameworks, but can map team practice to them on demand.

## Core concepts

### Microsoft Responsible AI Standard v2 — the structure

The Standard is organised around six principles, with *goals* under each. The current public version enumerates (paraphrased from the Standard; refer to the published PDF for the authoritative wording):

- **Accountability** — goals include impact assessment, oversight of significant adverse impacts, fit for purpose, data governance and management, human oversight and control.
- **Transparency** — goals include system intelligibility for decision-making, communication to stakeholders, disclosure of AI interaction.
- **Fairness** — goals include quality of service, allocation of resources and opportunities, minimisation of stereotyping, demeaning, and erasing outputs.
- **Reliability and safety** — goals include reliability and safety guidance, failure management, ongoing monitoring, feedback, and evaluation.
- **Privacy and security** — goals include privacy standard, Microsoft security policy.
- **Inclusiveness** — goals include human-AI interaction guidelines applied across accessibility and assistive-technology considerations.

Each goal names specific *requirements* — what must be done to meet the goal — and in Microsoft's internal use is traced to a release-gate for the product in question.

For the team-scope manager, the three principles most directly operational are **Accountability**, **Transparency**, and **Reliability and safety**. Fairness, Privacy and security, and Inclusiveness are more frequently architectural or policy-level; the manager's team practice contributes evidence, not primary ownership.

### Google AI Principles — the structure

Google publishes seven AI principles and an accompanying statement of applications they will not pursue. The principles (paraphrased; refer to the published page for the current authoritative wording):

1. Be socially beneficial.
2. Avoid creating or reinforcing unfair bias.
3. Be built and tested for safety.
4. Be accountable to people.
5. Incorporate privacy design principles.
6. Uphold high standards of scientific excellence.
7. Be made available for uses that accord with these principles.

Google updates the principles periodically. Alongside the principles, Google publishes *Responsible AI Progress Reports* documenting the operational application. For deployers of Google / Vertex AI products, the principles are the public-facing commitment the team's practice supports indirectly.

For the team-scope manager, principles **2 (unfair bias)**, **3 (safety)**, **4 (accountability)**, and **5 (privacy)** have the most direct team-scope operational mapping. Principles 1, 6, and 7 are strategic / organisational commitments the manager contributes to but does not own.

### The defensive-mapping discipline

The temptation with industry frameworks is to *restructure the team's practice* around their language. This is almost always a mistake at team altitude:

- The organisation's primary regulatory drivers are NIST RMF and the EU AI Act (plus sector-specific statutes). Reshaping the team around Microsoft RAI language competes with that hierarchy.
- Industry frameworks evolve — Google updated its principles repeatedly; Microsoft's Standard was revised from v1 to v2. Practice tied tightly to a specific version depreciates.
- The practice the organisation *actually* needs — the NIST crosswalk, the Article 4 program, the mod-103 review stack, the mod-109 incident response — is the substrate. Industry-framework mapping is a view, not a rewrite.

The defensive discipline: the manager maintains a **framework-mapping table** that shows, for each Microsoft RAI principle and each Google principle, which team-scope artifact provides the operational evidence. The table is updated when the framework updates. The team's practice does not change to fit the table; the table changes to point at the practice.

### The Microsoft RAI mapping

A workable mapping, one row per principle. The "team-scope evidence" column points at the artifact the manager produces elsewhere in the track.

| Microsoft RAI principle | Primary team-scope evidence | Composing artifacts | Gaps the manager routes upward |
|---|---|---|---|
| **Accountability** | [`mod-103` Ch. 5](../mod-103-review-standards-and-eval-commissioning/05-the-accountability-contract-ai-generates-humans-own.md) accountability contract; Chapter 2 crosswalk GOVERN 2.1 row | [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) retrospective artifacts; Chapter 4 Article 14 sheets | Organisation-wide impact-assessment library |
| **Transparency** | Chapter 4 Article 50 sheets; [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) AGENTS.md disclosure | [`mod-105`](../mod-105-team-ai-enablement-programs/) + Chapter 3 Article 4 literacy records (team-internal transparency) | Program-level customer disclosure language |
| **Fairness** | Review checklist items for fairness ([`mod-103` Ch. 2](../mod-103-review-standards-and-eval-commissioning/)); eval commissioning that includes fairness tests ([`mod-103` Ch. 4](../mod-103-review-standards-and-eval-commissioning/)); [`mod-108` Ch. 6](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/06-ai-in-hiring-legal-and-compliance-framing.md) EEOC / NYC LL144 framing | `ai-risk-engineer` engineered fairness evaluation | Program-level fairness policy and systemic bias assessment |
| **Reliability and safety** | [`mod-103` Ch. 4](../mod-103-review-standards-and-eval-commissioning/) eval commissioning; [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) incident response | Standards-as-code stack from [`mod-103` Ch. 3](../mod-103-review-standards-and-eval-commissioning/) | Program-level safety thresholds and acceptance criteria |
| **Privacy and security** | Chapter 6 data-handling policy; [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) tool-authorisation policy | [`mod-109` Ch. 5](../mod-109-accountability-incident-response-and-blameless-postmortems/05-routing-contract-with-risk-engineer-and-secops.md) SecOps routing | Program-level DPIAs and privacy policy |
| **Inclusiveness** | Accessibility considerations in the team's applied workflows (role-dependent); Module G of the Chapter 3 Article 4 curriculum | [`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/) workforce considerations | Program-level inclusiveness commitments |

The pattern across the six: the team's practice composes with artifacts already produced in the track. Where a cell routes upward as a gap, the manager documents it rather than attempting to author it alone.

### The Google AI Principles mapping

| Google principle | Primary team-scope evidence | Composing artifacts | Gaps the manager routes upward |
|---|---|---|---|
| **Be socially beneficial** | Use-case register with purpose statements (Chapter 7) | [`mod-102`](../mod-102-team-ai-adoption-and-roadmap/) roadmap rationale | Program / executive statement of organisational mission |
| **Avoid unfair bias** | Review checklist and eval commissioning as for MS RAI Fairness | `ai-risk-engineer` fairness evaluation | Same as MS RAI Fairness |
| **Built and tested for safety** | Eval commissioning; incident response; [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) delegation ladder | Standards-as-code stack | Program-level safety commitments |
| **Accountable to people** | Accountability contract; Article 14 sheets | Chapter 3 Article 4 training records; [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) retrospective | Executive-level public accountability commitments |
| **Privacy design principles** | Chapter 6 data-handling policy; tool-authorisation policy | Vendor data-use evidence from [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) | DPIAs, formal privacy design reviews |
| **Scientific excellence** | Eval commissioning quality; peer learning via [`mod-105`](../mod-105-team-ai-enablement-programs/) CoP | n/a | Program-level R&D / research commitments |
| **Available only for accordant uses** | Use-case register with sign-off; tool-authorisation policy; vendor use-restriction compliance from [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) | n/a | Program-level go/no-go on AI use cases |

The gaps are consistent: where an industry principle lives at program altitude, the team-scope cell routes upward.

### Composing the two mappings

The team's framework-mapping artifact has two tables — one for Microsoft RAI, one for Google. Where the organisation has publicly committed to only one framework, only that mapping is maintained; where to both, both. Where the organisation has committed to neither but to a bespoke responsible-AI commitment (increasingly common), the manager produces a third mapping against the organisation's own principle list, using the same shape.

The mapping artifact is one-to-two pages per framework. It is **not re-authored** every quarter; it is **re-pointed** when any of (a) the framework updates, (b) a team-scope artifact changes, (c) a new team workflow enters scope.

### What this chapter deliberately does not do

- It does not take a position on the frameworks' adequacy. The frameworks are inputs; the manager does not endorse or critique them.
- It does not try to map team practice to every public responsible-AI framework in circulation (OECD, UNESCO, Partnership on AI, UN, individual country frameworks). The two in this chapter are the most commonly referenced in enterprise responsible-AI commitments; other frameworks are mapped on demand against the same table shape.
- It does not substitute for the NIST crosswalk or the Article 4 / 14 / 50 practice. Those are the primary compliance substrates. The industry-framework mappings are views over the same artifacts.

### What the audit actually reads

When a customer, partner, or internal auditor asks "show us how your team's AI practice supports [the public RAI commitment]", the manager:

1. Opens the framework-mapping table.
2. For each row, points at the team-scope artifact.
3. For each gap, points at the upward routing note (which named stakeholder owns the gap).

The audit does not expect the team to run Microsoft's internal processes or Google's internal processes. It expects the organisation to be able to connect the public commitment to real practice *somewhere*. The team-scope mapping is what lets the organisation make that connection at the team layer.

## Example: a partner security questionnaire

Composite — calibration, not case study.

The financial-services team's firm has signed a contract with an enterprise customer. The customer's security team issues a 70-page questionnaire. Section 8 — *Responsible AI* — asks:

- "Describe how AI systems used in connection with the services support Microsoft Responsible AI Standard principles."
- "Describe how human oversight is operationalised."
- "Describe fairness testing and ongoing monitoring."
- "Describe staff training on AI responsible-use."

The manager receives the three questions from the customer's firm's responsible-AI-lead and responds, pulling from the mapping artifact:

- **Human oversight** → Chapter 4 Article 14 workflow sheet for the underwriting-assist workflow (and n equivalent sheets for the other in-scope workflows).
- **Fairness testing and monitoring** → eval-commissioning records with fairness tests, commissioned from `ai-risk-engineer`; the quarterly review cadence on fairness-metric drift from [`mod-103` Ch. 4](../mod-103-review-standards-and-eval-commissioning/).
- **Staff training** → the Chapter 3 Article 4 training record with per-person completion and the segmentation rationale.
- **MS RAI principle mapping** → the one-page MS RAI mapping artifact.

The response is 2–3 pages. Every answer points at a real artifact. The customer accepts and moves on. The firm's responsible-AI lead files the response in the enterprise sales support library; it feeds every subsequent customer response. The team's mapping artifact is now a reusable asset at program altitude.

## Summary

- Two frameworks dominate industry responsible-AI commitments: **[Microsoft Responsible AI Standard v2](https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-Responsible-AI-Standard-v2-General-Requirements-3.pdf)** (six principles, goal-based) and **[Google AI Principles](https://ai.google/responsibility/principles/)** (seven principles plus application restrictions).
- Neither is the primary regulatory driver at team scope; **the mapping discipline is defensive**: show how team practice supports the organisation's commitment without restructuring practice around industry language.
- The **framework-mapping artifact** has one row per principle, pointing at the team-scope artifact that provides evidence, composing artifacts, and the upward-routed gaps.
- Microsoft RAI principles most directly team-operational: **Accountability, Transparency, Reliability and safety**. Fairness, Privacy and security, and Inclusiveness have team-scope evidence with important program-level gaps.
- Google principles most directly team-operational: **Avoid unfair bias (2), Safety (3), Accountability (4), Privacy (5)**. Principles 1, 6, 7 live at program altitude.
- The audit the mapping serves is usually a **customer / partner security questionnaire** or an internal responsible-AI commitment review — not the primary regulator audit.
- The mapping is **re-pointed, not re-authored**, when (a) the framework updates, (b) a team artifact changes, (c) a new workflow enters scope.
- Other frameworks (OECD AI Principles, UNESCO, PAI, bespoke organisational commitments) are mapped against the **same table shape** when the organisation has committed to them.
- The mapping feeds the Chapter 7 upward packet as the industry-framework evidence section.
