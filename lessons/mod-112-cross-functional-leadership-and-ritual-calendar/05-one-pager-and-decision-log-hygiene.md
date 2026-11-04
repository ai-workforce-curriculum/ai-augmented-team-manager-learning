# Chapter 5 — One-Pager and Decision-Log Hygiene

> *A one-pager is the version of the team a new peer can hold in their head after one read. A decision log is the version of the team's history a successor can trust without having been there. Both are the artifacts that make the manager replaceable — which is the same thing as making the operating system real.*

## Motivation

The eleven backing artifacts from mod-101 through mod-111 are each defensible but *long*. A new peer manager, a rotating skip-level leader, a new partner in Product or Design, a new counsel assignee reading the governance posture for the first time — none of them will read eleven artifacts. They will read one one-pager. If the one-pager does not exist, they will invent a mental model of the team from whatever signal happens to reach them first — a Slack thread, a demo they attended, the one incident the team had six months ago. That invented model will be wrong in specific ways, and it will drive decisions made about the team in rooms the manager is not in.

The complementary artifact is the decision log. A team's history is the set of decisions that have been made about it — scope changes, ritual retirements, policy amendments, tool-registry additions and sunsets, partnership structure changes. Without a log, the only way to reconstruct the team's history is to interview the departing manager. The interview is the failure mode: either the departing manager is unavailable and the history is lost, or they are available and their time is burned on reconstruction when it should be on handoff of judgement. With a log, the successor reads the dated entries in order and knows what the team has done and why.

Three failure modes the chapter prevents:

- **No one-pager.** The team is explained each time it is explained, from scratch, by the manager. Explanations drift. Peers hold inconsistent mental models. The time-cost of bringing new partners up to speed is high and recurring. The team's visibility to leadership is a function of how recently the manager last pitched them.
- **A one-pager that is a marketing document.** The one-pager exists but is written to make the team look good. It elides the gap register, downplays the incident history, omits the ritual-calendar cost, inflates the headline AI-ROI number. A peer who reads it and then meets the team concludes the one-pager cannot be trusted; the artifact loses its function as a legible compression of the team. Marketing-shaped one-pagers teach peers to read around them rather than from them.
- **Decision log that is a meeting-notes dump or a change log without rationale.** A log of "we decided X on date Y" without *why X* and *what would reverse it* is a log that cannot be read. The successor sees that a decision was made; they do not know whether the conditions that justified it still hold.

This chapter does three things. First, it names the one-pager's shape at L40 — the sections, the length, the honesty discipline. Second, it introduces a decision-log format adapted from the [Architectural Decision Records (ADR)](https://github.com/joelparkerhenderson/architecture-decision-record) pattern, scoped to team operations rather than code architecture. Third, it names the successor-readiness check — the Monday-morning test the module optimises for, re-applied specifically to these two artifacts.

## Core concepts

### The one-pager

A workable shape for the L40 team one-pager. Target length: **literally one page when printed** (around 600–900 words). If it will not fit on a page, detail belongs in a backing artifact; the one-pager links to it.

**Sections, in order:**

1. **The team in one sentence.**
   - What the team does, at what scope, within what domain. Example: "The *underwriting-assist* team owns the ML-assisted underwriting workflow for consumer credit decisions in the Americas region, from model-output inference through reviewer handoff and compliance filing."
2. **Composition.**
   - Headcount (manager + N ICs); stage ladder distribution from [`mod-105`](../mod-105-team-ai-enablement-programs/) (how many at each stage); any specialist roles on the team (tech lead, review-standard owner, enablement champ).
3. **Workflow mix.**
   - Top 3–5 workflows from [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/), with rough percentage of effort. Example: "feature work ~55%, platform maintenance ~20%, review-standard and eval investment ~15%, incident response ~10%."
4. **Measurement anchor.**
   - URL to the [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) dashboard, plus the three headline tiles currently most load-bearing for the team's narrative.
5. **Current roadmap arc.**
   - One sentence summarising the current quarter's commitments; link to [`mod-102`](../mod-102-team-ai-adoption-and-roadmap/) roadmap. Not a full roadmap.
