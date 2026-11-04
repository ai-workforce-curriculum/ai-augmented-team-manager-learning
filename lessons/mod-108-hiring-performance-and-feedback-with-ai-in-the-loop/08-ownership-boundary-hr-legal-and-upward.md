# Chapter 8 — Ownership Boundary: HR, Legal, and Upward to L45 / L50

> *The hiring work, the performance work, and the workforce-planning work in this module all sit at team scope. Three domains sit next to that scope — HR / employee-relations partners (formal process), legal counsel through HR (opinion and regulator response), and the levels above (cross-team architecture, org-wide workforce planning). This chapter names the boundary against each and the handoffs that cross it. Do neither more nor less than your job.*

## Motivation

Every module in the track closes with an ownership-boundary chapter because the level-40 team-manager role lives at the intersection of several specialties and overreach is one of the common failure modes. mod-108 has more adjacent domains than most of the other modules — HR owns formal employment actions, legal counsel owns opinion and regulator response, and the levels above own cross-team and org-wide workforce planning. The boundary is sharp against each; this chapter names each explicitly.

[`mod-107` Chapter 8](../mod-107-skill-growth-anti-atrophy-and-career-development/08-ownership-boundary-with-hr.md) names the general HR boundary in detail for the skill-growth domain; mod-108 Chapter 8 does not re-derive that material. It extends the boundary into the specific hiring-and-performance territory where the handoffs differ.

## Core concepts

### Boundary 1 — HR partnership

The division in [`mod-107` Chapter 8](../mod-107-skill-growth-anti-atrophy-and-career-development/08-ownership-boundary-with-hr.md) holds here. The specific mod-108 extensions:

**What stays on the manager's side (hiring):**

- Interview-loop design and the rubric.
- Rater calibration on the rubric.
- Writing offer-letter justification material (cost case, role / level rationale).
- Deciding the role scope and the day-to-day work the hire will do.
- The hire / no-hire recommendation after the loop runs.
- Candidate conversations about the role, the team, and the work (within the structured-interview frame).

**What belongs to HR (hiring):**

- The offer letter itself, including compensation terms, benefits, start date, and legal language.
- Candidate communications about compensation specifics, benefits, and employment terms.
- Background checks, employment verification, and the formal background-check process.
- Candidate notice under NYC Local Law 144 (Chapter 6).
- Reasonable-accommodation handling under the ADA (Chapter 6).
- Formal response to candidate complaints or adverse-action notices.
- Record retention for hiring decisions per EEOC / Title VII obligations.

**What stays on the manager's side (performance):**

- 1:1 cadence and content (Chapter 4).
- Monthly reflective and quarterly written feedback artifacts (Chapter 4).
- The underperformance root-cause drill before formal escalation (Chapter 5).
- The quarterly ladder-aligned performance review the manager drafts.
- Promotion-case authoring and the supporting packet.
- The calibration-defence note (Chapter 3).

**What belongs to HR (performance):**

- The performance-review template and process mechanics.
- Performance improvement plans (PIPs) — formal document, timeline, review cadence, consequences.
- Terminations.
- Compensation calibration at scale (the band structure, cross-team equity enforcement).
- Levelling and promotion process mechanics (committee structure, quorum, appeals).
- Any conversation that touches employment-law-exposed territory (harassment, discrimination claims, protected-class considerations, retaliation concerns).

### Boundary 2 — Legal counsel through HR

Legal counsel is almost never a direct contact for the team manager; the route is through HR. The specific questions that route to legal:

- **Scope determinations under compliance regimes.** Does this specific tool fall under NYC LL 144's AEDT definition? Is this feature an Annex III high-risk use under EU AI Act? Does this term in the vendor contract adequately address data handling? These are legal determinations.
- **Regulator inquiries.** Any contact from the EEOC, a state civil-rights body, the NYC DCWP, an EU AI Office, or a comparable regulator goes through HR to legal. The manager does not respond directly.
- **Candidate complaints that reference protected classes, discrimination, or specific legal frameworks.** The complaint may be informal. The route is still through HR to legal, not through the manager's informal response.
- **PIP drafting with employment-law exposure.** A PIP for an IC in a protected class, following a leave, after a complaint, or under other employment-law-visible circumstances goes through HR with counsel's involvement.
- **Vendor contracts with data-handling and AI-training-on-candidate-data clauses.** The specific language belongs to counsel through the procurement / legal workflow.

