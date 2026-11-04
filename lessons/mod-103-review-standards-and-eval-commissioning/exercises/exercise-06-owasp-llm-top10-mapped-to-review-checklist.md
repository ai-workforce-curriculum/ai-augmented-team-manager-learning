# Exercise 06 — Mapping OWASP LLM Top 10 to Your Review Checklist

**Estimated effort:** 2 hours.

## Objective

Produce a **row-per-risk crosswalk** from the OWASP Top 10 for LLM Applications (<https://owasp.org/www-project-top-10-for-large-language-model-applications/>, current published version) into your team's review checklist (Exercise 01), standards-as-code stack (Exercises 02–03), and commissioning backlog (Exercise 04). Your deliverable is a single document — `docs/ai-review-owasp-crosswalk.md` or equivalent — plus the updates to the three existing artifacts to reference the crosswalk at the right points.

## Prerequisites

- Chapter 6 of this module.
- Exercises 01, 02, 03, and 04 at v0.1 or later. The crosswalk operates on the artifacts those exercises produced.
- Live read of the OWASP page before starting. Do not work from the table in Chapter 6 — re-pull titles and descriptions from <https://owasp.org/www-project-top-10-for-large-language-model-applications/>, because OWASP rotates the list periodically (notably between the 2023 and 2025 versions). If an older version is pinned anywhere in your prior work, this is the exercise where you update it.
- Awareness that depth beyond the review-time altitude belongs to [`ai-risk-engineer`](https://github.com/ai-governance-curriculum/ai-risk-engineer-learning) (L25, AI Governance). Chapter 7 is the boundary.

## Problem statement

OWASP's Top 10 is published; your team's checklist is bespoke; the eval backlog is in flux; the standards-as-code stack is young. Nothing connects the four except the manager who wrote them. The crosswalk is the connection — it ensures that for each of the ten risks, the team has an answer to *"where in our stack does this risk get caught?"*

You will author:

1. **The crosswalk document.** One row per OWASP LLM risk. Four columns: *review section (Chapter 2 / Exercise 01)*, *standards-as-code layer (Chapter 3 / Exercises 02–03)*, *eval that catches regression (Chapter 4 / Exercise 04)*, *out-of-scope (explicit rationale if left empty)*.
2. **Updates to Exercise 01's PR template.** The S6 Security section references the crosswalk; the specific OWASP LLM0x rows the reviewer must look at are listed.
3. **Updates to Exercise 02's AGENTS.md / Cursor rules.** Each security-related rule carries a comment naming the OWASP LLM0x it addresses.
4. **Updates to Exercise 03's security linter.** At least one lint rule carries a comment / doc-reference to the OWASP row it encodes.
5. **Updates to Exercise 04's commissioning brief(s).** Each brief notes which OWASP row(s) its eval is the regression gate for; if none, this is explicit.

## Steps

1. **Re-pull the OWASP Top 10 for LLM Applications.** Open the project page; read each risk's definition, example attacks, and mitigation guidance. Note any changes vs. the version you studied in Chapter 6 (titles rotate between 2023 and 2025 releases). Pin the version date in your crosswalk document.
2. **For each of the ten risks, answer four questions:**
   - *Does this risk apply to any of our team's AI workflows?* If no, say so with one sentence of rationale. If yes, continue.
   - *Which section of our review checklist catches it?* Name the exact section from Exercise 01. If none, this is a checklist gap.
   - *Which layer of standards-as-code enforces it (even partially)?* Cursor rule / AGENTS.md section / lint rule / CI gate. If none, this is a stack gap.
   - *Which eval is the regression gate for it?* An existing or commissioned eval from Exercise 04. If none, this is a commissioning gap.
3. **Write the crosswalk as a table.** One row per risk; four or five columns. Keep it one page if possible, two at most. The rows with gaps (no checklist row, no stack layer, no eval) are visible — they are the backlog.
4. **Walk the gaps.** For each gap row, decide: (a) add a row to the checklist, (b) add a rule / section / lint rule, (c) commission an eval (this becomes an Exercise 04 follow-on), or (d) explicitly declare out-of-scope with rationale (e.g., LLM03 Supply Chain may be governance-time rather than review-time on your team). Document the decision in the crosswalk.
5. **Propagate the updates to the four prior artifacts.** Edit the PR template to reference OWASP rows in S6; add OWASP-tagged comments to Cursor rules and AGENTS.md security section; tag lint rules with their OWASP row; update the commissioning briefs.
6. **Dry-run one adversarial read.** Pick one closed PR from your team that was AI-authored. Open the crosswalk and the PR together. For each OWASP row that applies, confirm the review as-performed covered it. Note any gaps — these are indicators that the crosswalk needs a sharper review-section binding, not that the past review was individually wrong.
7. **Walk the crosswalk to your `ai-risk-engineer` peer (or the closest available).** Ten to twenty minutes. Confirm the boundary from Chapter 7: which rows should the team cover at review time and which should they commission from the peer? Record the agreement (or disagreement) at the bottom of the crosswalk.
8. **Freeze v0.1.** Title, date, source-page version date, authorship, change log.

## Starter guidance

- Each row should answer one question only: *at review time, where does this risk get caught?* Deeper risk engineering is not in scope here — do not try to describe attack construction or guardrail design in the crosswalk. Chapter 7 is the hand-off.
- A row with "out-of-scope" is a valid outcome. LLM04 Data and Model Poisoning may legitimately be out-of-scope at team-scope review time because the team does not fine-tune or curate retrieval corpora — the rationale is the artifact.
- The crosswalk should be read-in-two-minutes. A two-page document that is scanned beats a six-page document that is skipped.
- Resist the urge to invent attacks. The OWASP page carries example attacks for each risk; cite them (or short-form them). Your team's crosswalk is the mapping, not the research.
- When a risk applies to only some of your workflows, note that per-workflow. "Applies to our customer-reply agent; N/A on our test-skeleton agent."
- The gap list that falls out of this exercise is a concrete backlog that threads into your next commissioning brief (Exercise 04 round 2) and your next standards-as-code iteration (Exercise 03 round 2).

## Acceptance criteria

The crosswalk is complete when:

- The OWASP source URL and the source-page version date are pinned at the top of the document.
- All ten risks (LLM01 through LLM10) are listed, each with a one-line description in your team's words.
- For each risk, the four questions are answered: *applies to our team (y/n + rationale)*, *review-checklist section (Exercise 01)*, *standards-as-code layer (Exercises 02–03)*, *eval that catches regression (Exercise 04)*.
- Every gap is either (a) resolved by updating one of the prior artifacts and noted here, or (b) explicitly declared out-of-scope with rationale, or (c) added to the commissioning backlog as a future brief.
- Exercises 01, 02, 03, and 04 have been updated to carry OWASP row references at the right points.
- An adversarial dry-run on one closed AI-authored PR has been performed; findings documented.
- `ai-risk-engineer` (or the closest peer) has reviewed the crosswalk and the Chapter 7 boundary agreement is documented at the bottom.
- The artifact carries a title, date, authorship, and a change log.

## Stretch goals

- **AISVS mapping.** OWASP publishes an "AI Security Verification Standard (AISVS)" alongside the Top 10 — a longer-form set of verifiable requirements. Pick one or two rows of the AISVS most relevant to your team and pull them into the crosswalk as a second-tier reference. Depth hands off to your security partner / `ai-risk-engineer` peer.
- **Gen AI Red Teaming Guide.** OWASP's companion red-teaming guide names concrete red-team activities per risk. Pick one and draft a commissioning brief (Exercise 04 shape) for your `ai-risk-engineer` peer.
- **NIST crosswalk preview.** Map each OWASP row that applies to your team to the NIST AI RMF function (GOVERN / MAP / MEASURE / MANAGE) it most naturally connects to. Hand the result to your `ai-governance-analyst` peer or to the owner of [`mod-110`](../../mod-110-ai-governance-and-policy-at-team-scope/). The crosswalk becomes a rung in the team-scope-to-governance roll-up.
- **Public-facing crosswalk template.** Scrub your crosswalk of team specifics; publish it as a generic template a peer manager could fork. The field benefits from more public team-scope OWASP crosswalks. Pair with [`mod-112`](../../mod-112-cross-functional-leadership-and-ritual-calendar/) on cross-functional communication.
- **Quarterly refresh ritual.** Add the OWASP Top 10 re-pull to the quarterly ritual from Chapter 3's reconciliation. The point is that the crosswalk is a living document; title and example changes on the OWASP side should propagate into your artifacts within a quarter.
