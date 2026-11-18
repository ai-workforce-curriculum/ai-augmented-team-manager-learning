# Lab 03 — Data-Matrix Decision Drill on Four Tuesday-Afternoon Scenarios

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 6 (the data-class × tool-class matrix; the vendor clause-reader's five fields; the Hugging-Face-style model-card discipline for team-selected models; the IP sidecar; the *what leaves the premise* distinction; the data-leak trigger list), with side-checks against Chapter 1 (what practice vs. policy means at team scope), Chapter 3 (how Module E of the Article 4 curriculum covers data handling for the team), and Chapter 7 (how data-and-IP incidents land in the upward packet).
**Complements, does not duplicate:** [Exercise 04](../exercises/exercise-04-data-and-ip-handling-policy.md) asks you to *author* the v0.1 data-and-IP policy for **your own** team — your own data-classification tiers, your own tool stack, your own vendor clauses, your own IP sidecar — with the privacy office, procurement, and counsel partners. This lab hands you a pre-built composite matrix, clause-reader, and model-card index for a fictional team, then runs you through four Tuesday-afternoon IC scenarios where you have to **read** the policy and decide allowed / conditional / prohibited in under a minute per scenario — before you spend authoring hours on a policy and discover that your matrix fails the Tuesday-afternoon test the first time an IC actually uses it. The policy that matters is the one an IC can read and act on in 30 seconds; this lab calibrates your reading of a matrix that works.

## Objective

For each of four composite IC scenarios, produce a decision sheet with: (i) the **cell** of the pre-built matrix the question lands in (data class × tool class); (ii) the **cell value** — allowed, conditional, or prohibited — read from the matrix; (iii) the **specific condition** cited (if conditional) — vendor clause, tagging requirement, approval workflow, audit trail; (iv) the **alternative path** if the primary cell is prohibited — synthetic fixture, transformation, tool-authorisation exception; (v) the **30-second response to the IC** in one or two sentences; (vi) **any trigger fired on the data-leak trigger list** (TC1–TC5-equivalent). Then compare against the answer key.

Target: **you read the correct cell on all four scenarios, you resist the two specific drifts — treating a zero-retention enterprise contract as a free-pass on a prohibited cell, and treating anonymised-looking data as safely de-classified when the matrix's transformation gate has not been applied — and on the one scenario that fires a data-leak trigger you name the three correct next moves (preserve, call, do not communicate externally) rather than the typical "investigate and ask vendor" misroute.** These are the two reading drifts Chapter 6 flags as common and the one data-leak reflex Chapter 6's trigger list is designed to prevent.

## Prerequisites

- Chapter 6 read end-to-end — the matrix, the clause-reader, the model-card discipline, the IP sidecar, the *what leaves the premise* distinction, the data-leak trigger list, and the jurisdictional-awareness list. Keep the matrix on a scratch page; you will score against it.
- Chapter 3 skimmed — Module E (data / IP / confidentiality) of the Article 4 curriculum.
- Chapter 4 skimmed — the triggers for routing to counsel and the Article 50 interaction sheet shape (Scenario C implicates one).
- Chapter 7 skimmed — the data-leak-incidents field of the upward packet.
- A blank file for your decision sheets.
- A timer.

## The fictional context

Same team as [Lab 01](lab-01-govern-crosswalk-cell-grading-on-a-composite-artifact-list.md) and [Lab 02](lab-02-article-14-and-50-triage-on-four-composite-workflows.md) — the "Claims Intelligence" team at Northstar Mutual.

> **"Claims Intelligence" team, Northstar Mutual (EU-headquartered personal-lines insurer, Dublin).** 10 engineers, 1 manager. Runs `ClaimsPilot` (internal RAG for claims-handlers) and `UWCopilot` (underwriting-assist; counsel-classified adjacent-to-high-risk under Annex III 5(b); Article 14 sheet v3.2 live). Data policy v1.3 (Chapter 6 team artifact) is on the wiki; the matrix below is the pre-built v1.3. Tools in use: Claude Code via team gateway with Claude for Enterprise contract; Cursor Business; the bespoke `ClaimsPilot` orchestrator on top of a GPT-family model via the enterprise gateway; a self-hosted embedding model; and — for one scenario — a shared ChatGPT consumer account one IC has used historically. The firm's data-classification standard has five tiers (Public, Internal, Confidential, Restricted, Regulated). Counsel's Privacy & AI partner is reachable through GC. Procurement maintains the mod-111 vendor registry at `drive://northstar-governance/vendors/`. SecOps is via `#security-ir` PagerDuty. The IP sidecar v1.1 is on the wiki.

## The pre-built artifacts

### The data-class × tool-class matrix (Chapter 6 v1.3)

```
                           Local-only IDE   Claude for Ent.    Cursor Business   ClaimsPilot RAG   Self-hosted      Consumer ChatGPT
                           (no cloud)       (zero-retention)   (enterprise)      (internal)        embedding        (no enterprise
                                                                                                   model            contract)
Public                     allowed          allowed            allowed           allowed           allowed          allowed
Internal (non-sens.)       allowed          allowed            allowed           allowed           allowed          conditional ¹
Confidential               allowed          conditional ²      conditional ²     allowed           allowed          prohibited
Restricted                 allowed          prohibited         prohibited        prohibited ³      conditional ⁴    prohibited
                                            (incl. customer
                                             files, claim
                                             files, UW files,
                                             PII)
Regulated                  mgr + counsel    prohibited         prohibited        prohibited        prohibited       prohibited
(PHI, PCI card data,       sign-off
 GDPR special category)
```

**Conditions:**

- **¹ Consumer-tier × Internal:** prohibited by default; **conditional** only for Internal content that is already public-adjacent (e.g., open-source code already on GitHub, published documentation). Vendor clause citation: OpenAI consumer ToS as of 2026-10 (link in registry); note that consumer ToS permits training-on-inputs by default and has no retention cap the organisation has negotiated. Approval: team-manager sign-off per case + logged in tool-authorisation exception queue.
- **² Confidential × Claude for Ent. / Cursor Business:** conditional on *per-document tagging per the tagging workflow at `drive://northstar-claims/policies/confidential-tagging-v1.0.md`*; vendor clauses Anthropic Enterprise 2026-04 (training opt-out confirmed; 30-day retention with zero-retention option enabled; EU tenancy) and GitHub Cursor Business 2026-06 (training opt-out confirmed; 30-day retention default). No per-case approval required for tagged documents; manager sign-off required for untagged exception requests per mod-106 tool-authorisation policy.
- **³ Restricted × ClaimsPilot RAG:** prohibited for *external-source Restricted data* (e.g., an applicant's full file); the `ClaimsPilot` index itself contains the firm's own policy/coverage docs which are *Confidential-at-highest*, not Restricted, and are permitted in the index per the ClaimsPilot model card (see model-card index below). Claims-handler queries of the index that include applicant-identifiers in the query text are prohibited; query redaction / per-case lookup via the claims-case ID (not the applicant identifier) is the permitted path.
- **⁴ Restricted × self-hosted embedding model:** conditional on *per-model deployment review*; current deployment review 2026-09-22 confirmed Restricted data is permitted for embedding *only* when (a) the embedding is retained in the Northstar-tenanted vector store, (b) the raw text is discarded after embedding, and (c) query-time retrieval returns content only to authenticated Northstar systems. Manager + `ai-risk-engineer` + procurement sign-off on the deployment review.

### The clause-reader summary (vendors in scope for this lab)

- **Claude for Enterprise (Anthropic).** Training-on-your-data: opt-out confirmed; team is opted out. Retention: 30 days default; zero-retention option enabled 2026-04-12. Residency: EU-tenancy (DE + IE) per contract. Access and audit: zero-knowledge posture; audit logs via enterprise admin console. Deletion: configurable retention + manual deletion workflow via admin console. Contract clause reference: `drive://northstar-governance/vendors/anthropic-enterprise-2026-04.md`.
- **Cursor Business.** Training-on-your-data: opt-out confirmed; team is opted out. Retention: 30 days default. Residency: US-primary with EU subprocessors. Access and audit: audit logs via enterprise admin console. Deletion: manual deletion workflow. Contract reference: `drive://northstar-governance/vendors/cursor-business-2026-06.md`.
- **OpenAI consumer (ChatGPT).** Training-on-your-data: **yes** (consumer ToS, no negotiated opt-out). Retention: 30 days default with limited user controls. Residency: US. Access and audit: minimal. Deletion: user-driven, not contractually guaranteed. Contract reference: consumer ToS as of 2026-10 (link). **No enterprise contract exists for this account.**

### The model-card index (team-selected models)

- **`claude-sonnet-4-6` via Claude for Enterprise** — card at `drive://northstar-claims/model-cards/claude-sonnet-4-6-v2.1.md`. Intended use: `claims-router` summarisation, `UWCopilot` draft generation (adjacent-to-high-risk; see Article 14 sheet). Data classes permitted per the matrix: Public, Internal, Confidential-tagged. Operational constraints: HITL checkpoint per UWCopilot workflow; no shell authorisation in the UWCopilot harness.
- **`claude-sonnet-4-6` via Claude Code gateway** — card at `drive://northstar-claims/model-cards/claude-sonnet-4-6-codegateway-v1.3.md`. Intended use: engineering workflows (code generation, review, debugging). Shell authorisation is present per mod-106 tool-authorisation; data classes permitted: Internal, Confidential-tagged. Model card is a thin extension of the Claude for Enterprise card.
- **`gpt-5` via the `ClaimsPilot` orchestrator** — card at `drive://northstar-claims/model-cards/gpt-5-claimspilot-v1.0.md`. Intended use: `ClaimsPilot` RAG generation over the internal policy/coverage index. Data classes permitted at query-time: query text may be Internal or Confidential-tagged; raw Restricted applicant data is prohibited in the query per the matrix footnote ³. Operational constraints: query redaction layer in the orchestrator.
- **Self-hosted embedding model (`bge-m3`)** — card at `drive://northstar-claims/model-cards/bge-m3-v1.2.md`. Intended use: `ClaimsPilot` and internal retrieval. Data classes permitted for embedding: Internal, Confidential, Restricted *per the matrix footnote ⁴* (per-model deployment review passed 2026-09-22). Operational constraints: embedding-only; raw text not retained; retrieval access control to Northstar-tenanted systems.

### The IP sidecar (v1.1)

- Model-output ownership: Northstar owns outputs subject to vendor TOS; counsel-confirmed per vendor as of 2026-08.
- Open-source license interactions: AI-generated code that resembles open-source code → run the firm's attribution-and-review workflow at `drive://northstar-claims/policies/ip-oss-ai-workflow-v1.0.md` before merge.
- Pre-existing confidentiality undertakings: for the three customers covered by bespoke NDA with no-third-party clauses, their data is **Restricted-plus** for this policy's purposes — treat as Restricted + do not include in any AI tool regardless of class permissions.
- Attribution and disclosure: AI involvement in customer-facing deliverables requires the counsel-approved footer (see Article 50 interaction sheet for `ClaimsExplain` if live).

### The data-leak trigger list (half-page per Chapter 6)

- **What is a data-leak event?** Any event where data of a classification higher than the matrix permits for the tool class has left the premise *or* is unaccounted for after leaving the premise.
- **Who to call, in order.** 1. SecOps on-call via `#security-ir` PagerDuty. 2. Counsel partner via GC. 3. Manager (if the manager is not the person discovering).
- **What to preserve.** The prompt, the response, the timing, the vendor session identifier, the user account, any screenshots or logs the IC has, the agent session if still open (do not close until SecOps instructs).
- **What to escalate to counsel immediately.** Any event touching Regulated data, Restricted applicant data, or an affected person.
- **What *not* to do.** Do not delete logs. Do not communicate externally. Do not post publicly (including vendor-side community forums). Do not notify the vendor until SecOps and counsel have confirmed the step. Do not "investigate from both ends" — SecOps owns the forensic timeline.

## The four composite Tuesday-afternoon scenarios

### Scenario 1 — the enterprise-contract reflex

> **Tuesday 14:10.** IC pings in Slack: *"I've got a reproducer for the UWCopilot ranking-anomaly bug where it's weighting the wrong feature on NL postcode data. I need to paste one real applicant file into Claude Code to walk through the branch. Claude for Enterprise is zero-retention and EU tenancy, so I'm good on both fronts — right? Timeboxing, I'd like to be running in 5 minutes."*

### Scenario 2 — the "anonymised" paste

> **Tuesday 14:35.** IC pings: *"I've scrubbed the name, email, and policy number from this applicant file — just leaving the age band, postcode, prior-claims count, and the assessed-risk score. That's basically internal statistics now, right? I want to use ChatGPT on my personal account to help me think through whether the UWCopilot risk-score distribution matches what a statistician would expect. It's faster than the team gateway today — gateway's being flaky."*

### Scenario 3 — the ClaimsPilot query shape

> **Tuesday 15:05.** Claims-handler (not on your team; routed in by their lead): *"Can I ask `ClaimsPilot` 'what's the policy coverage for applicant Mary O'Sullivan on claim CL-2027-004129?' The handler-tool product team said just use natural language and it'll handle the rest. I'd normally ask you but I'm on hold with the applicant."*

### Scenario 4 — the discovered paste

> **Tuesday 16:20.** Junior IC comes to your desk: *"Uh. I pasted a Confidential policy-coverage doc into my personal ChatGPT this morning — I was helping a friend-who-also-works-in-insurance understand a weird clause and I used our real doc instead of synthesising one. The doc is labelled Confidential in the firm's classification. I only noticed because I saw the Confidential footer when I was copying the paste back into Slack to show them later. The ChatGPT chat is still open."*

## Steps

### Step 1 — Set up your decision sheet (3 min)

Create a working file `lab-03-decision-sheets.md` with this template, repeated once per scenario:

```
Scenario <N>: <one-line description>

(i)   Cell (data class × tool class): <row> × <column>
(ii)  Cell value                     : allowed / conditional / prohibited
(iii) Specific condition             : <clause / tagging / approval / audit trail>
                                       <OR: "prohibited — alternative required">
(iv)  Alternative path               : <synthetic fixture / anonymisation + review /
                                        tool-authorisation exception / counsel-routing /
                                        n/a if cell is allowed/conditional-cleanly>
(v)   30-second response to the IC   : <one or two sentences>
(vi)  Trigger fired on data-leak    : YES / NO
      trigger list
      If YES                        :
        First call                   : <SecOps / counsel / manager>
        Second call                  : <...>
        Preserve                     : <specific artifacts>
        Do NOT                       : <specific anti-actions>
```

Time yourself. Target per scenario: **under 2 minutes for reading the matrix + drafting the IC response**, with the full triage sheet at 7–10 minutes per scenario. The field target is 30 seconds per IC decision. The over-budget is diagnostic signal.

### Step 2 — Scenario 1 (7–10 min)

Decide Scenario 1 against the template. Do not look at the key yet. The specific tempting miss: the IC's logic sounds correct (zero-retention + EU tenancy) and the IC has time pressure.

### Step 3 — Scenario 2 (7–10 min)

Decide Scenario 2. The specific tempting miss: the IC has already stripped obvious PII; the question is whether residual data remains Restricted.

### Step 4 — Scenario 3 (7–10 min)

Decide Scenario 3. The specific tempting miss: the handler is external to your team but their lead routed them in; the question is about a workflow you nominally own; there is time pressure (applicant on hold).

### Step 5 — Scenario 4 (7–10 min)

Decide Scenario 4. This is the data-leak scenario. The specific tempting miss: the junior IC is in front of you, uncomfortable, and wants a path forward; the easy move is to say "close the chat and we'll figure it out tomorrow."

### Step 6 — Compare against the answer key (15 min)

Read the key below only after you have decided all four.

#### Answer key — Scenario 1 (enterprise-contract reflex)

- **(i) Cell.** Row = **Restricted** (applicant files are Restricted per the firm's classification; the matrix illustration row explicitly lists *"customer files, claim files, UW files, PII"* under Restricted). Column = **Claude for Enterprise (zero-retention)**.
- **(ii) Cell value.** **Prohibited.** Chapter 6's matrix illustration and the pre-built matrix above both show Restricted × Claude for Enterprise as prohibited.
- **(iii) Specific condition.** n/a — cell is prohibited. The IC's reasoning (zero-retention + EU tenancy = safe) conflates *vendor contract properties* (what the vendor commits to) with *data-class decisions* (what the team's policy permits). Chapter 6 is explicit: *"ICs frequently equate 'enterprise contract' with 'anything goes'. The policy explicitly disabuses this."* The vendor contract is the *floor* — zero-retention means the vendor won't retain; it does not mean the team authorises the data class into the tool.
- **(iv) Alternative path.** Two legitimate paths. **Path A (preferred):** synthetic fixture. Generate a synthetic applicant file that reproduces the ranking-anomaly branch (Internal class; permitted in Claude for Enterprise without conditions). The branching behaviour — not the applicant's identity — is what the IC needs. Chapter 6's Tuesday-afternoon example uses this exact path. **Path B (exception):** if the branch is genuinely irreproducible synthetically (rare), open a tool-authorisation-policy exception request per mod-106 that routes to the manager for sign-off with specific justification, specific scoping (one applicant record, one session, under observation), and specific post-use deletion. Manager signs off in writing; the exception is logged in the tool-authorisation exception queue; the upward packet reflects it.
- **(v) 30-second response.** *"Matrix cell is Restricted × Claude for Enterprise = prohibited (see v1.3 at [link]; zero-retention doesn't change the cell — the vendor-contract axis and the data-class axis are independent). Go synthetic: generate a fixture that reproduces the branch and run in Claude Code; if the branch is irreproducible synthetically, open a mod-106 tool-authorisation exception request and I'll review today. Timebox: 10 min for fixture, 30 min for exception if needed."*
- **(vi) Data-leak trigger.** **NO.** The IC asked before pasting; no data has left the premise. The exchange is itself the control working.

#### Answer key — Scenario 2 (the "anonymised" paste)

- **(i) Cell.** This is the most ambiguous scenario on classification. Two reads:
  - **Strict read.** The residual fields (age band, postcode, prior-claims count, assessed-risk score) remain *Restricted or Confidential* depending on the firm's classification standard — postcode plus claims history has re-identification potential under GDPR's reasonably-identifiable-natural-person test, which Chapter 6 names in the jurisdictional-awareness list. So the cell is **Restricted × Consumer ChatGPT** or **Confidential × Consumer ChatGPT**.
  - **Liberal read.** If the firm's data-classification standard has a *de-identified aggregate* class separate from Restricted, and the IC's scrub meets the de-identification test, the row could drop to Internal. This is almost never the case in practice without a formal de-identification review.
- **(ii) Cell value.** **Prohibited** in both reads for the *Consumer ChatGPT* column. Restricted × Consumer ChatGPT = prohibited; Confidential × Consumer ChatGPT = prohibited. Even if the classification dropped to Internal, the Consumer ChatGPT cell is **conditional ¹** (manager sign-off per case, logged in tool-authorisation exception queue) — not *anything goes*.
- **(iii) Specific condition.** n/a — cell is prohibited. The vendor contract matters here: **Consumer ChatGPT has no enterprise contract; training-on-inputs is permitted by the consumer ToS; no negotiated opt-out; US residency.** Chapter 6's *"what leaves the premise"* section is explicit: *"A shared Google / ChatGPT / Claude account with the consumer terms of service is not the same thing as the enterprise or business tier with zero-retention terms."* The IC's mental model confuses the two.
- **(iv) Alternative path.** **Fix the gateway.** If the team gateway is flaky, the right move is to open a ticket with the gateway owner, not to route around it to consumer tools. **Statistical review path:** if the IC wants a statistician's distribution review, the right tool is a proper statistical analysis in the team's analytics environment (R, Python, or whatever the team uses) with synthetic distribution samples. **Documentation path:** if the IC genuinely needs a conversational tool for the statistical reasoning, use Claude for Enterprise (not consumer) with a *synthetic* distribution derived from the real one (same distributional properties, no real records).
- **(v) 30-second response.** *"Scrubbing name/email/policy-number doesn't drop the class — postcode + claims count has re-identification potential (GDPR Article 4(1) test). Consumer ChatGPT has no enterprise contract and training is on by default (see clause-reader at [link]); any data class above Public is prohibited there. Three paths: (a) file a gateway ticket and use Claude for Enterprise, (b) do the stats properly in our analytics env, (c) use a synthetic distribution with the same shape. All three faster than cleaning up after a Confidential leak."*
- **(vi) Data-leak trigger.** **NO** — asked before pasting.

#### Answer key — Scenario 3 (the ClaimsPilot query shape)

- **(i) Cell.** Multiple cells interact here. The user is a claims-handler (authorised consumer of `ClaimsPilot`), the tool is `ClaimsPilot` (internal RAG), the data in the query is the applicant's name — which is a Restricted datum (PII) — in the query text. Matrix footnote ³ is the controlling condition: *"Restricted × ClaimsPilot RAG: prohibited for external-source Restricted data (e.g., an applicant's full file); the ClaimsPilot index itself contains the firm's own policy/coverage docs which are Confidential-at-highest. Claims-handler queries of the index that include applicant-identifiers in the query text are prohibited; query redaction / per-case lookup via the claims-case ID (not the applicant identifier) is the permitted path."*
- **(ii) Cell value.** **Prohibited as asked.** The *redacted / claim-ID-based query* is **allowed**.
- **(iii) Specific condition.** The permitted shape of the query: use the claim ID (`CL-2027-004129`), not the applicant's name. The orchestrator's query-redaction layer is designed to strip identifiers that slip in, but the handler should not rely on the layer; the handler should write the query without the identifier.
- **(iv) Alternative path.** Same question, correct shape: *"what's the policy coverage for claim CL-2027-004129?"* The orchestrator resolves the claim ID internally (via authenticated Northstar-tenanted systems per the `gpt-5-claimspilot-v1.0.md` model card's operational constraints) without exposing the applicant's name to the query.
- **(v) 30-second response.** *"Query shape needs to be claim-ID-based, not name-based — matrix footnote ³. Re-ask as: 'what's the policy coverage for claim CL-2027-004129?' and the orchestrator resolves the applicant mapping internally. Also — the handler-tool product team's 'just use natural language' guidance is wrong for this specific workflow; I'll flag it to them for a correction. Takes 10 seconds to re-ask."*
- **(vi) Data-leak trigger.** **NO** if the handler asks before sending. If they already sent the name-based query, the redaction layer *may* have stripped the name before it reached the model, but that is a trigger-adjacent event — audit-log check needed; if the redaction layer did not catch it, treat as Scenario 4 shape.

#### Answer key — Scenario 4 (the discovered paste)

- **(i) Cell.** Row = **Confidential** (per the firm's classification, with the Confidential footer on the doc). Column = **Consumer ChatGPT (no enterprise contract)**. Matrix cell: **Prohibited.** The paste has already happened; the question is incident response, not permission.
- **(ii) Cell value.** **Prohibited — now a data-leak event.** Chapter 6's data-leak definition fires: *"any event where data of a classification higher than the matrix permits for the tool class has left the premise or is unaccounted for after leaving the premise."* Confidential data has entered Consumer ChatGPT, which is prohibited, with no negotiated retention cap, no training opt-out, US residency, and consumer-tier terms.
- **(iii) Specific condition.** n/a — this is an incident. The data-leak trigger list is now the operative artifact.
- **(iv) Alternative path.** The IC's forward path is now the incident response, not a "fix forward" with the data.
- **(v) 30-second response (incident-mode, not permission-mode).** *"OK, stop. This is a data-leak event per the Chapter 6 trigger list. Do not close the ChatGPT tab yet (preserve). Do not delete anything. Right now: (1) I'm paging SecOps via `#security-ir`, (2) I'm looping in counsel through GC, (3) we preserve the chat ID, timestamps, exact doc text pasted, your user account, and any screenshots. We do NOT contact OpenAI, we do NOT post about this anywhere, we do NOT investigate the chat further ourselves — SecOps owns the forensic timeline from here. You are not in trouble; this is exactly what the trigger list is for. Go to the quiet room and wait for SecOps to call — I'll come get you in ~10 minutes."*
- **(vi) Data-leak trigger.** **YES.** Per the Chapter 6 trigger list:
  - **First call.** SecOps on-call via `#security-ir` PagerDuty.
  - **Second call.** Counsel partner via GC.
  - **Third call.** (If the manager is not the person discovering — in this scenario the manager is receiving the discovery, so the manager is the one doing the paging.)
  - **Preserve.** The open ChatGPT tab/session; chat ID and URL; timestamps; the exact Confidential doc text pasted; the IC's user account; screenshots; the Slack thread or verbal-report note; any downstream messages the IC sent that referenced the content ("I was going to show them in Slack later").
  - **Escalate to counsel immediately.** The event does not touch Regulated data or applicant data on its face, but the Confidential policy-coverage doc *may* be subject to one of the bespoke-NDA customer clauses in the IP sidecar; counsel assesses. The friend-who-also-works-in-insurance dimension is a potential competitor-adjacent leak that counsel will want to understand.
  - **Do NOT.** Delete the chat. Communicate with OpenAI. Post publicly (including the vendor's community forum). Notify the "friend" or ask them to delete their side (counsel decides). Discuss the leak outside the containment group. "Investigate from both ends" — SecOps owns the forensic timeline; the manager does not race SecOps to understand what happened.

### Step 7 — Diagnose your reading drift (10 min)

Compare your decision sheets against the key. For each miss, write one paragraph:

- **If you marked Scenario 1 `conditional` or `allowed` because zero-retention + EU tenancy "covers it":** this is the *enterprise-contract reflex* drift Chapter 6 names explicitly: *"ICs frequently equate 'enterprise contract' with 'anything goes'. The policy explicitly disabuses this."* The vendor-contract axis and the data-class axis are independent; the matrix cell is the product of both. The Chapter 6 Tuesday-afternoon worked example runs the exact pattern — Restricted × Claude Code enterprise = prohibited despite zero-retention. The IC's language ("zero-retention is EU tenancy so I'm good") is the archetypal misread; your job is to correct it in one sentence and route to the synthetic-fixture path. Re-read Chapter 6's *"What leaves the premise"* and the Tuesday-afternoon example.
- **If you marked Scenario 2 `conditional` or `allowed` because the IC had already scrubbed name/email/policy-number:** this is the *anonymisation-as-de-classification* drift. GDPR's reasonably-identifiable-natural-person test — named in Chapter 6's jurisdictional-awareness list — captures postcode + prior-claims count + assessed-risk score as reasonably re-identifiable in combination. Chapter 6's *"what leaves the premise"* also distinguishes *"allowed after transformation — synthetic or anonymised versions of the data may go; the raw may not. The transformation step is explicit in the workflow."* The IC's scrub is not a *formal* de-identification review; absent one, the classification does not drop. And even if it did, Consumer ChatGPT with no enterprise contract and training-on-by-default is the wrong column at best. Re-read Chapter 6's *"What leaves the premise"*.
- **If you marked Scenario 3 `allowed` because the handler is authorised to use ClaimsPilot:** this is the *tool-authorisation-is-not-query-shape-authorisation* drift. The handler's authorisation to use the tool does not authorise any query shape; matrix footnote ³ is explicit about the required query shape (claim ID, not applicant name). The product team's "just use natural language" guidance is a separate problem — a mis-documented product requirement that the manager has to flag for correction. A clean response both corrects the handler's query shape and names the product-team-level issue.
- **If you treated Scenario 4 as a "coach the IC and we'll figure it out tomorrow" case:** this is the *data-leak-as-coaching-moment* drift Chapter 6's trigger list is specifically designed to prevent. The trigger list is: SecOps first, counsel second, manager (if not discoverer); preserve; escalate to counsel immediately on any Confidential-plus event; do NOT delete logs, communicate externally, post publicly, or notify the vendor. "We'll figure it out tomorrow" means logs may be gone, the "friend" may have screenshotted the exchange, the vendor may have rotated the session, and counsel has lost the time it needs to assess. The response is incident-mode, not coaching-mode. The coaching conversation happens *after* SecOps closes the incident, and it is blameless (per mod-109 discipline).
- **If your 30-second response on Scenario 4 included "I'll reach out to OpenAI to see if they can delete the chat":** this is the *contact-the-vendor-first* drift — a specific line on the *"What not to do"* list. SecOps and counsel coordinate any vendor engagement; the manager does not communicate with OpenAI on an incident until SecOps and counsel have confirmed the step (there are regulatory-clock and preservation implications the manager is not positioned to judge). Chapter 6: *"do not notify the vendor until SecOps and counsel have confirmed the step."*
- **If your 30-second response on any scenario took more than a few sentences:** the policy is designed so the IC gets an actionable answer in 30 seconds. If the manager is writing paragraphs, the manager is either (a) the policy's substitute (not what the matrix is for), (b) over-caveating because the matrix is not clear enough, or (c) over-explaining because the IC is not fluent enough (Module E of the Chapter 3 Article 4 curriculum is the fix). Diagnose which.

## Expected output

A file `lab-03-decision-sheets.md` with four decision sheets in the Step 1 template, plus a diagnosis section covering every call that differed from the key. Roughly 0.5–1 page per scenario; 1 page for the diagnosis.

Something like:

```
Scenario 1 — Enterprise-contract reflex
(i)   Cell                       : Restricted × Claude for Enterprise
(ii)  Cell value                 : Prohibited
(iii) Specific condition         : n/a — cell is prohibited; IC conflated
                                   vendor-contract axis with data-class axis.
(iv)  Alternative path           : Path A — synthetic fixture (Internal, allowed
                                   in Claude for Enterprise without conditions);
                                   Path B — mod-106 tool-authorisation exception
                                   if branch is irreproducible synthetically,
                                   with manager sign-off + logged in exception
                                   queue.
(v)   30-second response         : "Matrix cell Restricted × Claude for Ent. =
                                   prohibited (v1.3 at [link]; zero-retention
                                   doesn't change the cell). Go synthetic:
                                   reproduce the branch in a fixture, run in
                                   Claude Code. If genuinely irreproducible,
                                   open a mod-106 exception and I'll review
                                   today. Timebox: 10 min fixture / 30 min
                                   exception if needed."
(vi)  Data-leak trigger          : NO — IC asked before pasting; exchange is
                                   the control working.

✅ match on cell + response. Initial draft read `conditional` because the IC's
   zero-retention logic sounded coherent — corrected on re-reading Ch. 6's
   "What leaves the premise" and the Tuesday-afternoon worked example.

Scenario 4 — Discovered paste (data-leak event)
(i)   Cell                       : Confidential × Consumer ChatGPT
(ii)  Cell value                 : Prohibited — data-leak event per Ch. 6 list
(iii) Specific condition         : n/a — incident mode now active
(iv)  Alternative path           : n/a — forward path is incident response
(v)   30-second response         : [incident-mode response per key — preserve,
                                   page SecOps, loop counsel, IC to quiet room,
                                   no external contact, no further investigation]
(vi)  Data-leak trigger          : YES
      First call                : SecOps via #security-ir PagerDuty
      Second call               : Counsel via GC
      Preserve                  : chat tab/session; chat ID + URL; timestamps;
                                   exact doc text; IC account; screenshots;
                                   Slack thread; any downstream references.
      Do NOT                    : delete chat; contact OpenAI; post publicly;
                                   notify the friend or ask them to delete;
                                   discuss outside containment group;
                                   "investigate from both ends".

✅ match on incident-mode call. Initial reflex was to include "I'll reach out
   to OpenAI about the chat" — caught on re-reading Ch. 6's "What not to do"
   list; SecOps + counsel coordinate any vendor engagement, not the manager.
```

## Checkpoint

Before moving on to [Exercise 04](../exercises/exercise-04-data-and-ip-handling-policy.md) (your team's own data policy) or back to the module's exercises in general, you should be able to answer **yes** to all six:

- Did you resist the *enterprise-contract reflex* on Scenario 1 — reading the cell as the product of the data-class axis and the tool-class axis independently, and routing to the synthetic-fixture path as the default?
- Did you resist the *anonymisation-as-de-classification* reflex on Scenario 2 — recognising that a casual scrub does not meet a formal de-identification review, that residual re-identification potential keeps the class elevated, and that Consumer ChatGPT with no enterprise contract and training-on-by-default is the wrong column *even if* the class had dropped?
- Did you correct the query shape on Scenario 3 (claim ID, not applicant name) *and* flag the product-team-level "just use natural language" misguidance for correction — rather than fixing one handler's query and leaving the systemic issue unaddressed?
- On Scenario 4, did you switch into incident-mode within the first sentence — SecOps first, counsel second, preserve, do-not-contact-the-vendor, do-not-delete, do-not-post — and treat the junior IC with blameless framing (the trigger list is the control working; this is what it is for)?
- On every 30-second response, did you stay close to one or two sentences and route the IC to a specific alternative path — rather than explaining the policy (that is Module E of Chapter 3's Article 4 curriculum; the matrix is the Tuesday-afternoon artifact)?
- On Scenario 4's incident response, did you remember both the *first-call* list (SecOps → counsel) *and* the *preserve* list *and* the *do-not* list — rather than remembering two of the three?

If any answer is no, re-read the relevant Chapter 6 section (*"The data-class × tool-class matrix"*, *"The vendor data-use clause reader"*, *"What leaves the premise"*, *"Incident recovery for data-leak events"*, or the Tuesday-afternoon worked example) before starting [Exercise 04](../exercises/exercise-04-data-and-ip-handling-policy.md) on your own team's policy.
