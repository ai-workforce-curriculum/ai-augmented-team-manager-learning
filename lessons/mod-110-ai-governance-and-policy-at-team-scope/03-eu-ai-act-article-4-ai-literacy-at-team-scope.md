# Chapter 3 — EU AI Act Article 4: AI Literacy, Operated at Team Scope

> *The EU AI Act names the obligation, the EU AI Office gives the guidance, and your organisation's counsel sets the legal position. None of them run the training; you do. The deployer's Article 4 obligation becomes real on the day someone asks for the evidence packet.*

## Motivation

[Regulation (EU) 2024/1689](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) — the EU AI Act — entered into force in August 2024. [Article 4](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) obligates both **providers** (the entities that develop or place AI systems on the EU market) and **deployers** (the entities that use AI systems under their authority in the course of their activities) to *"take measures to ensure, to their best extent, a sufficient level of AI literacy of their staff and other persons dealing with the operation and use of AI systems on their behalf, taking into account their technical knowledge, experience, education and training and the context the AI systems are to be used in, and considering the persons or groups of persons on whom the AI systems are to be used."* Article 4 applies from **2 February 2025** — the first of the Act's provisions to become directly applicable.

Most organisations the level-40 manager will work in are **deployers**, not providers. The deployer's obligation is operational: ensure the people using AI on behalf of the organisation have the AI literacy appropriate to what they do. The organisation sets policy; the manager runs the practice.

