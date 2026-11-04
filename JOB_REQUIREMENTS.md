# Job Requirements — AI-Augmented Team Manager

**Role level:** 40 (team manager — AI Workforce family)
**Track:** `ai-augmented-team-manager-learning`
**Research window:** 2026-08-06 → 2026-11-04 (last 90 days)
**Today:** 2026-11-04
**Live postings sampled this cycle:** 25 (18 L40 team-manager + 7 L45-or-above supplementary; see [`.aicg/job-requirements.json`](.aicg/job-requirements.json) `research_status.seniority_split`)

This file documents the requirements catalog used to seed the AI-Augmented Team Manager curriculum. Raw normalised data lives in [`.aicg/job-requirements.json`](.aicg/job-requirements.json); the planned curriculum lives in [`.aicg/curriculum-plan.json`](.aicg/curriculum-plan.json); this cycle's additive delta (four differentiator modules — the remaining eight modules extend level-40 breadth with authoritative references) is in [`.aicg/curriculum-plan-delta.json`](.aicg/curriculum-plan-delta.json).

## Status — 2026-11 research pass, 25 in-window postings sampled

The literal title "AI-Augmented Team Manager" does not yet appear verbatim in the market. The role is hired against under adjacent titles — **Engineering Manager, AI Enablement / AI Transformation / Agentic Workflows / Developer Productivity AI / Applied AI / AI-Enabled Engineering** — with team-scope framing. 25 live postings observed 2026-08-06 → 2026-11-04 across Greenhouse, Ashby, Lever, Workday, BuiltIn, and employer career sites (Harvard HUIT, ServiceNow, NVIDIA, NSW LRS, Airbnb, Datadog). 7 of 25 carry an in-window `date_posted`; 14 are live-but-undated on ATS (counted as posting evidence with `date_observed = 2026-11-04`); 4 are retained as language exemplars only (`date_posted` outside window).

The sample skews toward **engineering-team managers** because that market is codifying the deliverables first — the same role in design, analytics, research, legal-ops, and customer-support teams is covered through the authoritative references (Microsoft Work Trend Index, McKinsey State of AI, MIT Sloan Management Review, OECD AI-at-work briefings) catalogued in [`.aicg/job-requirements.json`](.aicg/job-requirements.json) `authoritative_references`.

