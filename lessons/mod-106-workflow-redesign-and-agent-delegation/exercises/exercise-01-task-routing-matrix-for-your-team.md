# Exercise 01 — Task Routing Matrix for Your Team

**Estimated effort:** 3 hours.

## Objective

Produce **v0.1 of the task-routing matrix** for your real team (or the team shape you are preparing to inherit): a one-page artifact that names, for each of 10 recurring task types, whether the task routes to **AI unattended**, **AI + human pair (variant A or B)**, **junior human**, **senior human**, or **stop doing this task** — with a one-sentence jagged-frontier reason per row and a dated re-check.

This is the first of the five mod-106 artifacts. Exercises 02, 03, 04, and 05 each build a different downstream artifact that references this matrix; the routing matrix is the artifact they are all consistent with.

## Prerequisites

- [Chapter 1](../01-the-jagged-frontier-and-why-this-module-exists.md) — the jagged-frontier framing and the R7 posting anchor.
- [Chapter 2](../02-the-task-routing-decision.md) — the routing rule and the five destinations.
- A working mental model of your team's current workflow: primary tools in use, the recurring artifacts the team produces, the typical rhythm of the week/sprint.
- Optional: [`mod-101` Chapter 3](../../mod-101-ai-augmented-team-manager-position-and-contract/03-authoring-the-team-human-machine-contract.md) if your team's human/machine contract is in flight — the C1 clause (*what AI may draft*) is sharpened by the matrix.

## Problem statement

Every team that has adopted an AI coding assistant or agent has an *implicit* routing in place by default: whichever engineer picked up the task used (or did not use) the AI according to personal preference, and the resulting split of work between AI, junior humans, and senior humans is an accident of individual habit, not a managerial decision. [Dell'Acqua et al.'s](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321) jagged-frontier finding says that implicit routings will systematically fail on the tasks that look adjacent to inside-frontier work but sit outside the capability line — and the team will not know they are failing because the errors are subtle.

The explicit matrix is the response. It names 10 recurring task types on your team, places each one relative to the frontier using three concrete questions, assigns a routing with a reason, and schedules a re-check. It is one page, not three. It is reviewed quarterly. It is the first artifact a new engineer on your team reads about AI delegation.

## Steps

1. **Draft the 10 task types.** Spend 20 minutes listing the recurring work your team does. Aim for specificity: *"review a one-file bug-fix PR with a regression test already included"* not *"code review"*; *"draft the sprint retro summary"* not *"write reports"*. If your draft has more than 15 items, narrow to the 10 that matter most this quarter; if fewer than 8, expand until you have 10. A task that only one person on the team does is not a *team* recurring task — leave it off.
2. **Run the three-question placement on each task type.** For each row, answer:
   - *Is the required output a transformation of existing input (summarise, translate, reformat, lint-check) or a judgment grounded in context the model does not have?* (transformation → inside; judgment → outside)
   - *Can a non-expert reader check the output in under 60 seconds, or does the output need 10+ minutes of context to evaluate?* (fast-checkable → inside; slow-to-check → outside)
   - *Is the task well-represented in public written material, or is it bespoke to your team's local vocabulary?* (well-represented → inside; bespoke → outside)
   Note the three answers per row briefly (e.g., `IT/FC/WR` for *inside transformation / fast-check / well-represented*).
3. **Assign the routing per row.** Apply Chapter 2's guidance: three inside answers → candidate for AI unattended or AI + human pair; three outside → candidate for senior human; mixed → candidate for AI + human pair or junior human + AI. **Default to AI + human pair, variant A** when uncertain; the promotion to unattended is a later, deliberate decision.
4. **Write the one-sentence "why" per row.** The sentence must reference the jagged-frontier reasoning, not a tool preference. *"Inside frontier because it's a mechanical aggregation and the blast radius is small — handoff doc, humans read-after"* is a defensible sentence; *"We use Cursor here so this goes to AI"* is not.
5. **Decide the per-row review mechanism.** For AI-unattended rows, name the aggregate audit (Kind 4 from Chapter 4) that keeps the routing honest. For AI-paired rows, point at the [`mod-103`](../../mod-103-review-standards-and-eval-commissioning/) review standard (or a subset) that the reviewer will run.
6. **Flag the *stop-doing-this* candidates.** As you review the list, mark any task where neither humans nor AI should be doing this at this cadence. Weekly reports nobody reads. Handoff rituals that duplicate ticket data. A honest matrix will have 1–2 such rows.
7. **Set the re-check dates.** Default: quarterly, 90 days from today. Adjust shorter (30–60 days) for rows where the model or the tool is under active change; adjust longer (180 days) for stable, outside-frontier senior-human rows.
8. **Assemble the one-page artifact.** Markdown table, 10 rows. Add a header (title, team name, author = you, date, version `v0.1`), a two-sentence scope-and-caveats paragraph, and a short change-log entry.
9. **Co-review with one senior IC.** 30 minutes. Ask: *"name one row where you disagree, and why."* Expect 1–3 corrections. Record the corrections in the change-log.
10. **Co-review with one junior engineer.** 20 minutes. Ask: *"of the rows I've routed to senior human, which could you do with AI help?"* The question is a direct counter to the under-routing-to-junior failure mode (Chapter 2). Record their answer; move any row they can defend.

