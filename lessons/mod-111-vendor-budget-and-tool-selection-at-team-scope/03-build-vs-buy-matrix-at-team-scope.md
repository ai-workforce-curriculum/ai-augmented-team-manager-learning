# Chapter 3 — The Build-vs-Buy Matrix at Team Scope

> *The question is not "do we build it or buy it." The question is "do we use it as shipped, wrap it with a thin layer we own, extend it through its extension points, or build the thing ourselves." Three of those four answers are routinely correct at team scope. The fourth almost never is.*

## Motivation

A 2024 reading of "build vs buy" treated it as binary. In 2026 the binary framing is the wrong vocabulary for AI tooling for two reasons:

- **The vendors ship composable products.** Every Tier 2 and Tier 3 copilot from Chapter 2 exposes a rules layer, a Model Context Protocol surface, custom instructions, hooks, and in several cases a plugin or extension model. A team that uses the shipped product *plus* a 400-line rules file and two internal MCP servers is neither "buying" nor "building"; it is *extending*.
- **The build-side economics have collapsed asymmetrically.** Writing your own IDE assistant from scratch against a public model API is still infeasible for a team manager to green-light. Writing a custom slash command, a repo-specific review agent, or an internal eval harness on top of a vendor product is a day-scale task. The build-side moved; the frame has to move with it.

R6 ("build-vs-buy defensibility") in the role contract scores at 0.28 — below the threshold at which the role owns the build-side architecture. The question is kept at team scope anyway because the *wrap* and *extend* stances are very much in scope and routinely drive real decisions. The failure mode this chapter prevents is the manager either (a) building a layer they should have used a vendor extension point for, or (b) using the vendor as shipped when a 200-line wrapper would have 10x'd the team's leverage.

The chapter does three things. First, it names the **four stances** (buy, wrap, extend, build) with specific decision criteria. Second, it gives the **cost-side anchors** for each stance and the **R6 threshold** where ownership routes upward. Third, it names the common **anti-patterns** — half-built stacks, re-implemented extension points, abandoned forks — and how the matrix prevents each.

## Core concepts

### The four stances

Each candidate tool from the Chapter 2 matrix gets a stance decision. The four:

