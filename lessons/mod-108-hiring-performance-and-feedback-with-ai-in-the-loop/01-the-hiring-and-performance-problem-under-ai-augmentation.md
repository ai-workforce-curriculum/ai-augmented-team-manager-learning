# Chapter 1 — The Hiring and Performance Problem Under AI Augmentation

> *The interview loop you ran last year scored candidates on a signal — unassisted output quality — that half your real-world work no longer produces. The performance review you wrote last cycle differentiated on a metric — individual throughput — that generative AI is already compressing. Both artifacts still exist in your HR system. Neither measures what you now need to measure. This module rewrites both at team scope, inside the legal framing that applies in 2026.*

## Motivation

The 25-posting evidence base that seeds this track names *AI-era workforce planning (team size, role-mix, hiring, levelling under AI augmentation)* as requirement **R9**, posting frequency **0.16** (see [`JOB_REQUIREMENTS.md`](../../JOB_REQUIREMENTS.md)). The theme sits below the 0.30 posting-frequency threshold the track applies to posting-based requirements. It is kept at team scope regardless, for a specific reason: the level-40 team manager is the operator who signs the offer letter, writes the performance review, opens the performance improvement plan with HR, and files the headcount request. The decisions that flow from those documents are made with or without a clear policy on how AI changes them. Running without a policy is a decision; this module is the alternative.

Two pillars make the module. The first pillar is **hiring**: the structured-interview mechanics that remain the strongest evidence-based predictor of job performance (Google re:Work / Project Oxygen) have to compose with a world in which the candidate has an agent running next to them during the technical screen and the compliance regime for automated employment decisions (EEOC, NYC Local Law 144, EU AI Act) has been codified. The second pillar is **ongoing performance management**: 1:1s, feedback, goal-setting, and underperformance framing in a team where measured output compression (Noy & Zhang) and tenure-concentrated gains (Brynjolfsson, Li, Raymond) are now empirical facts, not predictions. Chapters 2 and 6 cover the hiring pillar; Chapters 3–5 cover the performance pillar; Chapter 7 covers the workforce-planning artifact and the upward boundary; Chapter 8 names the HR / legal / level-45+ ownership edges.

This chapter does three things. First, it names the shape of the hiring-and-performance problem under AI augmentation — what is new, what is not, and what the manager has to re-author. Second, it names the five pieces of mod-108 that respond to it. Third, it draws the scope boundary against HR (formal processes), legal counsel (opinion), and the levels above (org-wide and cross-team scope).

## Core concepts

### What is new, what is not

Hiring and performance management are domains with a long, mature practitioner literature — most of it still correct. The following are **not** new under AI augmentation:

- The evidence base for structured interviews. Google's Project Oxygen and the broader industrial-organisational psychology literature on interview validity (structured interviews outperform unstructured interviews on job-performance prediction; same-question-same-rubric interviews reduce adverse impact) remain correct. Google re:Work's *Guide to Structured Interviewing* is the primary reference.
- The architecture of performance management. Grove's *High Output Management* on the manager's role in 1:1s and output measurement, the OKR practice popularised at Intel and Google (Doerr, *Measure What Matters*), and the DORA / SPACE / DX Core 4 productivity frameworks (mod-104) are load-bearing and continue to apply.
- The division of labour with HR. Formal performance improvement plans, terminations, and employment-law-exposed decisions are HR-owned work. The boundary described in [`mod-107` Chapter 8](../mod-107-skill-growth-anti-atrophy-and-career-development/08-ownership-boundary-with-hr.md) is the boundary here, restated for the hiring domain in Chapter 8 of this module.

What is **new** is a short list that nevertheless reshapes most of the operational detail:

