# Exercise 05 — The Upward Evidence Packet for the Governance Program

**Estimated effort:** 2 hours.

## Objective

Produce **v0.1 of your team's upward evidence packet**: the single quarterly artifact the manager produces for `senior-ai-governance-architect` (L50) and `head-of-ai-governance` (L60) that composes the outputs of Exercises 01–04 (plus the Chapter 4 Article 14 / 50 sheets) into the shape the governance program consumes.

The methodological anchor is [Chapter 7](../07-upward-evidence-packet-and-ownership-boundary.md), composed with the four prior-exercise outputs. The packet's design respects the different audiences — architect, head of governance, counsel, risk-engineering peer — reading different sections of the same document.

## Prerequisites

- [Chapter 1](../01-the-governance-problem-at-team-scope.md) — the scope of the module.
- [Chapter 7](../07-upward-evidence-packet-and-ownership-boundary.md) — the packet shape and ownership boundary.
- Outputs of [Exercise 01](exercise-01-nist-ai-rmf-govern-to-team-practice.md) (NIST GOVERN crosswalk), [Exercise 02](exercise-02-eu-ai-act-article-4-ai-literacy-for-your-team.md) (AI-literacy evidence), [Exercise 03](exercise-03-microsoft-rai-and-google-aip-team-mapping.md) (industry-framework mapping), [Exercise 04](exercise-04-data-and-ip-handling-policy.md) (data-and-IP policy). If any is still a draft, the packet labels the section accordingly.
- The Chapter 4 Article 14 and Article 50 workflow sheets for every in-scope workflow.
- [`mod-109`](../../mod-109-accountability-incident-response-and-blameless-postmortems/) incident retrospectives for the quarter in question.
- 30 minutes with `senior-ai-governance-architect` (or `head-of-ai-governance`) to validate the packet shape against what the program actually consumes.

## Problem statement

The Chapter 7 packet is the single artifact the governance program consumes from the team. Without it, the team's four content exercises produce artifacts the program cannot easily aggregate. With it, the program rolls up team evidence into its program view with low cost.

Different readers of the packet want different sections first. The executive summary and the gap register are the shared surface. The crosswalk, the mapping, and the Article 14/50 sheets are the technical substrate. The incident index is the reality check.

The exercise's deliverable is the template and a filled v0.1 using the outputs of Exercises 01–04. Future quarters produce the next version by substitution.

The common failure mode the exercise prevents: a packet that is the four exercises concatenated. Concatenation produces a 60-page unreadable document; the governance program will not read it; the packet will not improve practice. The packet's point is composition — the summary, the gap register, the cross-cuts — not concatenation.

## Steps

1. **Fetch the Chapter 7 packet shape.** The section list in Chapter 7. Confirm the shape with `senior-ai-governance-architect` or `head-of-ai-governance`; if the program has a required shape, match it; if not, use Chapter 7's shape as the default.
2. **Author the executive summary.** One page. Three parts:
   - Team name, scope, period covered; sign-off.
   - What changed since last packet (new in-scope workflows, new vendors, resolved gaps, new gaps). For v0.1 this is the "baseline" summary.
   - Three to five bullets of material facts the governance program should know.
3. **Compose the NIST GOVERN crosswalk section.** Copy the crosswalk from Exercise 01. Include the leading gap register slice.
4. **Compose the Article 4 AI-literacy evidence section.** Pull the curriculum version, segmentation table, per-tier completion rate, LMS reference, and new-hire onboarding compliance from Exercise 02. The LMS link is a reference, not a full export (the full export is an appendix).
5. **Compose the Article 14 and Article 50 sections.** Pull the workflow sheets from Chapter 4. Include the summary table (workflow, classification, oversight role, last review, next review). The full sheets are appendix / linked.
6. **Compose the industry-framework mapping section.** Copy the mapping tables from Exercise 03. Include each framework's gap register slice.
7. **Compose the data-and-IP policy section.** Pull the matrix (current version), the vendor clause-reader summary (referenced, not duplicated), the model-card index, the IP sidecar version, and the data-leak incident count from Exercise 04 and [`mod-109`](../../mod-109-accountability-incident-response-and-blameless-postmortems/).
8. **Compose the incident and retrospective index.** From [`mod-109`](../../mod-109-accountability-incident-response-and-blameless-postmortems/): count of incidents by class, links to retrospectives, regression-fixture-backfeed status.
9. **Author the consolidated gap register.** Every unfilled or route-upward cell from sections 2–8. One table. Columns: gap; source section; owner (role); owner (person); due date; routing (upward / sideways / team-backlog); notes. Order by routing; upward-first.
10. **Author the change-log.** Material changes since last packet. For v0.1, this is the "baseline" entry.
11. **Compose the appendices.** Links to full crosswalk, full mapping tables, full workflow sheets, full matrix, full training-record exports. Links, not duplicates.
12. **Validate with the architect or head of governance.** 30 minutes. Walk the packet. Specific question: *is this consumable? which sections do you read first, and in what order? what would you change about the shape?* Record corrections and amend.
13. **Finalise and file.** v0.1 with authors, reviewers, date. File at a specific location in the team's governance drive and in the program's governance-program-level repository. Communicate the shape to the team.
14. **Set the next-packet cadence.** Default: quarterly. Next-packet date in the change-log. Trigger conditions for off-cycle packets (new in-scope workflow, new vendor with material clause change, framework update, incident with program-wide implications).

