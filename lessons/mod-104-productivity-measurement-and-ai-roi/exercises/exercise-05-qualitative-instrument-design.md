# Exercise 05 — Qualitative Instrument Design

**Estimated effort:** 2 hours.

## Objective

Design the **three qualitative instruments** — AI-specific retro prompts, standing 1:1 questions, quarterly pulse survey — specified in Chapter 8, tuned to your team's actual composition, tooling, and operating cadence. The output is a single Markdown file (`docs/ai-qualitative-instrument.md`) that documents each instrument, its cadence, its reading posture, and its governance posture.

This instrument is the circuit breaker against the drift Chapter 1 and Chapter 8 warn about. Produced once as v0.1, revised thereafter at the quarter boundary (which the Exercise 06 retro ritual builds in).

## Prerequisites

- Chapter 8 of this module.
- Chapter 5 of this module (the distribution finding motivates the segmented reading posture).
- Your team's current retro / 1:1 / survey cadence. If your team does not run retros, design the retro-prompt instrument into a 30-minute monthly if a 6-week retro is not an option.
- Your HR / People partner's view on anonymous-survey tooling, if your organisation has a convention. If it does not, plan for a lightweight tool (Google Forms, Typeform, Culture Amp, or whatever is already in-house).
- Awareness of your team's size — team-size constrains what can be run anonymously (see Chapter 8's governance note).

## Problem statement

Most teams either (a) have no AI-specific qualitative instrument at all, (b) have one that is so general it does not surface AI-specific signal ("how was your sprint?") or (c) run a biweekly pulse that engineers have stopped responding to thoughtfully.

Your job is to design a *stable, low-burden, longitudinally-readable* qualitative instrument tailored to your team. The design *is* the artifact; running the instrument is the next step. Expect the first version to be revised at the first quarterly retro (Exercise 06), which is why v0.1 is explicit.

## Steps

1. **Enumerate the team and its workstreams.** Tenure distribution, workstream split, cadence of retros / 1:1s / surveys currently in place. These facts determine what instruments are feasible.
2. **Design the retro prompts.** Three to five prompts based on Chapter 8's candidate set. Adapt to your team's actual tooling (name the specific agents the prompts probe). Specify: cadence (default 6 weeks), time budget inside the retro (default 15–20 minutes), whose turn it is to capture notes.
3. **Design the standing 1:1 questions.** Two questions, as Chapter 8 specifies. Pick a cadence (every second or third 1:1; not every one). Document how to handle signal from these questions — Chapter 8 is explicit that 1:1 content is confidential by default; your own notes posture needs to reflect that.
4. **Design the quarterly pulse survey.** 5–8 Likert-scale questions plus one free-text. Base on Chapter 8's candidate set; tune for your team's current operating concerns. Decide anonymity posture: anonymous (recommended if team size and org culture support), non-anonymous but promised-aggregate (if not). Decide tool.
5. **Document the reading posture.** For each instrument, how do you *read* the output? Which pattern from Chapter 8's four (aligned-up, quant↑/qual flat, quant flat/qual↓, quant↓/qual↑) does each instrument help identify? What does the output feed into (the Exercise 04 one-pager's Section 4; the Exercise 06 retro)?
6. **Document the distribution posture.** How are you going to surface the distribution the literature predicts (tenure-segmented, workstream-segmented)? What segmentation is feasible without de-anonymising?
7. **Document the governance posture.** Anonymity promises; confidentiality of 1:1 signal; unattributed-vs-aggregate reporting from retros. Any specific do-not-dos (e.g. *"we do not report pulse survey averages for sub-cohorts smaller than 4 engineers to protect anonymity"*).
8. **Set the review cadence.** When does v0.2 land? The default is at the first Exercise 06 quarterly retro.
9. **Walk the draft to one peer manager and one engineer on your team.** Specifically ask: *does the retro prompt set feel like it will surface real signal or be checkbox noise? Does the 1:1 cadence feel invasive or appropriately spaced? Does the pulse survey feel answerable in under 5 minutes and not threatening?*
10. **Freeze v0.1.** Dated, titled, author, reviewers, scope-and-caveats, change log.

