# Chapter 1 — The Jagged Frontier and Why This Module Exists

> *AI is unevenly good at your team's work. The managerial job is to decide, at team scope, which part of each workflow routes to which kind of worker — human or machine — and where the checkpoints go. Dell'Acqua et al. named the shape of that unevenness; this module is the operational response.*

## Motivation

The 25-posting evidence base that seeds this track names *SDLC workflow redesign and agent delegation — human + agent routing, AGENTS.md authoring, tool-authorisation policy, delegation ladder* as requirement **R7**, with a posting frequency of **0.28** in the sample (see [`JOB_REQUIREMENTS.md`](../../JOB_REQUIREMENTS.md)). Recurring verbatim phrasings in the postings include *"redesign the SDLC for human + agent work,"* *"author the team's AGENTS.md,"* *"define when an agent can act without human approval,"* *"set the delegation ladder for agent tasks,"* and *"decide what humans still do once agents take over the routine slice."*

R7 sits **below the strict 0.30 threshold** this track applies to posting-based requirements. It is kept in the curriculum for a specific, documented reason: the operational research anchor for the work is strong enough that absence would be a defect in the track regardless of posting frequency. [Dell'Acqua et al., *Navigating the Jagged Technological Frontier: Field Experimental Evidence of the Effects of AI on Knowledge Worker Productivity and Quality* (HBS WP 24-013, Sept 2023)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321) is the first large-scale randomised-experiment study of generative-AI assistance on real knowledge-work tasks, and its findings make the routing decision — *what goes to AI, what goes to a junior human, what goes to a senior human* — a first-order managerial decision, not a tooling preference. The curriculum policy ([`JOB_REQUIREMENTS.md`](../../JOB_REQUIREMENTS.md)) is explicit: *keep R7 because the authoritative research makes it non-obviously load-bearing even at 0.28 posting-frequency*.

This chapter does three things. First, it reads Dell'Acqua et al. at manager-fluency — enough to apply the frontier metaphor, not enough to re-derive the regression. Second, it names the five pieces of mod-106 that operationalise the research — routing, delegation ladder, human-in-the-loop checkpoints, AGENTS.md / MCP / A2A tool-authorisation policy, and attention redirection. Third, it draws the scope boundary: what this module covers, what it defers to the IC-mechanics track below, and what it defers to the frontier-safety track sideways.

## Core concepts

### Reading Dell'Acqua et al. at manager-fluency

The study, run with 758 consultants at Boston Consulting Group, randomised participants into three conditions on a battery of 18 realistic consulting tasks: a **control** group with no AI access, an **AI-only** group with GPT-4 access, and an **AI + prompt-engineering overview** group (GPT-4 plus a short training on how to use it). Two findings are the load-bearing ones for this module.

**Finding 1 — "the jagged technological frontier."** The tasks were not uniformly inside or outside AI's capability. On tasks *inside* the frontier — where GPT-4 was genuinely competent — consultants with AI finished **12.2% more tasks**, completed them **25.1% more quickly**, and produced output that human graders rated **~40% higher quality** than the control group, on average. On tasks *outside* the frontier — where GPT-4 was subtly wrong in ways that a non-expert could not see — consultants with AI were **19 percentage points less likely to produce correct answers** than the control group. The frontier is jagged because the tasks that look adjacent from the outside — a market sizing vs. a recommendation grounded in the same market data — can sit on opposite sides of the capability line.

The managerial implication is the entire thesis of this module: **a task's inside-or-outside-the-frontier status is not knowable from its surface form**, and a workflow that routes a task to AI assistance without naming *which side of the frontier the task sits on* will systematically fail on the outside-frontier tasks while succeeding on the inside-frontier ones. The routing decision (Chapter 2), the delegation ladder (Chapter 3), the HITL checkpoint set (Chapter 4), and the tool-authorisation policy (Chapter 6) are four operational responses to the same underlying problem: you need an explicit mechanism to decide which side of the frontier each task is on *before* the agent runs.

**Finding 2 — "centaurs and cyborgs."** The study also characterised two patterns of effective human + AI collaboration. **Centaurs** divide tasks: the human decides the overall structure and the sub-tasks, then routes individual sub-tasks to AI based on fit. **Cyborgs** interleave: the human and AI collaborate turn-by-turn, with the human editing, redirecting, and recovering from AI errors inline. Both patterns worked; the failure case was the *uncritical consumer* who received AI output and shipped it without applying judgment. For managers, this reads as the shape of the delegation ladder: hand-off patterns (Chapter 3) have to be more structured than *"send this to the agent and see what comes back."*

**The second-order finding** (returned to in Chapter 7). AI-augmented workers in the inside-frontier condition did not just complete the inside-frontier tasks faster — they also shifted their time and attention toward the outside-frontier tasks, the parts of the work the AI could not do well. The managerial reading is that automating the routine slice of a job frees human capacity, and *where that capacity goes next is a design decision*. If you do not make the decision, the capacity drifts — back to the automated work (because it still *looks* like work), into longer Slack conversations, or into meetings that compensate for the trust ambiguity the AI introduced. Chapter 7 is the operational response.

### Where R7 fits in the 25-posting evidence base

The requirement table in [`JOB_REQUIREMENTS.md`](../../JOB_REQUIREMENTS.md) ranks eight recurring requirements for the role. R7 is 7th at 0.28. The three requirements above the 0.30 threshold most adjacent to R7 are:

- **R1 (0.76)** — team-level AI adoption and workflow redesign in general (owned by [`mod-102`](../mod-102-team-ai-adoption-and-roadmap/)). R1 is the *strategic* adoption question — which workflows to touch, in what order. R7 is the *operational* redesign of a specific workflow once it has been selected.
- **R2 (0.60)** — review standards and the *AI generates, humans own* accountability model (owned by [`mod-103`](../mod-103-review-standards-and-eval-commissioning/)). R2 owns the *quality bar* the agent's output has to pass. R7 owns the *delegation structure* that produces the output in the first place.
- **R6 (0.28)** — AI vendor and tool governance (owned by [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/)). R6 is adjacent-sibling at the same frequency; it governs *which agents* are permitted on the team, R7 governs *how the agents are wielded*.

The reading is that R7 is one slice of the broader R1 adoption work, sharpened to the specific question of how a workflow is restructured once AI is present. The posting sample mentions it less often than the strategic adoption work because it is a *second-order* managerial requirement — you only need the delegation-ladder work once the adoption work has succeeded enough to put agents inside your team's workflow. In many organisations, R1 is still in progress and R7 is not yet required — which is why the frequency is lower. But where R1 has landed, R7 is immediate, and the research anchor makes it a non-optional competence at level 40.

### The five pieces of mod-106

A mod-106-literate manager produces five composed artifacts over the course of this module. Each exercise is one artifact; each chapter grounds one piece or the boundary around the module.

| Piece | What it does | Chapter(s) | Exercise |
|---|---|---|---|
| **Task-routing matrix** | Decides, per recurring task type, whether work routes to AI, to a junior human, to a senior human, or to a human + AI pair — grounded in jagged-frontier reasoning | 2 | [Exercise 01](exercises/exercise-01-task-routing-matrix-for-your-team.md) |
| **Delegation ladder** | For each task type routed partly or wholly to an agent, names the delegation level — from *"draft and present for approval"* to *"act unattended within a bounded policy"* | 3 | [Exercise 02](exercises/exercise-02-agents-md-and-delegation-contract.md) (part) |
| **Human-in-the-loop checkpoint set** | Identifies the mandatory gates — pre-invocation, mid-run, post-generation, periodic — in each workflow and links them to the review standard | 4 | [Exercise 04](exercises/exercise-04-human-in-the-loop-checkpoint-design.md) |
| **AGENTS.md + tool-authorisation policy** | A team-scope `AGENTS.md` file plus the companion policy classifying each tool call into an authorisation band | 5, 6 | [Exercise 02](exercises/exercise-02-agents-md-and-delegation-contract.md), [Exercise 03](exercises/exercise-03-mcp-tool-authorisation-policy.md) |
| **Attention redirection plan** | Where the team's highest-value human attention goes once the routine slice is automated — grounded in Dell'Acqua's second-order finding | 7 | [Exercise 05](exercises/exercise-05-post-automation-attention-redirection-plan.md) |

Chapters 1 and 8 bracket the module: Chapter 1 opens with the research anchor and the scope statement; Chapter 8 closes with the ownership boundary against the neighbouring IC and governance tracks.

### What this module is *not*

The adjacent-but-distinct work matters, as it does for every module in this track.

- **Not an IC-mechanics course on building agents.** The actual mechanics of writing agent harnesses, authoring tool definitions, wiring MCP servers, building eval rigs, and iterating prompt-and-tool-call loops at the engineering level belong to [`ai-assisted-software-engineer`](https://github.com/ai-engineering-curriculum/ai-assisted-software-engineer-learning) at level 25. That track teaches your ICs how to build the agent; this module teaches you how to route your team's work through one. Chapter 8 is explicit on the boundary.
- **Not a frontier-safety or red-team course.** The deep red-teaming of autonomous agents at the edge of model capability, formal alignment-eval authoring, and adversarial-eval harness design belong to [`agentic-safety-engineer`](https://github.com/ai-governance-curriculum/agentic-safety-engineer-learning) at level 40 in the AI Governance family. That role operates at *frontier capability* scope; the manager routes team findings to that role, does not re-derive them. Chapter 8 is again explicit.
- **Not a procurement or vendor-governance course.** Which agents to put on the team in the first place, their data-handling posture, the budget envelope, and the registry are [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/)'s remit. mod-106 operates once the agents are already approved and present on the team.
- **Not a policy-authoring course for the enterprise.** Translating external regulation (EU AI Act, ISO/IEC 42001) into company-wide policy belongs to [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) at team-scope and to `head-of-ai-governance` (level 60) at enterprise scope. mod-106 writes a team-scope *tool-authorisation policy* (Chapter 6, Exercise 03) that composes with the broader policy — not the broader policy itself.
- **Not an IT-automation course (RPA, workflow engines).** The pre-generative-AI tradition of workflow automation (Zapier, UiPath, Airflow, n8n) is adjacent and valuable context but is not the subject here. mod-106 is scoped to the specific case where a workflow includes a *generative* AI agent whose outputs are non-deterministic and whose tool calls can have real-world effects.

### The five artifacts, read against the mod-101 human/machine contract

The contract drafted in [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) Chapter 3 named five clauses: C1 (what AI may draft), C2 (what humans must do before shipping), C3 (who is on the hook), C4 (incident response when the AI is wrong), C5 (what data the AI may see). mod-106 operates inside those clauses and sharpens them.

- The **task-routing matrix** (Exercise 01) is the operational version of **C1** — it says, per task type, *what* AI may draft.
- The **delegation ladder** (Exercise 02 part) is the operational version of **C2** — it says *what humans must do before shipping* for each task-type-level pair.
- The **HITL checkpoint set** (Exercise 04) is also C2, read from the workflow side rather than the ladder side.
- The **AGENTS.md + tool-authorisation policy** (Exercises 02, 03) is the operational version of **C5** — it says *what data the AI may see and what it may do with it*.
- The **attention redirection plan** (Exercise 05) is the forward-looking version of **C3** — it says *what the humans on the hook are now for*, given that the routine slice is automated.

If your mod-101 contract is still TBD at the start of this module, Chapter 3 of mod-101 is the prerequisite. mod-106 will not help you write it; it will only operationalise it.

## Example: one workflow, one jagged frontier, one routing decision

The purpose of this example is to make the jagged-frontier framing concrete before Chapter 2 formalises it.

Consider a *platform team's weekly on-call handoff review*. The outgoing on-call writes a short summary of the week's incidents and the state of open alerts; the incoming on-call reads it, asks clarifying questions, and takes over. The team is considering routing this workflow through an AI assistant. The surface form of the workflow is *"produce a one-page summary from a week of alert data and incident tickets."* On the surface, this is an inside-the-frontier task — summarisation is one of the better-studied AI capabilities, and the length is short.

A jagged-frontier reading breaks it into four sub-tasks and routes each separately:

- **Sub-task A: *summarise the quantitative alert data for the week* (counts by service, mean time to acknowledge, number of pages after hours).** Inside the frontier; AI drafts, outgoing on-call reads in ~90 seconds, signs off. This is the kind of mechanical aggregation AI does reliably if the input data is clean.
- **Sub-task B: *summarise the two critical incidents of the week in narrative form, including hypothesised root cause*.** On the frontier edge. AI can draft the sequence of events competently from the ticket timeline, but the *hypothesised root cause* is the kind of claim that is subtly wrong in ways the incoming on-call cannot catch. Route: AI drafts the timeline; the outgoing on-call writes the root-cause hypothesis themselves; the incoming on-call reads both and asks follow-ups.
- **Sub-task C: *flag the two or three live risks the incoming on-call should keep an eye on next week*.** Outside the frontier. This is a judgment call grounded in context that is not in the ticket system — a conversation with another team last Thursday, a vendor deployment scheduled for Tuesday, a half-remembered pattern from six weeks ago. Route: humans only. Any AI attempt will produce a plausible list of generic risks that will miss the actual load-bearing ones.
- **Sub-task D: *route follow-up actions to specific people*.** Mixed. The *names* are in the ticket system (inside the frontier); the *judgment of who is the right owner right now* is not (outside the frontier). Route: AI proposes the names; outgoing on-call confirms or redirects.

The routing above is one defensible mapping, not the one mapping. The point is that **the workflow is not routed as a whole**; it is decomposed into sub-tasks and each sub-task is placed relative to the frontier. Chapter 2 is the matrix that generalises this; Chapter 4 is the HITL checkpoints that enforce the handoff; Chapter 6 is the tool-authorisation policy that governs what the agent is allowed to touch when it is writing sub-task A.

## Summary

- R7 (SDLC workflow redesign and agent delegation) sits at **0.28 posting frequency** — below the strict 0.30 threshold. It is kept in the curriculum because the research anchor ([Dell'Acqua et al., 2023](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321)) makes it a non-optional managerial competence at level 40.
- The **jagged technological frontier** is Dell'Acqua et al.'s term for the unevenness of AI capability: tasks that look adjacent on the surface can sit on opposite sides of the capability line. The frontier is not knowable from the surface form of the task.
- **Centaurs** (divide tasks, route sub-tasks to AI) and **cyborgs** (interleave with AI turn-by-turn) are two effective collaboration patterns; the failure case is the *uncritical consumer* who ships AI output without applying judgment.
- Dell'Acqua et al.'s **second-order finding** — that AI-augmented workers shift attention to tasks AI cannot do well — makes *attention redirection* (Chapter 7) a managerial design decision, not a bystander effect.
- mod-106 produces five composed artifacts: the **task-routing matrix** (Exercise 01), the **delegation ladder** (part of Exercise 02), the **HITL checkpoint set** (Exercise 04), the **AGENTS.md + tool-authorisation policy** (Exercises 02, 03), and the **attention redirection plan** (Exercise 05).
- mod-106 is *not* an IC course on building agents (that is [`ai-assisted-software-engineer`](https://github.com/ai-engineering-curriculum/ai-assisted-software-engineer-learning), L25), not a frontier-safety course (that is [`agentic-safety-engineer`](https://github.com/ai-governance-curriculum/agentic-safety-engineer-learning), L40 AI Governance), not a procurement course ([`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/)), and not an enterprise-policy course ([`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/)). Chapter 8 is the full boundary statement.
- The five artifacts operationalise the mod-101 human/machine contract, clause-by-clause. If your C1–C5 contract is still a TBD, go back to [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) Chapter 3 before working through this module.
