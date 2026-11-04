# Chapter 1 — The Level-40 Scope and the Ladder Around You

> *What is this role, in one sentence? The team-scale operating system for AI-augmented work.*

## Motivation

Every module in this track assumes you are a **line manager of a single team of 5–30 ICs whose daily work routes through AI**. Everything you will build — adoption roadmap, review standards, ROI narrative, delegation ladder, incident runbook, governance crosswalk — is scoped to that team.

The AI Workforce family hires for AI-augmented people-manager work at three adjacent levels. If you cannot say out loud what belongs at your altitude and what belongs to the neighbours, you will do one of two things wrong: (a) take on work that should have gone up to `ai-enablement-lead` and burn the quarter on it, or (b) hand off work that belongs to you and watch your team drift. The purpose of this chapter is to make that boundary precise.

## Core concepts

### The level-40 definition

A **level-40 AI-augmented team manager** owns the operating system of one team, 5–30 ICs, whose work is AI-augmented. That means:

- **One team.** Not a department, not an eng org. A single reporting line into you.
- **5–30 ICs.** Below 5 you are a tech lead; above 30 you are a senior manager or director with sub-managers reporting in — a different job, covered by `ai-engineering-manager` (level 50).
- **AI-augmented work.** The ICs' daily workflow goes through an AI tool (Cursor, Claude Code, Copilot, an internal agent, an analyst copilot, a design copilot). The team's throughput, quality, cost, and risk posture are measurably different because of that.
- **Operating system.** Adoption roadmap, review standards, eval commissioning, productivity measurement, enablement cadence, delegation ladder, incident runbook, governance crosswalk, vendor posture, ritual calendar. You own the plumbing that keeps all of that running on one team.

Note what is **not** in the definition: a specific discipline. The market this cycle codifies the deliverables first on engineering teams, so the examples lean engineering, but the role is discipline-agnostic. A design-team manager, analytics-team manager, content-team manager, support-team manager running AI-augmented work at team scope is in scope here; translate the engineering-flavoured examples into your discipline's equivalents.

### The ladder around you

Four neighbours bound the role. Learn them by owner, by altitude, and by the one-sentence hand-off.

| Neighbour | Level | Family | What they own that you don't | Hand-off to / from you |
|---|---|---|---|---|
| `ai-assisted-software-engineer` | 25 | AI Engineering | IC-scope AI coding fluency: Cursor, Copilot, Claude Code, prompt craft, IC-mechanics of agent authoring | **Below you.** Your reports are trained there. You inherit their fluency; you do not out-ship them. |
| `ai-augmented-analyst` | 20 | AI Workforce | IC-scope analyst copilot work — AI-assisted SQL, notebook analysis, dashboard authoring | **Below you.** Your analytics reports are trained there. Same inherit-don't-out-ship rule. |
| `ai-enablement-lead` | 45 | AI Workforce | **Org-wide** AI enablement programs; multi-team coordination; procurement at scale; rolling the best team pilot out across the company | **Above you.** When a team pilot becomes company-wide, it graduates to L45. You hand off the pilot package, the ROI case, and the lessons learned. |
| `ai-engineering-manager` | 50 | AI Engineering | Engineering-specific manager-of-managers scope: multiple engineering teams, portfolio planning, cross-team architecture, EM-of-EMs mentorship | **Above you.** When you have sub-managers reporting in and the team shape becomes a team-of-teams, you are doing L50 work. |

Three sideways neighbours matter too, and are revisited in Chapter 4:

- `ai-augmented-product-manager` (peer, level 30, AI Workforce) — AI-feature product scope and AI-ROI framing for the product itself, not the team.
- `ai-risk-engineer` (peer, level 25, AI Governance) — engineered risk-eval, red-team, guardrail depth. You commission this work; you do not re-build the rig.
- `ai-governance-analyst` (below, level 15, AI Governance) — operational governance legwork: intake, inventory, framework crosswalks, impact-assessment drafts. You consume this output at team scope.

