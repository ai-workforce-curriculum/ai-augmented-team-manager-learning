# Chapter 2 — The Task-Routing Decision: AI, Junior Human, Senior Human

> *Routing is the manager's first lever. Before you argue about the delegation ladder, the HITL gate, or the tool-authorisation band, you have to decide: does this piece of work route to an agent, to a junior human, to a senior human, or to a pair? The jagged-frontier reading from Chapter 1 forces that decision to be explicit.*

## Motivation

A manager who has not authored a routing decision for a recurring workflow has implicitly delegated it to the team's defaults. The defaults are predictable: tasks the senior engineers find tedious go to the AI without a quality gate; tasks the junior engineers find scary go to the senior engineers (and the junior engineer does not learn); tasks the AI handles plausibly but subtly wrong ship without catching the subtlety. Each of the three defaults is a specific instance of the jagged-frontier failure.

The first-order deliverable of this module is a **task-routing matrix**: a short document, legible to the whole team, that says *for each recurring task type, which destination owns it*, with the reason. Three destinations plus the pair variants:

- **AI unattended** — the agent does the task and the output goes straight into the downstream workflow without a human reviewing each instance.
- **AI + human pair** (two sub-variants — *AI drafts, human reviews before use* and *human drafts, AI refines and pattern-checks*) — a human is on the loop for each instance.
- **Junior human** — a junior engineer (level 20–25 IC) does the task, with or without an AI assistant, as a developmental assignment.
- **Senior human** — a senior IC or staff engineer does the task, with or without an AI assistant, because the task demands judgment the junior cannot yet supply.

A fifth destination — **do not do this task at all** — is often the correct answer and is covered at the end of this chapter.

## Core concepts

### The routing rule, derived from the jagged frontier

The decision procedure — not a formula, a procedure — is a short loop any manager can run in a 30-minute meeting with a senior IC present.

**Step 1 — name the task-type precisely.** Not *"code review"* but *"review a one-file bug fix PR for a bug the author has reproduced locally and tested a regression against."* Not *"drafting the sprint plan"* but *"draft the backlog ordering for the next sprint from the current backlog state and the three product priorities the PM has filed."* Specificity is load-bearing because the jagged frontier is specific. Two versions of *"code review"* can sit on opposite sides.

**Step 2 — place the task relative to the capability frontier.** This is the Dell'Acqua et al. check. Ask three concrete questions:

- *Is the required output a transformation of input the model already has (summarise, translate, reformat, lint-check), or a judgment grounded in context the model does not have (team history, stakeholder intent, a half-remembered conversation)?* Transformations lean inside. Judgments lean outside.
- *Can a non-expert reader check the output in under 60 seconds and catch an error, or does the output require 10+ minutes of context to evaluate?* Fast-checkable outputs lean inside — because the HITL pattern of *AI drafts, human verifies* has low overhead. Slow-to-check outputs lean outside, because even a diligent human reviewer will miss subtle errors.
- *Is the task representative of a well-established written corpus the model has likely seen a lot of, or is it a bespoke artifact of the team's local vocabulary and conventions?* Well-represented tasks lean inside; bespoke lean outside.

Three "inside" answers → candidate for *AI unattended* or *AI + human pair*. Three "outside" answers → candidate for *senior human*, possibly with AI as a research tool, not a drafter. Mixed answers → candidate for *AI + human pair* or *junior human + AI*.

The procedure does not produce a definitive routing. It produces a **first-pass placement** that the senior IC can push back on with one or two concrete counterexamples the manager has not seen. Chapter 1's example (the on-call handoff) walked through exactly this placement on four sub-tasks.

**Step 3 — assign the routing with a named reason.** Every routing in the matrix should be legible to the whole team as a sentence: *"This task is routed to AI unattended because X."* If you cannot write the X, the routing is premature.

**Step 4 — name the scheduled re-check.** Every routing has a date on which it is reviewed — quarterly at minimum, more often if the model, the tool, or the team changes. Routings go stale; the matrix must sunset.

### The three destinations and the two pair variants

A fuller picture of what each destination is for, and the acceptance criteria that go with it.

