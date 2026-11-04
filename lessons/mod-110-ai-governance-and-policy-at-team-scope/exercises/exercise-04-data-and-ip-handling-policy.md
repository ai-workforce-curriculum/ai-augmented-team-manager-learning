# Exercise 04 — Data, IP, and Confidentiality: Author the Team Policy

**Estimated effort:** 2 hours.

## Objective

Produce **v0.1 of your team's data-and-IP handling policy**: the one-page data-class × tool-class matrix, the per-vendor clause-reader summary (referenced, not duplicated), a lightweight model-card record per selected model, the one-page IP sidecar, and the half-page data-leak trigger list.

The methodological anchor is [Chapter 6](../06-data-ip-and-confidentiality-practice.md). Grounding sources: the organisation's data-classification standard; the vendor contracts for each tool on the team's stack; counsel's IP position; the [Hugging Face model card](https://huggingface.co/docs/hub/model-cards) convention ([Mitchell et al., 2019](https://arxiv.org/abs/1810.03993)); the [`mod-106`](../../mod-106-workflow-redesign-and-agent-delegation/) tool-authorisation policy; the [`mod-111`](../../mod-111-vendor-budget-and-tool-selection-at-team-scope/) vendor registry.

## Prerequisites

- [Chapter 6](../06-data-ip-and-confidentiality-practice.md) — the operational pieces of the policy and the matrix design.
- [`mod-101`](../../mod-101-ai-augmented-team-manager-position-and-contract/) C5 clause of the human/machine contract.
- [`mod-106`](../../mod-106-workflow-redesign-and-agent-delegation/) tool-authorisation policy and delegation ladder.
- [`mod-109`](../../mod-109-accountability-incident-response-and-blameless-postmortems/) incident runbook — the data-leak trigger list is a slice.
- The organisation's current data-classification standard (usually from the privacy / security office).
- Vendor contracts for each tool on the team's stack. Where you do not have direct access, request the clause summaries from procurement.
- Counsel's current IP position on model outputs, derivatives, and open-source interactions.
- 30 minutes with the privacy / security office, 30 minutes with procurement, 30 minutes with counsel's partner (or their delegate).

## Problem statement

Your team's ICs make daily decisions about what data goes into which AI tool. The vendor contracts and the organisation's data-classification standard set the position, but in practice the IC does not know the clause-by-clause details; they know the shorthand ("Copilot Business is OK for most things", "do not use ChatGPT for customer stuff"). When the shorthand is wrong — on an unusual data class, on a vendor change, on a contract renewal with changed terms — the result is a data-leak incident that was preventable.

The exercise's deliverable is the one-page matrix that makes the shorthand correct and inspectable. The IC reads the matrix and knows, in 30 seconds, whether the thing they want to do is allowed. The audit reads the matrix and traces each cell to a contract clause. The data-leak incident is prevented because the matrix was consulted.

The exercise is specifically *operational* — it produces the matrix. The matrix references the vendor contracts, the counsel IP position, and the data-classification standard; it does not interpret them. Interpretation is counsel's; the matrix is the manager's.

The common failure mode the exercise prevents: a policy that has the right language ("do not expose confidential data to tools without zero-retention contracts") but no matrix — so ICs have to translate the policy for their specific case and get it wrong. The matrix is the translation, done once, with sign-off.

## Steps

