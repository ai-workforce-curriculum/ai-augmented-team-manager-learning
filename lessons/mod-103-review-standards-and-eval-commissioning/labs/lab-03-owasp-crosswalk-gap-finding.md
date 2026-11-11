# Lab 03 — OWASP LLM Top 10 Crosswalk Gap-Finding on a Fictional Team

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 6 (the OWASP Top 10 for LLM Applications crosswalk; one-row-per-risk discipline; "out-of-scope + rationale" as a valid outcome) and Chapter 7 (the ownership boundary with `ai-risk-engineer`), with a side-check against Chapter 2 (where the S6 Security section of the PR template references the crosswalk) and Chapter 4 (where eval briefs cite OWASP rows as regression gates).
**Complements, does not duplicate:** Exercise 06 asks you to build the crosswalk for **your own** team's workflows, re-pulling the live OWASP page. This lab gives you a fixed, partially-filled crosswalk for a fictional team — some rows correct, some with gaps, some mis-attributed, some that should be out-of-scope but aren't — so you can calibrate the gap-finding eye before you spend a real session on your real team. Do this before Exercise 06.

## Objective

Read a partially-filled OWASP LLM Top 10 crosswalk for a fictional customer-platform team. For each of the ten rows, decide: (a) does the entry match the team's workflows? (b) is the review-section / standards-as-code-layer / eval attribution correct? (c) should this row be marked out-of-scope with rationale — and if the sample marks it in-scope, is that a mistake? (d) does the row warrant a companion commission to `ai-risk-engineer`? Compare against the answer key. Target: **you flag at least eight of the ten rows correctly** and your "should-be-out-of-scope-with-rationale" classification is right on the three rows where it applies.

## Prerequisites

- Chapter 6 read end-to-end (the ten risks; the crosswalk table shape; the three-places-the-crosswalk-lives discussion; the reading posture).
- Chapter 7 skimmed (what hands off to `ai-risk-engineer`).
- Chapter 2 skimmed (the seven checklist sections, so you can name which section an OWASP row maps to).
- A blank file for your gap-finding memo.
- A timer.

