# Prerequisites — AI-Augmented Team Manager track

**Role level:** 40 (team manager, AI Workforce family)
**Track:** `ai-augmented-team-manager-learning`

This track is a people-manager specialty layered on top of three load-bearing prior experiences: (a) general people-management fundamentals, (b) IC-scope AI-augmented work (enough to be hands-on, not enough to out-ship your team), and (c) working familiarity with the AI-governance vocabulary. Those fundamentals are **not** re-taught here — the modules step directly onto team-level adoption roadmaps, review norms, productivity measurement, agent delegation, accountability, and governance translation at team scope.

## Assumed lower-level curriculum

Complete or be practically fluent in the equivalent of these lower-level tracks before starting:

- **General people-management fundamentals** — this track assumes you have run 1:1s, given feedback, hired at least once, run a quarterly planning cycle, and owned a team budget. If you have never done any of that, start with the recommended reading list below rather than this track. There is no project-internal "ai-people-management-101" prerequisite — people management is a cross-domain discipline the industry teaches through practice, mentorship, and the four texts in [Recommended reading](#recommended-reading-before-starting).
- **[`ai-assisted-software-engineer-learning`](https://github.com/ai-engineering-curriculum/ai-assisted-software-engineer-learning)** — IC-scope AI-augmented engineering fluency (Cursor / Copilot / Claude Code / Promptfoo / LangSmith / basic agent authoring). The manager inherits team members from this track and must stay hands-on enough to review and model good practice. <!-- needs-research: lock the exact role_level on that packet when it lands; current estimate ~25. -->
- **[`ai-augmented-analyst-learning`](https://github.com/ai-workforce-curriculum/ai-augmented-analyst-learning)** — IC-scope AI-augmented analyst fluency where the team does analytics / data work. <!-- needs-research: role_level pending. -->
- **[`ai-governance-analyst-learning`](https://github.com/ai-governance-curriculum/ai-governance-analyst-learning) — level 15** — operational analyst work in the AI Governance family: AI use-case intake and triage, model / AI-system inventory, NIST AI RMF and EU AI Act framework crosswalks, first-draft impact assessments, jurisdictional regulatory tracking, model / system / dataset card authoring at analyst tier. This role *consumes* that legwork and sets team-scope policy on top of it.

## Assumed working knowledge

Even without holding the equivalent role formally, you should be practically fluent in:

- **Running a team** — 1:1 cadence, feedback loops, performance management, quarterly planning, hiring, budget ownership, interview-loop design, promotion-case authoring. If any of these are new, pair this track with the four texts in [Recommended reading](#recommended-reading-before-starting).
- **Hands-on AI tool fluency** — use an AI coding assistant (Cursor, Claude Code, Copilot) and an AI knowledge-work tool (ChatGPT / Claude / Gemini / NotebookLM) in your own work weekly. Use Promptfoo or LangSmith enough to read an eval report and ask the right questions. Enough to review — not to out-ship your team.
- **A software-development context** — version control, pull-request workflow, CI / CD vocabulary at team-manager altitude. The track uses engineering-team examples heavily because the market codifies those deliverables first; non-engineering managers should translate the examples into their own discipline's equivalents.
- **Reading and writing policy at team scope** — team charters, ADRs, ritual calendars, exec one-pagers, decision logs. If you have never authored or maintained a team-scope policy artifact, mod-101 will feel abstract.
- **Basic statistics and measurement literacy** — reading a dashboard, choosing a metric under which you will be judged, defending your choice to an exec. This track covers DX Core 4 / SPACE / DORA at measurement-literacy depth rather than statistical-methodology depth; deep methodology is linked out to `model-evaluation-engineer` (level 30, ML Engineering family).
- **AI-governance vocabulary** — NIST AI RMF (GOVERN / MAP / MEASURE / MANAGE functions), EU AI Act high-risk categories, ISO/IEC 42001 management-system shape, OWASP Top 10 for LLM Applications. You should be able to open the NIST AI RMF Playbook and understand what GOVERN sub-category 1.1 is asking for without getting lost.

## Not assumed, taught here

You do **not** need prior experience with:

- Any specific AI-adoption framework for team scope — mod-102 covers the team roadmap.
- Any specific review-standards-as-code convention — Cursor rules files, AGENTS.md, ADR templates, lint-as-policy. Mod-103 covers the working set.
- Any specific eval framework at the commissioning tier — G-Eval / Promptfoo / LangSmith / Inspect AI. Mod-103 covers the commissioning contract; IC-mechanics defer to `ai-assisted-software-engineer` (level ~25).
- Any specific productivity framework under AI augmentation — DX Core 4 / SPACE / DORA / Kersten flow metrics. Mod-104 covers the working set and the empirical literature.
- Enablement-program design at team scope — Day 0 / 30 / 60 / 90 structure, bootcamp and workshop authoring. Mod-105 covers it.
- Agent-delegation patterns at team scope — AGENTS.md delegation ladder, MCP tool-authorisation policy, Google Agent-to-Agent working fluency. Mod-106 covers it.
- The specific research on AI-induced skill distribution (Brynjolfsson NBER, Noy-Zhang Science, Dell'Acqua jagged-frontier) — mod-107 covers reading and policy translation.
- Interview-loop redesign for AI-augmented candidates — mod-108 covers it.
- Blameless post-mortem adaptation for AI-produced incidents — mod-109 covers it.
- NIST AI RMF GOVERN translation to team practice, EU AI Act Article 4 AI-literacy obligation, Microsoft Responsible AI Standard / Google AI Principles mapping — mod-110 covers them.
- Vendor evaluation and build-vs-buy at team scope — mod-111 covers the working set.
- Ritual-calendar design and cross-functional partnership patterns under AI augmentation — mod-112 covers them.

## Recommended reading before starting

The four texts below are *the* assumed baseline — the track layers AI-augmentation onto them. Read them first if any are new:

- [Andrew S. Grove, *High Output Management*](https://www.hachettebookgroup.com/titles/andrew-s-grove/high-output-management/9780679762881/) — manager-output model, meetings, 1:1s, leverage.
- [Camille Fournier, *The Manager's Path*](https://www.oreilly.com/library/view/the-managers-path/9781491973882/) — line-manager through engineering-lead playbook; transferable beyond engineering.
- [Will Larson, *An Elegant Puzzle: Systems of Engineering Management*](https://press.stripe.com/an-elegant-puzzle) — systems-of-management framing (team sizing, hiring loops, planning systems).
- [Julie Zhuo, *The Making of a Manager*](https://www.juliezhuo.com/book/manager.html) — first-time manager playbook; feedback, trust, meetings.

Plus two psychological-safety and productivity-research references that come up again and again in-track:

- [Amy Edmondson, *The Fearless Organization*](https://fearlessorganization.com/the-fearless-organization-book) — canonical psychological-safety text; used in mod-107 and mod-109.
- [Forsgren, Humble, Kim, *Accelerate*](https://itrevolution.com/product/accelerate/) + the [SPACE framework (ACM Queue 2021)](https://queue.acm.org/detail.cfm?id=3454124) + the [DX Core 4 framework](https://getdx.com/research/measuring-developer-productivity-with-the-dx-core-4/) — productivity measurement grounding for mod-104.

## Not required, useful to have

- Prior work with an eval-tooling platform (Promptfoo, LangSmith, Arize Phoenix, Langfuse, Inspect AI) — IC depth belongs to `ai-assisted-software-engineer` (level ~25) and `ai-eval-engineer` (level 30, AI Engineering family). Managers benefit from being able to read an eval report.
- Prior work with a GRC-for-AI / AI governance platform (Credo AI, Holistic AI, ModelOp) — mod-110 walks the platforms at manager-fluency depth.
- [IAPP AI Governance Professional (AIGP)](https://iapp.org/certify/aigp/) certification — most-cited cross-functional AI-governance credential; shared vocabulary with legal, compliance, and risk partners.
- Prior reading of the NIST AI RMF 1.0 (AI 100-1) and NIST AI RMF Playbook — mod-110 teaches the translation to team practice; a prior read makes the module faster.
- A recent [Microsoft Work Trend Index](https://www.microsoft.com/en-us/worklab/work-trend-index) or [McKinsey State of AI](https://www.mckinsey.com/capabilities/quantumblack/our-insights/the-state-of-ai) report — grounds mod-102, mod-104, mod-107 context.

## Not in scope for this track (linked out)

- **IC-scope AI-augmented engineering, analysis, or writing work** — owned by [`ai-assisted-software-engineer-learning`](https://github.com/ai-engineering-curriculum/ai-assisted-software-engineer-learning) (level ~25) and [`ai-augmented-analyst-learning`](https://github.com/ai-workforce-curriculum/ai-augmented-analyst-learning) (level ~20). This track assumes IC fluency; it does not teach it. <!-- needs-research: role_level numbers pending on both packets. -->
- **Engineered AI risk-eval, red-team, and guardrail depth** — owned by [`ai-risk-engineer-learning`](https://github.com/ai-governance-curriculum/ai-risk-engineer-learning) (peer, level 25, AI Governance family). Managers commission and act on the evidence, don't re-build the rig.
- **Application-layer LLM / agent evaluation-engineering depth** — traces, judges, RAG eval, eval-gated CI/CD, online eval — owned by [`ai-eval-engineer-learning`](https://github.com/ai-engineering-curriculum/ai-eval-engineer-learning) (peer, level 30, AI Engineering family).
- **Statistical / benchmark / judge-vs-human calibration methodology depth** — owned by [`model-evaluation-engineer-learning`](https://github.com/ml-engineering-curriculum/model-evaluation-engineer-learning) (peer, level 30, ML Engineering family).
- **Org-wide AI enablement programs, multi-team coordination, procurement at scale** — owned by [`ai-enablement-lead-learning`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) (level 45). Single-team scope stays here. <!-- needs-research: role_level pending. -->
- **Engineering-specific manager-of-managers scope** — owned by [`ai-engineering-manager-learning`](https://github.com/ai-engineering-curriculum/ai-engineering-manager-learning) (level 50). <!-- needs-research: role_level pending. -->
- **Control-library architecture, policy taxonomy, cross-jurisdiction reconciliation** — owned by [`senior-ai-governance-architect-learning`](https://github.com/ai-governance-curriculum/senior-ai-governance-architect-learning) (level 50).
- **AI governance program leadership, board-level reporting, regulator engagement** — owned by [`head-of-ai-governance-learning`](https://github.com/ai-governance-curriculum/head-of-ai-governance-learning) (level 60) and [`chief-ai-officer-learning`](https://github.com/ai-governance-curriculum/chief-ai-officer-learning) (level 70).
- **Frontier-agent red-team methodology and dangerous-capability evaluation** — owned by [`agentic-safety-engineer-learning`](https://github.com/ai-governance-curriculum/agentic-safety-engineer-learning) (level 40, AI Governance family).
- **Legal opinion** — out of scope; routed to counsel.
- **Formal employment actions (PIP, termination, compensation calibration)** — this track covers the manager-side framing; formal actions route through HR / employee-relations partners.
- **SOC-side incident handling** — out of scope; this role feeds AI-specific signal to SecOps.