1. **Read the organisation's data-classification standard.** List the tiers (usually 4–5). For each tier: the formal definition; common examples in your team's domain; common examples of near-misses (data that looks like one tier but is actually another).
2. **Inventory the team's tool stack.** Every AI tool on the team's stack, with its specific contract tier. Enterprise Copilot is distinct from consumer Copilot; Claude for Enterprise is distinct from Claude Pro; Gemini Enterprise is distinct from Gemini consumer. The contract tier is in the matrix column header.
3. **For each tool, fetch the vendor's current data-use terms.** Specifically: training-on-your-data; retention; residency; subprocessors; audit; deletion. Work from the contract (for enterprise tiers) or the terms of service (for consumer tiers). Procurement is the partner for this.
4. **Author the clause-reader summary per vendor.** Five fields per vendor (training-on-your-data; retention; residency; access and audit; deletion). Plain-language. Link to the authoritative contract clause. Note: if the organisation's [`mod-111`](../../mod-111-vendor-budget-and-tool-selection-at-team-scope/) tool registry already maintains this, reference it; do not duplicate. If not, this exercise seeds the entry.
5. **Draft the data-class × tool-class matrix.** Rows = data classes; columns = tool classes (with contract-tier distinctions explicit in headers). Fill each cell: **allowed**, **conditional**, or **prohibited**. Each allowed and conditional cell cites the specific contract clause that permits it. Each conditional cell names the specific condition (vendor clause citation, per-doc tagging, approval workflow).
6. **Review with privacy / security office.** 30 minutes. Walk the matrix with the privacy / security partner. They validate: does the matrix correctly map the organisation's data-classification standard? Are any cells over-permissive? Are any cells over-restrictive (and therefore going to be bypassed in practice)? Record corrections.
7. **Author the model-card records.** For each model the team has selected (within a vendor, if the team selects the model tier; and for self-hosted or open-weight models): identity, intended use at team scope, inputs/outputs, known limitations, evaluations referenced, operational constraints (tool-authorisation, HITL requirements, data-class permissions), change-log. One page each. Cross-reference to Hugging Face's [annotated model card](https://huggingface.co/docs/hub/model-card-annotated) for structure; cross-reference to the vendor's published model / system card where one exists.
8. **Author the IP sidecar.** One page. Fields: model-output ownership; derivative works and training data; open-source license interactions; third-party content; pre-existing confidentiality undertakings; attribution and disclosure. Each field reflects counsel's position (quoted or paraphrased per counsel's preference). Counsel signs off.
9. **Author the data-leak trigger list.** Half a page. Fields: what counts as a data-leak event; who to call (named roles and persons); what to preserve; what to escalate to counsel immediately; what *not* to do (do not delete logs; do not communicate externally; do not notify vendor unilaterally).
10. **Validate with worked examples.** Pick 5–10 real IC decisions in the last quarter (a prompt that went into a tool; a paste-in; a tool choice for a specific task). For each: trace through the matrix, the clause reader, and the IP sidecar; confirm the decision the matrix would recommend. Where the matrix would have changed the IC's decision, that is a signal the policy is improving practice.
11. **Review with counsel's partner.** 30 minutes. Counsel validates: does the IP sidecar accurately reflect counsel's position? Is the data-leak trigger list operationally aligned with the firm's breach-notification policy? Record counsel's specific corrections.
12. **Rollout.** Matrix v0.1 is adopted at a specific date. Communications plan: a team Q&A session; the matrix pinned in the wiki and in `#eng-ai-*` channels; a short message to the team that this is now the artifact of record. Incidents between policy publication and the first refresh are retrospectively evaluated against the matrix to surface misses.

## Starter guidance

- **The matrix is the policy, not the beginning of the policy.** If the matrix does not answer the question, the policy has a gap. Do not pretend the matrix is a quick start for a longer document; it is the document.
- **Every cell has a citation or it is a gap.** "Allowed" without a contract clause is unverified. The audit will ask.
- **Enterprise is distinct from consumer.** Make the contract-tier distinction explicit in column headers. A row that says "allowed in Copilot Business; prohibited in Copilot Individual" is not three rows; it is two columns with different cells.
- **Do not be more restrictive than counsel.** The matrix enforces what counsel has agreed to. If the matrix is more restrictive, work gets worked around; if less, the organisation is at risk. Match counsel.
- **Do not be more permissive than the vendor contract.** The clause-reader tells you the vendor's commitment. The matrix cannot grant permissions the contract does not grant.
- **Synthetic / anonymised paths are distinct from raw paths.** Where a workflow has a path for synthetic data (allowed) and a path for raw (prohibited), the policy names both. The transformation step is explicit.
- **Model-card records are lightweight.** Full research-grade model cards are the provider's job. Team-side records are 1 page with the fields in Chapter 6; they document the team's selection and its operational constraints, not the model's full behaviour profile.
- **IP is counsel's position.** The sidecar reports counsel; it does not derive counsel. "I think" has no place in the sidecar.
- **The trigger list points at mod-109.** Do not re-author the incident runbook. Point.

