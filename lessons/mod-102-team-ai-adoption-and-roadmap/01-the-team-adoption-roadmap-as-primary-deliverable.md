# Chapter 1 — The Team AI-Adoption Roadmap as Your Primary Deliverable

> *"Drive team-level AI adoption and workflow redesign." Three in four postings in the sample ask for exactly this. Read that as: this is the artifact you will be measured on.*

## Motivation

Across the 25-posting sample that seeded this track, requirement theme **R1 — drive team-level AI tool adoption and workflow redesign — appeared in 76% of the postings** (see [`JOB_REQUIREMENTS.md`](../../JOB_REQUIREMENTS.md)). No other requirement comes close to that frequency. If the hiring market is coherent about anything for this role, it is coherent about this: the manager owns a **team-level AI-adoption roadmap**.

Most managers who try to write that roadmap for the first time get stuck in one of three ways. They write a **tool list** (we will buy Cursor, Copilot, Claude Code) and call it a roadmap. They write a **rallying memo** (we are going all-in on AI this year) and call it a roadmap. Or they write a **feature-level product plan** that belongs to their PM peer, not to them. None of those is the artifact. This chapter names what the artifact actually is, what belongs in it, what does not, and how it earns its keep against an exec read.

The downstream chapters sharpen individual slices: the jagged-frontier task sort (Chapter 2), the pilot/rollout and opt-in/mandate choices (Chapter 3), industry-survey calibration (Chapter 4), the platform hand-off (Chapter 5), and the exec-facing artifact set (Chapter 6). This chapter is the frame.

## Core concepts

### The roadmap's four questions

A team-level AI-adoption roadmap answers four questions, in this order. If any one is missing, it is not a roadmap, it is a wish.

1. **What are we going to automate — and what are we deliberately *not* going to?** Not "where could AI help" but "which concrete tasks, on which workflows, for which roles, are we moving onto an AI-augmented path this quarter." The not-list is as load-bearing as the list.
2. **In what order?** The sequencing — which pilot starts in week 1, which graduates to a team rollout in week 6, which waits for next quarter, and why. A roadmap without an order is a backlog with ambition.
3. **With whom?** Who pilots, who reviews, who partners from Platform / DevEx / Product / Security, and who is the named owner at each step. "The team" is not a named owner.
4. **How will we know it worked — and how will we know it did not?** The success + kill criteria for each step. A measure-nothing roadmap is a vibe. A measure-everything roadmap is a stall. A roadmap names a handful of metrics, says what counts as success, and says what causes a roll-back.

Everything else in the artifact — the exec one-pager, the pilot charters, the decision log — is a supporting document that serves one of those four answers.

### What the roadmap is *not*

Four common deliverables are often confused with the roadmap and are not it:

- **A tool procurement plan.** Which seats, which tier, which vendor is a procurement conversation owned at team scope in [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/). The roadmap consumes the procurement outcome; it does not substitute for it.
- **A product plan for an AI feature.** Features your team ships to customers are owned by your peer `ai-augmented-product-manager` (L30, AI Workforce family). The roadmap is about how your team *works*, not what your team *ships*.
- **An org-wide enablement program.** Multi-team rollout, cross-team coordination, procurement at scale, and company-wide change management are owned by `ai-enablement-lead` (L45). Your roadmap is one team's slice. Chapter 5 is the hand-off.
- **A policy document.** NIST AI RMF crosswalks, EU AI Act Article 4 translation, data-handling rules — these live in the human/machine contract (see [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) Chapter 3) and the governance crosswalk in [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/). The roadmap *references* those; it does not replace them.

Confusing any of the above with the roadmap is the fastest way to spend a quarter writing the wrong document. If an exec reads your roadmap and asks "what is this really — a tool plan? a product plan?" you have mis-framed it.

### The anatomy — seven sections, one page

A workable team-level AI-adoption roadmap fits on one legible page or two short ones. The headings are:

1. **Scope.** The team (name, size, discipline), the horizon (one quarter or two), the owner (you).
2. **The task sort.** The output of Chapter 2's jagged-frontier exercise — what is in-scope for AI drafting this horizon, what is deliberately out-of-scope, with one-sentence rationale per line.
3. **The sequence.** The ordered list of pilots and rollouts across the horizon with named owners, review partners, and start/end dates. Chapter 3 is the method behind this list.
4. **Adoption mode per step.** Opt-in vs. mandate vs. default-on, decided per step, with the change-management stance stated. Chapter 3 again.
5. **Success and kill criteria.** The handful of measurements per step — adoption, time saved, quality bar, cost — plus the "we roll this back if…" line. Chapter 4 keeps these calibrated against the industry; [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) is the measurement depth.
6. **Platform / DevEx / Product / Security partners.** Who you are coupling to, what you are asking for, what you are offering back. Chapter 5 is the method; the explicit hand-off contract to `ai-enablement-lead` sits here too.
7. **Decision log stub.** The three-to-five decisions already made with date, owner, and one-line rationale — so the roadmap carries its own history and does not drift invisibly.

That is the whole artifact. One page does the job; two pages is still legible to a VP in two minutes. Three pages is a sign something else is in scope — move it to a supporting doc and link.

### The decision about *what to automate* is prior to *how*

A failure mode of this role is to pick tools, then look for problems. The right order is:

1. **Sort the team's tasks** — which classes AI should be routed to first, which classes humans should stay on, which classes are contested. Chapter 2 is the method; Dell'Acqua's *jagged technological frontier* is the grounding.
2. **For each AI-targeted task, pick the adoption mode** — pilot first, then rollout? opt-in or mandated? default-on? Chapter 3.
3. **Only then pick the tools and the configuration** — the roadmap says "these tasks go onto an AI-augmented path"; the tooling (Cursor rules, Copilot settings, Claude Code configuration, bespoke agents) is downstream of that decision. Deep tool mechanics live in [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) (workflow redesign and agents) and [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) (vendor + budget).

