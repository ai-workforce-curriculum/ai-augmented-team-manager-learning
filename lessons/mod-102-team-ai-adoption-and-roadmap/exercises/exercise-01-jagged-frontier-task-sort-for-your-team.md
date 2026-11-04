# Exercise 01 — Jagged-Frontier Task Sort for Your Team

**Estimated effort:** 3 hours.

## Objective

Produce a **dated, scored, and signed task sort** of your team's actual work, using the six-dimension rubric from Chapter 2, with every task family placed into one of the four buckets: *AI-first*, *AI-assisted (review-only)*, *human-led*, or *pilot candidate*. The output is the input to every downstream chapter in this module. You are not writing a thesis; you are producing one short table your team will actually use.

## Prerequisites

- Chapter 2 of this module.
- Chapter 1 (so you know where the sort fits in the roadmap artifact).
- Chapter 3 of [`mod-101`](../../mod-101-ai-augmented-team-manager-position-and-contract/) — the C1 table of the human/machine contract. The sort and the C1 table must end this exercise consistent; if you already have a draft contract, bring it.
- Access to two months of your team's actual task record: recent PR titles, ticket categories, meeting-type calendar, Slack-thread topics, stand-up topics. Not a tool's marketing page.
- 2–3 senior ICs who do the work daily (lined up for a 90-minute working session).

## Steps

1. **Build the raw task list (before the session).** From the last two months of your team's output, list every recurring task family — one line per family. Target: 20–40 task families. Keep the granularity at the *family* level ("PR descriptions," "unit-test skeletons"), not the artifact level ("PR #3417"). Where you are unsure, lean toward splitting — a split that turns out to collapse is easy to undo; a bucket that was secretly two tasks is not.
2. **Pre-score alone.** Against each task, fill in the six-dimension rubric (capability fit, verifiability, blast radius — higher safer, frequency, judgment density — higher safer, reversibility) with a 1–5 score and a one-line note. Run three representative instances through the model for any task you are unsure about *before* scoring capability fit — do not score from gut.
3. **Run the 90-minute session with 2–3 senior ICs.** Share the pre-score. Walk the table top-to-bottom. For each row, ask: (a) are there instances I missed; (b) is the capability-fit score reflecting a *representative* instance, not the easiest or hardest; (c) is blast radius calibrated against what has actually gone wrong in the last year on this task; (d) is judgment density capturing team-norm and context dependence, not just task complexity. Revise scores as you go. Keep notes on every disagreement.
4. **Place each task in one of the four buckets.** Rule of thumb: *AI-first* if sum ≥18 with no cell ≤2; *AI-assisted (review-only)* if sum 15–17 or sum ≥18 with one cell at 2; *human-led* if sum ≤12 or any cell =1 in blast radius, verifiability, or judgment density; *pilot candidate* otherwise. The rubric is a scaffold — override consciously when the group has a specific reason, and log the override next to the row.
5. **Reconcile against the C1 table in the human/machine contract.** For every task whose sort-bucket contradicts the contract's C1 column, decide which document is wrong. Fix the contract first, then the sort. Record the reconciliation in your decision log.
6. **Freeze and date the sort.** Title: `Task Sort v0.1 — [team name] — [YYYY-MM-DD]`. List the scorers (yourself + the ICs). Add a one-paragraph *scope-and-caveats* note: what your team does, which tools you tested capability fit against, which tool-versions and model generations were in use during scoring.
7. **Walk one session's worth of findings to one partner function.** Pick one of: your Platform lead, your PM peer, or your `ai-risk-engineer` peer. Ten minutes. Ask: does the bucketing surprise you? Capture any pushback and either update the sort or log the counter-argument without updating.

## Starter guidance

- The point of the session is not consensus — the point is to catch your blind spots. If the ICs agree with every pre-score, you either picked ICs who defer to you or you did a very safe scoring. Push for the disagreement.
- When capability fit is contested, *run the model*. A one-paragraph test on three representative instances resolves most arguments faster than discussion.
- Blast-radius score is where theatre creeps in. The honest score is calibrated against *what has actually gone wrong on this task in the last year*, not against worst-case fear.
- Judgment density is not the same as "complexity." A complex-but-mechanical task (a long refactor) can be low-judgment-density. A simple-but-political task (customer apology email) can be high.
- The **pilot candidate** bucket should not be a catch-all for "I don't know." Use it when the sort genuinely does not resolve and a scoped pilot would. If the bucket has >25% of your tasks, you did not score them.
- The sort is a living document, not a one-shot. Expect to re-run it every quarter. v0.1 does not need to be perfect; it needs to be defensible and dated.

## Acceptance criteria

The sort is complete when:

- 20–40 task families from your team's *actual* work are listed (not from a template).
- Each task carries a 1–5 score on all six dimensions, plus a one-line rationale.
- Each task is placed in one of the four buckets, with any rubric-override noted.
- At least three tasks are in *human-led* and at least two are in *pilot candidate* — if either bucket is empty, re-examine (empty buckets in a first-pass sort are a sign of under-scrutiny, not a sign of a clean team).
- The sort is reconciled against the C1 table in the human/machine contract; drift is fixed.
- The artifact is titled, dated, lists scorers, and carries a scope-and-caveats paragraph.
- One partner-function review has been done and either (a) reflected in the sort or (b) logged as a counter-argument.

## Stretch goals

- Run the sort *in the dark* — ask each scorer to pre-score independently without seeing yours, then compare. Disagreements before the session are higher-signal than disagreements after.
- Add a seventh column: *drift risk* — how stable is this score against the next model generation? (1–5, higher = more stable.) Tasks with low drift risk should carry a shorter re-score interval.
- For your top three *AI-first* tasks, draft the Chapter 2 → Chapter 3 bridge: what would the pilot look like if you decided to validate the sort at week-2 scale? This is the warm-up for Exercise 02.
- Map each *human-led* task to the skill it protects (e.g., "post-mortem writing protects root-cause reasoning skill"). The map is the input to [`mod-107`](../../mod-107-skill-growth-anti-atrophy-and-career-development/)'s anti-atrophy plan.
- Compare your team's bucketing to the broader pattern reported in the most recent Microsoft Work Trend Index, Stack Overflow Developer Survey, and (for engineering teams) GitHub Octoverse. Note divergences for the Exercise 04 industry-context paragraph.
