# Exercise 02 — Agent Framework Selection Matrix

**Estimated effort:** 2 hours.

## Objective

Produce **v0.1 of your team's agent-framework and authoring-environment selection matrix**: the four agent frameworks ([LangChain / LangGraph](https://langchain-ai.github.io/langgraph/), [CrewAI](https://docs.crewai.com/), [AutoGen](https://microsoft.github.io/autogen/), [PydanticAI](https://ai.pydantic.dev/)) plus serious vendor-SDK alternatives, and the three authoring environments ([Claude Code](https://docs.claude.com/en/docs/claude-code), [Cursor](https://docs.cursor.com/), [OpenAI Codex](https://github.com/openai/codex)) scored for your workflows, with a standardise-vs-let-ICs-pick stance per slot and explicit interaction with [`mod-106`](../../mod-106-workflow-redesign-and-agent-delegation/)'s delegation ladder.

The matrix complements [Exercise 01](exercise-01-copilot-build-vs-buy-matrix.md) — Exercise 01 covers the IDE-shaped copilots; Exercise 02 covers the framework and agent-authoring slot that sometimes overlaps (Claude Code and Codex live in both spaces) and sometimes does not (LangGraph is not an IDE). The methodological anchor is [Chapter 4](../04-agent-frameworks-and-authoring-environments.md).

## Prerequisites

- [Chapter 4](../04-agent-frameworks-and-authoring-environments.md) — the framework and authoring-environment landscape, the standardise-vs-let-ICs-pick decision.
- [Chapter 3](../03-build-vs-buy-matrix-at-team-scope.md) — the four stances; vendor SDKs as a *buy* option vs frameworks as a *wrap*.
- [Exercise 01](exercise-01-copilot-build-vs-buy-matrix.md) — the copilot matrix; Tier 3 candidates overlap with authoring environments.
- Prior-module artifacts your team has produced:
  - [`mod-106` Chapter 2](../../mod-106-workflow-redesign-and-agent-delegation/) — the team's delegation ladder (which workflows are fully-automated, which review-required, which human-with-AI-support).
  - [`mod-103`](../../mod-103-review-standards-and-eval-commissioning/) — the eval harness that any production agent will run against.
- An inventory of the team's current agent-shaped work: scheduled pipelines, repeated workflows, agent-authored slash commands, internal tooling the team builds for itself.
- Current docs for each framework (linked in [`resources.md`](../resources.md)).

## Problem statement

Teams default into frameworks and authoring environments through organic adoption: one engineer prototypes with LangChain, another builds something in Claude Code, a third imports CrewAI for a demo. Six months later, the team has three agent runtimes, no shared maintenance capacity, and a new hire who has to learn all three to be productive.

The matrix forces the decision rather than letting it happen. The deliverable is not a single framework pick — it is a *stance per slot* (framework slot, authoring-environment slot) with a clear reason: standardise, standardise with experiment permission, or let ICs pick.

The failure mode the exercise prevents: a framework pick made on the basis of one engineer's preference without reference to the team's delegation profile, or a let-ICs-pick decision that is actually the absence of a decision.

## Steps

