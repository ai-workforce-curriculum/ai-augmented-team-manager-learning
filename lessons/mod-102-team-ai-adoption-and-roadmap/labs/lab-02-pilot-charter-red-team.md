# Lab 02 — Pilot Charter Red-Team on a Broken Sample

**Duration:** 60 minutes.
**Chapters exercised:** Chapter 3 (the seven charter fields; kill criteria; opt-in / opt-out / mandate; the four-question adoption-mode check).
**Complements, does not duplicate:** Exercise 02 asks you to draft **your own** quarter's worth of pilot charters for the AI-first and pilot-candidate buckets from your real task sort. This lab gives you a deliberately broken sample charter — with every common failure mode present — and asks you to grade it against the Chapter 3 bar, then rewrite the two sections that matter most. Doing this first sharpens your eye for what a workable charter looks like, before you have to write one on your own team.

## Objective

Read a sample pilot charter that has multiple deliberate gaps. Identify every gap against Chapter 3's seven required fields. Rewrite two sections — the **kill criteria** and the **adoption-mode reasoning** — to meet the bar. Produce a short grading memo that could be handed to the (fictional) author.

## Prerequisites

- Chapter 3 read (why pilot; the seven charter fields; opt-in / opt-out / mandate; the four questions; the "pilots that are actually contract revisions" sub-section).
- A blank file for your grading memo and the rewritten sections.

Useful but not required: Chapter 6 (the "writing failure modes" — marketing voice, hedging, undated owners).

## Steps

### Step 1 — Read the sample charter (5 min)

Below is "Lakehouse Platform Team: AI-Drafted SQL Pilot Charter v0.1." Read it once end-to-end before doing anything else. Do not take notes on the first pass.

```
LAKEHOUSE PLATFORM TEAM — AI-DRAFTED SQL PILOT CHARTER v0.1

We are launching an exciting new initiative to transform our team's
analytics velocity with AI-drafted SQL. This is the first step in our
broader journey toward AI-augmented engineering excellence.

Workflow
--------
The team will use AI to draft SQL queries against the lakehouse for
ad-hoc analyst requests. We think this will save significant time.

Cohort
------
The team (everyone who wants to participate).

Horizon
-------
Q1 2027.

Success
-------
- We aim to explore meaningful productivity gains.
- SQL output should be accurate.
- Analysts should be happy.

If it doesn't work
------------------
We will revisit at the end of Q1.

Adoption
--------
All engineers will be required to use the AI drafting workflow for
any SQL request longer than 10 lines. This mandate is being issued
by the team lead to ensure consistency.

Tools
-----
Cursor + Claude Code.

Owner
-----
The team.
```

### Step 2 — Grade against the seven charter fields (15 min)

Chapter 3 names seven required fields for a pilot charter:

1. Task and workflow (family from task sort + specific workflow — repo, tool, prompt pattern, review step).
2. Cohort (named ICs, 2–5, representative, opt-in — not a self-selected enthusiast club, not a draft from across the team).
3. Horizon (2–6 weeks; longer than 8 and it is no longer a pilot).
4. Success criteria (pre-committed, measurable, same metrics you intend to use at rollout scale).
5. Kill criteria (pre-committed; what causes stop-and-not-promote).
6. Decision owner and decision date (specific date on which promote-or-kill is called and logged in the decision log).
7. Data collection plan (how, who, where).

Open your grading file. Under each of seven headings, write **present / partial / missing**, and a one-line note on what is specifically wrong. Expect to find at least one failure per field. Do not count "the document exists under that heading" as present; count "the content meets the Chapter 3 bar" as present.

A worked example for field 2:

```
Field 2 — Cohort: missing.
"The team (everyone who wants to participate)" is a self-selected
enthusiast club, which Chapter 3 names as exactly the wrong cohort
shape. Charter must name 2–5 ICs, representative of the team.
```

### Step 3 — Grade against the adoption-mode four questions (8 min)

Chapter 3's four questions resolve the opt-in / opt-out / mandate choice:

1. Is there a legitimate reason an IC should not do this with AI this quarter? (Context the model cannot see; a specific client constraint; an in-flight incident; a personal-skill protection window per `mod-107`.)
2. Does consistency across the team add real value?
3. Did someone above you (security, legal, enablement lead, exec) already say "yes, this is required"?
4. Will the review bar hold at full-team scale?

Under heading **Adoption mode**, write:

- Which of the four questions does the sample charter answer?
- Did the "mandate" come from above the team lead, or did it originate at team-manager altitude?
- Would the review bar hold at full-team scale for ad-hoc SQL on this team? (Lab 01 scored this task's blast radius at 2 — customer-facing analytics product sometimes consumes the output — which is the Chapter 3 sign that the review bar is doing real work.)
- Apply Chapter 3's default sequence: opt-in during pilot, opt-out after a successful pilot, mandate only when the mandate came from somewhere else. What should the mode be, and why?

Expect to find: a manager-origin mandate with none of the four questions resolved; a mode that Chapter 3 says you will likely have to walk back within a quarter.

### Step 4 — Grade the writing voice (5 min)

Chapter 6 names three writing failure modes — marketing voice, hedging, and undated / un-owned statements. Under heading **Voice**, write:

- Which phrases in the charter are marketing voice? (Hint: "exciting," "transform," "excellence," "broader journey," "significant.")
- Which phrases are hedging? (Hint: "aim to explore," "meaningful," "should be accurate," "should be happy," "we think.")
- Which statements are undated or un-owned? (Hint: "the team," "the team lead," "end of Q1," "Q1 2027" with no start date.)

Three or more hits in each column is a tell that the charter was written to be announced, not to be executed.

### Step 5 — Rewrite the kill-criteria section (12 min)

Open a new section in your grading file: **Field 5 — Kill criteria, rewritten.** Replace the sample's "If it doesn't work: we will revisit at the end of Q1" with a block that meets the Chapter 3 bar:

- Pre-committed. Falsifiable. Dated.
- At least one numeric trigger (e.g., quality bar, cost, adoption rate).
- At least one *operational* trigger — reviewer-burnout signal or an incident ([`mod-109`](../../mod-109-accountability-incident-response-and-blameless-postmortems/)-shaped) — so the pilot has a stopping rule that will fire even if the numeric metrics are silent. Exercise 02's starter guidance is explicit about this.
- A "no measurable improvement by end of horizon" rule *can* be present, but cannot be the only rule.
- A specific decision date on which the promote-or-kill call lands.

Target: four to six bullet lines. Use the terseness of Chapter 3's style, not the marketing voice of the sample.

A worked calibration for the shape (not a template to copy verbatim):

```
Kill criteria (any one triggers stop-and-not-promote):
- Reviewer-reported quality bar drops for two consecutive weeks
  (reviewer survey n≥3 per week; "drops" = any reviewer rating the
  AI-drafted output below "would ship from an IC").
- Any P1 data-quality incident attributable to an AI-drafted query
  that was not caught in review.
- Token spend exceeds $X/week per pilot IC for two consecutive weeks.
- No measurable median-time delta on the target workflow by end of
  week 4 (data from Field 7 collection plan).

Decision call: YYYY-MM-DD, @manager, logged in the decision log.
```

### Step 6 — Rewrite the adoption-mode section (10 min)

Under a new heading **Adoption mode, rewritten**, replace the sample's manager-origin mandate with:

- The mode that Chapter 3's default sequence prescribes for a pilot (opt-in during the pilot itself).
- The mode you will walk the team to *after* the pilot completes, *if* the success criteria hold — with the four-question check applied and shown in one line per question.
- A trigger that shifts the post-pilot mode: "opt-out if adoption > X% under opt-in by week N *and* reviewer quality bar holds *and* the review bar can carry rollout load." Chapter 6 calls this the trigger-to-revisit shape.
- Explicit statement that mandate is *not* on the table from team-manager altitude for this workflow (unless something above the team lead has issued it — which the sample did not).

Target: six to eight lines. Terse. In the voice of a commitment document, not a rally memo.

### Step 7 — Write the grading memo (5 min)

At the top of your file, write a 6–10 line memo addressed to the fictional author. Structure:

- One-sentence verdict (ship / revise / rewrite). This one is a rewrite.
- Three-bullet summary of the most load-bearing gaps (one each from fields 1–4, fields 5–7, and voice).
- One sentence on what the decision log will carry if this charter is rewritten (name the date and the owner so the log entry is draftable).
- One sentence pointing to Chapter 3's seven-field spec and the four-question adoption-mode check as the calibration.

## Expected output

A single file, roughly one and a half pages, containing:

1. The grading memo at the top (6–10 lines).
2. Field-by-field grading notes under headings Field 1 through Field 7.
3. A grading block under heading **Adoption mode** (four questions).
4. A grading block under heading **Voice** (marketing / hedging / undated-or-un-owned).
5. A rewritten **Kill criteria** section that meets the Chapter 3 bar.
6. A rewritten **Adoption mode** section with the four-question check visible and a trigger-to-revisit.

A reasonable final document is one to two pages. If yours is much longer, you are over-grading or re-writing more of the charter than this lab asks for; if much shorter, you are probably missing a field.

## Checkpoint

Before moving on to Exercise 02 (where you draft **your own** pilot charters for your real quarter's sequence), you should be able to answer **yes** to all four:

- Did you flag all seven charter fields as present / partial / missing, and did you catch at least six failures across the seven fields?
- Did you correctly identify the "mandate" as a manager-origin mandate that Chapter 3 says you will likely have to walk back, and did your rewrite step the mode down to opt-in during pilot?
- Does your rewritten kill-criteria section contain at least one *operational* (non-numeric) trigger — reviewer-burnout or incident-shaped — in addition to any numeric triggers?
- Does your rewritten adoption-mode section carry a trigger-to-revisit in the Chapter 6 shape (threshold + condition + duration)?

If any answer is no, re-read Chapter 3's "The pilot charter — what a pilot must have before it starts" and "Choosing between the three" sections, and Chapter 6's "The failure modes to notice in yourself," before drafting your own charters in Exercise 02.