The manager's job is to flag and route. The manager does not compose legal opinion and does not put the organisation into a position where a decision-of-record is made on the manager's own reading of the law. If the question has the word "legal" in it, route.

### Boundary 3 — Upward to L45 (enablement lead) and L50 (engineering manager)

Three categories of work route upward:

**Cross-team workforce planning.** Rebalancing headcount across teams, consolidating duplicate roles, moving ICs between teams, cross-team role-architecture decisions. The team manager owns their own team's headcount request (Chapter 7); the cross-team question belongs to the manager's own manager, or to the L45 enablement lead when the question is about enablement-at-scale, or to the L50 engineering manager when the question is about engineering-management-of-managers scope.

**Organisational levelling architecture.** Adding, removing, or re-defining ladder levels; shifting comp bands; changing role definitions across the organisation. The team-scope ladder refresh in Chapter 3 composes with the organisation's ladder; wholesale changes are L45 / L50 / HR work.

**Org-wide hiring policy.** Policies that affect how every team in the organisation runs its interview loop, how every team handles AI-use disclosure, how every team's performance reviews incorporate AI leverage. The team manager writes team practice (Exercises 01 and 02); org-wide codification is L45 and above.

The upward handoff is a short note — one paragraph — the manager writes to the upward owner. It names the observation, the team-scope action (if any), and the specific upward question. The owner at the next level decides the scope.

### Boundary 4 — Peer handoff to sideways roles

Three peer / adjacent domains touch mod-108:

