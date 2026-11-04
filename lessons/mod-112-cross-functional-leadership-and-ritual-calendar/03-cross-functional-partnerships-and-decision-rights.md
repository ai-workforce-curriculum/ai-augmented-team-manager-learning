# Chapter 3 — Cross-Functional Partnerships and Decision Rights

> *A partnership is not a friendship. A partnership is a set of decisions that have to be made jointly, a cadence at which they get made, and a written record of who has the call in the room when the call is made. A partnership without decision rights is a Slack channel.*

## Motivation

The team the L40 manager owns is one node in a graph of partner functions, each of which owns a different shape of decision. Product owns the *what* and the *why*. Platform / DevEx owns the *where it runs* and *how the team ships*. Design owns the *patterns and system*. Data / Analytics owns the *metric definitions* and the *instrumentation*. AI-Governance at team scope — the peer who maintains the governance crosswalk at the next team over, or the `ai-risk-engineer` peer at L25 — owns the *engineered risk and governance rails*. The engineering manager running the team has formal authority over how the team *does its work* and informal influence over the joints between the team's work and each partner's.

AI-augmented work hardens every joint. The Product partner wants the roadmap to reflect the throughput gains visible in the [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) dashboard and is correctly suspicious that the gains are activity, not outcome. The Platform / DevEx partner is choosing which agent runtime and which eval harness to platform across teams and needs the team's tool-registry and workflow-catalog evidence to inform the choice. The Design partner is building an AI-era design-system patch — status components, confidence surfaces, human-in-the-loop affordances — and needs team feedback on patterns actually in use. The Data partner is instrumenting the AI cost tile and the AI adoption tile with numbers the manager relies on. The AI-Governance peer owns the gap register that the manager's upward packet lands in. Each joint has a decision shape, a cadence, and a record of who decides. If any of those is missing, the joint is a source of improvisation, which under pressure becomes conflict, which under more pressure becomes an incident.

The default failure mode is that the joints are undefined because the manager and the partners get along. Nothing goes wrong until a decision has to be made that has consequences in both teams — a roadmap item that depends on a platform capability that is not scheduled, a confidence-UI pattern that Design has not approved and the team has shipped, a metric definition the Data team changed that broke the manager's ROI narrative. At that point there is no established forum for the decision, no record of who has the call, and no default outcome. The decision gets made in a crisis Zoom with the wrong people in the room, or gets escalated upward to a VP who should not have had to spend the cycle.

