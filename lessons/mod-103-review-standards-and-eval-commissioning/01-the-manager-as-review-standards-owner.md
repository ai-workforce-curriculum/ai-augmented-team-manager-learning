# Chapter 1 — The Manager as the Owner of Review Standards for AI-Generated Work

> *When the author is a model, "LGTM" is a decision about the system, not about the diff. The manager who refuses to write that decision down has already made it — badly.*

## Motivation

Across the 25-posting sample that seeded this track (see [`JOB_REQUIREMENTS.md`](../../JOB_REQUIREMENTS.md)), two neighbouring themes are the second- and third-most-cited requirements for the role:

- **R2 — set review standards and the accountability model for AI-generated work.** Posting frequency **0.60** (6 in-window postings; the remainder of the 25-posting sample is live-but-undated ATS evidence treated as corroborating language). Verbatim phrasings include *"set the team's bar for AI-generated code,"* *"define what 'reviewed' means when a model drafted the diff,"* *"author the AI-review checklist and roll it out,"* and *"own the standards-as-code stack (Cursor rules, AGENTS.md, lint, pre-commit) for agent authors."*
- **R3 — commission evaluation frameworks for AI output at the SDLC / workflow level.** Posting frequency **0.44**. Verbatim: *"commission golden-task and regression evals,"* *"decide what to evaluate and act on the findings,"* *"stand up LLM-as-judge for review signal,"* *"own the feedback loop from eval into team practice."*

R2 and R3 share roughly 40% of their underlying language, which is why this module folds them together. The through-line is a single posture: **the team-manager is the named owner of how AI-authored work is judged on this team.** You are not a reviewer-of-reviewers. You are not an IC eval engineer. You own the **system of review** — the checklist, the standards-as-code stack, the eval commissioning, and the accountability routing — that every reviewer on your team operates inside.

This is Chapter 1 of `mod-103`. The remaining chapters sharpen individual slices:

- Chapter 2 — the AI-work PR / document review checklist and verification bar.
- Chapter 3 — standards-as-code (Cursor rules, AGENTS.md, ADRs, lint, pre-commit) so the same norms govern human and agent authors.
- Chapter 4 — commissioning eval frameworks at team scope.
- Chapter 5 — the accountability contract, and how blame routes when an agent is wrong.
- Chapter 6 — mapping team review norms to the OWASP Top 10 for LLM Applications.
- Chapter 7 — the ownership boundary with `ai-risk-engineer` (L25, AI Governance family).

This chapter is the frame that holds the other six.

## Core concepts

### Why R2 lands on the manager and not on a senior IC

A frequent misreading of the postings: "this is really tech-lead work; the manager just signs it off." The posting language says otherwise, in three ways.

1. **"Own the standard"** — not "contribute to." The team-manager is named as the directly-responsible party.
2. **"Roll it out"** — not "write it." Authoring is the easy half; the hard half is getting a 5–30 person team to use it uniformly, under deadline, under reviewer fatigue, across a 12-month model-and-tool churn cycle. That is manager work.
3. **"Accountability"** — not "quality." R2 bundles the review standard with the accountability model because the market has learned the two cannot be separated. An IC can write a great checklist; only a manager can route blame when the checklist is skipped.

If you treat R2 as "write a checklist and give it to the tech lead," you will fail the hiring loop, and more importantly you will fail the team: the checklist will drift, the reviewer-of-record will become whoever was less busy, and the first AI-produced incident will land on the IC who happened to click "approve."

### "LGTM" is a decision about the system, not about the diff

When a human wrote the diff, "LGTM" on a code review is a near-trivial speech act. The reviewer has read the change, the author is on the hook for intent, and the chain of custody is socially clear.

When a model wrote the diff and a human approved it, "LGTM" compresses five distinct decisions:

1. *The submitter read every line the model wrote.*
2. *The submitter ran or replicated what is runnable.*
3. *The submitter verified the claims the diff makes against sources the model cannot see (team norms, downstream consumers, in-flight work).*
4. *The reviewer independently did some non-trivial subset of 1–3.*
5. *If the diff ships broken, the submitter and reviewer accept that they — not the model — ship the regression.*

A manager who has not decided *which of the five* is required for which artifact class has implicitly made all of them optional. The purpose of the review standard in this module is to make that implicit decision explicit and durable.

