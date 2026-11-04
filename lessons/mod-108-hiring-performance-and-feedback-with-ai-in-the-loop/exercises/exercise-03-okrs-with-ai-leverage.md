# Exercise 03 — OKRs (or KPIs) With AI Leverage

**Estimated effort:** 2 hours.

## Objective

Produce **v0.1 of your team's quarter OKR set under AI augmentation**: a 2–3-page artifact containing one team-scope OKR composed with your organisation's goal-setting template, three IC-scope OKRs for three archetypal ICs on the team (one junior, one senior, one staff — or the closest equivalents), and a one-page writing-rules note that documents the principles used so the team can author future OKRs consistently.

The deliverable is the goal-set the manager runs the quarter against, references in monthly 1:1s, and uses as the input to the quarterly written feedback artifact from [Chapter 4](../04-performance-management-with-ai-in-play.md). The methodological anchors are [Doerr's OKR practice](https://www.whatmatters.com/) and [Grove's *High Output Management*](https://www.hachettebookgroup.com/titles/andrew-s-grove/high-output-management/9780679762881/) composed with the AI-augmentation adaptations in Chapter 4.

## Prerequisites

- [Chapter 4](../04-performance-management-with-ai-in-play.md) — the OKR adaptations, the 1:1 rotation, the feedback cadence.
- [Chapter 3](../03-levelling-criteria-refresh.md) — the ladder axes IC-scope OKRs calibrate against.
- Your team's **current quarter OKR set** (or KPI set, if your organisation uses KPIs instead) and the organisation's goal-setting template.
- Your team's mod-104 dashboard state (DX Core 4 / SPACE / DORA / cost dashboard) — the team-scope OKR reads from this, so knowing what the dashboards currently show is the starting point.

## Problem statement

Pre-AI OKR authoring in engineering teams typically produced two patterns the chapter is explicit about not repeating under AI augmentation: team-level OKRs that mixed outcomes with throughput mechanisms ("ship the migration by Q2 by reducing PR cycle time 20%"), and IC-level OKRs that were effectively throughput targets dressed as outcomes ("author 20 design docs; ship 25 features"). Under AI leverage both patterns get worse: throughput compresses across the team (Noy & Zhang), the mechanism-as-outcome framing becomes gameable because the mechanism is easily increased, and the IC-level targets reward the exact signal the mod-107 atrophy work is trying to counter.

The AI-augmentation adaptation is specific. Team-scope OKRs name outcomes (customer-visible or system-state outcomes) and treat AI leverage as a *how* in a mechanism key result (or omit the mechanism entirely). IC-scope OKRs compose with the team OKR and weight ladder-aligned growth moves: specific judgement artifacts, specific mentorship outcomes, specific review-standard contributions.

The common failure mode this exercise prevents is specific: writing an OKR that reads *"increase AI tool adoption to 90% on the team"* or *"reduce PR cycle time 30% via AI"* and discovering six months in that the metric went up, the business outcome did not, and the IC incentive structure now rewards the atrophy behaviour. Strip the mechanism out of the OKR; leave the outcome.

## Steps

1. **Pull the team-scope outcome.** Name the one or two customer-visible or system-state outcomes the team is accountable for this quarter. Phrase as outcomes, not activities. If an outcome is phrased as an activity ("do the migration"), rewrite as a state ("migration cutover complete; downstream consumers stable for 60 days post-cutover").
2. **Write one team-scope OKR.** One objective, two to four key results. Key results split into two categories:
   - **Outcome KRs** (the thing the team is accountable for).
   - **Mechanism KRs** (optional; the specific way the team is making the outcome true that is worth naming). Mechanism KRs may reference AI leverage *as a how* — "judgement-weighted review pass applied to 100% of migration PRs" is a mechanism KR that references the mod-103 review standard and composes with the team's AI use. Mechanism KRs never read "use AI more" or "increase adoption"; those are activity metrics, not mechanisms.
3. **Write three IC-scope OKRs**, one for each of: one junior-tier IC, one senior-tier IC, one staff-tier (or closest-equivalent) IC on your team. Compose each with the team OKR and with the IC's ladder-axis growth path. Structure:
   - Objective: typically ladder-aligned at senior and above (*"grow into senior-tier Axis A evidence over the cycle"*) and more outcome-aligned at junior (*"contribute to the migration's in-frontier workstream"*).
   - 2–4 key results. For senior / staff: at least one axis-aligned growth KR (narratable judgement moves, review-standard amendments, mentorship-of-judgement outcomes). For junior: at least one outcome KR tied to the team OKR. For all levels: at least one KR that is specifically observable (not aspirational).
4. **Pressure-test every KR against the mechanism-as-outcome trap.** For each KR, ask: *"if someone goosed this metric with no regard to the underlying outcome, would the KR still read as success?"* If yes, the KR is a mechanism dressed as an outcome; rewrite.
5. **Pressure-test every KR against the throughput trap.** For each KR, ask: *"am I measuring 'did more' or 'did the right thing'?"* If the former, consider whether the KR belongs; if it does, pair it with a quality KR so the metric cannot be gamed.
6. **Write the one-page OKR writing-rules note.** Four to six rules the team will apply to future OKRs, grounded in the adaptations from Chapter 4. Examples: *"AI usage is the how, not the what; no OKR reads 'use AI more.'"* *"IC-scope OKRs weight ladder-aligned growth moves at senior and above."* *"Team-scope OKRs name outcomes customer-visible or system-state."* *"Every KR has a quality pair or is not a throughput KR."* The note is the team's shared standard; it compounds across quarters.
7. **Walk the OKRs through the monthly 1:1 cadence.** For each of the three IC-scope OKRs, write one example 1:1 conversation prompt: how will the manager and IC discuss progress on this OKR in the next monthly reflective 1:1 from Chapter 4? If the OKR doesn't support a specific 1:1 conversation prompt, it is probably miscalibrated.
8. **Co-review with a peer manager and one senior IC.** Thirty minutes each.
   - Peer manager: *"are the team-scope OKRs calibrated to our current baseline? Any OKR that reads 'use AI more' hidden in disguise?"*
   - Senior IC: *"does the senior / staff IC-scope OKR match what you would see as a growth-year objective for yourself?"*
9. **Finalise and share with the team.** OKRs are meaningless if the team does not know what they are. The share includes the writing-rules note so the team understands the pattern, not just the specific OKRs.

## Starter guidance

- **Mechanism is a how, not a what.** "Ship migration with zero post-cutover incidents" is an outcome. "Use AI effectively on the migration" is a mechanism (and a vague one). "Judgement-weighted review pass applied to 100% of migration PRs with amendments proposed where gaps surface" is a specific mechanism and belongs as a KR *if* the team wants to make visible how the outcome will be produced.
- **Never write an "adoption" OKR as a team objective.** Adoption / activation KRs can live inside a mechanism KR for the enablement work; they are not objectives themselves.
- **IC-scope OKRs for juniors emphasise outcomes; for seniors and above, growth.** A junior IC is accountable to the team's outcome and is building toward the senior-tier axes; a senior IC is already producing team outcomes and is being evaluated on ladder-axis growth. The OKR shape differs.
- **Throughput KRs need a quality pair.** "Ship 20 features" is a throughput KR. Paired with "features launched have no post-launch rollback within 30 days" it reads differently; paired with nothing it is a gameable metric.
- **"Used AI effectively" is not a KR.** It is a condition on *how* the work is done, which may belong in the quarterly written feedback artifact (Chapter 4) but is not a key result.
- **The writing-rules note is the compounding value.** The specific quarter's OKRs matter for the quarter; the rules compound across quarters and across managers.
- **Length: 2–3 pages total.** The team-scope OKR is half a page; three IC-scope OKRs are one and a half pages combined; the writing-rules note is one page. The 1:1 prompts live in the manager's notes, not the shared artifact.
- **Compose with [`mod-104`](../../mod-104-productivity-measurement-and-ai-roi/).** The team-scope OKRs read outcomes that the mod-104 dashboards can reveal progress against, when relevant; they do not use the dashboards as KPIs for individual OKRs.

## Acceptance criteria

The artifact is complete when:

- One team-scope OKR with one objective and two to four KRs; outcome-shaped; no "use AI more" wording.
- Three IC-scope OKRs covering junior, senior, and staff (or closest equivalents) on the team; each composed with the team OKR; senior / staff ones weight ladder-aligned growth moves.
- Every KR has been pressure-tested against the mechanism-as-outcome trap and the throughput trap, and the result is noted in the artifact.
- A one-page OKR writing-rules note names 4–6 rules grounded in Chapter 4.
- For each IC-scope OKR, one example monthly 1:1 conversation prompt is written.
- Peer-manager and senior-IC co-review entries are recorded with any corrections.
- An IC on the team could read the artifact and the writing-rules note and author a self-proposed OKR for the next cycle that follows the pattern.
- Total length: 2–3 pages (plus one-page writing-rules note). More than five pages is over-written.

## Stretch goals

- **A worked historical example.** Pick an OKR the team ran before the refresh. Rewrite it against the writing-rules note; narrate what changed.
- **A quarterly review template.** The specific form the manager uses at end-of-quarter to assess OKR progress. One page; references the writing-rules note.
- **Compose with Exercise 02.** For each IC-scope OKR, name which ladder axis the OKR is building signal toward. The composition gives the manager a quarterly read on whether the IC is producing the signal the next packet will need.
- **A cross-team peer OKR comparison.** If a peer team is running under a different (pre-refresh) OKR pattern, map the difference. Useful calibration before the next cross-team planning cycle.
- **A "bad OKR" critique section.** A one-page appendix walking through 4–5 common-but-bad OKR patterns and what to do instead. Trains the team's OKR literacy.
- **A one-page team OKR explainer for the exec stakeholder.** The exec reads outcomes, not mechanisms. The explainer gives the exec stakeholder the summary without the IC-level detail that is not theirs to see.
