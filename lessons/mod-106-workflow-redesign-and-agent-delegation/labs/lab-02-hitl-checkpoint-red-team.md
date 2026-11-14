# Lab 02 — HITL Checkpoint Red-Team on a Broken Sample

**Duration:** 60 minutes.
**Chapters exercised:** Chapter 4 (the four kinds of HITL; the five-field specification; the four named failure modes; the three edge cases), with a side-check against Chapter 3 (the ladder-level ↔ HITL-kind mapping) and Chapter 6 (Band 3 ↔ Kind 1 at the tool-call layer).
**Complements, does not duplicate:** Exercise 04 asks you to design HITL checkpoints for three real workflows on *your own* team. This lab gives you a fixed, deliberately broken sample checkpoint set so you can rehearse the red-team reading — spotting missing fields, misused kinds, drifted scopes — against a known answer key before trusting the move on your own team's drafts.

## Objective

Read four deliberately broken HITL checkpoint specs for a fictional team. For each: (a) name which of the five fields (trigger, reviewer role, checklist, decision surface, SLA) are missing or thin; (b) name which of the four named failure modes it exhibits (yes-to-all, missing mid-run gate, rubber-stamp, ghost audit) or which edge-case consideration it ignores; (c) rewrite the spec into a fully-specified version. Then compare against the answer key. The target is **at least one defect caught on every checkpoint and a rewritten spec that passes all five-field checks**.

## Prerequisites

- Chapter 4 read (four kinds, five fields, four failure modes, three edge cases).
- Chapter 3 skimmed (so you can read the ladder-level / HITL-kind mapping table).
- Chapter 6 skimmed (so you can recognise where Band 3 forces Kind 1 at the tool-call layer).
- Optional: `mod-103` review-standard read-through so you know what a real checklist looks like.
- A blank text file for your diagnoses and rewrites.

## The fictional team

> **"Billing" team, FerryWave SaaS.** 11 engineers (2 senior, 9 mid/junior). Owns billing, invoicing, and the payment-webhook pipeline. Two agents in day-to-day use: *Reviewer* (an internal Claude Code agent that drafts code-review comments on PRs) and *Postmaster* (an agent that drafts outbound customer billing emails from templates + invoice data). The team has an AGENTS.md and a v0.2 tool-authorisation policy that classifies `email.send_customer` as Band 3 and `github.merge_pr` as Band 3; all other tools in use are Band 1 or Band 2. The team runs ~40 agent-touching outputs per day in normal conditions; on the first of the month ("invoice day"), that spikes to ~300.

Each of the four checkpoint specs below is drawn from this team's live workflow documentation. Each is thin, broken, or drifted in a specific way.

## Steps

### Step 1 — Set up your scratch file (3 min)

Create a working file `lab-02-hitl.md`. Add this header:

```
# Lab 02 — HITL red-team scratch (Billing team, FerryWave)

Five fields a checkpoint must specify (Chapter 4):
  1. Trigger
  2. Reviewer role (not person; rotation/backup named)
  3. What the reviewer checks (checklist; mod-103 pointer)
  4. Decision surface (accept / reject / edit-and-accept / escalate)
  5. SLA (duration + timeout behaviour)

Four named failure modes (Chapter 4):
  A. Yes-to-all pre-invocation approval  (Kind 1 scoped too broadly)
  B. Missing mid-run gate                (Kind 2 absent at a judgment boundary)
  C. Rubber-stamp post-generation review (Kind 3 without checklist / rotation)
  D. Ghost periodic audit                (Kind 4 without a written finding)

Three edge cases (Chapter 4):
  I.   Latency-critical workflows (move Kind 1/2 out of hot path)
  II.  Bursty workflows (name burst-mode downgrade explicitly)
  III. Agent-to-agent workflows (consuming agent is not a reviewer)
```

### Step 2 — Red-team the four checkpoints (30–40 min)

Below are four broken specs. For each: **start the timer**, write (a) which of the five fields are missing or thin; (b) which failure mode or edge-case consideration it exhibits; (c) a rewritten spec with all five fields populated and the Chapter 3 consistency check noted (does the kind match the ladder level?); (d) time elapsed. Target **no more than 7 minutes per spec**.

Do not scroll to the answer key until all four are done.

#### Checkpoint A — Reviewer agent on single-file bug-fix PR reviews

> *"When Reviewer finishes drafting a PR review comment, the PR author reads it before using it. HITL: yes."*

Context: the delegation ladder entry for this workflow is **Level 3** (draft-and-present with aggregate audit replacing per-instance approval); the mod-103 review standard has a dedicated §Code-review checklist.