**AI unattended.** The strongest claim in the matrix. The agent produces output and the output enters the downstream workflow without a per-instance human review. *This is appropriate when all of the following hold:* the task sits well inside the frontier; the blast radius of a bad output is small (not an external-facing artifact, not a production write, not a customer-visible decision); a cheap aggregate quality signal exists (sample-audit, periodic eval, downstream user-reported failure rate); and the team has agreed on the acceptable aggregate error rate. Most tasks on a mod-106-literate team should *not* be routed here; a disciplined matrix will have 1–3 AI-unattended entries and the rest are AI-paired. The temptation to over-route here is the biggest routing failure (see below).

**AI + human pair, variant A: *AI drafts, human reviews before use*.** The default for inside-or-near-frontier tasks where a per-instance human review is affordable. AI produces the artifact; a human — junior or senior, depending on the acceptance call required — reviews and signs off before the artifact is used. Appropriate acceptance criteria are inherited from the mod-103 review standard: a checklist of named items, not a thumbs-up gut-check.

**AI + human pair, variant B: *human drafts, AI refines and pattern-checks*.** Common on tasks where the generative act is the valuable one (writing, design, architecture decision records) and the AI serves as a critic / consistency-checker rather than a drafter. The human produces v0; the agent suggests edits, flags inconsistencies, catches typos, or compares to an established pattern library; the human accepts, rejects, or revises. Lower AI influence on the output, higher-value creative work by the human. This variant appears more often than teams expect.

**Junior human (with or without AI).** A task routed to a junior engineer as a *developmental* assignment. Important corollary: *"with AI"* here is not the same as *AI + human pair*. The question is who owns the output. In the pair variant, the senior human co-owns the output; in the junior-human variant, the junior engineer owns the output and the AI is their tool. This distinction decides the review and feedback loop (mod-108 handles the feedback-loop mechanics). Many tasks that senior engineers find routine should be routed here *even if the AI could do them* — see the "skill-growth preservation" argument below and in [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/).

**Senior human (with or without AI).** A task routed to a senior IC or staff engineer because the task sits outside the frontier *and* the judgment required cannot yet be supplied by a junior. Examples: architecture decisions with multi-quarter blast radius; incident-root-cause calls across subsystems; final go/no-go on an irreversible migration.

**A fifth destination — "stop doing this."** An honest routing matrix will surface tasks that neither humans nor AI should be doing at the current cadence. Weekly reports nobody reads. Handoff rituals that duplicate information in the ticket system. Meeting-minutes documents that are a snapshot of the meeting the attendees already attended. The arrival of AI tends to legitimise *more* of this kind of work ("now we can afford to produce it cheaply") when the correct response is to stop producing it at all. Note each such task in the matrix explicitly; it is a finding the next quarterly review can act on.

### The task-routing matrix as an artifact

The matrix is a table, not a document. One row per recurring task type. One page, sortable. Below is the shape; the content is your team's. Exercise 01 produces v0.1.

| Task type (specific phrasing) | Routing | Why (one sentence, jagged-frontier reasoning) | Review mechanism | Re-check date |
|---|---|---|---|---|
| Review single-file bug fix PR with regression test already added | AI + human pair, variant A | Inside frontier (lint-adjacent), fast-checkable; model misses on race conditions so junior reviewer runs the regression test | Checklist from mod-103 review standard; AI diff summary reviewed | 2026-05-01 |
| Author architecture decision record for new storage choice | Senior human | Outside frontier (local-context judgment, multi-quarter blast radius); AI drafts background section only, not the decision | AI output used as research input, not shipped; human-authored decision text | 2026-05-01 |
| Summarise week's alert telemetry for on-call handoff | AI unattended | Inside frontier (quantitative aggregation); blast radius small (handoff doc, humans read-after); audited quarterly | Weekly spot-check; monthly sample-audit by outgoing on-call | 2026-04-01 |
| ... | ... | ... | ... | ... |

The table is scaled to the team's actual task types. A platform team of 18 might have 12–20 rows. A content team of 8 might have 6–10 rows. A matrix with 60 rows is a document nobody will read; a matrix with 2 rows is not doing the work.

