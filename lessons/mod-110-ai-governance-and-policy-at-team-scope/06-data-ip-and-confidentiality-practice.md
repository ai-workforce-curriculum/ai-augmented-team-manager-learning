# Chapter 6 — Data, IP, and Confidentiality: The Team's Operational Policy

> *The organisation's privacy policy, data-classification standard, and vendor contracts set the position. The team's job is to make the position operational: a one-page chart on the wall that answers, for every real workflow, which data class goes into which tool, and what the manager has to do when the answer is "neither of the above."*

## Motivation

Of all the AI-governance work at team scope, data and IP handling is the most frequent *live* question. The IC in front of their editor on Thursday morning does not need to look up NIST subcategories or the EU AI Act Article numbers to do their work; they need to know whether they can paste the current ticket's contents into the agent. The vendor's data-use clauses the organisation negotiated two quarters ago mean nothing if the IC does not know they exist.

The manager's job in this chapter is to translate three upstream layers into one operational team-scope artifact:

1. **The organisation's data-classification standard.** Usually a four- or five-tier scheme (public, internal, confidential, restricted, sometimes regulated). Owned by the privacy / security office; the team inherits.
2. **Vendor data-use clauses.** The specific contractual position with each AI tool vendor on training-on-your-data, retention, residency, subprocessors, auditability. Usually negotiated by procurement and legal; the team inherits — and operates against the clauses on a daily basis.
3. **IP position on model outputs.** Whether the organisation has a position on ownership of model outputs, derivative works, open-source-license interactions with AI-generated code, and the manager's accountability for the team honouring the position.

The output is the team's **data-and-IP handling policy** — one page, operationally runnable, with a sidecar page for IP, that answers the Thursday-morning question for every real workflow.

Chapter 6 compose with:

- The C5 clause of the [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) human/machine contract (*"what AI may see"*) — the policy is the operational form of C5.
- The [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) tool-authorisation policy — the data policy filters what *data* is allowed; the tool-authorisation policy filters what *tools* are allowed, and the two compose.
- The [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) tool registry and vendor-governance practice — where the vendor data-use clauses are maintained; Chapter 6 reads from it rather than re-maintaining a duplicate.
- The [Hugging Face model card](https://huggingface.co/docs/hub/model-cards) practice (which [originates in Mitchell et al., 2019](https://arxiv.org/abs/1810.03993)) for self-hosted or open-weight models the team selects; the manager maintains a lightweight model-card record per selected model.

This chapter does three things. First, it names the four operational pieces of the policy. Second, it describes the Hugging Face model-card discipline at team scope. Third, it names the IP sidecar — the one-page position on outputs, derivatives, and open-source-license interactions.

## Core concepts

### The data-class × tool-class matrix

The core artifact. A table whose rows are the organisation's data classes and whose columns are the team's tool classes. Each cell is one of **allowed**, **conditional**, or **prohibited**, with a short justification and a link to the vendor clause that supports it.

A composite illustration — the team's actual matrix will be specific to its vendor list and the organisation's classification scheme:

| Data class | Local-only IDE (no cloud) | Enterprise coding assistant with zero-retention contract (e.g., Copilot Business / Enterprise, Claude for Enterprise) | Consumer AI chat (no enterprise contract) | Vendor-hosted RAG over internal docs | Self-hosted open-weight model |
|---|---|---|---|---|---|
| Public | allowed | allowed | allowed | allowed | allowed |
| Internal (non-sensitive) | allowed | allowed | conditional (vendor training risk) | allowed | allowed |
| Confidential | allowed | conditional (vendor clause citation) | prohibited | conditional (per-doc tagging) | allowed |
| Restricted (customer data, financial data, PII) | allowed | prohibited | prohibited | prohibited (unless specifically approved) | conditional (per-model deployment review) |
| Regulated (PHI, PCI card data, GDPR special category) | manager + counsel sign-off | prohibited | prohibited | prohibited | prohibited |

Three design points about the matrix:

- **"Conditional" is not "ask your manager."** Each conditional cell names the *specific* condition — the vendor clause, the tagging requirement, the approval workflow, the audit trail. If the condition is not written down, the cell is effectively prohibited: no IC can take a conditional action safely without ambiguity.
- **The matrix is the policy, not the beginning of the policy.** The IC should be able to answer their question by reading the matrix. If the matrix doesn't answer, the policy has a gap and the matrix is amended.
- **Every allowed and conditional cell has a vendor clause citation.** The clause is in the vendor's contract or terms-of-service. The link in the cell points at the specific clause (or the clause number in the organisation's contract repository). Without the citation, the cell is effectively unverified.

### The vendor data-use clause reader

For each vendor on the team's tool list, the policy records a short *clause reader* — a plain-language summary of the clauses that matter at team scope. Five fields per vendor:

