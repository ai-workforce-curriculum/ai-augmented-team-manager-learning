# Chapter 7 — The Tool Registry, Ongoing Evaluation, and the Ownership Boundary

> *The registry is the composed output of mod-111. It is one artifact, one owner, one review cadence, one place a visitor can read in ten minutes and see every tool the team runs, why the team runs it, what it costs, what data goes in it, and when it is next reviewed. Everything in the module exists to produce this artifact and keep it current.*

## Motivation

The five pieces of mod-111 — [the copilot matrix](01-the-vendor-selection-problem-at-team-scope.md), [the build-vs-buy call per candidate](03-build-vs-buy-matrix-at-team-scope.md), [the agent-framework / environment matrix](04-agent-frameworks-and-authoring-environments.md), [the budget distribution](05-tool-and-token-budget-distribution.md), [the due-diligence records](06-vendor-due-diligence-and-data-handling.md) — compose into a single artifact, the **team tool registry**. The registry is not a spreadsheet of licences; it is the dated, justified, revocable record of every tool the team runs, with ownership and sunset discipline.

The failure mode this chapter prevents is **registry rot**. A registry maintained once and never revisited becomes a pre-AI artifact by Month 6: tools that sunset without the registry noticing, new tools appearing in the team without entries, clause references drifting out of date, exit plans that become fiction. The chapter names the quarterly cadence that keeps the registry live, the signals that trigger off-cycle amendments, and the ownership boundary beyond which the team registry stops and the org-wide framework starts.

The chapter does four things. First, it describes the **registry structure** — the fields per entry and the organisation of the whole. Second, it describes the **quarterly re-evaluation cadence** that keeps the registry live. Third, it describes **off-cycle amendment triggers** — the events that force a mid-quarter update. Fourth, it draws the **ownership boundary** to [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning), SecOps, procurement, FinOps, and counsel.

## Core concepts

### The registry structure

The registry has one row per tool. The *entry* is the full composition of the five mod-111 artifacts for that tool. Workable field list per entry:

| Field | What it is | Sourced from |
|---|---|---|
| **Tool name + tier** | E.g., "Cursor Business (Tier 2 agentic IDE)" | Chapter 2 |
| **Status** | Trial / Active / Sunset-pending / Sunset | Chapter 7 |
| **Date added to registry** | First inclusion date | Chapter 7 |
| **Primary workflows** | Which [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) workflows this tool supports | Chapters 2, 4, 5 |
| **Stance** | Buy / Wrap / Extend | Chapter 3 |
| **Ownership** | Named owner (manager + maintainer for Wrap/Extend) | Chapter 3 |
| **Evaluation rationale** | One-paragraph justification citing the dated Chapter 2 matrix | Chapter 2 |
| **Budget allocation** | Seat + token layers per [`mod-105`](../mod-105-team-ai-enablement-programs/) stage | Chapter 5 |
| **Due-diligence record** | Link to the filled Exercise 04 checklist | Chapter 6 |
| **Data-handling posture** | Link to the Exercise 05 clause-reader entry composed with [`mod-110` Chapter 6](../mod-110-ai-governance-and-policy-at-team-scope/06-data-ip-and-confidentiality-practice.md) | Chapter 6 |
| **Exit plan** | Decommissioning steps + switch-cost estimate | Chapter 6 |
| **Dependencies** | Other registry entries that depend on this one (e.g., a wrap-layer repo, an MCP server) | Chapter 3 |
| **Next review date** | Default: quarterly | Chapter 7 |
| **Change log** | Dated edits with who and why | Chapter 7 |

Three design points about the registry:

- **One owner for the registry as a whole.** The team manager owns the registry. Individual tool entries may have maintainer owners (for Wrap/Extend stances). The manager is the composition owner.
- **The registry has a canonical location.** Team wiki page, repo file, governance drive — pick one and link everywhere else. A registry that lives in three places with slight variations is a registry with no owner in practice.
- **The registry is readable in ten minutes.** If a new team member cannot read the current registry in ten minutes and know what the team runs and why, the registry is doing too much — move detail into linked documents and keep the registry page an index.

### The quarterly re-evaluation cadence

Once per quarter the manager runs the re-evaluation. Scope:

