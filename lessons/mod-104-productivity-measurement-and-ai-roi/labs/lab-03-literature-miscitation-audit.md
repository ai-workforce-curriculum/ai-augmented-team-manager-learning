# Lab 03 — Literature Mis-citation Audit on an Exec Slide

**Duration:** 45–60 minutes.
**Chapters exercised:** Chapter 5 (the five anchor studies; what each does and does not claim; the responsible-citation shape; "what *not* to do with the literature"), with side-checks against Chapter 7 (how the citation travels into Section 3 of the one-pager) and Chapter 1 (the theatre shapes the mis-cite reinforces) and Chapter 9 (where the product-feature ROI citation crosses the manager / PM boundary).
**Complements, does not duplicate:** Exercise 02 asks you to produce **your own** one-page literature digest with a one-sentence citation form for each of the five anchor studies, for reuse in your real one-pager. This lab gives you a fixed, deliberately mis-cited exec-ready slide for a fictional team and asks you to diagnose every citation error against the five anchor studies, rewrite the three load-bearing citations in Chapter 5's responsible-citation shape, and cross-check against Chapter 7's Section-3 structure. You run the diagnosis on a known-broken input here so you can calibrate your citation reflex before you write Section 3 under the Q-review time pressure of Exercise 04.

## Objective

Read a curated sample: a fictional "AI Productivity — Q-review cross-team summary" slide authored by an adjacent team's manager and circulated to the peer manager group. The slide carries six citation claims. Identify each citation error against the Chapter 5 anchor studies (Peng, Ziegler, Noy & Zhang, Brynjolfsson, Dell'Acqua). Rewrite the three load-bearing citations in the Chapter-5 responsible-citation shape. Flag the two claims that cross into *industry-survey* territory (Chapter 5 "do not cite industry surveys as if they were peer-reviewed research") and the one claim that crosses the Chapter-9 manager / PM boundary. Target: **you identify at least five of the seven findings in the answer key**, and your three rewrites each name the study, the task, the population, the effect size, and the limit in one sentence.

## Prerequisites

- Chapter 5 read end-to-end (the five anchor studies; the responsible-citation shape; the cross-cutting findings; "what *not* to do with the literature").
- Chapter 7 skimmed (Section 3 "What the literature predicts, and what we actually see"; the one-sentence-of-specific-citation claim).
- Chapter 1 skimmed (the three theatre shapes — the mis-cite often reinforces one or more).
- Chapter 9 skimmed (the manager / PM boundary; team-productivity ROI vs product-feature ROI).
- A blank file for your diagnosis and rewrites.
- A timer.

Optional but useful: Exercise 02 draft or the literature digest you have in progress — the lab's rewrites will plug directly into Exercise 02's one-sentence citation forms.

## The fictional context

> **Peer manager's cross-team slide.** The slide below is one page of an internal cross-team Q-review deck, circulated by `@peer-manager-adjacent-team` to the full peer manager group. The peer manager's team is the "Document Intelligence" team at the same org as yours — 11 engineers, shipped an AI-powered document-summary feature in Q3, used Copilot + a fine-tuned internal model. The peer manager has asked the group for feedback on the slide *before* presenting to the VP next week. You are the reviewer. Treat the slide as a real artifact you would mark up in a shared doc — your audit will become the comment thread.

## The circulated slide

Read all six citation claims end-to-end before taking notes. Deliberately mis-cited. Do not scroll past them until you are done reading.

```
DOCUMENT INTELLIGENCE — Q3 AI PRODUCTIVITY, PEER DRAFT

Headline
--------
AI tools are delivering real productivity gains across software
engineering. Our team is in line with industry benchmarks.

Research evidence
-----------------
1. GitHub research (Copilot) shows developers are 55% more productive
   with AI tools.

2. Microsoft Work Trend Index 2024 finds 75% of knowledge workers
   now use AI at work; our 94% adoption rate exceeds this.

3. Science 2023 (Noy & Zhang) shows generative AI produces 18%
   better output across all knowledge work, confirming that AI
   writes better than humans in most cases.

4. NBER research (Brynjolfsson et al.) establishes that senior
   engineers gain the most from AI tooling because they have the
   experience to direct it effectively.

5. The Dell'Acqua study at HBS shows that AI makes consultants
   40% better at their jobs.

6. Our team's AI-powered document-summary feature drove a 23%
   retention lift among enterprise customers in Q3 — strong evidence
   that AI investment is paying back.

Our own number
--------------
Our team's deployment frequency rose 31% QoQ with AI tooling.
Consistent with the 25% average productivity gain reported in
the published literature.

Decision ask
------------
Grow AI investment: +8 Copilot seats, +4 Cursor seats, expanded
model-access budget.
```

