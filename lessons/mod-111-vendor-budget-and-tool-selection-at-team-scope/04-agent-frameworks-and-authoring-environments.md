# Chapter 4 — Agent Frameworks and Agent-Authoring Environments

> *The copilot question was "which one does the team code in." The agent question is sharper: "when an IC builds an agent on top of our systems next Tuesday, which framework does that agent run on, which authoring environment did they build it in, and who else on the team can maintain it when they rotate." Both halves have to be answered together or the registry has a hole.*

## Motivation

By 2026, two overlapping ecosystems matter at team scope:

- **Agent frameworks** — Python (and increasingly TypeScript) libraries that structure multi-step LLM programs: planning, tool-calling, memory, multi-agent coordination, state. The serious ones in scope: [LangChain / LangGraph](https://langchain-ai.github.io/langgraph/), [CrewAI](https://docs.crewai.com/), [AutoGen](https://microsoft.github.io/autogen/), [PydanticAI](https://ai.pydantic.dev/). Each has defensible positioning and production users; the choice between them is a stance, not an obvious default.
- **Agent-authoring environments** — the local developer tools in which ICs write, test, and iterate on agents: [Claude Code](https://docs.claude.com/en/docs/claude-code), [Cursor](https://docs.cursor.com/), [OpenAI Codex](https://github.com/openai/codex), and the agent modes inside other IDEs. The authoring environment is where the agent exists before it is productionised; the environment's extensibility (slash commands, custom agents, hooks, skills) often matters more than the framework choice for teams whose "agent" work is operational, not productionised.

Many teams default to a *framework choice without an authoring-environment choice* and end up with LangGraph code that no one can iterate on efficiently because the team never picked where the iteration lives. Other teams standardise on an authoring environment and then grow organic agents across six different runtimes because the framework question was never asked. mod-111 forces the manager to hold both halves of the decision at once.

The chapter does four things. First, it describes the agent-framework landscape with distinct positioning for each framework. Second, it describes the agent-authoring environment landscape. Third, it names the **standardise vs let-ICs-pick** decision and when each is right. Fourth, it draws the interaction with [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/)'s delegation ladder — where agents live operationally.

## Core concepts

### The four agent frameworks in scope

| Framework | What it is | Where it shines | Trade-offs | Primary reference |
|---|---|---|---|---|
| [**LangGraph**](https://langchain-ai.github.io/langgraph/) (the LangChain project's agent runtime) | Graph-based agent runtime from the LangChain organisation; explicit state machines; checkpointing; human-in-the-loop as first-class | Long-horizon agents; durable state; explicit control-flow; production hardening | Steep conceptual overhead; the ecosystem brings LangChain abstractions (which many teams either love or want to avoid) | [LangGraph docs](https://langchain-ai.github.io/langgraph/) |
| [**CrewAI**](https://docs.crewai.com/) | Role-based multi-agent framework; "crew" as the primary abstraction; declarative task-and-agent configuration | Multi-agent workflows where distinct roles (researcher, writer, reviewer) are a natural fit; fast to prototype | Less explicit about long-horizon state than LangGraph; multi-agent patterns tend toward chattiness and cost | [CrewAI docs](https://docs.crewai.com/) |
| [**AutoGen**](https://microsoft.github.io/autogen/) (Microsoft Research) | Multi-agent conversation framework; agents-as-chat-participants abstraction; `AutoGen v0.4` added the Core / AgentChat / Studio separation | Group-chat patterns; research-adjacent work; studios/UI tooling; strong Microsoft ecosystem integration | Framework has gone through visible API churn across versions; team should check current stability | [AutoGen docs](https://microsoft.github.io/autogen/stable/) |
| [**PydanticAI**](https://ai.pydantic.dev/) | Type-safe agent framework from the Pydantic team; structured outputs and tool-calling as the core primitives | Team wants Python-type-level correctness on agent I/O; integrates naturally where Pydantic is already the data-contract layer | Younger ecosystem; multi-agent / long-horizon patterns are less mature than LangGraph's | [PydanticAI docs](https://ai.pydantic.dev/) |

A few things that are true across the frameworks and worth explicit:

- **All four support [OpenAI](https://platform.openai.com/docs), [Anthropic](https://docs.claude.com/en/docs/build-with-claude/overview), and open-weight models** via their provider abstractions. Framework choice does not lock the team to a model provider.
- **All four have Model Context Protocol support**, either natively or via wrappers, as of late 2025. The MCP question from Chapter 2 and Chapter 3 is live across the frameworks.
- **None of them replaces [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) eval commissioning.** An agent built on any of these frameworks still needs the eval harness from `mod-103 Chapter 4` to produce defensible quality evidence.
- **The vendor SDK is also an option.** [Anthropic's `claude-agent-sdk`](https://docs.claude.com/en/api/agent-sdk-overview) and [OpenAI's Agents SDK](https://platform.openai.com/docs/guides/agents-sdk) are first-party SDKs that compete with the third-party frameworks for the "we need less abstraction" slot. The Chapter 3 build-vs-buy framing applies: if the vendor SDK ships what you need, that is a stronger *buy* than adding a framework dependency.

### The three authoring environments in scope

The *authoring environment* is where ICs write, test, iterate, and maintain agent-adjacent work — custom slash commands, small focused agents, repo-local automation scripts, eval harnesses. The three primary candidates:

| Environment | What it is | Where it shines | Trade-offs | Primary reference |
|---|---|---|---|---|
| [**Claude Code**](https://docs.claude.com/en/docs/claude-code) | Terminal-native and IDE-integrated agent from Anthropic; `AGENTS.md`, slash commands, sub-agents, hooks, skills | Long-horizon work; agent-authoring via `AGENTS.md` + skills; MCP as a native integration; headless CI mode | Anthropic-ecosystem-centric by default; cost model is usage-based and benefits from stage-shaped distribution per Chapter 5 | [Claude Code docs](https://docs.claude.com/en/docs/claude-code) |
| [**Cursor**](https://docs.cursor.com/) | VS Code fork; agent mode, MCP support, rules, custom modes, background agents | IDE-native authoring; strong for teams whose work is majority-IDE-shaped; `.cursor/rules/` ergonomics | VS Code fork trade-offs (extension compatibility, upstream lag); authoring surface is less explicit about agent patterns than Claude Code | [Cursor docs](https://docs.cursor.com/) |
| [**OpenAI Codex**](https://github.com/openai/codex) | OpenAI's CLI / cloud agent; sandboxed execution; cloud-hosted variant for longer runs | Teams already on the OpenAI ecosystem; cloud-hosted mode useful for scheduled or long-running jobs; a clean CLI mental model | Less mature in `AGENTS.md`-style conventions than Claude Code at the time of writing; cloud-mode cost model needs explicit tracking | [Codex on GitHub](https://github.com/openai/codex) |

Two observations about the authoring-environment slot:

- **The authoring environment sometimes *is* the agent.** When the team's agent work is "an IC runs Claude Code with a specific `AGENTS.md` to do a specific repeated task," the authoring environment is the agent runtime — no separate framework is involved. This is often the right stance for operational agent work (routine refactors, test generation, eval runs); the framework overhead is paid only when the work moves to a scheduled, parameterised, multi-step pipeline.
- **The environment choice also determines where [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/) skill-growth happens.** ICs who build agents in Claude Code become Claude-Code-literate; ICs who build in Cursor become Cursor-literate. The portability of the resulting skill matters when thinking about team composition over time.

### The standardise vs let-ICs-pick decision

Three stances the team can take for each slot (framework and environment):

| Stance | What it means | When right | Risks |
|---|---|---|---|
| **Standardise on one** | The team picks one framework and one environment; new agent work goes there; the registry records the choice as mandatory | High maintenance-coherence need; multi-engineer-maintained agents; junior-heavy team benefiting from a single learning curve; centralised ops | Risk of lock-in to a framework whose trajectory diverges from the team's needs; blunts IC exploration |
| **Standardise on one, allow experiment** | Default is the standard; ICs may run experiments in alternatives with a time-boxed trial that reports back into the quarterly registry review | Teams balancing coherence with evolution; stage-3 and -4 engineers (per [`mod-105`](../mod-105-team-ai-enablement-programs/)) explicitly scoped for exploration | Requires discipline on the time-box — experiments become long-lived shadow stacks without it |
| **Let ICs pick** | No standard; each IC chooses per agent; the registry records which framework / environment each agent uses | Small team with senior engineers only; agents that are single-maintainer by design; strong need for local optimisation | Framework fragmentation; new hire onboarding across three frameworks; maintenance becomes the original builder's job forever |

The useful way to think about this: **framework and environment have different standardisation pressures**.

- **Framework** is where multi-engineer maintenance usually happens. Most teams should *standardise on one framework* (with experiment permission) because the maintenance-coherence matters: when the original builder rotates, someone needs to maintain the agent.
- **Authoring environment** is often more personal-ergonomics-heavy — some ICs produce more in Claude Code, some in Cursor, some in Codex. *Let-ICs-pick on environment* is often defensible for stage-3+ ICs, with the constraint that the artifacts the IC produces (rules, prompts, `AGENTS.md`, slash commands) live in team repos and are portable.

A reasonable default team position:
- **Standardise framework.** Pick one (LangGraph / CrewAI / AutoGen / PydanticAI / vendor SDK) and make it the team default. Experiments in a different framework are time-boxed and report back.
- **Standardise one authoring environment + let-ICs-pick one more.** E.g., Claude Code as the standardised environment (because the team's agent work is the central use case), plus Cursor as a permitted parallel for ICs whose IDE-ergonomics benefit from it. All produced artifacts live in team repos.

### The interaction with the delegation ladder (`mod-106`)

[`mod-106` Chapter 2](../mod-106-workflow-redesign-and-agent-delegation/) defines the delegation ladder — when work is delegated to a fully-automated agent, to a review-required agent, to a human, etc. The framework and environment choice interacts with the ladder in a specific way:

- **Fully-automated delegation (bottom of the ladder)** usually runs on a *framework* — scheduled pipelines, CI-triggered agents, long-horizon runs. The framework choice matters because production hardening (checkpointing, retries, observability) is at stake. LangGraph's explicit state management is often a fit here; vendor SDK can also be.
- **Review-required delegation** often runs in an *authoring environment* — an IC invokes Claude Code or Cursor's agent mode, the agent produces output, a human reviews before shipping. The environment choice matters because ergonomics and HITL (human-in-the-loop) support drive how quickly the IC can iterate.
- **Human-with-AI-support** sits in the IDE — Tier 1 and Tier 2 copilots from Chapter 2 rather than an explicit agent framework at all.

The matrix has to score each framework and each environment against the team's *delegation ladder profile* — a team doing mostly review-required work has a different answer than a team running production-grade fully-automated agents.

### Lock-in and portability

Three sub-decisions that go on every framework / environment matrix row:

- **Model-provider portability.** Can we change the model provider without rewriting the agent? All four frameworks support multiple providers; most authoring environments do too (with caveats — Claude Code is Anthropic-centric by default; Cursor is model-agnostic).
- **Protocol portability.** Does the agent communicate with internal systems via a standardised protocol (MCP) or a framework-specific interface? Framework-specific is faster to build initially; MCP is more portable.
- **Artifact portability.** Rules, prompts, `AGENTS.md`, custom commands — are these in team repos and portable across environments, or are they trapped inside a vendor's walled garden? Portable artifacts survive an environment switch; walled artifacts require re-authoring.

Portability is a weight in the matrix but is rarely dominant — the team is almost always better off picking the framework / environment that fits the current workflow well than optimising for a switch that may never happen. The point of recording portability is to make the *cost of switching* explicit before the switch is needed.

### What this chapter deliberately does *not* do

- **Does not pick a framework or environment for the team.** Reasons: (a) the correct answer depends on the team's workflow shape and existing ecosystem; (b) the framework landscape moves faster than the curriculum publishing cadence; (c) the manager's decision is more defensible if supported by Exercise 02's dated matrix than by a curriculum recommendation.
- **Does not cover framework-internal architecture** (LangGraph's graph primitives vs CrewAI's crew model vs AutoGen's group-chat model vs PydanticAI's type-first model). The *engineering* comparison of agent frameworks lives in the `agent-infra-engineer` / `agentic-engineer` learning paths; this chapter covers the *manager-scope selection* framing.
- **Does not cover self-hosting economics.** Running an agent framework against a self-hosted open-weight model is a Chapter 3 *extend* stance decision with cost implications outside this chapter's scope.
- **Does not re-cover the [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) delegation framework.** The ladder lives there; this chapter cross-references it as an input, not as something it owns.

## Example: two different teams, two different stances

A pair of composite shaped examples — calibration, not case studies.

**Team A — a six-person devtools team with heavy production-automation work.**

Primary use case: nightly refactor runs across a large monorepo; scheduled eval runs against internal services; multi-step bug-triage pipelines. Delegation profile skews toward fully-automated with review on the final step.

- **Framework stance.** Standardise on **LangGraph**. Rationale: durable state and checkpointing are load-bearing for the nightly pipelines; explicit graph structure makes multi-engineer maintenance tractable; team already uses LangChain for a smaller integration. Experiments in PydanticAI permitted for small type-heavy sub-agents.
- **Authoring-environment stance.** Standardise on **Claude Code** as the authoring default; let-ICs-pick on **Cursor** for in-IDE work. Rationale: scheduled pipelines are developed in Claude Code with explicit `AGENTS.md` and slash commands; ad-hoc IDE work goes through Cursor.
- **Exercise 02 output.** A matrix with LangGraph as mandatory for new scheduled agent work; Claude Code as the primary environment with a Cursor-permitted carve-out; vendor SDKs scored but not adopted (framework ecosystem already established).

**Team B — a four-person internal-tools team with heavy exploratory agent work.**

Primary use case: "someone's building something new this month" is the norm; agents are often single-maintainer and short-lived; the team's output is more "patterns other teams adopt" than "scheduled pipelines."

- **Framework stance.** **Let-ICs-pick** on framework. Rationale: agents are single-maintainer by design, lifecycle is short, the cost of a framework mismatch is low; the team's output is patterns, not production pipelines. The registry records which framework each live agent uses.
- **Authoring-environment stance.** Standardise on **Claude Code** for authoring, with the authoring artifacts (`AGENTS.md`, skills, slash commands) living in a shared team repo so patterns compose. Rationale: pattern-sharing is the team's output; a shared environment with a shared artifact repo amplifies it.
- **Exercise 02 output.** A matrix with no framework default, a "framework-of-record on each agent" column in the registry, Claude Code as mandatory authoring environment, a shared `AGENTS.md` / skills repo as the team's main maintenance artifact.

Both are defensible; both are dated; both produce a Chapter 7 registry entry that an auditor can read.

## Summary

- Two overlapping ecosystems: **agent frameworks** ([LangChain / LangGraph](https://langchain-ai.github.io/langgraph/), [CrewAI](https://docs.crewai.com/), [AutoGen](https://microsoft.github.io/autogen/), [PydanticAI](https://ai.pydantic.dev/), plus [vendor SDKs](https://docs.claude.com/en/api/agent-sdk-overview) as a serious *buy* option) and **agent-authoring environments** ([Claude Code](https://docs.claude.com/en/docs/claude-code), [Cursor](https://docs.cursor.com/), [OpenAI Codex](https://github.com/openai/codex)). The decision has to hold both halves at once.
- **Framework** is where multi-engineer maintenance happens — *standardise* with experiment permission as the default stance.
- **Authoring environment** is personal-ergonomics-heavy — *standardise one + let-ICs-pick one more* is often defensible, with portable artifacts in team repos.
- The decision composes with [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) delegation profile: fully-automated work drives framework choice; review-required work drives environment choice; human-with-AI work stays in Tier 1 copilots from Chapter 2.
- **Lock-in and portability** — model-provider portability, protocol portability (MCP), artifact portability — are matrix columns, not usually dominant weights, but are what makes the Chapter 7 sunset discipline possible.
- **Does not pick for the team.** Exercise 02 produces the dated framework-and-environment matrix per team workflow; the curriculum does not short-circuit the decision.
- **Composes with Chapter 3** build-vs-buy framing: vendor SDK as a *buy*, framework adoption as a *wrap*, extending a framework with internal tooling as *extend*, writing your own agent runtime as a routed-upward *build* request.
