# Exercise 03 — Opt-In vs. Mandate Rubric

**Estimated effort:** 2 hours.

## Objective

Produce a reusable **adoption-mode rubric** for your team — a half-page decision tree that takes any proposed AI-targeted workflow and returns *opt-in*, *opt-out* (default-on), or *mandate*, with the reasoning. Stress-test the rubric against ten real or realistic scenarios. The output is both a usable rubric and a short set of worked scenarios you can hand to a future manager, a skip-level, or your enablement-lead partner.

## Prerequisites

- Chapter 3 of this module.
- Exercises 01 and 02.
- An awareness of what has already been mandated *above you* — any security, legal, enablement-lead, or exec decisions that have locked in a mode for a specific workflow in your org. Mandates from above are inputs, not decisions, to your rubric.

## Steps

1. **Draft the rubric as a decision tree.** Four leaves: opt-in, opt-out (default-on), mandate, not-ready. Four branches, from Chapter 3's four questions:
   - *Is there a legitimate reason an IC should not do this with AI this quarter?* → if yes, limits the upper bound to opt-in or opt-out.
   - *Does consistency across the team add real value?* → if yes, leans opt-out over opt-in; if no, opt-in may be enough.
   - *Did someone above you already say "required"?* → if yes, mandate (and your job is translation, not design).
   - *Will the review bar hold at full-team scale?* → if no, step back to opt-in or shrink scope.
   Draw it so the first answer that lands you in a leaf stops the walk.
2. **State the defaults next to each leaf.** For opt-in: how enablement is offered (voluntary, async, drop-in). For opt-out: how the default is communicated and how opt-out requests are logged. For mandate: how the "why" from above you is quoted and linked. For not-ready: what the follow-up is (pilot? another quarter?).
3. **Compose ten scenarios.** Mix real tasks from Exercise 01 (at least five) with realistic extensions. Each scenario in two or three sentences. Hit at least:
   - a high-frequency, inside-the-frontier engineering task (e.g., PR descriptions);
   - a customer-facing output with non-trivial blast radius (e.g., support reply template);
   - a judgment-dense people-management task (e.g., first-draft 1:1 prep);
   - a workflow already mandated above you (e.g., a security-review tool);
   - a workflow where your team is split (two senior ICs for, two against);
   - a pilot that succeeded on the cohort but you suspect was cohort-selection bias;
   - a workflow that depends on a non-enterprise tool;
   - a workflow owned by Platform, not your team;
   - a workflow with a measurement that is not actually measurable;
   - an edge case specific to your team.
4. **Walk each scenario through the rubric.** Record (a) the leaf it lands on; (b) the reasoning in one or two sentences; (c) any overrides or caveats.
5. **Flag the overrides as *rubric debt*.** Overrides are not a weakness — they are the rubric telling you where it is incomplete. For every override, ask: is this one-off, or does it point to a missing branch? Add missing branches.
6. **Pressure-test for walk-back cost.** For every scenario you landed on *mandate*, ask: if I have to walk this back in six weeks (reviewer burnout, partner-function pushback, incident), what is the cost? If the walk-back cost is high and the mandate was not from above you, step down to opt-out.
7. **Add a change-management one-liner per leaf.** Opt-in: who you tell, when, and how. Opt-out: how you announce the default, how the opt-out column is read monthly. Mandate: how the "why" is communicated from the person above you who issued it. The leaves are the *decision*; the change-management lines are the *rollout*.

## Starter guidance

- Mandate is a tool for translating decisions from above you. If you find yourself inventing mandates from your altitude, that is a tell that you are using *scope* as a substitute for *persuasion*. Walk it back to opt-out and do the enablement instead.
- The "consistency adds value" question is often answered with yes-but-not-that-much. Watch for marginal-consistency reasoning — a one-point gain in uniformity does not pay for a mandate.
- Opt-out is the mode most people under-use and over-fear. It is the honest default for a workflow where the pilot cleared its bar and the review infrastructure holds. Rogers' *Diffusion of Innovations* makes the case clearly: without a default, the late-majority and laggard segments stay out of range of the benefit.
- The not-ready leaf is legitimate. "This workflow needs another pilot" or "this workflow needs a review bar we don't yet have" is a clean decision. Pretending otherwise is how roadmaps fall over.
- The rubric does not replace the pilot charter — the two are different instruments. The charter commits one pilot to its kill switch; the rubric commits the team to an adoption-mode decision principle.

## Acceptance criteria

The rubric and scenarios are complete when:

- The decision tree fits on half a page, is readable, and has four leaves including *not-ready*.
- Each leaf has a one-line default change-management statement.
- Ten scenarios have been walked through with a clear leaf, two-sentence reasoning, and overrides logged.
- Overrides have been examined for rubric debt; at least one missing branch has been flagged or filled in.
- Mandate decisions have been pressure-tested for walk-back cost. None are a manager-origin mandate on high-walk-back-cost workflows.
- The rubric is dated, named, and pinned alongside the task sort and the pilot charters.

## Stretch goals

- Run the rubric past three ICs separately and compare their decisions to yours. Disagreements are higher-signal than agreement.
- Translate the rubric into a one-paragraph FAQ for the team: "Why is X opt-out and Y opt-in?" This is useful as a team-channel pin.
- Map each mandate decision to the policy document above you that issued it (e.g., org security policy v3.2 §4; `ai-enablement-lead`'s roll-out memo dated YYYY-MM-DD). Mandates without a source document should be rechecked.
- For each opt-out rollout, pre-write the week-4 pulse question for the team: "is this working?" If the question is too generic to give useful signal, refine the measurement in Exercise 02's charter.
- Compare your rubric's leaves against the broad patterns in the most recent *Microsoft Work Trend Index* ("BYOAI," manager-friction, mandate-fatigue themes). Where your rubric is tighter or looser than the reported pattern, note the reason — this is material for Exercise 04 and Exercise 06.
