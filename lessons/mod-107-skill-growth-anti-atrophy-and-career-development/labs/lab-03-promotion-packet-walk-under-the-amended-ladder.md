# Lab 03 — Promotion Packet Walk Under the Amended Ladder

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 6 (the three new axes A / B / C; the amended promotion-packet structure with Sections 2a, 2b, 3, 4; the three failure modes the updated ladder prevents; the common authoring mistakes), Chapter 3 (why output-based promotion signal compresses under AI augmentation), with side-checks against Chapter 2 (the growth-path channel that explains why high throughput at junior tier doesn't imply ladder-readiness) and Chapter 4 (the uncritical-consumer / centaur / cyborg distinction that Axis A probes for).
**Complements, does not duplicate:** Exercise 03 asks you to author **your team's** v0.1 ladder amendment and the amended promotion-packet template. This lab hands you a fixed, deliberately mixed-signal sample promotion packet from a fictional team — a packet that would have passed the pre-AI ladder on throughput and representative-artifact polish — so you can calibrate your *reading* of the amended axes before you spend authoring hours on your own ladder.

## Objective

Read a curated sample: an IC's **senior → staff** promotion packet from a fictional team, authored under the team's *pre-AI-augmentation* ladder. The packet reads as promotion-ready by the old rubric. Apply Chapter 6's amended rubric — Axes A / B / C scaled to the staff tier, plus the Sections 2a / 2b / 3 / 4 structure — and produce a verdict with reasoning. Then propose the two-to-three specific additions the IC's candidate-manager should request before the packet is re-submitted. Target: **you produce a verdict of "not yet, with named additions required" (rather than "yes" or "no"), and your named additions cover at least four of the five findings in the answer key**.

## Prerequisites

- Chapter 6 read end-to-end (the three new axes with their scaled descriptions; the before/after promotion-packet structure; the three failure modes; the common authoring mistakes).
- Chapter 3 read (Noy & Zhang's dispersion compression; the "promotion signal based on output volume and polish stops differentiating" argument).
- Chapter 2 skimmed (the growth-path channel — why high measured throughput at a junior-ish seniority does not imply ladder-readiness under AI augmentation).
- Chapter 4 skimmed (so you can score Axis A against the centaur / cyborg / uncritical-consumer distinction).
- Optional: Exercise 01 of your own (if drafted) — the policy memo whose citations ground the amendment.
- A blank file for your verdict and the named additions.
- A timer.

## The fictional context

> **"Order Routing" team, Trellis Marketplace.** 10 engineers (1 staff, 3 senior, 6 mid/junior). Owns the order-routing service and the fulfilment-adapter repo. Agents in use: Cursor Business (10 seats, rolled out Q1 2026); Claude Code via team gateway (usage-based, Q2 2026). The mod-106 routing matrix exists in v0.3 and flags **two outside-frontier task-types**: *"fulfilment-adapter migrations under vendor-SLA constraints"* and *"architecture-direction memos for the order-routing redesign."* The team's mod-107 ladder amendment is in **v0.1, drafted two quarters ago** — the three axes are published, but this is the *first* promotion packet authored under the amended rubric, and the IC's candidate-manager has drafted the packet in the *pre-AI-augmentation* shape without picking up Sections 2a / 2b / 3 / 4. The IC (D.R., 4 years on the team, 7 years in the industry) is up for senior → staff.

Score the packet against this team's ladder amendment and its routing matrix, not against an idealised packet.

## The candidate's promotion packet (v1, candidate-manager's draft)

Read all four sections before scoring. **Do not** scroll to the answer key until you have produced your verdict and the named additions.

### Promotion packet — D.R., senior → staff, Order Routing team, Q4 2026 cycle

> **Author:** D.R.'s candidate-manager (candidate also contributed). **Target level:** staff engineer. **Prior review cycle:** meets expectations at senior. **Rollout:** this would be the first packet authored under the Order Routing team's mod-107 ladder amendment v0.1.

#### Section 1 — Impact summary

> *D.R. has had a strong year. In Q1–Q3 2026, D.R. shipped 67 PRs across the order-routing service and the fulfilment-adapter repo — up from 48 in the same period of 2025 and the highest PR count on the team. D.R. led the Q2 rollout of Cursor onto the Order Routing team (scheduled the sessions, authored the team's Cursor rules file, mentored the mid-level engineers on tool fit) and the Q3 standup of the Claude Code team gateway (coordinated with Platform, authored the usage policy in collaboration with Finance). D.R.'s shipping velocity sets the pace for the team; their Cursor acceptance rate is 71%, the highest on the team. D.R. is consistently in the top two or three on the mod-104 DX Core 4 self-reported satisfaction and effectiveness tiles. The team's throughput is up ~30% year-over-year, and D.R.'s individual contribution and the Cursor rollout are the two most-named drivers in team-retro feedback.*

#### Section 2 — Representative artifacts

> *Three PRs are selected as representative of D.R.'s current level:*
>
> 1. **`order-routing/pull/5218`** — refactor of the order-dispatch state machine from a nested-switch implementation to a table-driven one. +640 lines, −780 lines, 12 files. Merged 2026-05-14. Reviewer: the staff engineer. Review comments: 6, all addressed; reviewer noted "cleaner than I would have authored it."
> 2. **`fulfilment-adapter/pull/2871`** — introduction of a new fulfilment-vendor's SLA-aware retry adapter. +410 lines, −30 lines, 5 files. Merged 2026-07-02. Reviewer: a senior engineer. Review comments: 3, all addressed. The new adapter passes the integration test matrix on first run; CI-time improvement of 8% on the adapter test suite.
> 3. **`order-routing/pull/5944`** — the quarterly team-wide upgrade of the OpenTelemetry instrumentation across the service's handlers. +1,200 lines, −900 lines, 24 files. Merged 2026-09-28. Reviewer: the staff engineer and a senior engineer (paired). Review comments: 9, 8 addressed; one open for a follow-up ticket. The mod-103 review-checklist pass took the reviewers ~2.5 hours in paired review; the staff reviewer's note: "this is the kind of cross-cutting change we've been hoping D.R. would take on — scope was handled well."

#### Section 3 — Leadership and mentorship

> *D.R. mentors the two newest mid-level engineers (J.M. and K.S.), pairing with each on average one hour per week. Both have remarked positively on the pairing in their own 1:1s. D.R. has also informally reviewed drafts of the Platform team's AI-usage policy at their request, and chaired the team's Thursday-morning "coffee with Cursor" show-and-tell sessions throughout Q2 (which were dropped in Q3 as attendance fell). D.R. ran the Q2 Cursor bootcamp (one half-day session, 90 min per sub-topic, whole team attended). D.R. is well-regarded on the team; peer feedback is uniformly positive on D.R.'s technical skill and enablement work.*

#### Section 4 — Peer feedback

> *Three selected quotes:*
>
> - *"D.R. is one of the most productive engineers I've worked with. The order-dispatch refactor is cleaner than anything we had before."* — a senior peer.
> - *"D.R. is who I ask when I don't know which tool or approach to use. The Cursor rollout was smooth because D.R. ran it."* — a mid-level peer.
> - *"D.R. carried the OpenTelemetry upgrade. That was a significant undertaking and it landed clean."* — the staff engineer.

## Steps

### Step 1 — Set up your working file (3 min)

Create a working file `lab-03-packet-walk.md`. Add this header:

```
# Lab 03 — Promotion packet walk under amended ladder
#        D.R., senior → staff, Order Routing (Trellis Marketplace)

Chapter 6 axes (scaled to the staff tier):
  A  Judgement under AI augmentation — staff bar:
     "predicts where the AI will be wrong in advance, routes around
      it, sets the team's frontier placement on new task-shapes —
      decides which routing-matrix decisions the matrix should make"
  B  Mentorship of judgement — staff bar:
     "designs and leads the team's deliberate-practice carve-out
      (Chapter 5); the retro mechanism feeds into the next quarter"
  C  Review craft on AI-assisted work — staff bar:
     "reshapes the review standard itself when retro surfaces a gap;
      the mod-103 standard is version-controlled; staff ICs edit it"

Chapter 6 promotion-packet amendment (Sections 2a / 2b / 3 / 4):
  2a  Representative artifacts, each annotated by the IC with two
      sentences: "what I decided the AI could draft" and "what I
      decided to write myself." Reviewer evaluates the decision,
      not only the artifact.
  2b  Three narratable judgement moves — a review catch another
      reviewer missed, a push-back on a stakeholder's AI-generated
      plan, a redirect of a routing-matrix classification.
  3   Mentorship of judgement specifically — not generic mentorship.
      Named ICs whose judgement capacity grew under the IC's pairing.
      Carve-out 1 produces the evidence.
  4   Peer feedback with the added prompt: "name a decision this IC
      made that you would not have expected from someone at the
      prior level."

Chapter 6 failure modes the updated ladder prevents:
  FM1  Fast-shipping junior-ish IC promoted on throughput before
       judgement warrants it
  FM2  Senior IC who looks flat on output — leverage has moved into
       mentorship / review and the old rubric does not surface it
  FM3  Staff IC whose scope you cannot name — diffuse by nature,
       worse under AI augmentation unless the amendment surfaces
       the review-standard and routing-matrix work

For the packet record: (a) verdict (yes / not yet, named additions
required / no — the chapter's middle option is almost always the
right one on a first v1 draft against v0.1 amendment); (b) one-
paragraph reasoning; (c) 3–5 specific named additions the
candidate-manager should request before re-submission.
```

### Step 2 — Score Section 1 (Impact summary) (6–8 min)

Read Section 1 against Chapter 6's "Section 1" guidance: *"Impact summary (unchanged structure, but impact is now measured in terms of decisions, not throughput — 'led the decision to route schema migrations through the human-reviewed path; avoided one incident caught at review time' rather than 'shipped 25 PRs')."*

- Which sentences in Section 1 are throughput-shaped? Count the PR-volume, acceptance-rate, and velocity-ranking framings.
- Which sentences are *decision*-shaped? (A "led the decision to X" or "chose Y over Z and avoided W" shape.)
- Does Section 1 cite research or ladder axes? (It should not need to — but if the candidate-manager has drafted the section as if the ladder had not been amended, the writing will betray that.)
- Which Chapter 3 common mistake is the "acceptance rate 71%, highest on the team" framing making? (Hint: Chapter 3 specifically names the dispersion-compression finding and warns against reading output-rate as a promotion signal under AI augmentation.)

Write a 3–4-line verdict on Section 1.

### Step 3 — Score Section 2 and attempt a 2a / 2b split (10–12 min)

Read Section 2 against the amended **Section 2a** (judgement-annotated artifacts) and **Section 2b** (narratable judgement moves).

For each of the three representative PRs, ask: *does the packet carry the Section 2a judgement annotation (two sentences per artifact: "what I decided the AI could draft, what I decided to write myself")?* Then ask: *does the packet carry Section 2b at all — three narratable judgement moves such as a review catch, a stakeholder push-back, a routing-matrix redirect?*

Score each PR individually:

- **PR 1 (state-machine refactor).** Is "cleaner than I would have authored it" from the reviewer evidence of judgement, or evidence of a polished artifact? Chapter 3 is explicit that the output-polish signal has compressed under AI augmentation.
- **PR 2 (fulfilment-adapter retry).** Note the task-type: *fulfilment-adapter migrations under vendor-SLA constraints* is **on the Order Routing team's routing matrix as outside-frontier**. Section 2a for this artifact specifically needs the decision-annotation; a clean PR on an outside-frontier task without the annotation is the specific place the Chapter 4 uncritical-consumer risk lives.
- **PR 3 (OpenTelemetry upgrade).** Cross-cutting scope is a classic staff-tier-signal shape, and the paired review with the staff engineer is strong — but is there a Section 2a annotation of "what I decided the AI could draft" on a 1,200-line change? And does "9 comments, 8 addressed, one follow-up ticket" tell you anything about the IC's judgement on the AI's output?

Then ask the Section 2b question: are there any judgement moves narrated at all — a review catch on another IC's PR, a push-back on a stakeholder's AI-generated plan, a redirect of a routing-matrix classification? Scan the entire packet, not just Section 2.

Write a 4–5-line verdict on Section 2 / 2a / 2b.

### Step 4 — Score Section 3 (Leadership and mentorship) (8–10 min)

Read Section 3 against Chapter 6's amended **Section 3**: *"Mentorship of judgement specifically — not generic mentorship. Named ICs whose judgement capacity grew under the IC's pairing. Chapter 5's paired-review rotation produces the evidence."*

- Is the mentorship work in Section 3 *mentorship of judgement* or *generic mentorship*? The pairing "on average one hour per week" with J.M. and K.S. is mentorship; the packet does not name what judgement capacity grew in either.
- The Cursor rollout work — authoring the rules file, running the Q2 bootcamp, chairing the Thursday show-and-tells — is it **Axis B** (mentorship of judgement) or **Axis C-adjacent** (team enablement / mod-105 work) or neither? Chapter 6 is specific about what Axis B rewards; is a Cursor rollout an Axis B artifact?
- The "coffee with Cursor" sessions were dropped in Q3 as attendance fell. Is this a signal of a Chapter 6 common authoring mistake (Chapter 6 lists *"Mentor outcomes, not activities. Axis B rewards mentorship that moved a junior IC's capacity, not mentorship hours. The distinction protects against performative mentorship"*)?
- Did the candidate-manager cite **Carve-out 1 (paired-review rotation)** as the evidence source for Axis B? Does the packet reference any paired-review outcomes at all?

Write a 4–5-line verdict on Section 3, including the implicit **Axis B** scoring at the staff tier.

### Step 5 — Score Section 4 (Peer feedback) and the implicit Axis C (6–8 min)

Read Section 4 against the amended **Section 4** (standard quotes + one added prompt: *"name a decision this IC made that you would not have expected from someone at the prior level."*). Then ask the implicit **Axis C** question: *"has D.R. reshaped the review standard — the mod-103 standard — in a way the packet surfaces?"* The staff-tier Axis C bar is explicit: *"reshapes the review standard itself when the retro surfaces a gap; the mod-103 standard is version-controlled; staff ICs edit it."*

- Do any of the three peer quotes answer the added-prompt question, even informally? *"D.R. is the most productive engineer I've worked with"* is not the answer the prompt is looking for; *"D.R. caught the subtle timing bug in J.M.'s AI-assisted PR that neither of us would have noticed"* would be.
- Does the packet cite any mod-103 review-standard contribution by D.R.? Any proposed amendment D.R. authored, any retro gap D.R. surfaced and closed, any change to the Order Routing team's version-controlled review checklist?
- Does the packet cite any **routing-matrix** contribution (Axis A at staff tier)? Did D.R. propose or amend any routing-matrix classification this cycle?

Write a 3–4-line verdict on Section 4 and the implicit Axes A / C.

### Step 6 — Produce the overall verdict and the named additions (10–12 min)

Draft the overall verdict in three parts:

- **Verdict:** *yes* / *not yet, named additions required* / *no*. Chapter 6 is explicit that the amendment is additive and that reviewers *"evaluate the decision, not only the artifact"*; on a v1 draft that was authored before Sections 2a/2b/3 structure was picked up, the right verdict is almost always *not yet, named additions required* — the packet has to be re-submitted in the amended shape, and a *no* on this packet would be based on *absence of annotation*, not *absence of candidate strength*.
- **Reasoning:** a one-paragraph summary tying your Section 1, 2, 3, 4 verdicts together. Specifically: the pre-AI-augmentation reading of this packet is a strong yes; the AI-augmented reading is a "the signal we need to see is not in this draft, and this is the Chapter 3 compression finding in action — a staff-tier promotion case cannot be made on throughput, tool-rollout work, and polished artifacts alone."
- **Named additions:** a numbered list of 3–5 specific items the candidate-manager should request D.R. and D.R. himself add before re-submission. Each item should be specifically actionable and pointed at a Chapter 6 section or axis.

### Step 7 — Compare against the answer key (8 min)

Read the key below only after you have produced your verdict and named additions.

#### Answer key — verdict and findings

**Verdict: not yet — named additions required before the committee votes.**

This is the Chapter 6 "first packet authored under v0.1 amendment" shape in its most common form. D.R. is credibly staff-tier; the packet as drafted does not demonstrate it in the amended rubric. The pre-AI-augmentation ladder would have voted *yes* on this packet (strong throughput, cross-cutting PR, visible enablement work, uniformly positive peer feedback). The amended ladder is the explicit response to exactly this reading — Chapter 3's compression finding predicts that output-polish-plus-throughput packets will look identical for candidates at a range of actual judgement levels, and Chapter 6's three axes are what the committee reads instead.

**Five findings, each tied to a named addition.**

**Finding 1 — Section 1 is throughput-shaped, not decision-shaped (Chapter 6 Section 1 amendment).** The 67-PRs, +30% team throughput, 71% acceptance rate, and "sets the pace" framing are the *exact shape* Chapter 6 asks the amendment to replace. The 71% Cursor acceptance rate framed as "highest on the team" is also the Chapter 3 compression-finding mistake in its most common packet form — under AI augmentation, a high acceptance rate is as consistent with uncritical consumption as with skilled use, and framing it as a top-rank signal reads the output volume as promotion evidence precisely the way the chapter warns against.

- **Named addition 1:** rewrite Section 1 in decision-shaped language. Replace the PR count and acceptance-rate framings with two or three specific decisions D.R. led this year — a specific architectural call, a specific routing-matrix amendment, a specific review-standard change — with the one-sentence outcome / risk-avoided framing Chapter 6 models.

**Finding 2 — Section 2 has no Section 2a annotations and no Section 2b judgement moves (Chapter 6 Sections 2a + 2b).** All three artifacts are presented as artifacts, not as artifacts-plus-judgement-annotations. PR 2 is the sharpest absence: *fulfilment-adapter migrations under vendor-SLA constraints* is **on the Order Routing routing matrix as outside-frontier**, and a clean 410-line PR on an outside-frontier task-type with no Section 2a annotation is the specific place the Chapter 4 uncritical-consumer risk lives. The "passes the integration test matrix on first run" framing is especially risky — Chapter 4's hard case is exactly this shape (the artifact looks clean; the deference may be invisible until a vendor-SLA edge arrives in production).

- **Named addition 2:** add Section 2a annotations to all three PRs — two sentences each: "what I decided the AI could draft and why" and "what I decided to write myself and why." Reviewer evaluates the *decision*, not only the artifact (Chapter 6).
- **Named addition 3:** add Section 2b — three narratable judgement moves. Candidates: a review catch D.R. made on J.M.'s or K.S.'s AI-assisted work; a push-back on a stakeholder's AI-generated plan; a redirect of a routing-matrix classification. Chapter 6 is explicit that these are the moves demonstrating the IC's judgement has been *active*, not deferred.

**Finding 3 — Section 3's mentorship work is Axis-B-adjacent at best; the Cursor rollout is Axis-B-mislabeled (Chapter 6 Section 3 + Axis B scaling + the common-authoring-mistakes list).** The one-hour-per-week pairing with J.M. and K.S. is not evidence against D.R. — it is evidence of mentorship *hours*, not mentorship *outcomes*. Chapter 6 is explicit: *"Mentor outcomes, not activities. Axis B rewards mentorship that moved a junior IC's capacity, not mentorship hours. The distinction protects against performative mentorship — which has always been a risk and is more of a risk now."* The Cursor rollout work — authoring the rules file, running the Q2 bootcamp, chairing the Thursday show-and-tells — is largely mod-105 team-enablement work (which is *not* the mod-107 Axis-B signal and which the candidate-manager may be mis-classifying as such). The dropped-when-attendance-fell show-and-tells are a soft signal in the common-authoring-mistakes direction.

- **Named addition 4:** name the specific judgement capacity J.M. or K.S. has grown under D.R.'s pairing — tied to a specific outside-frontier task-type from the routing matrix. If the pairing has produced a visible lift in a junior's ability to re-derive a decision on a fulfilment-adapter migration or to catch an AI-wrong architectural suggestion, name it and name the artifact. The Chapter 5 Carve-out 1 (paired-review rotation) outcomes are the natural evidence site. If there is no such outcome, the one-hour-per-week pairing is a *weak* Axis B signal and Section 3 should be honest about it — the packet is stronger for being specific.

**Finding 4 — Section 4 does not carry the added peer-feedback prompt; peer quotes are throughput-shaped (Chapter 6 Section 4 amendment).** None of the three peer quotes answer *"name a decision this IC made that you would not have expected from someone at the prior level"* — they praise productivity, tool-fit knowledge, and project delivery. All three quotes are consistent with a senior-tier contribution; none are specifically staff-tier-shaped under the amended ladder. Chapter 3's compression finding predicts this: output-polish-based peer feedback stops differentiating under AI augmentation.

- **Named addition 5:** re-solicit peer feedback with the added prompt. Chapter 6 specifies the prompt exactly; add it to the standard feedback form and ask the same three peers (and ideally one additional reviewer — the staff engineer is a clear candidate, since they already reviewed PRs 1 and 3) to answer it. The answers are the Section 4 evidence the committee reads for Axes A/B/C under the amended rubric.

**Finding 5 — Axes A and C are not surfaced (Chapter 6 staff-tier Axis-A and Axis-C scaling).** The packet does not name a routing-matrix contribution (Axis A at staff tier: *"sets the team's frontier placement on new task-shapes — decides which routing-matrix decisions the matrix should make"*). The packet does not name any mod-103 review-standard contribution by D.R. (Axis C at staff tier: *"reshapes the review standard itself when the retro surfaces a gap; the mod-103 standard is version-controlled; staff ICs edit it"*). For a staff-tier promotion, the absence of both of these is the single sharpest gap — Axis A and Axis C at the staff tier are what distinguish staff from strong-senior under the amended ladder, and both are *observable* on the team's version-controlled artifacts.

- **Named addition 6 (optional 6th):** D.R. and the candidate-manager scan the team's routing-matrix history (mod-106 Exercise 01's version control) and the team's review-standard history (mod-103 version control) for the last four quarters, and name specific contributions D.R. has authored on each. If D.R. has authored none, this is the specific staff-tier gap the amendment is designed to surface, and the packet should be re-submitted next cycle after D.R. has a quarter of visible Axis-A and Axis-C work. Chapter 6 is clear that the staff-tier axes are *aspirational by design* and that not every senior IC clears them.

**Pass bar:** *not yet, with named additions required*, plus at least **four of five findings** named with the correct axis / section mapping. Three or fewer findings named means a re-read of Chapter 6 (especially "The three new axes, named" and "What a promotion packet looks like after the update") before running Exercise 03 on your team's ladder.

### Step 8 — Spot-check the manager's framing of the re-submission conversation (5 min)

Before you close the file, write one paragraph on *how* the candidate-manager should present these named additions to D.R. The paragraph tests whether you have internalised the Chapter 7 psychological-safety / Chapter 8 ownership-boundary posture. Three features of a good manager framing:

- Start with the straightforward read of the pre-AI ladder: D.R. is a credibly staff-tier candidate on the previous rubric's grounds. The re-submission is a *packet* issue, not a *candidate* issue.
- Name the amendment as the reason for the re-submission — the ladder changed, this is the first packet under the new ladder, and the packet needs to match the new shape. The Chapter 3 compression finding is the one-sentence research grounding if D.R. asks why.
- Do **not** cite Dell'Acqua or Noy & Zhang as implying anything about D.R. specifically (Chapter 8's named failure: *"Do not cite Dell'Acqua or Noy & Zhang as justification in an HR conversation about an individual IC. The research is about populations; an individual's pattern is specific."*). The research grounds *the amendment*; it is not evidence that D.R. has deferred on any specific artifact.

A closing paragraph that threatens consequences, reads as an audit, or implies D.R.'s judgement is suspect has drifted; revise.

## Expected output

A scratch file, roughly a page and a half, containing:

- Four section-by-section verdicts (Sections 1, 2 / 2a / 2b, 3, 4 / Axis A + C), each 3–5 lines.
- A one-paragraph overall verdict, explicitly naming *not yet, named additions required*.
- A numbered list of 3–5 specific named additions, each tied to a Chapter 6 section or axis.
- A paragraph on the manager's framing of the re-submission conversation, tested against the Chapter 7 + Chapter 8 posture.

Something like:

```
Overall verdict — not yet, named additions required.

Pre-AI ladder read: strong yes (throughput, cross-cutting PR, visible
  enablement, uniformly positive peer feedback). AI-augmented ladder
  read: Sections 2a / 2b / 3 (mentorship-of-judgement specifically)
  and the Section-4 added prompt are absent; Axes A and C at staff
  tier are not surfaced. Chapter 3 compression finding in its
  canonical packet form — output-shaped signals look identical at a
  range of actual judgement levels, and the amended axes are what
  the committee reads instead.

Named additions:
  1. Rewrite Section 1 in decision-shaped language (Ch. 6 Section 1).
  2. Add Section 2a annotations to all three PRs (Ch. 6 Section 2a).
  3. Add Section 2b — three narratable judgement moves (Ch. 6 2b).
  4. Replace "mentorship hours" with named junior-IC-capacity outcomes
     tied to a routing-matrix outside-frontier task-type (Axis B, Ch.
     6 Section 3; Chapter 5 Carve-out 1 is the evidence site).
  5. Re-solicit peer feedback with Chapter 6's added prompt (Section 4).
  6. (Optional) Scan routing-matrix and review-standard version control
     for Axes A and C contributions over the last four quarters.

Manager framing of re-submission: emphasise that the amendment is
  additive and the packet needs to match the new shape — not that
  D.R. has deferred on anything. Do NOT cite Dell'Acqua/Noy & Zhang
  as applying to D.R. specifically (Chapter 8 boundary).
```

## Checkpoint

Before moving on to Exercise 03 (where you author **your team's** v0.1 ladder amendment and the promotion-packet template), you should be able to answer **yes** to all five:

- Did you reach a verdict of **"not yet, named additions required"** — not **"yes"** (which is the pre-AI ladder read and misses the compression finding) and not **"no"** (which would be based on absence of annotation, not absence of candidate strength)?
- Did you identify the 71% Cursor acceptance rate framed as "highest on the team" as the specific Chapter 3 compression-finding mistake — reading output volume / acceptance rate as a promotion signal under AI augmentation?
- Did you flag the fulfilment-adapter retry PR (PR 2) as specifically high-risk-for-uncritical-consumer-pattern because the task-type is on the routing matrix as outside-frontier and the PR has no Section 2a decision annotation?
- Did you distinguish the Cursor rollout work (mod-105 team-enablement, *not* mod-107 Axis B) from mentorship of judgement (Axis B specifically — named junior-IC-capacity outcomes tied to outside-frontier task-types)?
- Did your framing of the re-submission conversation stay on Chapter 7's psychological-safety posture and Chapter 8's boundary (no citing research as implying anything about D.R. specifically; no audit-shaped language; no consequences-threat)?

If any answer is no, re-read Chapter 6 ("The three new axes, named" and "What a promotion packet looks like after the update"), Chapter 3 ("Why Finding 3 is the one that reshapes your ladder"), and Chapter 8 ("What the manager must *not* do") — then re-attempt the verdict — before running Exercise 03 on your team's ladder.