- **Re-run the Chapter 2 bake-off for any tool category under question.** Not every tool every quarter — just the ones where (a) the team has signalled dissatisfaction, (b) the vendor has made material changes, (c) a new entrant has reached the serious-candidate bar.
- **Re-pin stages per IC per tool** per [`mod-105` Chapter 4](../mod-105-team-ai-enablement-programs/04-tool-budgets-by-learning-stage.md). The stage pin feeds the budget distribution (Chapter 5).
- **Refresh the Chapter 5 budget distribution** with the new stage pins and a stage-shift projection for the next quarter.
- **Refresh the Chapter 6 due-diligence record** for any vendor where a material change has happened — new DPA version, new SOC 2 report, new subprocessor added, material model-routing change, re-contracted tier.
- **Review the sunset shortlist** — tools on the registry whose usage has decayed below threshold, whose Chapter 2 scores have been outperformed, or whose maintenance cost has drifted above the value they return.
- **Produce the quarterly rollup** for the Chapter 7 upward packet consumer (`senior-ai-governance-architect` + `ai-enablement-lead`): list of adds, keeps, sunsets, open conditions, flagged risks.

The cadence lives on the [`mod-112`](../mod-112-cross-functional-leadership-and-ritual-calendar/) ritual calendar. A typical implementation: one half-day quarterly review session, with the artifacts prepped in the preceding week.

### Off-cycle amendment triggers

Some events force a mid-quarter amendment. The triggers and the amendment scope:

| Trigger | Amendment |
|---|---|
| Vendor announces material data-handling change | Re-run Chapter 6 due-diligence for the vendor; re-check Chapter 2 Axis 4 (data handling); amend registry entry. |
| Vendor announces material model-routing change | Re-check Chapter 2 Axis 2 (output quality) with eval regression tests from [`mod-103`](../mod-103-review-standards-and-eval-commissioning/); amend registry entry. |
| Incident (per [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/)) implicates a tool | Add incident reference to registry entry; amend evaluation rationale if the incident changes the risk calculus. |
| New tool appears in team usage without entry | Investigate shadow adoption; run the Chapter 2 process or sunset the shadow use; add entry or disable. |
| Enterprise-commit change at org scope | Re-check Chapter 5 budget against new commit shape; amend budget allocation. |
| Headcount change (hire, rotation, departure) | Update seat allocation; stage-pin new engineer; reclaim seats on departure within named window. |
| New data class added to [`mod-110` Chapter 6](../mod-110-ai-governance-and-policy-at-team-scope/06-data-ip-and-confidentiality-practice.md) matrix | Re-check every registry entry against the new data class; amend data-handling cells. |
| Legal / regulatory change | Route to legal; re-check affected registry entries. |

The trigger list is a slice of the [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) incident runbook crossed with the [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) data-policy change-management discipline. Keep the trigger list short and specific; a trigger list that fires on everything fires on nothing.

### The sunset discipline

A tool is sunset when:

- **Demand did not materialise.** A tool adopted for a workflow that never happened, or a workflow that moved to a different tool, or a workflow that stopped being done.
- **Outperformed by a registry alternative.** A tool whose Chapter 2 scores have been meaningfully exceeded by a sibling in the registry. Keep the better scorer; sunset the other.
- **Cost drift.** A tool whose per-useful-task cost has drifted above threshold without the usage justifying it.
- **Data-handling failure.** A tool whose clause reader no longer allows the team's actual data-class usage (vendor changed terms; team's data classes shifted into a restricted band).
- **Maintenance debt unaffordable.** A Wrap/Extend tool whose maintenance cost has drifted above the value it delivers; the owner has rotated and no successor is named.

The sunset process:

1. **Status change to Sunset-pending** on the registry entry.
2. **Communication to the team** with the reason and the date.
3. **Execution of the exit plan** per Chapter 6 — revoke credentials, retrieve data, update [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) tool-authorisation policy.
4. **Status change to Sunset** with a dated change-log entry.
5. **Retention of the entry in the registry** for at least four quarters in the Sunset state, so the history is legible. Deletion from the registry loses institutional memory.

The sunset discipline is what keeps the registry a live artifact rather than an accretion of licences. A team that has never sunset a tool is almost certainly carrying some.

### The ownership boundary

The team manager owns the registry. The following roles are **upstream, sideways, or counsel** — the manager flags to them, consumes from them, or routes through them, but does not re-own their work.

