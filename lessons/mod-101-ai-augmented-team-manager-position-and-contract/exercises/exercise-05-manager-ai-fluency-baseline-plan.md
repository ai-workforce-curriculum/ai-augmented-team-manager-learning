# Exercise 05 — Manager AI-Fluency Baseline Plan

**Estimated effort:** 2 hours.

## Objective

Produce a dated, 90-day **AI-fluency baseline plan** against the Chapter 5 bar. The plan calibrates your current fluency against five tool categories and five manager-altitude artifacts, names a deliberate cadence (weekly / monthly / quarterly) that keeps the bar met without crossing into IC work, and leaves a one-paragraph note on how you will know if you have drifted up (out-shipping) or down (losing review authority).

## Prerequisites

- Chapter 5 of this module.
- Your team's actual tool stack: which AI coding assistant, which general-purpose assistant, which eval tool, which agent-authoring environment, which standards-as-code conventions.
- Exercise 02 complete — you have an honest manager-output baseline to layer AI onto.

## Steps

1. **Rate current fluency on five tool categories.** For each of the five Chapter 5 tool categories, mark *fluent / adequate / weak / not yet*. Use your team's actual tool, not a generic placeholder. The five:
   - AI coding assistant (Cursor / Copilot / Claude Code / Windsurf / …).
   - General-purpose AI assistant (Claude / ChatGPT / Gemini / …).
   - Eval tool at reading level (Promptfoo / LangSmith / Inspect AI / Langfuse / Phoenix / …).
   - Agent-authoring environment at reading level (Claude Code / LangGraph / CrewAI / PydanticAI / …).
   - Team's standards-as-code stack (Cursor rules / AGENTS.md / ADRs / lint / pre-commit / CI gates).
2. **Rate current artifact-authoring fluency.** For each of the five manager-altitude artifacts from Chapter 5, mark *strong / adequate / weak / not yet attempted*:
   - Team human/machine contract (Exercise 03 is the entry point).
   - Quarterly adoption-roadmap one-pager.
   - Quarterly ROI narrative.
   - AI-incident post-mortem narrative.
   - Governance crosswalk snippet at team scope.
   (Hiring loop structure is also on the Chapter 5 list; include it if your team is hiring, otherwise skip for now.)
3. **Write the IAPP AIGP vocabulary note.** One paragraph on where you currently stand on AIGP body-of-knowledge vocabulary — never heard of it / familiar with the structure / can recognise it in a meeting / have read key sections. State which `mod-110` reading you will reach for to close the gap.
4. **Write the drift tests.** Two short paragraphs:
   - *Drift up (out-shipping):* name a specific signal you will watch for — e.g., "if I am shipping more than X PRs on the main repo in a month, I am crossing into IC work." State the number honestly.
   - *Drift down (losing review authority):* name a specific signal — e.g., "if I cannot open a Promptfoo report from our main workflow and name the regression in it, my fluency is slipping." State the test concretely.
5. **Draft the 90-day plan.** Three columns: *week / activity / outcome*. Thirteen weeks of entries. Cadence should match Chapter 5's suggestion (weekly tool check-in + monthly standards re-read + quarterly end-to-end change) but adjusted to your real calendar, with specific artifacts tied to the modules ahead (the Exercise 03 contract; the `mod-102` adoption-roadmap one-pager; the first eval-report read-through for `mod-103`). Every row must name a concrete output (a note, a revision, a shared document), not just an intention.
6. **Set the check-in.** One sentence stating when (date, 90 days out) and with whom (your own manager, a peer manager, your coach) you will review the plan against outcome.

## Starter guidance

- Fluency is measured by output, not by hours logged. The plan should drive artifacts and reviewed activities, not reading hours.
- Do not over-commit. A sustainable thirteen weeks beats an ambitious four. If the plan would require more than two hours a week of dedicated fluency time, cut it.
- If your fluency rating is *weak* or *not yet* on more than two of the five tool categories, start the plan on the one with the highest leverage: usually the AI coding assistant your team uses most, or the eval tool you cannot currently read.
- If your fluency rating is *fluent* on all five tools, verify by pairing with an IC on a non-trivial task and have them pressure-test you. Fluency people claim and fluency people hold are often different things.
- Pick drift signals you can **observe passively** rather than ones that require weekly introspection — e.g., a PR count from your own GitHub, a calendar accounting of time, a monthly reflection prompt.

## Acceptance criteria

The plan is complete when:

- All five tool categories and all five artifact classes have an honest current rating.
- An AIGP vocabulary paragraph is written with a planned reading.
- Both drift tests (up and down) are stated with concrete, observable signals.
- Thirteen weeks of plan rows are filled in with specific activities and named outputs.
- A check-in date (90 days out) and a reviewer are named.
- The whole artifact fits on one page and is clear to a reviewer who does not know your tool stack.

## Stretch goals

- Share the plan with your own manager and get agreement on the two drift tests — their view on what "out-shipping" looks like for you may differ from yours.
- If your team uses more than one AI coding assistant or more than one eval tool, pick the dominant one for the plan and note the others for the next cycle — do not spread thin.
- Draft the companion *team-fluency bar* you will publish for your team alongside your manager one — a direct input to `mod-105` on enablement. Mark it as a sketch; `mod-105` is where the full enablement program gets authored.