6. **Tool and governance posture.**
   - One line each: tool registry ([`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/)) current state, governance crosswalk ([`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/)) current state, open gap count, open incident retrospective count. All URLs.
7. **Cross-functional partners.**
   - Named people and their current scope. "Product: J. Smith (consumer-credit PM). Platform/DevEx: L. Chen (shared-platform EM). Design-systems: R. Okafor. Data: M. Patel. AI-Governance peer: S. Mwangi (`ai-risk-engineer`, underwriting cluster)." URL to the decision-rights grid from Chapter 3.
8. **Ritual calendar at a glance.**
   - The four to six most load-bearing rituals and their cadences. URL to the full calendar from Chapter 2.
9. **Open loops.**
   - Three to five named open loops with owner and expected resolution window. "Eval-regression backlog: review-standard owner, Q1 burn-down. Platform decision on agent-runtime standardisation: Platform EM, expected Q2. Design-system contribution for AI confidence surface: joint with Design, in review."
10. **What the team is *not*.**
    - One sentence naming the scope boundary. "The team does not own the underlying credit model (that is the Credit-ML team) or the compliance filing system (that is Risk Operations). We own the assist layer and the reviewer workflow."
11. **Date, version, change log link.**

The one-pager lives at a canonical URL — team wiki page, governance drive, or similar — and is linked everywhere. There is one copy. A one-pager that exists in three slightly-different versions in three systems is a one-pager with no owner.

### The honesty discipline for the one-pager

The one-pager earns its credibility by not lying. Three practices that keep it honest:

- **Open loops section cannot be empty.** A team with no open loops is either at an unusual moment of steady state (one quarter per year, if ever) or is hiding things. Peers who see an empty open-loops section stop trusting the document. If genuinely at steady state, write "No open loops this period; next scheduled triggers: Q1 tool-registry review, Q1 governance retrospective."
- **What the team is not section exists.** A team that does not know what it is not has not scoped itself. Peers reading this section learn what *not* to escalate to the team, which is more useful than learning what to escalate.
- **No AI-ROI headline number without the qualifier.** If the one-pager cites a productivity gain, cite the [`mod-104` Ch. 1](../mod-104-productivity-measurement-and-ai-roi/01-metrics-that-separate-gain-from-theatre.md) anti-theatre framing in one sub-clause. "DX Core 4 time-to-ship trend is ↓ 22% year-over-year; attribution across AI assist, platform investment, and roadmap shape is in the backing dashboard" is honest; "22% faster with AI" is marketing and will be read as marketing.

### The decision log

