# Lab 02 — Article 14 and 50 Triage on Four Composite Workflows

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 4 (the Article 14 deployer reading; the Article 14 workflow sheet's eight fields; Article 50's four most-commonly-live deployer obligations — 50(1), 50(3), 50(4), text-published-to-inform-the-public; the Article 50 interaction sheet; the five triggers for routing to counsel; GPAI deployer practice), with side-checks against Chapter 1 (scope boundary against counsel), Chapter 3 (how Article 4 literacy ties to Article 14 competence), and Chapter 7 (how in-scope workflow sheets land in the upward packet).
**Complements, does not duplicate:** [Exercise 01](../exercises/exercise-01-nist-ai-rmf-govern-to-team-practice.md) picks up the Article 14/50 trigger list as the GOVERN 1.4 row of the crosswalk, and [Exercise 05](../exercises/exercise-05-upward-evidence-packet-for-governance-program.md) composes Article 14/50 sheets into the upward packet — but neither exercise asks you to **triage** a workflow for sheet-authoring and counsel-routing decisions before the sheets exist. This lab hands you four composite workflow descriptions and asks the specific decisions a manager has to make *before* the Article 14/50 practice runs: does the workflow need a sheet? which sheet? does it fire the counsel-trigger list? what composition path does it follow? A manager who can triage in 10 minutes per workflow is a manager whose sheets will be filled from the right inherited artifacts; a manager who guesses on triage will produce sheets that the architect's review re-does.

## Objective

For each of four composite workflow descriptions, produce a triage sheet with: (i) **classification signal** — what Chapter 4 reading says is the *likely* legal-position outcome (counsel decides; you flag the signal); (ii) **Article 14 sheet needed?** — yes/no/pending-counsel, with the field-by-field composition plan if yes; (iii) **Article 50 sheet needed?** — yes/no/pending-counsel, with the specific sub-paragraph (50(1), 50(3), 50(4), text-published-to-inform-the-public) and the disclosure-text ownership; (iv) **counsel triggers fired** — which of Chapter 4's five trigger lines; (v) **upstream / downstream composition** — which prior-module artifacts the sheet(s) will inherit from (mod-103 Ch. 5; mod-106 HITL / delegation ladder / tool-authorisation; mod-107 anti-atrophy; mod-109 trace-preservation / routing); (vi) **what the manager does *not* do**. Then compare against the answer key.

Target: **you call the classification signal correctly on at least three of four workflows (counsel sets the final; you read the signal); you fire the correct counsel-trigger pattern on all four; you resist the two specific drifts — treating "internal-only" as a free-pass from Article 50 when the workflow touches an affected person, and treating "high-risk-adjacent" as grounds for the manager to interpret Annex III rather than route.** These are the two reading drifts Chapter 4 flags as common.

## Prerequisites

- Chapter 4 read end-to-end — the deployer reading of Article 14 (five operational translations: named oversight role, competence and training, authority to override, support, automation-bias mitigation); the Article 14 workflow sheet's eight fields; Article 50's five sub-paragraph obligations and which fall on providers vs. deployers; the Article 14 and Article 50 sheet shapes; *"Composition with the rest of the track"*; the five triggers for routing to counsel; the GPAI-deployer practice. Keep the Chapter 4 trigger list and the two sheet templates on a scratch page; you will score against them.
- Chapter 3 skimmed — the role-tier segmentation and the Article 4 competence tie-in (Article 14 competence inherits from Article 4 literacy).
- Chapter 7 skimmed — the ownership-boundary table and the Article 14/50 sections of the upward packet.
- A blank file for your triage sheets.
- A timer.

## The fictional context

Same team as [Lab 01](lab-01-govern-crosswalk-cell-grading-on-a-composite-artifact-list.md) — the "Claims Intelligence" team at Northstar Mutual.

> **"Claims Intelligence" team, Northstar Mutual (EU-headquartered personal-lines insurer, Dublin).** 10 engineers, 1 manager. Owns `claims-router`, `claims-intelligence-platform`, `ClaimsPilot` (internal RAG over policy/coverage docs for claims-handlers), and `UWCopilot` (underwriting-assist for human underwriters — counsel classified adjacent-to-high-risk under Annex III category 5(b) on 2026-07-02 with an Article 14 workflow sheet at `drive://northstar-claims/article-14-sheets/uwcopilot-v3.2.md`). Four new workflow proposals are in the roadmap for Q1 2027. The manager has to triage each before the Q4 2026 packet closes so the gap register and the Q1 planning are coherent. Counsel (Privacy & AI counsel) has a two-week turnaround on classification questions. `ai-risk-engineer` is engaged on UWCopilot's fairness eval. Pinned artifacts: mod-103 accountability contract, mod-103 review checklist, mod-106 routing matrix + HITL + delegation ladder + tool-authorisation policy, mod-107 anti-atrophy practice, mod-109 incident runbook + routing contract + trace-preservation checklist, Chapter 3 Article 4 literacy curriculum.

