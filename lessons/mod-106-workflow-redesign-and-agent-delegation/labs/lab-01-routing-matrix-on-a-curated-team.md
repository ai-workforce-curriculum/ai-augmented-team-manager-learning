# Lab 01 — Routing Matrix on a Curated Sample Team

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 1 (jagged frontier framing) and Chapter 2 (the three-question placement, the five destinations, the three mis-routing failure modes), with side-checks against Chapter 3 (delegation level implications) and Chapter 7 (*stop-doing-this* as attention-redirection input).
**Complements, does not duplicate:** Exercise 01 asks you to produce v0.1 of the routing matrix for *your own* team. This lab uses a fixed, deliberately mixed task set for a fictional team so you can calibrate your three-question placement and the paired-vs-unattended-vs-senior decision against a known answer key — before you spend a real session on your real team.

## Objective

Read a curated list of **ten recurring task types** for a fictional 14-engineer internal-tools team. For each, (a) answer Chapter 2's three placement questions; (b) assign one of the five destinations (plus *stop doing this*); (c) write a one-sentence jagged-frontier "why"; (d) name the per-row review mechanism. Then compare against the answer key. The target is **no more than one destination-level disagreement with the key on the seven "clean" rows (1, 2, 3, 6, 7, 9, 10) and a defensible position on the three "contested" rows (4, 5, 8)**.

## Prerequisites

- Chapter 1 read (jagged-frontier framing; the five pieces of mod-106).
- Chapter 2 read (the three-question placement; the five destinations plus *stop doing this*; the three mis-routing failure modes).
- Optional: Chapter 3 skimmed (so you can anticipate the Level-N implication of each destination).
- A blank text file or notebook for your placements.
- A timer you can check per task.

## The fictional team

> **"Internal Tools" team, MerchHub Retail.** 14 engineers (1 staff, 4 senior, 9 mid/junior). Owns the handful of small internal apps and CLIs that the rest of engineering uses every day: the deploy console, the on-call paging tool, the release-notes generator, the feature-flag admin UI, and the internal expense portal. Discipline: full-stack + a bit of SRE-flavoured work. Current tool surface: GitHub Enterprise, Cursor (SSO), an internal Claude Code deployment behind the corporate proxy, PagerDuty, Datadog, and an internal MCP server for the deploy console that is already approved on the tool-authorisation policy allow-list. Reviewer bandwidth is "fine, not generous." No agent deployment in production customer-facing paths. One junior engineer finished a rotation two weeks ago and has capacity to take on developmental assignments.

Score each task against this team, not an idealised team. Review bandwidth and the junior engineer's developmental runway matter.

## Steps

### Step 1 — Set up your scratch file (3 min)

Create a working file `lab-01-routing.md`. Add this header:

```
# Lab 01 — Routing matrix scratch (Internal Tools, MerchHub)

Three-question placement (Chapter 2):
  Q1. Transformation of existing input (summarise/translate/reformat/lint-check)
      or judgment grounded in context the model does not have?
        → transformation = Inside;  judgment = Outside
  Q2. Can a non-expert reader check the output in <60s and catch an error,
      or does it need 10+ min of context to evaluate?
        → fast-checkable = Inside;  slow-to-check = Outside
  Q3. Well-represented in public written material, or bespoke to this team's
      vocabulary and conventions?
        → well-represented = Inside;  bespoke = Outside

Five destinations (+ sixth):
  - AI unattended
  - AI + human pair, variant A  (AI drafts, human reviews before use)
  - AI + human pair, variant B  (human drafts, AI refines / pattern-checks)
  - Junior human (± AI)
  - Senior human (± AI)
  - Stop doing this task

Default when uncertain: AI + human pair, variant A.
Three failure modes to notice in myself:
  F1. over-routing to AI unattended  → start with 0–1 unattended rows
  F2. over-routing to senior human   → >20% senior-human is a bottleneck smell
  F3. under-routing to junior human  → ask: "could a junior do this with AI pair?"
```

### Step 2 — Route the ten task types (30–40 min)