The decision log is a dated, append-only record of team-scope decisions. The format is adapted from the [Architectural Decision Records (ADR)](https://github.com/joelparkerhenderson/architecture-decision-record) pattern used in software architecture — short, dated, structured documents capturing a decision and its reasoning.

**Per-entry template:**

| Field | Example |
|---|---|
| **ID** | DL-2026-11-14-003 (date + sequence) |
| **Title** | Retire the weekly AI-tools sync; replace with monthly CoP |
| **Date** | 2026-11-14 |
| **Author** | J. Doe (team manager) |
| **Status** | Active \| Superseded (by DL-xxxx) \| Reversed (by DL-xxxx) |
| **Scope** | Team ritual calendar |
| **Context** | What was true in the team / organisation / market that made the decision live. Example: "Team is at Stage 3–4 across all ICs per the mod-105 ladder; the weekly sync has thinned to repeat content over the last 4 sessions; the defended tile (novel-workflow adoption rate) is stable but not moving." |
| **Decision** | The decision itself. Example: "Retire the weekly AI-tools sync on 2026-11-20. Replace with a monthly 45-minute CoP session owned by the enablement champ, with purpose: one novel-workflow demo per session, rotating demo owner." |
| **Rationale** | Why the decision was made. Example: "Chapter 2 audit template shows the ritual is no longer defending its tile; ~288 person-hr/yr cost outweighs current value delivered; monthly cadence matches the current stage distribution." |
| **Alternatives considered** | What was weighed and why it was not chosen. Example: "Keep weekly, reduce to 30 min — rejected because the content, not the duration, is the issue. Retire outright — rejected because stage progression could regress if the CoP forum disappears." |
| **Reversal conditions** | What would cause the decision to be revisited. Example: "If novel-workflow adoption tile drops in Q1 next year, or if stage distribution regresses, revisit with potential bi-weekly cadence." |
| **Review date** | When to check in on the decision. Example: "2027-02-14 (quarterly spot audit)." |
| **Links** | URL to Chapter 2 audit entry; URL to replaced ritual's template; URL to the enablement champ's CoP charter. |

The template is scaled. Not every decision is a six-field ADR — a trivial decision (adding a new eval task to the eval-set review) gets a one-line log entry; a material decision (retiring a ritual, amending a decision-rights row, changing the pre-read structure) gets the full template.

### Decisions that go in the log

- Ritual calendar changes (additions, retirements, cadence shifts) — Chapter 2.
- Decision-rights grid changes — Chapter 3.
- Pre-read structure changes — Chapter 4.
- Tool-registry adds, keeps, sunsets — [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/).
- Policy amendments at team scope ([`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/)).
- Workflow catalog changes with team-scope impact ([`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/)).
- Review-standard material amendments ([`mod-103`](../mod-103-review-standards-and-eval-commissioning/)).
- Partnership structure changes (new partner, discontinued joint ritual, escalation-path change).
- Roadmap scope changes outside the normal quarterly cycle.
- Enablement-program material changes ([`mod-105`](../mod-105-team-ai-enablement-programs/)).

### Decisions that do not go in the log

- Individual performance decisions. Belong to [`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/) private records.
- Confidential personnel discussions. Belong to HR partnership channels.
- Sprint-level or tactical workflow choices. Belong to the team's own standup / planning notes.
- Any decision with information the manager is not authorised to publish team-wide.

The log is team-visible and successor-readable. A log that is secretly selective is worse than no log; peers learn to read around it.

### The successor-readiness check

Re-apply the Monday-morning test from Chapter 1 specifically to these two artifacts. A competent peer manager, picking the team up cold, should be able to:

- **Read the one-pager in 10 minutes** and have an accurate first-approximation mental model: shape of team, workflow mix, measurement anchor, roadmap arc, partners, rituals, open loops, scope boundary.
- **Read the last six months of decision log entries in 30 minutes** and understand the team's recent history: what changed, why it changed, what would reverse it, when to revisit.
- **Not need to ask the departing manager** more than a handful of specific questions about judgment calls (people decisions, partnership-nuance history).

If the peer cannot do these three things, the artifacts are not successor-ready. The remedy is not longer documents; it is clearer composition and better honesty discipline.

### A short note on tooling

- A one-pager can live in a wiki page (Confluence, Notion, GitHub Wiki, a plain `README.md`) or a short document. Format matters less than the canonical-location discipline.
- A decision log can live in a wiki, a repo (`decisions/` folder with ADR-numbered Markdown files), or a shared drive. Repos have the advantage of change-tracked history; wikis have the advantage of linkability from other documents. Teams that run both often draft in the repo and summarise on the wiki.
- Templating the one-pager so the sections are consistent across teams in the same organisation is valuable; a shared template is often an artifact owned by [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) at L45 or [`ai-engineering-manager`](https://github.com/ai-engineering-curriculum/ai-engineering-manager-learning) at L50.
- Decision logs that fall out of use because they are hard to write get easier when the template is short. Keep the template friction low.

## Example: a decision-log entry that saves the next quarter

Composite — calibration.

The team has run the quarterly tool-registry review (per [`mod-111` Ch. 7](../mod-111-vendor-budget-and-tool-selection-at-team-scope/07-tool-registry-ongoing-evaluation-and-ownership-boundary.md)). One outcome: the team decides to sunset a specific agent-authoring environment in favour of standardising on Claude Code. The reasoning is specific: one IC's heavy use of the sunset tool has offset into a wrap-layer the team maintains, which has drifted into higher maintenance debt than the value it delivers.

The decision-log entry:

| Field | Value |
|---|---|
| **ID** | DL-2026-10-22-001 |
| **Title** | Sunset `competitor-tool` in favour of standardisation on Claude Code |
| **Date** | 2026-10-22 |
| **Author** | J. Doe (team manager) |
| **Status** | Active |
| **Scope** | Tool registry, team-scope workflow catalog |
| **Context** | Per the Q3 tool-registry review: `competitor-tool` usage has concentrated on one IC; the team-authored wrap layer has grown to ~3 IC-days/month maintenance; the agent-authoring workflows it supports have 90% coverage in Claude Code since Claude Code's Q3 feature set landed. |
| **Decision** | Sunset `competitor-tool` from the active registry on 2026-11-30. Keep in the registry as Status=Sunset with full historical record. Migrate the concentrated-usage IC to Claude Code with a 30-day pairing / coaching window from the enablement champ. Retire the wrap layer; archive the repo. |
| **Rationale** | (1) Wrap-layer maintenance cost exceeded the value delivered against the Chapter 2 evaluation axes. (2) Standardising on a single Tier 3 environment reduces the team's cognitive overhead. (3) The migrating IC has completed the Claude Code pilot ([`mod-105`](../mod-105-team-ai-enablement-programs/) Stage 3 exit) and is ready for the transition. |
| **Alternatives considered** | (a) Keep both tools; update wrap layer against the Q3 feature changes — rejected: the wrap-layer maintenance is the primary cost and this does not address it. (b) Sunset on a longer timeline (6 months) — rejected: the wrap layer is actively costing time now; one month with pairing is a sufficient off-ramp. |
| **Reversal conditions** | If the migrating IC's productivity tile regresses by >15% over the migration window, revisit. If an agent-authoring workflow category appears that Claude Code does not cover and `competitor-tool` does, the sunset status allows re-adoption on explicit decision-log entry (do not silently re-add to active). |
| **Review date** | 2026-12-22 (end of migration window); 2027-01-22 (quarterly spot audit). |
| **Links** | [Q3 tool-registry review notes]; [IC migration plan]; [wrap-layer repo archive]; [mod-111 Ch. 7 audit entry]. |

Four weeks later, a new engineer joins the team. They are a heavy prior user of `competitor-tool` and ask on their first Monday why the team is not on it. The manager points them at the decision-log entry. The new engineer reads it in ten minutes, understands the reasoning, and does not re-open the question. The joining conversation is twenty minutes rather than two hours.

Six months later, Claude Code has a feature regression that genuinely hurts the team. The manager opens the reversal-conditions section of the decision log, reads it, and realises they are in reversal territory. A new decision-log entry — DL-2027-04-xxx — supersedes the sunset and re-adds `competitor-tool` for a specific workflow category, with a dated return review. The log carries the full history: original decision, context at the time, reversal conditions, and the reversal entry pointing back to the original.

A year later the manager rotates and a peer takes over. The peer reads the log for the tool-registry thread. In twenty minutes they understand not just the current state of the registry but the trajectory of decisions that got the team there. They are not starting from scratch.

## Summary

- The **one-pager** is a one-page, canonically-located, honest compression of the team — composition, workflow mix, measurement anchor, roadmap arc, tool / governance posture, partners, ritual snapshot, open loops, scope boundary. Updated at least quarterly; linked everywhere.
- The **honesty discipline**: open-loops section non-empty; what-the-team-is-not section present; AI-ROI claims qualified with attribution; no marketing voice.
- The **decision log** is a dated, append-only record of team-scope decisions in an [ADR-style](https://github.com/joelparkerhenderson/architecture-decision-record) short template: context, decision, rationale, alternatives, reversal conditions, review date, links. Scaled: trivial decisions get one-line entries; material decisions get the full template.
- **Decisions in the log**: ritual-calendar changes, decision-rights changes, pre-read structure changes, tool-registry adds/sunsets, policy amendments, partnership changes, review-standard amendments. **Not in the log**: individual performance, confidential personnel, tactical workflow choices.
- The **successor-readiness check**: a peer picks the team up cold, reads the one-pager in 10 minutes and the last 6 months of log in 30 minutes, and does not need to interview the departing manager about non-judgment matters.
- These two artifacts are **what make the manager replaceable**, which is the same thing as making the team's operating system real — a system that depends on one person's memory is not an operating system.