Triage each workflow *as if you are the team manager, writing the triage sheet to hand to counsel together with the formal classification request*. Your job is to flag cleanly, compose existing artifacts into the sheet drafts, and name what you do *not* do.

## The four composite workflow proposals

### Workflow A — `ClaimsExplain`: AI-generated applicant-facing claim-decision explanations

> **Proposal from Product (2026-11-05).** When a claim decision is issued — approve, deny, or partial-settle — the applicant receives a decision letter today, human-authored by the claims-handler from a template library. Product wants to pilot an AI-generated explanation: the claims-handler reviews and sends. The AI model (Claude Sonnet via the team gateway) reads the claim file, the policy terms, the decision rationale captured by the claims-handler, and drafts a plain-English explanation customised to the applicant. The claims-handler can accept, edit, or reject the draft. The sent letter is delivered via email or post. Volume: ~3,500 letters/month across the four Northstar geographies (IE, UK, DE, NL). Decisions that deny or partial-settle require the explanation; approvals are a brief confirmation. The claims-handler's current review checklist (mod-103 v2.3) does not yet have an AI-generated-content row. The retention policy for the letter is seven years per the firm's claims records policy.

### Workflow B — `InternalWikiPilot`: AI assistant over the team's internal engineering wiki

> **Proposal from the team's staff engineer (2026-11-08).** The team maintains a ~400-page engineering wiki (architecture decisions, on-call runbooks, deployment procedures). The staff engineer proposes a Claude-powered RAG assistant over the wiki, accessible to the ten engineers on the team via the Claude for Enterprise gateway. Use case: the IC asks *"what's the current on-call-escalation policy for p99 latency incidents on the claims-router?"* and gets a summarised answer with citations. No customer data goes into the index; only engineering content. Only team members have access. The team's data-and-IP matrix (Chapter 6 v1.3) covers *Internal (non-sensitive)* data on Claude for Enterprise as **allowed**. The firm's AI-governance program has flagged no concerns on this class of workflow.

### Workflow C — `HandlerCoach`: AI-enhanced call-centre tooling with voice tonality analysis

> **Proposal from Claims Operations (2026-11-11), co-authored with the Workforce-Experience team.** The claims-call-centre handles ~12,000 inbound calls/month. Operations proposes a tool that (a) transcribes the call in real time (an existing capability), and (b) analyses the handler's voice tonality and pacing against a bank of "high-empathy / low-empathy" examples derived from supervisor-scored historical calls — producing a per-call "empathy signal" on the supervisor's dashboard for coaching conversations with the handler. The applicant (the caller) is not told the tonality analysis is occurring; the handler is told as part of their onboarding. Operations frames this as *"workforce development, not surveillance."* The vendor providing the tonality-classifier is a US-based start-up with a standard enterprise contract; residency is US with EU subprocessors. No decision is made *to the applicant* on the tonality signal; the signal only feeds supervisor coaching.

### Workflow D — `UWCopilot-NA`: UWCopilot extension to the North American market

> **Proposal from Business Development (2026-11-14).** UWCopilot (the existing adjacent-to-high-risk underwriting-assist workflow for the EU market, with the active Article 14 sheet) has been running smoothly for six months. Business Development wants to extend it to the US (New York, California, and Texas) and Canada (Ontario, Quebec), where Northstar has subsidiaries. The workflow design is unchanged: AI drafts, human underwriter decides. The underwriting team in the US reports to a different legal entity (Northstar NA, Inc.); the Canadian underwriting team reports to Northstar Canada Ltd. The data flows are: applicant file enters the model (US applicants' data stays in US tenancy; EU applicants' data stays in EU tenancy; Canadian stays in CA). The firm has a dedicated US compliance partner at the parent legal-and-compliance team and a separate Canadian compliance partner.

## The triage matrix, pinned

Chapter 4's five triggers to counsel (paraphrased from *"The triggers for routing to counsel"*):

```
TC1 — New workflow plausibly within Annex III (employment, education, credit,
      essential-service access, law enforcement, border control, justice,
      critical infrastructure). Default: flag and ask.
TC2 — Existing workflow changes in a way that could change its classification
      (new data sources, new decision authority, new population of affected
      persons, pilot → production).
TC3 — Vendor change that could affect classification (model swap, new provider,
      new vendor disclosure).
TC4 — Affected-person request implicating Article 50 ("is this AI?").
TC5 — Regulator-facing communication or request.
```