[Google's Project Oxygen](https://rework.withgoogle.com/en/guides/managers-identify-what-makes-a-great-manager/) — the long-running research project documenting what distinguishes highly-rated managers at Google — identified ten behaviours that correlate with great managers. Several of them (empowers the team; expresses interest in team members' success; is productive and results-oriented; has a clear vision/strategy; supports career development) are team-inward and compose with [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/) and [`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/). Others — *is a good communicator*, *is a good coach*, *collaborates across [Google]*, *has key technical skills* — are team-outward and are the behavioural surface this chapter structures. The chapter's thesis: Project Oxygen is the *behavioural* baseline; decision-rights grids and partner-ritual cadence are the *structural* scaffolding that makes those behaviours scale across a five-function partnership surface.

This chapter does four things. First, it names the five partner functions in scope at team L40 and the shape of each joint. Second, it introduces a decision-rights grid (a RAPID-style framing, compactly) and shows how to populate one for the five joints. Third, it names the Google re:Work behavioural baseline and how the structural scaffolding reinforces (not replaces) the behaviours. Fourth, it names the cadence at which each partnership runs and the rituals (on the Chapter 2 calendar) that execute it.

## Core concepts

### The five partner functions in scope

For an L40 engineering-team manager inside a mid-sized organisation, the following five functions are the first-order partners. Larger organisations add more (Security, Legal, Finance, People Operations); smaller organisations collapse some into one role. The decision-rights discipline is the same regardless.

**Product.**

- *What they own.* The product roadmap; feature priority; outcome definition; stakeholder alignment on *what* the team builds and *why it matters*.
- *Shape of joint work.* Roadmap framing; outcome-measurement agreement; release decisions; discovery-vs-delivery balance; AI-augmented capacity claims (how much the throughput gain is worth in roadmap terms).
- *Cadence.* Weekly tactical (roadmap-level); biweekly or monthly strategic (quarter-shape); quarterly off-site review (half-year strategy).
- *Likely conflict.* The manager presents productivity gains from [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/); the Product partner sees the gains as capacity for more features; the manager's position is that some of the gains should go to platform health, review-standard investment, or governance work. The decision-rights grid names who decides where the gains land.

**Platform / DevEx engineering management.**

- *What they own.* Developer-experience investment; shared infrastructure; agent runtime at org scope; eval-harness platform; coding-tool procurement at org scope (above the manager's team-scope selection from [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/)); DX Core 4 instrumentation ([`mod-104` Ch. 2](../mod-104-productivity-measurement-and-ai-roi/02-dx-core-4-and-space-anchors.md)).
- *Shape of joint work.* Tool standardisation vs team autonomy; eval-harness standardisation vs team-specific evals; DevEx investment prioritisation (which friction the platform team fixes first).
- *Cadence.* Monthly strategic; quarterly review; event-triggered (new platform capability lands; DX instrumentation changes).
- *Likely conflict.* The team wants to standardise on Cursor Business; the platform team is standardising org-wide on GitHub Copilot Enterprise. The decision-rights grid names whether the team can hold out, under what conditions, and for how long.

**Design / Design Systems.**

- *What they own.* Design-system patterns; interaction patterns; accessibility; information architecture; the AI-era design primitives (confidence surfaces, status indicators, human-in-the-loop affordances, model-output disclosures).
- *Shape of joint work.* Pattern approval for new AI-interaction UX; Article 50 transparency UI (from [`mod-110` Ch. 4](../mod-110-ai-governance-and-policy-at-team-scope/04-articles-14-and-50-human-oversight-and-transparency.md)); design-system contribution process.
- *Cadence.* Weekly tactical (pattern-level questions as they arise); monthly strategic (pattern reviews in design-system forums); event-triggered (any novel AI-interaction surface).
- *Likely conflict.* The team wants to ship an agent-assisted workflow that uses a confidence-UI pattern Design has not published; Design wants the pattern in the system before shipping. The decision-rights grid names the escalation path and the interim standard.

**Data / Analytics.**

- *What they own.* Metric definitions; instrumentation; the shared dashboarding platform; analytic consistency across teams; the plumbing beneath the [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) dashboard.
- *Shape of joint work.* Metric-definition alignment (what counts as a "merged PR with AI assist"); instrumentation of new workflows; cross-team metric comparability; dashboard-tile authoring.
- *Cadence.* Monthly strategic; event-triggered (new workflow, new tool, new metric). A standing biweekly or monthly data-sync is common.
- *Likely conflict.* The team's local definition of a tile diverges from the org-wide definition; the manager's upward narrative looks different from the Data team's cross-team view. The decision-rights grid names which definition is canonical and how the manager surfaces the divergence.

**AI-Governance at team scope.**

- *What they own.* At L40, this is the peer manager or `ai-risk-engineer` (L25) with whom the manager produces joint governance evidence; in organisations with a formal L50 architect or L60 head, the manager's packet feeds into that role. The joint ownership includes: the gap-register handling at team and architect scope, the engineered-risk commissioning relationship ([`mod-103` Ch. 4](../mod-103-review-standards-and-eval-commissioning/) + [`mod-110` Ch. 2](../mod-110-ai-governance-and-policy-at-team-scope/02-nist-ai-rmf-govern-translated-to-team-practice.md)), the tool-registry data-handling cells ([`mod-111` Ch. 6](../mod-111-vendor-budget-and-tool-selection-at-team-scope/06-vendor-due-diligence-and-data-handling.md)), the Article 14/50 workflow sheets ([`mod-110` Ch. 4](../mod-110-ai-governance-and-policy-at-team-scope/04-articles-14-and-50-human-oversight-and-transparency.md)).
- *Shape of joint work.* Gap-register closure; eval-commissioning briefs; incident retrospectives with engineered root-cause; policy-triggered workflow amendments.
- *Cadence.* Quarterly (packet production); semiannual (retrospective); event-triggered (incident, new policy, new workflow entering scope).
- *Likely conflict.* The governance peer wants a workflow classified as high-risk requiring a full Article 14 sheet; the team's judgment is that the workflow is in-scope but sits on the fence. The decision-rights grid names who classifies and who escalates.

### The decision-rights grid

The structural scaffolding. A compact form of the [RAPID framework](https://www.bain.com/insights/rapid-tool-to-clarify-decision-accountability/) — five roles per decision: *Recommend*, *Agree*, *Perform*, *Input*, *Decide*. RAPID's value at team scope is not strict adherence but the discipline of writing down who holds the *Decide* slot per decision type.

A workable grid template for one partnership (populated for the Product partnership; the same grid shape is filled for each of the five):

| Decision type | Recommend | Agree | Perform | Input | Decide | Ritual |
|---|---|---|---|---|---|---|
| Quarter roadmap shape | PM + Manager (joint) | Design, Data | Team | Platform, Governance | VP Product | Quarterly strategic review |
| Mid-sprint priority swap | PM | Manager | Team | — | PM | Weekly roadmap sync |
| Capacity allocation (features vs platform health) | Manager | PM | Team | — | Manager | Quarterly off-site |
| Outcome-metric definition | Data + PM (joint) | Manager | Data | Design | PM | Monthly data sync |
| Release decision (go/no-go) | PM + Manager | Governance (if high-risk workflow) | Team | Design, Platform | PM | Release ritual |
| AI-adoption budget for features vs platform | Manager | PM | Team | — | Manager (with VP Eng sign-off above threshold) | Quarterly review |

Two design principles for the grid:

- **One Decide slot per row.** Joint decide (two names) is a smell: in practice one of them will decide, and the ambiguity invites retroactive disagreement. Write down which of the two is the tie-breaker.
- **The grid is dated and lives in the decision log.** When a decision-right moves (e.g., the capacity-allocation row shifts from the manager alone to a joint manager-PM-VP triangle as the team grows), the shift is a decision-log entry (Chapter 5) with rationale and reversal conditions.

The grid is drafted by the manager and the partner together — not by the manager unilaterally. A grid the partner has not seen is a wish-list; a grid the partner has signed is a contract. The drafting conversation is often the most valuable session of the module: it surfaces decisions that have been getting made informally and locates them.

### The Google re:Work behavioural baseline

The structural grid does not replace the behavioural work. [Project Oxygen](https://rework.withgoogle.com/en/guides/managers-identify-what-makes-a-great-manager/) identified ten behaviours. The four that most directly apply to cross-functional partnership:

- **Is a good communicator** — listens, shares information, keeps the partnership informed, over-communicates in failure modes.
- **Collaborates across [the organisation]** — does not optimise for the team at the cost of the function; brings cross-team context into local decisions.
- **Is a good coach** — this applies outward too: a partner who lacks context about how AI-augmented work is landing on the team benefits from a coach-shaped conversation, not a status-report-shaped one.
- **Has key technical skills to advise the team** — in cross-functional partnership, this reads as *knows enough of the partner's function to be a credible collaborator*. The manager who cannot discuss metric definitions with Data, confidence-surface patterns with Design, or eval-harness standardisation with Platform is operating with a handicap.

The behavioural baseline and the structural grid reinforce each other. The grid without the behaviours is a bureaucratic artifact; the behaviours without the grid scale only until the partnership is tested; together they produce partnerships that run on cadence, resolve joint decisions cleanly, and compose upward.

Three Oxygen behaviours that are *inward* (empowers the team; expresses interest; supports career development) are covered in [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/) and [`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/). The remaining ones (clear vision, results-oriented, decisive) apply to both; see [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) for the vision / contract framing and [`mod-102`](../mod-102-team-ai-adoption-and-roadmap/) for the results-orientation framing.