### What is distinctive about level 40

The level-40 differentiator is **single-team scope** combined with **people-management ownership**.

Against the IC tracks below you: you no longer author the AI artifact; you review it, model the practice, set the review standard, and decide when it ships. The craft is the judgment around the output, not the output itself. You stay hands-on enough to review and model good practice — Chapter 5 sets the fluency bar — but you do not out-ship your team.

Against `ai-augmented-product-manager` (peer, L30): that role owns the AI-feature product and its ROI; you own the team that builds (or uses) it. Both read DX Core 4 / SPACE / DORA; the PM frames product ROI, you frame team ROI.

Against `ai-risk-engineer` (peer, L25): that role builds engineered guardrails, red-team rigs, and risk evals. You commission that work, consume its evidence, and act on findings at team scope. You will not write the eval harness.

Against `ai-enablement-lead` (above, L45): that role runs enablement across many teams, owns the procurement envelope, and coordinates the rollout program. You run enablement inside one team and feed signal upward.

Against `ai-engineering-manager` (above, L50): that role manages managers. You manage ICs. The shape of the job changes — portfolio planning, EM-of-EMs mentorship, cross-team architecture decisions — once sub-managers report in.

### What you own at this level (one inventory)

The 12-module plan rolls up into eleven things you own end-to-end at team scope:

1. Team AI-adoption roadmap and workflow redesign (`mod-102`).
2. Review standards, standards-as-code, eval commissioning (`mod-103`).
3. Team productivity, cost, and AI-ROI measurement (`mod-104`).
4. Team-scope enablement program (`mod-105`).
5. Agent delegation at team scope (`mod-106`).
6. Skill-growth protection and career development (`mod-107`).
7. Hiring, performance management, feedback with AI in the loop (`mod-108`).
8. Accountability and AI-incident response (`mod-109`).
9. AI governance and policy translation at team scope (`mod-110`).
10. Vendor, tool, and budget selection at team scope (`mod-111`).
11. Cross-functional ritual calendar and exec communication (`mod-112`).

Everything else — org-wide enablement, cross-team portfolio planning, control-library architecture, regulator engagement, legal opinion, formal employment actions, SOC-side incident handling — is routed to a neighbour. Chapter 4 is the decision rubric for which neighbour.

## Example: Three managers, three altitudes, one model upgrade

Your vendor ships a new model version and deprecates the one in production in 90 days. Three managers at three altitudes act on it:

- **The level-25 IC (`ai-assisted-software-engineer`) on your team** opens a Cursor rules file and tests three prompts against the new model, flags that the diff-summary prompt regressed, and files a ticket.
- **You (level 40)** re-check every prompt and review habit the team relies on, update your team's AGENTS.md and the review checklist, run a short enablement session for the new default behaviours, re-cost the team's token spend, and update the quarterly ROI one-pager for your VP.
- **The level-45 enablement lead** decides whether this upgrade changes the company-wide tool-standard, coordinates procurement renegotiation, and runs the cross-team comms plan.

All three jobs are real and all three are different. If you try to do the L25 job, you spend the week reprompting; if you try to do the L45 job, you overstep. The level-40 job is the middle slice: one team's operating system catches up to the new model, legibly, on time.

## Summary

- You are a single-team people manager, 5–30 ICs, whose team's work is AI-augmented.
- You inherit IC-scope AI fluency from `ai-assisted-software-engineer` (L25) and `ai-augmented-analyst` (L20) below; you do not out-ship them.
- Org-wide enablement belongs to `ai-enablement-lead` (L45) above you; manager-of-managers scope belongs to `ai-engineering-manager` (L50) above you.
- You own the team-scale operating system across 11 responsibility areas; Chapter 4 details the rubric for everything you do *not* own.
- The level-40 differentiator is the combination of single-team scope and people-management ownership. Keep both in frame.
