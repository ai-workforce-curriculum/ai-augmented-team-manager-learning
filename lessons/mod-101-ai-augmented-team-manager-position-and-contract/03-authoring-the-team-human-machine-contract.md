# Chapter 3 — Authoring the Team's Human/Machine Contract

> *"AI generates, humans own." Six words. Your team deserves a longer document.*

## Motivation

Across the 25-posting sample that seeded this track, one phrase showed up again and again in different wordings: **"AI generates, engineers own."** Variations include "humans are accountable for what ships," "the model drafts, the reviewer signs off," "we never ship an AI artifact that no human has read." The phrase is useful shorthand. It is not a usable contract.

A **contract**, in the sense this chapter uses it, is a written artifact your team can point at when things go right and when things go wrong. It names what humans own, what the AI owns, what a human reviewer must do before an AI-drafted artifact ships, where the manager is on the hook, where the ICs are, and where the vendor is. Every team of 5–30 ICs doing AI-augmented work needs one. Most do not have one yet — they operate on vibes and the vibes break under incident.

This is the chapter where you learn what the artifact looks like. Exercise 03 is where you draft yours. Mod-103 is where you encode parts of it into standards-as-code (Cursor rules, AGENTS.md, ADRs, lint policies). Mod-109 is where you live by it when an AI-produced incident lands.

## Core concepts: the four parties and the five commitments

### The four parties

Any AI-augmented artifact — a PR, a design doc, a report, a dashboard query, an email draft — passes through up to four parties on the way to shipping:

1. **The AI (model + agent + tool connections).** The drafter.
2. **The IC** who prompted the model, reviewed its output, and submitted it.
3. **The reviewer** (often a peer IC; sometimes the manager) who approves it.
4. **The vendor** (the model provider; the tool provider; the inference host).

A contract that does not name all four will leave a gap when an incident happens. The gap is usually where the reviewer sits — because reviewers get busy and because "the model wrote this" is tempting as a dodge. Chapter 3's job is to prevent that dodge.

### The five commitments the contract must cover

A usable contract answers five questions. Each is addressable in one short section; together they rarely need more than two pages.

**C1. What work may the AI draft?**
Name the artifact classes (code, tests, docs, review comments, status updates, dashboards, analyses) and the classes where AI drafting is expected, allowed, allowed-with-review-only, or **not allowed** at all. Examples of classes most teams restrict: employee feedback, compensation decisions, promotion packets, incident post-mortems, security incident writeups. The default *is not* "anything that fits in a prompt box" — it is "work we have decided AI may draft on this team."

**C2. What must the human do before the artifact ships?**
The verification requirement. Minimum spec per artifact class:
- *Read every line the model wrote.* No "LGTM" on a diff you did not read.
- *Run / execute / replicate* where applicable. Tests, queries, numbers.
- *Check the claims against sources* where applicable. Cited facts, imported data, quoted docs.
- *Judge the fit to context* that the model cannot see (team norms, downstream consumers, political context, in-flight work).
This is also where you set the **review budget** — how much time a reviewer gets, so the contract is realistic. A two-paragraph commit comment that encodes a three-hour judgment call is not acceptable here.

**C3. Who is accountable when something ships broken?**
The accountability stack. In order:
1. **The IC** who submitted the artifact is accountable for shipping it. They cannot delegate accountability to the model.
2. **The reviewer** who approved it is accountable for the approval. They cannot delegate accountability to the IC or the model.
3. **The manager** (you) is accountable for the system — the standard, the enablement, the reviewer bandwidth, the choice to use AI on this class of work in the first place. You cannot delegate accountability for the system to a vendor.
4. **The vendor** is accountable for what their SLA says — availability, documented behaviour, published guardrails. They are not accountable for your choice to use their tool on work it was not fit for.
The stack is deliberate: it blocks the "the model did it" dodge at each layer.

**C4. What do we do when the AI is wrong?**
The incident-triage shape in one paragraph, pointing forward to `mod-109`. At minimum:
- Report it (where, how, within what window).
- Pull the artifact back where feasible; otherwise correct and communicate.
- Preserve the trace — prompt, model version, tool connections, retrieved context — so the fault chain can be reconstructed.
- Feed the finding back into C1 (did this class of work belong to AI?) and C2 (did the verification bar catch it?).
Blameless-post-mortem language from Google SRE and Allspaw is the target; `mod-109` adapts it for AI-produced incidents.

