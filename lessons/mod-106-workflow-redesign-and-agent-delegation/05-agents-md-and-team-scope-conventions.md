# Chapter 5 — AGENTS.md and the Team-Scope Delegation Contract

> *The agent reads what the repo tells it. On a disciplined team, that file is called `AGENTS.md`, it is version-controlled, and it is the written form of the delegation ladder, the HITL checkpoints, and the tool-authorisation policy as the agent itself sees them.*

## Motivation

Before a shared convention existed, every AI coding tool invented its own project-level context file: `.cursorrules`, `CLAUDE.md`, `.github/copilot-instructions.md`, `.aider.conf.yml`, and so on. Teams running more than one tool found themselves maintaining the same information in three places and watching the copies drift. The [AGENTS.md](https://agents.md/) convention, adopted in 2025 by a growing list of agent tools, standardises a single top-of-repo file that any conforming agent can read for project-level instructions.

For a team manager, AGENTS.md is more than a tooling convenience — it is the **artifact the agent itself sees**. The delegation ladder (Chapter 3), the HITL checkpoints (Chapter 4), and the tool-authorisation policy (Chapter 6) are all authored by humans and read by humans. AGENTS.md is the piece the agent actually picks up and acts on. A mismatch between what the ladder says and what AGENTS.md says is a defect that the agent will act on in favour of the AGENTS.md file, because the agent is reading AGENTS.md, not the ladder.

This chapter is what belongs in that file, how the team-scope *delegation contract* composes with it, and how the pair stays consistent with the artifacts from Chapters 2–4. Exercise 02 produces v0.1 of both files.

## Core concepts

### What AGENTS.md is for (and what it isn't)

The AGENTS.md convention names three core purposes: *(1)* give agents project context (how to build, test, lint, commit); *(2)* set repo-local conventions the agent should respect (naming, directory layout, forbidden edits); *(3)* name the human review and ownership points the agent needs to know about. Different tools consume AGENTS.md slightly differently — some treat it as a system-prompt append, some as an inline instruction set, some as context the model retrieves on demand — but the file itself is a Markdown document the human owners write and the agent reads.

A mod-106-literate AGENTS.md sits at the intersection of repo-level and team-level concerns.

**In scope for AGENTS.md:**

- Build, test, lint, commit, and run commands the agent needs to invoke.
- Repo layout conventions (which directories are the agent's primary workspace; which are *read-only* to the agent; which are off-limits).
- Review-standard pointers (where the mod-103 checklist lives; which classes of change trigger which review).
- Delegation summary (per the Chapter 3 ladder) — enough for the agent to recognise its scope ceiling and know when to stop and surface.
- HITL trigger points — which actions require pre-invocation approval (Kind 1) and which do not.
- Tool-authorisation summary — a short, legible version of the policy from Chapter 6, pointing at the authoritative policy file.
- Escalation condition language — what the agent should say when it hits a ceiling.
- Pointers to related artifacts (routing matrix, delegation ladder, tool-authorisation policy, mod-101 contract).

**Out of scope for AGENTS.md:**

- Tool-call policy at the enforceable layer. AGENTS.md is a *document*, not a *runtime enforcer*. If the policy is *"the agent must not run `git push`,"* AGENTS.md says so *and* Chapter 6's tool-authorisation policy enforces it at the tool-call layer. The document alone is not sufficient — Chapter 6 explains why.
- Secrets, tokens, credentials. Standard rule: anything that would be in `.gitignore` for a human engineer is also absent from AGENTS.md.
- Long-form training material. AGENTS.md is read on every agent run (or near every); verbose prose costs tokens and attention. Short, imperative, pointer-rich is the shape.
- Content that should be in mod-101's contract, mod-103's standard, or mod-109's incident runbook. AGENTS.md *points at* those files; it does not inline them.

A good AGENTS.md on a 10-engineer team is 100–300 lines. Longer typically means the file has drifted into reproducing content that should be in the pointed-at documents; shorter typically means it is skipping load-bearing context.

### The shape of a mod-106-literate AGENTS.md

Below is a skeleton. The content is the team's, and most of it points at other versioned artifacts.

```markdown
# AGENTS.md — [team name] — v0.X — [date]

## What this file is
This repo is primarily maintained by the [team name] team. This file tells any AI agent
(Cursor, Claude Code, Codex, Aider, internal agents) what is in scope, what is out of
scope, and where the human review and approval points are.

## How to build / test / lint
- `make test` runs the full test suite (~90 seconds).
- `make lint` runs the linter and the formatter.
- `make verify` runs lint + test + mod-103 review-standard checks.
- Agents must run `make verify` before proposing to commit any change.

## Repo layout (agent-relevant parts)
- `src/`             — agent's primary workspace.
- `docs/`            — human-authored. Agent may suggest edits; see Review scope below.
- `docs/mod-106/`    — this module's team-scope governance artifacts (routing matrix, ladder, HITL, tool-auth policy).
- `migrations/`      — **off-limits** to agents at scope ceiling [Level 3 and below]; agent must stop and surface.
- `.github/`         — **off-limits** to agents at any level; humans only.

## Delegation summary (full ladder in docs/mod-106/delegation-ladder.md)
- Code review on single-file bug-fix PRs: Level 3. Author the review comment; may not request changes or merge.
- Code review on multi-file refactors: Level 2. Draft comment and surface to a human reviewer.
- Test-writing for a new unit: Level 3.
- Migrations and schema changes: Level 2 drafting only; human authors the migration file.

## Where humans sit in the loop
- Pre-invocation approval required for: any `git push`, any `gh pr merge`, any deploy command, any outbound HTTP to external services beyond the authorised MCP server list.
- Mid-run gate on: multi-step plans with >3 files touched — surface the plan before executing.
- Post-generation review: all PRs opened by the agent go to the human author on the ticket.
- Periodic audit: Monday 10:00 handoff review; monthly sample-audit of agent-authored PRs (filed in docs/mod-106-audit/).

## Tool-authorisation summary (full policy in docs/mod-106/tool-auth-policy.md)
- Read tools (file read, test run, git status, `gh pr view`): always available.
- Write tools (file edit, test fixture creation): available in `src/` and `test/`; not in `migrations/` or `.github/`.
- External tools (HTTP, outbound email, Slack post, deploy): only via the authorised MCP server list in the policy file; each call is Kind 1 (pre-invocation approval).

## Escalation condition language
When the agent needs to surface and stop, use this template:
> "I am stopping because [condition]. The authorised level for this task is [level]; the proposed action exceeds it. Please review and either approve the specific action or re-scope the request."

## Related artifacts
- Team human/machine contract: docs/mod-101-contract.md
- Review standard: docs/mod-103-review-standard.md
- Routing matrix: docs/mod-106/routing-matrix.md
- Delegation ladder: docs/mod-106/delegation-ladder.md
- HITL checkpoint set: docs/mod-106/hitl-checkpoints.md
- Tool-authorisation policy: docs/mod-106/tool-auth-policy.md
- Incident runbook: docs/mod-109-incident-runbook.md
```

The shape above is a *skeleton*. Your team's content replaces every bracketed placeholder and most of the specific items. The numbered sections and the pointer-forward pattern are what should be stable.

### The team-scope delegation contract

The *delegation contract* is a short, human-signed document that lives beside AGENTS.md and does three things AGENTS.md does not:

- **States the humans on the hook.** Named roles — team manager, senior IC domain-owner, PR-author-of-record — with the explicit sentence: *"I own the agent's actions in my scope, and I am the signatory for the specific tool-authorisations below."* Mirrors mod-101 contract clauses C3 and C4.
- **States the scope of unattended authority.** A plain-English list of what the team's agents may do without a human in the loop at the per-action level. *"Agents on this team may read any file in this repo, run the build and test suites, draft code review comments, propose PRs. Agents may not merge PRs, push to remote branches, deploy, or contact external services except via the MCP server list in the tool-authorisation policy."*
- **States the escalation path and the incident boundary.** What happens when an agent exceeds its scope ceiling; what classifies as an incident; who gets paged. Mirrors mod-109.

Where AGENTS.md is the file the agent reads, the delegation contract is the file the team reads. They cover overlapping content; they are not duplicates. A weekly or monthly manager-authored change to the contract triggers a corresponding change to AGENTS.md; a change to AGENTS.md that is not reflected in the contract is a defect in the change-control process.

### How AGENTS.md composes with the four other artifacts

Four composition rules keep the five-artifact set coherent.

- **Routing matrix → AGENTS.md:** the matrix names task types; AGENTS.md summarises the routing in the *repo-local* language the agent sees. A row in the matrix that routes to AI unattended must be reflected in AGENTS.md as *"the agent may do X without asking."* A row that routes to senior human must be reflected as *"the agent must stop and surface tasks of class Y."*
- **Delegation ladder → AGENTS.md:** the ladder is the authoritative per-row level; AGENTS.md's *"Delegation summary"* section is the human-and-agent-readable rollup. Any mismatch between the ladder and the AGENTS.md summary is a defect; the ladder wins and AGENTS.md is regenerated.
- **HITL checkpoints → AGENTS.md:** Kind 1 checkpoints (pre-invocation) are what the agent most needs to respect. AGENTS.md's *"Where humans sit in the loop"* section lists every Kind 1 and Kind 2 trigger. Kind 3 and Kind 4 may be mentioned by pointer only (they fire on the human side, not the agent's).
- **Tool-authorisation policy → AGENTS.md:** the policy's enforced bands (Chapter 6) are reflected in AGENTS.md as a *summary*, with the pointer to the authoritative file. AGENTS.md is not the enforceable policy; it is the agent's view of the policy's categories.

### Multiple agent tools, one AGENTS.md

A team that uses Cursor, Claude Code, and an internal agent should have *one* AGENTS.md at the repo root. Three considerations.

- **Conforming tools read AGENTS.md by convention.** Cursor supports project-level rules in [its rules file](https://docs.cursor.com/context/rules-for-ai); Claude Code reads AGENTS.md (and CLAUDE.md); several community agents follow the same convention. A team-scope AGENTS.md is the shared surface.
- **Tool-specific files, when required, point at AGENTS.md.** If a tool insists on a `.cursorrules` or `CLAUDE.md`, the content of those files should be a short pointer: *"See AGENTS.md for the authoritative project instructions. This file exists only because this tool requires it."*
- **Where tools require tool-specific instructions** (model override, tool-specific commands), they live in the tool-specific file. They are the exception, not the rule.

The default is **one AGENTS.md, zero duplication** — and every drift from the default is a documented exception.

### AGENTS.md versioning and review

AGENTS.md is version-controlled like any other code. Four practical conventions.

- **Semantic versioning in the header.** `v0.X.Y` with a date. A promotion in the delegation ladder is a `v0.X.0 → v0.(X+1).0` bump; a correction is a `v0.X.Y → v0.X.(Y+1)`.
- **PR review by the full team on major bumps.** AGENTS.md is read by every engineer on every tool-assisted run; a bad bump has team-wide effect. Major bumps are opened as a PR with the manager and at least one senior IC as required reviewers.
- **Dated change-log.** A short change-log at the bottom of the file naming what changed and why in each version. Agents sometimes use the change-log to calibrate how recently a constraint was added; humans use it to orient when they come back to the file.
- **Scheduled review.** AGENTS.md is reviewed at the same quarterly ritual that reviews the delegation ladder (Chapter 3). The two cannot drift if they are reviewed together.

## Example: an AGENTS.md diff from a Chapter 3 demotion

Suppose the platform team's quarterly ladder review demotes *"code review on multi-file refactors"* from Level 3 to Level 2 after a near-miss on a refactor the agent approved. The corresponding AGENTS.md diff:

```diff
 ## Delegation summary
-- Code review on multi-file refactors: Level 3. Draft comment, may request changes.
+- Code review on multi-file refactors: Level 2. Draft comment and surface to a human reviewer; may not request changes directly.
```

And the change-log addition:

```
## Change log
- v0.4.0 (2026-04-05): demoted multi-file-refactor review to Level 2 after 2026-03-28 near-miss on PR #2451; see incident note in docs/mod-109-incidents/2026-03-28.md.
```

Two-line diff; one change-log line; the escalation condition in the AGENTS.md (unchanged) still covers the new scope. This is what *living with* an AGENTS.md looks like in practice — the file changes often, each change is a specific decision with a cited reason, and the diff is readable in 30 seconds.

## Summary

- [AGENTS.md](https://agents.md/) is the 2025-era convention for a single top-of-repo file any conforming agent reads for project-level context.
- A mod-106-literate AGENTS.md covers: **build/test/lint commands, repo layout + off-limits directories, delegation summary, HITL triggers, tool-authorisation summary, escalation-condition language, pointers to the authoritative artifacts**.
- AGENTS.md is **not** the enforceable tool-authorisation policy (that is Chapter 6's artifact); it is the *agent's view* of the policy, in short imperative form.
- The **team-scope delegation contract** sits beside AGENTS.md: humans-on-the-hook, unattended-authority scope, escalation path, incident boundary. It mirrors mod-101's contract clauses C3, C4.
- Four composition rules keep the five-artifact set coherent: the routing matrix, delegation ladder, HITL checkpoint set, and tool-authorisation policy each project a summary into AGENTS.md; the authoritative file wins on any conflict.
- A team using multiple agent tools (Cursor, Claude Code, Codex) has **one AGENTS.md** at the repo root and uses tool-specific files only as thin pointers.
- AGENTS.md is **version-controlled, semantically versioned, PR-reviewed on major bumps, change-logged, and reviewed quarterly** with the delegation ladder.
- Exercise 02 produces v0.1 of both AGENTS.md and the delegation contract for your team's main repository.
