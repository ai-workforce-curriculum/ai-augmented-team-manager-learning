# Exercise 02 — Pilot vs. Rollout Decision Drill

**Estimated effort:** 2 hours.

## Objective

Convert the *AI-first* and *pilot candidate* buckets from Exercise 01 into a **dated pilot/rollout sequence** with a pre-committed charter for every pilot in flight this quarter. The output is sections 3 (sequence) and partial 5 (success/kill) of the roadmap one-pager, plus a one-page charter per pilot. You are making the sequencing decisions this chapter asks you to make, and you are pre-committing to the kill criteria *before* the pilots run.

## Prerequisites

- Chapter 3 of this module.
- Exercise 01 complete — task sort with buckets.
- A rough reading of this quarter's team context: in-flight projects, reviewer bandwidth, change-fatigue signals, upcoming re-orgs or launches, policy-mandate state from org (any security / legal / enablement decisions already made above you).
- The measurement vocabulary from Chapter 2 of [`mod-104`](../../mod-104-productivity-measurement-and-ai-roi/) if authored, or a working draft — you will commit to metrics here, and they should be the metrics you will use at rollout scale.

## Steps

1. **Separate "obvious rollout" from "pilot first."** For each *AI-first* task from Exercise 01, apply the four pilot-skip criteria from Chapter 3 (score ≥25 with no cell ≤2; comparable case already piloted; tool already in team use; blast radius small). Mark each task *pilot-skip eligible* or *pilot-first*. Expect most to be *pilot-first* in your team's first year; pilot-skip is a conscious call.
2. **Draft the quarter's pilot/rollout sequence.** Two columns, ordered by start date: pilots (start–end weeks, cohort size, task family) and rollouts (post-pilot promotion dates, scope). Anchor against your team's horizon (one quarter or two). Three to six pilots is a workable range; more than that and you are over-committing.
3. **Write a pre-pilot charter for each pilot.** One page, seven fields: task and workflow; cohort (named ICs, 2–5, opt-in); horizon (2–6 weeks); success criteria (pre-committed, measurable); kill criteria (pre-committed); decision owner and decision date; data collection plan. Field 5 — the kill criteria — is the one that matters most. Write it in the voice of "we will stop if…," not in the voice of "we hope not to see…"
4. **Pick the adoption mode per pilot *and* per expected rollout.** Apply Chapter 3's four questions. Default to opt-in during pilot, opt-out after a successful pilot, mandate only when the mandate came from above you. Log the mode for each with one-sentence reasoning.
5. **Pressure-test the sequence against six scenarios.** For each, write a two-to-four-sentence response using only what you have written so far:
   - A pilot ships evidence of a 25% time saving but reviewer-reported quality bar drops. Promote, extend, or kill?
   - Three weeks into pilot, a team member resigns and the cohort shrinks from 5 to 3. Continue or restart?
   - A sibling team runs the same pilot three weeks ahead of you and reports success. Skip your pilot?
   - Platform drops a new shared Cursor-rules deployment mid-pilot that conflicts with your team-local config. Continue, pause, or restart?
   - Your VP asks to accelerate the rollout of two pilots by four weeks. Which do you push back on and with what evidence?
   - An incident ([`mod-109`](../../mod-109-accountability-incident-response-and-blameless-postmortems/)) occurs on an AI-first task not in the pilot. Does the pilot plan change?
6. **Sanity-check reviewer bandwidth.** Add up the review load implied by the opt-out rollouts in sections 3–4 — how many PRs, docs, or artifacts hit which reviewers per week. If the number is beyond what reviewers can honestly carry, step back one mode or shrink scope. Dishonest review bandwidth is the #1 killer of opt-out rollouts.
7. **Share the full sequence with one named IC in the cohort and one partner function.** Fifteen minutes each. Ask: is this honest; does the kill criteria make sense; is anything missing. Capture pushback; revise.

## Starter guidance

- The temptation is to over-commit — six pilots this quarter, two opt-out rollouts, mandate on one. In practice, two to three pilots and one or two opt-out rollouts is a full quarter at team scope. Leave headroom.
- The kill criteria is the test. If every pilot's kill criteria reads "no measurable improvement," you have not written a kill criteria — you have written a hedge. Make at least one kill criteria about *reviewer burnout* or *incident signal* so it is operational, not just numeric.
- Pilots and incident response interact. The pilot charter should reference the incident process from `mod-109` so there is no ambiguity about what happens if the pilot triggers one.
- Decision dates are not aspirational — put them on your calendar as recurring reminders. A pilot that misses its decision date is a pilot that silently became policy.
- Opt-in during pilot is almost always the right posture. Mandate during pilot is a tell that you are using "pilot" as cover for "rollout with no kill switch."

## Acceptance criteria

The deliverable is complete when:

- A dated pilot/rollout sequence covers the full horizon with three to six pilots and one to four rollouts.
- Each pilot has a one-page charter with all seven fields filled in. No "TBD." No kill-criteria hedges.
- Each pilot has a named decision owner (you, almost always) and a specific decision date.
- Each pilot and each expected rollout has an adoption mode (opt-in, opt-out, mandate) with one-sentence reasoning.
- The six scenarios each receive a 2–4 sentence response grounded in the sequence.
- Reviewer bandwidth is sanity-checked and, if over-committed, scope or mode has been walked back.
- One cohort IC and one partner function have reviewed the sequence; the review notes are logged.

## Stretch goals

- For each pilot, write the *success story* and the *kill story* in two paragraphs each — what the pilot looks like at promote-call-time in each outcome. If one of the two is much harder to write, the metrics may be asymmetric.
- Map each pilot's success criteria to the DX Core 4 / SPACE / DORA metric it will register against (see [`mod-104`](../../mod-104-productivity-measurement-and-ai-roi/)). If none map cleanly, revisit whether the metric is measurable.
- Pre-write the *week-3 pulse* and the *promote/kill memo* templates. If you can't picture the template, you do not know what evidence you are expecting.
- Run the sequence past your `ai-enablement-lead` (L45) — flag which pilots you expect to be graduation candidates and which you expect to stay team-local. This primes Exercise 05.