Article 50 sub-paragraphs most commonly live for a deployer:

```
50(1) — AI-system-to-natural-person interaction (deployer carries provider's
        disclosure to the user).
50(3) — Emotion-recognition or biometric-categorisation systems (deployer informs
        affected persons).
50(4) — Deep-fake / artificially-generated-or-manipulated image/audio/video; and
        text-published-to-inform-the-public (deployer discloses).
```

Article 14 workflow sheet fields (Chapter 4):

```
1. Workflow name + counsel classification + sign-off date
2. Named oversight role (+ named persons + LMS curriculum link)
3. Decision points (what, information shown, decisions available, time budget)
4. Override mechanism (how to decline / override; mod-106 delegation ladder ref)
5. Automation-bias mitigation (review-checklist items, standards-as-code,
   Article 4 literacy modules)
6. Trace preservation (mod-109 trace-preservation checklist ref)
7. Escalation path (mod-109 routing contract ref)
8. Change log
```

Article 50 interaction sheet fields (Chapter 4):

```
1. Workflow name + Article 50 sub-paragraph + counsel sign-off
2. Disclosure text (exact wording, counsel-approved)
3. Where the disclosure appears (UI, document, communication; screenshot/link)
4. Verification (automated check, periodic sampling, process gate)
5. Exemption basis if any (counsel-approved rationale)
6. Change log
```

## Steps

### Step 1 — Set up your triage sheet (3 min)

Create a working file `lab-02-triage-sheets.md` with this template, repeated once per workflow:

```
Workflow <letter>: <one-line description>

(i)   Classification signal        : likely <high-risk / adjacent / limited-risk /
                                      Annex III category X / outside regulated use-case>
      Rationale                   : <one or two sentences — what Chapter 4 reading says
                                     about the shape; counsel sets the final>
(ii)  Article 14 sheet needed?    : YES / NO / PENDING-COUNSEL
      If YES, composition plan   :
        Field 2 (oversight role)  : <inherited from mod-103 Ch. 5 ...>
        Field 3 (decision points) : <inherited from mod-106 HITL ... + workflow-specific>
        Field 4 (override)        : <inherited from mod-106 tool-authorisation / delegation>
        Field 5 (auto-bias mit.)  : <inherited from mod-103 review checklist + Ch. 3 lit.>
        Field 6 (trace)           : <inherited from mod-109 trace-preservation checklist>
        Field 7 (escalation)      : <inherited from mod-109 routing contract>
(iii) Article 50 sheet needed?    : YES / NO / PENDING-COUNSEL
      If YES                     :
        Sub-paragraph             : 50(1) / 50(3) / 50(4) / public-interest-text
        Disclosure text owner     : counsel (always)
        Where disclosure appears  : <UI / letter / audio preamble / ...>
        Verification path         : <automated check / sampling / process gate>
(iv)  Counsel triggers fired     : TC1 / TC2 / TC3 / TC4 / TC5 (one or more)
      Specific ask to counsel   : <bounded ask per Ch. 4 reading — flag, not interpret>
(v)   Upstream / downstream       :
      Prior-module composition  : <mod-103 ..., mod-106 ..., mod-107 ..., mod-109 ...>
      New team artifact needed  : <if any — e.g., new mod-103 checklist row>
(vi)  What the manager does NOT do: <one or two bullets — the scope-boundary line>
```

Time yourself. Target per workflow: 10–12 minutes. If you spend more than 15 on one, note the drift and move on; Step 6 diagnoses it.

### Step 2 — Workflow A (10–12 min)

Triage Workflow A (`ClaimsExplain`). Do not look at the key yet. The specific tempting miss: this is an *internal-facing* draft that a human sends — so it may feel Article-50-free. Look again at the Article 50 sub-paragraphs.

### Step 3 — Workflow B (10–12 min)

Triage Workflow B (`InternalWikiPilot`). The specific tempting miss: a team-only internal productivity tool with no customer data looks like a no-sheet, no-trigger workflow. Check whether that reading is clean against Chapter 4.

### Step 4 — Workflow C (10–12 min)

Triage Workflow C (`HandlerCoach`). The specific tempting miss: Operations frames this as "coaching, not surveillance" and the applicant is not affected directly. Read Article 50's sub-paragraphs carefully.

### Step 5 — Workflow D (10–12 min)

Triage Workflow D (`UWCopilot-NA`). The specific tempting miss: UWCopilot already has an Article 14 sheet and a classification — so a geography extension looks like no new work. Check Chapter 4's trigger list.

### Step 6 — Compare against the answer key (15–20 min)