- **The interview candidate has an agent.** The candidate's day-to-day work is AI-augmented; refusing AI during the technical screen measures something the role does not require, while permitting it uncritically measures the agent rather than the candidate. Chapter 2 is the operational response.
- **Measured output compresses across the team.** Noy & Zhang's (Science 2023) finding on dispersion compression means the signal the promotion committee reads at calibration time is noisier than it was. Chapter 3 is the ladder-criteria response.
- **The underperformance question has a new axis.** Before AI, underperformance was a human-skill or motivational question. After AI, three root causes compete for the explanation: the human skill gap, the workflow mismatch (routing matrix wrong — mod-106), or the tooling gap (wrong tools, wrong access, wrong enablement — mod-105). Chapter 5 is the root-cause framing.
- **The compliance regime for AI-in-hiring is in effect in 2026.** EEOC guidance on automated employment decisions (2023), NYC Local Law 144 bias audit requirements for automated employment decision tools (effective 2023-07-05), and the EU AI Act's Article 6 and Annex III classification of hiring AI as high-risk (entering phased application 2026–2027) are not theoretical. Chapter 6 covers what the manager has to understand to set team practice; legal opinion itself stays with counsel.
- **Workforce planning now has to narrate AI leverage.** Headcount requests, levelling calibrations, and role-mix shifts are made against a cost structure that includes AI tooling spend and a productivity baseline that is moving. Chapter 7 is the artifact.

### The two pillars, briefly stated

**Pillar 1 — Hiring.** Interview-loop redesign under AI-augmented candidates, scoring live-coding and live-writing when the candidate has agents on hand, and compliance framing for automated employment decisions. The structured-interview reference (Google re:Work) is the methodological anchor; SHRM's AI-in-HR materials and the EEOC / LL 144 / EU AI Act references are the compliance anchors. The deliverables are the interview-loop redesign artifact (Exercise 01) and the compliance checklist (Exercise 05).

**Pillar 2 — Ongoing performance management.** 1:1 cadence, feedback, goal-setting (OKRs or KPIs) that reflects AI leverage, underperformance root-cause framing, and PIP contracts with HR when warranted. The methodological anchors are Grove's *High Output Management*, the OKR literature, and DORA / SPACE / DX Core 4 under AI-augmented conditions (mod-104). The deliverables are the levelling-criteria refresh (Exercise 02), the OKR-under-AI-leverage artifact (Exercise 03), and the underperformance root-cause drill (Exercise 04).

The two pillars compose through a shared artifact — the team's levelling/promotion rubric — which is drafted in [`mod-107` Chapter 6](../mod-107-skill-growth-anti-atrophy-and-career-development/06-career-ladder-under-ai-augmentation.md) and run against in both the interview loop (Pillar 1) and ongoing performance (Pillar 2). The division is: mod-107 writes the ladder; mod-108 runs the hiring and performance mechanics against it.

### The five pieces of mod-108

A mod-108-literate manager produces five composed artifacts over the course of this module.

| Piece | What it does | Chapter(s) | Exercise |
|---|---|---|---|
| **Interview-loop redesign** | The team's interview loop rewritten for AI-augmented candidates — allowed-AI policy per stage, structured-interview rubric, live-coding / live-writing scoring under agent use | 2 | [Exercise 01](exercises/exercise-01-interview-loop-redesign-under-ai.md) |
| **Levelling-criteria refresh** | The team-scope rubric amendment (composing with the mod-107 ladder) that weights judgement, system understanding, mentorship, and ownership so AI-amplified throughput does not crowd them out | 3 | [Exercise 02](exercises/exercise-02-levelling-criteria-refresh.md) |
| **OKRs / KPIs with AI leverage** | A goal-set authored at team scope that reflects AI leverage — team-level outcomes and individual-level growth goals, where "used AI effectively" is a *how*, not a *what* | 4 | [Exercise 03](exercises/exercise-03-okrs-with-ai-leverage.md) |
| **Underperformance root-cause drill** | A diagnostic that separates the three root causes (human, workflow, tooling) so the manager works the right lever — and names when to co-escalate to HR | 5 | [Exercise 04](exercises/exercise-04-underperformance-root-cause-drill.md) |
| **LL 144 / EEOC / EU AI Act compliance checklist** | A team-practice checklist that names which assistive AI the team uses in hiring, whether it meets the NYC AEDT / EEOC / EU AI Act triggers, what is logged, and what gets escalated to legal | 6 | [Exercise 05](exercises/exercise-05-ll144-eeoc-compliance-checklist-for-your-team.md) |
| **Headcount justification exec pre-read** | The workforce-planning artifact at team scope — role-mix shift, AI-leverage assumptions, cost framing, upward-scope handoff — one-pager for the exec stakeholder | 7 | [Exercise 06](exercises/exercise-06-headcount-justification-exec-pre-read.md) |