**Sampling continuity.** Five requirement themes clear the 0.30 posting-frequency threshold and are owned by this track. Three themes (R6 vendor governance 0.28, R7 workflow redesign 0.28, R10 skill atrophy 0.08) are *not* at threshold but are still kept as standalone modules — in R6 and R7 because the manager-scope framing is distinct from org-wide scope (L45); in R10 because authoritative research (Brynjolfsson NBER, Dell'Acqua jagged-frontier, Noy-Zhang) grounds the practice regardless of posting-frequency signal, and the market is expected to codify the risk as adoption matures.

**Grounding references.** Alongside live evidence, the catalog is grounded in authoritative public references across:

- **Management foundations** — [Grove, 'High Output Management'](https://www.hachettebookgroup.com/titles/andrew-s-grove/high-output-management/9780679762881/); [Fournier, 'The Manager's Path'](https://www.oreilly.com/library/view/the-managers-path/9781491973882/); [Larson, 'An Elegant Puzzle'](https://press.stripe.com/an-elegant-puzzle); [Zhuo, 'The Making of a Manager'](https://www.juliezhuo.com/book/manager.html); [Google re:Work manager behaviours (Project Oxygen)](https://rework.withgoogle.com/guides/managers-identify-what-makes-a-great-manager/); [Edmondson, 'The Fearless Organization' (psychological safety)](https://fearlessorganization.com/the-fearless-organization-book); [Westrum culture typology (BMJ 2004)](https://qualitysafety.bmj.com/content/13/suppl_2/ii22); [Lencioni, 'Death by Meeting'](https://www.tablegroup.com/product/death-by-meeting/).
- **Productivity / developer experience** — [DORA research reports](https://dora.dev/research/); [Forsgren, Humble, Kim — 'Accelerate'](https://itrevolution.com/product/accelerate/); [Forsgren et al. 'SPACE of Developer Productivity' (ACM Queue)](https://queue.acm.org/detail.cfm?id=3454124); [DX Core 4 framework](https://getdx.com/research/measuring-developer-productivity-with-the-dx-core-4/); [Kersten 'Project to Product' (flow metrics)](https://projecttoproduct.org/).
- **AI-at-work empirical research** — [Peng et al. 'The Impact of AI on Developer Productivity: Evidence from GitHub Copilot' (arXiv:2302.06590)](https://arxiv.org/abs/2302.06590); [Ziegler et al. 'Measuring GitHub Copilot's Impact on Productivity' (Commun. ACM)](https://cacm.acm.org/research/measuring-github-copilots-impact-on-productivity/); [Noy & Zhang 'Experimental evidence on the productivity effects of generative artificial intelligence' (Science 2023)](https://www.science.org/doi/10.1126/science.adh2586); [Brynjolfsson, Li, Raymond 'Generative AI at Work' (NBER)](https://www.nber.org/papers/w31161); [Dell'Acqua et al. 'Navigating the Jagged Technological Frontier' (BCG + HBS)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321); [MIT Sloan Management Review AI research](https://sloanreview.mit.edu/topic/ai/).
- **Industry surveys** — [Microsoft Work Trend Index](https://www.microsoft.com/en-us/worklab/work-trend-index); [McKinsey 'State of AI'](https://www.mckinsey.com/capabilities/quantumblack/our-insights/the-state-of-ai); [Gartner AI research](https://www.gartner.com/en/topics/artificial-intelligence); [OECD future of work](https://www.oecd.org/future-of-work/); [WEF Future of Jobs 2025](https://www.weforum.org/publications/the-future-of-jobs-report-2025/); [GitHub Octoverse](https://github.blog/news-insights/octoverse/); [Stack Overflow Developer Survey](https://survey.stackoverflow.co/).
- **Team review / standards-as-code conventions** — [Cursor Rules for AI coding agents](https://docs.cursor.com/context/rules-for-ai); [AGENTS.md convention](https://agents.md/); [Model Context Protocol (MCP)](https://modelcontextprotocol.io/); [Google Agent-to-Agent protocol](https://google.github.io/A2A/).
- **Eval & observability** — [G-Eval (arXiv:2303.16634)](https://arxiv.org/abs/2303.16634); [Promptfoo](https://www.promptfoo.dev/docs/intro); [LangSmith](https://docs.smith.langchain.com/); [Inspect AI (UK AISI)](https://inspect.aisi.org.uk/).
- **AI governance at team scope** — [NIST AI RMF 1.0 (AI 100-1)](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf) + [Playbook](https://airc.nist.gov/AI_RMF_Knowledge_Base/Playbook); [ISO/IEC 42001:2023 (AI management system)](https://www.iso.org/standard/81230.html); [EU AI Act (Regulation 2024/1689)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) — primary focus on **Article 4 (AI literacy)**, Article 14 (human oversight), Article 50 (transparency); [EU AI Office guidance](https://digital-strategy.ec.europa.eu/en/policies/ai-act); [Microsoft Responsible AI Standard](https://www.microsoft.com/en-us/ai/responsible-ai); [Google AI Principles](https://ai.google/responsibility/principles/); [OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/); [IAPP AI Governance Professional body of knowledge](https://iapp.org/certify/aigp/).
- **Hiring with AI compliance** — [US EEOC guidance on AI in employment](https://www.eeoc.gov/laws/guidance/select-issues-assessing-adverse-impact-software-algorithms-and-artificial); [NYC Local Law 144 AEDT bias audits](https://www.nyc.gov/site/dca/about/automated-employment-decision-tools.page); [SHRM AI-in-HR resources](https://www.shrm.org/topics-tools/topics/artificial-intelligence); [Josh Bersin AI-in-L&D research](https://joshbersin.com/category/ai-in-hr/); [Google re:Work structured interviews](https://rework.withgoogle.com/guides/unbiasing-raise-awareness/).
- **Incident response (adapted for AI)** — [Google SRE Blameless Postmortem Culture](https://sre.google/sre-book/postmortem-culture/); [Allspaw 'Blameless Post-Mortems'](https://www.etsy.com/codeascraft/blameless-postmortems/); [AI Incident Database](https://incidentdatabase.ai/); [OECD.AI AI Incidents Monitor](https://oecd.ai/en/incidents).

Every requirement in the catalog cites ≥1 such reference, and every requirement is shaped so posting-frequency evidence can be refined underneath it without restructure.

## Methodology

1. Sampled 25 live job postings across adjacent-title matches for AI-augmented people-manager work in the 2026-08-06 → 2026-11-04 window, drawn from Greenhouse, Ashby, Lever, Workday, BuiltIn, and employer career sites.
2. Extracted verbatim requirement bullets per posting; normalised into 15 requirement themes (5 above the 0.30 posting-frequency threshold, 5 below but kept at team scope with rationale, 5 explicit prereq / peer / higher-level link-outs).
3. Mapped each theme to (a) the role on the level ladder that should own it primarily and (b) the curriculum module that will cover it.
4. Applied the **ownership rule** — assign coverage to the lowest-level role that genuinely requires the skill; higher-level tracks link back rather than duplicate. In particular, deferred:
   - *Down* to `ai-governance-analyst` (level 15) for operational governance legwork (crosswalks, intake, impact-assessment drafting); to `ai-augmented-analyst` (level 20) and `ai-assisted-software-engineer` (level 25) for IC-scope AI-augmented work the team practices; and to a generic people-management background (Grove, Fournier, Larson, Zhuo) that is listed in `PREREQUISITES.md` but not re-taught.
   - *Sideways* to `ai-augmented-product-manager` (peer, level 30, AI Workforce family) for AI-feature product scope and ROI framing.
   - *Sideways* to `ai-risk-engineer` (peer, level 25, AI Governance family) for engineered risk-eval / guardrail / red-team depth — managers commission and act, don't re-build.
   - *Sideways* to `ai-infra-team-lead` (peer / lower-adjacent, level 35, Infra family) for infra-team-lead-specific delivery depth — this track stays discipline-agnostic.
   - *Up* to `ai-enablement-lead` (level 45, AI Workforce family) for org-wide enablement programs, multi-team coordination, and procurement at scale.
   - *Up* to `ai-engineering-manager` (level 50) for engineering-manager-of-managers scope and cross-team engineering management; to `senior-ai-governance-architect` (level 50) for control-library architecture; to `head-of-ai-governance` (level 60) for governance program leadership; to `chief-ai-officer` (level 70) for executive scope.
   - *Out of scope* to legal counsel (no legal opinion), to HR / employee-relations partners (formal employment actions), and to security-operations / DFIR (SOC-side incident handling).
5. Flagged below-threshold themes for the next refresh cycle to monitor; kept each in a dedicated module where authoritative research grounds the practice.

## Requirement themes → curriculum ownership

The table below lists each requirement theme, its posting frequency this cycle (n=25), its planned owner per the level hierarchy, and the curriculum coverage path.

| # | Theme | Freq | Owner role | Coverage |
|---|---|---|---|---|
| R1 | Drive team-level AI tool adoption and workflow redesign — own the team's AI-adoption roadmap, sequence pilots vs. rollouts, partner with Platform / DevEx, run change management | 0.76 | `ai-augmented-team-manager` (this) | [`mod-102-team-ai-adoption-and-roadmap`](lessons/mod-102-team-ai-adoption-and-roadmap) |
| R2 | Set review standards and accountability model for AI-generated work — PR / review checklists, standards-as-code (Cursor rules, AGENTS.md, ADRs, lint policies), 'AI generates, humans own' contract | 0.60 | `ai-augmented-team-manager` | [`mod-103-review-standards-and-eval-commissioning`](lessons/mod-103-review-standards-and-eval-commissioning) |
| R3 | Commission evaluation frameworks for AI output at SDLC / workflow level — golden tasks, regression sets, LLM-as-judge, replay; decide what to evaluate and act on findings | 0.44 | `ai-augmented-team-manager` | [`mod-103-review-standards-and-eval-commissioning`](lessons/mod-103-review-standards-and-eval-commissioning) (folded with R2 — ~40% content overlap) |
| R4 | Measure team productivity, cost, and AI ROI — DX Core 4 / SPACE / DORA under AI-augmented conditions, token / seat cost tracking, adoption-vs-activation, AI-ROI narrative to leadership | 0.40 | `ai-augmented-team-manager` | [`mod-104-productivity-measurement-and-ai-roi`](lessons/mod-104-productivity-measurement-and-ai-roi) |
| R5 | Design and run team-level AI enablement programs — Day 0 / 30 / 60 / 90, bootcamps, workshops, communities of practice, tool-budget distribution, fluency measurement | 0.36 | `ai-augmented-team-manager` | [`mod-105-team-ai-enablement-programs`](lessons/mod-105-team-ai-enablement-programs) |
| R6 | AI vendor and tool governance at team scope — procurement, build-vs-buy, tool registry, cost control, data-handling guarantees | 0.28 | `ai-augmented-team-manager` | [`mod-111-vendor-budget-and-tool-selection-at-team-scope`](lessons/mod-111-vendor-budget-and-tool-selection-at-team-scope) (below-threshold; kept because team-scope framing distinct from L45) |
| R7 | SDLC workflow redesign and agent delegation — human + agent routing, AGENTS.md authoring, tool-authorisation policy, delegation ladder | 0.28 | `ai-augmented-team-manager` | [`mod-106-workflow-redesign-and-agent-delegation`](lessons/mod-106-workflow-redesign-and-agent-delegation) (below-threshold; kept because research-grounded) |
| R8 | Build and operate internal agents — IC-mechanics of agent authoring | 0.24 | `ai-assisted-software-engineer` (level 25) | Linked out; not re-taught |
| R9 | AI-era workforce planning (team size, role-mix, hiring, levelling under AI augmentation) | 0.16 | `ai-augmented-team-manager` (team-scope only) | [`mod-108-hiring-performance-and-feedback-with-ai-in-the-loop`](lessons/mod-108-hiring-performance-and-feedback-with-ai-in-the-loop) (cross-team scope defers upward) |
| R10 | Prevent skill atrophy and preserve judgment — deliberate practice, career-development ladder under AI augmentation | 0.08 | `ai-augmented-team-manager` | [`mod-107-skill-growth-anti-atrophy-and-career-development`](lessons/mod-107-skill-growth-anti-atrophy-and-career-development) (below-threshold; research-grounded) |
| R11 | AI-assisted IC-level engineering / analyst work — Cursor / Copilot / Claude Code fluency at IC tier | (prereq) | `ai-assisted-software-engineer` (level 25) / `ai-augmented-analyst` (level 20) | Listed in [`PREREQUISITES.md`](PREREQUISITES.md); not re-taught |
| R12 | General people-management fundamentals — 1:1s, feedback, hiring, performance, budget | (prereq) | General management background | Listed in [`PREREQUISITES.md`](PREREQUISITES.md); not re-taught |
| R13 | Engineered AI risk, red-team, and guardrail depth (team consumes) | (peer) | `ai-risk-engineer` (level 25, AI Governance family) | Commissioning contract in [`mod-103`](lessons/mod-103-review-standards-and-eval-commissioning); engineering depth linked out |
| R14 | Org-wide AI enablement programs beyond a single team | (higher) | `ai-enablement-lead` (level 45) | Hand-off contract in [`mod-105`](lessons/mod-105-team-ai-enablement-programs) and [`mod-102`](lessons/mod-102-team-ai-adoption-and-roadmap); depth linked out |
| R15 | AI governance program leadership, board reporting, regulator engagement | (higher) | `head-of-ai-governance` (level 60) / `chief-ai-officer` (level 70) | Linked out |

## Curriculum modules not directly R-indexed

These modules are not a 1:1 mapping of a requirement theme but cover authoritative-reference-grounded scope required at level 40:

| Module | Scope | Grounding |
|---|---|---|
| [`mod-101-ai-augmented-team-manager-position-and-contract`](lessons/mod-101-ai-augmented-team-manager-position-and-contract) | Role position, level-40 scope, ownership rule, manager-output fundamentals, human/machine contract | Grove, Fournier, Larson, Zhuo; Google re:Work |
| [`mod-109-accountability-incident-response-and-blameless-postmortems`](lessons/mod-109-accountability-incident-response-and-blameless-postmortems) | Accountability for AI-produced work; AI-incident triage and post-mortem at team scope | Google SRE, Allspaw; AI Incident Database, OECD.AI Incidents Monitor |
| [`mod-110-ai-governance-and-policy-at-team-scope`](lessons/mod-110-ai-governance-and-policy-at-team-scope) | NIST AI RMF GOVERN → team practice; EU AI Act Article 4 AI literacy at team scope; Microsoft RAI / Google AI Principles mapping | NIST AI RMF + Playbook; EU AI Act; MS RAI Standard; Google AI Principles; OWASP LLM Top 10; IAPP AIGP |
| [`mod-112-cross-functional-leadership-and-ritual-calendar`](lessons/mod-112-cross-functional-leadership-and-ritual-calendar) | Ritual calendar, cross-functional partnering, exec communication, one-pager / decision-log hygiene, certifications portfolio | Lencioni; Google re:Work manager behaviours; IAPP AIGP |

## Posting evidence

25 postings sampled 2026-08-06 → 2026-11-04; 7 in-window, 14 live-but-undated, 4 outside-window language exemplars. See [`.aicg/job-requirements.json`](.aicg/job-requirements.json) `postings` for full verbatim bullets.

| # | Employer | Title | Location | Posted | Seniority |
|---|---|---|---|---|---|
| [p-01](https://careers.speedinvest.com/companies/dialpad/jobs/75794817-engineering-manager-ai-transformation) | Dialpad | Engineering Manager, AI Transformation | Buenos Aires | 2026-04 | language exemplar |
| [p-02](https://www.purpose.jobs/discover/companies/duo-security/jobs/74538910-sr-director-ai-engineering-security-business-group) | Duo Security (Cisco) | Sr. Director — AI Engineering Productivity and Developer Experience | San Jose, CA | 2026-04-16 | L45+ supplementary |
| [p-03](https://careers.harvard.edu/job/ai-enablement-lead-in-cambridge-ma-united-states-jid-1456) | Harvard University (HUIT) | AI Enablement Lead | Cambridge, MA | 2026-10-15 | L40 in-window |
| [p-04](https://builtin.com/job/engineering-manager-developer-productivity-ai/8896574) | Stripe | Engineering Manager, Developer Productivity AI | Remote US | (removed 2026-07-23) | language exemplar |
| [p-05](https://job-boards.greenhouse.io/figma/jobs/6008752004) | Figma | Manager, Software Engineering — DevEx AI Tools | SF / NYC / Remote | undated_but_live | L40 |
| [p-06](https://builtin.com/job/engineering-manager-ai-enablement/9704963) | Grow Therapy | Engineering Manager, AI Enablement | NYC / SF / Seattle | undated_but_live | L40 |
| [p-07](https://careers.servicenow.com/jobs/744000148624764/senior-ai-engineering-enablement-lead/) | ServiceNow | Senior AI Engineering Enablement Lead | Santa Clara, CA | 2026-09-09 | L40 in-window |
| [p-08](https://www.klaviyo.com/careers/jobs/7801432003) | Klaviyo | AI Enablement Program Manager | Boston, MA | undated_but_live | L40 |
| [p-09](https://job-boards.greenhouse.io/verkada/jobs/5198815007) | Verkada | Engineering Manager, Agentic Workflows | San Mateo, CA | 2026-09-28 | L40 in-window |
| [p-10](https://www.dreamworkhq.com/job/d86efaf3-f4fe-4844-a43f-f5784a0adb5d) | MGM Resorts International | Director, AI-Enabled Engineering | Las Vegas, NV | 2026-10 | L45+ supplementary |
| [p-11](https://jobs.ashbyhq.com/rescale/b95879d6-184f-43be-b73f-682d910d5964) | Rescale | Senior Software Engineering Manager, Core Cloud Compute — AI | Remote US | undated_but_live | L40 |
| [p-12](https://jobs.ashbyhq.com/scan-com/60081ce4-636f-4634-be6a-7a67080acd0f) | Scan.com | Senior Engineering Manager | New York, NY | undated_but_live | L40 |
| [p-13](https://jobs.ashbyhq.com/Tremendous/36365a33-9969-44f7-a8da-7ff24f386c34) | Tremendous | Engineering Manager | Remote (NYC HQ) | undated_but_live | L40 |
| [p-14](https://jobs.ashbyhq.com/palo-it/ef50d64f-5525-4386-a48f-3361a04cbb3e) | PALO IT | Lead Forward Deployed Engineer | Sydney / Singapore | undated_but_live | L40 |
| [p-15](https://jobs.generalcatalyst.com/companies/instacart/jobs/58981058-senior-software-engineering-manager-ai-developer-productivity) | Instacart | Senior Software Engineering Manager, AI & Developer Productivity | Remote US | 2026-05 | language exemplar |
| [p-16](https://careers.airbnb.com/positions/8316130/) | Airbnb | Manager, Engineering, Dev AI | Remote US | undated_but_live | L40 |
| [p-17](https://www.indexventures.com/startup-jobs/datadog/manager-i-engineering-ai-developer-products/) | Datadog | Manager I, Engineering — AI Developer Products | Paris, FR | undated_but_live | L40 |
| [p-18](https://careers.datadoghq.com/detail/8212114/) | Datadog | Manager II, Engineering — Database Monitoring (AI) | New York, NY | undated_but_live | L40 |
| [p-19](https://freehire.me/jobs/ai-enablement-lead-software-engineering-nsw-land-registry-services-ed76vj44) | NSW Land Registry Services | AI Enablement Lead — Software Engineering | Sydney, AU | 2026-10-23 | L40 in-window |
| [p-20](https://careers.franciscopartners.com/companies/symplr/jobs/74011052-senior-staff-software-engineer-ai-enablement-lead) | symplr | Senior Staff SWE — AI Enablement Lead | Bengaluru, IN | 2026-02-16 | language exemplar |
| [p-21](https://careers.mheducation.com/jobs/7165) | McGraw Hill | Director, Engineering — AI Enablement | Remote US | undated_but_live | L45+ supplementary |
| [p-22](https://jobs.nvidia.com/careers/job/893392478748) | NVIDIA | Director, AI Enablement | Santa Clara, CA | undated_but_live | L45+ supplementary |
| [p-23](https://www.dreamworkhq.com/job/383e8d9b-8376-4e8d-8510-9e564235567d) | Rocket Companies | Software Engineering Manager — AI Enablement and Developer Tooling | Detroit, MI | 2026-11-03 | L40 in-window |
| [p-24](https://jobs.lever.co/goodleap/880a10a8-1cdc-49d3-a0b6-108eb81057d8) | GoodLeap | Engineering Manager, AI Transformation | Remote US | undated_but_live | L40 |
| [p-25](https://freehire.me/jobs/senior-engineering-manager-applied-ai-hearstlab-mm77ypuq) | HearstLab (Hearst) | Senior Engineering Manager, Applied AI | New York, NY | 2026-11-01 | L45+ supplementary |

**Reading notes.** The 25-posting sample skews toward engineering-team management because the market is codifying the manager deliverables for engineering teams first. The same role exists in design, analytics, legal-ops, customer-support, and knowledge-work teams but is not yet as frequently titled-and-posted. Authoritative references (Microsoft Work Trend Index, McKinsey State of AI, MIT Sloan Management Review, OECD AI-at-work briefings) ground the curriculum beyond engineering so the track stays discipline-agnostic.

## Ownership map — quick reference for next cycle

When backfilling postings, use this ownership decision to keep the curriculum from drifting into peer territory:

- **AI Governance Analyst** (level 15, `ai-governance-analyst-learning`) — operational analyst work (intake, inventory, crosswalks). <!-- needs-research: confirm final level assignment once ai-governance-analyst `role_level` locks. -->
- **AI-Augmented Analyst** (level ~20, `ai-augmented-analyst-learning`) — IC-scope AI-augmented analyst work. <!-- needs-research: role_level pending; confirm against `ai-augmented-analyst-learning/.aicg/job-requirements.json` when that file is populated. -->
- **AI-Assisted Software Engineer** (level ~25, `ai-assisted-software-engineer-learning`) — IC-scope AI-augmented engineering work; agents authored by this track's reports. <!-- needs-research: role_level pending. -->
- **AI Risk Engineer** (level 25, `ai-risk-engineer-learning`) — engineered AI risk / red-team / guardrail depth. Managers commission and act on the evidence.
- **AI-Augmented Team Manager** (this track, level 40, AI Workforce family) — team-scale operating system for AI-augmented work.
- **AI-Augmented Product Manager** (peer, level 30, `ai-augmented-product-manager-learning`) — product-side AI-feature scope and ROI framing. <!-- needs-research: role_level pending. -->
- **AI Infra Team Lead** (peer / lower-adjacent, level 35, `ai-infra-team-lead-learning`) — infra-specific team-lead delivery depth.
- **AI Enablement Lead** (level 45, `ai-enablement-lead-learning`) — org-wide enablement programs. This role hands off upward when scope exceeds a single team. <!-- needs-research: role_level pending. -->
- **AI Engineering Manager** (level 50, `ai-engineering-manager-learning`) — engineering-manager-of-managers scope. <!-- needs-research: role_level pending. -->
- **Senior AI Governance Architect** (level 50) — control-library architecture.
- **Head of AI Governance** (level 60) / **Chief AI Officer** (level 70) — governance and executive scope.

## Salary evidence

<!-- needs-research: salary coverage. None of the 25 postings sampled on 2026-11-04 rendered a verbatim salary range in server-side HTML. Pay-transparency obligations in CA / NY / CO / WA state-filtered US postings suggest the band was published on the ATS detail page via client-side rendering and was not captured by this cycle's crawl. Next cycle: fan out to Lever / Workday tenants whose salary bands render server-side; cross-reference Levels.fyi, Glassdoor (with provenance caveats), and Candor data. Do not quote a headline aggregate until live-posting salary coverage reaches n≥8. -->

## Below-threshold themes — tracked for next cycle

| # | Theme | Freq | Rationale for current treatment |
|---|---|---|---|
| R6 | Vendor + tool governance | 0.28 | Kept in [`mod-111`](lessons/mod-111-vendor-budget-and-tool-selection-at-team-scope) at team scope; org-wide procurement defers to `ai-enablement-lead` (level 45). |
| R7 | Workflow redesign + agent delegation | 0.28 | Kept in [`mod-106`](lessons/mod-106-workflow-redesign-and-agent-delegation) because the authoritative research (Dell'Acqua jagged-frontier) makes it non-obviously load-bearing even at 0.28 posting-frequency. |
| R9 | AI-era workforce planning | 0.16 | Covered at team-scope only in [`mod-108`](lessons/mod-108-hiring-performance-and-feedback-with-ai-in-the-loop); cross-team scope defers upward. |
| R10 | Skill atrophy / career development | 0.08 | Kept in [`mod-107`](lessons/mod-107-skill-growth-anti-atrophy-and-career-development) because the empirical research (Brynjolfsson NBER, Dell'Acqua, Noy-Zhang) grounds the practice; frequency expected to rise as the market codifies the risk. |

Watch all four themes on the next refresh — any crossing 0.30 justifies promoting its scope or splitting its coverage from the folded-in treatment.

## Next cycle to-do

- Widen beyond engineering-team manager postings to (a) design-team managers, (b) analytics / data-team managers, (c) customer-support team leads, (d) legal-ops / knowledge-work team managers.
- Pick up IAPP AIGP-oriented team-manager postings (frequently crosses into ai-governance-analyst framing but is team-manager-scope).
- Chase live salary data via server-side-rendered ATS tenants (Lever, Workday); aim for n≥8 with published salary before next headline aggregate.
- Watch R6, R7, R9, R10 frequency; reassess scope if any crosses 0.30.
- Lock the level numbers for `ai-augmented-analyst`, `ai-assisted-software-engineer`, `ai-augmented-product-manager`, `ai-enablement-lead`, `ai-engineering-manager` once those packets land, and update the `<!-- needs-research -->` markers in this file.
