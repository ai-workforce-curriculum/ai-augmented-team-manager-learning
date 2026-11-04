# Chapter 5 — Partnering with Platform / DevEx / Product, and the Graduation Hand-Off

> *"A good pilot either graduates to a Platform-owned product, or stays explicitly team-shaped. A pilot that drifts into 'kind of platform, kind of team' is the one that bit-rots."*

## Motivation

A team-level AI-adoption roadmap is not run in isolation. Every AI-targeted task family on the roadmap touches some shared system — a shared code repo, a shared tool configuration, a shared cost budget, a shared security review, a shared enablement programme — and the owners of those shared systems have their own roadmaps. If you do not couple the team roadmap to Platform, DevEx, Product, Security, and the org-wide enablement lead early, one of two things happens: you build team-local infrastructure that duplicates Platform work (expensive, brittle, invisible at the org level), or you depend silently on Platform in ways that break the first time their roadmap moves.

This chapter sets the coupling. It covers (a) who the shared-infrastructure partners are and what each wants from your roadmap, (b) the signals that a pilot should graduate out of the team to become a Platform-owned product or an org-wide enablement rollout, and (c) the specific hand-off contract to `ai-enablement-lead` (L45) when the team pilot becomes company-wide. Team Topologies (Skelton & Pais, 2019) is the grounding framework; this chapter translates it for AI-augmented work at team scope.

## Core concepts

### The four partner functions

Four partner functions show up across the 25-posting sample as natural couplings for the team manager. Name them and the hand-off is cleaner.

- **Platform team.** Owns shared engineering infrastructure — CI, build systems, shared libraries, tool configurations deployed company-wide. From a Team Topologies point of view, Platform is a *Platform team* and your team is a *Stream-aligned team* that consumes Platform's services. In AI-adoption terms: Platform owns the shared Cursor-rules deployment mechanism, the shared AGENTS.md convention, the shared MCP servers, the shared token-cost dashboard, the shared allowed-model list. Your roadmap is a *consumer* of Platform's work and sometimes a *contributor* back.
- **DevEx (Developer Experience).** Owns the measurement and quality-of-life layer for developers — DORA / DX Core 4 / SPACE metrics, developer-survey programmes, friction logs. In AI-adoption terms: DevEx is the natural owner of the team-productivity-and-ROI dashboard your roadmap feeds. [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) covers the measurement depth; DevEx is where the measurement infrastructure lives.
- **Product (`ai-augmented-product-manager`, peer, L30).** Owns customer-facing AI features. Where your team is *building* an AI feature the PM owns, the PM's product roadmap drives *what* and your team roadmap drives *how your team works on it*. Where your team is only *using* AI in internal work, Product is largely out of the loop — but you should still see them weekly, because product ROI framing and team ROI framing use the same reference reading (DX Core 4, SPACE, DORA, industry surveys from Chapter 4).
- **Security / `ai-risk-engineer` (peer, L25 in AI Governance family).** Owns engineered risk evaluation, red-team rigs, and guardrail infrastructure. In AI-adoption terms: when the roadmap moves a task into AI-augmented mode, Security is where the risk-posture question gets answered. You *commission* the risk evaluation; they *build* the rig. `ai-risk-engineer` is the technical peer; Security partners (CISO office, appsec) are the org-level stakeholders. Depth is linked from [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) and [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/).

A fifth partner — `ai-enablement-lead` (L45, AI Workforce) — is *above* you rather than sideways. Their shape is covered in the graduation hand-off section below.

### What each partner wants from your roadmap

Partner coupling is easier when you can state *what each partner wants to see in your roadmap* and give it to them without being asked.

