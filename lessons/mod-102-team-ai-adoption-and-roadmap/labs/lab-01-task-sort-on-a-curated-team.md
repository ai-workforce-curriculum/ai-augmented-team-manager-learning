# Lab 01 — Task Sort on a Curated Sample Team

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 2 (jagged frontier, six-dimension rubric, four buckets), with a side-check against Chapter 1 (roadmap ownership) and Chapter 6 (contract-roadmap drift).
**Complements, does not duplicate:** Exercise 01 asks you to score *your own* team's tasks across the six-dimension rubric in a live 90-minute session. This lab uses a fixed, deliberately mixed task set for a fictional team so you can calibrate your scoring against a known answer key — before you spend a real session on your real team.

## Objective

Read a curated list of twelve task families for a fictional 10-engineer platform team. For each, (a) score the six-dimension rubric; (b) place it in one of the four buckets; (c) record a one-line rationale. Then compare against the answer key. The target is **no more than one bucket-level disagreement** with the key on the eight "clean" rows (1–3, 7–10, 12) and a defensible position on the four "contested" rows (4–6, 11).

## Prerequisites

- Chapter 2 read (six-dimension rubric; the AI-first / AI-assisted / human-led / pilot-candidate buckets; the ≥18-sum / no-single-score-≤2 rule of thumb).
- Chapter 1 skimmed (so you know where the sort lands in the roadmap artifact).
- A blank file for your scores and rationale.
- A timer you can check per task.

Optional but useful: Chapter 6's "writing failure modes" (so the rationale lines stay flat rather than marketing).

## The fictional team

> **"Lakehouse Platform" team, FinSure Financial Services.** 10 engineers (1 staff, 3 senior, 6 mid/junior). Owns the shared data lakehouse that most other engineering teams consume. Discipline: platform / data engineering. Current tool surface: GitHub + Cursor (enterprise SSO), an in-house Claude Code deployment behind the corporate proxy, Buildkite CI, Prometheus + Grafana. No agent deployment in production yet. The team is three months post-reorg; reviewer bandwidth is "okay but not generous"; one open security review against the lakehouse from Q3. Horizon: Q1 2027.

Score each task in the context of *this* team, not an idealised team — a judgment-dense task on this team may score differently than on a looser team.

## Steps

### Step 1 — Set up your scratch file (3 min)

Create a working file `lab-01-task-sort.md`. Add this header:

```
# Lab 01 — Task sort scratch (Lakehouse Platform, Q1 2027)

Rubric (Chapter 2, 1–5 per dimension, higher = safer where marked):
- CF   capability fit (does the model produce useful output on representative instances?)
- V    verifiability (can a reviewer verify in bounded time?)
- BR   blast radius (↑ safer — low score means hard-to-reverse / customer-visible)
- F    frequency
- JD   judgment density (↑ safer — low score means tacit / people / politics / context)
- R    reversibility

Rule of thumb:
- sum ≥18 with no cell ≤2  → AI-first
- sum 15–17, or sum ≥18 with one cell at 2  → AI-assisted (review-only)
- sum ≤12, or any cell =1 in BR/V/JD  → human-led this quarter
- otherwise  → pilot candidate
```

### Step 2 — Score the twelve tasks (30–40 min)

Below are twelve task families. For each: start the timer; write (a) the six scores; (b) sum; (c) bucket; (d) one-line rationale (why you landed where you did). Target **no more than 3 minutes per task**. Do not scroll to the answer key until all twelve are done.

Tasks 1–3 are "clean AI-first-ish" cases. Tasks 4–6 are contested. Tasks 7–10 are "clean non-AI-first" cases. Tasks 11–12 close the lab.

1. **PR descriptions on the lakehouse-ingestion repo.** ~35 PRs/week; reviewer reads the diff anyway; the description is a summary.
2. **Unit-test skeletons for new ETL transforms in Python.** ~15–20 new transforms per quarter; `pytest` runs in CI; coverage gate at 80%.
3. **First-draft ADRs for small-to-medium data-model changes.** ~2–3 per month; template already in `docs/adr/`; staff engineer and senior eng always review.
4. **SQL skeletons against the lakehouse for ad-hoc analyst requests routed to the team.** ~10 asks/week; results sometimes land in a customer-facing analytics product (via the PM peer); reviewer is usually a mid-level engineer.
5. **Short Slack replies to downstream consumer teams' questions about ingestion delays or schema changes.** ~5–10/day; sometimes politically sensitive (contested migrations).
6. **Golden-task eval authoring for a new data-quality check pipeline.** Needs to run as a `mod-103`-style eval harness; team has no in-house eval expertise; the staff engineer wants to own the design.
7. **Incident post-mortems for lakehouse data-quality incidents.** ~1–2 per quarter; blameless template exists; always root-caused by the responder.
8. **Quarterly performance input for direct reports.** Done by the manager; sensitive.
9. **Security review comments on Platform's proposed enterprise LLM gateway.** Legal-adjacent; staff engineer owns; one open finding from Q3's review of the lakehouse.
10. **Migration-sequencing plans for cross-team data-model changes.** 2–3 per quarter; touches 4–6 downstream teams; failure mode is cascading breakage across the org.
11. **On-call runbook edits — adding or updating the "what to do if X" entries in the team runbook.** ~2–4 edits/week; runbook is read at 3am by whoever is on-call.
12. **Author the team's quarterly ROI one-pager (per `mod-104`), summarising adoption, time deltas, and token cost.** Done by the manager; audience is the VP and the enablement lead.