**C5. What may the AI see, and what may it keep?**
The data-handling boundary. Short list per team:
- What data may be pasted into the tool at all (public, internal-allowed, confidential-allowed, confidential-prohibited, regulated).
- Which tool with which enterprise posture is approved (e.g., the SSO-authenticated enterprise tier vs. a personal account).
- Retention and training-opt-out posture of the vendor (link to the DPA; `mod-110` and `mod-111` go deeper).
- Secrets, keys, tokens, customer PII rules.
This section is short and specific. It is also the one most likely to be a cut-and-paste from org policy; your job is to translate it into the team's day-to-day vocabulary.

### What a workable contract looks like on the page

A one-to-two-page artifact, pinned in the team's working wiki, with these headings:

1. Scope of this contract (team name, what we do, time horizon).
2. What AI may draft (C1 table: artifact class × allowed / allowed-with-review / not-allowed).
3. What the human must do before it ships (C2 verification requirements per class).
4. Accountability stack (C3 — IC, reviewer, manager, vendor).
5. What we do when the AI is wrong (C4, with link to `mod-109` runbook when it exists).
6. What the AI may see (C5 data-handling boundary).
7. Change log (every revision dated and attributed; this contract updates every quarter minimum and after every incident).

The change log is not optional. A contract without a change log drifts invisibly; a contract with one is a quarter-by-quarter record of how the team's AI posture matured.

### The framing phrase, decoded

"AI generates, humans own" compresses three decisions:

- **Who drafts** — the model may. (C1.)
- **Who checks** — a human must, to a stated bar. (C2.)
- **Who is on the hook** — a human, always. (C3.)

When you hear the phrase from a candidate in a hiring loop (mod-108) or a VP in a review (mod-112), it is useful to know which decision they are reaching for. Most of the time it is C3 — accountability — not C1 or C2. Clarifying which part of the contract they mean is a fast test of whether they have run this system before.

## Example: a terse contract for a 10-person application engineering team

The sample below is illustrative; it is a sketch, not a template to adopt wholesale.

> **Scope.** Payments platform team; 10 engineers; runway for the next quarter; owned by `@manager`.
>
> **AI may draft:** production code (Python / TypeScript), tests, PR descriptions, ADR first drafts, on-call runbook edits, status updates.
> **AI may draft with review-only:** customer-facing error messages; incident post-mortems (first draft only; human rewrites before publishing).
> **AI may not draft:** employee feedback, compensation input, promotion packets, security incident writeups, legal-facing communications.
>
> **Verification bar.** For code and tests: every line the model wrote is read by the submitter and by one reviewer; tests pass locally and in CI; the reviewer confirms the diff is scoped. For ADRs and runbooks: the submitter has verified claims against the source system; a second engineer confirms. For status updates: the manager edits for honesty and context before sending.
>
> **Accountability stack.** IC submits → reviewer approves → manager owns the standard → vendor to SLA.
>
> **When AI is wrong.** Report in `#eng-ai-incidents`; pull the artifact if possible; preserve the prompt and model version; add to the mod-109 incident tracker. We write a blameless note within 72 hours.
>
> **What AI may see.** Enterprise SSO Cursor + Claude Code only; no personal accounts. No customer PII, no secrets, no production credentials in prompts. The vendor DPA is linked in the runbook.
>
> **Change log.** v0.1 2026-10-14 (@manager, kickoff); v0.2 2026-11-03 (@manager, post Q3 incident #41, tightened C4 trace-preservation).

Two pages. Legible to the team. Legible to a VP. Legible to the governance analyst when they ask for team evidence.

## Summary

- The contract names four parties (AI, IC, reviewer, vendor) and answers five questions (what may AI draft; what must humans do before shipping; who is on the hook; what we do when AI is wrong; what AI may see).
- Each of C1–C5 maps to a downstream mod: C1/C2 to `mod-103` (encoded as standards-as-code), C3 to `mod-108`/`mod-109` (performance and incident), C4 to `mod-109` (incident response), C5 to `mod-110`/`mod-111` (governance and vendor).
- A workable artifact is one-to-two pages with a change log, pinned in the team wiki. The change log is the audit trail of your team's AI maturity.
- "AI generates, humans own" is the slogan. The contract is the system. The slogan without the system is a liability.