- **Platform wants to see:** which shared mechanisms your team depends on (Cursor rules repo, AGENTS.md convention, shared MCP servers, token-cost dashboard), which team-local workarounds you currently have, and which workarounds you would retire if Platform owned the mechanism. This feeds Platform's prioritisation.
- **DevEx wants to see:** the handful of adoption + outcome metrics your roadmap commits to measuring, so DevEx can align them with the DX Core 4 / SPACE instrumentation they already run. Divergent per-team metrics are a cost on DevEx; shared metrics across teams let them see trends.
- **Product (PM peer) wants to see:** anywhere your team roadmap intersects a customer-facing AI feature on the product roadmap. Co-ownership of the intersection; neither of you owning all of it. The PM also wants a heads-up when your team's internal AI work could become a customer-facing capability — some product features start as team-internal tooling.
- **Security / `ai-risk-engineer` want to see:** the C5 data-handling boundary (from the human/machine contract, [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) Chapter 3), the risk-scored task sort (Chapter 2's blast-radius column), the specific eval commissioning plan (`mod-103`), and the incident-handling link ([`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/)). They need to know what evaluation rig you want and when, not just that one is coming.

Adding a half-page "partner view" to the roadmap — one short paragraph each — resolves most partner-coupling drift.

### Who owns what — the shared-infrastructure boundary

A persistent failure mode is to build team-local infrastructure that duplicates Platform work. A helpful frame: at team scope you own **team-specific *configuration*** of shared mechanisms; at Platform scope they own the **shared *mechanisms* themselves**. Table:

| Mechanism | Shared infrastructure (Platform-owned) | Team-specific configuration (you own) |
|---|---|---|
| Cursor rules | Deployment pipeline; linter integration; cross-team template | Your team's specific rules file for your repos |
| AGENTS.md convention | Repo-level convention, shared template, CI gate | Your team's AGENTS.md per repo |
| MCP server fleet | Shared MCP servers for shared tools (ticket system, docs, codebase, observability) | Your team's selection of which servers to wire in, with what scope |
| Allowed-model list | Enterprise-approved models and tiers | Your team's choice among the approved list |
| Token-cost dashboard | Instrumentation, aggregation, exec-roll-up | Your team's budget, alert thresholds, cost attribution |
| Prompt library / review templates | Shared starter library | Your team's team-specific prompts and review checklists |
| Eval rig | Shared eval infrastructure (`mod-103`) | Your team's golden-task set and regression set |

The rule of thumb: if the mechanism is generic enough that a second team would benefit, it belongs to Platform. If the thing is specific to your team's workflow, it belongs to you.

### Pilots that should graduate out of the team

A successful pilot (Chapter 3) has three possible futures: (1) team-wide rollout; (2) graduation to Platform / DevEx ownership of the mechanism, with your team as the reference user; (3) graduation to an org-wide enablement rollout owned by `ai-enablement-lead` (L45). The signals that distinguish these:

**Graduate to Platform (mechanism becomes shared infrastructure) when:**
- The pilot built a mechanism (a Cursor-rules convention, an AGENTS.md pattern, an MCP server configuration, a token-cost-attribution scheme) that a second team would adopt unchanged or with modest adaptation.
- The team-local version is a maintenance load that pulls you out of the manager role — if you are spending a day a week on tool-config plumbing, the mechanism belongs to Platform, not to you.
- A second team is asking for the same thing in their own roadmap.

The hand-off to Platform is not a hand-off of the *roadmap* — your team roadmap continues. It is a hand-off of *one mechanism* to shared ownership. Your team becomes a reference user of the shared version.

**Graduate to `ai-enablement-lead` (org-wide rollout) when:**
- The pilot's success is reproducible outside your team's context — the workflow does not depend on team-local norms or a specific IC's expertise.
- Rolling out the workflow to many teams is a *programme* (cadence, enablement content, measurement, change-management comms) rather than a *configuration* — i.e., the bottleneck is people, not infrastructure.
- The impact at team scope is large enough that org-wide roll-out has a credible ROI case.

The hand-off is a *package* — pilot charter, success evidence, ROI narrative, enablement artifacts, risks and known failure modes. The next section specifies what the package contains.

**Keep team-local (no graduation) when:**
- The workflow is genuinely team-specific — a team-of-analysts discipline-specific prompt library, a team-of-support-engineers knowledge-base-integration pattern.
- The impact is real but modest, and the team-local maintenance is low.

Deliberately not graduating is a legitimate choice. State it in the decision log.

### The graduation package to `ai-enablement-lead`

When a team pilot is graduating to an org-wide enablement rollout, you hand off a package. A workable package is one short artifact per item below, pinned together with a cover letter:

1. **Pilot charter.** The one-page pre-pilot charter from Chapter 3 — scope, cohort, horizon, success criteria, kill criteria, decision owner, data plan. Unchanged; this is what you committed to at the start.
2. **Evidence of success.** The measurements that landed against the committed success criteria: adoption rate, time delta, quality bar, cost. Honest about what did and did not clear the bar.
3. **Team-context signals.** Why this worked on your team. Team shape (size, discipline, seniority profile, in-flight stress), tool surface, review bar, enablement that preceded the pilot. The enablement lead needs this to decide what to replicate and what is team-specific.
4. **ROI narrative.** One paragraph. The team-level ROI framing from [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/), scaled to the org if the enablement lead takes it broad — with the assumptions stated so the enablement lead can re-score.
5. **Enablement artifacts.** The Cursor-rules file, AGENTS.md, prompt library, review checklist, data-handling note, 30-minute onboarding deck — whatever your team used to do the thing. These are reusable raw material; the enablement lead will adapt them, not copy them.
6. **Known risks and failure modes.** What nearly killed the pilot, what you watch for, what the kill criteria would catch. The enablement lead has to replan for failure modes at scale that you only had to defend against at team scale.
7. **Hand-off decision and open questions.** One short section: what you are proposing (graduate / graduate with adaptation / do not graduate) and what you are explicitly leaving to the enablement lead to decide (procurement, legal review at scale, cross-team sequencing).
8. **Your continuing role.** Explicit — reference user, cross-team enablement contributor, "do-not-call" after the hand-off, or a stated time-bounded advisory role. Ambiguity here produces the "whose problem is this?" emails three months later.

The package fits in 3–5 pages plus the artifact files. Longer is less read.

### Partner coupling at refresh cadence

Partner coupling is a weekly or bi-weekly conversation at team-manager scope, not a one-off. Reasonable cadence:

- **Weekly, 15 minutes with Platform lead.** What are you depending on; what is changing; where is friction. The 15-minute weekly keeps the roadmap coupled without the ceremony of a formal cross-team meeting.
- **Bi-weekly, 30 minutes with DevEx.** Metrics alignment; dashboards; anything flagged in [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/).
- **Weekly, 30 minutes with your PM peer.** Standing 1:1, same as any team-manager/PM peer pair. Intersection points flagged here.
- **Monthly, 30 minutes with `ai-enablement-lead`.** Pre-reads before each: what your team roadmap looks like, what pilots are in flight, what you might hand off this quarter.
- **Opportunistic with Security / `ai-risk-engineer`.** Before any task-sort change that moves a task into the AI-first or AI-assisted bucket on a workflow that carries risk; before commissioning an eval; immediately on any incident ([`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/)).

Writing the partner cadence into the roadmap is a tell that you have done the coupling work.

### A note on the product-manager-peer boundary

Chapter 1 named the top-level boundary against `ai-augmented-product-manager` (L30): PM owns product-side AI-feature adoption; team manager owns team-side workflow adoption. In day-to-day work, the boundary is tested in two places:

- **When your team ships an AI feature.** The PM's product-adoption data and your team's workflow-adoption data are *different* data sets, measured differently, and used for different decisions. The PM reads feature engagement and retention; you read team throughput and review-bar hold. Do not merge the dashboards.
- **When internal team tooling becomes customer-facing.** If your team's internal AI workflow could become a product offering, the right move is a sideways hand-off to the PM, not a one-person decision. State the signal in the roadmap and flag it in your 1:1 with the PM.

A clean boundary with the PM peer means neither of you re-litigates the other's roadmap each quarter.

## Example: a sketch of the partner-view section of a team roadmap

Illustrative; adjust for your org's partner function names:

> **Platform.** Depending on: the shared Cursor-rules deployment, the shared AGENTS.md convention, the shared allowed-model list. Asking for: a shared MCP server for our observability tool (currently team-local). Offering: our PR-description convention as a candidate for the shared template library. Cadence: weekly 15 with `@platform-lead`.
>
> **DevEx.** Metrics aligned with DX Core 4 (`@devex-lead`): adoption rate per AI-targeted task family, median review time per PR, reviewer-reported quality bar (reviewer survey n≥5/week), monthly token spend per IC. Dashboard owned by DevEx; team-specific thresholds owned by us. Cadence: bi-weekly 30.
>
> **Product (PM peer).** Intersection this quarter: the lakehouse-SQL pilot touches the forthcoming analyst-copilot feature. Co-ownership agreed; PM owns the feature roadmap, we own the team-workflow slice. Cadence: standing weekly 1:1.
>
> **Security / `ai-risk-engineer`.** Commissioning this quarter: golden-task eval set for PR descriptions and SQL skeletons (`@ai-risk-engineer`, under `mod-103`). Data-handling boundary: enterprise-SSO Cursor + Claude Code only; no personal accounts; no customer PII in prompts. Cadence: opportunistic; immediate on incident.
>
> **Enablement lead.** Likely graduation this quarter: the PR-description workflow, if the week-6 adoption and quality bars hold. Package draft dated 2027-01-25; decision call 2027-02-05 (`@enablement-lead` + `@manager`). Cadence: monthly 30.

Three short paragraphs plus a cadence note per partner. Fits half a page; carries the coupling; leaves no partner wondering what you expect of them this quarter.

## Summary

- The team roadmap is coupled to four partner functions — Platform, DevEx, Product (PM peer), Security / `ai-risk-engineer` — and one hand-off relationship upward to `ai-enablement-lead` (L45). Write that coupling into the roadmap; do not keep it in your head.
- Platform owns shared *mechanisms*; you own team-specific *configuration* of those mechanisms. A mechanism that benefits a second team belongs to Platform.
- A successful pilot has three futures: team-wide rollout, graduation to Platform ownership, or graduation to org-wide enablement rollout. Decide consciously; "no graduation" is a legitimate choice.
- Graduation to `ai-enablement-lead` is a *package* (pilot charter, evidence, team-context signals, ROI narrative, enablement artifacts, risks, hand-off decision, your continuing role). Short, honest, pinned together.
- Partner coupling is a cadence, not a one-off: weekly with Platform, bi-weekly with DevEx, weekly with PM, monthly with enablement lead, opportunistic with Security. Writing the cadence into the roadmap is the tell that the coupling exists.
- Hold the ownership line with the PM peer. Internal team workflow and customer-facing AI feature are different objects, measured differently, decided differently.