### Partnership ritual cadence

The cadence table. One row per partnership, with the ritual that executes the decision rights on the Chapter 2 calendar.

| Partnership | Default ritual | Default cadence | Lencioni type | Decision-rights row(s) this ritual decides |
|---|---|---|---|---|
| Product | Roadmap sync | Weekly or biweekly | Weekly tactical | Mid-sprint priority swap, release decision |
| Product | Quarterly roadmap | Quarterly | Quarterly off-site | Quarter roadmap shape, capacity allocation |
| Platform / DevEx | Platform sync | Monthly | Monthly strategic | Tool standardisation disputes, DX investment prioritisation |
| Design | Pattern review | Monthly or as-triggered | Monthly strategic | Pattern approval, confidence-surface patterns |
| Data / Analytics | Data sync | Monthly | Monthly strategic | Metric definition, instrumentation plan |
| Data / Analytics | Dashboard review | Biweekly | Weekly tactical | Tile authoring, tile-definition drift |
| AI-Governance | Packet sync | Quarterly | Monthly strategic | Packet shape, gap register, triggered amendments |
| AI-Governance | Retrospective | Semiannual | Quarterly off-site | Retrospective findings, program-level requests |

The cadence is a default; it adjusts per real context. A team shipping a monthly product release might need a biweekly design-pattern ritual; a team in steady state might run the governance packet-sync quarterly as the only formal touchpoint and route exceptions through the gap register.

### Boundary with the upward specialities

A partnership map does not replace the roles above the manager. Specifically:

