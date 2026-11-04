# AI-Augmented Team Manager Curriculum

<!-- aicg:orientation:start -->
> **Start here:** [Module 00: Your Relationship to the Model](lessons/00-your-relationship-to-the-model/README.md). Where this role sits relative to the model, what it owns, and who it works with across the sibling curricula.
<!-- aicg:orientation:end -->

**Role level:** 40 (team manager — AI Workforce family)
**Family:** AI Workforce
**Status:** planned — modules and projects below are the planned scope authored from [`.aicg/curriculum-plan.json`](.aicg/curriculum-plan.json). Lessons and projects will be drafted by subsequent autonomous content cycles.

## Overview

This track teaches the *team-scale operating system* for AI-augmented work for a line manager running a 5-30 person team at level 40: taking ownership of a team's AI-adoption roadmap and sequencing pilots vs. rollouts (grounded in 76% of the live-posting sample and Dell'Acqua's "jagged technological frontier" research) → setting review norms for AI-generated work and commissioning eval frameworks (standards-as-code via Cursor rules files, AGENTS.md conventions, ADR templates; LLM-as-judge via G-Eval / Promptfoo / LangSmith / Inspect AI; accountability contract: "AI generates, humans own") → measuring team productivity, cost, and AI ROI (DX Core 4, SPACE, DORA under AI-augmented conditions, flow metrics; grounded in Peng / Ziegler / Noy-Zhang / Brynjolfsson / Dell'Acqua empirical literature) → running team-level enablement programs (Day 0 / 30 / 60 / 90 bootcamps, workshops, communities of practice, tool-budget distribution) → redesigning workflows for human + agent hybrid work (jagged-frontier delegation, MCP tool-authorisation, AGENTS.md delegation ladders) → protecting skill growth and anti-atrophy under AI augmentation (deliberate-practice carve-outs, judgment-weighted career ladders) → hiring, performance management, and feedback with AI in the loop (interview-loop redesign, OKRs that reflect AI leverage, EEOC / NYC LL144 compliance at team scope) → running AI-incident response and blameless post-mortems adapted for AI-produced incidents (Google SRE + Allspaw adapted for fault chains that include a model) → translating AI governance into team practice (NIST AI RMF GOVERN at team scope, EU AI Act Article 4 AI-literacy obligation, Microsoft Responsible AI Standard, Google AI Principles, OWASP LLM Top 10) → owning vendor / tool / budget selection at team scope (Cursor / Copilot / Claude Code / agent frameworks; build-vs-buy matrix) → designing the cross-functional ritual calendar and the exec-communication story that ties roadmap, ROI, governance, and incident history into one coherent narrative.

