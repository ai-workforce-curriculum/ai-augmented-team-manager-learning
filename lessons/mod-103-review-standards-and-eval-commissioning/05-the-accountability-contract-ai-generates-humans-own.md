# Chapter 5 — The Accountability Contract: "AI Generates, Humans Own"

> *If "AI generates, humans own" is a slogan on a wall, the first serious incident is going to find out which human it meant.*

## Motivation

Chapter 3 of [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) introduced the team **human/machine contract** and its five sections (C1 what AI may draft, C2 verification bar, C3 accountability stack, C4 when AI is wrong, C5 what AI may see). This chapter is the operational deepening of **C3 + C4** at the altitude of *standards and eval work* — the slice of the contract that governs review and the route-of-blame when an AI-produced artifact ships broken.

R2 (0.60 of the posting sample; see [`JOB_REQUIREMENTS.md`](../../JOB_REQUIREMENTS.md)) does not just ask for a review checklist. It asks for the **accountability model** that attaches to the checklist. Verbatim phrasings: *"'AI generates, engineers own,'"* *"the model drafts, the reviewer signs off,"* *"humans are accountable for what ships,"* *"we never ship an AI artifact that no human has read."* Behind the slogan is a specific manager-owned decision: *when the artifact is wrong, which human is on the hook, how, and how does the team learn without sliding into blame?*

The deep incident-response work — the triage flow, the AI-specific post-mortem template, the write-up artifact — lives in [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/). This chapter is the version of the contract the team pins *before* any incident, so that when one happens the mod-109 runbook has rails to run on.

## Core concepts

### The four parties on the hook — recap and sharpen

From the mod-101 contract: the AI (model + agent + tools), the IC (who prompted and submitted), the reviewer (who approved), and the vendor (who sold the tool). A workable accountability contract makes four assertions at team scope:

1. **The IC** who submitted the artifact is accountable for shipping it. They cannot delegate accountability to the model. "The agent did it" is not a defence; the IC chose to use the agent, chose the prompt, and chose to click submit.
2. **The reviewer** who approved it is accountable for the approval. They cannot delegate to the IC or to the model. "Tests passed and the diff looked clean" is not a defence; the Chapter 2 checklist specifies what *reviewed* means.
3. **The manager** is accountable for the *system* — the standard (Chapter 2 of this module), the standards-as-code stack (Chapter 3), the eval that should have caught this (Chapter 4), the reviewer bandwidth, and the decision to allow AI authorship on this class of work in the first place. The manager cannot delegate the system to the vendor or to the agent.
4. **The vendor** is accountable for what their SLA says — model availability, documented behaviour, published guardrails. The vendor is *not* accountable for your choice to use their tool on work it was not fit for.

The ordering is deliberate. The accountability stack prevents the "it was the model" dodge at each layer: the IC cannot push accountability sideways to the model; the reviewer cannot push it back to the IC; the manager cannot push it up to the vendor. At the top of the stack, the human-vendor line is held by *the vendor's SLA*, not by informal assumption.

### Accountability is not blame

A contract that collapses accountability into blame will not be used. The team will not report the incident, will not preserve the trace, will not learn.