## Starter guidance

- Keep the retro prompts *stable* across cycles. The longitudinal signal is the value; changing the wording every cycle destroys it. If a prompt is wrong, revise it at the quarterly Exercise 06 retro and note the revision in the change log.
- Keep the pulse survey short. 5–8 Likert items is the ceiling. Response-rate decays steeply past that. The free-text prompt is the one open field; keep it narrow ("one AI-related change you would make to this team if you could") rather than broad ("anything else").
- Do not combine the pulse with the DX survey. They are different instruments at different cadence. Combining them halves the response thoughtfulness on both.
- Segmentation is *diagnostic* not *decorative*. Compute it even if it is not reported upward. The tenure-segmented reading is often the finding; the team-average is often the headline. Both have a role.
- Governance cannot be an afterthought. If your team is 4 engineers, anonymous surveys are effectively non-anonymous; design accordingly. If your organisation's HR partner has an opinion on survey instruments, consult them.
- A biweekly cadence will burn the instrument out. 6-week retro + quarterly pulse + every-2nd-1:1 is a sustainable load.
- The 1:1 question about *pressure to use AI tooling when it is not helping* is the single most important question in the design. Chapter 8 explains why. Do not drop it in a revision.

## Acceptance criteria

The qualitative instrument design is complete when:

- Three instruments are documented: retro prompts (with cadence, time budget, prompt set), standing 1:1 questions (with cadence, confidentiality note), quarterly pulse survey (with question set, tool, anonymity posture).
- A reading-posture section names which of the four Chapter 8 quant-vs-qual patterns each instrument helps identify and where the output feeds (Exercise 04 one-pager, Exercise 06 retro).
- A distribution-posture section names how tenure and workstream segmentation will be surfaced without de-anonymising.
- A governance-posture section names anonymity promises, 1:1 confidentiality defaults, retro-reporting defaults (aggregate or unattributed by default).
- The retro prompt set is 3–5 stable prompts — not more.
- The pulse survey is 5–8 Likert-scale questions plus one free-text — not more.
- The 1:1 standing-question set is exactly 2 questions (as Chapter 8 specifies), including the pressure-to-use-AI question.
- At least one peer manager and one engineer have reviewed and the feedback is reflected or logged.
- The artifact is titled, dated, lists contributors, carries a scope-and-caveats paragraph, and carries a change log.
- A v0.2 review date (default: first Exercise 06 retro) is scheduled in the calendar.

## Stretch goals

- **Baseline run.** Run the pulse survey once before the first full quarterly Exercise 06 retro, as a baseline. Report the results back to the team (aggregate, with the governance posture intact). The act of reporting signals to the team that the instrument is for them, not for the exec deck.
- **Prompt-set stress test.** For each retro prompt, ask: *what is the shape of a negative answer? What would I do with it?* If the answer is "nothing," the prompt is checkbox noise. Cut.
- **Non-code work slice.** If your team has non-engineering members, write a parallel prompt set tailored to their work. The frontier is also jagged for design, PM-embedded, ops-embedded work, and the instrument should reach them.
- **Cross-manager norm.** If multiple team managers in your organisation are producing mod-104 artifacts, agree on *common* pulse-survey questions where it is sensible. The aggregate signal across teams is more valuable than per-team-only; alignment lets [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) and [`mod-112`](../../mod-112-cross-functional-leadership-and-ritual-calendar/) rituals work.
- **Instrument-decay scan.** After three cycles, compute per-prompt response rate and free-text thoughtfulness. Prompts that are not surfacing signal get rotated out; prompts that are get kept.
- **Anonymity audit.** For any sub-cohort you plan to report on (e.g. "data-pipeline cohort response was X"), audit the cohort size against your anonymity promise. If the cohort is < 4 engineers, aggregate up or do not report at that cut.