Read the key below only after you have triaged all four.

#### Answer key — Workflow A (ClaimsExplain)

- **(i) Classification signal.** **Pending counsel — most likely *limited-risk* with a live Article 50 sub-paragraph obligation.** Rationale: this is not Annex III category 5(b) (creditworthiness evaluation) — that was UWCopilot; this is explanation of a claim decision, which is a *communication* workflow to the applicant. The claim-decision itself is a human decision; the AI drafts the explanation. However, Article 50's text-published-to-inform-the-public sub-paragraph specifically covers AI-generated or -manipulated text *"published to inform the public on matters of public interest"* with specific exemptions (e.g., human-reviewed editorial content). A one-to-one applicant letter may or may not meet that sub-paragraph's scope — counsel decides. Independent of 50(4), many EU and UK data-protection frames (GDPR Articles 13/14/22 on automated decision-making and transparency) separately may attach — again, counsel.
- **(ii) Article 14 sheet needed?** **PENDING-COUNSEL — probably no**, because the human claims-handler is the decision-maker on the letter's content (edit/accept/reject) and the underlying claim decision is a human decision that the AI explains rather than makes. If counsel classifies the workflow as high-risk or adjacent (unlikely), the sheet is composed: oversight role = claims-handler + review checklist; decision points = draft-review-send; override = reject or edit; auto-bias mitigation = new mod-103 checklist row for AI-authored content (the checklist currently has no such row — a gap); trace = mod-109 trace-preservation; escalation = mod-109 routing.
- **(iii) Article 50 sheet needed?** **YES, pending counsel confirmation of the sub-paragraph.** Most likely **Article 50(4) text-published-to-inform-the-public** or an adjacent GDPR disclosure. Sub-paragraph pending counsel; disclosure text owner is counsel; disclosure appears in a letter footer or opening line; verification is a process gate on the template (the letter cannot be sent without the disclosure embedded). Counsel will also assess whether the human-review exemption applies and how to word disclosure if it does not.
- **(iv) Counsel triggers fired.** **TC1** (new workflow — *"when a new workflow enters the team's roadmap that is plausibly within Annex III"* reads broadly; for safety, any new applicant-facing AI touches TC1 as a flag). **TC2 adjacent** if ClaimsExplain is a variation of an existing claims-letter workflow that changes AI involvement. Bounded ask to counsel: *"ClaimsExplain pilot adds AI-drafted applicant-facing claim-decision explanations with human handler review-and-send. Please confirm: (a) is this within any Annex III category or GDPR Article 22 automated-decision scope? (b) which Article 50 sub-paragraph applies to the letter text and does the human-review exemption apply? (c) what disclosure text, if any, must appear in the letter? Target pilot start: Q1 2027. Decision needed by 2026-12-15."*
- **(v) Upstream / downstream.** mod-103 Ch. 2 **adds a new review-checklist row** for AI-authored applicant-facing content (a Chapter 2 crosswalk gap also surfaces here — GOVERN 1.2). mod-109 trace-preservation applies; a new specific trace element may be needed — the draft, the handler's edits, the sent version. The team's Chapter 6 data-matrix needs to confirm that applicant-file content into the model is permitted under the firm's data-class policy; applicant records are typically Restricted class and the matrix cell is likely conditional pending handler-only access + tenancy constraints.
- **(vi) What the manager does *not* do.** **Does not draft the Article 50 disclosure text.** **Does not decide whether GDPR Article 22 applies.** **Does not pilot the workflow before counsel's classification and disclosure sign-off.** Does not assume "human review" = "Article 50 exempt" without counsel confirming the sub-paragraph.

#### Answer key — Workflow B (InternalWikiPilot)