It is a **people-manager track at level 40**, positioned in the **AI Workforce family**. The differentiator against [`ai-engineering-manager-learning`](https://github.com/ai-engineering-curriculum/ai-engineering-manager-learning) (level 50, manager-of-managers for engineering teams) and [`ai-enablement-lead-learning`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) (level 45, org-wide enablement programs) is *single-team scope*: this curriculum builds the operating system for one team of 5-30 ICs whose work runs through AI. The differentiator against peer [`ai-augmented-product-manager-learning`](https://github.com/ai-workforce-curriculum/ai-augmented-product-manager-learning) is *people management*: this role owns the team itself, not the product. The differentiator against peer [`ai-risk-engineer-learning`](https://github.com/ai-governance-curriculum/ai-risk-engineer-learning) (level 25, AI Governance family) is *managerial commissioning*: this role commissions the risk-eval / guardrail work that peer engineers and acts on the evidence, rather than re-building the rig.

Total planned commitment: **180 hours across 12 modules** + **120 hours across 3 projects** = **~300 hours**.

## Ownership rule

Following the project-wide ownership rule, this curriculum:

- **Owns** the team-scale operating system for AI-augmented work end-to-end: team adoption roadmap and workflow redesign, review norms and eval commissioning for AI-generated artifacts, team productivity + AI-ROI measurement, team-scope enablement programs, agent-delegation at team scope, skill-growth protection and career development under AI augmentation, hiring / performance / feedback with AI in play, accountability + AI-incident response at team scope, team-scope governance and policy translation, vendor / budget / tool selection at team scope, and cross-functional ritual-calendar leadership.
- **Defers down** to [`ai-governance-analyst-learning`](https://github.com/ai-governance-curriculum/ai-governance-analyst-learning) (level 15) for operational governance legwork (intake, inventory, framework crosswalks, impact-assessment drafting) this role consumes at team scope; to [`ai-augmented-analyst-learning`](https://github.com/ai-workforce-curriculum/ai-augmented-analyst-learning) (level ~20) and [`ai-assisted-software-engineer-learning`](https://github.com/ai-engineering-curriculum/ai-assisted-software-engineer-learning) (level ~25) for IC-scope AI-augmented work this role's reports practice; to a generic people-management background (Grove, Fournier, Larson, Zhuo) that is listed in [`PREREQUISITES.md`](PREREQUISITES.md) and not re-taught.
- **Defers sideways** to [`ai-augmented-product-manager-learning`](https://github.com/ai-workforce-curriculum/ai-augmented-product-manager-learning) (peer, level 30, AI Workforce family) for AI-feature product scope and ROI framing; to [`ai-risk-engineer-learning`](https://github.com/ai-governance-curriculum/ai-risk-engineer-learning) (peer, level 25, AI Governance family) for engineered risk-eval, red-team, and guardrail depth the team consumes; to [`ai-infra-team-lead-learning`](https://github.com/ai-infra-curriculum/ai-infra-team-lead-learning) (peer / lower-adjacent, level 35, Infra family) for infra-team-lead-specific delivery depth — this track stays discipline-agnostic.
- **Defers up** to [`ai-enablement-lead-learning`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) (level 45, AI Workforce family) for org-wide enablement programs, multi-team coordination, and procurement at scale; to [`ai-engineering-manager-learning`](https://github.com/ai-engineering-curriculum/ai-engineering-manager-learning) (level 50) for engineering-manager-of-managers scope; to [`senior-ai-governance-architect-learning`](https://github.com/ai-governance-curriculum/senior-ai-governance-architect-learning) (level 50) for control-library architecture; to [`head-of-ai-governance-learning`](https://github.com/ai-governance-curriculum/head-of-ai-governance-learning) (level 60) for governance program leadership; to [`chief-ai-officer-learning`](https://github.com/ai-governance-curriculum/chief-ai-officer-learning) (level 70) for executive scope.
- **Out of scope** to legal counsel (this role does not deliver legal opinion), to HR / employee-relations partners (formal employment actions), and to security operations / DFIR (SOC-side incident handling; this role feeds AI-specific signal to SecOps).

See [`JOB_REQUIREMENTS.md`](JOB_REQUIREMENTS.md) for the requirements-to-coverage map with 25-posting live evidence and the cited authoritative references the catalog is grounded in.

## Module Plan

| Module | Title | Hours | Status |
|---|---|---|---|
| mod-101-ai-augmented-team-manager-position-and-contract | The AI-Augmented Team Manager: Role, Scope, and the Human/Machine Contract | 14 | planned |
| mod-102-team-ai-adoption-and-roadmap | Driving Team-Level AI Adoption and the Adoption Roadmap | 18 | planned |
| mod-103-review-standards-and-eval-commissioning | Review Standards, Standards-as-Code, and Commissioning Eval Frameworks | 18 | planned |
| mod-104-productivity-measurement-and-ai-roi | Measuring Team Productivity, Cost, and AI ROI | 16 | planned |
| mod-105-team-ai-enablement-programs | Team-Level AI Enablement Programs | 14 | planned |
| mod-106-workflow-redesign-and-agent-delegation | Workflow Redesign and Agent Delegation at Team Scope | 16 | planned |
| mod-107-skill-growth-anti-atrophy-and-career-development | Skill Growth, Anti-Atrophy, and Career Development in AI-Augmented Teams | 14 | planned |
| mod-108-hiring-performance-and-feedback-with-ai-in-the-loop | Hiring, Performance Management, and Feedback with AI in the Loop | 16 | planned |
| mod-109-accountability-incident-response-and-blameless-postmortems | Accountability, AI-Incident Response, and Blameless Post-Mortems | 14 | planned |
| mod-110-ai-governance-and-policy-at-team-scope | AI Governance, Policy, and Compliance at Team Scope | 14 | planned |
| mod-111-vendor-budget-and-tool-selection-at-team-scope | Vendor Selection, Tool Budget, and Build-vs-Buy at Team Scope | 12 | planned |
| mod-112-cross-functional-leadership-and-ritual-calendar | Cross-Functional Leadership and the Team Ritual Calendar | 14 | planned |

## Project Plan

| Project | Title | Hours | Status |
|---|---|---|---|
| project-101-team-ai-operating-system | The Team AI Operating System — Adoption Roadmap + Review Standards + Agent Delegation | 40 | planned |
| project-102-90-day-productivity-and-enablement-program | 90-Day Productivity & Enablement Program for an AI-Augmented Team | 40 | planned |
| project-103-ai-incident-accountability-and-governance-package | AI Incident + Accountability + Governance Package for One Team | 40 | planned |

## Module summaries

### mod-101 — The AI-Augmented Team Manager: Role, Scope, and the Human/Machine Contract
Define the level-40 team-manager scope in the AI Workforce family against `ai-enablement-lead` (level 45, org-wide), `ai-engineering-manager` (level 50, manager-of-managers), and the IC tracks this role inherits from. Read Grove, Fournier, Larson, Zhuo as the assumed baseline (prerequisite, not re-taught) and layer AI-augmentation onto it. Author the team's human/machine contract — what humans own, what the AI owns, what verification must happen before AI output ships, where the manager is on the hook — grounded in the "AI generates, engineers own" language observed across the 25-posting sample. Build the manager's own AI-tool fluency bar (Cursor / Claude Code / Copilot / Promptfoo / LangSmith at review-and-model level, not out-ship-ICs level).

### mod-102 — Driving Team-Level AI Adoption and the Adoption Roadmap
Author the team's 12-month AI-adoption roadmap — what to automate, in what order, with whom, how to measure success — grounded in 76% of the posting sample (R1) and Dell'Acqua's "jagged technological frontier" framing. Sequence pilots vs. rollouts, opt-in vs. mandate. Partner with Platform / DevEx / Product; know when a team-specific pilot graduates to Platform-owned product (hand-off to `ai-enablement-lead` at level 45). Use industry-survey data (Microsoft Work Trend Index, McKinsey State of AI, GitHub Octoverse, Stack Overflow Developer Survey) as input, not as the plan itself. Author the roadmap one-pager, pilot charter, rollout decision log, and exec pre-read.

### mod-103 — Review Standards, Standards-as-Code, and Commissioning Eval Frameworks
Set team-level review standards for AI-generated work — PR / review checklists, verification requirements, what "LGTM" means when the author was a model — anchored in R2 (0.60, 6 in-window postings) and R3 (0.44). Encode standards-as-code with Cursor rules files, AGENTS.md conventions, ADR templates, lint policies, pre-commit hooks. Commission eval frameworks at team scope using LLM-as-judge (G-Eval), Promptfoo, LangSmith, Inspect AI — decide WHAT to evaluate, who owns the harness, how outputs feed back. Author the accountability contract. Map team review norms to OWASP LLM Top 10 so prompt-injection / sensitive-data risks surface at review time. Engineered risk / guardrail depth stays owned by `ai-risk-engineer` (peer, level 25).

### mod-104 — Measuring Team Productivity, Cost, and AI ROI
Choose metrics that separate AI-induced gain from AI theatre — DX Core 4 as current industry standard, SPACE as the research anchor, DORA under AI-augmented conditions, flow metrics from Kersten. Read the empirical literature (Peng arXiv:2302.06590; Ziegler Commun. ACM; Noy & Zhang Science 2023; Brynjolfsson, Li, Raymond NBER; Dell'Acqua et al.) as evidence for metric choice. Track per-engineer token / seat cost and tool-budget; defend the AI tooling spend to leadership with rollback criteria. Author the team-productivity narrative — a one-pager a VP can sign, a dashboard for ongoing review, and a "what we got wrong last quarter" ritual. Instrument qualitative signal alongside quantitative. Dashboard construction linked to `ai-augmented-analyst` (level 20); product-ROI framing linked to `ai-augmented-product-manager` (level 30).

### mod-105 — Team-Level AI Enablement Programs
Design a team-scope enablement program — Day 0 / 30 / 60 / 90 structure for a 5-30 person team, internal bootcamps, workshops, communities of practice — anchored in R5 (0.36, 4 in-window postings). Pick and distribute tool budgets (Cursor seats, Copilot seats, token allowances) by learning stage. Measure fluency growth with practical artifacts grounded in Josh Bersin AI-in-L&D research and Microsoft Work Trend Index. Partner with HR / L&D / Platform on delivery. Hand off to `ai-enablement-lead` (level 45) when scope graduates to org-wide.

### mod-106 — Workflow Redesign and Agent Delegation at Team Scope
Redesign team workflows for human + agent hybrid work using Dell'Acqua's jagged-frontier framing to decide what routes to AI vs. junior human vs. senior human (R7 below-threshold but research-anchored). Author agent-delegation patterns at team scope — AGENTS.md conventions, delegation contracts, tool-authorisation policy; working fluency with Model Context Protocol and Google Agent-to-Agent. Design human-in-the-loop checkpoints. Plan where the team's highest-value human attention goes once AI takes over the routine slice. Agent-construction IC mechanics stay owned by `ai-assisted-software-engineer` (level 25); frontier-agent safety depth stays owned by `agentic-safety-engineer` (level 40, AI Governance family).

### mod-107 — Skill Growth, Anti-Atrophy, and Career Development
Read the research on AI-induced skill distribution (Brynjolfsson NBER: gains concentrate at lower tenure; Noy & Zhang Science: compressed gap; Dell'Acqua: deskilling on some tasks) and translate each finding into team policy (R10 below-threshold but research-anchored). Design deliberate-practice carve-outs — paired-review rotations, periodic AI-off work, judgment-weighted review standards. Adjust the team's career-development ladder to reward judgment, not just AI-assisted throughput. Instrument burnout and over-reliance signals using Edmondson "The Fearless Organization" and Westrum culture typology. HR formal processes link out.

### mod-108 — Hiring, Performance Management, and Feedback with AI in the Loop
Redesign the interview loop for AI-augmented candidates (Google re:Work structured-interview baseline; SHRM AI-in-HR practice). Adjust levelling / promotion criteria so AI-amplified throughput doesn't crowd out judgment, system understanding, mentorship, ownership. Run performance management with AI in play — 1:1 cadence, feedback, OKR / KPI goal-setting that reflects AI leverage, underperformance root-cause framing. Comply with AI-in-hiring legal framing (US EEOC, NYC Local Law 144, EU AI Act Article 6 + Annex III on high-risk hiring AI). Author team-scope workforce-planning artifacts (R9 at team scope only; cross-team scope defers upward).

### mod-109 — Accountability, AI-Incident Response, and Blameless Post-Mortems
Operate the accountability contract end-to-end. Adapt blameless post-mortem practice (Google SRE, Allspaw) for AI-produced incidents — the team cannot blame the model but must find the fault chain (human reviewer, harness, prompt, agent policy, tool connection). Triage AI-specific incidents at team scope — hallucination-driven harm, prompt-injection exploitation, unauthorised-tool-use, model regression — using AI Incident Database and OECD.AI Incidents Monitor as precedents. Coordinate with `ai-risk-engineer` (level 25) on engineered root-cause and SecOps on the SOC-side chain. Fold confirmed incidents back into mod-103 eval commissioning and mod-106 delegation playbook.

### mod-110 — AI Governance, Policy, and Compliance at Team Scope
Translate NIST AI RMF 1.0 GOVERN function into team-scope practices using the Playbook as day-to-day reference. Meet the EU AI Act Article 4 AI-literacy obligation for deployers (the manager is the operational owner at team scope). Apply Article 14 (human oversight) and Article 50 (transparency) where the team's AI touches regulated use cases. Map team practice against Microsoft Responsible AI Standard and Google AI Principles. Set data / IP / confidentiality policy for the team. Produce team evidence for upward-rolling governance programs owned by `head-of-ai-governance` (level 60) and architecture owned by `senior-ai-governance-architect` (level 50). Legal opinion defers to counsel.

### mod-111 — Vendor Selection, Tool Budget, and Build-vs-Buy at Team Scope
Evaluate AI coding / knowledge-work copilots (Cursor, GitHub Copilot, Claude Code, Windsurf, Continue, Cody, Zed, JetBrains AI) against team context with a defensible build-vs-buy matrix (R6 below-threshold but kept at team-scope). Evaluate agent frameworks (LangChain / LangGraph, CrewAI, AutoGen, PydanticAI) and agent-authoring environments. Distribute tool budgets by enablement stage from mod-105. Partner with procurement, security, legal on vendor due-diligence (DPA, SOC 2, model-provenance). Org-wide procurement linked to `ai-enablement-lead` (level 45).

### mod-112 — Cross-Functional Leadership and the Team Ritual Calendar
Design the team ritual calendar — planning, review, retro, demo, 1:1s, office hours, community-of-practice cadence — justified against the measurement framework from mod-104 (Lencioni "Death by Meeting" trade-offs). Partner with Product, Platform / DevEx, Design, Data, and AI-Governance peers using Google re:Work manager-behaviour findings. Communicate upward — exec pre-reads, quarterly reviews — connecting roadmap (mod-102), productivity narrative (mod-104), governance posture (mod-110), and incident history (mod-109) into one coherent story. Run one-pager and decision-log hygiene so the team's AI-augmented operating system is legible. Position IAPP AIGP as shared cross-functional vocabulary.

## Assessment

Each module ships **1 quiz** plus the exercises and a lab listed in [`.aicg/curriculum-plan.json`](.aicg/curriculum-plan.json). Each project ships a portfolio-grade README, a reproducibility bundle (roadmap artifacts, review-standards + AGENTS.md packages, delegation contracts, governance crosswalks, incident runbooks and post-mortems, enablement plans, productivity-dashboard specs), and an explicit rubric covering adoption-roadmap defensibility, review-standards clarity, eval-commissioning quality, productivity-narrative honesty, enablement-program design, workflow redesign and delegation ladder, skill-growth protection, hiring-and-performance compliance, incident-response rigour, governance-posture coverage, vendor-selection defensibility, and cross-functional communication.

## Where to go after this curriculum

- **`ai-enablement-lead-learning`** (level 45, AI Workforce family) — org-wide enablement programs, multi-team coordination, procurement at scale.
- **`ai-engineering-manager-learning`** (level 50) — engineering-specific manager-of-managers scope.
- **`senior-ai-governance-architect-learning`** (level 50) — architectural scope on the Governance ladder.
- **`head-of-ai-governance-learning`** (level 60) — program leadership, board reporting, regulator engagement.
- **`chief-ai-officer-learning`** (level 70) — executive scope.
- **`ai-augmented-product-manager-learning`** (peer, level 30) — natural cross-training for product-side AI-feature scope and ROI framing.
- **`ai-risk-engineer-learning`** (peer, level 25, AI Governance family) — natural cross-training for engineered risk / red-team / guardrail depth this role commissions.

<!-- needs-research: backfill live-posting salary coverage into JOB_REQUIREMENTS.md once Lever / Workday server-side-rendered salary bands are fanned-out in the next research cycle (no salary ranges rendered in the 2026-11 crawl). -->
<!-- needs-research: lock role_level numbers for ai-augmented-analyst, ai-assisted-software-engineer, ai-augmented-product-manager, ai-enablement-lead, ai-engineering-manager once those packets land; update the level references in this file and in PREREQUISITES.md. -->
