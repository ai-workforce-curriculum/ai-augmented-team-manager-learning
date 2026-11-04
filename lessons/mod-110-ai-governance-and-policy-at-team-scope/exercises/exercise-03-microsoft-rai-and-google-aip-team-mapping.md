# Exercise 03 — Microsoft RAI and Google AI Principles: Team-Scope Mapping

**Estimated effort:** 2 hours.

## Objective

Produce **v0.1 of your team's industry-framework mapping**: one mapping table per framework the organisation has publicly committed to or routinely references. Each table maps the framework's principles / goals to the team-scope evidence artifact that supports them, with composing artifacts and upward-routed gaps.

The methodological anchor is [Chapter 5](../05-microsoft-rai-and-google-ai-principles-mapping.md). Primary sources: [Microsoft Responsible AI Standard v2](https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-Responsible-AI-Standard-v2-General-Requirements-3.pdf) and [Google's AI Principles](https://ai.google/responsibility/principles/). The mapping is *defensive* — not a restructuring of team practice around industry language, but a view that the team can serve on demand when a customer questionnaire, partner responsible-AI commitment review, or internal commitment audit asks for one.

## Prerequisites

- [Chapter 5](../05-microsoft-rai-and-google-ai-principles-mapping.md) — the defensive-mapping discipline and the two mapping tables.
- Your organisation's public responsible-AI commitments (if any). Common forms: a page on the corporate website; a section of the annual report; the RFP response in the enterprise sales library; a customer-facing security-questionnaire template; an internal policy named "Responsible AI commitments".
- The Chapter 2 crosswalk (from [Exercise 01](exercise-01-nist-ai-rmf-govern-to-team-practice.md)) — the mapping points at the same artifacts the crosswalk points at.
- The team artifacts cited in Chapter 5's mapping tables ([`mod-103`](../../mod-103-review-standards-and-eval-commissioning/), [`mod-106`](../../mod-106-workflow-redesign-and-agent-delegation/), [`mod-108`](../../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/), [`mod-109`](../../mod-109-accountability-incident-response-and-blameless-postmortems/), Chapter 3, Chapter 4, Chapter 6 of this module).
- 15 minutes with the enterprise sales / responsible-AI lead at the organisation (where one exists) to confirm which frameworks the organisation actually commits to in external-facing materials.

## Problem statement

Your organisation has made public commitments to responsible-AI principles. The commitments typically cite one or more industry frameworks (Microsoft RAI, Google AIP, OECD AI Principles, or the organisation's own named principle set). When an audit — customer-security questionnaire, partner responsible-AI review, internal commitment audit — asks how team practice supports the commitment, the team has evidence it can point at, but the evidence is not labelled by the framework's language.

The exercise produces the labels. The mapping table for each framework points at the same artifacts the Chapter 2 crosswalk points at, but under framework-appropriate principle names.

The exercise explicitly does *not* restructure team practice to match industry language. The team's primary structure is the NIST crosswalk and the EU AI Act practice; industry-framework mapping is a view, not a rewrite.

The common failure mode the exercise prevents: a mapping that claims each principle is supported with "yes" cells, but where the cells cite "the review checklist" generically without specific artifact URLs. An audit that reads such a mapping and asks for one concrete artifact will surface that most of the "yes" is aspirational.

## Steps

1. **Confirm the organisation's framework commitments.** Which frameworks does the organisation publicly commit to? Which does it reference in customer-facing materials without committing to? Which does leadership internally benchmark against? The first category is required; the second is recommended; the third is nice-to-have. Build the mapping for at least the first.
2. **Fetch the current framework texts.** [Microsoft Responsible AI Standard v2](https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-Responsible-AI-Standard-v2-General-Requirements-3.pdf) and [Google AI Principles](https://ai.google/responsibility/principles/) are the two primary frameworks named in this module; fetch the current authoritative version of each. If the organisation commits to another framework (OECD, UNESCO, a bespoke principle set), fetch that too.
3. **Author the Microsoft RAI mapping.** One row per principle (Accountability, Transparency, Fairness, Reliability and safety, Privacy and security, Inclusiveness). For each row: primary team-scope evidence (specific artifact citation, URL); composing artifacts (links to other team modules); upward-routed gaps (what the team cannot itself provide — program-level fairness policy, impact-assessment library, etc.).
4. **Author the Google AI Principles mapping.** Same shape, one row per principle (Socially beneficial, Avoid unfair bias, Safety, Accountable to people, Privacy, Scientific excellence, Accord with these principles).
5. **Author a bespoke-commitment mapping if applicable.** If the organisation has published its own responsible-AI principle set (common at larger organisations and most financial-services organisations), author the same-shape mapping for it. If not, skip this step.
6. **Validate with one worked customer question per mapping.** For each framework, pick a plausible customer-questionnaire or partner-review question (e.g., "How does your organisation operationalise fairness in AI-produced outputs for the services covered by this contract?"). Draft a 1–3 paragraph response that points *only* at the mapping's cited artifacts. If you cannot produce a credible response from the mapping alone, the mapping has a gap.
7. **Confirm with the enterprise sales / responsible-AI lead.** 15 minutes. Review the mappings and the sample responses. Ask: *is this what you would hand to a customer? what would you change? which cells would trigger a follow-up question?*
8. **Author the gap-register section.** Every upward-routed cell becomes a row in the gap register (same shape as Exercise 01). Route to `senior-ai-governance-architect` or `head-of-ai-governance` per the cell's routing.
9. **Finalise and file.** v0.1 with change-log. File at a specific location. Link from the Chapter 7 upward-packet template.

## Starter guidance

- **Defensive, not aspirational.** The mapping cites what exists. It does not promise what the team will do. Aspirational cells become audit debt.
- **The same artifact can legitimately support multiple principles.** The [`mod-103`](../../mod-103-review-standards-and-eval-commissioning/) accountability contract supports MS RAI Accountability and Google AIP Principle 4 (accountable to people) and GOVERN 2.1 in the NIST crosswalk. One artifact, three citations. This is a feature, not a problem.
- **Upward-routed gaps are explicit.** A cell that says "the team contributes but does not own this principle — the organisation's program-level X owns it" is a valid mapping. Not every cell needs team-scope primary ownership.
- **Framework version matters.** Microsoft's RAI Standard moved from v1 to v2; Google's AI Principles have been updated multiple times. The mapping cites the framework version it is built against. Update when the framework updates.
- **Avoid translating team language into framework language.** If the team calls it "the review checklist", the mapping cites "the review checklist" with URL; it does not rename it "the Microsoft-RAI-aligned review assurance mechanism". The audit reads around framework language, not through it.
- **Short, specific, URL-dense.** The mapping is 1–2 pages per framework. Dense with specific artifact citations; thin on prose.
- **A principle that cites no team artifact and no gap routing is a mapping bug.** Either the team has evidence or the team routes the gap. There is no third option.

## Acceptance criteria

The mapping is complete when:

- A mapping table exists for each framework the organisation has publicly committed to or routinely references.
- Each row has: principle name, team-scope evidence (specific URL or path citation), composing artifacts, upward-routed gap (if applicable).
- Microsoft RAI mapping covers all six principles (Accountability, Transparency, Fairness, Reliability and safety, Privacy and security, Inclusiveness).
- Google AIP mapping covers all seven principles.
- Bespoke-commitment mapping exists where applicable.
- At least one worked customer / partner response has been drafted per framework, using only the mapping's cited artifacts, and the response reads credibly.
- The gap register section lists every upward-routed cell with owner (role and person where possible), due date, and routing (upward or sideways).
- The enterprise sales / responsible-AI lead has reviewed and provided specific corrections where one exists.
- A change-log entry names authors, reviewers, date, and framework versions. v0.1.
- The mapping is filed at a specific location and linked from the Chapter 7 upward-packet template.

## Stretch goals

- **Author OECD AI Principles mapping as a third table.** The [OECD AI Principles](https://oecd.ai/en/ai-principles) are widely referenced in government-facing commitments; adding them extends the mapping's reach. Same shape.
- **Author a UNESCO or ISO 42001 cross-reference.** The [UNESCO Recommendation on the Ethics of AI](https://www.unesco.org/en/artificial-intelligence/recommendation-ethics) and [ISO/IEC 42001:2023](https://www.iso.org/standard/81230.html) are cited in international and regulated-industry commitments. Add these as additional mappings if the organisation commits to them.
- **Produce reusable customer-response snippets.** For each principle in each framework, produce a 2–3-paragraph pre-written response that the enterprise sales library can reuse without re-querying the team. This scales the mapping's value across the organisation.
- **Automate the mapping as structured data.** Store the mapping in a structured format (CSV, JSON) so that the same artifact citation can be reused across multiple framework-rows and so that framework-updates can be partially re-generated.
- **Compose with [Exercise 05](exercise-05-upward-evidence-packet-for-governance-program.md).** The Chapter 7 packet's industry-framework section is this mapping plus the gap register. Author them in sequence.
- **Compose with [`mod-111`](../../mod-111-vendor-budget-and-tool-selection-at-team-scope/) tool registry.** Where a vendor's own responsible-AI statement is a filter criterion (Microsoft RAI-aligned, Google-AI-Principles-compatible, signatory of the EU AI Code of Practice), cite the tool registry in the composing-artifacts cell.
- **Benchmark against peer organisations.** Where a peer organisation has published a public responsible-AI report that cross-references MS RAI or Google AIP, read it for structure. Not for content — the team's evidence is specific — but for how peers organise their public responses.