### Step 3 — Compare against the answer key (10 min)

Below is the key. For each task, compare your score and bucket to the key; count hits (same bucket) and near-misses (one bucket off, e.g., AI-first vs. AI-assisted). Specific dimension scores may differ by a point in either direction without being a miss — the bucket is the load-bearing output.

#### Answer key

> **Note on scores.** The scores below are one defensible scoring on the Lakehouse team, dated against a late-2026 model generation. Your scoring may differ by ±1 on individual cells; what matters is the bucket and the rationale. Where your bucket differs, the answer key's rationale is the arbitrator.

1. **PR descriptions** — CF 5, V 5, BR 4, F 5, JD 5, R 5. Sum **29**. **AI-first.** Inside the frontier; reviewer reads the diff; consistency across the team adds value in review.
2. **Unit-test skeletons** — CF 5, V 5, BR 4, F 4, JD 5, R 5. Sum **28**. **AI-first.** `pytest` is the verifier; failing test is self-flagging; test-skeleton drafting is a textbook Dell'Acqua "inside-the-frontier" task.
3. **First-draft ADRs** — CF 4, V 4, BR 4, F 3, JD 3, R 5. Sum **23**. **AI-first.** Lower frequency and judgment-dense enough that the staff + senior always review — but that review is already in the workflow, which is why it survives as AI-first. (Compare to Chapter 2's worked example.)
4. **Ad-hoc SQL against the lakehouse** — CF 4, V 3, BR 2, F 5, JD 3, R 3. Sum **20**. **AI-assisted (review-only).** The BR of 2 (results sometimes flow to a customer-facing product) blocks AI-first; verifiability is a review step, not a test run. Chapter 3's four-question rollout check would put this in opt-in with mandatory sr-review during a pilot. Contested row: a defensible alternative is "pilot candidate" if the review bar is uncertain. Mark as pilot candidate *only* if you flag the review-bar uncertainty in the rationale.
5. **Short Slack replies to downstream teams** — CF 3, V 2, BR 2, F 5, JD 2, R 2. Sum **16**. **Human-led this quarter.** JD 2 and BR 2 are the pins — a short reply to a consumer team in a contested migration is a judgment-dense, hard-to-reverse artifact even if the words look short. Contested row: a defensible alternative is AI-assisted with a strict "sr-eng review before send" bar, but at this team's reviewer bandwidth, Chapter 3's fourth question ("will the review bar hold at full-team scale?") says no.
6. **Golden-task eval authoring** — CF 3, V 3, BR 3, F 2, JD 3, R 4. Sum **18**. **Pilot candidate.** Exactly the "rubric does not resolve" case: the team has no eval expertise, the staff engineer wants to own the design, and `mod-103` is where the eval-commissioning method lives. A 4-week pilot with the `ai-risk-engineer` peer (Chapter 2 example) is the right answer. Contested row: a defensible alternative is "human-led this quarter" if the staff engineer's ownership intent takes it entirely off-roadmap.
7. **Incident post-mortems** — CF 3, V 2, BR 1, F 1, JD 1, R 1. Sum **9**. **Human-led.** BR 1 and JD 1 and R 1 all pin this to human-led regardless of sum; this must also show up as "AI may not draft" in the C1 column of the human/machine contract (mod-101 Chapter 3). Chapter 2 names this as a canonical human-led example.
8. **Performance input** — CF 3, V 2, BR 1, F 2, JD 1, R 1. Sum **10**. **Human-led.** Same pins as #7; this is also "AI may not draft" in C1. Chapter 2 canonical example.
9. **Security review comments** — CF 3, V 3, BR 1, F 2, JD 2, R 2. Sum **13**. **Human-led.** BR 1 (regulated, legal-adjacent, open Q3 finding) is the pin; this is a `mod-110`-shaped workflow and should also be "AI may not draft" in C5 (data-handling) at a minimum, likely also C1.
10. **Migration-sequencing plans** — CF 3, V 2, BR 2, F 1, JD 2, R 2. Sum **12**. **Human-led.** Judgment-dense (team-politics, cascading failure modes, downstream-consumer context the model cannot see); Chapter 2's worked example scores this exactly at the human-led boundary.
11. **On-call runbook edits** — CF 4, V 4, BR 3, F 3, JD 3, R 4. Sum **21**. **AI-assisted (review-only).** Capability fit is strong; the "read at 3am" blast radius is why the shipping artifact must go through a human pass. Chapter 2's worked example buckets this identically.
12. **Quarterly ROI one-pager** — CF 4, V 4, BR 3, F 1, JD 3, R 4. Sum **19**. **AI-first** (drafting), with a strong caveat. The manager still writes the narrative; the model drafts the data-ingestion-and-summarise step. If you are scoring this as "human-led" because you (the manager) write it personally, that is a legitimate Chapter 1 move — the manager-altitude artifact is yours — but note the sort-level answer is still AI-first on the drafting sub-step. Contested read: either scoring is defensible; the point is to notice the difference between *who ships the artifact* and *what step gets AI-drafted*.

### Step 4 — Diagnose misses (10 min)

For every bucket-level miss (and any bucket you are uncertain about on the contested rows 4, 5, 6, 11, 12), write one paragraph in your scratch file:

- Which dimension did you over-score or under-score, and what was the reason?
- Did you pin the task on a single ≤2 cell (the Chapter 2 override) or on the sum? If on the sum, did you miss a ≤2 cell that should have been an override?
- Is the blast-radius score calibrated against *what has actually gone wrong on this task* on a team like this, or against worst-case fear? (Exercise 01 starter guidance: blast-radius score is where "theatre creeps in.")
- Did you confuse *complexity* with *judgment density*? (Exercise 01 starter guidance: a long refactor is complex but not judgment-dense; a customer apology email is simple but very judgment-dense.)

### Step 5 — Reconcile against the C1 table (5 min)

Chapter 2 says the four buckets are "the operational twin" of the C1 table in the human/machine contract (mod-101 Chapter 3). For tasks 7, 8, and 9 above, write one line each on what the C1 bucket must say. For tasks 1, 2, and 11, write one line each on what C1 must say so the roadmap and contract stay consistent. Example shape:

```
Task 7 (post-mortems): C1 must read "AI may not draft."
Task 1 (PR descriptions): C1 must read "AI may draft; reviewer reads the diff anyway."
Task 11 (runbook edits): C1 must read "AI may draft; mandatory sr-eng review before merge."
```

If any of your six scoring buckets contradict a sensible C1 posture, Chapter 6's "drift between contract and roadmap" failure mode applies — flag it in the scratch file.

### Step 6 — Re-run four contested rows from memory (5 min)

Close your file for a minute, then re-score rows 4, 5, 6, and 12 from memory. Compare to your first pass. Tasks where your first-pass and second-pass buckets disagree are the tasks where the rubric is not yet internalised — mark them for revisit when you run Exercise 01 live.

## Expected output

A single scratch file, roughly one to two pages, containing:

- Twelve rows of six scores + sum + bucket + one-line rationale.
- A diagnostic paragraph per bucket-level miss or contested-row uncertainty.
- Six one-line C1-reconciliation notes.
- A re-run of four contested rows from memory.

Something like:

```
Task 1 (PR descriptions)
  CF 5  V 5  BR 4  F 5  JD 5  R 5   sum 29   AI-first
  Reviewer reads the diff; consistency across the team adds value.
  ✅ match.

Task 4 (ad-hoc SQL)
  CF 4  V 3  BR 2  F 5  JD 3  R 3   sum 20   AI-assisted (review-only)
  BR 2 (customer-facing analytics product) blocks AI-first; sr-eng review required.
  ✅ match — contested row; alternative pilot-candidate flagged.

Task 5 (Slack replies)
  My pass: CF 3  V 3  BR 3  F 5  JD 3  R 3   sum 20   AI-assisted
  Key:                                       sum 16   human-led
  Miss. Over-scored JD and BR; "contested migration" context pins both at 2.
  Lesson: judgment-density = team-politics and context-the-model-cannot-see.
```

## Checkpoint

Before moving on to Exercise 01 (where you score **your team's** real task inventory), you should be able to answer **yes** to all four:

- Did you match the answer-key bucket on all eight "clean" rows (1, 2, 3, 7, 8, 9, 10, 12)?
- For each of the four contested rows (4, 5, 6, 11), did you either match the key or write a rationale that cites the specific dimension and the Chapter 3 four-question check that resolves the tension?
- Did you correctly apply the "any cell ≤1 in BR / V / JD → human-led regardless of sum" override on rows 7, 8, and 9?
- Did your six C1-reconciliation notes agree with the bucket-level call? (If any contradict, the roadmap and contract would be in drift per Chapter 6.)

If any answer is no, re-read Chapter 2's "A six-dimension task-sort rubric" and "Four outcome buckets" sections — and the contested-row rationales above — before running Exercise 01 on your real team's tasks.