## Steps

### Step 1 — Set up your audit memo (3 min)

Create a working file `lab-03-citation-audit.md`. Add this header:

```
# Lab 03 — Citation audit (Document Intelligence Q3 slide)

Chapter 5 anchor studies:
  S1  Peng et al. 2023       (arXiv:2302.06590)       Copilot, bounded task, ~55%
  S2  Ziegler et al. (CACM)  observational, acceptance-rate ↔ self-report
  S3  Noy & Zhang 2023       (Science)                writing, ~40% / ~18% quality
  S4  Brynjolfsson et al. 2023 (NBER 31161)           support, ~14% avg, 34% juniors
  S5  Dell'Acqua et al. 2023 (BCG + HBS / SSRN 4573321) jagged frontier +40%/-19%

Chapter 5 "what NOT to do":
  N1  compound claims ("research shows 30%" without a citation)
  N2  cite industry marketing surveys as peer-reviewed research
  N3  let the literature freeze (2023 anchors need refresh every ~4 quarters)

Chapter 9 boundary:
  B1  team-productivity ROI (yours)    vs    product-feature ROI (PM's)

For each of the six claims, record:
  (a) which anchor study it is trying to cite (or which it conflates),
  (b) what the study actually found,
  (c) specifically how the claim mis-cites it,
  (d) the responsible-citation rewrite (if load-bearing).
```

### Step 2 — Audit the six claims against Chapter 5 (20–25 min)

Work through claims 1 through 6 in order. For each: *is this a direct mis-cite of an anchor study, an industry-survey slippage (N2), a compound claim (N1), a Chapter-9 boundary crossing, or a legitimate citation with a specific defect?* Write 2–3 lines per claim. Do not scroll to the answer key until you have at least five findings written down. **Target: no more than 4 minutes per claim.**

Specifically, for each claim:

- **Claim 1 — "GitHub research shows developers are 55% more productive with AI tools."** Which anchor does this intend to cite? What was the specific task in that study? What is the correct scope-limited restatement?
- **Claim 2 — "Microsoft Work Trend Index 2024: 75% of knowledge workers use AI at work; our 94% adoption rate exceeds this."** Is this an anchor study? Where in Chapter 5 is this specifically addressed? Is "our 94% adoption exceeds 75%" a legitimate comparison?
- **Claim 3 — "Noy & Zhang: 18% better output across all knowledge work; AI writes better than humans in most cases."** What was the task domain in Noy & Zhang? What was the specific effect reported? Is the "across all knowledge work" generalisation supported? Is "AI writes better than humans in most cases" a reading of this finding?
- **Claim 4 — "Brynjolfsson et al.: senior engineers gain the most."** This is the *most important* mis-cite on the slide. What did Brynjolfsson et al. actually find? Which direction is the distribution the claim inverts?
- **Claim 5 — "Dell'Acqua at HBS: AI makes consultants 40% better at their jobs."** What did Dell'Acqua et al. find on *inside-frontier* tasks? What did they find on *outside-frontier* tasks? What does the "40% better at their jobs" claim omit?
- **Claim 6 — "Our AI-powered document-summary feature drove 23% retention lift."** Which Chapter-9 boundary does this cross? Why is this specifically *not* a team-productivity-ROI citation?

### Step 3 — Audit the "Our own number" paragraph and the decision ask (5 min)

Separately from the claims, write a 4–5 line diagnosis of:

- The "Our team's deployment frequency rose 31% QoQ with AI tooling. Consistent with the 25% average productivity gain reported in the published literature." sentence. Which Chapter-5 "what *not* to do" patterns appear? Does it meet Chapter 7's Section-3 bar ("the published range is X–Y; our team's own measurement is Z, for these specific reasons")?
- The decision ask. Is it a Chapter-7 decision ask? Given the citation defects above, would the VP's follow-up question — *"what is the published range by task, and where does our team sit in that range?"* — be answerable from the slide?

### Step 4 — Compare against the answer key (10 min)

Below is the answer key — seven findings. For each, check whether your audit found it. Count hits (same claim or same location, same finding) and near-misses (same claim but different framing).

#### Answer key — seven findings

1. **Claim 1 (Peng mis-attribution and scope-strip).** The 55% number comes from Peng et al. (2023, arXiv:2302.06590) — not generically "GitHub research" (though GitHub Copilot is the tool). The ~55% effect was on a *single bounded greenfield HTTP-server task* in a controlled setting; generalising to "developers are 55% more productive with AI tools" is the *exact mis-cite pattern* Chapter 5 is written to prevent. The responsible citation: "A 2023 controlled study on a bounded HTTP-server task found a ~55% completion-time improvement with Copilot access (Peng et al. 2023, arXiv:2302.06590)." Replace in the slide.

2. **Claim 2 (Microsoft Work Trend Index — N2 industry-survey slippage).** Chapter 5 is explicit: "do not cite industry marketing surveys as if they were peer-reviewed research. The McKinsey / Microsoft / Gartner surveys … belong in the 'industry adoption' paragraph, not in the empirical-evidence paragraph." The Microsoft WTI is a legitimate signal of adoption-rate context in a Chapter-4 / mod-102 industry-context paragraph, but it does not belong under a "Research evidence" header alongside Peng / Noy-Zhang / Brynjolfsson / Dell'Acqua. Secondarily: "our 94% adoption exceeds 75%" is the Chapter-1 Theatre A move (adoption-count as productivity) dressed as benchmarking — adoption is a provisioning number, not productivity.

3. **Claim 3 (Noy & Zhang domain-overstretch).** Noy & Zhang (Science 2023) studied *mid-level professional writing tasks* (press release, short report, email, analysis plan) with N = 453 college-educated professionals — not "all knowledge work." The reported effects were ~40% time improvement and ~18% quality improvement (the slide dropped the time half entirely). The claim "AI writes better than humans in most cases" is *not* a Noy & Zhang finding — the quality improvement was on AI-*assisted* human output, not AI-replaces-human, and the distribution finding (lower-rated workers benefit more) is the chapter's load-bearing observation that the slide omits. Responsible citation: "Noy & Zhang (Science 2023) found a ~40% time improvement and ~18% quality improvement on mid-level professional writing tasks, with disproportionate benefit to lower-rated workers." Replace in the slide.

4. **Claim 4 (Brynjolfsson distribution-inversion — the load-bearing mis-cite).** Brynjolfsson, Li & Raymond (NBER 31161) studied customer-support agents (N > 5,000) in a staggered rollout. The ~14% average productivity gain was concentrated among *low-experience workers* (34% for the least-experienced tier) and was *minimal* for the most-experienced agents. The slide **inverts the direction of the distribution** — this is Chapter 5's single most important qualitative claim from the literature for a team manager, and the slide gets it backwards. "Senior engineers gain the most" is the opposite of the finding. This mis-cite is also actively dangerous: if the VP acts on it, the team will under-invest in junior-support agent fluency and over-invest in senior tooling where the literature predicts the smallest marginal gain. Responsible citation: "Field evidence from a customer-support setting shows a ~14% average productivity gain, concentrated among junior workers (34% for the least-experienced tier) and much smaller for senior workers (Brynjolfsson, Li & Raymond, NBER 2023)." Replace in the slide.