#### Checkpoint B — Postmaster agent on outbound customer billing emails

> *"Before Postmaster sends a customer billing email, a human must approve. Trigger: any outbound email. Reviewer: whoever is on duty in the billing-ops Slack channel. Decision: approve or reject. On invoice day we skip approval for bulk sends because the queue would back up."*

Context: the delegation ladder entry for this workflow is **Level 4** (bounded co-decision); `email.send_customer` is Band 3 on the tool-authorisation policy; the team sends ~300 emails on invoice day vs. ~5–10 per day the rest of the month.

#### Checkpoint C — Postmaster agent on outbound customer billing emails (continued: the audit)

> *"We do a monthly audit of all customer emails Postmaster sent in the previous month. The audit covers whether the emails were appropriate and whether anything went wrong. The audit is done in the monthly billing team sync."*

Context: no written audit artifact exists from the last two monthly syncs. The sync agenda shows "Postmaster audit" as a 10-minute topic.

#### Checkpoint D — Reviewer agent on multi-file refactor PR reviews

> *"When Reviewer is going to draft a review comment on a multi-file refactor PR, it does so autonomously and files the comment. The PR author reads the comment as part of normal PR review. If the author disagrees they say so in the thread."*

Context: the delegation ladder entry for this workflow is **Level 2** (draft-and-present, approval required). The staff engineer noticed last week that Reviewer had filed an "LGTM"-style comment on a refactor that touched five service boundaries; the staff engineer disagreed with the LGTM but didn't realise until two days later.

### Step 3 — Compare against the answer key (10 min)

For each checkpoint, compare your diagnosis to the key below. A diagnosis counts as a match if (a) you caught the primary failure mode / edge-case misuse and (b) your rewritten spec populates all five fields with a coherent set of choices.

#### Answer key

**Checkpoint A — Reviewer on single-file bug-fix PR reviews.**

- **Fields missing or thin.** Trigger is implicit (acceptable, but should name the event precisely — "when Reviewer finishes a draft comment on a single-file bug-fix PR"). Reviewer role is named ("PR author") — this is fine. *Checklist is missing* — "reads it" is a gut-check, not a checklist. Decision surface is missing entirely. SLA is missing entirely.
- **Failure mode.** **Failure C — rubber-stamp post-generation review.** No checklist means the PR author will "approve" the comment by not pushing back, and the Kind 4 audit cadence on their track record is not named either.
- **Rewritten spec.**

    ```
    Kind: 3 (post-generation review) + Kind 4 (monthly sample-audit)
    Trigger: when Reviewer finishes a drafted PR-review comment on a single-file bug-fix PR
    Reviewer role: PR author of record (not the agent; not the on-call reviewer).
                   Rotation covers vacation (backup = any senior on the team).
    Checklist: mod-103 §Code-review checklist — five items:
               (1) is the regression test covering the stated bug;
               (2) does the review comment reference the right line/function;
               (3) does the review comment surface a correctness issue the author missed;
               (4) does the comment flag anything outside the stated bug scope;
               (5) is the tone consistent with the team's review standard.
    Decision surface: accept / reject / edit-and-accept / escalate-to-senior.
                      (Not "approve or reject" alone — most real reviews are edit-and-accept.)
    SLA: review completes within 24h of the PR being opened; on timeout the agent-authored
         comment is auto-collapsed and the senior on-call reviewer is paged.
    Kind 4 audit: quarterly sample of 10 past PRs this reviewer approved; staff engineer
                  re-reads against the checklist; one-page written finding filed in
                  docs/mod-106-audit/.
    Ladder consistency: ladder says Level 3 → minimum Kind 3 required with Kind 4 overlay.
                        Rewritten spec matches.
    ```

**Checkpoint B — Postmaster on outbound billing emails.**