- **[`ai-augmented-product-manager`](https://github.com/ai-engineering-curriculum/ai-augmented-product-manager-learning) (peer, L30).** Hiring product managers or product-adjacent roles on an engineering team touches the peer domain. The interview-loop redesign principles compose; the specific role content is the peer track's.
- **[`ai-risk-engineer`](https://github.com/ai-engineering-curriculum/ai-risk-engineer-learning) (peer, L25).** Engineered bias evaluation of hiring AI tools, red-team work on vendor tools, guardrail construction around AI used in the hiring loop — the peer domain. The team manager commissions and acts on findings; does not re-build.
- **Security / IT security.** Data-handling security review for hiring AI vendors — including candidate PII handling, resume data retention, and video/transcript storage — is security's domain through the procurement process. The manager flags; security owns the review.

### Boundary 5 — Out of scope entirely

- **IC-level AI-tool fluency.** Cursor / Claude Code / Copilot prompt patterns, agent authoring, eval-rig construction at the IC tier are [`ai-assisted-software-engineer`](https://github.com/ai-engineering-curriculum/ai-assisted-software-engineer-learning) (L25). The manager uses the fluency as a prerequisite; does not re-teach.
- **General people-management fundamentals.** The 1:1 cadence structure, feedback mechanics generally, hiring fundamentals generally — assumed as prerequisite (see [`PREREQUISITES.md`](../../PREREQUISITES.md)). The module augments the fundamentals for AI augmentation; does not re-derive them.
- **Legal opinion itself.** Named explicitly in Chapter 6 and repeated here. Counsel's work.

### The three handoffs that are specifically mod-108

Across mod-108, three operational handoffs recur. Each has a specific manager-side pre-work and HR-side ownership shape.

**Handoff A — the compliance-review handoff for a new hiring AI tool.** Manager's pre-work: the three-question assessment from Chapter 6 (substantially assists an employment decision; demographic data consumed / inferred; jurisdictions). Routed to: HR, who coordinates with legal counsel on scope determination and with vendor procurement on contract. Manager's follow-up: pause the tool's use until the compliance review is complete.

**Handoff B — the formal performance process handoff (PIP conversation with HR).** Manager's pre-work: two quarters of documented growth conversation (Chapter 4 feedback artifacts), the documented Chapter 5 root-cause drill with workflow/tooling causes excluded or addressed, and the specific pattern the manager is observing. Routed to: HR as the open-question Handoff 1 conversation from [`mod-107` Chapter 8](../mod-107-skill-growth-anti-atrophy-and-career-development/08-ownership-boundary-with-hr.md). Manager's follow-up: if HR and the manager jointly decide to open a PIP, the manager's documentation protocol shifts per that chapter's Handoff 3.

**Handoff C — the role-architecture handoff upward.** Manager's pre-work: the observation (what's shifting and why), the team-scope action the manager is already taking, the specific upward question. Routed to: the L45 enablement lead or L50 engineering manager, depending on the question's shape (enablement-at-scale vs. manager-of-managers). Manager's follow-up: continue operating at team scope within the current role definitions; the upward owner decides whether the organisation-wide answer is different.

### What the manager must *not* do at the boundary

Many of these are restatements of [`mod-107` Chapter 8](../mod-107-skill-growth-anti-atrophy-and-career-development/08-ownership-boundary-with-hr.md); included here for the mod-108 slice.

- **Do not promise a candidate anything that is HR's to commit to.** Compensation specifics, start dates, benefits, employment terms. The manager can speak to the role, the team, the work; HR speaks to the offer.
- **Do not take a candidate complaint to resolution without HR.** Even a mild informal complaint that references protected classes or specific legal frameworks is an HR escalation moment.
- **Do not open an informal PIP.** Named in Chapter 5 and in [`mod-107` Chapter 8](../mod-107-skill-growth-anti-atrophy-and-career-development/08-ownership-boundary-with-hr.md). Scheduled improvement check-ins with explicit consequences are a PIP; run them through HR.
- **Do not approve a new AI tool in the hiring pipeline without the Chapter 6 compliance review.** Even when the tool is cheap, time-pressured, and seems obviously benign.
- **Do not interpret the compliance regimes.** Chapter 6 is manager-practice; the legal interpretation is counsel's.
- **Do not route everything upward.** The opposite failure. Team-scope decisions belong to the team manager — the ladder refresh, the interview-loop redesign, the headcount request. Running everything up through L45 / L50 wastes the levels above and signals that the team manager is not operating at the manager's own scope.
- **Do not frame HR as adversary.** HR as partner is the working mode. Adversarial framing produces brittle handoffs and worse outcomes.

### Common failure modes at the boundary

- **The manager has no HR partner relationship.** Many managers meet HR only during a formal process — which is the worst possible time to meet them. Build the partnership before a specific case is needed; the HR partner being someone the manager talks to monthly changes the quality of the handoffs when they matter.
- **The manager escalates to HR as venting, not as partnership.** The partner relationship corrodes under venting; the partnership works under framed questions.
- **The manager hides behind HR.** "HR said we can't do X." The manager owns their own judgement; HR composes with it. If HR said something the manager disagrees with, open the conversation.
- **The manager escalates upward too fast.** Team-scope decisions are the manager's. An exec stakeholder who sees every mid-level hiring decision escalated upward loses trust in the manager's scope.
- **The manager does not escalate upward when warranted.** Role-architecture signals that would belong to L45 get implemented at team scope and create precedents the organisation didn't intend.
- **The manager treats legal counsel as an obstacle.** Counsel composes with manager practice; the compliance work is the context, not a blocker. Managers who treat it as a blocker tend to work around it, which is the specific failure mode the regimes are designed to prevent.

### The signs the boundary is holding

Three signals that the manager is operating at the right scope:

- **HR partnership is specific and current.** The HR partner knows the team, the recent patterns, and where the manager is on the open questions. The handoffs are short, specific, and productive.
- **Legal counsel is rarely contacted directly but is engaged when warranted.** Routing through HR is the pattern. When counsel is engaged on a specific vendor review or regulator inquiry, the manager's role is to inform and respond to specific questions, not to lead the engagement.
- **The level above knows what's at team scope.** Upward handoffs are explicit; the L45 / L50 owner knows what the manager is seeing and has either picked up the cross-team question or has given the manager the boundary to handle it at team scope.

## Example: three handoffs in one quarter

Composite example; calibration, not a case study.

A manager runs a quarter of hiring and performance work. Three handoffs cross the boundary:

**Handoff A — new AI interview-scoring tool proposed by a recruiter partner.** The recruiter forwards a vendor demo of a tool that "scores structured-interview transcripts for consistency with the organisation's rubric." The manager runs the three questions from Chapter 6. Scores candidates substantially: likely trigger. Consumes transcript data including demographic correlates: in scope for adverse-impact analysis. Jurisdictions include NYC, California, two EU member states: all three regimes in scope. The manager flags the tool to HR and asks for a compliance review. HR routes to legal; the review takes six weeks; outcome is "defer adoption until vendor completes EU conformity assessment and we draft the LL 144 candidate notice." The manager pauses the vendor conversation and continues with the human-only loop.

**Handoff B — a mid-level IC on a two-quarter growth-conversation pattern.** The manager has run two quarters of feedback artifacts; the Chapter 5 drill surfaced a composed workflow + modest human-growth root cause. The workflow intervention closed the workflow gap in Q2; the residual human-growth signal (Axis A moves still thin) remains. The manager opens the Handoff-1 conversation with HR: *"this is where I am, this is what I've tried, here's the drill output; is this a pattern I continue to work on in 1:1s or structure differently?"* HR assesses with the manager and recommends another quarter of structured 1:1 work with a specific framing. No PIP opened. The manager documents the HR-advised framing and continues.

**Handoff C — role-architecture signal upward.** Over the quarter the manager has observed that the team's work mix has shifted toward outside-frontier agent-operations work. The team's current role categories do not cleanly describe an IC whose work is to operate and maintain internal agent systems. The manager writes a one-paragraph note to the L45 enablement lead describing the observation, the team-scope actions already taken (routing-matrix updates, specific pairings), and the specific upward question: *"is 'agent operations engineer' a role the organisation is considering authoring? If yes, how should I slot the next senior hire against that shape? If no, I'll continue hiring under the existing 'senior engineer' category and treating the agent-operations work as a scope of that role."* The L45 owner replies in a few days; the organisation is planning to author the role in the next fiscal cycle; the manager's next hire is informed by that upcoming shape.

Three handoffs, three different boundary routes, one quarter. Each handoff kept the manager's work at the manager's scope and the shared decisions at the appropriate joint ownership.

## Summary

- **The mod-108 boundary runs against four partners:** HR (formal employment actions), legal counsel through HR (opinion and regulator response), L45 / L50 upward (cross-team and org-wide), and L25 / L30 peer / sideways (risk engineering, product-management, security).
- **Manager owns:** interview-loop design and rubric, 1:1 cadence and content, feedback artifacts, root-cause drill, promotion-case authoring, headcount request and levelling rationale, team-scope compliance practice, upward handoff notes.
- **HR owns:** offer letters and compensation specifics, candidate notice (LL 144), ADA accommodations, PIP documents and process, terminations, performance-review template mechanics, calibration process, record retention per Title VII.
- **Legal counsel owns (through HR):** compliance scope determinations, regulator responses, specific candidate complaints, vendor contract language, legal interpretation of the regimes.
- **Levels above own:** cross-team workforce planning, org-wide levelling architecture, org-wide hiring policy codification.
- **Three recurring handoffs:** compliance-review for new tools, formal performance-process (PIP conversation), role-architecture signal upward.
- **Must-nots:** promise HR's commitments, resolve candidate complaints without HR, open informal PIPs, approve new AI tools without compliance review, interpret the regimes, escalate team-scope decisions upward, frame HR as adversary.
- **Signals the boundary is holding:** specific and current HR partnership, legal counsel rarely contacted directly but engaged when warranted, the level above knows what's at team scope.
- **Composes with** [`mod-107` Chapter 8](../mod-107-skill-growth-anti-atrophy-and-career-development/08-ownership-boundary-with-hr.md) (general HR boundary), [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) (incident handoffs are separate from performance handoffs), [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) (broader team-scope governance).
