# Lab 03 — Compliance Triage on a Vendor Intake

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 6 (the three regimes in effect in 2026 — EEOC / Title VII + ADA, NYC Local Law 144, EU AI Act Article 6 + Annex III; the three load-bearing questions at team scope; the "What the manager must *not* do" list; the Handoff-A routing to HR / legal), with side-checks against Chapter 2 (the loop's compliance triggers flagged in Exercise 01 Step 6), Chapter 8 (Boundary 2 — legal counsel through HR; the Handoff-A pattern), and the compose points to [`mod-110`](../../mod-110-ai-governance-and-policy-at-team-scope/) (AI governance at team scope more broadly).
**Complements, does not duplicate:** Exercise 05 asks you to produce the full **team-scope compliance checklist for your own team** — AI inventory in the hiring and performance pipeline, trigger assessment per tool, documentation state, routing map, review cadence. This lab hands you four fixed, deliberately mixed-trigger vendor intakes from a fictional recruiter forward so you can calibrate your triage reading on tools with specific regime exposures — including one tool that is *tempting to call out-of-scope* when it is not, one that is *tempting to call in-scope* when it is on the boundary, one that is cleanly high-risk, and one that is cleanly low-risk — before you spend inventory hours on your own team's real tools.

## Objective

For each of four hypothetical vendor intakes forwarded to the manager this quarter, run the three load-bearing questions from Chapter 6 (substantial-assistance verb; demographic-data footprint; jurisdictional scope), classify the tool under each applicable regime (no AEDT trigger / NYC LL 144 / EU AI Act Annex III / ADA accommodation exposure), produce a routing decision (approve at team scope / flag to HR for compliance review / pause and route through legal counsel through HR), and name the specific manager-side action to take now. Then compare against the answer key. Target: **all four regime classifications match the key per tool (or you correctly identify a boundary case and flag for legal determination rather than classifying it yourself), all four routing decisions match the key, and on every tool you default to pausing use until the compliance review completes rather than approving ahead of it**.

## Prerequisites

- Chapter 6 read end-to-end — the three regimes, the three load-bearing questions, the manager-vs-HR-vs-legal division of labour, the "What the manager must *not* do" list, and the worked resume-screening example.
- Chapter 8 skimmed — Boundary 2 (legal counsel through HR) and Handoff A.
- A blank file for your triage output.
- A timer.

**A note on legal scope.** This lab practises the *manager's triage move*. The lab's classifications are calibration exercises against Chapter 6's framing, not legal opinions on specific vendor products. Real tools require real counsel review; the lab answers do not substitute for either. The failure the lab is designed to catch is the *manager-side* error — approving a tool without the compliance review, interpreting the law into own-practice, promising "unbiased" to candidates — not legal errors on scope boundaries, which are counsel's work in any real case.

## The fictional context

> **"Catalog Platform" team, Trellis Marketplace.** 9 engineers (1 staff, 3 senior, 5 mid/junior). Owns the catalog service, the pricing adapter, and the search indexer. Hiring plan: four open requisitions this quarter — two senior engineers, two mid-level engineers — across US-based remote (including candidates located in NYC, California, and Texas), UK-based remote, and remote candidates in two EU member states (Germany and Spain). The team's current interview loop is a redesigned loop under [Exercise 01](../exercises/exercise-01-interview-loop-redesign-under-ai.md) v0.2: phone screen, two technical screens (both AI-permitted with disclosure), one system-design round (AI-permitted with disclosure), one behavioural / cross-functional round, one final. No AEDT currently in the loop; sourcing is recruiter-led with LinkedIn and a referral channel.
>
> **The intake.** The recruiter forwards four vendor demos the manager received over the last week. The vendors' product pages are paraphrased below; the recruiter has flagged all four for the manager's call on whether to proceed with any of them. Finance has indicated that any one of them would fit this year's hiring-tool budget if adopted.

Score each tool against *this team's* actual hiring footprint (US-remote including NYC, UK, EU member states Germany + Spain), not against an idealised stateless hiring context. Jurisdiction is load-bearing and compounds across the three regimes.

## The rubric, before you triage

Pin the three load-bearing questions and the classification options to a scratch file.

```
Three load-bearing questions per tool (Chapter 6):

Q1. Does the tool MAKE, SUBSTANTIALLY ASSIST, or SUBSTANTIALLY INFLUENCE
    an employment decision?
    Verbs matter. "Summarises for a human reviewer to score independently"
    is different from "scores," "ranks," "classifies," "filters above /
    below a threshold." The compliance footprint hinges on this verb.

Q2. What DEMOGRAPHIC DATA does the tool CONSUME, PRODUCE, or INFER?
    Includes features that correlate with protected classes even when the
    tool does not take demographic data as input (EEOC 2023 TA). Name
    patterns, graduation year, employment gaps, address, accent, facial
    expression, speech patterns are all common correlates.

Q3. IN WHICH JURISDICTIONS does the hiring happen? Where do candidates
    live?
    NYC LL 144: jobs in NYC OR candidates located in NYC.
    EU AI Act: AI systems placed on EU market OR outputs used in EU.
    US EEOC/Title VII: US employment decisions broadly.
    ADA: all US employment; concerns on personality/cognitive/video
    analysis especially.

Classification per tool (may trigger multiple):
  N   No AEDT / Annex III / ADA trigger — approve at team scope.
  LL  Likely NYC LL 144 in-scope — annual bias audit, candidate notice
      ≥10 business days, data-source disclosure, published summary. ROUTE.
  EU  EU AI Act Annex III high-risk — Articles 8-15/17 obligations from
      2026-08-02; vendor conformity assessment + deployer logs, human
      oversight, Article 4 AI literacy, Article 50 transparency. ROUTE.
  AD  ADA accommodation exposure — personality/cognitive/video analysis
      concern; reasonable accommodation path required. ROUTE to HR.
  ??  Boundary case — flag to HR for legal determination; manager does
      not classify.

Manager-side action options:
  A  Approve at team scope. Default only for N-classified tools.
  F  Flag to HR for compliance review; HR routes to legal; manager pauses
     the tool's use pending review; falls back to human-only in interim.
  P  Pause and route through HR → legal counsel on a priority path for a
     high-exposure case (candidate complaint, regulator letter, etc.) —
     rare in a triage lab; included for completeness.
```

Chapter 6 is explicit: the manager runs the three questions and routes; the manager does not interpret the law. "Boundary case — flag to HR for legal determination" is a legitimate answer; it is not a dodge.

## Steps

### Step 1 — Set up your triage sheet (3 min)

Create a working file `lab-03-triage.md`. For each tool, create an entry:

```
Tool <letter> — <short name>

Q1 SUBSTANTIAL-ASSISTANCE VERB   : <answer; cite the vendor language>
Q2 DEMOGRAPHIC DATA FOOTPRINT    : <answer; name correlates even when
                                   demographic data isn't explicit input>
Q3 JURISDICTIONS                 : <answer; name every regime triggered>

Classification: N / LL / EU / AD / ??  (may be multiple)
Manager-side action: A / F / P

One-sentence manager reasoning:
```

### Step 2 — Triage Tool A (12–15 min)

#### Tool A — "InterviewLens" — structured-interview scoring from transcripts

> **Vendor product page (paraphrased).** *"InterviewLens scores structured-interview transcripts against your rubric. Upload the recording or paste the transcript; InterviewLens returns a consistency-with-rubric score (0–100), a recommended hire / lean-hire / lean-no-hire / no-hire bucket, and a highlight reel of the moments the AI identified as highest-signal. Our ML model is trained on 1.2M interview transcripts across 400 enterprise customers. Human raters remain in the loop — they see the AI's score alongside their own and can override."*
>
> **Vendor-stated inputs.** Interview transcript text; audio recording if available; the customer's rubric; the role description.
>
> **Vendor-stated outputs.** Consistency score (0–100), hire / lean-hire / lean-no-hire / no-hire bucket, highlight reel.
>
> **Vendor-stated jurisdictional footprint.** Available to customers in US, UK, EU. Vendor claims GDPR and NYC LL 144 compliance; claims a bias audit was completed in 2025.
>
> **Finance note (via recruiter).** "If we approved this, we'd use it on all four requisitions."

Run the three questions. Classify. Decide action. Do not read the answer key yet.

### Step 3 — Triage Tool B (10–12 min)

#### Tool B — "NoteKit" — AI-assisted interviewer-note summarisation

> **Vendor product page (paraphrased).** *"NoteKit sits in your interviewers' workflow. The rater takes notes during the interview; NoteKit groups the notes by rubric criterion at the end of the stage so the rater can review before scoring. NoteKit does not score, rank, or classify candidates — it reorganises the rater's own notes alongside the rubric structure the rater uses. The rater scores independently. NoteKit exports to your ATS in a structured format."*
>
> **Vendor-stated inputs.** The rater's typed notes; the customer's rubric.
>
> **Vendor-stated outputs.** The rater's notes, regrouped under the rubric criteria headers; no score, no classification, no recommendation.
>
> **Vendor-stated jurisdictional footprint.** Available globally.
>
> **Finance note (via recruiter).** "This is the lightweight one — should be straightforward."

Run the three questions. Classify. Decide action.

### Step 4 — Triage Tool C (10–12 min)

#### Tool C — "SkillSignal" — video-based personality and cognitive-signal analysis

> **Vendor product page (paraphrased).** *"SkillSignal is a short, asynchronous assessment candidates complete at home. The candidate records themselves answering five standardised questions on video. Our ML model analyses facial expressions, speech patterns (prosody, pace, word choice), and content to produce a profile across six workplace dimensions: communication, collaboration, adaptability, drive, analytical thinking, resilience. Each dimension is scored 1–5 with a confidence interval. Hiring managers use the profile to inform their hire decision; the profile does not replace human judgement."*
>
> **Vendor-stated inputs.** Candidate's video response (facial, speech, content).
>
> **Vendor-stated outputs.** Six-dimensional profile with 1–5 scores plus confidence intervals.
>
> **Vendor-stated jurisdictional footprint.** US only. Vendor does not publish an LL 144 bias audit on the website; a redacted internal validity study is available on request.
>
> **Finance note (via recruiter).** "Asynchronous assessment would cut phone-screen time 40%. The CFO is particularly interested in this one."

Run the three questions. Classify. Decide action.

### Step 5 — Triage Tool D (10–12 min)

#### Tool D — "ReferenceRadar" — reference-check email drafting and sentiment summarisation

> **Vendor product page (paraphrased).** *"ReferenceRadar helps your recruiter team handle reference checks efficiently. For each reference, ReferenceRadar drafts the outreach email in the recruiter's voice, schedules the call, and — for calls that happen — transcribes the audio and summarises the reference's response under three themes: strengths, growth areas, verification. The summary is for the recruiter and the hiring manager; the recruiter decides what to share with the panel. ReferenceRadar does not score the candidate, does not produce a hire / no-hire recommendation, and does not infer anything about the candidate's protected-class status from the reference's words."*
>
> **Vendor-stated inputs.** Reference contact details; the role the candidate is interviewing for; call audio.
>
> **Vendor-stated outputs.** Drafted email; call transcript; three-theme summary (strengths / growth areas / verification).
>
> **Vendor-stated jurisdictional footprint.** US, UK, EU.
>
> **Finance note (via recruiter).** "Would save the recruiter team 6–8 hours per hire."

Run the three questions. Classify. Decide action. Now compare all four against the answer key.

### Step 6 — Compare against the answer key (10 min)

Read the key below only after you have triaged all four tools.

#### Answer key — Tool A, "InterviewLens"

- **Q1 substantial-assistance verb.** *Scores* the candidate (0–100), *buckets* into hire / lean-hire / lean-no-hire / no-hire, and provides a *highlight reel* the human rater is anchored by. These are substantial-assistance verbs — scoring and classifying — regardless of the vendor's "human raters remain in the loop" framing. Per Chapter 6, "a tool that *scores a candidate* or *ranks candidates*" is categorically different from one that summarises; this is the former.
- **Q2 demographic data footprint.** Consumes transcript content, which carries speech patterns, vocabulary, name mentions, cultural references, and — if audio is included — prosody, accent, speech rate. All of these correlate with protected classes (national origin, race, age, disability status) even when no demographic data is explicit input. EEOC 2023 TA applies directly.
- **Q3 jurisdictions.** Team hires US-remote (including NYC), UK, EU (Germany + Spain). All three regimes trigger: US EEOC / Title VII (and ADA for the content-analysis dimension), NYC LL 144 (candidates in NYC + scoring verb is well within AEDT scope), EU AI Act Annex III (evaluation of candidates is explicitly Annex III).

**Classification: LL + EU + AD (+ EEOC / Title VII monitoring).** The vendor's claim that a bias audit was completed in 2025 is a *vendor-side* assertion; Chapter 6 is explicit that *"the vendor's audit said it was unbiased is not a defence"* and that the deployer's obligations exist independently of the vendor's audit. The vendor's "human raters remain in the loop" framing does not change the substantial-assistance verb, because the human sees the AI's score first and is anchored by it — the LL 144 DCWP final rules and the EU AI Act Annex III deployer obligations apply to systems that *substantially assist* decisions, which includes anchoring effects.

**Manager-side action: F.** Flag to HR for compliance review with the Chapter 6 trigger assessment attached. HR routes to legal counsel for LL 144 scope determination (likely in-scope), EU AI Act Annex III deployer-obligations review (including vendor's conformity assessment documentation — request it in writing; if unavailable, that is itself the review result), and procurement for contract review including data handling and candidate-transcript retention. Pause the tool's use until the review completes; keep the loop running human-only in the interim. The manager does not interpret the DCWP final rules or the Annex III scope boundaries; the manager flags the pattern and routes.

Do **not**: approve for non-NYC candidates ahead of the LL 144 review (the inconsistent-treatment pattern is itself an EEOC exposure); promise the loop is "unbiased" based on the vendor's audit; run bias analyses on protected-class data personally; cite Chapter 6 as legal opinion.

#### Answer key — Tool B, "NoteKit"

- **Q1 substantial-assistance verb.** The vendor states it does not score, rank, or classify. The verb is *reorganise the rater's own notes alongside the rubric structure the rater uses.* That is a summarisation / formatting assist, not a scoring verb. The rater scores independently *after* the regrouping. Per Chapter 6 and the DCWP final rules' typical treatment: a tool that summarises candidate materials for a human to then score independently is typically outside the AEDT scope.
- **Q2 demographic data footprint.** Minimal and indirect — the rater's own notes do not consume demographic data beyond what the rater has already recorded. The vendor handles the notes but does not infer from them. No new demographic inference is introduced.
- **Q3 jurisdictions.** Same team footprint as Tool A — US, UK, EU.

**Classification: N (no AEDT / Annex III / ADA trigger) — with one caveat worth naming.** This is the one tool in the intake that plausibly classifies as outside the three regimes' trigger scopes at the manager-triage level. The caveat is that *"typical" DCWP treatment is a legal determination, not a manager determination*. Chapter 6 is explicit: scope boundaries belong to counsel. A clean triage path on NoteKit is still to flag it to HR with the trigger assessment and let HR confirm (likely in one short exchange with counsel) that the summarisation verb is out of scope — rather than to approve unilaterally. If your organisation has a lightweight path for low-exposure tools (HR partner's judgment with named escalation on disagreement), NoteKit fits that path.

**Manager-side action: F (lightweight) or A if your organisation has established a summarisation-verb carve-out with HR previously.** Default to F if unsure — the cost of the HR exchange is low; the cost of a mis-classified tool that later surfaces as in-scope is high (per Chapter 6's "Treating the compliance work as paperwork rather than practice" common failure). Do **not** approve by assuming the vendor's "we don't score" claim ends the inquiry; verify.

A reasonable co-review co-conclusion with HR: approve for US/UK; separately confirm EU AI Act Article 50 transparency obligations are satisfied by the vendor's product documentation (summarisation systems have Article 50 touchpoints even when not high-risk under Annex III). Document the inventory entry for Exercise 05.

#### Answer key — Tool C, "SkillSignal"

- **Q1 substantial-assistance verb.** *Produces a six-dimensional profile with 1–5 scores and confidence intervals.* The vendor's "profile does not replace human judgement" does not change the substantial-assistance verb — scoring the candidate across six dimensions is substantial assistance, categorically.
- **Q2 demographic data footprint.** Facial-expression analysis, speech patterns (prosody, pace, word choice), and content analysis. Per the EEOC 2022 ADA guidance, this is *the* canonical example of AI assessment that "can disadvantage candidates with disabilities" — speech patterns can be confounded with speech impairments, autism spectrum traits, non-native speakers, deaf / hard-of-hearing candidates, and other protected-class categories. Facial-expression analysis similarly. This is the single most ADA-exposed tool shape named in the 2022 guidance. Correlates with race / national origin / age are also present throughout the model inputs.
- **Q3 jurisdictions.** The vendor claims "US only," but the team hires US-remote (including NYC and California), UK, and EU — so the tool's "US only" would only cover some of the team's requisitions. The uneven coverage is itself a signal: using SkillSignal on US candidates but not on UK / EU candidates creates a differential assessment pattern that is a specific EEOC / Title VII exposure.

**Classification: EU (if deployed on any EU candidate — but vendor states not available there, so not applicable) + LL (NYC candidates, in-scope AEDT by scoring verb) + AD (strongly exposed per EEOC 2022 ADA guidance) + EEOC / Title VII monitoring (differential-treatment exposure from uneven deployment across jurisdictions).** The absence of a published LL 144 bias audit on the vendor's website (vendor offers only a redacted internal validity study on request) is itself an LL 144 compliance gap — the public bias-audit summary is a *requirement* of LL 144, not a nice-to-have.

**Manager-side action: F, with high-exposure framing.** Flag to HR for compliance review with explicit ADA concern raised — this tool is the specific shape (video analysis, facial expression, speech pattern) the EEOC 2022 guidance names. HR routes to legal counsel for a full LL 144 scope + bias-audit-adequacy review (vendor's redacted study is not the LL 144 public bias audit), and runs an ADA-accommodation framework review with HR before any pilot. Pause use; fall back to the current human-only phone screen. Do **not** approve ahead of the review even on the CFO's interest — the compliance exposure is specifically the shape the EEOC named in 2022, and the time-saving case (40% of phone-screen time) is Chapter 6's "Treating the compliance work as paperwork rather than practice" common failure in disguise — a specific trade of compliance posture for recruiter time.

Separately: the vendor's response to a bias-audit publication request will itself inform the review. A vendor that cannot or will not produce the LL 144 public bias audit after request is a vendor the organisation should not contract with for this use, per the LL 144 requirements and per Chapter 6's "Letting the vendor's audit be the full answer" common failure.

#### Answer key — Tool D, "ReferenceRadar"

- **Q1 substantial-assistance verb.** Three distinct verbs across the product's scope: (i) *drafts the outreach email* — a drafting assist, not a scoring verb; (ii) *transcribes the audio* — a transcription assist, not a scoring verb; (iii) *summarises the reference's response under three themes* — a summarisation assist, not a scoring verb. The vendor explicitly states the tool does not score the candidate or produce a hire / no-hire recommendation.
- **Q2 demographic data footprint.** The reference's own words (via transcription) are consumed. The vendor states it does not infer protected-class status from the reference's words. However, reference-content summarisation that themes "growth areas" may surface language that *correlates* with protected-class considerations if the reference themselves uses such language (coded "grit" language, age-adjacent comments, caregiving references). The tool does not *produce* protected-class inference, but it does *propagate* reference-side language the manager would in any case hear.
- **Q3 jurisdictions.** US, UK, EU footprint. EU candidates implicate EU AI Act — but the tool's verb set (draft / transcribe / summarise) is not an Annex III evaluation verb; the summarisation does not assist the hiring decision in the way LL 144's AEDT definition intends.

**Classification: N (no AEDT trigger; not Annex III high-risk by scoring verb) — with Article 50 transparency and GDPR / data-handling flags.** EU AI Act Article 50 transparency applies to synthetic-content and some summarisation tools generally (not specifically high-risk). GDPR applies to the reference's audio and transcript data regardless of AI-Act status — this is a data-handling review, not an AEDT scope question. The reference themselves should also be notified that the call is being recorded and transcribed, per US state recording laws and EU GDPR; this is not a vendor choice, it is a jurisdictional requirement.

**Manager-side action: F (lightweight).** Flag to HR with the trigger assessment. HR confirms the verb set is out of AEDT / Annex III scope; routes to legal for a data-handling / recording-consent / GDPR review and to procurement for the contract (candidate / reference data retention, training-on-your-data clauses). Approve for use after the data-handling review, with the recruiter team trained on the recording-notice obligation. Do **not** approve unilaterally before the data-handling review — "it doesn't score candidates" is the manager's correct classification on the AEDT question, but the data-handling questions are independent.

Separately: inventory this tool for Exercise 05 regardless of the N classification. Chapter 6's Section 5 review cadence requires re-evaluation when any new tool is added — ReferenceRadar should enter the team's AI inventory even though it does not trigger LL 144 or Annex III.

### Step 7 — Diagnose your triage drift (12 min)

Compare your triage sheet against the key. For each classification mismatch, each routing mismatch, and each approve-ahead-of-review decision, write one paragraph:

- **If you approved Tool A for non-NYC candidates ahead of the full review:** this is the specific "dodge the triggers by sub-scoping" failure mode. A differential-treatment pattern (AI scoring in some jurisdictions, human-only in others) is itself a Title VII adverse-impact exposure on the basis of location, and the LL 144 / Annex III triggers do not vanish by not deploying in those jurisdictions — the organisation's broader hiring consistency is also a factor. Fall back to human-only everywhere during the review.
- **If you classified Tool B as in-scope under LL 144 or Annex III:** the summarisation / regrouping verb is Chapter 6's canonical "typically outside AEDT scope" shape. You may have been correct to flag to HR anyway (the triage lab's "F (lightweight)" is the right default under uncertainty), but if you classified it as LL 144-in-scope with certainty, re-read Chapter 6's "The NYC Local Law 144 frame: bias audits and candidate notice" section — the DCWP final rules narrow the scope to tools using statistical / ML / AI to *issue a simplified output* that *substantially assists* the decision; a summariser that regroups the rater's own notes does not issue an output on the candidate.
- **If you classified Tool C's ADA exposure as a nice-to-have flag rather than the primary classification:** the EEOC 2022 ADA guidance names video / facial / speech analysis as *the specific shape* of concern. Chapter 6 restates this: *"the 2022 guidance on the ADA and AI adds a specific concern: AI systems that assess traits like personality, cognitive ability, or communication style can disadvantage candidates with disabilities. The guidance names specific concerns — e.g., video analysis that scores facial expressions or speech patterns is especially exposed."* ADA is primary, not secondary, on SkillSignal. If you under-weighted it, the pre-AI instinct (ADA concerns = accommodations, not screening-tool concerns) has drifted into the AI-era triage; re-read the 2022 guidance framing.
- **If you approved any tool ahead of the compliance review on the grounds of recruiter time saved or finance interest:** Chapter 6's "Common failure modes" names *"Treating the compliance work as paperwork rather than practice"* and *"Letting the vendor's audit be the full answer"* explicitly. The CFO's interest and the recruiter's time are legitimate business signals; they are not reasons to bypass the compliance review. The manager's job is to flag and route; if the review takes six weeks, the loop runs human-only for six weeks.
- **If you classified Tool D as high-risk under Annex III because it touches reference audio:** the Annex III scope is *recruitment and selection decisions*, not any AI used anywhere in hiring. Reference-call summarisation is a summarisation verb; it does not evaluate the candidate for selection in the Annex III sense. The data-handling exposure under GDPR is real but is a separate review, not an Annex III one. Separating the AEDT / Annex III scope from the data-handling / GDPR scope is the manager-side clarity the triage lab is designed to build.
- **If you cited Chapter 6 as legal opinion in any of your classifications:** Chapter 6 is explicit about not doing this. The chapter frames team practice; the specific tool-in-scope determinations are counsel's work through HR. Your triage move is the three-question assessment + routing, not the legal determination.

### Step 8 — Draft the HR / legal routing note for Tool A from memory (10 min)

Close your file for a minute. Draft the short note (3–5 sentences) you would send to your HR partner on Tool A, as the Handoff-A pattern from Chapter 8. The note should name: the tool; the three-question assessment result; the specific regimes you believe trigger (framed as "likely," not as a legal determination); the specific manager-side action you've taken (pause use); the specific HR-side question (coordinate legal review for scope + conformity + contract). Compare against the shape below:

```
[To: HR partner]

Recruiter forwarded a vendor demo for InterviewLens, a tool that scores
structured-interview transcripts and buckets candidates into
hire/lean-hire/lean-no-hire/no-hire. Running the Ch. 6 three-question
assessment: the tool substantially assists employment decisions (scoring
+ bucketing); consumes transcript / audio content with correlates to
protected classes (per EEOC 2023 TA); our footprint covers US (incl.
NYC), UK, and two EU member states. My read is this is likely in-scope
under NYC LL 144 and EU AI Act Annex III, plus Title VII monitoring; the
vendor's claimed 2025 bias audit does not change the deployer-side
obligations.

I've paused the vendor conversation and will run the current loop
human-only until the review completes. Can you coordinate the legal
review for LL 144 scope confirmation, Annex III conformity-assessment
documentation from the vendor, and contract review including candidate-
transcript data handling? Happy to supply the trigger assessment write-
up and the vendor's materials.

Thanks —
```

The note is short, specific, framed as *likely* triggers (not legal determinations), and routes the legal-determination question to the right owner. The manager's pre-work was the three-question assessment; HR's work is coordinating the legal review. Chapter 8's Handoff-A pattern is exactly this shape.

### Step 9 — Re-triage Tool C from memory (5 min)

Close your file. Re-triage Tool C from memory — the three questions, the classification, the action. The specific failure mode to catch yourself on: under-weighting ADA. The EEOC 2022 guidance names video / speech / facial analysis as the canonical concern; if your second pass does not centre ADA, the pre-AI instinct ("ADA is for existing employees asking for accommodations") has drifted into the hiring-AI triage. Re-read Chapter 6's ADA paragraph before running Exercise 05.

## Expected output

A scratch file, roughly a half-page per tool, containing:

- Four triage sheets: three-question answers with specific evidence, classification (letter codes), routing action, one-sentence reasoning.
- A diagnostic paragraph per classification mismatch, routing mismatch, or approve-ahead-of-review decision.
- A short HR / legal routing note drafted from memory on Tool A.
- A second-pass triage on Tool C with specific attention to the ADA framing.

Something like:

```
Tool A — InterviewLens
  Q1 verb      : SCORES + BUCKETS + highlight reel → substantial assistance
                 regardless of "human in the loop" framing (anchoring effect)
  Q2 data      : transcript text + audio → speech patterns, prosody, name
                 mentions, cultural refs → EEOC 2023 TA correlates
  Q3 jurisdic. : US (NYC + ADA), UK, EU (Germany, Spain) → all three regimes
  Classification: LL + EU + AD (+ EEOC monitoring)
  Action: F — pause use; HR coordinates legal review for LL 144 scope + EU
          AI Act Annex III conformity + contract/data handling.
  Reasoning: vendor's audit is vendor-side; deployer obligations independent.
  ✅ match.

Tool B — NoteKit
  Q1 verb      : REGROUPS rater's own notes → summarisation, not scoring
  Q2 data      : rater's notes only; no new demographic inference
  Q3 jurisdic. : US, UK, EU
  Classification: N (with Art. 50 transparency flag for EU)
  Action: F (lightweight) — flag to HR to confirm summarisation verb is out
          of scope; approve post-confirmation.
  Reasoning: DCWP final rules narrow AEDT to simplified-output tools that
             substantially assist; summariser regrouping own notes is not.
  ✅ match.

Tool C — SkillSignal
  Q1 verb      : PRODUCES 1–5 scores across 6 dimensions → substantial
                 assistance regardless of "doesn't replace human" framing
  Q2 data      : facial expression + speech patterns + content → ADA primary
                 exposure per EEOC 2022 guidance; also race/national origin/
                 age correlates throughout
  Q3 jurisdic. : vendor claims US-only; deploying US-only on a multi-
                 jurisdiction loop creates differential-treatment exposure
  Classification: LL + AD (primary) + EEOC monitoring
  Action: F with HIGH-EXPOSURE framing; pause use; HR routes to legal for
          full LL 144 + ADA framework review before any pilot.
  Reasoning: this is the specific shape the EEOC 2022 guidance names. No
             public LL 144 bias audit on vendor website is itself an LL 144
             compliance gap.
  ✅ match.

Tool D — ReferenceRadar
  Q1 verb      : DRAFT email + TRANSCRIBE call + SUMMARISE reference →
                 three separate summarisation verbs; no scoring verb
  Q2 data      : reference's words consumed via transcription; vendor claims
                 no protected-class inference
  Q3 jurisdic. : US, UK, EU → GDPR + state recording-consent laws apply
                 independent of AEDT / Annex III
  Classification: N (AEDT / Annex III); data-handling + Art. 50 flags
  Action: F (lightweight) — approve after data-handling review and
          recording-notice training for recruiter team.
  Reasoning: AEDT scope is selection decisions; summarisation of references
             is not selection. GDPR / recording consent is separate review.
  ✅ match.

Drift notes:
  First-pass on Tool C: classified LL as primary, ADA as secondary.
  Re-read Ch. 6 ADA paragraph: video/facial/speech analysis is the canonical
  EEOC 2022 ADA concern — the specific shape named. ADA is primary; LL 144
  composes. The pre-AI instinct treats ADA as accommodations-only; the 2022
  guidance expanded it to screening-tool design.
```

## Checkpoint

Before moving on to Exercise 05 (full team-scope compliance checklist on your own tools) and Exercise 01's Step 6 (flagging compliance triggers in your loop), you should be able to answer **yes** to all six:

- Did you reach the **LL + EU + AD** classification on Tool A despite the vendor's "human in the loop" framing and 2025 bias-audit claim?
- Did you recognise Tool B as the one summarisation-verb case in the intake and *still* default to flagging to HR (lightweight) rather than approving unilaterally?
- Did you centre **ADA as primary** on Tool C per the EEOC 2022 guidance, and treat the CFO's interest + recruiter time-saving as legitimate-but-not-overriding business signals rather than as reasons to bypass compliance?
- Did you keep Tool D's **AEDT / Annex III scope** separate from its **data-handling / GDPR / recording-consent** exposure, and route the two to the right review paths?
- On every tool, did you default to **F (flag + pause)** rather than **A (approve at team scope)** when uncertain, matching Chapter 6's "the compliance work is practice, not paperwork" framing?
- Did you resist citing Chapter 6 as a legal opinion in any classification, and keep all scope-boundary questions framed as "likely" triggers routed to counsel through HR?

If any answer is no, re-read Chapter 6 end-to-end — the three load-bearing questions, the EEOC 2022/2023 guidance paragraphs, the LL 144 and EU AI Act Annex III sections, the "What the manager must *not* do" list, and the "Common failure modes" list — and re-run the affected tool's triage before starting Exercise 05 on your real team's AI inventory.