- **(i) Classification signal.** **Outside regulated use-case territory.** Rationale: internal-only, team-only access, engineering content only, no customer data, no applicant data, no decision affecting a natural person. Chapter 4 names *"many engineering teams will find their own workflows are not high-risk — internal productivity use of AI coding assistants on non-regulated code is typically outside Annex III"* — this fits.
- **(ii) Article 14 sheet needed?** **NO.** Chapter 4: *"the manager's obligation in that case is not to run an Article 14 practice; it is to be able to produce evidence that the classification was considered and to flag any drift."* The classification-was-considered evidence is a brief note in the Q4 upward packet; the drift-flag trigger exists if the workflow later expands scope.
- **(iii) Article 50 sheet needed?** **NO.** No interaction with a natural person outside the team; no generated content leaving the team; no deep-fake; no emotion-recognition; no biometric categorisation; no public-interest text. (If the wiki's content later is used to generate customer-facing content, that is a *new workflow* — TC1/TC2 fires.)
- **(iv) Counsel triggers fired.** **None** on current scope. A proactive note to the governance partner naming the workflow as *outside-Annex-III-and-outside-Article-50* is useful documentation; the upward packet's crosswalk GOVERN 1.4 row and the Chapter 2 example-row pattern cover this. If scope expands (e.g., *"the wiki assistant should also answer customer-handler questions over the policy docs"*), re-triage.
- **(v) Upstream / downstream.** mod-106 **tool-authorisation policy** — confirm Claude for Enterprise is on the approved tool list for Internal data class (Chapter 6 matrix). mod-103 **review checklist** — no specific new row (engineering content use is covered by the existing checklist). Chapter 3 **Module B** (team-specific AI stack walkthrough) — update to mention `InternalWikiPilot` once live, with its C5 data-handling constraints.
- **(vi) What the manager does *not* do.** **Does not open a counsel ticket for a routine internal productivity tool.** Does not create an Article 14 workflow sheet "just to be thorough" (sheet-authoring where not needed inflates the packet and dilutes the signal on real in-scope workflows). Does not promise more to the governance partner than the workflow does.

#### Answer key — Workflow C (HandlerCoach)

- **(i) Classification signal.** **Likely high-risk under Annex III AND a live Article 50(3) obligation.** This is the specific workflow shape the "coaching, not surveillance" framing is designed to mask. Rationale (Chapter 4 reading; counsel confirms):
  - **Annex III dimension.** Workforce-experience / employment-management AI systems are named in Annex III (*"employment, workers management, and access to self-employment"* reads onto systems used to *"monitor and evaluate the performance and behaviour of persons"* in employment contexts). An empathy-signal per call that feeds supervisor coaching is a performance-evaluation signal regardless of the framing. Counsel decides whether this specific design hits the category; the manager flags.
  - **Article 50(3).** Emotion recognition and biometric categorisation systems carry an Article 50(3) deployer obligation: *"deployers must inform natural persons of operation of such systems."* Voice tonality analysis as *"empathy signal"* is an emotion-recognition system under the Act's definition in Article 3; Article 50(3) attaches. The handler is told at onboarding (which may or may not satisfy "informed" as the Act requires — counsel decides); the applicant (the caller) is *not told*, and the handler's voice is being analysed, not the applicant's — so the natural person whose emotion is being recognised is the handler, not the caller. The Article 50(3) obligation attaches to the handler.
- **(ii) Article 14 sheet needed?** **YES if counsel confirms Annex III** — which is the likely outcome. Composition: oversight role = supervisor + Workforce-Experience partner (new role for this workflow — not inherited; the mod-103 Ch. 5 accountability contract may need extension); decision points = none *to the applicant*, but the empathy signal materially influences handler performance reviews, so the oversight is *on the signal's use in performance management* (which is mod-108 territory, not mod-106 — flag to Chapter 7 cross-reference). Override = supervisor can discount the signal in a coaching conversation; the handler can dispute per the firm's performance-management grievance process (mod-108 cross-reference). Auto-bias mitigation = specific training for supervisors on automation-bias in empathy signals; reviewer-tier Article 4 literacy; new mod-107 anti-atrophy consideration (do supervisors still coach well when the signal is absent?). Trace = mod-109 trace-preservation + the empathy-model inputs and outputs retained per employment-records policy. Escalation = mod-109 routing with a specific HR partner addition.
- **(iii) Article 50 sheet needed?** **YES.** Sub-paragraph **50(3)** — emotion recognition. Disclosure text owner: counsel. Disclosure appears in handler onboarding + per-shift reminder in the handler dashboard. Verification: process gate on the dashboard (empathy signal is hidden until handler confirms acknowledgement).
- **(iv) Counsel triggers fired.** **TC1 (new workflow plausibly within Annex III — employment-related performance evaluation)**. **Also route to HR / employment counsel specifically.** Also implicates GDPR (profiling of an employee), works-council / employee-representative notification obligations in some jurisdictions (DE, NL in particular — Northstar operates in both), and potentially sector-specific telephony-recording law. Bounded ask: *"HandlerCoach pilot proposes voice-tonality analysis producing a per-call empathy signal for supervisor coaching. (1) Is this within Annex III (employment / performance evaluation)? (2) Does Article 50(3) attach and what disclosure to the handler? (3) Does the vendor's US tenancy + EU subprocessors meet the data-flow requirements for employee data from DE, NL, IE, UK? (4) Works-council / employee-representative notification required in DE and NL? (5) Does the firm's existing employee-monitoring policy cover this or does it need extension?"*
- **(v) Upstream / downstream.** mod-108 performance-management framing — likely substantial changes needed. mod-103 accountability contract — the supervisor's role in acting on the signal may need a new clause. mod-106 tool-authorisation — the vendor's enterprise contract and data residency need procurement review. Chapter 6 data policy — employee voice-call data is restricted at minimum; the vendor's clause-reader and model-card entries need to be filled before the pilot. Chapter 7 upward packet — this workflow probably needs its own section or a specific gap-register entry given how many triggers fire.
- **(vi) What the manager does *not* do.** **Does not accept "coaching, not surveillance" as a counsel substitute.** Does not pilot before counsel + HR + works-council processes clear. Does not assume the caller's lack of exposure makes Article 50 moot — Article 50(3) protects the handler, not the caller, in this design. Does not negotiate directly with the vendor on data residency; procurement + counsel own that.

#### Answer key — Workflow D (UWCopilot-NA)

- **(i) Classification signal.** **Existing Annex III classification applies only to the EU workflow.** The US and Canada extensions are *outside EU AI Act territorial scope* for most purposes (the Act applies to AI systems *placed on the EU market or used in the EU*, with some extraterritorial reach — counsel assesses). However, each jurisdiction has its own regime:
  - **US (NY, CA, TX)** — NYC Local Law 144 (automated-employment-decision tools — not applicable here; UW is not employment), state-specific lending-discrimination statutes (ECOA, FCRA, various state UDAP regimes), NAIC guidance on insurance AI (NAIC Model Bulletin 2023-01), state-by-state insurance regulator positions. Specifically relevant to this workflow: CA Insurance Code, NY DFS Insurance Circular Letter on AI, TX Department of Insurance guidance.
  - **Canada (ON, QC)** — PIPEDA, Quebec Law 25, OSFI guidance (if applicable to Northstar Canada), AIDA (Bill C-27) status as of the triage date.
- **(ii) Article 14 sheet needed?** **The existing EU sheet continues to apply for EU operations.** For US and Canada operations, the question is whether the *equivalent compliance regimes* require a parallel artifact. Counsel decides; the shape of the EU Article 14 sheet is likely usefully portable but is not automatically a compliance artifact for the other jurisdictions. **Expect a parallel artifact per jurisdiction**, mapped to each regulator's expectations, authored with each jurisdiction's compliance partner.
- **(iii) Article 50 sheet needed?** **Not for EU (internal workflow — EU sheet already notes "n/a").** For US / Canada, equivalent transparency / disclosure expectations under NAIC bulletin, state insurance regulators, PIPEDA, Quebec Law 25 may apply — counsel assesses per jurisdiction.
- **(iv) Counsel triggers fired.** **TC2 (existing workflow changes in a way that could change its classification — expansion from pilot to production **and** new population of affected persons).** Also counsel-equivalent routes in each jurisdiction (US compliance partner + Canadian compliance partner — the firm has both). Bounded ask: *"UWCopilot (adjacent-to-high-risk under Annex III 5(b); EU Article 14 sheet v3.2 live) proposes extension to US (NY, CA, TX) and Canada (ON, QC) operations. (1) EU: does the extension affect the EU classification? Confirm no. (2) US: does the workflow require registration / disclosure / model-governance filings under NAIC Model Bulletin, NY DFS circular, CA / TX insurance regulator positions? (3) Canada: PIPEDA, Quebec Law 25 obligations? Any OSFI touchpoints? (4) Are the data-flow arrangements (US data stays in US tenancy, EU in EU, CA in CA) compliant with each jurisdiction's cross-border transfer rules? (5) Is a parallel Article-14-equivalent artifact needed per jurisdiction and what shape?"*
- **(v) Upstream / downstream.** mod-111 vendor registry — tenancy per jurisdiction is a deal-point that may need re-negotiation if not already contracted. Chapter 6 data policy — three new jurisdictions' data-classification regimes to inherit and reflect in the matrix. mod-103 accountability contract — the named oversight role per jurisdiction may differ (US underwriter in US, CA underwriter in CA, etc.); each named person needs Article-4-equivalent training (Chapter 3 Article 4 maps to each jurisdiction's equivalent). Chapter 7 upward packet — the UWCopilot section is now a multi-region section.
- **(vi) What the manager does *not* do.** **Does not extend the EU Article 14 sheet to US / Canada as if the EU regime applied.** Does not negotiate the tenancy arrangement directly with the vendor (procurement + counsel). Does not assume the EU classification extends; Chapter 4's trigger list is explicit that *"a workflow changes in a way that could change its classification — new population of affected persons, expansion from pilot to production"* fires TC2 even without a vendor change. Does not make the mistake of treating "same workflow, new geography" as a no-op.

