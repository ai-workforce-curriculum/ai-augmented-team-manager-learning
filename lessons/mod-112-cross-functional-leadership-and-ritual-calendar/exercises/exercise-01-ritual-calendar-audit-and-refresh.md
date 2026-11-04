# Exercise 01 — Ritual Calendar Audit and Refresh

**Estimated effort:** 2 hours.

## Objective

Produce **v0.1 of your team's audited ritual calendar**: every ritual classified against [Lencioni's four meeting types](https://www.tablegroup.com/product/death-by-meeting/), anchored to a specific dashboard tile from [`mod-104`](../../mod-104-productivity-measurement-and-ai-roi/) (or a named gap-register / incident-class tile from [`mod-110`](../../mod-110-ai-governance-and-policy-at-team-scope/) / [`mod-109`](../../mod-109-accountability-incident-response-and-blameless-postmortems/)), with a calendar-budget line and explicit retirement decisions for rituals that are not earning their slots.

The calendar is the time-layer of the team operating system (Chapter 7). The methodological anchors are [Chapter 2](../02-the-ritual-calendar-under-ai-augmented-work.md) for the inventory, Lencioni classification, and tile-justification discipline, and [Chapter 5](../05-one-pager-and-decision-log-hygiene.md) for the decision-log entries that record material amendments.

## Prerequisites

- [Chapter 1](../01-the-operating-system-in-visible-form.md) — the four composed pieces of mod-112 and the Monday-morning successor test.
- [Chapter 2](../02-the-ritual-calendar-under-ai-augmented-work.md) — ritual inventory, Lencioni meeting-type classification, tile-anchor discipline, calendar-budget math.
- [Chapter 5](../05-one-pager-and-decision-log-hygiene.md) — decision-log template for recording retirements and amendments.
- Prior-module artifacts your team has produced:
  - [`mod-104`](../../mod-104-productivity-measurement-and-ai-roi/) dashboard — the tile names you will anchor rituals to.
  - [`mod-105`](../../mod-105-team-ai-enablement-programs/) stage ladder — informs cadence of enablement rituals.
  - [`mod-109`](../../mod-109-accountability-incident-response-and-blameless-postmortems/) incident retrospectives — triggers the incident retro ritual on the calendar.
  - [`mod-110`](../../mod-110-ai-governance-and-policy-at-team-scope/) gap register — provides tile anchors for governance retrospective.
  - [`mod-111`](../../mod-111-vendor-budget-and-tool-selection-at-team-scope/) tool registry — triggers quarterly tool-registry ritual.
- Access to the team's current calendar — meeting invites, standing holds, recurring events from the past four weeks.

## Problem statement

Your team's calendar accreted over time. Some rituals were added when the team was earlier in its enablement journey, some are inherited from the agile method the team uses, some were added by well-intentioned peers at launch, and some are drift. Every ritual costs the people in the room multiplied by the slot length multiplied by the frequency; the rituals that pay rent earn their cost by moving a specific dashboard tile, and the ones that do not have become a tax on heads-down maker time.

The failure mode the exercise prevents: a calendar audit that revalidates every ritual because "we always do it" and retires nothing. A calendar audit that meets the discipline is one that has *at least one retirement or material right-sizing* and that classifies every surviving ritual against Lencioni's four types with a named defended tile.

Scope: this is the *team's* ritual calendar. Cross-functional rituals your team attends but does not own (e.g., company all-hands, a sister team's demo you drop in on, a program-level forum owned by [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning)) are *in scope only as attended-time costs*, not as audit targets — you cannot retire a ritual you do not own. Note those rituals and their time cost, but do not audit them.

## Steps

1. **Enumerate every recurring ritual on the team's calendar.** Open the last four weeks of calendar. List every recurring event — including standups, planning, review, retro, 1:1s, office hours, CoP, dashboard reviews, eval reviews, incident retros, governance retros, tool-registry reviews, cross-functional syncs. For each, record: slot length, cadence (daily / weekly / biweekly / monthly / quarterly), attendee list, owner.
2. **Compute the annual cost per ritual.** Use the Chapter 2 formula: attendees × slot length × annual frequency. Sum into a total for the team's annual ritual cost. Compare the sum to the team's total annual capacity (headcount × ~2,000 person-hr/yr); compute the *percentage of capacity*.
3. **Classify each ritual against Lencioni's four types.** Daily check-in / weekly tactical / monthly strategic / quarterly off-site review. If a ritual spans two types, it is overloaded; mark it for split or re-scope in step 6.
4. **Fill the audit template for each ritual.** Per Chapter 2:
   - Ritual name
   - Cadence
   - Lencioni type
   - Attendees
   - Purpose (one sentence)
   - **Defended tile** — the specific [`mod-104`](../../mod-104-productivity-measurement-and-ai-roi/), [`mod-109`](../../mod-109-accountability-incident-response-and-blameless-postmortems/), or [`mod-110`](../../mod-110-ai-governance-and-policy-at-team-scope/) tile the ritual is meant to move
   - **Signal-of-decay** — what observable state indicates the ritual has stopped earning its slot
   - Owner
   - Last audit date