The chapter-2 checklist is the operational form of 1–3. Chapter 5's accountability contract is the operational form of 4–5. The standards-as-code stack in chapter 3 is how all of that stays alive after the kick-off memo is six months old.

### Three failure modes this module exists to prevent

Working teams that skip this work tend to fail in three recognisable ways. Each has a chapter dedicated to preventing it.

**Failure mode A — "The model wrote it, so I skimmed."** The reviewer treats model-authored diffs as a lower-scrutiny class because the diff "looks clean" or "looks plausible" or "was easy to generate." Clean-looking diffs are the specific risk; models that produce syntactically perfect code with a logically wrong branch are standard. Prevention: a review checklist (Chapter 2) that does not move with how the diff *looks*, plus a review budget that acknowledges reviewing model output is *slower*, not faster, than reviewing a comparable human diff on the same topic.

**Failure mode B — "We have a review standard; nobody follows it."** The manager wrote a good doc; the team never operationalised it. The checklist lives in a wiki page that nobody reads. The reviewer-of-record varies by day. Prevention: encode the standard into the tools (Chapter 3) so the standards-as-code stack enforces at the point of authoring — Cursor rules shape what the agent produces, AGENTS.md shapes what the agent allowed to do, pre-commit / CI shapes what can even land. A rule the robots obey is a rule the humans then also obey.

**Failure mode C — "We have no idea whether this is working."** The team shipped a review standard and a standards-as-code stack and… cannot say whether the AI-produced defect rate is better, worse, or the same as the human baseline, because there are no evals at the team scope to answer the question. Prevention: commission a modest eval harness with named owners (Chapter 4) that produces a report your team actually reads.

### What this module is *not*

As with `mod-102` and `mod-101`, naming the adjacent-but-distinct work is as load-bearing as naming the work itself.