### Step 7 — Diagnose your triage drift (10 min)

Compare your triage sheets against the key. For each miss, write one paragraph:

- **If you marked Workflow A `no Article 50 sheet` because the handler reviews and sends:** this is the *human-in-the-loop-as-Article-50-exemption* drift. Chapter 4 is explicit that *some* Article 50 sub-paragraphs have human-review exemptions (e.g., 50(4) public-interest text can be exempt when human-reviewed) but the exemption is *counsel's call*, not the manager's, and other Article 50 sub-paragraphs and adjacent statutes (GDPR 13/14/22) do not share that exemption shape. A clean triage flags the Article 50 question to counsel with the specific sub-paragraph the manager suspects; counsel decides whether the exemption applies and what the disclosure text is.
- **If you marked Workflow B `pending-counsel` because "we should be careful":** this is the inverse drift — *sheet-inflation on routine internal workflows*. Chapter 4 names the pattern: *"many engineering teams will find their own workflows are not high-risk — internal productivity use of AI coding assistants on non-regulated code is typically outside Annex III."* Over-flagging dilutes the counsel-trigger signal; the one note in the upward packet (*"team considered; outside Annex III; outside Article 50"*) is the right evidence shape. Reserve counsel bandwidth for TC1–TC5 questions that actually fire.
- **If you marked Workflow C `limited-risk, handler-coaching only` because Operations framed it as workforce development:** this is the *euphemism-as-classification* drift. Chapter 4's Article 50(3) (emotion recognition) attaches to voice tonality analysis of a natural person — the handler in this design — regardless of the downstream use. Annex III's employment / workers-management category attaches to performance-evaluation AI regardless of the framing. Framing is marketing, not classification; the manager reads through to the technical and legal substance before routing. A clean triage fires TC1, routes to counsel *and* HR counsel *and* works-council processes in DE/NL, and surfaces the vendor-contract data-flow questions the pilot cannot start before clearing.
- **If you marked Workflow D `no new work — existing sheet applies` because UWCopilot is already classified:** this is the *geography-as-no-op* drift. Chapter 4's TC2 is explicit: *"A workflow changes in a way that could change its classification — new data sources, new decision authority delegated to the AI, new population of affected persons, expansion from pilot to production."* A new population of affected persons in a new jurisdiction is *multiple* new regulatory regimes, not an extension of the existing one. The EU Article 14 sheet does not compliance-attest to US and Canadian regulators; equivalent artifacts (shaped from the EU sheet, but counsel-approved per jurisdiction) are the expected output. A clean triage also routes to the US and Canadian compliance partners who own their jurisdictions.
- **If your composition plan for Workflow A or C invented new oversight roles, decision points, or override mechanisms rather than naming the inherited artifacts:** this is the *authoring-when-the-task-is-composition* drift Chapter 4 names explicitly: *"the sheet is a mapping of existing artifacts to Article 14 language. If any field cannot be filled from existing artifacts, that is a gap in the team's stack and the exercise flags it."* The right move is to trace each of the eight fields to its upstream module artifact (mod-103 Ch. 5 for the role; mod-106 for decision points and override; mod-103 checklist + Chapter 3 Article 4 for automation-bias; mod-109 for trace and escalation) and flag the gaps where composition does not reach — not to author replacements.
- **If your bounded ask to counsel on any workflow was "please take a look":** per the discipline Chapter 4 names for Article 50 affected-person questions (the fourth trigger), and per the five-field clean-handoff shape from `mod-109` Ch. 5 that Chapter 4 reads onto counsel engagement, the ask is specific, bounded, time-boxed, and asks the *legal question* the manager needs answered to run the practice. A "please take a look" message guarantees either over-scoped work, misdirected work, or a return-trip to clarify that costs the triage clock weeks.