| Stance | What it means | Team-side cost | When right | Owned by |
|---|---|---|---|---|
| **Buy** | Use the vendor product as shipped. No custom config beyond vendor-provided settings. | Seats + tokens only. | The product's shipped experience is already a good fit; the team's workflows match the vendor's assumptions; the extension points are not needed. | Procurement + the manager; no engineering ownership. |
| **Wrap** | Use the vendor product plus a thin internal layer (rules file, prompt pack, slash commands, light CLI wrapper, telemetry hook). The wrapper lives in team-owned repos. | Seats + tokens + 1–5 engineer-weeks per quarter of maintenance. | The team has a distinctive review standard, a specific toolchain, or a repeated workflow the vendor doesn't natively encode. Wrap is the most common correct stance. | The manager + 1–2 engineering maintainers on the team. |
| **Extend** | Use the vendor product plus **production-grade** internal extensions — custom MCP servers wired to internal systems, model routing layers, custom-hosted eval pipelines, non-trivial agents composed on top of the product. The extensions live in team- or platform-owned infrastructure. | Seats + tokens + 1–3 engineer-months to stand up + ongoing maintenance (a named owner, not a side-of-desk effort). | The team has workflows that the vendor doesn't support natively and that are high-leverage *for this team*. Extension-point usage is defensible, but production-grade ownership routes up to `ai-infra-engineer` or `ai-enablement-lead` depending on scope. | Platform or AI-infra engineering; the manager commissions. |
| **Build** | Develop and operate a bespoke tool — IDE fork, from-scratch agent runtime, custom foundation-model deployment — that replaces the vendor product rather than composing with it. | Multi-engineer-month to multi-year commitment. | Almost never at team scope. Build decisions live at `ai-enablement-lead` (L45) or higher, informed by [`ai-infra-engineer`](https://github.com/ai-infra-curriculum/) production-infrastructure specialties. | Not owned at team scope. The manager flags the demand upward if the signal is strong. |

Three observations about the table:

- **The common correct stance is wrap.** Most mod-111 matrices should end up buying 2–4 tools and wrapping each with a thin internal layer (rules, prompts, telemetry). This is defensible, cheap, and easy to sunset.
- **Extend is the stance most commonly done badly at team scope.** A manager who green-lights a three-engineer-month internal-tooling build to "make Claude Code work for our codebase" is doing *extend* work the team cannot support in Q[N+2] when the primary builder leaves. Extend work is defensible only with a named owner and a roadmap that survives one engineer rotation.
- **Build is almost never right at team scope.** The R6 rubric below threshold formalises this. "Build" shows up on the matrix as a *signal to route upward*, not a stance the manager picks.

### Decision criteria for each stance

For each candidate tool on the Chapter 2 matrix, the stance decision runs the same four checks:

**Check 1 — Is the shipped experience sufficient for our main workflows?**

If yes → *Buy*. If no → check 2.

Signals that shipped is sufficient: the vendor's default instructions, rules support, and defaults produce output that passes [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) review standards without custom configuration; ICs do not routinely paste the team's style guide into every prompt; the vendor's defaults match the team's security posture per [`mod-110` Chapter 6](../mod-110-ai-governance-and-policy-at-team-scope/06-data-ip-and-confidentiality-practice.md).

Signals shipped is not sufficient: engineers routinely re-explain the team's conventions to the tool; the vendor's default model routing contradicts the team's data-handling policy for some data classes; review standards fail at a rate that compounds across tasks.

**Check 2 — Does the vendor's extension layer close the gap at thin-layer cost?**

If yes → *Wrap*. If no → check 3.

Signals a thin wrap is enough: a `.cursor/rules/` or `AGENTS.md` or custom-instructions file plus a prompt pack plus a couple of slash commands is roughly the cost of the fix; the team's existing [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) standards-as-code artifact is directly reusable; maintenance is a review-every-quarter task, not a project.

Signals wrapping is not enough: the integration needs to reach into internal systems the vendor cannot know about (internal ticket system, data catalog, custom CI, bespoke observability); the required change is in model routing or multi-model orchestration rather than prompts and rules.

**Check 3 — Does the vendor's extension-point architecture support what we need, and can we name an owner for the extension?**

If yes → *Extend*. If no → check 4.

Signals extend is feasible: the vendor supports Model Context Protocol or an equivalent, and the team's extension fits in that shape; the team or a sibling platform team has ownership capacity for the maintenance; the extension is a composition of standard pieces (MCP servers, hooks, custom routing), not a from-scratch layer.

Signals extend is too expensive: the required change is a foundational model-training or model-hosting change; the integration needs guarantees (latency SLAs, on-prem hosting) the vendor cannot provide; the maintenance scope would compound into a multi-engineer ongoing effort.

**Check 4 — Does the requirement rise to a "build" request that routes upward?**

If yes → *route to [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) (L45)* with a demand-signal packet — what the team needs, why vendor options do not meet it, what it would cost to build, what the alternatives are. Build decisions are not a team-manager call.

### Cost-side anchors

| Stance | Capital cost | Operating cost | Sunset cost |
|---|---|---|---|
| Buy | $0 engineering | Seats + tokens | Cancel contract; nothing to decommission on team side. |
| Wrap | 1–5 engineer-weeks initial | 1–2 engineer-weeks per quarter maintenance | Archive the wrap repo; retrain team on vendor defaults. |
| Extend | 1–3 engineer-months initial (MCP servers, routing, pipelines) | 20–30% of an engineer's time ongoing (named owner) | 2–4 engineer-weeks to decommission; may strand data in internal pipelines. |
| Build | Multi-engineer-month to multi-year | Named engineering team ongoing | Multi-quarter — usually requires a parallel operations period. |

The *sunset cost* column is often the forgotten half of the decision. A tool that is cheap to install and expensive to remove is an asymmetric commitment; the Chapter 7 registry treats sunset cost as a first-class attribute.

### The R6 threshold and what it implies

R6 in the role contract scores the manager's build-vs-buy ownership at 0.28, below the 0.5 threshold at which the role owns the deep architecture question. Reading this correctly:

- The manager **owns the stance call** per tool (buy / wrap / extend) at team scope.
- The manager **does not own the organisation-wide build architecture** — whether the org should stand up an internal AI platform, whether to run self-hosted inference, whether to adopt an enterprise framework. Those are [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) (L45) and upward.
- When a team-scope stance call indicates "build" or a heavy "extend", the manager **routes upward** with the demand signal — the team's evidence becomes an input into the upstream architecture decision, not a competing one.

The threshold is also why mod-111 does not teach IDE-fork architecture or foundation-model-hosting economics. These are not level-40 decisions.

### Wardley mapping as a situating frame

[Wardley mapping](https://learnwardleymapping.com/) (Simon Wardley's technique) is a useful background frame — not a required artifact — for the stance decision. Components live on a *genesis → custom-built → product → commodity* evolution axis. In 2026, foundation models and IDE-assistant copilots are on the *product* side of the axis; agent frameworks and MCP servers are on the *custom-built* side with pockets of *product*; team-internal review standards and prompt packs are on the *custom-built* side; the organisation's own code and data are *genesis* for the team.

The Wardley reading of stance choice:

- **Buy** things that are *product* or *commodity* for the team (foundation-model access, shipped IDE assistants).
- **Wrap** when the vendor product is at *product* evolution but the team needs *custom-built* adaptation to its workflows.
- **Extend** when the gap is in the *custom-built* space between vendor product and team-internal patterns.
- **Build** things that are *genesis* and nobody sells (and almost nothing in this list is genesis at team scope anymore).

The frame is not mandatory; the discipline is.

### Anti-patterns to prevent

- **Re-implementing an extension point.** Teams write their own "context inclusion" layer rather than using the vendor's rules system; writing one's own "tool integration" rather than using MCP; writing one's own "model router" rather than the vendor's model-selector. Each anti-pattern is 2–5 engineer-weeks of initial cost + ongoing maintenance to re-produce functionality the vendor supports natively and keeps current. *Check the vendor's extension documentation before writing wrapper infrastructure.*
- **Abandoned forks.** A team forks the vendor product to add a feature, falls behind on upstream, and is stuck in a quarterly "rebase or discard the fork" conversation. Forking the vendor's open-source product is an *extend* stance with unusually high maintenance cost; prefer upstream-compatible extension.
- **The "framework" trap.** A team wraps three tools in a shared internal framework "for consistency," freezing the vendor stack at the moment the framework was written and preventing the quarterly re-evaluation from landing anywhere. Framework-ownership at team scope is almost never defensible; prefer per-tool thin wrappers that evolve independently.
- **Unowned extensions.** The team stands up an internal MCP server for the ticket system; the author moves to another team; the MCP server slowly bit-rots; no owner notices until the ticket system changes its API and the extension breaks silently. Every extend-stance artifact has a *named owner* in the Chapter 7 registry; if no owner can be named, the extension should not have been built.
- **"We built it because the trial was six weeks out."** Procurement-cycle impatience is the most common reason build-stance decisions get taken at team scope. Chapter 7 makes this explicit: if a candidate is in trial, the team uses *the buy stance for an unofficial trial* with a dated deadline — not a parallel build that commits the team to a maintenance stream.

## Example: four candidates, four different stances

A composite shaped example — calibration, not a case study.

> **Team.** 15 engineers at a mid-sized SaaS. Four candidates coming out of the Chapter 2 bake-off: Cursor (Tier 2 agentic IDE), Copilot Enterprise (Tier 1), Claude Code (Tier 3 terminal), and an internal "team-coach" idea someone proposed in the last offsite.
>
> **Cursor — stance: Wrap.**
> The shipped product is strong. The team adds a `.cursor/rules/` directory with the team's review-standard rules (pulled directly from `mod-103`'s standards-as-code repo), a short `project.md` on the codebase conventions, and a prompt pack with three slash commands (`/review-pr`, `/write-tests`, `/bugfix-start`). Maintenance cost: ~1 engineer-week to initialise, ~1 engineer-week per quarter to refresh. Owner: the manager + one named engineer. Sunset cost: archive the rules directory; nothing to decommission.
>
> **Copilot Enterprise — stance: Buy.**
> The shipped product plus `.github/copilot-instructions.md` (a 50-line file pointing at the team's `mod-103` standards) is enough. The team does not stand up custom infrastructure; the GitHub-native experience is the whole fit. Maintenance cost: ~0.1 engineer-week per quarter to refresh the instructions file. Sunset cost: cancel seats.
>
> **Claude Code — stance: Extend.**
> The vendor product plus a team-owned MCP server for the internal ticket system plus a custom `AGENTS.md` describing the team's rituals plus a set of custom slash commands. The MCP server is the extend cost: ~2 engineer-months to stand up (platform engineer-owned, not manager-side), ~20% of one engineer's time ongoing. Named owner: the platform team's representative. Sunset cost: 3 engineer-weeks to decommission; the MCP server stores internal routing config that would need to be exported first.
>
> **"Team coach" — stance: Route upward (not Build).**
> The idea was: build an internal "team coach" agent that reads PR history, links commits to tickets, and generates a weekly team-performance digest. A full build would be ~6 engineer-months initially. The manager does *not* commit to the build; instead, the manager drafts a demand-signal packet for [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) describing what the team needs, with the evidence that two existing products (Linear AI, Jellyfish) provide ~70% of the value and could be evaluated at org scope. The build request routes up; the team continues without it; six months later org procurement adds a vendor product that closes most of the need.

Four candidates, four different stances, one dated matrix, one build request that correctly routed upward rather than becoming a team-side project.

## Summary

- The build-vs-buy framing at team scope is **not binary**. The four stances are **Buy** (use as shipped), **Wrap** (thin internal layer), **Extend** (production-grade extensions via the vendor's extension points), **Build** (bespoke, almost never right at team scope).
- **Wrap is the most commonly correct stance.** It is cheap, defensible, sunsets cleanly, and composes naturally with the [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) standards-as-code artifact.
- **Extend is the stance most commonly done badly.** Named owner + ongoing maintenance line + vendor extension-point usage (MCP, rules, hooks) are the three conditions that make extend defensible at team scope.
- **Build is routed upward.** R6 at 0.28 formalises the ownership boundary: build architecture is not a team-manager call; the manager flags the demand signal to [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) (L45).
- Four decision checks: shipped sufficient? → Buy. Thin-layer closes gap? → Wrap. Vendor extension-points support production-grade work with a named owner? → Extend. Otherwise route upward.
- **Cost-side anchors include sunset cost**, which is often the asymmetric half of the commitment.
- **[Wardley mapping](https://learnwardleymapping.com/)** is a useful situating frame, not a required artifact; the stance choice aligns with where the component sits on genesis → commodity.
- **Anti-patterns**: re-implementing extension points, abandoned forks, the "framework" trap, unowned extensions, build-as-procurement-impatience. The Chapter 7 registry's *owner* and *sunset* fields prevent each one.