| Role | What they own | How the registry interacts |
|---|---|---|
| [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) (L45) | Org-wide tool framework; enterprise-commit architecture; multi-team consolidation; vendor-renewal strategy | Consumes team registries as input into the org framework; the manager contributes team evidence and renewal input. |
| Procurement | Contract negotiation; MSA / DPA signature; commercial tier; renewal | Owns the contract signing. The manager contributes business case and files the signed artifact. |
| SecOps / InfoSec | Vendor security assessment depth; CAIQ / SIG completion; pen-test review; incident SLA negotiation | Owns the security depth. The manager files the result and routes flags. |
| Legal / Privacy Office | DPA interpretation; AI Act applicability; cross-border transfer legal position; regulated-use-case classification | Owns the legal position. The manager files the clause and routes questions. |
| FinOps | Long-term committed-use architecture; enterprise rate-card negotiation; multi-cloud cost arbitrage | Owns the commit architecture. The manager contributes usage evidence. |
| [`ai-infra-engineer`](https://github.com/ai-infra-curriculum/) / `model-platform-engineer` | Self-hosted inference infrastructure; model-hosting economics; fine-tuning / training infrastructure | Owns the infrastructure build. The manager contributes demand signal. |
| [`ai-risk-engineer`](https://github.com/ai-governance-curriculum/ai-risk-engineer-learning) (L25, AI Governance family) | Model-level adversarial testing; guardrail design; engineered-risk evidence | Owns the risk-engineering depth. The manager commissions and consumes. |
| `senior-ai-governance-architect` (L50) + `head-of-ai-governance` (L60) | Program-level control library; program accountability; regulator-facing evidence | Consume the quarterly registry rollup as input into the program view. |

The useful mental model: **the manager is the integrator at team scope**. Upward integrators ([`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning), `senior-ai-governance-architect`) consume the team-scope integration. The manager does not try to do the integrator's job above them, and the integrator above does not try to do the manager's job below them.

### Graduation signals toward `ai-enablement-lead`

A team manager who has been operating mod-111's registry well for a year is generating signals that compose into graduation toward [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) (L45):

- **Evidence shape.** The team's dated matrix, budget distribution, due-diligence records, and quarterly rollups are legible to the org framework consumer. The manager is already producing the input [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) consumes across teams.
- **Cross-team pattern spotting.** The manager notices when a tool decision the team made would compose with (or compete against) a sibling team's decision. The manager who is already thinking across teams is exercising L45-shape judgement.
- **Commitment input.** The manager participates in enterprise-commit shaping with pilot evidence and usage trajectory, not just a request-for-more-budget form. Procurement and FinOps recognise the manager as a serious counterparty.
- **Build-up signal.** Over time the team's Extend-stance artifacts (MCP servers, internal routing, custom pipelines) become patterns that other teams want to adopt. The manager is pattern-building at team scope in a way that scales.

These are not graduation *requirements* — [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) has its own curriculum with its own entry criteria. They are signals that the manager who runs mod-111 well is doing the apprenticeship for the role above.

### What this chapter deliberately does *not* do

- **Does not architect the org-wide framework.** That is [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) at L45.
- **Does not specify a storage format for the registry.** Wiki page, Git-tracked YAML, GRC tool, procurement database — all workable. The *content* and *cadence* matter; the storage is organisation-specific.
- **Does not replace the ritual calendar.** The cadence lives on [`mod-112`](../mod-112-cross-functional-leadership-and-ritual-calendar/)'s calendar; this chapter names the cadence, mod-112 operates it.
- **Does not duplicate the [`mod-110` Chapter 7](../mod-110-ai-governance-and-policy-at-team-scope/07-upward-evidence-packet-and-ownership-boundary.md) upward packet.** The tool-registry rollup is one *section* of that packet, not a parallel artifact.

## Example: a composed registry rollup for a quarter

A composite shaped example — calibration, not a case study.

> **Team.** 12 engineers at a mid-sized SaaS. Four quarters into mod-111 practice.
>
> **Registry (brief summary form; full registry has the field set above per entry).**
>
> - Cursor Business — Active — Wrap — Owner: manager + E. — rationale: current Tier 2 winner — budget: 12 seats + ~$200 overage — DD: filed 2026-05 — exit: 2 wks — next review: 2027-02.
> - Copilot Enterprise — Active — Buy — Owner: manager — rationale: Tier 1 for all 12; `.github/copilot-instructions.md` composes with mod-103 standards — budget: 12 seats on org commit — DD: filed 2026-02 — exit: cancel — next review: 2027-02.
> - Claude Code — Active — Extend — Owner: manager + platform engineer F. (MCP server) — rationale: Tier 3 agent authoring; shared `AGENTS.md`; MCP into internal ticket system — budget: $1,120/mo projected — DD: filed 2026-04 — exit: 3 wks — next review: 2027-02.
> - LangGraph (framework, standardised) — Active — Wrap — Owner: platform engineer F. — rationale: scheduled pipelines; checkpointable; team ramping — budget: open-source (model cost allocated to Claude Code) — DD: n/a (library, not vendor) — next review: 2027-02.
> - Windsurf — Sunset — — — rationale: parked candidate from Q[N-2]; usage did not materialise; sunset 2026-09; retained in registry through 2027-09.
> - Codex CLI — Trial — — — rationale: evaluating headless; 3-IC trial through 2027-01; decision at next quarterly review.
>
> **Quarterly activities.**
>
> - Chapter 2 bake-off re-run: Cursor vs Windsurf (deferred Windsurf — usage decay confirmed the Q[N-2] parking). Tier 3 re-check: Claude Code vs Codex CLI in trial.
> - Stage re-pins: 3 ICs advanced Cursor stage-1 → stage-2; 2 advanced Claude Code stage-1 → stage-2; 1 Copilot stage-3 → stage-4.
> - Budget refresh: Projected ~15% Claude Code spend rise next quarter driven by stage advancement; narrated in mod-104 tile.
> - Due-diligence refresh: Anthropic's new subprocessor added (documented in trust-centre update) noted in registry; SecOps confirmed no change to posture.
> - Sunset decision: Windsurf to Sunset state (was Sunset-pending); exit executed.
> - New trial: Codex CLI 3-IC trial opened.
>
> **Rollup to [`mod-110` Chapter 7](../mod-110-ai-governance-and-policy-at-team-scope/07-upward-evidence-packet-and-ownership-boundary.md) packet.**
>
> - Adds: Codex CLI trial.
> - Keeps: Cursor, Copilot, Claude Code, LangGraph.
> - Sunsets: Windsurf.
> - Open conditions: Anthropic ISO 42001 certification pending; re-check.
> - Flagged risks: stage-4 Copilot engineer running 2.5x median — Q conversation scheduled, not a cap.
> - Finance narrative: ~15% Claude Code spend rise projected; framed as stage-advancement, not drift.

Six registry entries, one quarterly review, one dated rollup, one flagged risk, one sunset executed. The registry is live.

## Summary

- The **tool registry** is the composed output of mod-111 — one artifact, one owner (the manager), one review cadence (quarterly), one canonical location. All five prior chapters feed it.
- Entry fields: **tool + tier, status, date added, workflows, stance, ownership, rationale, budget, due-diligence, data-handling, exit plan, dependencies, next review, change log**.
- **Quarterly cadence** re-runs targeted bake-offs, re-pins stages, refreshes budget distribution, refreshes due-diligence for changed vendors, reviews sunset shortlist, produces the upward rollup.
- **Off-cycle amendment triggers**: material vendor change, incident implication, shadow adoption, enterprise-commit change, headcount change, data-class change, regulatory change.
- **Sunset discipline**: Sunset-pending → exit-plan execution → Sunset state retained in registry for ≥ 4 quarters. A team that has never sunset a tool is carrying one.
- **Ownership boundary**: [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) (org framework), procurement (contract), SecOps (security depth), legal (clause interpretation), FinOps (commit architecture), [`ai-infra-engineer`](https://github.com/ai-infra-curriculum/) (self-host), [`ai-risk-engineer`](https://github.com/ai-governance-curriculum/ai-risk-engineer-learning) (engineered risk), `senior-ai-governance-architect` + `head-of-ai-governance` (program-level).
- **Graduation signals** to [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) at L45: evidence shape legible to org consumer, cross-team pattern spotting, commitment input, Extend-stance pattern-building.
- The registry **does not** architect the org framework, prescribe a storage format, own the ritual calendar, or duplicate the [`mod-110` Chapter 7](../mod-110-ai-governance-and-policy-at-team-scope/07-upward-evidence-packet-and-ownership-boundary.md) upward packet. It is the team-scope artifact the upward packet composes with.
