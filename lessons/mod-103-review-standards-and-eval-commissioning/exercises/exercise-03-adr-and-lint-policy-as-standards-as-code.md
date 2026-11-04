# Exercise 03 — The ADR Template and Lint-Policy Package as Standards-as-Code

**Estimated effort:** 2 hours.

## Objective

Produce the **compiler-enforced and author-time-scaffolded** half of your team's standards-as-code stack: an **ADR template** (with AI-specific additions) and a **lint / pre-commit / CI policy package** that encodes the subset of your team's norms that can be mechanically enforced. The deliverables plug into the stack you authored in Exercise 02 — AGENTS.md and Cursor rules are the behavioural guidance; this exercise is the *enforcement* layer.

## Prerequisites

- Chapter 3 of this module.
- Exercises 01 and 02 (the review checklist / verification-bar table and the AGENTS.md / Cursor-rules pair).
- Familiarity with your team's actual lint / formatter / type-checker / security-linter stack (ruff, eslint, mypy, bandit, semgrep, golangci-lint, clippy — pick what applies).
- Read Michael Nygard's original ADR note (<https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions>) and skim the ThoughtWorks ADR primer (<https://www.thoughtworks.com/en-us/insights/blog/architecture/architecture-decision-records-a-primer>) before starting.
- Access to a repo where you can land pre-commit / CI changes, even if in a scratch fork.

## Problem statement

A norm that the linter can enforce is a norm the team does not have to argue about at code-review time. A decision that the ADR template demands be explicit is a decision the team cannot accidentally make in a corner of a PR. The purpose of this exercise is to encode the mechanisable subset of your team's standard — and to explicitly surface the non-mechanisable subset so you know what the humans still have to carry.

You will author:

1. **`docs/adr/0000-template.md`** — your team's ADR template, carrying a classic Nygard-style body plus the Chapter 3 AI-specific additions (Provenance, Human oversight, Downstream consumers).
2. **One or more real ADRs** using the template: at least one documenting the adoption of AGENTS.md on your team, and at least one documenting a specific agent-related technical decision (e.g., "we use retrieval model X", "we restrict MCP tool Y", "we require human sign-off on changes under `src/billing/`"). Minimum two ADRs.
3. **A lint-policy package** encoded in-repo: `pyproject.toml` / `.eslintrc` / `ruff.toml` / equivalent, with your team's actual rule-set, including at least one AI-work-specific custom rule (even if minimal — e.g., a banned pattern around secrets or unsafe output interpolation).
4. **A `.pre-commit-config.yaml`** (or your framework's equivalent) chaining the formatter, linter, type-checker, secret-scanner, and at least one custom hook that enforces the PR-template completeness or an AGENTS.md-presence check.
5. **A CI gate definition** (`ci.yml` or equivalent) that runs the full stack and blocks merge on failure, including a check for the PR-template's load-bearing fields being filled.

## Steps

1. **Classify the norms from Exercises 01 and 02.** For each norm in your PR template and in your AGENTS.md / Cursor rules, mark one of: *lint-enforceable* / *CI-enforceable* / *pre-commit-enforceable* / *ADR-scaffoldable* / *human-only*. The "human-only" set should not be empty — accountability routing and review-time budget belong there.
2. **Draft the ADR template.** Start from Nygard's shape (Title, Status, Context, Decision, Consequences). Add three sections for AI-augmented teams:
   - **Provenance.** Was the first draft AI-authored? Which agent / model / retrieval? Who prompted?
   - **Human oversight.** Who read, who disagreed, who approved. Named humans with dates.
   - **Downstream consumers.** Who depends on this decision; how are they notified; what is the rollback path.
3. **Write two concrete ADRs using the template.** One about adopting AGENTS.md (the decision, the alternatives, the consequences, including the Provenance / Human oversight / Downstream consumers sections). One about a team-specific agent decision (your pick).
4. **Configure the linter.** Formatter config, lint rules, type-checker strictness. At least one custom lint rule that encodes a team-specific invariant — e.g., ban a specific unsafe pattern (raw string interpolation of model output), require a specific import order, or ban a specific library known to produce hallucinated API examples on your language.
5. **Add a security linter.** Semgrep / bandit / gosec / clippy security-rules / eslint-plugin-security (whichever fits). Include at least one rule that targets an OWASP LLM Top 10 risk (Chapter 6) — e.g., untrusted-input-to-shell patterns (LLM05).
6. **Add secret / credential scanning.** `detect-secrets` or `gitleaks` in pre-commit. Set a baseline and document how to update it.
7. **Write the pre-commit chain.** Formatter → linter → type-checker → security linter → secret scanner → custom hook. The custom hook must enforce one of: (a) PR-template completeness on commit, (b) presence-check of AGENTS.md / `.cursor/rules/` (fail if a load-bearing file was deleted without an accompanying ADR entry), (c) presence of the Provenance / Human oversight sections in any ADR being added.
8. **Define CI gates.** Minimum: full test suite, lint, type-check, security linter, dependency vulnerability scan, PR-template field check. Each gate blocks merge on failure.
9. **Dry-run.** Make three test commits in the scratch repo: one clean, one that violates a format rule, one that violates the custom lint rule. Confirm each fails at the right layer with a message a human can act on.
10. **Document the enforcement map.** Produce a short `docs/standards-as-code-map.md` that lists each norm from the checklist / AGENTS.md and the exact layer that enforces it (or marks it human-only). This document is the quarterly-reconciliation worksheet from Chapter 3.
11. **Reconcile with Exercises 01 and 02.** Walk the full stack top-to-bottom. Any norm that is in one artifact but missing from another is drift. Fix.

## Starter guidance

- The ADR template's AI-specific additions should not be optional. If the Provenance section is left blank, the pre-commit hook rejects. Teams who make the sections optional will slowly stop filling them in.
- A lint rule is cheap to add and expensive to maintain. Pick rules that will *actually trigger* on your team's real code; a rule that never fires is noise. Favour tightening the rule-set over time rather than opening with everything turned on.
- Pre-commit hooks must be fast — ideally under 10 seconds for a typical commit on a laptop. A slow pre-commit chain is a bypassed pre-commit chain.
- CI gates should *fail loudly, clearly, and actionably*. "lint failed" is bad; "lint rule `no-raw-shell-interp` failed at `src/api.py:42` — model output is being passed unescaped to `subprocess.run`; see `docs/standards-as-code-map.md`" is good.
- Custom rules in semgrep / eslint-plugins / ruff plugins are the right place for team-specific invariants. Use pattern-match rules; avoid hand-rolling full AST walkers unless you have a maintainer for them.
- The standards-as-code map document is often more valuable than any individual rule. It is the artifact a governance partner, a VP, or a new IC can read to understand how the team's norms are enforced.
- The two example ADRs do not need to be long. Nygard's original examples are one page. Resist the design-doc impulse.

## Acceptance criteria

The package is complete when:

- `docs/adr/0000-template.md` exists with all three AI-specific sections (Provenance, Human oversight, Downstream consumers) in addition to the classic Nygard body.
- At least two real ADRs have been written using the template — one for AGENTS.md adoption, one for a team-specific agent decision — each on one or two pages, with every section filled.
- The lint config has at least one team-specific custom rule and at least one OWASP-LLM-aligned security rule.
- Secret / credential scanning runs in pre-commit with a documented baseline.
- `.pre-commit-config.yaml` chains the formatter, linter, type-checker, security linter, secret scanner, and one custom hook enforcing PR-template / AGENTS.md / ADR completeness.
- A CI gate definition exists that blocks merge on any of the above failing, plus the test suite and dependency vulnerability scan.
- A dry-run documented that commits pass and fail at the expected layers with clear messages.
- `docs/standards-as-code-map.md` lists every norm from Exercises 01 and 02 and the layer that enforces it (or marks it human-only). The human-only set is non-empty.
- Every file carries a change log.

## Stretch goals

- **Rule telemetry.** Track which lint / pre-commit / CI rules fire most often on AI-authored PRs vs. human-authored PRs. The ratio is diagnostic — if a rule only fires on model-authored work, the model has not been taught; if a rule only fires on human-authored work, the humans have not been taught.
- **Standards-drift alert.** Add a CI job that fails if `AGENTS.md` or `docs/standards-as-code-map.md` changes without an accompanying ADR entry. This is the single simplest defence against silent erosion of the stack.
- **Reviewer load reduction measurement.** Measure review time per PR on the week before the lint-policy roll-out and the week after. Honest answer may be "no change" or "slightly up (because reviewers now believe the floor is held and spend their time on higher-order review)." Either is a real finding.
- **External ADR publication.** Publish one of your ADRs — the AGENTS.md-adoption one is often a good candidate — as an external blog post or a conference-talk-length summary. The field benefits from more public team-scope ADRs. Pair with [`mod-112`](../../mod-112-cross-functional-leadership-and-ritual-calendar/)'s cross-functional communication work.
- **Enforcement-map review with governance.** Walk the standards-as-code map to a governance partner or `ai-governance-analyst` peer. Note which rows they would like to see rolled up into the governance crosswalk (`mod-110`). Map the rows; you have now bridged team-scope to governance-scope mechanically.
- **ADR archaeology.** For one in-flight or recently-shipped agent-related technical decision in your team that was *not* captured in an ADR, retroactively write it. The exercise surfaces the drift and gives you a candidate for the "we wish we had captured this earlier" pattern.