1. **Inventory current agent-shaped work.** Make a short list: every scheduled pipeline, every repeated multi-step workflow, every agent-authored slash command the team uses more than once a week, every internal tool-and-prompt bundle. For each, note: which framework (if any) it uses, which authoring environment it lives in, who maintains it, how often it runs. This is the baseline — what the team *actually* has today.
2. **Map against the delegation ladder.** For each inventory item, note whether it is fully-automated, review-required, or human-with-AI-support per [`mod-106` Chapter 2](../../mod-106-workflow-redesign-and-agent-delegation/). The ladder profile drives framework weight (more fully-automated → framework matters more; more review-required → authoring environment matters more).
3. **Score each framework for your team.** Use a scoring convention consistent with Exercise 01 (1–5 per axis, pinned weights). Suggested axes for frameworks:
   - *Fit to delegation profile* (does it support the multi-step, checkpointable, HITL patterns you actually use?)
   - *Ecosystem maturity* (is the documentation current? are there production users? are the abstractions stable or churning?)
   - *Learning curve* (realistic for your team's framework-experience distribution — not just your most senior engineer)
   - *Portability* (model provider, protocol, artifacts)
   - *Composability with internal tooling* (MCP, hooks, provider-swap, structured outputs, type-safety)
4. **Score each authoring environment.** Suggested axes:
   - *Ergonomics for your IC mix* (stage-mixed, not just stage-3+; see Exercise 01 cohort discipline)
   - *Authoring-artifact support* (rules, `AGENTS.md`, custom commands, skills, hooks)
   - *Headless / scheduled mode*
   - *Composition with the chosen framework slot*
   - *Data-handling against [`mod-110` Chapter 6](../../mod-110-ai-governance-and-policy-at-team-scope/06-data-ip-and-confidentiality-practice.md)* — reuse the Axis 4 gate from Exercise 01 where the environment overlaps
5. **Consider the vendor-SDK alternative.** For teams whose agent needs are mostly single-vendor-centric, [Anthropic's claude-agent-sdk](https://docs.claude.com/en/api/agent-sdk-overview) or [OpenAI's Agents SDK](https://platform.openai.com/docs/guides/agents-sdk) may be a *buy* stance that competes with the framework's *wrap* stance. Score the vendor SDK alongside the frameworks in the same table.
6. **Decide the framework stance.** Standardise / Standardise-with-experiment / Let-ICs-pick. For most teams, the default is *Standardise with experiment permission* on the framework slot — multi-engineer maintenance makes coherence worth the constraint; experiment permission keeps the team evolving. Document the reason for whatever stance you pick.
7. **Decide the authoring-environment stance.** Often *Standardise one + let-ICs-pick one more* — the ergonomics case for ICs trumps coherence for the environment, as long as produced artifacts (rules, prompts, `AGENTS.md`) live in team repos and are portable.
8. **Document the interaction with Exercise 01.** For Tier 3 candidates that appear in both matrices (Claude Code, Codex), the two matrices should agree. If Exercise 01 picked Claude Code as Tier 3 and Exercise 02 picks Codex as the authoring environment, resolve the conflict explicitly — do not file two matrices that contradict each other.
9. **Draft the per-slot recommendation + stance.** One sentence of rationale per slot, citing scores or delegation-profile reasoning. Name the *experiment permission* scope if you adopted the standardise-with-experiment stance.
10. **Define the portability expectations.** For every framework / environment adopted: (a) which model providers it supports, (b) which protocol (MCP) it uses, (c) where the artifacts live so an IC rotation does not break the agent, (d) the switch-cost estimate per Chapter 3.
11. **File the matrix.** Dated. Link from the Chapter 7 tool registry. Register the next-review date. The matrix feeds into Exercise 03 (budget) and Exercise 04 (due diligence, for the framework if it is open-source + the authoring environment if it has a per-seat or per-token cost).

## Starter guidance

- **Framework and environment are different standardisation pressures.** Framework = maintenance-coherence (lean standardise). Environment = IC ergonomics (lean permit variety). Resist the temptation to apply one stance to both.
- **Delegation profile is the strongest input on the framework slot.** A team doing mostly fully-automated scheduled work has different needs than a team doing mostly ad-hoc exploration. Score with the profile explicit.
- **The authoring environment sometimes *is* the agent.** For teams whose agent work is "IC runs Claude Code with a specific `AGENTS.md`", the authoring environment replaces the framework rather than composes with it. This is often the right stance for review-required-dominant teams.
- **Vendor SDK is a real option, not a straw man.** For teams locked to one model provider for other reasons, the vendor SDK is often a cleaner *buy* than a framework's *wrap*. Score it honestly.
- **Framework churn is a real cost.** A framework that renames its primary abstraction every six months imposes migration work on the team. Factor into *ecosystem maturity* scoring; cite specific API stability (or lack of).
- **Let-ICs-pick is not laissez-faire.** Let-ICs-pick on framework means the registry records per-agent framework choice — the manager still knows what runs where. Let-ICs-pick-with-no-registry is drift dressed as flexibility.
- **Standardise does not mean everything existing moves.** When adopting a framework standard, the existing agents on other frameworks can stay on their framework through end-of-life or scheduled migration. Do not force a stop-the-world rewrite; set a direction.
- **Portability expectations matter even when switching is unlikely.** Record the switch-cost estimate so sunset discipline is possible. A framework with unknown switch cost is a commitment of unknown size.
- **Do not duplicate Exercise 01's Tier 3 decision.** If Exercise 01 picked Claude Code Tier 3, this exercise's authoring-environment slot inherits that. If this exercise disagrees, resolve the disagreement once — not in two places.

## Acceptance criteria

The matrix is complete when:

- Current agent-shaped work is inventoried with framework / environment / maintainer per item.
- The inventory is mapped against the [`mod-106`](../../mod-106-workflow-redesign-and-agent-delegation/) delegation ladder.
- At least three agent frameworks (or three + at least one vendor SDK) are scored against pinned axes, weighted consistently with Exercise 01's scoring convention.
- At least two authoring environments are scored on the same pattern.
- A framework stance is named (standardise / standardise-with-experiment / let-ICs-pick) with a one-paragraph rationale citing the delegation profile.
- An authoring-environment stance is named with a one-paragraph rationale.
- The Exercise 01 overlap on Tier 3 is resolved explicitly — the two matrices agree or the resolution is documented.
- Portability expectations are recorded: model-provider support, protocol support, artifact location, switch-cost estimate.
- Experiment-permission scope is defined where a standardise-with-experiment stance is adopted (who, what, how long, how reported back).
- The matrix is filed at a canonical location with a dated next-review marker.
- A change-log entry names authors, reviewers, and date. v0.1.

## Stretch goals

- **Agent-shaped work roadmap.** Project the next quarter's agent-shaped work from the [`mod-102`](../../mod-102-team-ai-adoption-and-roadmap/) adoption roadmap and the Chapter 7 upcoming workflow backlog. Score each projected item against the recommended framework and environment; flag any poor-fit items early so the stance can be re-checked before the item lands on the team.
- **Pattern-sharing inventory.** For stage-3 and stage-4 ICs maintaining agents, inventory the authoring artifacts (`AGENTS.md`, slash commands, skills, custom rules) that could be pattern-shared across the team or across teams. Compose with [`mod-107` Chapter 3](../../mod-107-skill-growth-anti-atrophy-and-career-development/) on skill development and pattern-building.
- **Multi-agent architecture sketch.** Where the team's delegation ladder includes a multi-agent workflow, sketch the architecture against the chosen framework and against one alternative (e.g., LangGraph vs CrewAI). The sketch is for the Chapter 7 registry's *rationale* field, not as a build commitment; it clarifies whether the framework is actually a fit.
- **Eval-harness composition.** For each production-grade agent you run or will run on the chosen framework, specify how the eval harness from [`mod-103` Chapter 4](../../mod-103-review-standards-and-eval-commissioning/) composes with it. A framework whose eval story is "we'll figure that out later" is a framework that will not pass the mod-103 gate.
- **Open-weight / self-hosted scenario.** Sketch what the framework slot would look like if the team moved to a self-hosted open-weight model for a subset of workflows. The scenario is for the Chapter 3 *extend* conversation and the cost-model sensitivity analysis — not a build commitment.