1. **Training-on-your-data.** Does the vendor train models on your inputs? Under what conditions? Is there an opt-out? If opt-out exists, is the team actually opted out, and where is the evidence?
2. **Retention.** How long does the vendor retain inputs and outputs? Can it be configured shorter? What is the team's configured retention?
3. **Residency.** Where does the data physically live? Which jurisdictions have access? Does the vendor use subprocessors, and where?
4. **Access and audit.** Who at the vendor can access the data? What logs are available to the organisation? What audit rights are contracted?
5. **Deletion.** How is deletion requested and verified?

A vendor whose clauses do not satisfy the organisation's position for a given data class produces a *conditional* or *prohibited* cell in the matrix. The clause-reader entries are maintained by procurement in the [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) tool registry; the team-scope policy references them, does not duplicate them.

For the most commonly deployed enterprise AI tools in 2025–2026, the organisation typically has a *zero-retention* or *bounded-retention* enterprise contract — distinct from the consumer or default-tier contract. The team policy must distinguish the enterprise contract from the consumer product. A shared Google / ChatGPT / Claude account with the consumer terms of service is *not* the same thing as the enterprise or business tier with zero-retention terms. The policy says this out loud.

### The model-card discipline for team-selected models

Where the team *selects* a model — including the specific model tier within a vendor (e.g., *gpt-5-high* vs *gpt-5*; *claude-opus-4-8* vs *claude-haiku-4-5*), a self-hosted open-weight model, or a fine-tuned derivative — the team maintains a lightweight model card per the [Hugging Face model card](https://huggingface.co/docs/hub/model-cards) convention. The convention originates in [Mitchell et al., 2019](https://arxiv.org/abs/1810.03993) ("Model Cards for Model Reporting"). Hugging Face's [Annotated Model Card](https://huggingface.co/docs/hub/model-card-annotated) is a usable template.

A team-scope model card has a shorter shape than the research artefact; a workable set of fields:

- **Model identity.** Name, version, provider, access mode (API, self-hosted, embedded).
- **Intended use at team scope.** Which workflows use this model and why; what it is explicitly not for.
- **Inputs and outputs expected.** Type of inputs; type of outputs; sensitivity classification relevant to the data matrix.
- **Known limitations and failure modes.** What the model is bad at that the team has observed or that the provider has documented; relevant benchmarks or eval references from the mod-103 commissioning backlog.
- **Fairness and safety evaluations referenced.** Which published evals are relevant; which have been commissioned by `ai-risk-engineer` or run internally.
- **Operational constraints.** Tool-authorisation posture (which tools this model may call); HITL checkpoint requirements if any (per Chapter 4); data classes permitted (per the matrix).
- **Change-log.** When the model was adopted; when the version changed; when the card was last reviewed.

The team maintains one card per selected model. When a vendor silently changes a default (a familiar failure mode — see [`mod-109` Ch. 5](../mod-109-accountability-incident-response-and-blameless-postmortems/05-routing-contract-with-risk-engineer-and-secops.md) for the incident-response reading), the change-log and the Chapter 2 crosswalk capture it; the eval-regression gate from [`mod-103` Ch. 4](../mod-103-review-standards-and-eval-commissioning/) is the detection mechanism.

The model card is *lightweight*. For a team with four to six models in active use, the cards are one page each, one review per quarter, reconciled against the vendor's own model/system card where published.

### The IP sidecar

IP is a legal-position question above all else — counsel owns the interpretation. The team-scope artifact is a one-page *IP sidecar* that captures counsel's position in operational form:

- **Model-output ownership.** The organisation's position on who owns AI-generated outputs. For most commercial AI vendors in 2025–2026, the vendor disclaims ownership of outputs and the customer owns them subject to the vendor's TOS; counsel confirms per vendor.
- **Derivative works and training data.** If the team fine-tunes a model, the organisation's position on the tuned model's IP status and the training data's status.
- **Open-source license interactions.** What to do when AI generates code that resembles open-source code. The organisation's position, usually involving an attribution or review step, lives here. [Snyk's and GitHub's guidance](https://github.com/features/copilot) on managing IP risk from code-generation tools is a useful reference; counsel's position is authoritative.
- **Third-party content.** The organisation's position on AI output that reproduces or resembles third-party IP — common in text generation that pastiches published works.
- **Pre-existing confidentiality undertakings.** What to do when the team is contractually bound to not expose a counterparty's data to third parties; which vendors qualify; which do not.
- **Attribution and disclosure.** Where the team must disclose AI involvement in deliverables (customer deliverables, open-source contributions, published content, regulatory filings). Composes with Chapter 4 Article 50.

The sidecar is not the policy itself — the policy is counsel's — but it is operationally what the team members read.

### What leaves the premise

A specific rule worth calling out: *what leaves the premise when an IC pastes something into a vendor's tool*. In zero-retention enterprise-tier agreements, the vendor's commitment is often that inputs are not retained or used for training; the data still *left the premise* in the sense that it crossed the firewall and reached the vendor's infrastructure. The policy distinguishes:

- **Still allowed** — because the vendor's zero-retention contract and the data class match.
- **Allowed after transformation** — synthetic or anonymised versions of the data may go; the raw may not. The transformation step is explicit in the workflow.
- **Prohibited** — the data class is restricted or regulated for this vendor class even with zero-retention.

This distinction matters because ICs frequently equate "enterprise contract" with "anything goes". The policy explicitly disabuses this.

### Incident recovery for data-leak events

When data leaves the premise that should not have (an IC pastes restricted customer data into a vendor's tool outside the enterprise contract; a vendor's silent change expands retention; a misconfigured subprocessor routes data to a non-approved jurisdiction), the response is a specific sub-flow of the [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) incident runbook with additional SecOps and counsel engagement. The data policy's final section is a half-page trigger list:

- *What is a data-leak event?* The policy's definition in plain language.
- *Who to call.* The SecOps on-call, the counsel partner, the manager — in that order, named.
- *What to preserve.* The prompt, the response, the timing, the vendor session identifier, the user account.
- *What to escalate to counsel immediately.* Any event touching regulated data or an affected person.
- *What not to do.* Do not delete logs; do not communicate externally; do not post publicly; do not notify the vendor until SecOps and counsel have confirmed the step.

The trigger list is a slice of the mod-109 runbook, not a replacement.

### Jurisdictional and sector awareness, briefly

The data policy inherits jurisdictional and sector positions from the organisation; the manager does not re-derive them. A short list the manager must be *aware of* (not interpret):

- **GDPR and UK GDPR** on personal data, special category data, cross-border transfers, data-subject rights.
- **CCPA / CPRA** on California consumer data and automated-decision disclosures.
- **US sector statutes** where relevant — HIPAA (PHI), GLBA (financial data), FERPA (education records), COPPA (children's data).
- **The EU AI Act** data-governance requirements for high-risk systems (Article 10) — flow downstream to the data classes handled in regulated workflows.
- **Export-control classifications** (EAR, ITAR) for teams handling such content.

Each of these shows up in the matrix as a data class or as a constraint on a vendor clause. The policy does not interpret the statutes; it operates the organisation's inherited position.

## Example: a specific IC decision on Tuesday afternoon

Composite — calibration, not case study.

An IC on the financial-services team is working on a bug in the underwriting-assist workflow. They have a local repro that requires one anonymised real applicant record (name and identifier scrubbed) and want to paste it into Claude Code's enterprise session to help them trace a specific branch of the logic.

The IC opens the data policy's one-pager:

- Applicant record is classified **Restricted** (per the firm's classification standard).
- Column: **Enterprise coding assistant with zero-retention contract**.
- Cell: **prohibited** — *"Restricted data not permitted in Claude Code under current contract tier even with zero-retention; see clause reader for Anthropic enterprise contract (link); route request through tool-authorisation policy for restricted-data exception."*
- The IP sidecar: no override; the restriction is per data class, not IP.

The IC concludes: cannot paste the record. Routes:

- Synthetic-fixture path: generate a fixture that reproduces the branching behaviour without real data; synthetic is Internal; permitted.
- Specific-case path: the branch is irreproducible synthetically; the IC opens a tool-authorisation-policy exception request per mod-106, which routes to the manager for sign-off against the matrix with a specific justification.

The IC does not have to make a judgement call; the policy decides and the exception workflow handles the edge. The total elapsed decision time is 30 seconds. This is what a policy does for a team.

## Summary

- The data-and-IP policy at team scope is the **operational version** of the C5 clause of the human/machine contract ([`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/)). It makes the vendor contracts and the organisation's data-classification standard legible at IC altitude.
- The core artifact is the **data-class × tool-class matrix** — rows: data classes; columns: tool classes; cells: allowed / conditional / prohibited, each with the vendor-clause citation that supports it.
- The matrix is **operationally-sufficient**: an IC can answer their question by reading it. If not, the matrix has a gap and is amended.
- Each vendor has a **clause reader** entry covering training-on-your-data, retention, residency, access and audit, deletion. Maintained in [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) tool registry; referenced here.
- Each selected model has a lightweight **model card** per [Hugging Face model card](https://huggingface.co/docs/hub/model-cards) convention ([Mitchell et al., 2019](https://arxiv.org/abs/1810.03993)) — identity, intended use, inputs/outputs, limitations, evaluations, operational constraints, change-log.
- The **IP sidecar** captures counsel's position on model-output ownership, derivative works, open-source license interactions, third-party content, confidentiality undertakings, and disclosure. Operational, not interpretive.
- The policy names explicitly what **leaves the premise** — distinguishing enterprise zero-retention contracts from consumer products, and raw data from anonymised or transformed versions.
- A half-page **data-leak trigger list** names what counts, who to call, what to preserve, what not to do — a slice of the [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) runbook.
- **Jurisdictional and sector awareness** inherits from the organisation (GDPR, CCPA, HIPAA, GLBA, EU AI Act Article 10, export control, etc.); the manager does not re-interpret statutes.
- The policy folds into the Chapter 2 crosswalk at GOVERN 1.2, 4.2, 6.1, 6.2, into the Chapter 4 Article 14 workflow sheets as the data-handling column, and into the Chapter 7 upward packet as the data-and-IP section.
