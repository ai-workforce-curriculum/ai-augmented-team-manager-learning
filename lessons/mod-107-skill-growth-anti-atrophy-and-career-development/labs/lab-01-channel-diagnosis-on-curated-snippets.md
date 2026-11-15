# Lab 01 — Channel Diagnosis on Curated 1:1 and Retro Snippets

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 1 (the three channels of atrophy, the lagged-signal argument), Chapter 2 (Brynjolfsson, Li, Raymond's growth-path channel), Chapter 3 (Noy & Zhang's differentiation channel), Chapter 4 (Dell'Acqua et al.'s deference channel and the uncritical consumer pattern), with side-checks against Chapter 5 (the three carve-outs — paired-review rotation, periodic AI-off artifact, judgment-weighted review pass) and Chapter 7 (1:1/retro as diagnostic instrument; Westrum typology on retros).
**Complements, does not duplicate:** Exercise 01 asks you to author the research-to-policy memo for **your own** team, and Exercise 02 asks you to build the quarterly carve-out schedule for **your own** team. This lab hands you a fixed, deliberately mixed-signal set of 1:1 and retro snippets from a fictional team — so you can calibrate your reading of *which channel is firing* and *which carve-out responds* before you spend real authoring hours on your team.

## Objective

Read a curated sample of five snippets from a fictional team's weekly 1:1s and quarterly retro: four from individual engineers' 1:1 conversations and one retro excerpt. For each snippet, (a) identify which of the three channels (growth-path / differentiation / deference) is most active, (b) name the specific Chapter 5 carve-out that would most directly respond, (c) classify any Westrum signs the retro snippet carries. Then compare against the answer key. Target: **at least four of five correct channel calls with the correct carve-out mapping**, and a Westrum classification that matches the key's reasoning on the retro excerpt.

## Prerequisites

