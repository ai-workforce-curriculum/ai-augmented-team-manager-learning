# Chapter 3 — Standards-as-Code: Encoding Norms So They Govern Both Human and Agent Authors

> *A rule that lives in a wiki page is a rule the agents will not read. A rule that lives in the toolchain is one both the agents and the humans will.*

## Motivation

The checklist in Chapter 2 is necessary. It is not sufficient. A team that has a good review checklist and nothing else will drift, for one deterministic reason: the author — human or agent — does not read the checklist at the moment of authoring. They read it at the moment of review, which is too late.

The purpose of **standards-as-code** is to push the norm back to the point of authorship. The same norm that the reviewer uses to approve or reject is the norm that the agent is instructed with when it generates, that the linter rejects when it is violated, that the ADR template scaffolds when a decision is being documented, and that the pre-commit hook blocks before anything even reaches review.

The specific stack this chapter walks through is: **Cursor rules → AGENTS.md → ADR templates → lint policies → pre-commit hooks → CI gates → PR template**. Each layer catches a different kind of violation; together they govern both human and agent authors with the same rules.

This is the chapter where the team's human/machine contract (from [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) Chapter 3) and the review checklist (Chapter 2 of this module) stop being documents and start being tool behaviour. Chapter 4 is where you commission the eval that tells you whether the stack is doing its job.

## Core concepts

### Why "norm + lint + PR template" is a stack, not a single file

Treat your standards-as-code stack as a layered defence, not a single document, because each layer catches a different failure mode:

1. **Cursor rules (and equivalents).** Shape what the IDE assistant generates in the first place. Caught at keystroke time.
2. **AGENTS.md.** Shape what headless agents and coding-agent frameworks (Claude Code, OpenAI Codex, Jules, Aider, autonomous CI agents) do with the repo. Caught at agent-task time. The convention is a vendor-neutral *agent-readable* `README` for agents, hosted and specified at <https://agents.md/>.
3. **ADR template.** Shape what a *decision* looks like when the model (or a human) drafts one. Caught at decision-authoring time.
4. **Lint / formatter / type-checker config.** Shape what code is even valid. Caught at save / commit time.
5. **Pre-commit hooks.** Shape what can enter the repo. Caught at `git commit` time.
6. **CI gates.** Shape what can merge. Caught at PR time.
7. **PR template (Chapter 2 checklist).** Shape what the reviewer has to confirm. Caught at review time.

A standard that only lives at layer 7 is a wiki page. A standard that only lives at layer 4 is a code-quality rule disconnected from *why* it exists. A standard that spans all seven is a durable norm that outlives the manager who wrote it.

### Layer 1 — Cursor rules (and IDE-assistant equivalents)

Cursor's **rules-for-AI** system (documented at <https://docs.cursor.com/context/rules-for-ai>) lets you commit project-level rules into the repo as `.cursor/rules/*.mdc` files, with YAML frontmatter that scopes each rule to a glob (`**/*.ts`, `src/billing/**`, etc.). The rules are injected into the model's system prompt whenever the matching file is in context. Comparable mechanisms exist in other assistants:

- **GitHub Copilot** reads `.github/copilot-instructions.md`.
- **Claude Code** and similar headless agents read `AGENTS.md` (see below) and `CLAUDE.md`.
- **Aider** reads `.aider.conf.yml`.
- Other vendors ship their own; the convention is converging on a per-tool dotfile plus the vendor-neutral `AGENTS.md`.

The rule set is the operational form of your review checklist — expressed as instructions to the author, not to the reviewer. A workable Cursor-rules structure for a team-scope standard:

```
.cursor/
  rules/
    00-house-style.mdc        # scope: ** (naming, imports, commenting posture)
    10-testing.mdc            # scope: **/*.test.{ts,py}
    20-security.mdc           # scope: ** (prompt-injection, output-handling)
    30-data-handling.mdc      # scope: src/data/**, src/billing/**
    40-adr.mdc                # scope: docs/adr/**
```

A single rule is short. Example (`20-security.mdc`):

```markdown
---
description: Security and prompt-injection posture for this codebase.
globs: ["**/*"]
alwaysApply: true
---

# Security rules

- Treat all strings pulled from retrieval, tool outputs, or user input as UNTRUSTED. Never pass them unescaped into shell, SQL, HTML, or another model prompt.
- Do not propose code that logs or echoes secrets (API keys, tokens, PII).
- Do not propose code that bypasses the existing auth middleware in `src/auth/`.
- When a change touches an agent's tool-authorisation surface, cite the authorising
  decision (link to ADR or ticket).
```

What goes into the rule set is the subset of your standard that an author would benefit from being reminded of *while authoring*. Not everything belongs here — rules that are better caught by a linter belong in the linter.