- **Fields missing or thin.** Trigger OK ("any outbound email"). Reviewer role is a person-pattern ("whoever is on duty in the billing-ops Slack channel") — ambiguous; no rotation; no backup. Checklist is missing entirely. Decision surface drops edit-and-accept. SLA is missing.
- **Primary problems.** **Failure A — yes-to-all pre-invocation approval** (on the non-invoice-day cadence of 5–10 emails/day, a "approve or reject" prompt with no checklist and no SLA trains the reviewer to accept). **Edge case II — bursty workflow** is being handled badly: the "we skip approval for bulk sends" clause is an *undocumented burst-mode downgrade* that silently drops Kind 1 at the exact moment the volume (and the blast radius) is highest. Chapter 4 says the burst-mode downgrade must be an explicit design, not an accident — and even in burst mode, Kind 4 sampling should keep a human on some fraction.
- **Rewritten spec.**

    ```
    Kind: 1 (pre-invocation approval, per-call) — Band 3 enforcement
          + Kind 4 (sampled audit in burst mode)
    Trigger: any call to the Band-3 tool email.send_customer
    Reviewer role: billing-ops shift reviewer (named rotation; backup = team manager;
                   on-call reviewer takes over after 20:00).
    Checklist: 4-item pre-send check — (1) does the customer match the invoice;
               (2) is the amount within the expected range for this customer;
               (3) does the body reference the right billing period;
               (4) are there any open support tickets with this customer that should block.
               (Pointer: docs/mod-106/email-review-checklist.md.)
    Decision surface: approve / reject / edit-and-send / escalate-to-manager.
    SLA (normal volume): 5 minutes; on timeout, the agent aborts the send and files
                         a note in docs/mod-109-nearmiss/.
    Burst-mode design (invoice day, defined as volume > 50/hour):
                         downgrade to sampled Kind 1 at 20% rate + full Kind 4 at end of day.
                         Manager is paged on invoice day to confirm burst-mode entered.
                         Burst-mode is ENTERED EXPLICITLY, not as a silent skip.
    Ladder consistency: ladder says Level 4 (bounded co-decision) → minimum Kind 2 at the
                        decision point; Kind 1 at the Band-3 tool-call site is additionally
                        required by Chapter 6 regardless of level. Rewritten spec matches.
    ```

**Checkpoint C — Monthly audit on Postmaster output.**

- **Fields missing or thin.** Trigger is present ("monthly"). Reviewer role is thin ("done in the monthly billing team sync" is a time-slot, not a role). Checklist missing. Decision surface undefined — what does "the audit" output if a problem is found? SLA is undefined (a 10-minute slot in a sync is not an audit).
- **Failure mode.** **Failure D — ghost periodic audit.** No written finding has come out of the last two audits; the audit is theatre. The load-bearing property is the *writing-down-of-findings*.
- **Rewritten spec.**

    ```
    Kind: 4 (periodic audit)
    Trigger: first Monday of each month at 10:00 (not "in the monthly sync").
    Reviewer role: rotating senior engineer on the team (named on the ladder review);
                   manager is backup; sync meeting is not the review venue.
    What they check: pull 20 random emails Postmaster sent in the previous month;
                     re-read each against the checklist in Checkpoint B;
                     flag any that would have been rejected on Kind 1 review but
                     passed through; cross-check invoice-day sampled Kind 4 output
                     against the burst-mode design.
    Decision surface: file a dated one-page finding in docs/mod-106-audit/.
                      "No issues this cycle" is a valid finding; absence of the file
                      is a defect in the next ladder review.
                      If >=2 would-have-rejected cases: demote delegation level
                      next ladder review; file a near-miss in docs/mod-109-nearmiss/.
    SLA: audit written-finding filed within 5 business days of audit date;
         missed audit = blocking defect at the quarterly ladder review.
    ```

**Checkpoint D — Reviewer on multi-file refactor PR reviews.**

- **Fields missing or thin.** Trigger is a workflow-step, acceptable. Reviewer role is "the PR author" implicitly — but the problem is that the comment *is already filed* by the time the author reads it, which means the "approval" is post-filing and the agent has effectively acted. No checklist, no SLA.
- **Failure mode + ladder mismatch.** **Primary diagnosis: ladder/checkpoint mismatch.** The ladder entry says Level 2 (draft-and-present, approval required) — which requires **Kind 3 on every instance** (minimum). The checkpoint describes the agent *filing* the comment directly, which is behaviour consistent with Level 5 (act with advisory review), not Level 2. This is the exact drift Chapter 3 warns about: the ladder says one thing, the HITL spec says another. Also **Failure C** (no checklist; Kind 3 that is nominally present would be rubber-stamp in practice).
- **Rewritten spec.**

    ```
    Kind: 3 (post-generation review, every instance, BEFORE comment is filed)
          + Kind 4 (quarterly audit)
    Trigger: when Reviewer finishes drafting a review comment on a multi-file
             (>=2 non-test files) refactor PR
    Reviewer role: senior engineer or staff engineer — not the PR author,
                   because multi-file refactor review is itself the task the
                   senior should be doing; junior reviewer is not acceptable here.
                   Rotation across the two seniors + staff.
    Checklist: mod-103 §Multi-file refactor review checklist (separate from §Code-review):
               (1) are all changed files consistent with the stated refactor goal;
               (2) are any service boundaries changed, and was the change intentional;
               (3) is there a correctness issue the agent missed;
               (4) is the "LGTM"-shaped shortcut avoided — explicit per-file comment.
    Decision surface: accept / reject / edit-and-accept / escalate-to-staff.
    SLA: review completes within 48h of draft; on timeout the agent-authored draft
         is held, not filed; senior reviewer is paged after 48h.
    Kind 4 audit: quarterly, 5 random multi-file refactor PRs; staff engineer re-reads
                  including the agent's draft vs. what the senior filed; one-page finding.
    Ladder consistency: the ladder says Level 2; Chapter 3 requires Kind 3 on every
                        instance at Level 2. The CURRENT spec silently operates at Level 5
                        behaviour with a Level-2 label; that is the near-miss the staff
                        engineer spotted. Options: either rewrite the spec to real Level 2
                        (above), OR demote the ladder entry to Level 1 (shadow mode) while
                        the review standard is firmed up.
    ```