When you stay in this order, two things fall out naturally. First, the roadmap is defensible against "why this and not that" questions from leadership — the answer is in the task sort, not in a tool preference. Second, the roadmap survives model and tool churn, because it is written in terms of tasks, not product names. A model deprecation does not force a re-write; a tool migration is a parameter change inside one step.

### Ownership boundary with your product-manager peer

Your peer `ai-augmented-product-manager` (L30, AI Workforce family) also talks about "adoption" and also writes "roadmaps." Mark the boundary explicitly so you can draw it in a conversation:

| Axis | You (`ai-augmented-team-manager`, L40) | PM peer (`ai-augmented-product-manager`, L30) |
|---|---|---|
| Object | Your team's *internal workflow* | A product's *customer-facing AI feature* |
| "Adoption" means | ICs on your team using AI in their daily work | Users of the product engaging with an AI feature |
| ROI framing | Team-level: throughput, quality, cost, satisfaction | Product-level: feature engagement, retention, revenue impact |
| Key artifact | Team AI-adoption roadmap (this module) | AI feature roadmap (owned there) |
| Shared reading | DX Core 4 / SPACE / DORA, industry surveys | Same industry surveys, interpreted for the product |

Where you overlap deliberately: when your team is building the AI feature the PM owns, the PM's roadmap drives *what* ships and your roadmap drives *how your team works* on it. You co-own the connection, not either doc.

### Grounding in the posting evidence and in the authoritative references

Two anchors keep the roadmap honest:

- **Posting evidence.** The 25-posting sample in [`JOB_REQUIREMENTS.md`](../../JOB_REQUIREMENTS.md) uses recurring language — "drive team-level AI adoption," "sequence pilots vs. rollouts," "partner with Platform / DevEx," "run change management," "measure impact" — in R1 (0.76) and in closely related themes R4 (measurement, 0.40), R5 (enablement, 0.36), and R7 (workflow redesign, 0.28). The vocabulary in your roadmap should match that language, so a hiring manager, a VP, or a cross-functional partner reads the artifact and recognises the shape.
- **Authoritative references.** Dell'Acqua et al. *Navigating the Jagged Technological Frontier* (Chapter 2); Microsoft Work Trend Index, McKinsey State of AI, GitHub Octoverse, Stack Overflow Developer Survey (Chapter 4); Kotter's change-management sequence and Rogers's *Diffusion of Innovations* (Chapter 3); Team Topologies for Platform / Stream / Enabling-team boundaries (Chapter 5). These are the inputs the roadmap stands on; they are not the roadmap itself.

A good roadmap cites both. The posting evidence tells leadership "this is the deliverable the market asks for." The authoritative references tell leadership "this is the way we are going to do it."

## Example: a one-paragraph sketch of a 10-engineer team's Q1 roadmap

Treat this as calibration for length and shape, not a template to adopt:

> **Scope.** Payments platform team, 10 engineers, Q1 2027, owned by `@manager`.
>
> **Task sort.** AI-augmented this quarter: PR description drafting, test skeletons, ADR first drafts, on-call runbook edits, in-code refactors behind existing coverage, SQL authoring against the lakehouse. Not this quarter: incident post-mortems, migration sequencing, security review, employee feedback.
>
> **Sequence.** Weeks 1–3 pilot (3 ICs) of a Cursor-rules + AGENTS.md convention on the payments-api repo; weeks 4–6 team rollout on payments-api if adoption + review-bar hold; weeks 7–9 extend to payments-worker; weeks 10–12 commission a golden-task eval set with [`ai-risk-engineer`](https://github.com/ai-governance-curriculum/ai-risk-engineer-learning) peer and tune.
>
> **Adoption mode.** Opt-in in weeks 1–3; default-on with opt-out in weeks 4–12; no mandate this quarter.
>
> **Success / kill.** Target: ≥70% of eligible PRs touch the AGENTS.md flow by end of week 6; median review time per PR holds or improves; reviewer-reported quality bar holds (reviewer-survey, n≥5/week); token cost under seat budget. Kill: any sustained quality regression or reviewer-burnout signal.
>
> **Partners.** Platform team owns the Cursor-rules deployment mechanism (hand-off agreed with `@platform-lead`); DevEx owns the token-cost dashboard; AI-enablement-lead (`@enablement-lead`) consulted on whether the rollout should graduate org-wide in Q2.
>
> **Decisions so far.** 2027-01-04: scope to payments-api first (@manager — lowest risk, highest signal). 2027-01-07: no mandate this quarter (@manager — team norms + change-fatigue from last re-org).

One paragraph, legible to the team and to a VP, and every sentence is defensible against "why this and not that?"

## Summary

- R1 (76% of the sample) names the team AI-adoption roadmap as the manager's primary deliverable. Treat it as the artifact you will be measured on.
- The roadmap answers four questions: *what* to automate, *in what order*, *with whom*, *how we will know it worked*. All four must be present.
- Seven sections fit on one page: scope, task sort, sequence, adoption mode, success/kill, partners, decision-log stub.
- The roadmap is *not* a tool plan, not a product plan, not an org-wide enablement program, not a policy document. Confusing any of those with the roadmap is the standard first-quarter failure mode.
- Decide *what* to automate before *how* — tasks first (Chapter 2), sequence second (Chapter 3), tools third ([`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/), [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/)).
- Hold the ownership line against your PM peer (feature roadmap, not workflow) and the hand-off to `ai-enablement-lead` (org-wide, not team).