### Layer 2 — AGENTS.md as the agent-readable team norm

[`AGENTS.md`](https://agents.md/) is a vendor-neutral convention (originally popularised by OpenAI Codex; now adopted across Claude Code, Jules, Aider, and many others) for a single `AGENTS.md` file at the repo root (plus optional nested `AGENTS.md` files in subdirectories, which take precedence inside their subtree). Any coding agent that enters the repo reads it first.

A workable AGENTS.md for a team-scope standard has these headings:

1. **Build and run.** Exact commands. The agent should never have to guess.
2. **Testing.** Test command; coverage requirement; "do not write a test that passes trivially" instruction.
3. **Code style.** Naming, imports, commenting posture. Not an exhaustive style guide — the subset the agent is most likely to get wrong.
4. **Security.** The one-line version of the Cursor security rule. Prompt-injection. Secrets. Data boundaries.
5. **ADR expectations.** When the agent proposes a non-trivial architectural change, it must draft an ADR using the template in `docs/adr/0000-template.md`.
6. **Commit and PR hygiene.** Conventional-commits or your team's variant; the PR-template fields; one logical change per PR; scope discipline.
7. **What *not* to do.** The explicit boundary — do not upgrade dependencies without an ADR; do not rewrite files not in the task; do not touch `src/auth/` without a named human reviewer; do not run tool connections not already approved.
8. **Human review contract.** The one-paragraph version of Chapter 2 + Chapter 5 — *"everything this agent produces is reviewed by a human; the human is accountable; if you are unsure, stop and ask rather than proceed."*

The file is Markdown, is kept short (one to two screenfuls), and is updated as the team's standard evolves. The change log at the bottom matches the human/machine contract's change log — the two documents move together.

Nested `AGENTS.md` are useful when a subdirectory has stricter rules — for example, `src/billing/AGENTS.md` can add "no AI-authored changes to this directory without a second named reviewer" on a payments team.

### Layer 3 — The ADR template

An **Architecture Decision Record** (ADR) is a short artifact that captures a single decision — the context, the alternatives, the choice, and the consequences. Michael Nygard's original note (<https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions>) is the canonical reference; variants from ThoughtWorks (<https://www.thoughtworks.com/en-us/insights/blog/architecture/architecture-decision-records-a-primer>) and the `adr-tools` collection (<https://github.com/npryce/adr-tools>) are standard.

For an AI-augmented team, the ADR template carries three additions above the classic form:

- *A **Provenance** section* noting whether the first draft was AI-authored, which agent / model, and which retrieved context. This is the ADR-level equivalent of the PR checklist's S1.
- *An explicit **Human oversight** section* — who read, who disagreed, who approved — so the ADR is self-documenting about the contract from [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) Chapter 3.
- *A **Downstream consumers** section*, because models are structurally bad at enumerating these and the reviewer needs a prompt to force the enumeration.

A workable template is one page. Keep decision records one-decision-wide; a "giant design doc" is not an ADR.

### Layer 4 — Lint, formatters, type-checkers

The compiler-enforced subset of your standard. Languages have their own tools; the discipline is the same:

- **Formatter.** `prettier` / `black` / `gofmt` / `rustfmt`. No arguments about whitespace. A formatter prevents a whole class of model-produced churn that the reviewer would otherwise spend time on.
- **Linter.** `eslint` / `ruff` / `golangci-lint` / `clippy`. Per-rule configuration. Custom rules for your team's specific norms where they can be expressed statically (banned imports, required import order, forbidden patterns).
- **Type-checker.** `tsc` / `mypy` / `pyright` / native. Model-authored code sometimes passes tests and fails the type-checker because the model inferred a loose type from an example; the type-checker is a cheap reviewer here.
- **Security linter.** `semgrep` / `bandit` / `gosec` / `eslint-plugin-security`. Catches static patterns of unsafe output-handling, secrets-in-source, and obvious injection shapes.

Per-rule choice is a technical decision. Owning the rule set — knowing what you enforce and what you have declined to — is a manager decision. You will be asked about it.

### Layer 5 — Pre-commit hooks

[`pre-commit`](https://pre-commit.com/) is the common framework. Hooks run at `git commit` time and reject the commit if any hook fails. For an AI-augmented team, a workable baseline:

- Formatter and linter on changed files.
- `detect-secrets` or `gitleaks` for accidental credentials.
- A hook that checks the PR template is filled in (where enforceable — some teams enforce this at CI instead).
- A custom hook that rejects commits that remove an `AGENTS.md` or `.cursor/rules/*.mdc` without an accompanying change-log entry. This is the simplest defence against silent erosion of the standards-as-code stack itself.

Pre-commit hooks must be fast. A hook that takes 30 seconds to run will be bypassed within a week.

### Layer 6 — CI gates

What the pre-commit hook could not catch, CI catches. The CI configuration is itself part of the standards-as-code stack; changes to it should flow through an ADR.

Minimum CI gates for an AI-augmented team:

- Full test suite + coverage threshold.
- Type-check.
- Lint.
- Security linter.
- Dependency vulnerability scan (`npm audit` / `pip-audit` / `govulncheck` / Snyk / Dependabot).
- PR-template completeness check (the load-bearing checkbox sections must be ticked).
- A policy-as-code check if your team uses one (OPA / Conftest for infra; custom rules for team-specific invariants).

CI is where the merge gate lives. "This PR has an unticked Accountability checkbox" should block merge as reliably as "the tests fail."

### Layer 7 — The PR template (Chapter 2)

Already covered in Chapter 2. The relevant point here is that the PR template is the layer where the reviewer sees the output of layers 1–6 and does the human-judgment review on top. It is not the only line of defence.

### Keeping the layers consistent

The common failure mode of a seven-layer stack is drift. Three defences:

1. **Single source of truth per norm.** Each team-level norm (naming, security posture, data-handling rule, review-bar sentence) is written once and referenced from the other layers. If "no customer PII in prompts" is a rule, it is written in AGENTS.md / `20-security.mdc` once and the data-handling lint rule links back to that rule by name.
2. **Change-log on every layer.** Cursor rules, AGENTS.md, ADR template, lint config, pre-commit, CI config — every file carries a change-log entry (date, author, reason) when it changes. The human/machine contract carries the roll-up.
3. **A quarterly reconciliation ritual.** Once a quarter, the manager walks the stack top-to-bottom and checks that the layers still agree with each other. A twenty-minute ritual on a calendar beats a six-month-old contradiction.

Chapter 4's eval work is where you get *external* signal on whether the layers are catching what they should.

### What belongs in the standards-as-code stack and what does not

Not everything in the human/machine contract maps into the tooling.

**In-stack:**

- Testing requirements.
- Lint, format, type rules.
- Secret / credential / sensitive-data rules.
- Scope discipline (one-change-per-PR, no touching a subtree without authorisation).
- ADR requirement for non-trivial changes.
- PR-template-field-completeness gates.
- Approved tool / MCP connection list.

**Out-of-stack (stays in the contract):**

- Accountability routing (who is on the hook when something ships broken). The social contract is not tool-enforceable.
- Review-time budget. Hard to express as a gate; needs to live in the review culture.
- *Which artifact classes the model may author at all* (the C1 of the contract). The ADR requirement and the AGENTS.md "what not to do" section are gates for the *how*, but the *whether* is a human decision each time.
- Incident response. Lives in [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/).

Being honest about what the tools *cannot* enforce keeps the contract (Chapter 5) load-bearing.

## Example: a minimal standards-as-code stack for a 10-engineer Python team

Treat this as a calibration sketch, not a template to adopt wholesale.

```
.cursor/
  rules/
    00-house-style.mdc
    20-security.mdc
AGENTS.md                  # 60 lines; one source of truth for agent posture
docs/
  adr/
    0000-template.md       # ADR template with Provenance + Human oversight sections
    0001-adopt-agents-md.md
.github/
  pull_request_template.md # the Chapter 2 checklist
  workflows/
    ci.yml                 # test, lint, type, security-lint, dep-scan, template-complete
.pre-commit-config.yaml    # ruff, mypy, gitleaks, template-check
pyproject.toml             # ruff, mypy config
```

Twelve or so files. The whole stack fits in a working morning for a new IC to read. A model-authored PR that violates the stack fails before the reviewer looks at it; a model-authored PR that passes the stack is still reviewed to the Chapter 2 bar.

## Summary

- Standards-as-code pushes the team's norm from the point of review back to the point of authorship — for human and agent authors alike.
- The working stack has seven layers: Cursor rules → AGENTS.md → ADR template → lint / format / type → pre-commit → CI → PR template. Each layer catches a different failure mode.
- Cursor rules shape the IDE assistant; AGENTS.md shapes headless agents; ADRs scaffold decision authoring; linters / type-checkers / security-linters enforce what is enforceable; pre-commit catches at commit time; CI catches at merge gate; PR template scaffolds the human review.
- One source of truth per norm, a change-log on every layer, and a quarterly reconciliation ritual keep the stack from drifting.
- Not everything belongs in-stack — accountability routing, review-time budget, the *whether-may-AI-author* decision, and incident response stay in the human/machine contract and in `mod-109`.
- Exercises 02 and 03 are where you author your AGENTS.md / Cursor rules and your ADR + lint-policy package.