5. **Flag rituals without a defended tile or with a stale defended tile.** A ritual with no defended tile is a judgement call — justify the keep in one sentence or retire it. A ritual whose defended tile has not moved in a year is a decay signal; investigate before keeping.
6. **Make retirement / right-sizing / split decisions.** For each flagged ritual:
   - *Retire outright* — the signal the ritual defended is no longer at risk, and no replacement is needed.
   - *Right-size* — the content thinned but the forum is still needed; shift cadence, slot length, or attendees.
   - *Split* — the ritual is overloaded (weekly tactical pretending to be monthly strategic, or similar); split into two cleanly-classified rituals.
   - *Keep* — with a one-sentence justification recorded in the template.
7. **Write a decision-log entry for every material change.** Per Chapter 5's ADR-style template: context, decision, rationale, alternatives, reversal conditions, review date. Retirements and splits are material; cadence tweaks of established rituals are not.
8. **Rebuild the calendar in its refreshed shape.** Publish the updated slots. Communicate the changes to the team and to any cross-functional peer who attends an affected ritual. Where cross-functional rituals change, co-sign the change with the partner from Chapter 3.
9. **Measure the capacity reclaimed.** Compute the person-hr/yr saved by retirements and right-sizings. Record the number in the decision-log entries and in the next quarterly pre-read.
10. **Schedule the next audit.** Default: annual (next year, same quarter). Add quarterly spot-audit slots on the quarterly off-site. Record event triggers that fire an off-cycle audit (±2 headcount, major scope change, major process incident).

## Starter guidance

- **Calendar audits always surface at least one retirement.** If the exercise produces zero retirements, the discipline has not been applied — the "defended tile" test is binding; re-run it skeptically.
- **A ritual with no defended tile is a judgement call made in the open.** It is allowed; the discipline is that the decision is recorded, not that no such rituals exist.
- **Standup lengths drift.** A 5-minute check-in that reliably runs 25 minutes is a mis-classified tactical, not a long check-in. Either enforce the 5-minute discipline or re-classify to weekly tactical with an appropriate cadence.
- **Retros are inspection-and-amendment rituals.** Retros that discuss strategy are over-reaching the Lencioni classification; strategy is quarterly off-site territory.
- **Dashboard reviews are a legitimate ritual but need a tile.** A "dashboard review" that stares at tiles without producing amendments is a tile-reading club, not an audit. The defended tile of a dashboard review is usually "variance against expected", with signal-of-decay being "three consecutive reviews with no action items."
- **1:1 cadence is not a team-calendar choice alone.** Individual direct reports' needs vary ([`mod-107`](../../mod-107-skill-growth-anti-atrophy-and-career-development/) growth plans drive cadence); do not standardise 1:1 cadence in the audit without the directs' input.
- **Governance and tool-registry rituals are infrequent but load-bearing.** A governance retro at semi-annual cadence and a tool-registry review at quarterly cadence are both legitimate; do not retire them because they are rare.
- **Cross-functional rituals are harder to retire.** You do not unilaterally retire a ritual your PM or Design partner owns half of. Cross-functional retirements go through the Chapter 3 grid; co-sign.
- **The capacity reclaimed is a pre-read number.** The person-hr/yr saved by the audit is a credible line in the next quarterly pre-read's productivity section. Keep the number.

## Acceptance criteria

The refreshed calendar is complete when:

- Every recurring ritual on the team's calendar has a filled template with Lencioni type, attendees, purpose, defended tile, signal-of-decay, owner, and date.
- The annual cost per ritual is computed; the sum is expressed as a percentage of team capacity; the number is on the audit sheet.
- At least one retirement, right-sizing, or split is made, or an explicit written statement is produced that no changes are warranted and why (the latter is rare and skepticism is applied).
- Every material change has a decision-log entry (context, decision, rationale, alternatives, reversal conditions, review date, links).
- Rituals with no defended tile are explicitly noted; a one-sentence judgement-call justification is recorded for each.
- Cross-functional ritual changes are co-signed by the partner per Chapter 3 grid.
- The refreshed calendar is published to the team and attended partners; the communication links the audit template and the decision-log entries.
- The capacity reclaimed in person-hr/yr is computed and recorded.
- The next audit date and the event triggers for off-cycle audits are on the calendar.
- A change-log entry with authors, reviewers, and date; v0.1.

## Stretch goals

- **Calendar diff visualisation.** Produce a before / after view that shows the calendar's shape pre- and post-audit — slot counts per Lencioni type, person-hr/yr by category, retirements highlighted. Useful input to the next quarterly pre-read's "operating-system changes" line.
- **Cross-team comparison.** Compare your team's ritual cost (as % of capacity) against one sister team that has also run this exercise. Identify rituals one team has and the other does not; discuss whether the asymmetry is appropriate.
- **Partner retrospective.** For each cross-functional ritual that stays on the calendar, run a 20-minute retrospective with the counterpart. Confirm the ritual is earning its slot on both sides — a ritual earning its slot on your team but not on the partner's is a candidate for right-sizing.
- **Chapter 2 example as calibration.** Re-run Chapter 2's worked "retire the weekly AI tools sync" example against your calendar. Does your audit produce a similarly specific retirement, or does it stop at vague "trim some meetings" statements? Specificity is the test of discipline.
- **Attendance observability.** For each ritual, pull the last 8 sessions' attendance data from the calendar / Zoom / meeting tool. Rituals with consistently low attendance (<70% expected) are a decay signal before the defended tile moves; investigate and amend.