The [EU AI Office](https://digital-strategy.ec.europa.eu/en/policies/ai-act) has issued and is continuing to issue guidance on how deployers should interpret Article 4 — including a *Q&A on AI literacy* and a *Living repository of AI literacy practices* that collects operator-reported approaches. The guidance is deliberately risk-based and non-prescriptive: the Act does not mandate a specific curriculum, number of hours, or certification. It mandates that the measures be *sufficient*, *contextual*, and *documented in the sense that the deployer can evidence them if asked*.

That gap between "do something sufficient" and "produce an evidence-ready training record" is where the team manager works. This chapter does three things. First, it reads Article 4 and the EU AI Office guidance as published, without overclaiming. Second, it names the operational dimensions of a team AI-literacy program that satisfies the obligation: content coverage, role segmentation, evidence capture, refresh cadence, documentation. Third, it names what counsel owns and what the manager owns, and the handoff.

> **Non-lawyer disclaimer.** This chapter is curriculum — not legal advice. The authoritative interpretation of Article 4 for your organisation is held by your organisation's counsel and, where applicable, Data Protection Officer. The content below is a reading of the public text of Article 4, the EU AI Office's published guidance, and the EU AI Act implementation and training-market practice as of late 2026. If the text diverges from what your organisation's counsel has set for you, follow counsel.

## Core concepts

### Article 4 — the operational reading

The text names three threshold elements the deployer's measures must satisfy.

1. **Sufficient level of AI literacy.** Not a defined term in the Act. The EU AI Office guidance anchors this in [Recital 20](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) of the Act, which describes AI literacy as *"skills, knowledge and understanding that allow providers, deployers and affected persons … to make an informed deployment of AI systems, as well as to gain awareness about the opportunities and risks of AI and possible harm it can cause."* "Sufficient" is functional: sufficient *to what the person does* with the system.
2. **Covering the people who operate or use the system on the deployer's behalf.** This is broader than engineers. It covers reviewers, managers, product partners, customer-facing staff who use AI outputs, and sometimes contractors who touch the workflow. The scope question is a legal-position question for counsel; the team manager's practical reading is *every member of the team whose work routes through the AI system we deploy*.
3. **Taking into account technical knowledge, experience, education and training, and context.** Different roles need different training. The manager cannot run a one-size curriculum and call it sufficient for an operations analyst, an ML-fluent IC, and a non-technical product partner equally.
4. **And the persons or groups of persons on whom the AI systems are to be used.** Where the team's AI touches affected persons (customers, employees, applicants), literacy must consider their interests. This is an input to the team's AI-literacy content, not a separate training obligation.

Article 4 is *always-on*: it does not scale with the risk tier of the AI system (unlike many other obligations in the Act). A deployer using only general-purpose AI for internal productivity still has the obligation. The obligation grows with the context, not the risk tier alone.

### Article 4 vs. the rest of the Act — what this chapter does not cover

Article 4 is one obligation among many. For a team manager, it is the obligation most commonly operational at team altitude. Other obligations covered in part by other chapters:

- **High-risk AI systems** — Title III of the Act (Articles 8 through 29) places detailed obligations on providers and deployers of high-risk systems. Determining whether a specific team workflow is high-risk is a legal-position question; counsel decides. The operational practice for high-risk workflows is covered in Chapter 4 (Articles 14 and 50).
- **General-Purpose AI models and the AI Office Code of Practice** — mostly a provider obligation; deployers are affected indirectly through the systems built on top. Scope-of-the-Act framing for upstream models lives with counsel.
- **Prohibited AI practices** — Article 5 lists prohibited practices (e.g., social scoring by public authorities, certain real-time remote biometric identification). The team manager's job is to flag any workflow adjacent to a prohibition and route to counsel.

Chapter 3 covers the Article 4 obligation specifically. Chapter 4 picks up Articles 14 and 50 where the team's AI touches regulated contexts.

### The six dimensions of a team AI-literacy program

An Article 4 program the manager runs — authored specifically for this module and composable with [`mod-105`](../mod-105-team-ai-enablement-programs/) — has six operational dimensions. The exercise produces the six written down.

1. **Content coverage.** What the program teaches. A defensible baseline (consistent with the EU AI Office's published guidance and with the IAPP AIGP body of knowledge) covers: what AI is (core concepts; capabilities and limitations; terminology); how the team's specific systems work at a user level; the EU AI Act regulatory landscape (the parts of the Act relevant to the team's workflows); the team's accountability contract (from [`mod-103` Ch. 5](../mod-103-review-standards-and-eval-commissioning/05-the-accountability-contract-ai-generates-humans-own.md)); the C5 "what AI may see" clause (data handling — Chapter 6); how to recognise and report incidents (from [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/)); risks to affected persons where applicable. The depth varies by role; the coverage does not.
2. **Role segmentation.** Who gets which depth. Three or four tiers is typical: *general awareness* for anyone touching the system; *operational fluency* for ICs who prompt and review AI; *reviewer judgement* for those who approve AI-produced artifacts; *manager accountability* for those running the system. The curriculum maps content modules to tiers.
3. **Delivery modality.** How it is delivered. Live sessions, async e-learning, hands-on exercises, peer-led office hours, incident-driven micro-sessions — [`mod-105`](../mod-105-team-ai-enablement-programs/) covers the delivery practice. For Article 4, the modality is less important than evidence capture.
4. **Evidence capture.** What the record looks like. Per person, per module, with date and a completion signal. The LMS record is the usual load-bearing artifact. For activities that happen outside the LMS (lunch-and-learns, incident retrospective debriefs, pair-reviews), the record is a dated attendance log. The audit question is *"can you produce the per-person training record on demand?"* The answer has to be yes.
5. **Refresh cadence.** How often it is updated and re-taken. A reasonable default: yearly full-curriculum refresh, quarterly content-delta updates driven by changes in the team's AI stack, and incident-driven micro-refreshes after any retrospective. The team's AI-literacy policy records the cadence; the LMS enforces it.
6. **Documentation.** How the program itself is described, versioned, and signed off. One page naming scope, objectives, segmentation, cadence, sign-off (the manager, the AI-governance partner, and the people-partner), and change-log. This document is the one the auditor reads before asking for the records.

The six dimensions map to the exercise's acceptance criteria.

### Content coverage, in more detail

A defensible content outline per the EU AI Office's published guidance and cross-referenced to the IAPP [AIGP body of knowledge](https://iapp.org/certify/aigp/) — again, this is curriculum, not legal advice. The manager's program need not be built from scratch; it extends the organisation's baseline.

- **Module A — AI foundations (awareness tier).** What generative AI is; what an LLM is; what an agent is; what a hallucination is; what prompting is; what RAG is; what tool-use / function-calling is. The baseline that no team member should be missing.
- **Module B — The team's specific AI stack.** Which tools the team uses (Claude Code, Cursor, Copilot, internal RAG, vendor-X), the model families they rely on, what data goes into which tool, what guardrails are enforced, where the output lands. This is the module that cannot be inherited from a generic curriculum; it is team-specific.
- **Module C — Regulatory landscape at depth appropriate to role.** For the awareness tier: the EU AI Act exists; Article 4 is why this training exists; the firm is a deployer; the team's workflows are classified as X. For the operational tier: more detail on relevant Articles and the team's specific obligations. For the reviewer and manager tiers: enough to run the HITL checkpoint and the escalation path.
- **Module D — Accountability, review, and the human-in-the-loop.** The mod-103 accountability contract; the mod-103 review checklist; the mod-106 delegation ladder and HITL checkpoint design; what "AI generates, humans own" means operationally. Reviewer tier and above.
- **Module E — Data, IP, and confidentiality.** The Chapter 6 data-handling policy, abbreviated for training. What class of data may go into which tool; what must never; what the vendor's data-use clauses say in plain language; what the IP position is on model outputs; what to do if a mistake happens.
- **Module F — Incident recognition and reporting.** The mod-109 detection channels; what wrongness looks like per incident class; how to preserve the trace; the trigger line to escalate. All tiers.
- **Module G — Affected-person considerations.** Where the team's AI touches customers, applicants, employees, or external stakeholders, the risks to those parties, the firm's position on them, and the team's specific mitigations. Role-dependent.

Module B is the module the manager authors; A, C, E, F, G are typically inherited from a program-level curriculum and customised to the team; D is the team's existing mod-103 and mod-106 material.

### Evidence capture: what the record has to show

The Article 4 evidence packet, at team scope, answers five questions on demand:

- *Who is on the team, by role tier?*
- *What modules did each person complete, with date?*
- *What is the current curriculum version, with change-log?*
- *Who signed off on the curriculum, and when?*
- *When is each person's next refresh due, and what triggers it?*

If the LMS or equivalent system answers all five, the evidence is portable. If any answer lives only in the manager's memory or in a Slack thread, the evidence is not audit-ready.

One pattern that does not survive an audit: "we did a lunch-and-learn in July and everyone was there." Without a dated attendance record tied to a named curriculum module, this is not evidence.

One pattern that does: "LMS curriculum `#AI-FLUENCY-TM-V2`, person-level completion report attached (CSV), covering Modules A/B/C/D/E/F per segmentation table attached, average completion date 2026-10-15, next refresh 2027-01-15." This is three artifacts the auditor can cross-check and the governance program can roll up.

### Role segmentation, in practice

A workable tier structure for an engineering team of ~10:

| Tier | Who | Modules | Baseline hours | Refresh cadence |
|---|---|---|---|---|
| **Awareness** | Anyone touching the workflow (e.g., downstream consumers of the output who are not on the team) | A, C (awareness depth), F | 1–2 hours | Annual |
| **Operational** | ICs using the AI stack daily | A, B, C (operational), E, F | 4–6 hours | Semiannual + incident-driven |
| **Reviewer** | Senior ICs and tech leads who approve AI-produced artifacts | A, B, C (operational), D, E, F, G | 6–8 hours | Semiannual + incident-driven |
| **Manager** | Team manager and above | all modules | 8–12 hours | Annual + incident-driven |

The tiers are cumulative; the manager tier includes every reviewer-tier module.

The point is not that these hours are prescribed — they are not — but that the team's program has *a declared sizing* and that the sizing matches the risk context. A compliance team will accept "we decided 2 hours was sufficient for awareness because our team's AI exposure is narrow" if the decision is documented and defensible; they will not accept "2 hours" with no rationale.

### Where counsel owns and the manager hands off

The handoff lines are specific. Counsel owns:

- The firm's **classification** of each workflow (does the AI system qualify as high-risk? limited-risk? general-purpose-only?) — this determines whether other Articles beyond 4 attach.
- The firm's **interpretation** of "sufficient" in Article 4 for its specific industry and deployment context.
- The firm's **position** on whether specific vendor arrangements place the firm in a provider role for any subset of the AI stack.
- Any **affected-person notice** obligations under Article 50 or other statutes.
- **Regulatory engagement**, including any communication with the EU AI Office or national competent authority.

The manager owns:

- **Operating** the training program against counsel's classifications.
- **Producing** the evidence packet.
- **Flagging** workflows that may have drifted out of counsel's prior classification.
- **Keeping** the segmentation and content coverage current as the team's stack evolves.

Chapter 7 names the upward packet that aggregates these for the governance program.

## Example: the three-month Article 4 rollout

Composite — calibration, not case study.

The manager inherits the Chapter 1 engineering team. Counsel has classified the team's workflows as "limited-risk" with one "adjacent-to-high-risk" workflow (an underwriting-assist flow that routes to a sister team's high-risk system downstream). The firm's program-level AI-literacy policy v2.1 names a baseline curriculum (Modules A, C, E, F, G); the team-specific Module B and the role-specific tiering are left to the manager.

Over 90 days the manager:

- *Days 1–15:* Writes the one-page team AI-literacy policy, versioned v1.0, sized per the table above with explicit rationale per tier. Signed off by the manager, the governance partner (`senior-ai-governance-architect` or a `head-of-ai-governance` delegate), and the HR partner.
- *Days 16–30:* Authors Module B (the team-specific stack walkthrough). Records in LMS. Pilots with two volunteer ICs and iterates.
- *Days 31–60:* Rolls out Module B across the team; Modules A/C/E/F/G are run as a mix of the program-level content and team-specific anchor sessions. All completions are LMS-captured.
- *Days 61–75:* Runs a tabletop exercise driven by a modified mod-109 scenario to test Module F (incident recognition). Attendance recorded.
- *Days 76–90:* Produces the first Chapter 7 upward packet with the training-record section populated.

At the end of 90 days, the team has an evidence-ready Article 4 program, versioned, segmented, dated, and rollable-up. Steady-state cost is low (quarterly refresh plus incident micro-sessions); initial authoring cost is 15–20 manager hours plus IC time per the segmentation table.

## Summary

- [EU AI Act Article 4](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) obliges deployers to ensure *sufficient* AI literacy among their staff and others operating AI on their behalf. The Article applies from **2 February 2025**.
- "Sufficient" is **contextual and non-prescriptive**; the deployer must decide and document. The team manager operates against the organisation's interpretation.
- Six operational dimensions of a team AI-literacy program: **content coverage, role segmentation, delivery modality, evidence capture, refresh cadence, documentation**.
- A defensible baseline curriculum has **seven modules** (A through G); Module B (the team-specific stack walkthrough) is the one the manager must author.
- **Role segmentation** to at least three tiers (awareness, operational, reviewer) is standard; the manager tier extends above.
- **Evidence capture** answers five questions on demand: who, what, curriculum version, sign-off, next refresh. The LMS or equivalent is the load-bearing artifact.
- **Refresh cadence**: annual full refresh, semiannual or quarterly deltas, incident-driven micro-sessions. The cadence is declared in the policy and enforced by the LMS.
- **Handoff lines**: counsel owns classification, interpretation, affected-person notice, and regulator engagement; the manager owns operation and evidence production.
- The [EU AI Office](https://digital-strategy.ec.europa.eu/en/policies/ai-act) publishes ongoing guidance (Q&A, Living repository of AI literacy practices); the manager tracks changes against the program.
- The training record folds into the GOVERN 2.2 row of the Chapter 2 crosswalk and into the Chapter 7 upward packet.
