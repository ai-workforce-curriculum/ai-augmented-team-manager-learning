# Lab 02 — Red-Team a Broken Commissioning Brief

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 4 (the ten-section commissioning-brief rubric; the four eval shapes; judge calibration; what *not* to delegate), with a side-check against Chapter 7 (the ownership boundary with `ai-risk-engineer`).
**Complements, does not duplicate:** Exercise 04 asks you to write a **real** commissioning brief for an eval **your own** team would benefit from this quarter. This lab gives you a deliberately broken sample brief — every common failure mode present — so you can calibrate the rubric's bar before you have to write one yourself. Lab 02 is to Exercise 04 what Lab 02 of `mod-102` is to its exercise 02: a red-team on a known-bad sample.

## Objective

Read a deliberately broken sample commissioning brief for an LLM-as-judge eval. Grade it against the ten-section rubric from Chapter 4. Identify every gap. Rewrite the two sections that matter most — **pass / fail / regression thresholds** and **feedback loop** — so the harness owner could execute without a follow-up meeting. Produce a short grading memo that could be handed to the (fictional) author.

## Prerequisites

- Chapter 4 read end-to-end (the three framing questions; the four eval shapes; the ten-section brief; what *not* to delegate; what to read at what depth).
- Chapter 7 skimmed (the boundary with `ai-risk-engineer`; the three failure modes).
- A blank file for your grading memo and rewrites.
- A timer.