## Starter guidance

- **The matrix is a discipline, not a template.** Do not copy a routing from another team's example wholesale. The jagged frontier is specific to the task shape, which is specific to your team.
- **The sentence is load-bearing.** A reader who disagrees with a row should be able to disagree with the specific sentence, not the whole table. If the sentence is a hand-wave, a re-write in 90 days will be a guess.
- **Default to the paired variant when uncertain.** Chapter 2 is explicit: the matrix should land with 1–3 AI-unattended rows and the rest paired. A v0.1 matrix with 6 AI-unattended rows is almost certainly over-routed.
- **The *stop-doing-this* rows are a positive signal.** Teams sometimes try to find a destination for every task because routing *to nothing* feels like a failure. It is the opposite: it is a finding that frees capacity (Chapter 7's attention plan).
- **Senior-human rows should be rare.** A matrix with 5 senior-human rows out of 10 likely has a senior-bottleneck problem waiting to happen. Ask on each: *"could the junior engineer do this with an AI pair and the right review mechanism?"*
- **The re-check date is on the row, not on the matrix as a whole.** Different rows change at different rates.
- **Titles and framing matter for adoption.** The matrix's header should say *"Task Routing Matrix v0.1 — [team name] — [date] — reviewed quarterly"*. A matrix that looks finished at v1.0 reads as inflexible; a v0.1 reads as a living document.

## Acceptance criteria

The matrix is complete when:

- Ten rows, each a specifically-phrased recurring task type. No row is a single-person task.
- Each row has a three-letter placement note (e.g., `IT/FC/WR`) reflecting the Step 2 answers.
- Each row has a routing from the five destinations (plus the sixth, *stop doing this*).
- Each row has a one-sentence "why" grounded in the jagged-frontier reasoning, not a tool preference.
- Each row has a per-row review mechanism (aggregate audit or mod-103 review-standard pointer).
- At least one row is a *stop-doing-this* candidate, or you have written a short note explaining why no task on your team fits.
- Each row has a re-check date.
- The artifact has a title, version `v0.1`, date, author, two-sentence scope-and-caveats, and a change-log listing the senior-IC and junior-engineer co-reviews with the corrections they produced.
- The artifact is one printed page.
- A new engineer joining the team next quarter could read the matrix and know, for each of the 10 task types, how the team expects them to route the work.

## Stretch goals

- **Calibration-against-example.** After producing your v0.1, read Chapter 2's platform-team example matrix. Pick one row where your routing disagrees with the example's pattern (e.g., yours routes something to senior human that the example routed to AI + junior pair, or vice versa). Write a short note on why your team's context justifies the difference — or whether the example should prompt a re-route.
- **Shadow-decision run.** For one AI-paired row, run the routing for a full week in *shadow mode*: the agent produces the output, but the team does the work anyway and compares. Log the aggregate quality delta. This is the real empirical input to the Chapter 3 delegation-ladder level for that row.
- **Second-cohort review.** If your team has >8 engineers, run a second review with the full team (one hour). Ask: *"name one row where the routing surprises you."* Most routings will not surprise; a few will. The surprise-generating rows are where the team's implicit model and your explicit matrix diverge — those are the rows most worth discussing in detail.
- **Cross-team compare.** If another manager in your organisation is running the same exercise, trade v0.1 matrices and look for rows that are routed differently for the same task type. Differences are often instructive: either one team is over-routing or one team's context genuinely changes the frontier placement.
- **Counterfactual column.** Add a "counterfactual" column to the matrix: *"before the AI, how was this routed?"* The diff is the explicit shape of the attention shift Chapter 7 will act on. Many rows will have changed from senior to AI + junior pair or from junior to AI unattended; a few may have stayed at senior and your matrix should be able to defend those.