## Expected output

A file `lab-02-triage-sheets.md` with four triage sheets in the Step 1 template, plus a diagnosis section covering every call that differed from the key. Roughly 1–1.5 pages per workflow; 1 page for the diagnosis.

Something like:

```
Workflow C — HandlerCoach: AI-enhanced call-centre tooling with voice tonality
             analysis

(i) Classification signal     : likely Annex III (employment/performance
                                evaluation) AND Article 50(3) (emotion
                                recognition). Rationale: Ch. 4 reads voice
                                tonality → empathy signal → supervisor
                                coaching as a performance-evaluation AI on
                                an employee; Article 50(3) attaches to
                                emotion-recognition systems operated by a
                                deployer; the handler is the natural person
                                being analysed. "Coaching, not surveillance"
                                is a framing, not a classification.
(ii) Article 14 sheet needed?  : YES if counsel confirms Annex III (likely).
    Composition plan:
      Field 2 (oversight role) : supervisor + Workforce-Experience partner;
                                 new role — mod-103 Ch. 5 contract needs
                                 extension to cover.
      Field 3 (decision points): signal consumption at the supervisor
                                 dashboard; coaching conversation with the
                                 handler (mod-108 performance-management
                                 process — cross-reference to mod-108).
      Field 4 (override)       : supervisor discounts signal; handler
                                 disputes per firm grievance process (mod-108
                                 cross-reference).
      Field 5 (auto-bias mit.) : supervisor training on empathy-signal
                                 automation bias; reviewer-tier Ch. 3 Art. 4
                                 literacy; mod-107 anti-atrophy check.
      Field 6 (trace)          : mod-109 trace-preservation + empathy-model
                                 inputs / outputs retained per employment-
                                 records policy.
      Field 7 (escalation)     : mod-109 routing + HR partner.
(iii) Article 50 sheet needed? : YES — Article 50(3). Disclosure text owner:
    counsel. Appears: handler onboarding + per-shift reminder on dashboard.
    Verification: process gate on dashboard (signal hidden until handler
    acknowledges).
(iv) Counsel triggers fired    : TC1. Also HR / employment counsel; also
    likely works-council notification DE + NL. Specific ask: {5-field
    bounded ask as in key}.
(v) Upstream / downstream      :
    - mod-108 performance-management framing — substantial changes likely.
    - mod-103 Ch. 5 accountability contract — new supervisor clause.
    - mod-106 tool-authorisation — vendor data residency to procurement.
    - Ch. 6 data policy — employee voice-call data clause-reader + model-
      card entry per selected tonality classifier.
    - Ch. 7 upward packet — HandlerCoach probably has its own section.
(vi) What the manager does NOT do:
    - Accept "coaching, not surveillance" as a counsel substitute.
    - Pilot before counsel + HR + works-council clear.
    - Negotiate directly with the vendor on data residency.

✅ match on Article 50(3) + Annex III; initial draft marked this "limited-risk,
   internal performance management" — corrected after re-reading Ch. 4's
   Article 50(3) definition and Chapter 7's ownership-boundary line on legal
   interpretation.
```