Google SRE's *Postmortem Culture: Learning from Failure* (<https://sre.google/sre-book/postmortem-culture/>) and John Allspaw's *Blameless Post-Mortems* (<https://www.etsy.com/codeascraft/blameless-postmortems/>) are the canonical references and they apply here directly. The relevant distinction:

- *Accountability* is naming, up front, *who is responsible for the decision* — so the team knows who signs off, who owns the follow-up, and who the facts have to flow to. You cannot have a learning culture without it.
- *Blame* is punishing the decision-maker for the outcome in a way that disincentivises surfacing the fault.

A blameless contract keeps both: it says *the IC and reviewer are accountable*, and it says *the response to a surfaced fault is to improve the system, not to punish the surfacers*. Allspaw's language is strong — *"we … consider post-mortems a record of what the engineers did, what they expected to happen, what actually happened, and what they learned"* — and it applies unchanged to AI-produced incidents.

### When an AI-produced artifact is wrong — the C4 play

A workable short-form of what happens next, pinned on the contract and expanded in `mod-109`:

1. **Pull it back or correct it.** If the artifact is still revertable (a pre-prod change, a dashboard not yet shared, a document not yet distributed), revert. If not, correct forward and communicate.
2. **Report within the window.** A named channel (`#eng-ai-incidents` or your team's equivalent); a named time budget (within 1 working hour for a production-affecting incident; same day for a non-production one). Where the report goes is as important as that it exists.
3. **Preserve the trace.** This is the AI-specific obligation. At minimum: the prompt (or prompt chain), the model and version, the tool / MCP connections the agent was allowed to call, the retrieved context (where the eval tooling supports it — LangSmith's trace view is designed for exactly this), and the exact artifact as submitted. Without the trace, the post-mortem cannot distinguish between "the agent misbehaved" and "the human-agent system failed."
4. **Run the post-mortem.** `mod-109` has the detailed template. The team-scope summary: what did we expect, what happened, what did we learn, which section of the review checklist or standards-as-code stack should have caught this, and what is the specific change we are making to catch the next one of these.
5. **Feed the learning back into the stack.**
   - Was this a C1 problem? (The model drafted a class of artifact it should not have.) → Update C1 of the human/machine contract.
   - Was this a C2 problem? (The verification bar did not catch it.) → Update the Chapter 2 checklist and the PR template.
   - Was this a standards-as-code gap? (Rule missing in `.cursor/rules/`; `AGENTS.md` silent on it; lint / CI did not flag it.) → Update the Chapter 3 stack.
   - Was this an eval gap? (We did not have a regression that would have caught it.) → Commission the eval, with the Chapter 4 brief.
6. **Publish the write-up blamelessly.** Follow the Google SRE / Allspaw rubric. Attribute decisions to roles, not individuals; focus on "the system allowed this" rather than "the person did this."

Steps 1–3 are time-critical. Step 4 happens within one week. Steps 5–6 close the loop within two weeks.

### Where the manager is specifically on the hook

Being accountable for the *system* means that when an AI-produced incident happens, the questions that come to the manager are system-shaped, not individual-shaped.

- *Did the team have a review standard for this class of artifact?* If not → why not, and what is being added. If yes → was the standard followed? If not followed, why not — is it a norm problem or an infrastructure problem?
- *Did the standards-as-code stack enforce the subset that it should?* If `AGENTS.md` was silent on the exact rule that was violated, that is a Chapter 3 gap and it is on you.
- *Did the team have an eval that should have caught this?* If it was within scope of a workflow you had already commissioned an eval for, why did the eval not catch it? Calibration? Dataset? Threshold?
- *Was the reviewer bandwidth honest?* If the reviewer approved in 3 minutes because the queue was 40 deep, that is a budget problem — see Chapter 2 — and it is a manager fix.
- *Should the team have been using AI for this class of work at all this quarter?* The C1 decision. The manager made the call; if the call was wrong in retrospect, the contract gets updated and the team is told.

None of these should have a punitive edge. They are system questions about a system the manager owns.

### Where the manager is specifically *not* on the hook

Accountability for the system is not accountability for every reviewer's judgment call. You are not the reviewer-of-record; you are the owner of the standard the reviewer was operating against. Three things the contract should explicitly *not* make you accountable for:

- The specific line-by-line correctness of every model-authored diff. That is the reviewer's accountability, per the stack above.
- The behaviour of a model version you did not know about. If the vendor silently shipped a new default without notice and the regression gate (Chapter 4) was not in place yet, the system change is to *add the regression gate*, not to pretend you should have personally caught it.
- A vendor outage covered by the vendor's SLA.

Being clear about this up front — in the contract — prevents the "manager on the hook for everything" failure mode that burns managers out and leads to risk-averse under-adoption.

### The contract's accountability section, in words

A workable single section, suitable for copy-editing into your team's human/machine contract. (The full contract has four other sections — see mod-101 Chapter 3.)

> **Accountability for AI-generated work.**
>
> - The **IC** who submitted the artifact is accountable for the submission. Using an agent to draft does not transfer accountability.
> - The **reviewer** who approved is accountable for the approval. The verification bar is specified in the PR template and in the review checklist (`/docs/ai-review-checklist.md`).
> - The **manager** (`@manager-handle`) is accountable for the review standard, the standards-as-code stack, the commissioned evals, and the decision to permit AI authorship on each artifact class this quarter.
> - The **vendor** is accountable for their SLA — availability, documented behaviour, published guardrails.
>
> **When an AI-produced artifact is wrong:** we revert or correct within the hour; we report in `#eng-ai-incidents`; we preserve the prompt, model version, tool-authorisation surface, retrieved context, and the as-submitted artifact; we run a blameless post-mortem within one week per the mod-109 runbook; we close the loop into the review checklist, the standards-as-code stack, and the commissioning backlog within two weeks.
>
> **We do not practise blame.** We practise accountability. We follow Google SRE / Allspaw post-mortem norms; we attribute to roles and to systems; we name the specific standard-or-eval change that reduces the probability of the next incident of this shape.
>
> **Change log.** v0.1 2026-10-07 (@manager-handle, kickoff). v0.2 2026-11-03 (@manager-handle, post Q3 incident #41 — added trace-preservation requirements; narrowed C1 on auto-generated incident summaries).

Three paragraphs, a change log, pinned next to the review checklist. The team can point at it when things go right and when they go wrong.

### Signalling language in cross-functional conversations

You will be asked about this contract outside of your team.

- *By a VP:* "What do you do when the AI is wrong?" The answer is the four-party stack + the C4 flow + the pointer to mod-109. Ten seconds.
- *By a governance partner:* "How does your team meet NIST AI RMF MANAGE 2.3 / human oversight obligations?" The answer is: *the contract names the accountable humans at each step; the review checklist specifies the human oversight bar; the commissioned evals produce the evidence; `mod-110` is where this crosswalks to the org level*.
- *By legal / compliance:* "How do you preserve a defensible record when an agent takes an action?" The answer is: *the C4 trace-preservation requirement; the artefact IDs and prompts stored under our retention policy (see `mod-110`); the vendor DPA on file (see `mod-111`)*.
- *By a hiring-loop candidate (per `mod-108`):* "How does your team think about accountability for AI-produced work?" Watch whether they reach for C1 (what's allowed), C2 (what's verified), or C3 (who's on the hook) — most candidates reach for C3; the useful follow-up is whether they also reach for C2.

If you cannot answer any of these in a minute, the contract is not yet load-bearing in your head.

### What stays bounded by the OWASP LLM Top 10 (Chapter 6 preview)

Several C4 trace items (the tool-authorisation surface; the agent's instruction surface; the data that crossed into the prompt) map directly onto the OWASP LLM01 Prompt Injection, LLM02 Insecure Output Handling, LLM06 Sensitive Information Disclosure, LLM08 Excessive Agency, and LLM09 Overreliance risks (OWASP Top 10 for LLM Applications, 2025). Chapter 6 is where the review checklist carries those rows and the commissioning backlog refers back to the contract's C4 obligations as inputs.

## Example: a two-paragraph incident reconstruction

Illustrative — a shaped example, not a verified incident:

> **What happened.** A Claude Code session on a payments-api change proposed a refactor of the idempotency helper. The submitter read the diff, tests passed, the reviewer approved. The change silently inverted the TTL check (expected `>` where the agent wrote `>=`), which widened the idempotency window by one second under clock skew. A duplicate charge was created the following afternoon.
>
> **The accountability play.** *Incident reported* in `#eng-ai-incidents` at 15:04 the next day by the on-call engineer. *Artifact pulled back* via a hot-fix revert at 15:28. *Trace preserved*: prompt chain, Claude Code session ID, retrieved context (which happened to include a stale snippet from an old helper), and the exact as-approved diff, all captured to the incident ticket. *Post-mortem* ran at the Friday ritual with the `mod-109` template: expected behaviour, actual behaviour, system questions. *Loop closure*: (a) added a mutation-test row to the unit-test golden-task eval (Chapter 4) so the TTL branch is exercised; (b) added a `20-security.mdc` Cursor rule banning `>=` on TTL comparisons without an accompanying comment citing the expected semantics; (c) narrowed C1 — idempotency-adjacent refactors now require two reviewers for AI-authored diffs. *Write-up published* two weeks after the incident, blamelessly, attributing the fault to the "model saw stale retrieval context + our eval did not cover mutation on this branch + review-time budget was tight," not to any individual.

Three system changes; no individual named at fault; the contract stronger after than before.

## Summary

- The accountability contract turns "AI generates, humans own" into an operational artifact with a four-party stack: **IC accountable for submission, reviewer for approval, manager for the system, vendor for the SLA.**
- Accountability is not blame. Google SRE and Allspaw provide the discipline; it maps onto AI-produced incidents unchanged.
- When an AI-produced artifact ships broken: pull it back or correct forward; report in a named channel and window; preserve the trace (prompt, model, tools, retrieved context, artifact); run a blameless post-mortem within a week; close the loop into checklist, standards-as-code, and eval commissioning within two weeks.
- The manager is on the hook for the **system** (standard, stack, commissioned evals, bandwidth, the C1 decision), not for every reviewer's judgment call. Making the boundary explicit prevents burnout and risk-aversion.
- Several C4 trace obligations map to OWASP LLM Top 10 risks (Chapter 6). The commissioning backlog (Chapter 4) is where the C4 loop closes.
- The contract's accountability section is three paragraphs plus a change log, pinned next to the review checklist. It is the artifact the team points at when things go right and when they go wrong.
- Exercise 07 is where you draft v0.1 of the accountability contract for your actual team.