- **Not an eval-harness-authoring course.** You are commissioning the harness, not building it. The IC mechanics of harness implementation live in [`ai-assisted-software-engineer`](https://github.com/ai-engineering-curriculum/ai-assisted-software-engineer-learning) (level 25) and the domain depth lives at [`ai-eval-engineer`](https://github.com/ai-engineering-curriculum/ai-eval-engineer-learning) (level 30, AI Engineering family). Chapter 4 is deliberate about where the line sits.
- **Not an engineered-risk / guardrail-depth course.** Red-teaming, prompt-injection exploit construction, model guardrail tuning, and jailbreak-resistance evaluation are owned by [`ai-risk-engineer`](https://github.com/ai-governance-curriculum/ai-risk-engineer-learning) (level 25, AI Governance family). You *commission* that work and *act on the evidence*; you do not rebuild the rig. Chapter 7 draws the boundary.
- **Not a security course.** OWASP Top 10 for LLM Applications maps into your review checklist (Chapter 6) at the altitude of *what a reviewer must notice*, not at the altitude of *how to exploit each risk*. Application-security depth is downstream of your partner-function sign-off, not inside this module.
- **Not an incident-response runbook.** When an AI-produced artifact breaks in production, you follow the playbook in [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/). Chapter 5 of this module hands off to it.
- **Not an org-wide governance crosswalk.** NIST AI RMF, ISO/IEC 42001, EU AI Act articles map through to team practice via [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/). The team-scope review standard is a *source* for that crosswalk, not the crosswalk itself.

### The seven artifacts a mod-103-literate manager owns

By the end of this module, you are personally responsible for authoring (or heavily editing from a model draft) a bounded artifact set. Every exercise in this module corresponds to one of them:

1. **The AI PR / document review checklist.** Per artifact class. Encoded in the review template and in the CI gate where enforceable. (Exercise 01.)
2. **The team's AGENTS.md and Cursor-rules convention.** The human-and-agent-readable form of the standard. (Exercise 02.)
3. **The ADR template and lint-policy package.** The compiler-enforced subset of the standard. (Exercise 03.)
4. **The eval commissioning rubric.** The one-pager that goes to `ai-risk-engineer` or `ai-eval-engineer` when you need a harness built. (Exercise 04.)
5. **The LLM-as-judge / Promptfoo / LangSmith reading posture.** Enough fluency to read reports and challenge them — carrying forward from Chapter 5 of [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/). (Exercise 05.)
6. **The OWASP LLM Top 10 mapping into review.** A row-per-risk crosswalk from OWASP's 2025 list into your checklist. (Exercise 06.)
7. **The accountability contract — v0.1 of the team-signed document.** The agreement the team actually points at when an incident lands. (Exercise 07.)

This is the artifact set a hiring loop (per [`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/)) and an exec pre-read (per [`mod-112`](../mod-112-cross-functional-leadership-and-ritual-calendar/)) can both read in ten minutes. The point of the module is to produce the set; the chapters are the teaching that makes each one defensible.

### Grounding in the posting evidence and in the authoritative references

Two anchors keep the standard honest.

- **Posting evidence.** R2 (0.60) and R3 (0.44) in [`JOB_REQUIREMENTS.md`](../../JOB_REQUIREMENTS.md). Treat the recurring posting vocabulary — *"'AI generates, humans own,'"* *"standards-as-code,"* *"golden tasks,"* *"LLM-as-judge,"* *"accountability model"* — as the hiring-side signal of what artifacts the market wants to see you produce.
- **Authoritative references.** Primary and public. OWASP Top 10 for LLM Applications (Chapter 6). The G-Eval paper (Liu et al. 2023) and the Promptfoo / LangSmith / Inspect AI documentation (Chapter 4). Google SRE and Allspaw on blameless post-mortems (Chapter 5 and `mod-109`). Cursor Rules documentation, the AGENTS.md convention, and Michael Nygard's ADR note (Chapter 3). NIST AI RMF is referenced where the team-scope translation maps into the org-wide crosswalk owned by `mod-110`.

A defensible review standard cites both. The postings tell leadership *this is the artifact the market expects this role to produce*; the authoritative references tell leadership *this is the way we are producing it*.

## Example: a two-paragraph sketch of the review-standard frame

Treat this as calibration for shape, not a template to adopt.

> **Frame.** On this team, every artifact class carries a stated AI-authoring posture (allowed / allowed-with-review-only / not-allowed), a stated verification bar per class, and a named reviewer-of-record. `LGTM` on a model-drafted artifact asserts four things: *I read every line*, *I ran what is runnable*, *I checked claims against the source the model could not see*, *I accept the regression if this ships broken*. The checklist in `/.github/pull_request_template.md` carries the first three; the accountability contract in `/docs/human-machine-contract.md` carries the fourth.
>
> **Standards-as-code backing.** The Cursor rules in `.cursor/rules/` and the `AGENTS.md` at the repo root encode the same norms into what the agent is allowed to produce. The ADR template in `/docs/adr/0000-template.md` and the lint policy in `.eslintrc`/`ruff.toml` encode the compiler-enforced subset. Pre-commit hooks reject diffs that skip the review-template sections. Quarterly, we commission a small golden-task eval against the two or three agent flows that carry the most volume (currently: PR-description drafting and test-skeleton generation); the harness is owned by `@ai-risk-engineer-peer` and the output is read at our Q-review in `mod-112`. When an AI-produced artifact ships broken, the incident process in [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) runs.

Two paragraphs, legible to the team, to a VP, and to a governance partner.

## Summary

- R2 (0.60) and R3 (0.44) land on the manager as **owner of the review system** — the checklist, the standards-as-code stack, the eval commissioning, and the accountability routing. The posting language says *own and roll out*, not *contribute to*.
- "LGTM" on a model-authored artifact compresses five decisions. A manager who has not made those decisions explicit has implicitly made them all optional.
- Three failure modes to prevent: *"I skimmed because the model wrote it"* (Chapter 2 checklist), *"We have a standard, nobody follows it"* (Chapter 3 standards-as-code), *"We have no idea whether it's working"* (Chapter 4 eval commissioning).
- This module is *not* an eval-harness-authoring course, a risk-engineering course, a security course, an incident-response runbook, or an org-wide governance crosswalk. Chapter 7 keeps the ownership boundaries clean.
- By the end of the module you own a seven-artifact set: PR / doc checklist, AGENTS.md + Cursor-rules convention, ADR + lint package, eval commissioning rubric, eval-reading posture, OWASP LLM Top 10 mapping, accountability contract v0.1. One exercise per artifact.
