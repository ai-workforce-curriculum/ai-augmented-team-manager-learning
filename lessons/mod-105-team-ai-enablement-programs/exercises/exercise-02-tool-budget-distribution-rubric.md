# Exercise 02 — The Tool-Budget Distribution Rubric

**Estimated effort:** 2.5 hours.

## Objective

Produce a **tool-budget distribution rubric** for your actual team that allocates seats *and* usage budgets by learning stage, not by seniority. The output is a one-to-two-page artifact — `docs/mod-105-budget-rubric.md`-style — that includes: a published, shareable stage rubric; a per-tool allocation table showing the shape of seat and usage expectation at each stage; a projection of the quarter's spend given the current stage distribution; and a cross-link to the `mod-104` AI-cost ratio tile.

## Prerequisites

- Chapter 4 of this module.
- Chapter 1 of `mod-104` (the AI-cost ratio tile context) if you have completed it.
- A list of the AI tools your team currently has licences for (or is about to license).
- Access to the current licence/seat/usage spend numbers for those tools at your team or org — even imprecise. If you have no access, work from vendor list pricing + licence counts as a projection.
- Your team roster (or the roster you are about to inherit).

## Problem statement

Your team has — or is about to have — a budget for AI tooling that is non-trivial: one-to-three-figure dollars per engineer per month, with usage-based components that can vary by a factor of ten across engineers. The default allocation inherited from pre-AI tooling is seniority-shaped. The Chapter 4 research anchors (Brynjolfsson-Li-Raymond; Dell'Acqua et al.) argue this is the wrong shape for AI tooling specifically. Your job is to produce the shaped rubric and defend it operationally — both upward to Finance / VP of Engineering, and across to the team so that the stage pin is read as a learning signal, not a status game.

The rubric has two audiences:

- **Internal (the team).** Engineers read the rubric to understand *how they are placed* and *what would move them up a stage*. The rubric must be published, specific, and visible.
- **External (Finance / VP / Procurement).** They read the rubric to understand *why the spend is shaped this way* and *what the quarter's projection is*. The defense requires naming the Chapter 4 anchors and showing a shape that moves in the expected direction over the programme's lifetime.

## Steps

1. **Enumerate the tools.** List every AI tool on your team's current / planned stack (coding assistants, general-purpose assistants, eval tools, agent-authoring environments, specialised tools). For each: pricing structure (per-seat, usage-based, hybrid), current licence count, any usage caps or defaults the vendor applies.
2. **Write the published stage rubric.** For each tool category (or for each specific tool, if the categorisation is too coarse for your team), write 1–4 stage definitions per Chapter 4's shape. The rubric is published — engineers can read it. Keep each stage definition to two sentences. Stage 3 is the one most engineers will read most closely; make it specific.
3. **Pin each engineer.** For every engineer on the team, record a current stage pin per tool category. This can be a first pass; the Day-0 conversation from Exercise 01 refines it.
4. **Build the per-tool allocation table.** For each tool, a table with four rows (stages 1–4) and columns: seat/access (yes/no); expected usage shape (e.g. "soft floor, no cap" for stage 1 usage-based; "team-median" for stage 3); monitoring cadence (stage 4 has a quarterly review; stage 1–2 have no monthly ceiling).
5. **Compute the quarter's spend projection.** Using the current stage distribution, project the quarter's spend for each tool: seats (count × unit price) + usage (projected volume based on stage distribution × unit price). Produce a single roll-up total.
6. **Project the next quarter.** Assume the Chapter 2 cohort progression — N engineers moving from stage 1 to stage 2, M from stage 2 to stage 3. Project the next quarter's spend. The spend will likely *rise* in the early quarters of the programme as stage-1 engineers ramp into higher usage; this is the correct direction.
7. **Cross-link to mod-104.** Write the paragraph that will accompany the AI-cost ratio tile on the mod-104 dashboard: *"tool spend per 100 PRs merged is $X this quarter; the projected rise in Q[N+1] reflects the stage-shaped allocation; see mod-105 Exercise 02 for the rubric."*
8. **Walk the draft with one stakeholder.** Either a Finance partner, your VP of Engineering, or your L&D partner — pick the audience most likely to challenge the rubric and get the challenge early. Record their pushback and your response.
9. **Publish v0.1 to the team.** The rubric lives somewhere every engineer can find it (team README, Confluence, Notion). The per-individual stage pins are *not* published to the team — they live in the stage sheets from Exercise 01.
10. **Freeze v0.1.** Title: `mod-105 Tool Budget Rubric v0.1 — [team name] — [YYYY-MM-DD]`. Author (you). Reviewers (the stakeholder from step 8 + one engineer from your team). Scope-and-caveats paragraph. Change log. Sunset review date six months out.

## Starter guidance

- The rubric is *visible*; the individual pins are *confidential*. Keep them separate. If you conflate, engineers will optimise their pins for status and the instrument dies.
- A single sentence of justification per stage goes a long way. "Stage 3: the engineer makes a judgment call about when to use the tool and when not to, and can articulate the trade-off" is a stage definition engineers can self-check against. "Stage 3: advanced usage" is not.
- For usage-based pricing (tokens, request volume), favour *soft floors with no cap* at stages 1–2. Hard caps during learning are Chapter 1's Failure B. If Finance insists on a cap, propose stage-sensitive alerts instead and route the escalation per Chapter 7.
- For per-seat pricing with a lower non-enterprise tier (e.g. Cursor Pro vs. Cursor Business), it is often correct to give *everyone* the enterprise-tier seat regardless of stage. The marginal spend per seat is small; the marginal training cost of running two different tool experiences is not.
- The projection is a *projection*, not a commitment. Flag uncertainty bands. "Projected Q2 spend $X ± 20% based on stage-progression assumption Y" is defensible; "Q2 spend will be $X" is not.
- If your organisation has a FinOps function that asserts caps on behalf of the whole org, this exercise's artifact is also the response to that assertion. See Chapter 7 for the escalation posture.
- Avoid letting the rubric drift into a "levelling" document. The stage rubric is for *this tool* fluency; it is not a job-level descriptor. Keep that boundary explicit.

## Acceptance criteria

The rubric is complete when:

- Every AI tool on the team's stack is enumerated with its pricing structure and current licence count.
- A 1–4 stage rubric is published per tool category (or per tool, where categorisation is too coarse), with specific, two-sentence-per-stage definitions.
- Every engineer on the team has a current stage pin per tool category; the pins are confidential and live in the stage sheets.
- A per-tool allocation table lists seat/access + expected usage shape + monitoring cadence for each of the four stages.
- A quarter's spend projection shows seat + usage components by tool, with a roll-up total.
- A next-quarter projection shows the expected spend under cohort progression.
- A one-paragraph cross-link to the mod-104 AI-cost ratio tile is drafted.
- One upward stakeholder (Finance / VP / L&D) has reviewed; their pushback and your response is recorded.
- The published rubric is available team-wide; the individual pins are not.
- The artifact is titled, dated, lists contributors, carries scope-and-caveats and a change log, and has a six-month sunset date.
- Each stage definition stays within two sentences; the whole rubric fits on one to two pages.

## Stretch goals

- **Vendor-scenario modelling.** For your highest-spend usage-based tool, model three scenarios: current spend holds, 30% rise (healthy cohort progression), 100% rise (cohort progresses faster than expected). Which scenarios survive your org's budget tolerance? Which require escalation and to whom?
- **Stage movement history.** If you have run the rubric for more than one quarter, add a before/after table showing how many engineers moved between stages. This is itself a leading indicator for the mod-105 programme's health.
- **Tool fit challenge.** For each tool where a non-trivial fraction of the team is at stage 1 after a full programme cycle, write one paragraph on whether the tool is wrong for your team's work (per Chapter 2's "Day-30 PR slippage" cause (a)) versus whether the programme needs to adjust.
- **Rubric cross-check with a peer manager.** Share the published rubric (not the pins) with another manager running a mod-105 programme. Compare stage definitions. Divergences in how "stage 3" reads across teams are useful cross-team signal for the eventual L45 handoff (Chapter 8).
- **Small-team variant.** If your team is 5 engineers and the pattern of overlapping cohorts does not apply, write a one-paragraph note on how the rubric still functions at team-of-five scale — in particular, how you avoid the "we don't need a rubric, we all know where we are" pattern.