## Checkpoint

Before moving on to Lab 03 (data-matrix decision drill) or starting [Exercise 01](../exercises/exercise-01-nist-ai-rmf-govern-to-team-practice.md) and [Exercise 05](../exercises/exercise-05-upward-evidence-packet-for-governance-program.md) on your real team, you should be able to answer **yes** to all six:

- Did you flag the Article 50(3) obligation on Workflow C despite the "coaching, not surveillance" framing, and route to counsel + HR counsel + works-council processes — not to a single generic "please review" message to GC?
- Did you resist the inverse drift on Workflow B — treating a routine internal engineering productivity tool as counsel-worthy — recognising that over-flagging dilutes the trigger-list signal and that a one-note "outside Annex III, outside Article 50" in the upward packet is the correct evidence shape?
- Did you catch Workflow D's TC2 fire despite the "same workflow, new geography" framing — recognising that new population of affected persons is itself a classification trigger, that the EU Article 14 sheet does not compliance-attest to US and Canadian regulators, and that the US and Canadian compliance partners (not just EU counsel) own their jurisdictions?
- On every Article 14 composition plan, did you name the upstream module artifact for each of the eight fields (or flag the gap where composition does not reach) — rather than inventing new oversight-role, decision-point, or override-mechanism designs?
- On every bounded ask to counsel, did you follow the clean-handoff shape (specific question, time-boxed, with the specific legal issue the manager needs answered) rather than a "please take a look"?
- On every workflow, did you distinguish *what the manager flags* from *what the manager decides* — recognising that classification, disclosure text, exemption basis, and jurisdictional interpretation are counsel's; the manager's role is to triage cleanly, compose existing artifacts into draft sheets, and flag what the sheet cannot yet fill?

If any answer is no, re-read the relevant Chapter 4 section (*"Article 14 — the deployer's reading"*, *"The Article 14 workflow sheet"*, *"Article 50 — the transparency obligations"*, *"The Article 50 interaction sheet"*, *"Composition with the rest of the track"*, or *"The triggers for routing to counsel"*) or Chapter 7's ownership-boundary table before running [Lab 03](lab-03-data-matrix-decision-drill-on-four-tuesday-afternoon-scenarios.md) or starting [Exercise 01](../exercises/exercise-01-nist-ai-rmf-govern-to-team-practice.md) on your real team's crosswalk and the Chapter 4 practice embedded in [Exercise 05](../exercises/exercise-05-upward-evidence-packet-for-governance-program.md).