- **The platform-engineering-manager (L50) is not a partner the L40 manager owns alone**; above a certain organisational scale the Platform / DevEx partnership is multi-team, coordinated by [`ai-engineering-manager`](https://github.com/ai-engineering-curriculum/ai-engineering-manager-learning) or equivalent. The L40 manager's grid is for the team-level surface; the multi-team platform conversation is upward, not peer.
- **The AI-Governance program is not a peer at every level.** At L40, the governance peer is the counterpart manager of a sister team or the `ai-risk-engineer` (L25); upward, the [`senior-ai-governance-architect`](https://github.com/ai-governance-curriculum/senior-ai-governance-architect-learning) (L50) and [`head-of-ai-governance`](https://github.com/ai-governance-curriculum/head-of-ai-governance-learning) (L60) consume the manager's packet. The decision-rights grid captures the peer relationship; the upward packet (Chapter 4) is the architect-and-above relationship.
- **Enterprise-level procurement partnerships** (vendor framework negotiation) live at [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) L45 per [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/). The team manager's procurement joint is the *operational* partnership (seat allocation, due-diligence contribution, team-scope renewals), not the *framework* partnership.
- **Executive-coaching or executive-sponsor relationships** that mid-career managers develop are out of scope for mod-112; the module structures the functional partnerships, not the sponsor / mentor ones.

## Example: locating a decision that had no room

Composite — calibration.

An L40 engineering-team manager at a mid-sized SaaS company has a Product partner, a Platform / DevEx counterpart two teams over, and a Design-systems lead. The team has shipped an agent-assisted search feature. The feature uses a confidence-UI pattern that the team invented because the design system does not have one yet; the Design-systems lead was told about it at the launch review, approved it informally, and asked the team to "feed it back to the system." Three months later the pattern has not been fed back; two other teams have shipped similar features with incompatible UIs; a customer-facing inconsistency has been raised; the Design-systems lead is unhappy.

The manager pulls up the decision-rights grid draft (a legacy of running Exercise 02 the prior quarter) and realises the grid *does not have a row* for "novel AI-interaction UI pattern created ahead of the design system." The informal approval at the launch review was not on any decision cadence; nobody owned the feed-back-to-system. The joint had no written decision right.

The manager and the Design-systems lead run a 30-minute conversation. They add a row:

| Decision type | Recommend | Agree | Perform | Input | Decide | Ritual |
|---|---|---|---|---|---|---|
| Novel AI-interaction UI pattern (inside or outside design system) | Team (via tech lead or designer embed) | Design-systems lead | Team to prototype; Design to formalise | PM, other teams already using related patterns | Design-systems lead | Monthly design-system review |

They also add a *ritual*: the monthly design-system review, which the manager had not been attending, now has the team's representative on the rotation. The decision-log entry is written:

> "Added decision-rights row for novel AI-interaction UI patterns on 2026-11-10 after incident-adjacent conflict. Design-systems lead holds Decide; team recommends via tech lead or embedded designer. Ritual: monthly design-system review, team sends representative. Reversal: if the review cannot keep up with team pattern velocity, revisit in Q2 with a design-systems-contributor model."

Three things to notice:

- **The decision-log entry has a trigger.** The conflict triggered the amendment. A decision-log entry that says "we decided to be better partners with Design" without a specific decision is a vibe, not a decision.
- **The grid change creates a ritual change.** The team representative now attends a ritual they did not. The *behaviour* (Google re:Work: collaborates across) is backed by *structure* (the ritual) which is driven by *decision rights* (the grid row).
- **There is a reversal condition.** If the arrangement does not work (the design-system review is too slow to keep up), the arrangement changes — and the next change will be deliberate, not accretion.

The team ships the second feature in the series two weeks later with a pattern that is already a draft in the design system. The Design partner reads the one-pager and the decision log in the next quarterly sync and knows what changed and why. The friction surface moves from "what are these two functions doing together" to "how do we keep this tight as the pattern library scales."

## Summary

- The team L40 manager has **five first-order partner functions**: Product, Platform / DevEx, Design, Data / Analytics, AI-Governance (at peer scope). Each has an owned scope; each has a joint with the team; each joint has a decision shape, a cadence, and a record.
- The **decision-rights grid** is the structural scaffold — a RAPID-style table of decision types mapped to Recommend / Agree / Perform / Input / Decide roles and to the ritual that executes the decision. One Decide slot per row; drafted *with* the partner, not unilaterally.
- The **Google re:Work Project Oxygen** behavioural baseline (is a good communicator; collaborates across; is a good coach; has key technical skills) is the behavioural layer. Structure without behaviour is bureaucratic; behaviour without structure stops scaling under cross-function pressure; the two reinforce each other.
- Each partnership has **one or more rituals** on the Chapter 2 calendar that execute the decision rights. The cadence is a default; it adjusts per team shape.
- **Boundary**: the grid is for peer-partnerships at L40 — upward relationships (to L45, L50, L60) are structured via the upward packet in Chapter 4, not the grid; enterprise-framework procurement partnerships belong to [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning); multi-team platform coordination belongs to [`ai-engineering-manager`](https://github.com/ai-engineering-curriculum/ai-engineering-manager-learning).
- The output: when a novel joint decision surfaces, it is **located** — known partner, known ritual, known decider, known cadence — rather than improvised. The audit for drift is annual (Exercise 02) and event-triggered.
