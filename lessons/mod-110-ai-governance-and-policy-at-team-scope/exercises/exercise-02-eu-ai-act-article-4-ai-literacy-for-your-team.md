# Exercise 02 — EU AI Act Article 4: AI Literacy for Your Team

**Estimated effort:** 3 hours.

## Objective

Produce **v0.1 of your team's AI-literacy program**: a one-page policy document, a role-tier segmentation table, a module-to-tier mapping table, the LMS (or equivalent) curriculum spec, and the evidence-capture specification. The combined artifact discharges the deployer's [EU AI Act Article 4](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) obligation at team scope, in a form an audit can read.

The methodological anchor is [Chapter 3](../03-eu-ai-act-article-4-ai-literacy-at-team-scope.md), composed with [EU AI Office guidance](https://digital-strategy.ec.europa.eu/en/policies/ai-act) (including the Article-4 Q&A and the Living repository of AI literacy practices as published), the [IAPP AIGP](https://iapp.org/certify/aigp/) body of knowledge for content coverage, and the team's existing [`mod-105`](../../mod-105-team-ai-enablement-programs/) enablement artifacts.

> **Non-lawyer note.** This exercise produces curriculum and evidence shape — not a legal opinion. If your organisation's counsel has set specific Article 4 interpretation, follow counsel. If not, the output of this exercise is the team's defensible draft, which counsel can then review.

## Prerequisites

- [Chapter 3](../03-eu-ai-act-article-4-ai-literacy-at-team-scope.md) — the six dimensions, the seven-module content baseline, the role segmentation shape.
- [Chapter 2](../02-nist-ai-rmf-govern-translated-to-team-practice.md) — NIST AI RMF GOVERN 2.2, which this exercise's artifact fills.
- Your organisation's current AI-literacy policy, program-level curriculum, or program-level training obligation document. If none exists, the exercise flags this upward.
- Your team's current [`mod-105`](../../mod-105-team-ai-enablement-programs/) enablement artifacts (curriculum, bootcamp materials, 1:1 templates, CoP cadence).
- Your team's LMS access (Cornerstone, Workday Learning, Lessonly, Learnamp, Udemy Business, or whatever is in use), or the equivalent evidence-capture tool. If no LMS exists, name the fallback evidence store (shared drive with structured attendance logs, HRIS training field, or similar) and flag the gap.
- 30 minutes with your HR / people partner and 30 minutes with your governance partner (where each exists). HR partner validates evidence capture; governance partner validates coverage against the organisation's program-level curriculum.
- Counsel's existing position on Article 4 for your organisation, where available.

## Problem statement

Your team is operating AI-augmented workflows. The EU AI Act Article 4 obligation on your organisation as a deployer requires sufficient AI literacy among the team members operating or using those workflows. Depending on where your organisation sits, Article 4 may be a direct obligation (EU operations), an indirect obligation (EU customers or counterparties, or soft-law adoption by the organisation), or a defensible-practice input (US operations with EU exposure).

Whichever it is, the audit question is the same: *can you produce the team-scope training record for Article 4 on demand?* The exercise's deliverable is the artifact that makes "yes" the honest answer.

The common failure mode the exercise prevents: a training program that exists in practice (people have been trained — there were sessions, there are notes, there are Slack threads) but has no *evidence shape* — no LMS record, no role-tier structure, no module-to-tier mapping, no refresh cadence. The audit will not accept "we did a lunch-and-learn in July." The exercise's output is the structure that converts practice into evidence.

## Steps

1. **Read the organisation's current position.** Counsel's Article 4 interpretation (where it exists); the program-level AI-literacy curriculum (where it exists); the `head-of-ai-governance` program plan. Note what is set and what is not. If counsel has not set a position, the exercise's output is marked "draft pending counsel review" and routed upward.
2. **Inventory current team practice.** What training *has happened* in the last 12 months on AI topics? For each session or module: topic, audience, date, duration, delivery modality, evidence of completion. Most of this will be partial; capture what you can. The result is the baseline the policy has to improve on.
3. **Write the one-page policy.** Scope statement (who is covered); objectives (what the program ensures); segmentation (the role tiers); content coverage (the modules); cadence (initial + refresh); evidence capture (where records live); sign-off (manager; governance partner; HR partner); change-log. One page.
4. **Author the role-tier segmentation table.** Three or four tiers (awareness, operational, reviewer, manager). For each: which roles / levels are in the tier; required modules; baseline hours; refresh cadence. The table is page 2 of the policy artifact.
5. **Author the module-to-tier mapping.** The seven baseline modules from Chapter 3 (A: AI foundations, B: team-specific stack, C: regulatory landscape, D: accountability / review / HITL, E: data / IP / confidentiality, F: incident recognition, G: affected-person considerations). For each module: content outline (bulleted; 5–10 bullets per module); tier applicability; delivery modality; estimated duration per tier; author / owner. Modules A, C, E, F, G usually inherit from the organisation's program-level curriculum with team-specific overlays; Module B is almost always team-authored; Module D inherits from [`mod-103`](../../mod-103-review-standards-and-eval-commissioning/) and [`mod-106`](../../mod-106-workflow-redesign-and-agent-delegation/).
6. **Author Module B in detail.** Team-specific stack walkthrough: which tools the team uses (name and version), which model(s), what each tool is used for, what each tool is *not* for, what the C5 data-handling rules say (per [Chapter 6](../06-data-ip-and-confidentiality-practice.md)), what the HITL checkpoints are (per [`mod-106`](../../mod-106-workflow-redesign-and-agent-delegation/)), what the review checklist says (per [`mod-103`](../../mod-103-review-standards-and-eval-commissioning/)). This module cannot be inherited; it is team-specific. Author it as a 30–60-minute session or as a 30-minute async plus a 30-minute Q&A.
7. **Specify the LMS curriculum.** A specific LMS object (curriculum ID, or equivalent) that:
   - Ties each person to their tier.
   - Ties each module to its tier.
   - Captures completion per person per module with date.
   - Fires reminders per the refresh cadence.
   - Produces an exportable per-person CSV for the audit.
   If the LMS cannot do one of these, name the gap and the fallback (manual CSV from a shared drive; HRIS training field). Do not pretend the LMS does something it does not.
8. **Specify evidence capture for off-LMS activity.** Lunch-and-learns, ad-hoc sessions, incident-driven micro-sessions. For each: specific attendance log template; specific store; the dated-attendance pattern. Even off-LMS activity has evidence shape or it does not count.
9. **Specify the refresh cadence.** Annual full refresh (default); quarterly or semiannual content-delta refresh; incident-driven micro-session after each mod-109 retrospective. Enforce via the LMS.
10. **Sign-off and change-log.** Manager; governance partner; HR partner. v0.1 with a date. Where applicable, counsel review before the program is called "Article 4 compliant" — until counsel review, the program is "defensible Article 4 draft practice".
11. **Pilot the segmentation on current team members.** Run each team member through the segmentation table; confirm the tier they are in and the modules they need. Surface outliers (people whose actual work does not match the tier; people who have skills the segmentation does not map to; contractors or partners who touch the workflow but are not on the team roster).
12. **Review with HR partner, governance partner, counsel (as applicable).** Record specific corrections.

## Starter guidance

- **"Sufficient" is a design decision, not a rule.** The Act does not prescribe hours or modules. Your defensibility rests on documenting the decision, not on matching a benchmark. 2 hours of awareness tier with a clear rationale is defensible; 20 hours with no rationale is not.
- **Role tiers are cumulative.** The manager tier includes every reviewer module; the reviewer tier includes every operational module. This is easier for the LMS and easier for the audit.
- **Module B cannot be inherited.** The team-specific stack walkthrough is the module no program-level curriculum can replace. Author it specifically; refresh it when the stack changes.
- **The LMS is the load-bearing artifact.** If your organisation does not have an LMS, the fallback is a structured per-person training log in the shared drive or HRIS, with the same five fields (who, what, when, version, next-due). The fallback is defensible if it is consistent; it is not defensible if it exists in Slack.
- **Off-LMS learning counts but only if logged.** A lunch-and-learn without an attendance log is not evidence. The one-page policy explicitly names what off-LMS evidence looks like.
- **The regulatory-landscape module (C) should be tier-appropriate.** The awareness tier does not need Article-14-depth; the manager tier does. Over-teaching the awareness tier is a waste; under-teaching the manager tier is a gap.
- **Affected-person coverage (G) is context-specific.** If the team's AI touches only internal engineering workflows, Module G is light. If the team's AI touches customer-facing decisions or employment-screening, Module G is substantial and probably inherits from the organisation's program-level affected-person framing.
- **Length guidance.** One page policy; one page segmentation table; one page module-to-tier mapping; one to two pages Module B outline; one page LMS specification; one page off-LMS evidence specification. 5–8 pages total.
- **Do not claim regulatory compliance without counsel.** The exercise produces a defensible draft. The "Article 4 compliance" label attaches after counsel reviews. This is both legally correct and good practice.

## Acceptance criteria

The program is complete when:

- A one-page policy document names scope, objectives, segmentation, content coverage, cadence, evidence capture, sign-off, and change-log.
- A role-tier segmentation table lists every tier with its roles, required modules, hours, and refresh cadence. Every member of the team maps to a tier.
- A module-to-tier mapping lists seven (or more) modules (A–G), each with content outline, tier applicability, duration, modality, author / owner.
- Module B (team-specific stack) has a content outline that names the team's tools, models, HITL checkpoints, and data-handling rules by reference to [Chapter 6](../06-data-ip-and-confidentiality-practice.md) and [`mod-106`](../../mod-106-workflow-redesign-and-agent-delegation/).
- An LMS curriculum (or equivalent) is specified with the five capture capabilities, OR gaps are named with fallbacks.
- Off-LMS evidence capture is specified with templates and storage locations.
- Refresh cadence is specified with enforcement mechanism.
- Sign-off records for manager, governance partner, HR partner (and counsel where applicable) are attached. Where counsel review has not happened, the artifact is labelled "defensible draft pending counsel review".
- The segmentation has been piloted against the current team roster with outliers surfaced.
- The policy and tables are filed at a specific location in the team's wiki, with a link in the Chapter 7 upward-packet template.
- A path from each row in Chapter 2 crosswalk (GOVERN 2.2 and GOVERN 3.2) cites this artifact.

## Stretch goals

- **Author Module G in depth for affected-person scenarios.** If the team's workflows touch regulated-use-case territory (per [Chapter 4](../04-articles-14-and-50-human-oversight-and-transparency.md)), Module G needs more than a reference. Author the content outline specifically, in collaboration with counsel and the governance partner.
- **Author the micro-session template.** The post-mod-109-retrospective 15–30-minute micro-session template that converts each incident into a trainable moment. Compose with [`mod-109` Ch. 7](../../mod-109-accountability-incident-response-and-blameless-postmortems/07-team-scope-retrospective-and-ownership-boundary.md).
- **Integration with onboarding.** The 30-day onboarding plan for a new hire on the team; the first 7 days includes awareness-tier content; by day 30 the IC is at operational tier. Compose with [`mod-105`](../../mod-105-team-ai-enablement-programs/) Day 0/30/60/90 structure.
- **Extended segmentation for non-team roles.** If the team's AI workflows are consumed by product partners, customer-success staff, or other non-team roles, extend the segmentation to cover them (awareness tier at minimum).
- **Benchmark against the EU AI Office Living repository.** The [Living repository of AI literacy practices](https://digital-strategy.ec.europa.eu/en/policies/ai-act) compiles practices from operators. Compare your team's design against practices from similar-sized teams or similar industries. Record differences and justify.
- **Compose with [Exercise 01](exercise-01-nist-ai-rmf-govern-to-team-practice.md).** The GOVERN 2.2 row of the crosswalk should cite this artifact specifically. The gap register should include any gaps this exercise surfaces (missing LMS capability, missing counsel position, missing Module G depth).
- **Author a candidate-facing version.** For contractors and partner-team members who touch the workflow and need awareness-tier training, author a self-service public-URL-safe version that does not expose the firm's internal stack details.
