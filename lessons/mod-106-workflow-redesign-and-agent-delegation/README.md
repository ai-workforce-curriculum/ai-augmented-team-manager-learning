# mod-106 — Workflow Redesign and Agent Delegation at Team Scope

**Estimated effort:** 16 hours.

## What this module does

Turns the AI-augmented team's day-to-day work from *"we use the tools"* into **a redesigned workflow with explicit routing between AI, junior human, and senior human**, with an **authored delegation ladder**, **human-in-the-loop checkpoints** in the places the research says you need them, and a **tool-authorisation policy** that names which agent actions are permitted unattended and which require a human to approve. Reads [Dell'Acqua et al., *Navigating the Jagged Technological Frontier* (BCG + HBS, Sept 2023)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321) as the empirical anchor for the routing decision, then operationalises the first-order finding (above the frontier AI helps, below the frontier AI hurts) and the second-order finding (AI-augmented workers shift their effort to work AI cannot do). Reads the [AGENTS.md convention](https://agents.md/), the [Model Context Protocol (MCP)](https://modelcontextprotocol.io/), and the [Google Agent-to-Agent (A2A) protocol](https://a2a-protocol.org/) at the *manager-fluency bar* — enough to set policy, not to implement the server. Draws the ownership boundary against the IC-mechanics track ([`ai-assisted-software-engineer`](https://github.com/ai-engineering-curriculum/ai-assisted-software-engineer-learning), level 25) below and the frontier-safety track ([`agentic-safety-engineer`](https://github.com/ai-governance-curriculum/agentic-safety-engineer-learning), level 40, AI Governance family) sideways.

## Learning objectives

- Redesign team workflows for human + agent hybrid work — pick what routes to AI vs. junior human vs. senior human, author the delegation ladder, set human-in-the-loop checkpoints — grounded in [Dell'Acqua et al.'s](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321) jagged-frontier framing (R7, 0.28 — below strict threshold but anchored by authoritative research).
- Author agent-delegation patterns at team scope — AGENTS.md conventions, delegation contracts, tool-authorisation policy — including when an agent is permitted to call tools unattended vs. when a human must approve.
- Read and apply the Model Context Protocol (MCP) and Google Agent-to-Agent (A2A) protocol at the manager-fluency bar — enough to set tool-authorisation policy, not to implement the server.
- Decide where the team's highest-value human attention goes once AI takes over the routine slice — Dell'Acqua's second-order finding that AI-augmented workers shift to tasks AI can't do well.
- Position the ownership boundary: agent-construction IC mechanics live at `ai-assisted-software-engineer` (level 25, AI Engineering family); frontier-agent safety depth lives at `agentic-safety-engineer` (level 40, AI Governance family).

## Chapters

1. [Chapter 1 — The jagged frontier and why this module exists](01-the-jagged-frontier-and-why-this-module-exists.md) — Dell'Acqua et al. as the research anchor; R7 (0.28) as the posting evidence; the five pieces of mod-106.
2. [Chapter 2 — The task-routing decision: AI, junior human, senior human](02-the-task-routing-decision.md) — the three destinations; the routing rule derived from the jagged frontier; the matrix; the three mis-routing failure modes.
3. [Chapter 3 — Authoring the delegation ladder](03-authoring-the-delegation-ladder.md) — the delegation ladder as a managerial artifact, levels adapted for human + agent work, irrevocability as the breaking change.
4. [Chapter 4 — Human-in-the-loop checkpoints](04-human-in-the-loop-checkpoints.md) — the four kinds of HITL (pre-invocation approval, mid-run gate, post-generation review, periodic audit), grounded in EU AI Act Article 14 and NIST AI RMF MANAGE.
5. [Chapter 5 — AGENTS.md and the team-scope delegation contract](05-agents-md-and-team-scope-conventions.md) — the AGENTS.md convention, delegation-contract fields, how they compose with the mod-101 human/machine contract.
6. [Chapter 6 — MCP, A2A, and the tool-authorisation policy](06-mcp-a2a-and-tool-authorisation-policy.md) — one-pass reads of MCP and A2A at manager-fluency; the unattended-vs-approved tool-authorisation policy.
7. [Chapter 7 — The post-automation attention shift](07-the-post-automation-attention-shift.md) — Dell'Acqua's second-order finding; redirecting high-value human attention; the risk of attention drift back to routine.
8. [Chapter 8 — Ownership boundaries: IC agent mechanics and frontier-agent safety](08-ownership-boundaries-ic-agent-work-and-frontier-safety.md) — what is `ai-assisted-software-engineer` (L25) work vs. what is `agentic-safety-engineer` (L40, AI Governance) work vs. what stays here.

## Exercises

1. [Exercise 01 — Task routing matrix for your team](exercises/exercise-01-task-routing-matrix-for-your-team.md) (3 h) — produce v0.1 of your team's routing matrix across 10 recurring task types.
2. [Exercise 02 — AGENTS.md and delegation contract](exercises/exercise-02-agents-md-and-delegation-contract.md) (3 h) — write a team-scope AGENTS.md v0.1 and the delegation contract that sits beside it.
3. [Exercise 03 — MCP tool-authorisation policy](exercises/exercise-03-mcp-tool-authorisation-policy.md) (2 h) — classify every tool your team's agents can call into one of four authorisation bands.
4. [Exercise 04 — Human-in-the-loop checkpoint design](exercises/exercise-04-human-in-the-loop-checkpoint-design.md) (3 h) — design HITL checkpoints for three real workflows on your team.
5. [Exercise 05 — Post-automation attention redirection plan](exercises/exercise-05-post-automation-attention-redirection-plan.md) (2 h) — write the one-pager naming where your team's highest-value human attention goes next.

Labs and quizzes are authored on subsequent cycles.

## Resources

Primary sources — Dell'Acqua et al.; AGENTS.md; MCP spec; Google A2A; EU AI Act Article 14; NIST AI RMF; OWASP LLM Top 10; Jurgen Appelo's seven levels of delegation; Google SRE on toil elimination; and the sibling-track catalogue — are listed in [`resources.md`](resources.md).

## Where this fits in the track

mod-106 sits between the *measurement* modules (mod-104 productivity, mod-105 enablement) and the *governance* modules (mod-109 incident response, mod-110 team-scope policy). It is the module that actually changes how the work is done.

- **Back-links.** The human/machine contract drafted in [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) Chapter 3 is the scope boundary this module operates inside. The review standards authored in [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) are the quality bar every delegation band in this module has to pass through. The productivity narrative in [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) is where the attention-redirection evidence from Chapter 7 lands.
- **Forward links.** The incident-response runbook in [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) treats an unattended-tool call that caused harm as a first-class incident class. The team-scope governance crosswalk in [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) folds this module's tool-authorisation policy into the policy registry. The vendor and budget work in [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) draws on the authorisation-band classification to decide which vendors are worth paying for at what scope.
- **Sideways links.** [`ai-assisted-software-engineer`](https://github.com/ai-engineering-curriculum/ai-assisted-software-engineer-learning) at level 25 owns the IC mechanics of actually building the agents this module routes work through. [`agentic-safety-engineer`](https://github.com/ai-governance-curriculum/agentic-safety-engineer-learning) at level 40 (AI Governance) owns deep red-teaming and alignment evaluation at frontier-capability scope. Chapter 8 is explicit about which problems route where.