5. **Claim 5 (Dell'Acqua one-sided-reading — the jagged-frontier omission).** Dell'Acqua et al. (BCG + HBS, SSRN 4573321, 2023) found consultants were ~40% higher quality on *inside-frontier* tasks *and* ~19% *more likely to produce incorrect solutions* on *outside-frontier* tasks. The slide reports only the positive side ("40% better at their jobs"), which strips the entire jagged-frontier finding — the chapter's single most important *shape* claim from the literature. This is also the Chapter-1 Theatre pattern reinforcing: a dashboard or slide that quotes only the +40% number and not the -19% number is miscalibrated by construction, because the team's own number is almost certainly a composite of inside-frontier gain and outside-frontier loss. Responsible citation: "Dell'Acqua et al. 2023 show that AI assistance improves consultant task quality on 'inside-frontier' tasks and *degrades* it on 'outside-frontier' tasks — and that workers do not reliably identify the frontier without training (BCG + HBS field experiment)." Replace in the slide.

6. **Claim 6 (Chapter-9 boundary-crossing — manager-takes-credit-for-product).** The "23% retention lift" on the document-summary feature is a *product-feature ROI* claim, not a team-productivity ROI claim. Chapter 9 names this as one of the three recognisable failure modes when the boundary slips: "manager-takes-credit-for-product — an AI feature launches and performs well; the one-pager claims the lift. The PM notices. Trust is spent that was more valuable than the slide." The retention number is the PM's claim to make; the team-manager's contribution is the engineering-cost and delivery-quality *inputs* to the PM's one-pager. The peer-manager slide should credit the PM partner (`ai-augmented-product-manager`, L30) and report the engineering-side evidence only — "this feature took X weeks of engineer-time; the agent-infra costs $Y/month at expected load; change failure rate during build was Z."

7. **The "Our own number" + decision ask — N1 compound claim and Chapter-7 Section-3 failure.** "Our team's deployment frequency rose 31% QoQ with AI tooling. Consistent with the 25% average productivity gain reported in the published literature." fails three ways simultaneously: (a) "25% average productivity gain" is the N1 compound rough claim Chapter 5 warns against — there is no single average; the published range is Peng's 55% on a bounded task through Brynjolfsson's 14% average with 34% for juniors, and quoting a composite is the mis-cite the digest is supposed to prevent; (b) attributing 31% QoQ rise in deployment frequency to AI tooling without the Chapter-3 Caveat-1 attribution sidebar (agent-drafted scaffolding, tests, and PR descriptions can move the number without underlying work changing) is the specific trap Chapter 3 names; (c) Chapter 7 Section 3's shape is "the published range is X–Y; our team's own measurement is Z, for these specific reasons" — this sentence inverts it and asserts consistency without naming the range. The decision ask ("+8 Copilot seats, +4 Cursor seats, expanded model-access budget") is *actionable* which is good, but given the citation defects above, the VP's reasonable follow-up — *"what task classes are those seats going to, and which side of Dell'Acqua's frontier are they on?"* — is unanswerable from the slide. Chapter 7: a one-pager that could be filed and forgotten will be; a one-pager built on mis-cites that cannot survive the first follow-up question will be filed, and so will the next one.

Count your hits. **Five or more is the pass bar**; three to four means a re-read of Chapter 5's five study paragraphs and "What *not* to do with the literature"; two or fewer means re-read Chapter 5 end-to-end.

### Step 5 — Rewrite the three load-bearing citations (10–15 min)

Pick the three *load-bearing* mis-cites — Claims 1 (Peng), 4 (Brynjolfsson), 5 (Dell'Acqua) — and write each in Chapter 5's responsible-citation shape. Keep each citation to 1–2 sentences. Each must name:

- The study (author + year + venue).
- The task or population.
- The specific effect size (with the direction).
- The one-sentence scope limit that prevents the mis-cite.

Example shape (not a template to copy verbatim):

```
Peng et al. (2023, arXiv:2302.06590) — a controlled study on a
bounded HTTP-server task (N = 95 professional developers) — found
a ~55% completion-time improvement with Copilot access. The effect
is specific to a bounded, greenfield, well-specified coding task
in a controlled setting; it is not a claim about multi-task,
brownfield, real-team throughput.
```

Do all three. The Brynjolfsson rewrite is the most important — it reverses the direction of the mis-cite on the slide and needs to be unmistakable.

### Step 6 — Compose Section 3 in Chapter-7 shape (10 min)

Write the full Chapter-7 Section 3 ("What the literature predicts, and what we actually see") paragraph that the peer manager could substitute for the current "Research evidence" + "Our own number" sections. Use the three rewritten citations plus honest handling of the slide's own-number claim. Chapter 7 is explicit about the shape:

> *"Published effect sizes range widely (Peng 2023: 55% on bounded tasks; Brynjolfsson 2023: 14% avg in support, 34% for juniors; Dell'Acqua 2023: positive inside the frontier, negative outside). Our team's composed read is consistent with a moderate real gain concentrated on well-specified feature workstreams and no gain on data-pipeline work, which matches the outside-frontier pattern."*

Constraints:

- 4–6 sentences.
- Cite one or two anchors (not all five).
- Place the team's own number next to the published range, scope-limited.
- Name the limits of the own-number (per Chapter 3 Caveat 1 — agent-drafted scaffolding can move deployment frequency without underlying work changing).
- Do *not* cite industry surveys (Microsoft WTI, McKinsey) under the research-evidence header.
- Do *not* claim the product-feature retention lift (Chapter-9 boundary).

### Step 7 — Write the peer-review memo (5 min)

At the top of your file, under heading **Peer-review memo**, write a 5–8 line memo addressed to the peer manager. Treat this as the comment you would write before they present to the VP:

- One-sentence verdict (ship / revise / rewrite). This one is a rewrite.
- Three-bullet summary of the most load-bearing citation errors (Brynjolfsson distribution-inversion; Dell'Acqua one-sided reading; Chapter-9 boundary crossing on the retention claim).
- One line pointing to Chapter 5's responsible-citation shape as the calibration.
- One line stating what the slide has to carry that the current draft does not, in the voice of the actual VP ("the VP will ask what task classes the seats are going to — the current slide cannot answer that; the rewrite must").

## Expected output

A single scratch file, roughly two pages, containing:

- The peer-review memo at the top (5–8 lines).
- Claim-by-claim diagnosis under heading **Diagnosis** (six claims, each with the four items from Step 1's header).
- "Our own number" + decision ask diagnosis under **Composite claim — Chapter 5 + 7 check**.
- Three responsible-citation rewrites under **Load-bearing citation rewrites** (Peng, Brynjolfsson, Dell'Acqua), each 1–2 sentences.
- A full Section-3 rewrite in Chapter-7 shape (4–6 sentences) under **Section 3, rewritten**.

If your output is much longer than two pages, you are drifting into producing Exercise 02 in-lab; cut. If much shorter, you are probably skipping one of the six claims or the Section-3 rewrite.

## Checkpoint

Before moving on to Exercise 02 (where you produce **your own** one-page literature digest for Q-review reuse) and Exercise 04 (where you author Section 3 of your real team's one-pager), you should be able to answer **yes** to all four:

- Did you catch at least five of the seven findings, including specifically the Brynjolfsson distribution-inversion (Claim 4, the most important mis-cite) and the Chapter-9 boundary-crossing on the product-feature retention claim (Claim 6)?
- Did each of your three rewrites (Peng, Brynjolfsson, Dell'Acqua) name the study, the task or population, the effect size with direction, and the scope limit — in 1–2 sentences?
- Did your Section-3 rewrite place the team's own number *next to* the published range (not as a claim of consistency with a composite "25% average"), and name the Chapter-3 Caveat-1 attribution limit on the 31% deployment-frequency rise?
- Did your peer-review memo flag Microsoft WTI as belonging in the industry-context paragraph (Chapter 4 / mod-102 territory), *not* under the "Research evidence" header — per Chapter 5's "do not cite industry marketing surveys as if they were peer-reviewed research"?

If any answer is no, re-read Chapter 5's "Reading the five studies together," "Using the literature in the quarterly narrative," and "What *not* to do with the literature" subsections, plus Chapter 7's "Section 3 — What the literature predicts, and what we actually see," before producing your own literature digest in Exercise 02.
