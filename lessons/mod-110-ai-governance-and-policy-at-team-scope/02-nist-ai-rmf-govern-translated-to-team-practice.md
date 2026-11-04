# Chapter 2 — NIST AI RMF 1.0 GOVERN Function, Translated to Team-Scope Practice

> *The NIST AI RMF is written for an organisation. The level-40 manager's job is not to re-write it for a team; the job is to say — against each subcategory — exactly which team artifact discharges the practice, where its evidence lives, and which upstream policy it inherits from.*

## Motivation

The [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf) (January 2023) names four functions: GOVERN, MAP, MEASURE, MANAGE. Each is decomposed into categories and subcategories; each subcategory has a recommended set of actions in the [NIST AI RMF Playbook](https://airc.nist.gov/AI_RMF_Knowledge_Base/Playbook). The RMF is explicitly voluntary and framework-agnostic — it does not prescribe tools, organisational structures, or specific policies. That abstraction is why program-level governance teams reach for it; it is also why a level-40 manager picking it up for the first time cannot easily tell which subcategory applies to their actual team.

The GOVERN function is the subset that lives closest to the manager. It covers *policy, accountability, workforce, roles, and oversight* — the connective tissue that lets MAP, MEASURE, and MANAGE run coherently. In the published framework, GOVERN has six categories (GOVERN 1 through GOVERN 6) with 20 subcategories between them. Several of these subcategories are organisational (e.g., GOVERN 1.1 — *legal and regulatory requirements involving AI are understood, managed, and documented*); those stay with legal and the governance program. Several are team-grain (e.g., GOVERN 3.2 — *roles and responsibilities and lines of communication related to mapping, measuring, and managing AI risks are documented and are clear to individuals and teams throughout the organization*); these are exactly what the manager runs.

This chapter does three things. First, it names the GOVERN subcategories that live at team scope, and the ones that do not. Second, it maps each in-scope subcategory to a specific team artifact (most authored in other mod-10x chapters) and names where its evidence lives. Third, it introduces the **GOVERN crosswalk table** — the artifact Exercise 01 produces and the backbone of the Chapter 7 upward packet.

## Core concepts

### Why GOVERN first, and only GOVERN

The AI RMF's four functions are not sequenced but are naturally layered: GOVERN is the structural function on which the other three rest. For a team-scope translator:

- **GOVERN** names policy, roles, accountability, and workforce practice. Almost every subcategory maps to a concrete team artifact in some other mod-10x chapter. mod-110 is the one that *names the mapping*.
- **MAP** names context-setting and risk identification for a specific AI system. The engineered depth of MAP (threat modelling, capability/limitation mapping, impact assessment) lives at [`ai-risk-engineer`](https://github.com/ai-governance-curriculum/ai-risk-engineer-learning) (L25) and [`ai-governance-analyst`](https://github.com/ai-governance-curriculum/ai-governance-analyst-learning) (L15). The team-scope manager contributes use-case context and consumes the output.
- **MEASURE** names evaluation, testing, and measurement. This is the [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) commissioning scope at team altitude and the `ai-risk-engineer` scope at engineered altitude.
- **MANAGE** names incident response, risk prioritisation, and resource allocation. This is the [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) incident-response scope at team altitude.

mod-110 Chapter 2 scopes GOVERN. The team's MAP, MEASURE, and MANAGE evidence is cross-referenced in the crosswalk, not re-authored.

### The six GOVERN categories, at a glance

The NIST AI RMF 1.0 GOVERN function (pp. 21–26 of the framework; subcategory detail in the Playbook) covers:

- **GOVERN 1** — *Policies, processes, procedures, and practices across the organization related to the mapping, measuring, and managing of AI risks are in place, transparent, and implemented effectively.*
- **GOVERN 2** — *Accountability structures are in place so that the appropriate teams and individuals are empowered, responsible, and trained for mapping, measuring, and managing AI risks.*
- **GOVERN 3** — *Workforce diversity, equity, inclusion, and accessibility processes are prioritized in the mapping, measuring, and managing of AI risks throughout the lifecycle.* (In Playbook form, GOVERN 3 is primarily about *workforce diversity and competencies for AI risk work*, not DEI programs generally.)
- **GOVERN 4** — *Organizational teams are committed to a culture that considers and communicates AI risk.*
- **GOVERN 5** — *Processes are in place for robust engagement with relevant AI actors.*
- **GOVERN 6** — *Policies and procedures are in place to address AI risks and benefits arising from third-party software and data and other supply chain issues.*

Not every subcategory under these six is team-grain; the crosswalk picks the ones that are.

### The in-scope GOVERN subcategories at team altitude

The following GOVERN subcategories map directly to team-scope artifacts the manager already owns (or should by the end of this track). The subcategory numbers and verbatim text are from NIST AI RMF 1.0, Appendix A; refer to the published document for the full wording and to the Playbook for recommended actions.

| Subcategory | Team-scope interpretation | Backing artifact (team) | Backing artifact (upstream) |
|---|---|---|---|
| **GOVERN 1.2** — policies and procedures to define characteristics of trustworthy AI | How the team operationalises the organisation's trustworthy-AI characteristics (reliability, safety, fairness, privacy, explainability, security) at review time | [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) review checklist; [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) AGENTS.md conventions | Program policy registry |
| **GOVERN 1.3** — risk-management processes and outcomes are communicated | The team's use-case register, the eval backlog, the incident retrospective | [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) eval commissioning records; [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) retrospective artifacts | Program risk register |
| **GOVERN 1.4** — determination of risk management process alignment with applicable legal and regulatory requirements | Which team workflows touch which regulated-use-case territory; flag to counsel | Chapter 4 (Articles 14 & 50) workflow triggers | Counsel-owned legal mapping |
| **GOVERN 2.1** — roles, responsibilities, and lines of communication for AI risks are documented | The role chart for the team: IC, reviewer, manager, `ai-risk-engineer` peer, SecOps peer, counsel partner | [`mod-103` Ch. 5](../mod-103-review-standards-and-eval-commissioning/05-the-accountability-contract-ai-generates-humans-own.md) accountability contract; [`mod-109` Ch. 5](../mod-109-accountability-incident-response-and-blameless-postmortems/05-routing-contract-with-risk-engineer-and-secops.md) routing contract | Program RACI |
| **GOVERN 2.2** — the organisation's personnel and partners receive AI risk management training | The team's AI-literacy program (Article 4 interpretation) | Chapter 3 training record; [`mod-105`](../mod-105-team-ai-enablement-programs/) enablement artifacts | Program-wide curricula |
| **GOVERN 2.3** — executive leadership of the organisation takes responsibility for decisions about AI risks | Team-manager-level sign-off on team-grain AI decisions; upward escalation triggers | Chapter 7 upward packet; role contract from [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) | CEO / head-of-AI-governance sign-off |
| **GOVERN 3.2** — policies and procedures are in place to define and differentiate roles and responsibilities for human-AI configurations and oversight of AI systems | Human-oversight checkpoint design per workflow; delegation ladder | [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) delegation ladder and HITL checkpoints; Chapter 4 Art. 14 mapping | Program human-oversight standard |
| **GOVERN 4.1** — organisational practices are in place to foster a critical thinking and safety-first mindset | The review checklist; the C2 verification bar; the C4 "what happens when AI is wrong" play | [`mod-103` Ch. 2](../mod-103-review-standards-and-eval-commissioning/) review checklist; [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) C2/C4 clauses | Program culture statement |
| **GOVERN 4.2** — organisational teams document the risks and potential impacts of AI technology they deploy | The team's use-case register with risk notes and impact context | Chapter 6 data-handling policy; team use-case register (Chapter 7) | Program impact-assessment library |
| **GOVERN 4.3** — organisational practices are in place to enable AI testing, identification of incidents, and information sharing | The incident runbook; detection channels; the backfeed ritual | [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) runbook + retrospective; [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) eval regression gate | Program incident registry |
| **GOVERN 5.1** — organisational policies and practices are in place to collect, consider, prioritize, and integrate feedback from external AI actors | The team's downstream-consumer feedback channel; the partner-report escalation path from [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) Ch. 2 | [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) detection channels | Program external-stakeholder program |
| **GOVERN 6.1** — policies and procedures are in place that address AI risks associated with third-party entities | The team's vendor and tool list, with data-use clauses and SLA inheritance | [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) tool registry; Chapter 6 data-handling policy | Program vendor-governance program |
| **GOVERN 6.2** — contingency processes are in place to handle failures or incidents in third-party data or AI systems | The team's vendor-side incident response (silent model changes, deprecations, outages) | [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) vendor-side detection category; [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) continuity clauses | Program BCP |

GOVERN 1.1 (legal/regulatory understanding), GOVERN 1.5 (periodic policy review), GOVERN 1.6 (inventory of AI systems at org scope), and GOVERN 1.7 (risk-tiered deprecation) are *organisational* subcategories; the manager contributes to them but does not own them. The crosswalk lists them so the upward packet can show the contribution.

GOVERN 3 subcategories on workforce diversity, equity, inclusion, and accessibility are *part-organisational, part-team*. The team's hiring, levelling, and performance-management practices under AI augmentation sit in [`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/); the manager cross-references to that module rather than re-authoring here.

### The crosswalk artifact

Exercise 01 produces the team's **GOVERN crosswalk** — one table like the one above, filled in with the team's specific artifact paths and owners. Three columns matter beyond the subcategory:

1. **Team-scope interpretation** — one sentence of plain-language *"what we do at team altitude for this subcategory"*. Not a verbatim quote of the Playbook; a specific-to-this-team statement.
2. **Backing artifact (team)** — the specific file path, wiki link, or repository location where the evidence lives. Not "Slack"; not "the team wiki"; the specific URL. If the evidence does not exist, the cell is a **gap marker** with owner and date.
3. **Backing artifact (upstream)** — the policy, standard, or program document the team's practice inherits from. If none exists, the cell is empty and the gap routes upward to the governance architect; the team artifact stands on its own until policy catches up.

The crosswalk is the artifact the governance program consumes. It is also the artifact the manager uses to triage *gaps*: subcategories where either the team artifact or the upstream policy is missing become the backlog for the next quarter.

### Using the Playbook, not just the framework

The [NIST AI RMF Playbook](https://airc.nist.gov/AI_RMF_Knowledge_Base/Playbook) is the day-to-day reference for the subcategory practice. For each subcategory, it names:

- **Suggested actions** — a bulleted list of specific operational steps.
- **Transparency and documentation** — questions the subcategory implies the team should be able to answer.
- **References** — primary sources (ISO/IEC 23894, OECD, academic literature) that ground the action.

For the team-scope manager, the Playbook's *Transparency and documentation* questions are the acceptance criteria for the crosswalk. If the team cannot answer them, the cell is a gap.

One illustrative pair (paraphrased from the Playbook; refer to the live document for the current authoritative wording):

- GOVERN 2.1 asks the team to document roles and responsibilities. The Playbook's transparency questions include *"who is accountable for the AI system?"* and *"what is the escalation path if the system behaves unexpectedly?"*. The mod-103 Chapter 5 accountability contract and the mod-109 Chapter 5 routing contract between them answer both; the crosswalk cell cites them.
- GOVERN 4.3 asks the team to foster incident identification and sharing. The Playbook's transparency questions include *"how are AI incidents tracked and communicated?"*. The mod-109 incident runbook and the quarterly retrospective between them answer the question; the crosswalk cites them.

The pattern is the same for every subcategory: *which playbook questions does this team actually answer, and where is the answer written down?*

### Where NIST intentionally does not prescribe

Two silences in the RMF are load-bearing and the crosswalk has to respect them.

- **Risk thresholds are not in the framework.** NIST does not say what constitutes "acceptable" AI risk; it says the organisation must set and justify thresholds. At team scope, the manager inherits the organisation's thresholds; if none exist, the crosswalk routes GOVERN 1.3 upward as a gap.
- **Tooling is not in the framework.** NIST does not recommend specific GRC tools, evaluation platforms, or observability stacks. The team picks tools (see [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) for evals, [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) for the broader stack); the crosswalk records the choice and the justification.

These silences keep the RMF framework-agnostic and are useful at team altitude: the manager's practice does not have to match an external tool to pass an audit; it has to be documented, consistent, and inherit cleanly from the upstream policy.

## Example: filling in GOVERN 2.2 for a specific team

A concrete pass at a single row. Composite scenario — calibration, not case study.

The manager operates an engineering team of eight ICs and two tech leads at the financial-services firm from Chapter 1. The AI-literacy program (Chapter 3) runs as a 30-day onboarding module for new hires, a quarterly refresh for all team members, and an incident-driven micro-session after every retrospective. Evidence lives in the team's LMS (an internal Cornerstone deployment) and in the retrospective artifacts in the shared drive.

The GOVERN 2.2 row of the crosswalk might read:

- **Subcategory:** GOVERN 2.2 — personnel receive AI risk-management training appropriate to their roles.
- **Team-scope interpretation:** Every IC completes the 30-day AI-fluency onboarding; all team members complete a quarterly 60-minute refresh; incident retrospectives include a 15-minute literacy section tied to the fault chain.
- **Backing artifact (team):** LMS curriculum `#AI-FLUENCY-TM` (link); quarterly refresh records in LMS reports (quarterly export path); retrospective artifact store in `drive://ai-incidents/retrospectives/`.
- **Backing artifact (upstream):** Firm-wide AI-literacy policy v2.1 (link); firm-wide Article 4 compliance interpretation from Legal dated 2026-05-14 (link).

The row is runnable, inheritable, and auditable. The crosswalk is 20 or so rows like this.

## Summary

- NIST AI RMF 1.0 has four functions; **GOVERN** is the one that sits closest to the team manager and that structures the module.
- The RMF is deliberately **framework-agnostic**; the manager translates GOVERN subcategories into team-scope practice without inventing tooling or thresholds the organisation has not set.
- **12 GOVERN subcategories** are team-grain and map directly to artifacts the manager owns (most authored in other mod-10x chapters): GOVERN 1.2, 1.3, 1.4, 2.1, 2.2, 2.3, 3.2, 4.1, 4.2, 4.3, 5.1, 6.1, 6.2.
- **The NIST AI RMF Playbook** is the day-to-day reference: its transparency and documentation questions are the acceptance criteria for each crosswalk cell.
- **The crosswalk artifact** (Exercise 01) has four columns per row: subcategory, team-scope interpretation, backing team artifact, backing upstream artifact — with explicit **gap markers** where either is missing.
- **What NIST does not prescribe**: risk thresholds (inherit from the organisation; route upward as gap if absent) and tooling (document the team's choice in the crosswalk).
- Chapter 7 will fold the crosswalk, the Chapter 3 training record, the Chapter 5 industry-framework mapping, and the Chapter 6 data policy into the upward packet.