Below are ten recurring task types on the Internal Tools team. For each: **start the timer**, then write (a) the three placement answers as `I` or `O` for inside/outside (e.g., `I / O / I`); (b) the destination; (c) the one-sentence "why" grounded in jagged-frontier reasoning; (d) the per-row review mechanism; (e) time elapsed. Target **no more than 3 minutes per row**.

Tasks 1–3 are "clean inside-frontier" cases. Tasks 4–6 are contested or edge cases. Tasks 7–10 round out the mix.

Do **not** scroll to the answer key until you have placed all ten.

1. **Weekly release-notes generator**: produce a formatted changelog from merged-PR titles and commit messages for the team's internal CLIs. The output is published to an internal channel. The current workflow is the staff engineer copy-pasting from `git log` into a template every Thursday.
2. **Unit-test skeletons** for new HTTP handlers in the feature-flag admin UI (TypeScript). ~8–12 new handlers per quarter. `vitest` runs in CI; coverage gate is in place; the senior engineers review the final test coverage anyway.
3. **Deploy-console runbook entry drafting**: adding a short "if X breaks, do Y" entry to the deploy console's runbook when a new deploy failure mode is first observed. Read at 3am by whoever is on-call.
4. **Code review on a single-file bug fix PR** where the author has reproduced the bug locally and added a regression test; ~6–10 of these per week across the team's repos.
5. **PR review on a multi-file refactor** of the internal expense portal's payment-splitting logic. ~1–2 of these per month; reviewer historically catches 2–3 subtle correctness issues per refactor on average.
6. **Architecture decision record (ADR) authoring** for the choice of a new internal background-job system to replace the current cron-based scheduler. Multi-quarter blast radius; the staff engineer owns the decision.
7. **Weekly team status one-pager to the VP of Engineering** summarising shipped work, open risks, and hiring status. Done by the manager; the audience is external-ish within the company.
8. **Feature-flag change proposals** — a short write-up proposing to flip, add, or remove a feature flag in a shipped product. ~5–8 per week; sometimes customer-facing, sometimes internal-only; the PM co-signs the customer-facing ones.
9. **Postmortem write-up from an incident Slack timeline** for an incident in the deploy console. The sequence-of-events section is a timeline reconstruction; the root-cause and action-items section is a judgment call.
10. **Monthly "team dashboard polish" document** — a 2-page summary of the team's Datadog dashboards with annotations on which graphs matter this month. Historically read by nobody; filed because a long-gone director once asked for it.

### Step 3 — Compare against the answer key (10 min)

For each task, compare your destination to the key below. Count hits (same destination) and near-misses (one step off — e.g., *AI + human pair variant A* vs. *AI unattended*). Specific `I`/`O` answers on the three questions may differ by one answer in either direction without being a miss — the *destination* is the load-bearing output, and the "why" is how you defend it.

#### Answer key

> **Note on calibration.** The destinations below are one defensible routing on this fictional team against a late-2026 model generation and the team's stated reviewer bandwidth. Your reading may differ by one destination step on individual rows; what matters is the destination, the jagged-frontier "why," and the per-row review mechanism. On contested rows (4, 5, 8), the key notes the defensible alternative.

