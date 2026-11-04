# Exercise 01 — NIST AI RMF GOVERN Function Translated to Team Practice

**Estimated effort:** 3 hours.

## Objective

Produce **v0.1 of your team's NIST AI RMF GOVERN crosswalk**: a filled-in table — one row per team-grain GOVERN subcategory — mapping the subcategory to the specific team artifact that evidences the practice, the upstream policy it inherits from, and the gap (if any) with owner and due date.

The crosswalk is the backbone of the Chapter 7 upward evidence packet and the artifact the `senior-ai-governance-architect` consumes first. The methodological anchors are [NIST AI RMF 1.0](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf) (AI 100-1) and the [NIST AI RMF Playbook](https://airc.nist.gov/AI_RMF_Knowledge_Base/Playbook). The team-scope translation is grounded in [Chapter 2](../02-nist-ai-rmf-govern-translated-to-team-practice.md).

## Prerequisites

- [Chapter 1](../01-the-governance-problem-at-team-scope.md) — the five pieces of mod-110 and the scope boundary.
- [Chapter 2](../02-nist-ai-rmf-govern-translated-to-team-practice.md) — the GOVERN subcategory list and the crosswalk shape.
- [Chapter 4](../04-articles-14-and-50-human-oversight-and-transparency.md) — the trigger list for GOVERN 1.4.
- The organisation's AI-governance policy, control library, or GRC catalogue, if one exists. If none exists, the crosswalk flags this as a root gap.
- Prior-module artifacts your team has produced:
  - [`mod-103`](../../mod-103-review-standards-and-eval-commissioning/) review checklist, standards-as-code stack, eval commissioning records, accountability contract.
  - [`mod-105`](../../mod-105-team-ai-enablement-programs/) enablement curriculum.
  - [`mod-106`](../../mod-106-workflow-redesign-and-agent-delegation/) routing matrix, HITL checkpoints, delegation ladder, tool-authorisation policy.
  - [`mod-109`](../../mod-109-accountability-incident-response-and-blameless-postmortems/) incident runbook, routing contract, retrospective.
- 30 minutes with your `senior-ai-governance-architect` or `head-of-ai-governance` contact (or their delegate), if one exists at the organisation, to confirm which upstream policies the crosswalk should inherit from.

## Problem statement

Your team runs AI-augmented work. You have produced, across prior modules, artifacts that *would* support NIST GOVERN subcategory evidence, but the artifacts are not labelled by subcategory. The Chapter 7 upward packet depends on a crosswalk that labels them. Without the crosswalk, the governance program cannot consume your evidence; with the crosswalk, the governance program can roll your evidence into its program view.

The exercise's scope is specifically *mapping and gap-identification* — it is not producing new policy or re-authoring team artifacts. Policy that is missing routes upward as a gap; team artifacts that are missing route back into the backlog of the module that owns them (e.g., a missing routing matrix routes to [`mod-106`](../../mod-106-workflow-redesign-and-agent-delegation/)).

The common failure mode the exercise prevents: a crosswalk that says "yes" in every cell without a specific artifact citation. A cell without a link is not evidence; an auditor will ask for it, find nothing, and the cell is now a credibility problem. Every "yes" cell has a link or a dated gap marker.

## Steps

1. **Fetch the Playbook subcategory list for GOVERN.** Pull the current list from [the NIST AI RMF Playbook](https://airc.nist.gov/AI_RMF_Knowledge_Base/Playbook) (the Playbook is updated; use the current live version, not a cached copy). Confirm the subcategory list matches Chapter 2 — if NIST has added or renumbered subcategories, update the crosswalk shape.
2. **Draft the empty crosswalk table.** Four columns: subcategory (with NIST reference), team-scope interpretation, backing team artifact, backing upstream artifact. Add two trailing columns for gap-marker fields: *owner* and *due date*.
3. **Fill in-scope subcategories.** Start with the 12 Chapter 2 names GOVERN 1.2, 1.3, 1.4, 2.1, 2.2, 2.3, 3.2, 4.1, 4.2, 4.3, 5.1, 6.1, 6.2 and extend to any others the Playbook's current version names team-grain. For each:
   - Write a *one-sentence* plain-language team-scope interpretation. Do not paraphrase NIST; name what your team actually does.
   - Cite the backing team artifact with a specific link (wiki URL, repo path, or LMS record).
   - Cite the backing upstream artifact (program policy, control library entry, legal position). If none exists, leave the upstream cell empty and record a gap in the trailing columns.
4. **Fill out-of-scope / organisation-only subcategories.** GOVERN 1.1, 1.5, 1.6, 1.7 and any others the Playbook flags as organisational. Record these as "manager contributes; does not own" with a short note on the team's contribution (if any).
5. **Fill the DEI / workforce subcategories by cross-reference.** GOVERN 3 subcategories on workforce diversity and competency route to [`mod-108`](../../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/). Cite the specific chapter and artifact per subcategory.
6. **Pass the crosswalk by the architect / governance partner.** 30 minutes. Ask: *are we pointing at the right upstream policies?* *are any of our team artifacts in the wrong column?* *what does the program expect in the gap register that we are missing?* Record the specific corrections.
7. **Author the gap register.** For every unfilled or route-upward cell, produce a row with: gap, source cell, owner (role), owner (person), due date, routing (upward / sideways / team-backlog), notes. Order by routing (upward routes first; team-backlog routes last). The gap register is a separate section of the packet in Chapter 7.
8. **Finalise the crosswalk's change-log.** Who authored, who reviewed, when. v0.1.
9. **Validate against one worked question.** Pick one Playbook *transparency and documentation* question per in-scope subcategory. For each, trace: does the cited team artifact actually answer this question? If not, the artifact is either in the wrong cell or the artifact is incomplete; amend.
10. **Decide rollout.** Crosswalk v0.1 is adopted after architect sign-off. It is updated at every quarterly packet; any material change between quarters (new workflow, framework update, incident with crosswalk implications) triggers an off-cycle amendment.

## Starter guidance

- **The crosswalk is a *mapping* artifact, not a *policy* artifact.** You are not writing new policy. You are pointing at policy and practice that exist (or marking their absence). A crosswalk that tries to write policy will not be adopted and will not be credible.
- **One-sentence interpretations are mandatory.** A paraphrased Playbook sentence is not an interpretation. "GOVERN 2.2 — our team completes the firm's mandatory AI-fluency curriculum tier-by-tier, with quarterly refresh and incident-driven micro-sessions" is an interpretation. "GOVERN 2.2 — personnel receive AI training" is a paraphrase.
- **Citations must be specific URIs.** `drive://ai-governance/review-checklist-v2.3.md` or `https://github.com/acme/standards/blob/main/.cursor/rules/ai-review.md` is a citation. "the review checklist" is not.
- **Gaps are gifts.** The crosswalk's gaps are the Q2 backlog for the manager and the Q2 backlog for the architect. Fill them as gaps, not as excuses; owner and date are mandatory.
- **Playbook transparency questions are the acceptance criteria.** For any cell you are unsure about, open the Playbook's *Transparency and documentation* section for that subcategory; see whether your team actually answers the questions listed. If not, the cell is not yet green.
- **Use the Chapter 2 example row** (GOVERN 2.2 filled, for a specific team) as the quality bar; every cell should be at that density.
- **Do not duplicate `ai-risk-engineer` evidence.** GOVERN subcategories that cover engineered risk (prompts, red-team, guardrails) point at `ai-risk-engineer` commissioning records. The manager cites; the manager does not re-run.
- **One-page gap register at the top helps readability.** Full crosswalk is the body; the gap register as a leading summary table is what the architect reads first.

## Acceptance criteria

The crosswalk is complete when:

- All 12 team-grain GOVERN subcategories from Chapter 2 have rows with:
  - A one-sentence team-scope interpretation, not a paraphrase of NIST.
  - A specific team artifact citation (URL or repo path) OR an explicit gap marker with owner and date.
  - A specific upstream artifact citation OR an explicit gap marker with owner and routing.
- Any additional subcategories the current Playbook names team-grain are included.
- Organisation-only subcategories (GOVERN 1.1, 1.5, 1.6, 1.7, and any others) are recorded with a "manager contributes; does not own" note.
- GOVERN 3 workforce / DEI subcategories cross-reference to [`mod-108`](../../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/) with specific chapter and artifact references.
- The gap register is a separate leading section, with routing explicit (upward / sideways / team-backlog), owners named, due dates set.
- An architect or governance-partner review has produced specific corrections that are reflected.
- Playbook *Transparency and documentation* questions have been checked against the cited artifacts for each in-scope subcategory.
- A change-log entry names authors, reviewers, and date. v0.1.
- The crosswalk is filed at a specific location in the team's wiki or governance drive, with a link in the Chapter 7 upward-packet template.

## Stretch goals

- **Cross-walk the organisation's bespoke control library.** If the organisation maintains its own control catalogue (common in financial services, healthcare, EU-based organisations), add a trailing column mapping each subcategory to the organisation's control ID. This makes the architect's work faster.
- **ISO/IEC 42001 cross-reference.** If the organisation is pursuing [ISO/IEC 42001:2023](https://www.iso.org/standard/81230.html) certification for its AI management system, add a column mapping each subcategory to the 42001 clause. The architect decides whether this cross-reference is maintained at team scope or at program scope; team-side contribution is often welcomed.
- **Automation of the gap-register update.** Maintain the crosswalk in a structured format (CSV, YAML, or a simple spreadsheet) so the gap register can be auto-generated for each quarterly packet. One-off manual packets are brittle.
- **Workflow-aware crosswalk.** Where the team has multiple workflows, annotate each row with which workflows it applies to. A GOVERN 4.3 incident-detection row applies to every workflow; a GOVERN 1.4 regulated-workflow row applies only to in-scope ones. Workflow annotation makes the Chapter 4 Article-14 and Article-50 sheets easier to maintain.
- **Pre-fill against a historical quarter.** Take the team's prior quarter (before the crosswalk existed) and fill the crosswalk as if it had been in place. This exposes gaps between "we did it" and "we have evidence for it" that are useful to surface before the first live packet.
- **Compose with [Exercise 05](exercise-05-upward-evidence-packet-for-governance-program.md).** Exercise 05 produces the upward packet; Exercise 01 feeds its NIST section. Author them in sequence or at least pass the gap register from 01 into 05's template.