Optional but useful: the G-Eval paper abstract (<https://arxiv.org/abs/2303.16634>) for the calibration-against-human-judgement discipline.

## The fictional context

> **"Customer Platform" team, FinSure Financial Services.** 12 engineers (2 senior, 10 mid/junior). Owns `customer-comms`, a service that drafts internal-dashboard summaries of inbound customer support tickets and (optionally) proposes a first-draft reply. The team is running two agent workflows: (a) ticket summarisation for the internal dashboard card, (b) first-draft reply generation. Both are currently *opt-in* with sr-eng review. The team has an `ai-risk-engineer` peer, `@risk-peer`, in the central Security org. The team-manager drafted a commissioning brief last Friday and sent it to `@senior-ic-3` to build. `@senior-ic-3` replied this morning: *"I can start, but I have questions. Want to walk it on Wednesday?"* The manager wants to pre-empt the Wednesday meeting by fixing the brief first.

## The sample brief

Below is "Commissioning Brief v0.1: Customer-Comms Agent Eval." Read it once end-to-end before doing anything else. Do not take notes on the first pass.

```
COMMISSIONING BRIEF v0.1 — CUSTOMER-COMMS AGENT EVAL
Date: 2026-11-04. Author: @manager-handle.

Why
---
We should know how our customer-comms agents are doing. Leadership
has been asking. We want to measure quality.

What we'll evaluate
-------------------
The customer-comms agent (both flows — summary cards and first-draft
replies). Also any other related agent workflow we add later.

How
---
We'll use LLM-as-judge. The judge will score each output on a 1-5
scale for overall quality. We want high scores.

Dataset
-------
The team will use real customer tickets from the last quarter.

Judge
-----
Use whatever judge model is cheapest / most available.

Pass bar
--------
High scores. We'll know it's bad if the scores drop meaningfully.

Tool
----
TBD — maybe Promptfoo, maybe LangSmith, maybe we build something.
Pick whichever is fastest.

Owner
-----
The team.

Feedback
--------
We'll share results in our weekly team meeting.

Review
------
Ongoing.
```

Note the Friday email context: `@senior-ic-3` has already said they have questions. Your job is to find every one those questions is likely to be about.

## Steps

### Step 1 — Set up your grading memo (3 min)

Create a working file `lab-02-brief-grading.md`. Add this header:

```
# Lab 02 — Commissioning brief grading (Customer-Comms Agent Eval v0.1)

Ten-section rubric (Chapter 4):
  1. Decision this eval exists to inform (one sentence; tied to team action)
  2. Scope (which agent / workflow / class / model / data; what is OUT-of-scope)
  3. Eval shape (Golden-task / LLM-as-judge / Regression / Capability)
  4. Dataset (source, curator, freshness, privacy/sensitivity posture)
  5. Judge configuration (if judge-based: model, rubric, calibration requirement)
  6. Pass / fail / regression thresholds (specific numbers; specific triggers)
  7. Tool choice (Promptfoo / LangSmith / Inspect AI / other; justified in one line)
  8. Owner and co-owner (named humans; not "the team")
  9. Feedback loop (delivery location; reader; threshold-to-action; authoriser)
 10. Review and sunset (quarterly review; when does this end)

The three decisions the manager MUST NOT DELEGATE (Ch 4):
  - What to evaluate (the manager holds team work prioritisation)
  - What constitutes pass/fail (the number is a social instrument)
  - What the team does when the number moves (the response is a team-practice call)

Chapter 7 boundary: red-team / prompt-injection corpus / guardrail depth → `@risk-peer`.
                     eval-harness build on team's own workflow → senior IC on team.
                     Shared ownership between the two is fine.
```

### Step 2 — Grade each of the ten sections (20–25 min)

Work through the brief section by section. For each of the ten rubric items, note:

- What the brief *claims*.
- What the rubric *requires*.
- The specific gap, in one line.

Target: **no more than 2.5 minutes per section**. Do not scroll to the answer key until you have graded all ten.

Grade each on a three-point scale:

- **Pass** — the section meets the rubric bar as-is.
- **Partial** — present but missing a load-bearing element.
- **Fail** — missing, vague, or wrong.

### Step 3 — Identify delegation violations (5 min)

Separately: of the three things Chapter 4 says the manager must *not* delegate (what to evaluate, pass/fail bar, action on movement), which are being *delegated away* in this brief, and to whom? Chapter 4 says: *"If you find yourself being asked to approve the choice of embedding model or the schema of the eval dataset, you are being pulled too deep."* The inverse — being asked to approve a vague bar by the harness owner — is the pattern to spot.

### Step 4 — Check the Chapter 7 boundary (5 min)

Chapter 7 names three failure modes: *"I'll build it myself,"* *"The risk engineer will tell us what to measure,"* *"The risk engineer's report is self-explanatory."* Which, if any, is the sample brief sliding toward? Note it with one line of evidence.

Specifically: does the brief name `@risk-peer`? Should it? One of the two agent flows produces *replies to external customers*, which is the OWASP LLM01 / LLM05 / LLM06 risk surface that often warrants a companion commission to `@risk-peer`. The brief does not mention this. One-line observation.

### Step 5 — Compare against the answer key (10 min)

Below is the key — ten section grades, three delegation findings, and one Chapter-7 note. Count hits (same grade, same framing) and near-misses (same grade, different framing).

#### Answer key — section grades

1. **Decision — Fail.** "We should know how our agents are doing. Leadership has been asking." Chapter 4: *"An eval that is not attached to a team decision is a vanity metric. For each proposed eval, name the decision it informs."* "Measure quality" is not a decision. Examples the chapter gives: *"Should this workflow go default-on next quarter?"*, *"Should we block merges to the agent config without this gate passing?"*
2. **Scope — Fail.** Both flows plus "any other related workflow we add later" is not a scope statement; it is an opt-in-to-whatever. Chapter 4's brief shape asks for *specific* workflow(s), model version(s), repos, data, and an explicit *out-of-scope* list. There is no out-of-scope list at all.
3. **Eval shape — Partial.** "LLM-as-judge" is a shape, but the brief does not say *why* this shape over golden-task, regression, or capability. The reply-to-customer flow likely needs a *capability / safety* eval (LLM01 / LLM05 — can the agent refuse or sanitise a malicious ticket body?) in addition to a judge on quality. A single-shape brief that covers both flows will undermeasure the risky one.
4. **Dataset — Fail.** "Real customer tickets from the last quarter" is not a dataset specification. Missing: curator, instance count, freshness policy, and — load-bearing — the **privacy / sensitivity posture**. Chapter 4 explicitly points at `mod-110` for sensitive-data-through-a-third-party-judge, and customer tickets almost certainly carry PII. If the judge is a third-party-hosted model, this is a C5 data-handling decision that has not been made.
5. **Judge configuration — Fail.** "Use whatever judge model is cheapest" fails three Chapter 4 sub-bars at once. (a) No model is named. (b) No rubric is defined — Chapter 4's G-Eval reference requires a chain-of-thought, form-filling rubric; "overall quality 1-5" rewards verbose-as-faithful and is exactly the shape the chapter warns against. (c) No calibration requirement against human-rated judgement — the chapter says this is *"the single most common mistake with LLM-as-judge and the commissioning brief should require calibration evidence."*
6. **Pass / fail / regression thresholds — Fail.** "High scores" is not a number; "drop meaningfully" is not a trigger. Chapter 4 wants *specific-but-wrong* over *vague-but-right*: e.g., *"mean judge score ≥ 4.0/5.0 on the full 50-item golden set; regression on ≥ 0.2 drop between consecutive runs or ≥ 10 pp of items dropping category."*
7. **Tool choice — Fail.** "TBD — maybe Promptfoo, maybe LangSmith, maybe we build something" is the opposite of the brief's role. Chapter 4: *"Tool choice. Justified in one line."* One is chosen, justified against the brief's specific needs (CI integration? trace visibility? capability-eval structure?). "We build something" is a Chapter 7 Failure Mode A ("I'll build it myself") trap — the harness is not the team's product.
8. **Owner and co-owner — Fail.** "The team" is not an owner. Chapter 4: *"'The team' is not an owner."* Needs a named human for build and a named human for dataset curation; one is typically the `ai-risk-engineer` or `ai-eval-engineer` peer, the other a senior IC on the team. Here, the brief has gone to `@senior-ic-3` without the brief naming them.
9. **Feedback loop — Fail.** "Share results in our weekly team meeting" fails all four Chapter 4 sub-questions: *where delivered, who reads, what threshold triggers what action, who authorises the action*. A weekly-team-meeting update is not a loop — it is an informational broadcast. No threshold-to-action means no loop.
10. **Review and sunset — Fail.** "Ongoing" is not a sunset. Chapter 4: *"sunset when the decision the eval informs is retired."* The brief needs a quarterly-review date and a named sunset condition.

Section-grade count: **0 pass, 1 partial, 9 fail**. This is not an unusually bad first draft — it is a textbook "first-pass skip" that the rubric exists to prevent.

#### Answer key — delegation findings

1. **"What to evaluate" has been left unspecified** (section 1 Decision + section 2 Scope). Combined with "any other related workflow we add later," the brief is asking `@senior-ic-3` to decide the scope. Chapter 4: *"That is your call because you are the one holding the team's work prioritisation."*
2. **"What constitutes pass/fail" has been delegated to the harness owner** by implication ("high scores"). Chapter 4: *"A reviewer-facing number is a social instrument — if you do not understand why 4.0 and not 3.5, you cannot defend the number to the team or to leadership."* The manager must own the final number.
3. **"What the team does when the number moves" is absent entirely** (section 9). Chapter 4 names this as the third non-delegable decision; its absence means the first bad report lands with no response plan and the loop stays open.

#### Answer key — Chapter 7 boundary note

- **`@risk-peer` is unnamed; the capability / safety eval row for the reply-to-customer flow is missing.** Chapter 7 says the manager commissions red-team / guardrail / prompt-injection-corpus work from `ai-risk-engineer`; the reply flow is exactly the OWASP LLM01 / LLM05 surface that warrants a companion commission. Failure Mode B ("The risk engineer will tell us what to measure") is the dual to Failure Mode A — abdicating risk-prioritisation to the peer is as bad as doing their work for them. Fix: the brief should list the two flows separately, name `@risk-peer` as co-commissioner on the reply flow, and specify the capability-eval row (OWASP LLM01 / LLM05 / LLM06) alongside the judge row.

### Step 6 — Rewrite two sections (15–20 min)

Pick two sections and rewrite them to the Chapter 4 bar. **Required: section 6 (Pass / fail / regression thresholds) and section 9 (Feedback loop).** These are the two most non-negotiable sections; they also carry two of the three non-delegable decisions.

For section 6, your rewrite must:

- Name a specific pass-bar number with units (e.g., mean judge score ≥ X/5 on N items).
- Name a specific regression threshold with both a magnitude and a trigger (e.g., ≥ 0.2 drop between runs *or* ≥ 10 pp of items dropping category).
- Name what *action* the regression triggers (block merges to the agent config? rollback? ADR?) and *who authorises* it (tech lead for narrow; manager for workflow-level; sponsor plus governance for escalating).

For section 9, your rewrite must answer all four Chapter 4 sub-questions:

- Where is the report delivered? (channel; dashboard tile; Q-review slide; Monday pre-read.)
- Who reads it and what do they do? (triage; inform trend; new-finding → ADR draft.)
- What threshold triggers action? (named numerically — crosswalks to section 6.)
- Who authorises the action? (tech lead / manager / sponsor + governance.)

Example shape (this is calibration; your wording will differ):

```markdown
## Pass / fail / regression thresholds

- Pass bar: mean judge score ≥ 4.0/5.0 on the 50-item summary-card golden set,
  with ≥ 0.6 Spearman between judge scores and a 10-item human-rated sample
  (G-Eval calibration bar).
- Regression threshold: ≥ 0.2 drop in mean, OR ≥ 10% of items moving from
  category ≥ 4 to ≤ 3, between consecutive runs.
- Below pass bar once → block merges to the agent config; open an ADR. The
  tech lead authorises the block. Below bar twice consecutive → escalate to
  `@enablement-lead`.
```

### Step 7 — Reconcile against Chapter 7 (5 min)

Write one line naming `@risk-peer` as the co-commissioner for the reply flow and name the companion-brief shape (one paragraph). Chapter 4 names *"Stretch goal: draft a one-paragraph companion commission for `ai-risk-engineer` with the Chapter 7 boundary respected."* Do this inline in your grading memo.

## Expected output

A single scratch file, roughly two pages, containing:

- Ten rubric-section grades (Pass / Partial / Fail) with one-line rationales.
- Three delegation-violation findings.
- One Chapter-7-boundary note.
- Two rewritten sections (Pass / fail / regression thresholds; Feedback loop).
- One paragraph on the companion commission to `@risk-peer`.

Something like:

```
Section 6 (Pass/fail/regression thresholds) — FAIL.
  Brief says "high scores." No number; no regression trigger; no action; no
  authoriser. Chapter 4 requires all four. Also delegates the pass/fail
  decision to the harness owner, which is Chapter 4's second non-delegable
  decision.

Rewrite:
  Pass bar: mean judge score ≥ 4.0/5.0 on the 50-item summary-card golden set,
  with ≥ 0.6 Spearman against a 10-item human-rated sample.
  Regression: ≥ 0.2 drop in mean, OR ≥ 10% of items moving category, between
  consecutive runs.
  Action on first fail: block merges to agent config; open ADR; tech lead
  authorises. Second consecutive fail → escalate to @enablement-lead.
```

## Checkpoint

Before moving on to Exercise 04 (where you write the real commissioning brief for an eval your team would benefit from this quarter), you should be able to answer **yes** to all four:

- Did you grade at least nine of the ten sections correctly (Pass / Partial / Fail) with the correct rationale, including spotting that the `Decision` section is a vanity-metric rather than a team decision?
- Did you identify all three delegation-violation findings (*what to evaluate*, *pass/fail bar*, *action on movement*) and name where each is being delegated or left absent?
- Did your Pass/fail/regression rewrite produce **three specific numbers** (pass bar, regression magnitude, categorical shift) and name both the action and the authoriser?
- Did your Feedback-loop rewrite answer all four Chapter-4 sub-questions (where delivered, who reads, threshold-to-action, authoriser)?

If any answer is no, re-read Chapter 4's "What the manager produces: the commissioning brief" and "What *not* to delegate" sections — and the example two-paragraph brief at the end of Chapter 4 — before running Exercise 04 on a real workflow.