## Acceptance criteria

The policy is complete when:

- The data-class × tool-class matrix is one page, with rows (data classes) and columns (tool classes with contract-tier distinctions) filled. Every cell is one of allowed / conditional / prohibited.
- Every allowed and conditional cell cites a specific contract clause. Every conditional cell names the specific condition.
- A clause-reader summary exists for each tool column, with the five fields filled (training-on-your-data; retention; residency; access and audit; deletion). Or, the summary is a reference to [`mod-111`](../../mod-111-vendor-budget-and-tool-selection-at-team-scope/) where that registry maintains the summaries.
- A lightweight model-card record exists for each model the team has selected, covering identity, intended use, inputs/outputs, limitations, evaluations, operational constraints, change-log.
- The one-page IP sidecar covers the six fields (output ownership; derivatives; open-source license interactions; third-party content; confidentiality undertakings; disclosure), each reflecting counsel's position.
- The half-page data-leak trigger list covers the five fields (what counts; who to call; what to preserve; what to escalate to counsel; what not to do) and points at [`mod-109`](../../mod-109-accountability-incident-response-and-blameless-postmortems/) rather than duplicating.
- At least 5 worked examples have been traced through the matrix and confirmed to produce correct decisions.
- Privacy / security office review has produced specific corrections.
- Counsel review has produced specific corrections.
- A change-log entry names authors, reviewers, date. v0.1.
- The policy is filed at a specific location, pinned in the team's wiki, communicated to the team with rollout date, and linked from the Chapter 7 upward-packet template.

## Stretch goals

- **Automate matrix checks in CI.** For teams whose coding assistants interact with repositories, add a pre-commit or CI gate that checks for in-flight prompts containing patterns typical of restricted data (regex or ML-based classification). The gate is a defence-in-depth; the matrix remains the policy.
- **Tool-authorisation policy integration.** Compose with the [`mod-106`](../../mod-106-workflow-redesign-and-agent-delegation/) tool-authorisation policy so that tool access is gated on data-class scope. If a tool is not permitted for restricted data, the tool's access to repositories containing restricted data is also gated.
- **Draft an automated "compliance check" for AI prompts.** A pre-prompt gate ask: *what data class is in this prompt?* via a lightweight classifier or a UI check. Not a substitute for the matrix but a supplementary safeguard. Compose with the team's harness design.
- **Author a candidate-facing version for contractors / partners.** The sanitised one-page version that contractors can read without seeing the firm's internal classifications. Cross-reference to the Chapter 3 awareness-tier training for contractors.
- **Benchmark the matrix.** Where the organisation has sister teams with matrices, compare across teams. Common divergences (one team allows what another prohibits for the same data class and tool) are either program-level inconsistencies — route upward — or justified by workflow differences.
- **Compose with [Exercise 01](exercise-01-nist-ai-rmf-govern-to-team-practice.md) and [Exercise 03](exercise-03-microsoft-rai-and-google-aip-team-mapping.md).** This policy fills GOVERN 1.2, 4.2, 6.1, 6.2 in the crosswalk and the Privacy-and-security cells in the industry-framework mapping. Cross-reference explicitly.
- **Pre-fill a historical incident against the matrix.** Take the team's most recent data-handling near-miss (a paste-in that shouldn't have happened; a vendor change that could have leaked data; a model-swap that changed retention) and trace what the matrix would have done. Surfaces gaps in the matrix and calibrates the trigger list.
