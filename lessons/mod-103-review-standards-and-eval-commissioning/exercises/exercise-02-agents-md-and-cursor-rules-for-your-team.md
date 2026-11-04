# Exercise 02 — AGENTS.md and Cursor-Rules for Your Team

**Estimated effort:** 3 hours.

## Objective

Produce an `AGENTS.md` at the root of your team's primary repo and a small set of `.cursor/rules/*.mdc` (or the equivalent for your IDE assistant) that **encode the same norms your Exercise 01 PR template demands at review time — but at the point of authorship**. The artifact pair is your standards-as-code stack's human-and-agent-readable layer.

## Prerequisites

- Chapter 3 of this module.
- Exercise 01 — the PR template and verification-bar table. This exercise's deliverables should reference and extend, not contradict, Exercise 01.
- Working familiarity with your team's primary IDE assistant (Cursor / Copilot / Claude Code / equivalent). The authoring here is file-shape work; if you have never opened `.cursor/rules/`, do a quick walk of Cursor Rules documentation (<https://docs.cursor.com/context/rules-for-ai>) first.
- Read the AGENTS.md convention page (<https://agents.md/>) end-to-end once before starting. The convention is vendor-neutral; if your team uses only one coding agent, still author to the common convention — portability is an explicit value.

## Problem statement

Headless agents (Claude Code, OpenAI Codex, Jules, Aider, autonomous CI agents) and IDE assistants (Cursor, Copilot, Windsurf) are structurally incapable of following a norm they do not see. A norm that lives only in a wiki page is a norm that the next model-authored PR will not reflect. The purpose of this exercise is to put the norms where the authors — human and agent — will actually encounter them.

You will author:

1. **`AGENTS.md`** at the repo root, following the <https://agents.md/> convention — short (one to two screenfuls), vendor-neutral, covering: Build & run, Testing, Code style, Security, ADR expectations, Commit / PR hygiene, What not to do, Human review contract.
2. **`.cursor/rules/*.mdc`** (or your IDE assistant's equivalent dotfile set) with at least three rule files — one house-style, one testing, one security.
3. **Optional: nested `AGENTS.md`** in one subdirectory that warrants stricter norms (a security-sensitive package, a data-handling package, a public-API surface).

The deliverables must be coherent with Exercise 01's PR template — any norm the reviewer is asked to check should either appear in your authorship-time files here, or be explicitly documented as "reviewer-only" with a reason.

## Steps

1. **Pick the repo.** Use your team's primary production repo. If you cannot use the real repo, mirror its structure in a scratch repo with representative subdirectories.
2. **Inventory existing conventions.** Spend 15 minutes listing the implicit norms your team already follows — naming, imports, test shape, commit messages, review tone, scope discipline. These are the raw material. If you cannot articulate them, the agent cannot either.
3. **Draft `AGENTS.md`.** Follow the convention structure. Keep each section to 3–8 lines. Put *exact commands* in Build & run and Testing (`pnpm test`, `cargo test --all`, `uv run pytest`, etc.) — the agent should never guess. Resist the urge to include everything; a two-screenful AGENTS.md will be read, a six-screenful one will be ignored.
4. **Write the "What not to do" section with specifics.** Generic "do not break things" is useless. Concrete bans with concrete reasons:
   - "Do not rewrite files outside the ticket's stated scope."
   - "Do not upgrade dependencies in `pyproject.toml` / `package.json` without opening an ADR."
   - "Do not propose code that touches `src/auth/` without naming a second human reviewer."
   - "Do not call MCP tools not on the approved list in `.mcp-authorised.yml`."
5. **Write the "Human review contract" section** — the one-paragraph version of Chapter 5. Example: *"Every artifact you produce will be reviewed by a human who is accountable for what ships. If you are unsure, stop and ask rather than proceed. Preserve your trace (prompt chain, model, tool calls) when uncertain."*
6. **Draft three Cursor rules (or IDE-assistant equivalents).** `00-house-style.mdc`, `10-testing.mdc`, `20-security.mdc`. Each with YAML frontmatter (`description`, `globs`, `alwaysApply`), 10–25 lines of rules in the body. Mirror the AGENTS.md section content at the rule granularity — the rules apply at the glob scope that matters most.
7. **Author one nested `AGENTS.md`.** Pick a subdirectory with stricter norms (`src/billing/`, `src/auth/`, `migrations/`, `docs/public/`, etc.). The nested file layers on top of the root AGENTS.md per the convention — do not repeat; add.
8. **Dry-run.** Open the repo in your IDE assistant. Ask the assistant to make a small change in scope of one rule and a small change in scope of a nested-AGENTS.md subdirectory. Read the assistant's output. Does it reflect the norms? If not, which rule needs to be more specific? Iterate.
9. **Walk the pair to a senior IC.** Specifically ask: *does the Cursor rule file tell you anything surprising about what the agent will now produce? Does the nested AGENTS.md look right for that subdirectory?* Note surprises; iterate.
10. **Freeze v0.1.** Add a change log to AGENTS.md (date, author, reason for the change). Add the same change-log row to each Cursor rule file in a comment at the top. Add an entry to your team's human/machine contract linking to this artifact pair as part of the standards-as-code stack.

## Starter guidance

- The convention page (<https://agents.md/>) is the source of truth for shape. When in doubt, follow the convention — it maximises the number of agent runtimes that will honour your file.
- `alwaysApply: true` on a Cursor rule means the rule is injected whenever the glob matches a file in context. Use it sparingly for the house-style and security rules; scope narrower rules to the specific globs that need them.
- Do not put secret-detection patterns in the Cursor rules file — those belong in pre-commit (Exercise 03) and in the security linter. Rules are *behavioural guidance*, not *enforcement*.
- Favour rules that are falsifiable at review time. "Write clean code" is not a rule. "Prefer composition over inheritance; if you use inheritance, justify in a code comment that cites the specific reuse pattern" is.
- Nested AGENTS.md should *add* strictness, never relax it. If a subdirectory wants to relax a root norm, that is an ADR-level change, not a convention file change.
- Cursor-specific syntax (`@file:`, `@docs:`, etc.) is useful inside rules to bind authoritative context — e.g., the rule can reference the exact PR template file so the agent knows its format. Read the live Cursor docs for the current syntax.
- If your team uses GitHub Copilot primarily, mirror the AGENTS.md security + review-contract sections into `.github/copilot-instructions.md` — the two conventions coexist, and Copilot does not read AGENTS.md.

## Acceptance criteria

The pair is complete when:

- `AGENTS.md` exists at the repo root with all eight sections from Chapter 3 (Build & run, Testing, Code style, Security, ADR expectations, Commit / PR hygiene, What not to do, Human review contract) and a change log. One to two screenfuls total.
- At least three Cursor rule files (or equivalent) exist at `.cursor/rules/` with frontmatter and 10–25 lines of body each, scoped to appropriate globs.
- At least one nested `AGENTS.md` exists in a subdirectory with stricter norms, adding (never relaxing).
- A dry-run has been performed: the IDE assistant was given two tasks and the outputs documented as "reflected the rules" or "did not reflect — rule adjusted."
- A senior IC has walked the pair and given feedback; feedback either reflected or logged.
- The pair is coherent with Exercise 01's PR template — no norm in the template is absent from the authorship-time files unless marked reviewer-only.
- The team's human/machine contract (from mod-101) references this artifact pair in the standards-as-code section.
- Every file carries a change log (date, author, reason).

## Stretch goals

- **Multi-assistant mirror.** Author `.github/copilot-instructions.md` and `CLAUDE.md` alongside AGENTS.md, carrying the same norms. Note divergences where an assistant has a specific feature the others lack.
- **MCP authorisation policy.** Draft `.mcp-authorised.yml` (or your framework's equivalent) listing the exact set of tools the team's agents are allowed to call. Reference the file from AGENTS.md and the Cursor security rule.
- **Rule-adoption telemetry.** Set up (or describe) a lightweight telemetry hook — on each AI-authored PR, does the agent appear to have followed the rule? A simple version is to add a Chapter 2 PR-template line: "Confirm agent followed `AGENTS.md` — yes / no / with-override / N/A." Aggregate quarterly.
- **AGENTS.md diff for a hire.** Write a short "what this file is and why we have it" prose onboarding note for a new IC who has never seen the convention. Pairs with [`mod-105`](../../mod-105-team-ai-enablement-programs/)'s Day 0 / 30 / 60 / 90 enablement plan.
- **Regression gate for the file itself.** Write a pre-commit or CI check that prevents silent deletion of AGENTS.md sections (e.g., "the 'Human review contract' section must be present"). Pair with Exercise 03's lint-policy work.
- **Convention upstreaming.** If your team discovers a convention gap, file a feedback issue upstream to <https://agents.md/> or the relevant vendor. The convention improves when teams push back on it.