- Chapter 1 read (the three channels, the lagged-signal argument).
- Chapter 2 read (Brynjolfsson's distributional pattern and workforce-dynamics channel; the failure sequence flagged for Chapter 5).
- Chapter 3 read (Noy & Zhang's dispersion compression; what the finding does *not* say).
- Chapter 4 read (Dell'Acqua's uncritical consumer pattern; the hard case of the IC who sincerely endorses the AI's output).
- Chapter 5 skimmed (the three carve-outs; the "common failure modes" list).
- Chapter 7 skimmed (the four categories of prompts; the Westrum typology; what makes the prompts work).
- A blank file for your diagnosis.
- A timer.

## The fictional context

> **"Catalog Platform" team, Linden Supply.** 9 engineers (1 staff, 3 senior, 5 mid/junior). Owns the catalog service, the pricing adapter, and the search indexer used by three product teams. Agents in use: Cursor Business (9 seats, rolled out Q2) and Claude Code via team gateway (usage-based, rolled out Q3). mod-106 routing matrix exists in v0.2 and lists **three outside-frontier task-types**: *"schema migrations on the pricing adapter under uncertain consumer-traffic patterns"*, *"incident-narrative authoring for upstream-vendor-flavoured incidents"*, and *"architecture-direction memos for the search-indexer re-platform."* The team runs weekly 1:1s and a per-sprint retro. The snippets below are five excerpts from the last four weeks — four 1:1 moments and one retro moment — that the manager jotted down to review.

Score each snippet against this team, not an idealised team. The routing matrix, the review bandwidth, and the junior ICs' growth arcs matter.

## Steps

### Step 1 — Set up your working file (3 min)

Create a working file `lab-01-channel-diagnosis.md`. Add this header:

```
# Lab 01 — Channel diagnosis (Catalog Platform, Linden Supply)

Three channels (Chapters 2, 3, 4):
  G  Growth-path channel      — Brynjolfsson, Li, Raymond (NBER WP 31161)
                                Gains concentrate at low tenure; junior ICs
                                grow through a different curve; mistakes the
                                reviewer used to catch are absorbed by the
                                model before the artifact ships.
  D  Differentiation channel  — Noy & Zhang (Science 2023)
                                Output-quality dispersion compresses; bottom
                                quartile benefits more than top; promotion
                                signal based on output volume stops
                                differentiating.
  F  Deference channel        — Dell'Acqua et al. (HBS WP 24-013)
                                Uncritical-consumer pattern; on outside-
                                frontier tasks, AI-augmented workers defer
                                and ship plausibly-wrong answers. Centaur /
                                cyborg vs. uncritical consumer.

Three carve-outs (Chapter 5):
  C1  Paired-review rotation (one senior + one junior) on outside-frontier
      task-types; the senior models judgment, the junior forces articulation
  C2  Periodic AI-off artifact — pre-chosen, 2–4 hours, low-stakes;
      review is for the comparison, not the output
  C3  Judgment-weighted review pass — reviewer asks "if you were writing
      this from scratch, would you have made the decisions this artifact
      makes?" BEFORE looking at the diff; ~90s, on outside-frontier
      task-types, scheduled not on every review

Westrum typology on retros (Chapter 7):
  Gen  Generative — specific named AI-wrong cases; discussion without
       blaming the IC; routing matrix or review standard amended by
       end of retro; next retro references back
  Bur  Bureaucratic — AI-wrong cases named in categories without
       specifics; generic action item; next retro doesn't reference
  Pat  Pathological — AI-wrong cases not mentioned or reassigned to
       blame the IC who shipped; the pattern is present and silent

For each snippet record: (a) channel letter G/D/F, (b) carve-out C1/C2/C3
(one primary; a second may be partial credit), (c) one-sentence why,
(d) manager-side action.
```

### Step 2 — Read and diagnose Snippet A (8–10 min)

#### Snippet A — Monday 1:1 with junior engineer J.R. (18 months tenure)

> **Manager:** *"Walk me through a time this week you accepted an AI suggestion without changing it."*
>
> **J.R.:** *"The two feature-flag refactors from Tuesday — Cursor extracted the duplicated condition into a helper, wrote the matching tests, and the diff looked right. S.K. approved both PRs the same morning. I didn't need to change anything."*
>
> **Manager:** *"And a time you rejected or modified a suggestion?"*
>
> **J.R.:** *(pauses, then thinks)* *"... I don't think so, this week. I've been mostly on the feature-flag work; it's all pretty mechanical."*
>
> **Manager:** *"Over the last month, can you name one?"*
>
> **J.R.:** *(longer pause)* *"Honestly — no. I can't name one. I guess I've been lucky with what the tool's been suggesting."*

For Snippet A, write a 3–4-line diagnosis: channel, carve-out, one-sentence why, manager-side action.

### Step 3 — Read and diagnose Snippet B (8–10 min)

#### Snippet B — Thursday 1:1 with senior engineer S.K. (7 years tenure)

> **S.K.:** *"My throughput is going to look flat on the mid-year this year — you know this. Cursor and Claude are doing a lot of the drafting for the juniors, which is fine — the PRs are coming through faster. My own PR volume hasn't changed; the work I do that isn't shipping PRs has changed a lot, though. I pair-reviewed three outside-frontier PRs last sprint with J.R. and M.H. — the conversations are where I feel like I'm actually earning my salary, and J.R.'s second incident-narrative draft last week was visibly better than the first one. But I don't know how you write that down in a performance narrative. The dashboards are going to show me shipping less and the juniors shipping more, and the shape of the gap I'm closing for them isn't on any chart."*

For Snippet B, write a 3–4-line diagnosis: channel, carve-out (or ladder axis per Chapter 6), one-sentence why, manager-side action.

### Step 4 — Read and diagnose Snippet C (8–10 min)

#### Snippet C — Tuesday 1:1 with mid-level engineer M.H. (3 years tenure)

> **M.H.:** *"The pricing-adapter schema migration from last sprint — the one that paged on Saturday — I've been thinking about it. Claude suggested adding the new column with a default value and backfilling asynchronously. I read the suggestion, the reasoning sounded good, I ran the migration in staging, it worked, I shipped it. On production it collided with the Saturday vendor-traffic window — the backfill query was holding a lock the vendor's read path doesn't tolerate. If I'd actually sat and thought about the traffic pattern for this adapter — which I know, I've worked on it for a year — I would have scheduled the backfill overnight, or used a different column strategy entirely. I had the mental model; I just didn't engage it. The model's suggestion was plausible enough that I didn't pause."*
>
> **Manager:** *"At review time, did anyone ask what you'd have done from scratch?"*
>
> **M.H.:** *"No. The diff looked clean. S.K. approved it without flagging anything."*

For Snippet C, write a 4–5-line diagnosis: channel, carve-out(s), one-sentence why, manager-side action — this one is the fullest case in the lab.

### Step 5 — Read and diagnose Snippet D (6–8 min)

#### Snippet D — Wednesday 1:1 with new-grad engineer N.V. (4 months tenure)

> **N.V.:** *"Honestly the ramp has been great. I've shipped six PRs in four months — my rotation-mates at other companies tell me that's a lot for someone this early. Cursor is doing a lot of the grunt work; I spend most of my time understanding the codebase and reviewing what it proposes. I feel productive. The one thing that's a little weird is — I haven't really had the 'oh god I don't understand why this is wrong' moment that senior engineers at my last internship said was the real learning moment. Everything just... works. Is that normal? Should I be worried?"*

For Snippet D, write a 3–4-line diagnosis: channel, carve-out, one-sentence why, manager-side action. Note specifically what the manager does *not* do in response to a question phrased this honestly.

### Step 6 — Read and diagnose Snippet E, the retro excerpt (8–10 min)

#### Snippet E — Q-end retro, the "what went poorly" segment

> **Facilitator:** *"What went poorly this quarter?"*
>
> **M.H.:** *"The Saturday incident on the pricing adapter — we talked about that in the postmortem. I've added 'think about the traffic pattern before shipping schema migrations' to my personal notes."*
>
> **R.P. (junior):** *"We had a couple of AI-review things slip through on the smaller PRs — nothing bad, just a couple of 'oh that could have been caught' moments."*
>
> **Facilitator:** *"OK. Action items from that?"*
>
> **S.K.:** *"I think we need to be more careful with what we're accepting from the tool."*
>
> **Facilitator:** *"Right, 'be more careful with AI suggestions' — I'll add that as an action item. Owner?"*
>
> **S.K.:** *"Everyone? I don't know. Let's say me, and I'll bring it back next retro."*
>
> *(no one revisits it at the next retro.)*

For Snippet E, write a 5–6-line diagnosis: channel(s) implicated, Westrum classification (Gen/Bur/Pat), the specific manager intervention Chapter 7 recommends when this classification is observed, and which Chapter 5 carve-out(s) would have surfaced the signal more sharply.

### Step 7 — Compare against the answer key (10 min)

Read the key below only after you have written all five diagnoses.

#### Answer key

**Snippet A — J.R. (18-month junior).** Channel: **G (growth-path)**. Carve-out: **C2 (periodic AI-off artifact)** primary; C1 (paired-review rotation) partial.

- Brynjolfsson, Li, Raymond's finding is that AI gains concentrate at lower tenure; the junior IC's skill-growth curve changes shape because mistakes they used to make, recover from, and learn from are now absorbed by the model before the artifact reaches a reviewer. J.R. cannot name *one* rejection or modification over a month — the manager's Category-1 prompt (Chapter 7) has surfaced the growth-path pattern. The *feature-flag refactors* on which J.R. is deferring are inside-frontier mechanical work where the deference may well be appropriate; the diagnosis is not "J.R. is an uncritical consumer on this task-shape" but "J.R.'s growth curve is not being shaped by the mechanical slice, and the module's judgement muscle will not form through this work."
- Carve-out response: **C2** — schedule J.R.'s next AI-off artifact around an outside-frontier task-type from the routing matrix (not a feature-flag refactor). The artifact creates the unassisted baseline J.R.'s growth curve requires. **C1** also applies as a partial — pairing J.R. with a senior on an outside-frontier task would expose J.R. to the judgement-vocabulary they are not developing on inside-frontier work. The Chapter 2 Day-30 check-in example and the Chapter 5 Carve-out 2 together are the specific response.
- Manager action: do **not** frame as a performance concern — Chapter 2 and Chapter 5 are explicit that Day-30 PR slippage shapes are *programme-design signals, not performance signals*. The junior IC is doing what the current workflow produces. Reshape the workflow (what J.R. is asked to work on, what carve-out is scheduled) before reshaping the IC's self-assessment.

**Snippet B — S.K. (7-year senior).** Channel: **D (differentiation)**. Carve-out: ladder axis, not a Chapter-5 carve-out primarily — this is a **Chapter 6 Axis B** (mentorship of judgement) case.

- Noy & Zhang's finding is that AI compresses measured output quality; the top-tier benefits least on raw output but their leverage has moved into judgement, review, and mentorship work that the AI does not do. S.K. names exactly this pattern: PR volume flat, pair-review conversations rising, a specific junior IC's narrative-draft quality visibly improving. The chapter calls this out as "the top-of-distribution ICs need a different growth narrative," and Chapter 6's Failure mode 2 (the senior IC who looks flat) is this case precisely.
- Response: a **Chapter 6 Axis B** ladder entry — the junior IC's growth is the evidence of the senior's leverage. S.K.'s mid-year narrative should name J.R.'s improved second incident-narrative draft (and the paired-review conversations that produced it) as the *senior-tier* artifact. In calibration, the manager's line is Chapter 3's response: *"compare on Axis A and Axis B, not on volume — volume compresses under AI, as Noy & Zhang (Science 2023) documents."* Chapter 5's paired-review rotation (**C1**) is the production mechanism S.K.'s leverage comes through — the rotation must be scheduled, not ad-hoc, or the senior's leverage will be invisible to the next quarter's calibration too.
- Manager action: author the Exercise 03 ladder amendment (if not yet in place) so S.K.'s narrative can point at it; make the paired-review rotation visible on the ritual calendar so the work is both legible and institutionalised.

**Snippet C — M.H. (3-year mid-level).** Channel: **F (deference)**. Carve-out: **C3 (judgment-weighted review pass)** primary; **C1 (paired-review rotation)** also indicated.

- This is Dell'Acqua et al.'s uncritical-consumer pattern in its clearest form, grounded in an outside-frontier task-type from the routing matrix (schema migrations on the pricing adapter under uncertain consumer-traffic patterns). M.H. has the mental model — "I've worked on it for a year" — and did not engage it; the model's suggestion was plausible enough that the judgement muscle did not activate. Chapter 4 names this: *"the sincere endorsement is evidence that review-the-AI's-output was applied, not that re-derive-the-decision-from-scratch was applied."* Here, S.K.'s review also missed it: *"the diff looked clean."*
- Carve-out response: **C3** is primary. The judgement-weighted review pass asks the question *before* the reviewer sees the diff — exactly the anchoring-prevention Chapter 4 calls for. Applied on outside-frontier task-types (including pricing-adapter migrations), it would have surfaced M.H.'s re-derivable mental model and the traffic-pattern concern before the diff anchored the review. **C1 (paired-review rotation)** also applies because the paired conversation is where the "what would you have done from scratch" discussion happens and where the junior-reviewer-plus-senior pairing surfaces the local context the model does not have.
- Manager action: add pricing-adapter schema migrations to the Chapter 5 carve-out schedule explicitly (if not already there), ensure the next migration gets a paired review + judgement-weighted pass, and — separately, blamelessly — connect the postmortem signal to the next quarter's carve-out scope (Chapter 5 + Chapter 7's retro-prompt Category 4). Do **not** treat the incident as an individual-performance problem; Chapter 4 and Chapter 9's blameless frame both apply.

**Snippet D — N.V. (4-month new grad).** Channel: **G (growth-path)**. Carve-out: **C2 (AI-off artifact)** primary.

- Brynjolfsson, Li, Raymond's growth-path channel in its most important form: a junior IC whose growth curve is *structurally* different from what prior cohorts experienced. N.V.'s question — *"should I be worried?"* — is diagnostically rich: the IC has an internal model that something is off (the absence of the "oh god" moment prior seniors described), and does not have the vocabulary to name it. The chapter's failure sequence (Chapter 2, "The failure mode this chapter flags for Chapter 5"): IC ships good AI-assisted output → internal mental model does not form → outside-frontier failure arrives 9–18 months later. The manager cannot wait; the intervention is now.
- Carve-out response: **C2** — schedule N.V.'s first AI-off artifact in the coming quarter on a scoped (2–4 hour) low-stakes task that represents the IC's level, specifically chosen to re-introduce the "I had to build the mental model" experience. Review is for the comparison, not the output. The Chapter 2 Day-30 check-in pattern is the natural framing.
- Manager action: answer N.V.'s question honestly. *"That's the right thing to notice. The onboarding you're going through is structurally different from what seniors at your last internship had — here's what we're doing about it, here's the carve-out you're on for this quarter, here's why."* The question itself is a psychological-safety signal to protect (Chapter 7, Edmondson): a new-grad honest enough to ask is exactly the IC the team's growth plan has to be worthy of.

**Snippet E — Q-end retro.** Channels implicated: **F (deference)** on M.H.'s incident; **G (growth-path)** on R.P.'s "AI-review slips." Westrum classification: **Bur (bureaucratic)**, drifting toward **Pat (pathological)**.

- Bureaucratic signs per Chapter 7: AI-wrong cases named in categories without specifics ("a couple of AI-review things slip through on the smaller PRs — nothing bad"); generic action item ("be more careful with AI suggestions"); the next retro does not reference back. The pathological drift is visible in the ownership shrug ("everyone? ... let's say me") that will not produce follow-through — the action item will die quietly, and the deference pattern is both present and un-surfaced.
- Chapter 7's manager intervention when they see bureaucratic or pathological signs is explicit: *"not to run a culture-change workshop. It is to model the generative response in the next retro they attend — raise a specific case themselves, name their own role in the decision, and route it to a mechanism (routing matrix, standard, carve-out)."* The modelling is the intervention. Concretely: the manager names M.H.'s incident specifically at the next retro, names their own role in not having the Carve-out 3 running on pricing-adapter migrations in Q2, and routes the retro to a specific amendment — add pricing-adapter migrations to the Carve-out 3 scope in Q3, amend AGENTS.md's review-standard pointer, and reference it at the next retro.
- Carve-out(s) that would have surfaced the signal more sharply: **C3** on the pricing-adapter migration (would have surfaced M.H.'s re-derivable mental model before the diff anchored S.K.'s review); **C1** on R.P.'s "AI-review slips" (would have surfaced the slips in the paired conversation with specifics attached, where the retro surfaced only a category); and the Chapter 7 retro prompt *"Name one case this quarter where we accepted an AI output and later wished we hadn't. What was missing from the review?"* would have forced specificity. The absence of specificity in the retro is the Westrum diagnostic; the prompt is the mechanism that introduces it.

Count hits. **Four of five channels correctly identified with the correct carve-out, plus a Westrum classification matching the key's reasoning on Snippet E, is the pass bar.** Three or fewer means a re-read of Chapters 1–5 (especially the "common mistakes when citing" lists and Chapter 5's failure modes) before running Exercise 01 on your real team.

### Step 8 — Diagnose your misses (5 min)

For every channel miss, every carve-out mis-mapping, and every Westrum mis-classification, write one paragraph:

- Which of the three chapters' framings did you mis-apply? (G vs F is the most common mix-up: both look like "the IC did not challenge the AI," but G is about the *shape of growth* and F is about the *in-the-moment deference*.)
- Did you confuse an inside-frontier deference (appropriate) with an outside-frontier deference (the uncritical consumer pattern)? Snippet A tests this.
- Did you reach for a Chapter 5 carve-out when the primary response was a Chapter 6 ladder axis? Snippet B tests this.
- On the retro: did you classify it Generative because the facilitator went through the motions? The categories-without-specifics pattern is the Bureaucratic signature even when the facilitator is engaged.

### Step 9 — Re-run Snippet C from memory (5 min)

Close your file for a minute, then re-diagnose Snippet C from memory: channel, primary carve-out, manager-side action. Compare to your first pass. Snippet C is the "fullest case" because it composes a deference event (Chapter 4), a review-standard gap (Chapter 5 C3), a failure-of-incident-signal-to-trigger-carve-out (Chapter 7 retro), and a boundary-against-blame (Chapter 8 handoff-2). If your first pass only names one of these, the composition is not yet internalised — mark the row for re-read when you run Exercise 02 on your team's outside-frontier task-types.

## Expected output

A scratch file, roughly one to two pages, containing:

- Five diagnoses: channel letter, primary carve-out (or ladder axis for Snippet B), one-sentence why, manager-side action.
- A Westrum classification with reasoning on Snippet E.
- A diagnostic paragraph per miss.
- A re-run of Snippet C from memory.

Something like:

```
Snippet A — J.R., 18-month junior
  Channel: G (growth-path).
  Carve-out: C2 primary; C1 partial.
  Why: Brynjolfsson pattern — gains concentrate at junior tenure; IC cannot
       name one rejection in a month; the inside-frontier deference is not
       the diagnosis — the absent judgement-muscle formation is.
  Action: schedule next AI-off artifact on an outside-frontier task-type;
          do NOT frame as performance signal; programme-design signal per
          Ch. 2, Ch. 5.
  ✅ match.

Snippet B — S.K., 7-year senior
  Channel: D (differentiation).
  Carve-out: Chapter 6 Axis B (ladder), paired-review rotation (C1) is
             the production mechanism.
  Why: Noy & Zhang compression — top-tier leverage moved into
       mentorship / review; junior's improved second draft IS the
       senior's artifact; calibration line is the Ch. 3 response.
  Action: author ladder amendment (Ex 03) and surface the paired-review
          rotation on the ritual calendar.
  ✅ match.

Snippet C — M.H., 3-year mid-level [the fullest case]
  Channel: F (deference) on an outside-frontier task-type (pricing-
    adapter schema migrations — on the routing matrix).
  Carve-out: C3 primary (judgement-weighted review pass applied
    BEFORE the diff anchors S.K.'s review); C1 on the paired-review
    conversation where "what would you have done from scratch" lives.
  Why: Dell'Acqua uncritical-consumer pattern in its clearest form —
    IC had the mental model, didn't engage it, model's suggestion
    plausible enough to pass review ("the diff looked clean" is
    Ch. 4's exact phrase).
  Action: add pricing-adapter migrations to C3 scope; blameless
    postmortem (mod-109) runs separate from the growth conversation;
    do NOT frame as individual performance.
  ✅ match.

[... Snippets D and E in the same shape ...]
```

## Checkpoint

Before moving on to Exercise 01 (research-to-policy memo for your own team) and Exercise 02 (quarterly carve-out schedule for your own team), you should be able to answer **yes** to all five:

- Did you distinguish Snippet A's **growth-path** signal (Brynjolfsson) from Snippet C's **deference** signal (Dell'Acqua) — both of which involve an IC not challenging an AI suggestion — on the right basis (shape of growth vs. in-the-moment uncritical consumption on outside-frontier work)?
- Did you read Snippet B as a **differentiation** channel case that maps to a **Chapter 6 ladder axis**, not to a Chapter 5 carve-out as the primary response?
- Did you place Snippet D's new-grad case as a **growth-path** case and notice that the IC's own question is a psychological-safety signal to protect (Chapter 7, Edmondson) — not a performance-review trigger?
- Did you classify Snippet E's retro as **bureaucratic** (drifting pathological), identify the **model-the-generative-response** intervention Chapter 7 recommends, and name the specific Carve-out 3 / Carve-out 1 scope change that would have surfaced the signal with specifics?
- On every channel miss, did you identify whether you (a) confused inside-frontier deference with outside-frontier deference, (b) reached for a carve-out when the primary response was a ladder axis, or (c) classified the retro Generative because the facilitator went through the motions?

If any answer is no, re-read Chapters 2, 3, 4 end-to-end (especially the "common mistakes when citing" lists), Chapter 5's "Common failure modes when running the carve-outs," and Chapter 7's "What the retro layer specifically adds" — then re-attempt the misses — before starting Exercise 01 on your real team's context.