### Step 4 — Diagnose misses (10 min)

For every checkpoint where you missed the primary failure mode or produced a rewrite that still has <5 fields populated, write one paragraph:

- Which of the five fields did you under-specify? Was the under-specification because the field was "obvious" (and therefore implicit — Chapter 4's point is that implicit fields degrade in six months) or because the spec hadn't considered it?
- Did you spot the Chapter 3 **ladder-level / HITL-kind consistency** issue on Checkpoint D? If not, re-read Chapter 3's mapping table.
- Did you spot the **burst-mode drift** on Checkpoint B and classify it as an edge-case misuse rather than a reasonable operational shortcut? Chapter 4 is explicit: *burst-mode downgrade is a design, not an accident.*
- Did you resist the temptation to over-engineer? A rewritten spec with eight sub-cases on the decision surface and three different SLAs is as broken as one with none. The five fields should be each **one clear line**.

### Step 5 — Reconcile against Chapter 6 (5 min)

For Checkpoints B and D, verify your rewrite is consistent with the Chapter 6 tool-authorisation policy:

- Does Checkpoint B's Kind 1 fire at the exact tool-call site `email.send_customer` (Band 3)? Chapter 6 says Band 3 enforcement is at the **tool-call layer**, not the prompt layer, specifically so a prompt-injected agent cannot bypass the human approval.
- If Checkpoint D's workflow reached any Band 3 tool call (it doesn't — a PR-review *comment* is Band 2 at most), would your rewrite catch it with an additional Kind 1 trigger? Note the implied answer; this is the kind of cross-check Exercise 03 formalises.

If the answer is no on either, your rewrite would let an irrevocable tool call through without an enforceable gate — that is a Band-3-bypass defect and is incident-grade (Chapter 6).

## Expected output

A scratch file, roughly two pages, containing:

- Four red-team diagnoses (missing fields, failure mode, edge-case consideration).
- Four fully-specified rewritten checkpoints, each with the five fields and a ladder-consistency note.
- A diagnostic paragraph per primary-miss.
- A two-line Chapter 6 reconciliation on Checkpoints B and D.

Something like:

```
Checkpoint A — Reviewer on single-file bug-fix PR reviews
  Missing: checklist, decision surface, SLA; Kind 4 overlay absent.
  Failure: C (rubber-stamp Kind 3).
  Rewrite: [...5-field spec with mod-103 checklist pointer, edit-and-accept, 24h SLA...]
  Ladder consistency: Level 3 → Kind 3 + Kind 4 required. Match.
  ✅ caught primary failure.

Checkpoint B — Postmaster on outbound billing emails
  Missing: checklist, edit-and-accept decision, SLA.
  Failure: A + edge-case II (bursty, silent downgrade).
  Rewrite: [...explicit burst-mode design, sampled Kind 1 + full Kind 4 at EOD...]
  Chapter 6: Kind 1 fires at email.send_customer (Band 3) — tool-call layer, not prompt.
  ✅ caught burst-mode drift.
```

## Checkpoint

Before moving on to Exercise 04 (where you design HITL checkpoints for *your team's* three real workflows), you should be able to answer **yes** to all five:

- Did you catch the primary failure mode on all four checkpoints?
- Did each of your four rewrites populate all five fields with concrete one-line choices?
- Did you spot the **ladder/HITL mismatch** on Checkpoint D (the drift between Level 2 on paper and Level 5 behaviour in practice)?
- Did you spot the **silent burst-mode downgrade** on Checkpoint B and rewrite it as an explicit, paged, sampled-Kind-1 design?
- Does your Checkpoint B rewrite fire Kind 1 at the tool-call layer (not the prompt layer) on the Band-3 `email.send_customer` call?

If any answer is no, re-read Chapter 4's "What a checkpoint actually specifies" and "The most common HITL design failures," then re-attempt the misses before running Exercise 04 on your real workflows.