Two defensive conventions in the matrix shape:

- **Routings are named per task type, not per tool.** *"Use Cursor for code review"* is not a routing; *"Code review of a single-file bug fix PR is routed to AI + human pair, variant A"* is. Tools change faster than routings; the routing should outlive the specific tool.
- **"Why" is a single sentence grounded in the jagged-frontier reasoning.** If the "why" is *"because it's faster"* or *"because the vendor pitch said so,"* the routing is not defensible when it breaks. Tie it to Step 2 of the decision procedure above: *why this task sits inside / near / outside the frontier.*

### The three mis-routing failure modes

A mod-106-literate manager recognises all three. Each produces a specific pathology visible in the team's output quality, the team's morale, or the cost structure.

**Failure 1 — over-routing to AI unattended.** The team enthusiastically routes tasks to the agent, discovers that the agent produces plausible output, and progressively removes the per-instance human review. Output quality decays slowly, in ways that would show up in a sample-audit but do not show up in the per-instance acceptance (because there is none). Six months later, an external user surfaces a quality issue; a post-mortem reveals the matrix had seven AI-unattended rows where it should have had two. This is Dell'Acqua et al.'s outside-frontier failure in its most common managerial form.

Counter-measures: start with 0–1 AI-unattended entries in v0.1 of the matrix. Each promotion from *AI + human pair* to *AI unattended* is a deliberate decision with a named quality threshold and a dated commitment to the aggregate-audit mechanism. The default is *AI + human pair*, not *AI unattended*.

**Failure 2 — over-routing to senior human.** A protective reaction, often after a near-miss, in which everything that touches the AI gets routed to the senior engineers. Three months later, the senior engineers are overloaded, the junior engineers have stopped learning, and the team's throughput has fallen *below* the pre-AI baseline. The manager has traded one problem (AI errors on inside-frontier work) for another (senior-engineer bottleneck), and gained none of the inside-frontier productivity ([Dell'Acqua et al., 2023](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321)).

Counter-measures: a routing to *senior human* should be *rare and expensive* in the matrix. If more than ~20% of recurring task types are routed to senior humans, ask whether the junior engineers could own them with an AI pair; ask whether the task is inside the frontier and the senior-human routing is just risk aversion.

**Failure 3 — under-routing to junior human.** The most common and the subtlest. A senior engineer looks at an inside-frontier task, decides *"the AI can do this better than our juniors,"* and routes it to AI + senior-human pair. The junior engineer loses the developmental assignment. Over 6–12 months, the junior engineers' judgment on this task-class never develops; the team becomes dependent on AI + senior-human for a task that should have been a mid-level engineer's craft three years into their career. This is the skill-atrophy failure that [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/) treats in depth.

Counter-measures: treat the matrix as a joint artifact between you and the senior IC *and* at least one junior engineer. When a routing to AI + senior-human is proposed for a task a junior "could do," ask explicitly: *"what would this engineer learn if they did this with an AI pair instead?"* Some tasks should be routed to junior-human + AI *precisely because the AI is better at them* — the junior human's learning target includes *noticing when the AI is subtly wrong*, which is a specifically AI-era craft [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/) sharpens.

### The three questions people will ask about the matrix

Pre-empt them in the v0.1 draft.

- *"Why isn't this just a general rule?"* Because the jagged frontier is jagged. Rules of the form *"always route X to AI"* over- or under-fit. The matrix is per task type because the frontier is per task type.
- *"How often does the matrix change?"* Named explicitly: quarterly, plus on model upgrade, plus on tooling change. Each row carries a re-check date.
- *"Who decides?"* The manager owns the matrix; the senior IC co-authors; the junior engineers can propose changes with reasoning. This matches the mod-101 contract on ownership (C3).

### How the matrix composes with the other four pieces of mod-106

The matrix is the *first* artifact because it decides which other artifacts are needed.

