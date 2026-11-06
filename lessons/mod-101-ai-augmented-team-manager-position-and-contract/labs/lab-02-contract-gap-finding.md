# Lab 02 — Contract Gap-Finding on a Broken Sample

**Duration:** 60 minutes.
**Chapters exercised:** Chapter 3 (the four parties, the five commitments C1–C5).
**Complements, does not duplicate:** Exercise 03 asks you to draft **your own** team's human/machine contract from a blank page. This lab gives you a deliberately broken sample contract and asks you to grade it against the Chapter 3 framework. Doing this first sharpens your eye for what "finished" looks like before you draft yours.

## Objective

Read a sample human/machine contract that has several deliberate gaps and weaknesses. Identify every gap against C1–C5 and the four-party model. Rewrite one section — the accountability stack — to meet the Chapter 3 bar. Produce a short grading memo that could be handed to the (fictional) author.

## Prerequisites

- Chapter 3 read (four parties: AI, IC, reviewer, vendor; five commitments C1–C5; the "workable contract on the page" headings list; the terse sample at the end of the chapter).
- A blank file for your grading memo and the rewritten section.

## Steps

### Step 1 — Read the sample contract (5 min)

Below is "Payments Platform Team: AI Working Agreement v0.1." Read it once end-to-end before doing anything else. Do not take notes on this pass.

```
PAYMENTS PLATFORM TEAM — AI WORKING AGREEMENT v0.1

We believe in "AI generates, humans own." This document captures how our team
works with AI tools.

What AI does for us:
- Drafts code.
- Drafts tests.
- Drafts documentation.
- Drafts status updates.
- Helps with on-call.
- Writes PR descriptions.
- Explains legacy code.

What humans do:
- Review the output.
- Ship the code.
- Own the results.

If the AI is wrong:
- We fix it.

Tools:
- We use Cursor and ChatGPT.

Signed: the team.
```

### Step 2 — Grade against C1 (8 min)

Chapter 3 says C1 asks "what work may the AI draft?" and that the artifact-class answer must mark each class as **allowed / allowed-with-review-only / not allowed**. The default is not "anything that fits in a prompt box."

Open your grading file. Under heading **C1**, write:

- Which artifact classes are listed? Which are missing (compare against Chapter 3's examples most teams restrict: employee feedback, compensation decisions, promotion packets, incident post-mortems, security incident writeups)?
- For each class that *is* listed, does the sample mark it allowed / review-only / not-allowed? What is the default posture here?
- Are there contested classes that should be flagged with a note?

Expect to find: no class-level discrimination (everything is lumped into "drafts"), no explicit "not allowed" list, no review-only tier, no notes on contested classes.

### Step 3 — Grade against C2 (8 min)

Chapter 3's C2 asks "what must the human do before the artifact ships?" with four minimum verifications: read every line, run/execute/replicate, check claims against sources, judge fit to context. Plus a stated **review budget**.

Under heading **C2**, write:

- Which of the four verifications does "review the output" cover?
- Is there a review budget anywhere?
- Which artifact class in this sample encodes a judgment call too large for its stated review?

Expect to find: "review the output" collapses all four verifications into one unenforceable phrase; no budget; on-call runbook edits and PR descriptions sit side-by-side with no differentiation.

### Step 4 — Grade against C3 (8 min)

Chapter 3's C3 accountability stack names four parties (AI, IC, reviewer, vendor) and ranks three of them explicitly: IC accountable for shipping, reviewer accountable for approving, manager accountable for the system, vendor accountable per SLA. "The model" is not a valid accountability slot.

Under heading **C3**, write:

- How many of the four parties are named in the sample?
- Does "humans do: review the output / ship the code / own the results" survive the Chapter 3 test that no line can dodge accountability onto the model?
- Where is the manager layer? Where is the vendor layer?

Expect to find: no named reviewer layer, no manager layer, no vendor layer — only a single "humans" bucket, which is the exact dodge Chapter 3 names.

### Step 5 — Grade against C4 (5 min)

Chapter 3's C4 asks "what do we do when the AI is wrong?" with four minimum bullets: report, pull back / correct, preserve the trace (prompt + model version + tool connections + retrieved context), feed back into C1/C2. Blameless post-mortem language is the target.

Under heading **C4**, write:

- Which of the four C4 bullets are present?
- Does "we fix it" meet the Chapter 3 bar?
- Where would the trace be preserved on this team today?

### Step 6 — Grade against C5 (5 min)

Chapter 3's C5 asks "what may the AI see, and what may it keep?" with four minimum items: data classifications, approved tool at approved tier, retention / training-opt-out posture with link to the DPA, secrets / keys / PII rules.

Under heading **C5**, write:

- Which of the four C5 items are present?
- Does "we use Cursor and ChatGPT" cover enterprise-tier approval, retention posture, or PII rules?
- Spot the ambiguity on ChatGPT — personal account vs. enterprise SSO is the exact gap Chapter 3's sample closes.

### Step 7 — Structure check (3 min)

Chapter 3 lists seven required headings for a workable contract: Scope · C1 · C2 · C3 · C4 · C5 · Change log.

Under heading **Structure**, write a single line per missing heading. Expect to find: no scope statement (team name, what we do, time horizon), no change log (not optional per Chapter 3).

### Step 8 — Rewrite the C3 section to meet the bar (12 min)

Copy the sample's "What humans do / If the AI is wrong" region into a new section called **C3 — Accountability stack, rewritten**. Replace it with a four-line stack that:

- Names IC submitter, reviewer, manager, vendor each in one sentence.
- Blocks the "the model did it" dodge at each layer.
- Puts the manager on the hook for the system (standard, enablement, reviewer bandwidth, class-of-work decision).
- States what the vendor is and is not accountable for.

Use Chapter 3's terse sample ("IC submits → reviewer approves → manager owns the standard → vendor to SLA") as calibration, not a template to copy verbatim — write it in the payments-platform voice.

### Step 9 — Write the grading memo (6 min)

At the top of your file, write a 6–10 line memo addressed to the fictional author. Structure:

- One-sentence verdict (ship / revise / rewrite).
- Three-bullet summary of the most load-bearing gaps.
- One sentence on what the change log would have caught had it existed.
- One sentence pointing to Chapter 3's sample as calibration (not as a template to copy).

## Expected output

A single file containing:

1. The grading memo at the top (6–10 lines).
2. Section-by-section gap notes under headings C1, C2, C3, C4, C5, Structure.
3. A rewritten C3 section that would pass the Chapter 3 bar.

A reasonable final document is one to two pages. If yours is much longer, you are over-grading; if much shorter, you are probably missing a C-section.

## Checkpoint

Before moving on to Exercise 03 (where you draft **your own** contract from scratch), you should be able to answer **yes** to all three:

- Did you flag all four parties (AI, IC, reviewer, vendor) as absent or collapsed in the sample's "humans do" section?
- Did your rewritten C3 put the manager on the hook for the system (not just for "reviewing output")?
- Can you name, from memory, the seven required headings of a workable contract?

If any answer is no, re-read Chapter 3's "four parties," "five commitments," and "workable contract on the page" sections before starting Exercise 03.