Useful but not required: a live read of the OWASP Top 10 for LLM Applications page (<https://owasp.org/www-project-top-10-for-large-language-model-applications/>) if you can access it; the live page is more detailed than any summary. (The lab uses the Chapter 6 table as the definitional anchor so you can run it offline.)

## The fictional context

> **"Customer Platform" team, FinSure Financial Services.** 12 engineers; owns `customer-comms`. Two agent workflows in production (both opt-in with sr-eng review): (a) **summary cards** — internal-dashboard summaries of inbound customer support tickets, (b) **first-draft replies** — suggested first-draft responses the agent prepares for agents to edit and send. No fine-tuning; no retrieval corpus the team curates (the agent uses only prompt-level context from the current ticket). Model: a hosted vendor model (claude-sonnet-4-6). The team has a PR template at v0.3 (seven-section Chapter 2 shape), an AGENTS.md + `.cursor/rules/` stack at v0.2, and one commissioned eval at v0.1 — the Lab 02 commissioning brief (now rewritten) on the summary-card flow. `@risk-peer` has done one red-team sweep on the reply flow last quarter; one finding is open. There is no fine-tuning; the vendor dependency is a single named model; the only external code dependency is the official Anthropic SDK and `requests`.

## The sample crosswalk (v0.1, partially filled)

Below is the sample `docs/ai-review-owasp-crosswalk.md`. Read it once end-to-end before doing anything else. Note: the OWASP titles below follow the Chapter 6 table.

```
AI REVIEW — OWASP LLM TOP 10 CROSSWALK v0.1
Team: customer-platform
Date: 2026-11-04. Author: @manager-handle.
Source: https://owasp.org/www-project-top-10-for-large-language-model-applications/
Source-page version date: (not pulled)

| # | Risk                                   | Applies? | Review section      | Standards-as-code layer | Eval regression gate                |
|---|----------------------------------------|----------|---------------------|-------------------------|-------------------------------------|
| 1 | LLM01 Prompt Injection                 | Y        | S6 Security         | 20-security.mdc         | capability eval, planned next qtr   |
| 2 | LLM02 Sensitive Information Disclosure | Y        | S3 Correctness      | lint (ruff)             | TBD                                 |
| 3 | LLM03 Supply Chain                     | Y        | S1 Provenance       | dependabot              | capability eval                     |
| 4 | LLM04 Data and Model Poisoning         | Y        | S6 Security         | retrieval corpus pin    | regression eval on retrieval bumps  |
| 5 | LLM05 Improper Output Handling         | Y        | S4 Verification run | lint (eslint)           | golden-task eval                    |
| 6 | LLM06 Excessive Agency                 | N        | —                   | —                       | —                                   |
| 7 | LLM07 System Prompt Leakage            | Y        | S6 Security         | AGENTS.md security      | capability eval                     |
| 8 | LLM08 Vector and Embedding Weaknesses  | Y        | S6 Security         | retrieval pipeline pin  | regression eval                     |
| 9 | LLM09 Misinformation                   | Y        | S3 Correctness      | AGENTS.md "cite sources"| golden-task eval (G-Eval faith)     |
|10 | LLM10 Unbounded Consumption            | N        | —                   | —                       | —                                   |

Hand-off: @risk-peer reviewed, approved.
```

Read it carefully. Several rows are correct; several have the wrong attribution; several should be marked out-of-scope with rationale rather than filled in generically; one row is wrongly dismissed as N/A; one row is wrongly marked as applying. The "`@risk-peer` reviewed, approved" line is suspicious — Chapter 7 names the boundary conversation, but the sample does not record *what* was agreed.

## Steps

### Step 1 — Set up your gap-finding memo (3 min)

Create a working file `lab-03-crosswalk-gaps.md`. Add this header:

```
# Lab 03 — OWASP LLM Top 10 crosswalk gap-finding (customer-platform sample)

Team facts (anchor for gap-finding):
- Two agent workflows: summary cards (internal); first-draft replies (external exposure).
- Model: claude-sonnet-4-6 (vendor-hosted).
- No fine-tuning on this team.
- No team-curated retrieval corpus (only per-ticket prompt context).
- No agent-controlled tool / MCP connections beyond the model API.
- Code deps: Anthropic SDK + `requests`.
- v0.3 PR template; AGENTS.md + .cursor/rules/ at v0.2; one eval at v0.1 (summary card).

For each of the ten rows, I will record:
  (a) Applies (Y / N / out-of-scope with rationale) — correct?
  (b) Review-section attribution — correct section from Chapter 2?
  (c) Standards-as-code layer — correct layer from Chapter 3?
  (d) Eval regression gate — correct shape from Chapter 4?
  (e) Does this row warrant a companion commission to @risk-peer?

Chapter 6 reminder: "A row with 'out-of-scope' is a valid outcome. … The rationale
is the artifact." A row marked Y with vague fillers is worse than N-with-rationale.
```

### Step 2 — Walk the ten rows (30–40 min)

Work through the ten rows in order. **Target: 3–4 minutes per row.** For each row, note (a) the applies-call, (b) the review-section attribution, (c) the standards-as-code layer, (d) the eval gate, and (e) whether a companion `@risk-peer` commission is warranted.

Specifically, for each row, ask:

- **LLM01 Prompt Injection.** Where does untrusted text cross into the model's instruction surface on this team? What about the reply flow specifically (external customer text going into a model that then drafts a customer-visible reply)? Is this row load-bearing enough that a capability eval "planned next qtr" is insufficient?
- **LLM02 Sensitive Information Disclosure.** Customer tickets carry PII almost by definition. The sample routes this to S3 Correctness — is that the right section, or is this an S6 Security row? Does `ruff` detect PII emission? What else is needed?
- **LLM03 Supply Chain.** The team does not fine-tune, has no team-curated adapters, uses a single vendor model, and has two code dependencies. How much of LLM03 is in-scope at review-time vs. governance-time for this team? Chapter 6: *"some risks are more governance-time than review-time."*
- **LLM04 Data and Model Poisoning.** There is no fine-tuning and no team-curated retrieval corpus on this team. Is this a "retrieval corpus pin" row at all? Does the sample's filling-in-generically pattern apply?
- **LLM05 Improper Output Handling.** The reply flow produces text that goes to external customers; the summary flow produces text that renders in an internal dashboard card. Where does the model's output interpolate into downstream shell / SQL / HTML / another prompt? Is S4 Verification run the right section, or is this an S6 Security row?
- **LLM06 Excessive Agency.** The sample marks this N/A. Is that right? What tool / MCP connections does the agent have? Does drafting a customer-visible reply constitute an agent action that affects an external surface? Chapter 6: the question is whether the agent has *more tool/authorisation surface than its task requires.*
- **LLM07 System Prompt Leakage.** Can the summary-card or reply flows be prompted to leak their system prompt? Is this review-catchable, or primarily an `@risk-peer` capability-eval row?
- **LLM08 Vector and Embedding Weaknesses.** There is no retrieval pipeline on this team. The sample fills in a "retrieval pipeline pin." Is that the right call?
- **LLM09 Misinformation.** The reply flow says things to customers. Is S3 Correctness enough, or does this need its own faithfulness eval? The sample names a G-Eval faithfulness eval — is this consistent with the rest of the stack (the eval the manager commissioned in Lab 02 was on the *summary* flow)?
- **LLM10 Unbounded Consumption.** The sample marks N/A. Does the team have a per-agent token budget? A per-tool rate limit? Is the N/A defensible or a skip?

### Step 3 — Flag the hand-off line (2 min)

Chapter 7 says the crosswalk's hand-off agreement with `@risk-peer` must document *what was agreed* — which rows the team covers at review time and which `@risk-peer` commissions. The sample says *"reviewed, approved."* Write one line on whether that meets the Chapter 7 bar and what should replace it.

### Step 4 — Compare against the answer key (10 min)

Below is the key. For each row, check your attribution against it; count hits (correct in all five columns), near-misses (correct call, one column off), and misses (wrong call).

#### Answer key — row-by-row

1. **LLM01 Prompt Injection — correct Y; correct review-section; correct stack layer; BUT the eval is insufficient.** "Planned next quarter" is not a regression gate; the reply flow is *the* high-risk surface (external customer text → model → customer-visible reply) and a capability eval is overdue. **Companion commission to `@risk-peer` is warranted** — this is the row most central to the already-open Q3 red-team finding. Elevate the eval to this quarter; the Lab 02 brief's "capability-eval companion" paragraph is the right place.
2. **LLM02 Sensitive Information Disclosure — correct Y; WRONG review section (should be S6 Security, not S3 Correctness); the `ruff` layer is insufficient for PII; the "TBD" eval is a gap.** Chapter 6 crosswalk maps LLM02 to S6 Security. `ruff` is a general linter; `detect-secrets` / `gitleaks` + an AGENTS.md "no PII in prompts" rule is the correct layer. The eval gap should be surfaced as a backlog item; the dataset privacy posture also needs review (Chapter 4 points at `mod-110`). The whole row is partially correct but miscategorised.
3. **LLM03 Supply Chain — should be out-of-scope-at-review-time-with-rationale, not Y-with-filler.** The team does not fine-tune, has no team-curated adapters, uses a single vendor model, and has two mainstream code dependencies. Chapter 6: *"LLM03 may be more governance-time than review-time on your team. The rationale is the artifact."* The correct entry: *"Out-of-scope at review-time. Rationale: no fine-tuning, no team-curated adapter / retrieval corpus, single vendor model; dependency-vulnerability scan + vendor DPA handled at governance-time (see `mod-110`, `mod-111`). Revisit if the team adds a self-hosted model, fine-tune, or adapter."* The sample's "S1 Provenance + dependabot" is not wrong in the abstract but misses that the row belongs to a different scope at *this* team.
4. **LLM04 Data and Model Poisoning — should be out-of-scope-with-rationale.** This team has no fine-tuning and no team-curated retrieval corpus. Filling in "retrieval corpus pin" invents infrastructure that does not exist. Chapter 6: out-of-scope with rationale is valid; silent filler is not. Correct entry: *"Out-of-scope at review-time. Rationale: no team-owned fine-tune or retrieval corpus. Vendor-side poisoning is covered by LLM03 governance posture."*
5. **LLM05 Improper Output Handling — correct Y; WRONG review section (should be S6 Security, not S4 Verification run); the `eslint` layer is the wrong tool for a Python team; the eval is correct in shape.** Chapter 6 crosswalk is explicit: LLM05 maps to S6 Security. The Python team's security linter should be `semgrep` or `bandit`, not `eslint`. The reply flow specifically needs output-sanitisation review — a model-drafted reply that interpolates a customer-provided string without escaping into an HTML-rendered dashboard or a downstream shell is this row's archetypal failure. **Companion commission to `@risk-peer` is warranted** — the open Q3 finding most likely lives here.
6. **LLM06 Excessive Agency — WRONG N; should be Y.** The reply flow is agent-authored text that will be *sent to external customers* (after sr-eng review, but still). "Excessive agency" is specifically about *more tool/authorisation surface than the task requires*. Even without additional tools, the question of *which classes of reply the agent is authorised to draft* (refund offers? apology-for-regulated-dispute? legal statements?) is a Chapter 6 LLM06 question. The AGENTS.md "approved tool list" + a CI check that new tool connections require an ADR is the correct standards-as-code layer; an Inspect-AI capability eval is the correct regression gate. **Companion commission to `@risk-peer`** for the "refuses to draft class X reply" claims.
7. **LLM07 System Prompt Leakage — correct Y; correct section and layer; the eval is correct in shape but should name `@risk-peer`** as the owner. Chapter 6 crosswalk: LLM07 is capability-eval-shaped and is squarely in the `ai-risk-engineer` commissioning bucket (extraction-attempt prompts, output-filter verification).
8. **LLM08 Vector and Embedding Weaknesses — should be out-of-scope-with-rationale.** This team has *no retrieval pipeline* and no embedding model. Filling in "retrieval pipeline pin" and "regression eval" invents infrastructure. Correct entry: *"Out-of-scope at review-time. Rationale: no team-owned retrieval pipeline or embedding store. Revisit if the team adds retrieval."*
9. **LLM09 Misinformation — correct Y; correct section and layer; the eval is correct in shape BUT scope is wrong.** The Lab 02 commissioned eval covers the *summary* flow on faithfulness. The *reply* flow faithfulness is unmeasured; a customer-visible false statement by the agent is the archetypal LLM09 incident. Add: *"golden-task eval on reply flow — commissioning brief is a follow-on to the Lab 02 brief; owner `@senior-ic-3`, co-owner to be named."*
10. **LLM10 Unbounded Consumption — WRONG N; should be Y with a short-form response.** Even without agent loops, the team has per-call token cost. A missing per-agent token budget means a single misprompted session can blow a daily budget. Chapter 6 crosswalk: S4 Verification run + S6 Security; per-agent token budget configured; CI check for unbounded loops in orchestration. Not a `@risk-peer` row; this is operational and belongs with Platform (see `mod-111` for vendor-budget governance).

Hand-off line correction: *"Reviewed by `@risk-peer`, 2026-11-04. Agreed scope: `@risk-peer` commissions the capability-eval for LLM01, LLM05, LLM06, LLM07; the team covers LLM02, LLM09 (summary flow), LLM10 at review-time; LLM03, LLM04, LLM08 are out-of-scope-with-rationale this quarter."* The sample's "reviewed, approved" does not record the agreement and so is not actionable.

### Step 5 — Diagnose misses (5 min)

For every row where your call diverged from the key, write one line naming which of the three Chapter 6 failure modes you fell into:

- **Generic-filler mode** — you filled in a layer that did not actually exist (retrieval corpus pin on a team with no retrieval corpus; eslint on a Python team).
- **Wrong-section mode** — you attributed an S6 Security row to S3 Correctness or S4 Verification run (LLM02 and LLM05 are the two most common).
- **Silent-skip mode** — you marked a row N when it was actually Y (LLM06 or LLM10).
- **Over-filing mode** — you marked a row Y when it should be out-of-scope-with-rationale (LLM03, LLM04, LLM08).

The failure mode name is diagnostic; Chapter 6's "A row with 'out-of-scope' is a valid outcome. … The rationale is the artifact" is the corrective.

### Step 6 — Identify the two companion commissions to `@risk-peer` (5 min)

Based on your findings, which two rows most urgently warrant a one-paragraph companion commission to `@risk-peer`? Write the two commission paragraphs in the Chapter 4 one-paragraph shape (decision + scope + eval shape + tool + owner + loop + sunset — condensed to one paragraph). These paragraphs live in your team's commissioning backlog alongside the Lab 02 brief.

Hint: LLM01 (reply flow prompt-injection capability) and LLM05 (reply-flow output handling) are the strongest candidates; LLM06 and LLM07 are close seconds. Choose the two that you believe your `@risk-peer` would most benefit from having concrete.

### Step 7 — Reconcile the three prior artifacts (5 min)

Chapter 6: *"Updates to Exercise 01's PR template. The S6 Security section references the crosswalk; the specific OWASP LLM0x rows the reviewer must look at are listed."* And: *"Updates to Exercise 03's security linter. At least one lint rule carries a comment / doc-reference to the OWASP row it encodes."* And: *"Updates to Exercise 04's commissioning brief(s). Each brief notes which OWASP row(s) its eval is the regression gate for."*

Write three one-line notes:

- Which S6 Security rows should the PR template now surface by OWASP number?
- Which lint / security-linter rules should carry OWASP-row comments?
- Which commissioning brief needs an OWASP-row attribution added?

## Expected output

A single scratch file, roughly two pages, containing:

- Ten row-by-row entries (applies? review section? stack layer? eval? `@risk-peer` companion?) with one-line rationales.
- One hand-off-line correction.
- A diagnosis of each miss by failure mode (generic-filler / wrong-section / silent-skip / over-filing).
- Two one-paragraph companion commissions to `@risk-peer`.
- Three one-line prior-artifact reconciliation notes.

Something like:

```
Row 2 (LLM02) — Partial.
  Sample: Y, S3 Correctness, ruff, TBD.
  Correct: Y, **S6 Security**, detect-secrets + "no PII in prompts" AGENTS.md
    rule, regression eval on sensitive-data probe.
  Diagnosis: wrong-section mode. The Chapter 6 crosswalk is explicit.
  Fix: edit v0.1 to move the row to S6; name the specific stack layer.

Row 8 (LLM08) — Over-filing.
  Sample: Y, S6 Security, retrieval pipeline pin, regression eval.
  Correct: Out-of-scope at review-time. Rationale: no team-owned retrieval
    pipeline or embedding store. Revisit if retrieval is added.
  Diagnosis: over-filing mode (inventing infrastructure to fill the row).
```

## Checkpoint

Before moving on to Exercise 06 (where you build the crosswalk for **your own** team's workflows against a live OWASP page re-pull), you should be able to answer **yes** to all five:

- Did you correctly flag at least eight of the ten rows (either correct call or correct failure-mode diagnosis)?
- Did you correctly classify the three "should-be-out-of-scope-with-rationale" rows (LLM03, LLM04, LLM08) as over-filing misses in the sample, and write rationales that would survive a `@risk-peer` challenge?
- Did you correctly flip the two silent-skip rows (LLM06, LLM10) to Y with the right standards-as-code layer?
- Did your two companion-commission paragraphs cite the Chapter 4 brief shape and name `@risk-peer` as owner — honouring the Chapter 7 boundary (manager commissions, peer builds)?
- Did your hand-off-line rewrite record *what was agreed* (which rows `@risk-peer` commissions vs. which the team covers at review-time) rather than a generic "approved"?

If any answer is no, re-read Chapter 6's "The crosswalk table" and "A reading posture, not a certification" sections — and Chapter 7's "Three failure modes on this boundary" — before running Exercise 06 on your team's workflows. If your Python team mis-attributed `eslint` or if your retrieval-less team filled in a retrieval-pipeline pin, the Chapter 6 discipline *"your team's crosswalk is the mapping, not the research"* is the one to internalise.