- Rows routed to **AI unattended** or **AI + human pair** generate entries in the **delegation ladder** (Chapter 3, Exercise 02): what the agent is allowed to do, with what authority, for this task type.
- All AI-touching rows generate **HITL checkpoints** (Chapter 4, Exercise 04). Variant A rows have a *post-generation review* checkpoint; some rows have a *pre-invocation* checkpoint when the agent is about to touch something expensive or irreversible.
- All AI-touching rows contribute to the **AGENTS.md** file (Chapter 5, Exercise 02) and the **tool-authorisation policy** (Chapter 6, Exercise 03) — what the agent is told about this task type and what tools it can call while working on it.
- The tasks that are no longer taking the team's time because they have been routed to AI are the input to the **attention redirection plan** (Chapter 7, Exercise 05).

If the matrix changes, all four downstream artifacts change. Chapter 3 names the change-management mechanic.

## Example: the platform team's routing matrix at v0.1

A sketch from an 18-person platform-infra team, drawn against the on-call handoff example from Chapter 1. Not a template — a *calibration object* for the shape.

| Task type | Routing | Why | Review | Re-check |
|---|---|---|---|---|
| On-call handoff summary: quantitative alert aggregation | AI unattended | Inside frontier; small blast radius (internal doc) | Monthly sample-audit by rotating senior | 2026-04-01 |
| On-call handoff summary: narrative of the week's two critical incidents | AI + human pair, variant A | Edge of frontier; subtle wrong-root-cause risk | Outgoing on-call reviews narrative, writes root-cause hypothesis themselves | 2026-04-01 |
| On-call handoff: live-risks list for next week | Senior human (outgoing on-call) | Outside frontier; local context not in ticket system | n/a | 2026-07-01 (lower velocity of change) |
| Bug-fix PR review: single file, regression test present | AI + human pair, variant A, reviewer = junior | Inside frontier; junior learning assignment | mod-103 review checklist; AI summary + junior sign-off | 2026-04-01 |
| New-service ADR authoring | Senior human | Outside frontier; multi-quarter blast radius | AI used for background-reading only | 2026-07-01 |
| Weekly team status summary to VP | AI + human pair, variant A | Inside frontier, external-ish audience | Manager reviews and signs off | 2026-04-01 |
| Postmortem write-up from incident Slack timeline | AI drafts timeline, senior human writes conclusion + action items | Narrative-section is inside frontier; action-item authority is outside | Timeline draft reviewed by IC; action items authored by senior human | 2026-05-01 |
| Design doc title pass for library-of-record | **Stop doing this task** | Nobody reads them; title was for a discovery system that no longer exists | n/a | 2026-07-01 |

Eight rows; roughly the ratio a disciplined matrix will land at — one AI-unattended entry, four AI-paired entries, two senior-human entries, one *stop doing this*. A team this size with 12 more recurring task types adds 10–12 more rows and the ratio holds roughly (most entries are AI-paired or junior-paired; AI-unattended and senior-human are the bookends).

## Summary

- The **task-routing matrix** is the first-order deliverable of mod-106 and the decision mechanism for all four downstream artifacts.
- The routing rule has four steps: *name the task-type precisely*; *place it relative to the jagged frontier* using three concrete questions; *assign the routing with a named one-sentence reason*; *name the re-check date*.
- Five destinations: **AI unattended**, **AI + human pair variant A** (AI drafts, human reviews), **AI + human pair variant B** (human drafts, AI refines), **junior human (± AI)**, **senior human (± AI)**. A sixth, **stop doing this task**, is often the correct answer.
- Three recognisable mis-routing failures: *over-routing to AI unattended* (Dell'Acqua outside-frontier failure in managerial form), *over-routing to senior human* (senior bottleneck), *under-routing to junior human* (skill-atrophy — depth in [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/)).
- The matrix is **named per task type, not per tool**; "why" is grounded in the jagged-frontier reasoning; routings carry re-check dates.
- The default routing should be **AI + human pair**, not **AI unattended**. Each promotion to unattended is a deliberate decision with a named aggregate-quality mechanism.
- Exercise 01 produces v0.1 of your team's matrix. Rows in the matrix feed the delegation ladder (Chapter 3), the HITL checkpoints (Chapter 4), the AGENTS.md (Chapter 5), the tool-authorisation policy (Chapter 6), and the attention redirection plan (Chapter 7).