1. **Weekly release-notes generator.** `I / I / I`. **AI unattended.** Inside frontier (mechanical aggregation of structured input), fast-checkable (reader scans the list), well-represented (release-notes is a textbook summarisation task). Blast radius small (internal doc). Review mechanism: monthly Kind-4 sample-audit by rotating senior; written finding. This is one of the 1–2 AI-unattended rows a disciplined v0.1 matrix will carry.
2. **Unit-test skeletons.** `I / I / I`. **AI + human pair, variant A, with the junior as reviewer.** Inside frontier; `vitest` is an automatic verifier; the senior review is already in the workflow (the coverage gate forces review regardless). Could defensibly be promoted to AI unattended later with an audit mechanism, but at v0.1 the paired variant is correct. Review mechanism: mod-103 §Test-review checklist + senior sign-off at PR close. Deliberately route to **junior reviewer** to counter Failure 3 (under-routing to junior).
3. **Deploy-console runbook entry.** `I / O / O`. **AI + human pair, variant A.** Drafting the entry is inside frontier, but the *"what to do if X breaks"* judgment is local-context knowledge and the entry will be read at 3am — the blast radius of a wrong instruction is high even though the artifact is short. Review mechanism: mod-103 §Runbook checklist; on-call reviewer sign-off before merge. Could defensibly be variant B (human drafts, AI pattern-checks against prior runbook entries), which may be the stronger fit here — note the variant choice in the "why."
4. **Code review on single-file bug fix PR with regression test.** `I / I / I`. **AI + human pair, variant A, reviewer = junior engineer (developmental).** Inside frontier for the diff-reading sub-task; the regression test is the automatic verifier. The junior-reviewer assignment is a deliberate counter to Failure 3 — the junior learns the mod-103 review-standard mechanics *and* the AI-review craft (noticing where the agent's review comment is subtly wrong). Review mechanism: mod-103 §Code-review checklist. Contested row: defensibly routable to AI unattended if you are confident the regression-test + CI gate catches enough — but v0.1 should default to paired. Key arbitrator: pair, with junior reviewer.
5. **Multi-file refactor review on the expense portal's payment logic.** `I / O / O`. **Senior human (with AI as research tool, not drafter).** Outside frontier on verifiability (reviewer historically catches 2–3 subtle correctness issues per refactor — fast-check fails) and outside on local-context knowledge (payment-splitting logic is bespoke). Blast radius is customer-adjacent money handling. Review mechanism: no AI output ships; AI used only for background-reading and test-case brainstorming. Contested row: a defensible alternative is AI + senior-human pair variant B (human reviews, AI pattern-checks) — mark that if you take it, but the "AI drafts the review" variant A is not defensible here.
6. **ADR authoring for background-job system choice.** `O / O / O`. **Senior human.** Outside frontier (multi-quarter judgment grounded in the team's history, its hiring plans, and other systems' adjacency); the decision is irreversible-with-work and the blast radius is multi-quarter. Review mechanism: AI drafts the *background* and *alternatives-considered* sections only (see Chapter 3's platform-team Row 3); the decision, consequences, and follow-up-actions sections are authored by the staff engineer and are not AI output.
7. **Weekly VP status one-pager.** `I / I / O`. **AI + human pair, variant A.** Inside frontier on the aggregation sub-task; fast-checkable by the VP; but the framing and the *which risks to surface this week* judgment is manager-owned local context. The manager is the reviewer and signer. Review mechanism: manager reviews, edits, and ships. Note that this is a *manager-altitude* workflow — the destination is AI-paired, but the human in the pair is you, not an IC.
8. **Feature-flag change proposals.** `I / O / O` for customer-facing; `I / I / I` for internal-only. **Split the row** into two: *customer-facing feature-flag changes* → **AI + human pair, variant A, PM co-signs** (slow-to-check because of customer impact + bespoke per product area); *internal-only feature-flag changes* → **AI + human pair, variant A** at a lighter review bar. Contested row: the key's point is that your v0.1 draft of this row should **decompose the task-type** — Chapter 2 Step 1 ("name the task-type precisely") was failed if you tried to route the combined row. Partial credit for noticing the decomposition in your "why."
9. **Postmortem write-up.** `I / O / O` on the combined artifact. **Decompose**: *timeline reconstruction sub-task* → AI + human pair, variant A (inside frontier, IC reviews); *root-cause and action-items sub-task* → **senior human (incident responder authors; AI not permitted)**. This is the Chapter 3 Row 2 shape ("narrative sequence inside frontier; root-cause outside frontier; must be human-authored"). Review mechanism: mod-109 postmortem standard; timeline draft reviewed, root-cause authored not reviewed.
10. **Monthly team-dashboard polish document.** `I / I / O` on surface, but the right call is **Stop doing this task.** Historically read by nobody; filed for a now-departed director. This is exactly the shape Chapter 2's *stop-doing-this* lane catches, and the arrival of AI would tempt the team to "automate it cheaply" when the correct move is to retire the ritual. The retired capacity feeds Chapter 7's attention plan. If you routed this to AI unattended, that is the specific failure the chapter calls out — note it in your diagnostic paragraph.

### Step 4 — Diagnose misses (10 min)

For every destination-level miss (and any contested-row position where your "why" differs from the key's reasoning), write one paragraph:

- Which of Chapter 2's three placement questions did you answer differently from the key, and why?
- Did you fall into one of the three failure modes? *Failure 1* (over-route to AI unattended) is most likely on rows 2, 4, and 10. *Failure 2* (over-route to senior human) is most likely on rows 4, 7, and 8. *Failure 3* (under-route to junior human) is most likely on row 4.
- Did you treat the *task type* as named precisely enough? Rows 8 and 9 reward decomposition; a single destination on either is Step-1 of the Chapter 2 procedure failed.
- Did you confuse *tool preference* with *jagged-frontier reasoning* in the "why"? *"We use Cursor here so this routes to AI"* is Chapter 2's named anti-pattern.

### Step 5 — Reconcile against the delegation ladder (5 min)

Chapter 3 says every AI-touching row in your routing matrix will need a corresponding delegation-ladder entry. For rows 1, 2, 3, and 9 (specifically the timeline sub-task), write one line each naming the **expected delegation level** (1–7 from Chapter 3's Appelo mapping) you would propose at v0.1.

Example shape:

```
Row 1 (release-notes generator): Level 6 — act unattended with post-hoc audit.
Row 2 (unit-test skeletons): Level 3 — draft-and-present with aggregate audit.
Row 3 (runbook entry): Level 2 — draft-and-present, approval required.
Row 9 (timeline sub-task): Level 3 — draft-and-present with aggregate audit; root-cause sub-task is outside the ladder entirely.
```

If your routing destination and your expected delegation level are inconsistent (e.g., you routed a row to *AI + human pair variant A* but picked Level 5), flag the mismatch — Chapter 3's consistency rule says the ladder and the HITL/destination must agree.

### Step 6 — Re-run three contested rows from memory (5 min)

Close your file for a minute, then re-route rows 4, 8, and 9 from memory. Compare to your first pass. If your destination or decomposition differs between passes, the chapter is not yet internalised — mark the row for revisit when you run Exercise 01 on your own team.

## Expected output

A scratch file, roughly one to two pages, containing:

- Ten rows: three placement answers, destination, one-sentence "why," review mechanism, timing.
- A diagnostic paragraph per destination-level miss or contested-row uncertainty.
- Four one-line ladder-level notes (Step 5).
- A re-run of three contested rows from memory.

Something like:

```
Row 1 — release-notes generator
  I / I / I  →  AI unattended
  Why: inside frontier (aggregation), fast-checkable, well-represented; blast radius small (internal doc).
  Review: monthly Kind-4 sample-audit by rotating senior; written finding.
  Time: 1m 40s.
  ✅ match.

Row 4 — single-file bug-fix PR review
  My pass: I / I / I  →  AI + human pair A, reviewer = senior
  Key:                 →  AI + human pair A, reviewer = junior (developmental)
  Near-miss on reviewer role. Fell into Failure 3 (under-route to junior).
  Lesson: when the task is inside frontier and the review bar is bounded by mod-103 checklist,
  deliberately route the review to junior as the developmental assignment.

Row 10 — monthly team-dashboard polish
  My pass: I / I / O  →  AI unattended
  Key:                 →  Stop doing this task
  Miss. Fell into the "legitimise more routine work because now we can afford it" trap.
  Lesson: an honest matrix surfaces 1–2 stop-doing rows; the freed capacity feeds Chapter 7.
```

## Checkpoint

Before moving on to Exercise 01 (where you route *your team's* real recurring task types), you should be able to answer **yes** to all four:

- Did you match the answer-key destination on all seven "clean" rows (1, 2, 3, 6, 7, 9 timeline sub-task, 10)?
- For each of the three contested rows (4, 5, 8), did you either match the key or write a "why" that cites the specific placement answer and the failure-mode counter-measure that resolves the ambiguity?
- Did you decompose rows 8 and 9 into sub-tasks instead of trying to route the combined row?
- Did you identify row 10 as *stop-doing-this*, not an AI-unattended row?

If any answer is no, re-read Chapter 2's "The routing rule, derived from the jagged frontier," the three mis-routing failure modes, and the platform-team example — then re-attempt the misses — before running Exercise 01 on your real team's tasks.