Chapters 1 and 8 bracket the module: Chapter 1 opens with the scope and grounding; Chapter 8 closes with the HR / legal / upward ownership boundary.

### What this module is *not*

The adjacent-but-distinct work matters.

- **Not a legal opinion.** Chapter 6 covers what the manager has to understand to set team practice under EEOC, NYC Local Law 144, and EU AI Act exposure. Legal opinion on any specific tool, contract, or employment decision belongs to counsel through HR. The chapter is explicit on the line.
- **Not an HR-process course.** Formal employment actions — performance improvement plans, terminations, compensation freezes, adverse-action notices — belong to HR / employee-relations partners. The chapters give the manager-side framing; Chapter 8 names the handoffs.
- **Not a cross-team workforce-planning course.** This module covers team-scope workforce planning (R9 at team scope). Workforce planning across an engineering organisation, or role-architecture work that reshapes the levelling ladder across teams, belongs to [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) (level 45) or [`ai-engineering-manager`](https://github.com/ai-engineering-curriculum/ai-engineering-manager-learning) (level 50). Chapter 7 names the upward-scope handoff.
- **Not an atrophy course.** Deliberate practice, anti-atrophy carve-outs, and career-development-ladder *authoring* live in [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/). mod-108 *uses* the ladder mod-107 authors; it does not re-author it.
- **Not an AI-tool-selection course.** Which specific AI products the team allows candidates to use, which performance-review tools the organisation licenses, and vendor procurement generally live in [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/). mod-108 names *categories* of tooling and the compliance framing; the vendor-selection decision is composed from there.
- **Not an IC-recruiting-sourcing course.** Sourcing strategy, employer branding, recruiter partnering, and talent-brand work are important and are not covered here. The module starts at the interview-loop design stage and runs through to ongoing performance. The L45 track covers sourcing at scale.

### Where mod-108 sits in the track

Back-links:

- The role contract authored in [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) names the manager's responsibility for hiring, levelling, and performance at team scope; mod-108 operationalises those responsibilities.
- The review standards from [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) are the standard the live-coding / live-writing rubric inherits from in Chapter 2.
- The productivity measurement work in [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) is what Chapter 4's OKR work reads from when it writes team-level outcome goals.
- The enablement programme in [`mod-105`](../mod-105-team-ai-enablement-programs/) is one of the three root causes Chapter 5 separates; underperformance that is actually an enablement-gap is a mod-105 fix, not an HR process.
- The workflow redesign in [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) names the routing matrix; Chapter 5 separates "wrong routing" from "wrong IC."
- The ladder authored in [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/) is the standard Chapter 3 extends for hiring and ongoing performance reviews.

Forward-links:

- The accountability and post-mortem work in [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) is where an incident caused by an IC's AI-deference pattern is handled; the manager's separate growth-assessment is a mod-108 / mod-107 question. mod-109 is explicit on the blameless frame.
- The AI governance work in [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) sets the policy context Chapter 6's compliance checklist composes with; Article 4 of the EU AI Act (AI literacy) in particular interacts with both modules.
- The ritual calendar in [`mod-112`](../mod-112-cross-functional-leadership-and-ritual-calendar/) is where the performance-review cadence, the 1:1 cadence, and the quarterly calibration meeting land on the team calendar.

Sideways-links:

- HR partnership: see Chapter 8. Formal processes belong to HR; the manager-side framing is this module.
- Legal counsel: see Chapter 6. Compliance framing belongs to the manager; legal opinion belongs to counsel through HR.
- Up to [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) (level 45) for org-wide workforce planning, cross-team levelling architecture, and sourcing strategy beyond a single team; up to [`ai-engineering-manager`](https://github.com/ai-engineering-curriculum/ai-engineering-manager-learning) (level 50) for manager-of-managers scope on hiring and performance.

## Example: the review packet that stopped differentiating

A single composite example to make the problem concrete; treat as calibration, not a case study.

A team manager runs the usual Q4 performance-review cycle. The organisation's template has four rubric axes: impact, craft, collaboration, ownership. The manager writes six reviews. On impact, every IC on the team hits or exceeds the prior year's number — throughput is up across the board, deployment frequency is up, review latency is down. On craft, the manager is less sure: the PRs look clean, but the manager has a hard time distinguishing the senior IC's PR from the mid-level IC's PR on the artifact alone. On collaboration, the manager notes everyone is responsive in Slack and shows up to meetings. On ownership, the manager has one strong case — a senior IC who caught a subtle bug at review time that would have shipped — and five that are generic.

The manager submits the reviews. Calibration goes badly: two of the six reviews are challenged by peer managers who think the reviews over-rate the ICs on impact relative to their peers. The manager, defending in calibration, notices that *impact* now means "produced a lot of PRs" across the organisation and that the differentiation the review was supposed to produce — "who is operating at the next level?" — is not being produced. The signal that was supposed to differentiate is quieter than the noise introduced by output compression. The *one strong case* on ownership — the review-catch — is the only part of any of the six reviews that reads differently from what a mid-level IC's review would read.

The managerial lesson is not *"the reviews are bad."* It is that the review template (inherited, unchanged) is producing a flatter distribution of signal than the calibration process can absorb, and the one axis that still differentiates — the specific judgement move at review time — is under-represented in the template. Chapter 3 is the rubric-amendment response; Chapter 4 is the goal-set response; Exercise 02 is the artifact.

## Summary

- R9 (AI-era workforce planning, hiring, and levelling) sits at **0.16 posting frequency**, below the 0.30 threshold. It has a dedicated module at team scope because the level-40 team manager signs the offer letter and writes the performance review — running without a policy is a decision.
- **Two pillars:** hiring (interview-loop redesign + compliance) in Chapters 2 and 6, ongoing performance management (levelling, goals, underperformance, PIPs) in Chapters 3–5. The pillars compose through the mod-107 ladder.
- **What is not new:** the structured-interview evidence base ([Google re:Work](https://rework.withgoogle.com/guides/interviewing-leverage-work-sample-tests/) / [Project Oxygen](https://rework.withgoogle.com/guides/managers-identify-what-makes-a-great-manager/)), the architecture of performance management ([Grove](https://www.hachettebookgroup.com/titles/andrew-s-grove/high-output-management/9780679762881/), the OKR literature, [DORA / SPACE / DX Core 4](https://dora.dev/research/)), and the division of labour with HR.
- **What is new:** AI-augmented candidates in the interview loop, output-dispersion compression ([Noy & Zhang](https://www.science.org/doi/10.1126/science.adh2586)), the three-root-cause framing of underperformance (human / workflow / tooling), and the 2026 compliance regime ([EEOC](https://www.eeoc.gov/laws/guidance/select-issues-assessing-adverse-impact-software-algorithms-and-artificial), [NYC Local Law 144](https://www.nyc.gov/site/dca/about/automated-employment-decision-tools.page), [EU AI Act Article 6 + Annex III](https://eur-lex.europa.eu/eli/reg/2024/1689/oj)).
- mod-108 produces five artifacts: the **interview-loop redesign** (Exercise 01), the **levelling-criteria refresh** (Exercise 02), the **OKRs / KPIs with AI leverage** (Exercise 03), the **underperformance root-cause drill** (Exercise 04), the **LL 144 / EEOC / EU AI Act compliance checklist** (Exercise 05), and the **headcount justification exec pre-read** (Exercise 06).
- mod-108 is *not* a legal-opinion course (Chapter 6; opinion stays with counsel), not an HR-process course (Chapter 8; formal actions link to HR), not a cross-team workforce-planning course (links to L45+), not an atrophy course (ladder authored in [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/)), and not an AI-tool-selection course (links to [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/)).