## Starter guidance

- **The packet is a composition, not a concatenation.** The exec summary, the gap register, and the incident index are what distinguish a readable packet from an unreadable one. Spend half the exercise's time on these three.
- **The gap register is the register of truth.** Every gap from every prior exercise lives here. Nothing surprise-appears later. Nothing goes missing.
- **Links over duplicates.** The crosswalk should live once (in Exercise 01's filing location) and be linked from the packet. If the packet contains a full copy and the source drifts, the packet is lying. Link to the source of truth.
- **Named sign-off is load-bearing.** The packet is signed by the manager. Where the organisation's practice includes joint sign-off with the `ai-risk-engineer` peer or the `head-of-ai-governance` delegate, include their signatures. Unsigned packets do not get read.
- **Executive summary is the 30-second read.** Whatever the audience, they should learn the most important three to five things from reading it.
- **Gap register is the plan.** Every gap has an owner and a date. Gaps without owners do not get resolved; gaps without dates stay open forever.
- **Audience-aware section ordering.** Default order is in Chapter 7. For specific program partners, you may re-order (e.g., counsel's copy leads with Article 14/50; the architect's copy leads with the crosswalk). Do not re-structure; re-order.
- **Appendices are optional for the reader.** The main body should stand on its own.
- **Volume calibration.** v0.1 for a new team is heavy on gaps and change-log notes; this is expected. v0.2+ should show reduction in gaps or at least ownership assignment.
- **Do not replace mod-109 retrospectives.** The incident index points at retrospectives; it does not re-author them.

## Acceptance criteria

The packet is complete when:

- An executive summary on page 1 names team, scope, period, what changed, three to five material-fact bullets, and named sign-off.
- The NIST GOVERN crosswalk section includes the full crosswalk and the leading gap register slice.
- The Article 4 AI-literacy evidence section includes curriculum version, segmentation, per-tier completion rate, LMS reference, new-hire onboarding compliance.
- The Article 14 and Article 50 sections include summary tables and link to the full workflow sheets.
- The industry-framework mapping section includes each committed framework's mapping and gap register slice.
- The data-and-IP policy section includes the matrix version, clause-reader reference, model-card index, IP sidecar version, data-leak incident count.
- The incident and retrospective index covers incident counts by class, retrospective links, and regression-fixture-backfeed status.
- A consolidated gap register names every gap with owner (role and person), due date, routing, and notes. Ordered upward-first.
- A change-log entry names material changes since the last packet (or the "baseline" entry for v0.1).
- Appendices link to full artifacts without duplication.
- The architect or head of governance has reviewed and provided specific corrections.
- A change-log entry names authors, reviewers, and date. v0.1.
- The packet is filed at a specific location and communicated to the team.
- The next-packet date and trigger conditions are named.

## Stretch goals

- **Templatise the packet.** Produce a repeatable template that can be substituted-into for the next quarter in 30 minutes rather than 2 hours. Store it alongside the v0.1.
- **Automate the gap-register consolidation.** If the four prior exercises store their gap registers in structured format, auto-generate the consolidated register. Manual consolidation each quarter is brittle.
- **Produce a one-page executive version.** For reader who will never read the full 15–25 pages (board-level, `chief-ai-officer`), produce a one-page summary that `head-of-ai-governance` can hand up. The summary is a compact executive summary + top 5 gaps + recent incident class distribution.
- **Benchmark across sister teams.** If the organisation has multiple teams producing packets, the `senior-ai-governance-architect` rolls up. Request the roll-up and compare: which gaps are common across teams (program-level opportunity); which are team-specific (local issue).
- **Set up the retrospective cadence.** The semiannual governance retrospective (per Chapter 7) is scheduled on the [`mod-112`](../../mod-112-cross-functional-leadership-and-ritual-calendar/) ritual calendar. Attach the retrospective-note template (four questions) as an appendix of the packet so that next semester's retrospective runs against the right questions.
- **Compose with the [`mod-111`](../../mod-111-vendor-budget-and-tool-selection-at-team-scope/) vendor registry.** The data-and-IP section should cross-reference the vendor registry entries; where the registry has moved or updated, the packet reflects the change.
- **Pre-fill against a historical quarter.** Pull the team's most recent historical quarter (before the packet existed) and produce a retrospective packet. Surfaces what the team *would* have evidenced if the packet had existed. Calibrates the next quarter.
- **Observe the reader.** After the packet is delivered, ask the reader what they actually read, in what order, and what question it answered. Feed this back into the next-quarter shape.
