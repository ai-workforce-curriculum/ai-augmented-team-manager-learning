# Chapter 2 — The Jagged Technological Frontier and the Team Task Sort

> *"Inside the frontier, the model lifts you. Outside, it drags you. The frontier is jagged and not visible from the outside." — paraphrase of Dell'Acqua et al.*

## Motivation

The hardest decision in a team-level AI-adoption roadmap is not *which tool* to buy or *how* to roll it out. It is **which tasks route to AI first and which stay human-led**. Get that wrong and nothing downstream recovers: the wrong tasks picked at step 1 produce either a team that is bored because nothing changed, or a team that is burned because the model generated plausible-looking output on work the model was not ready for.

Dell'Acqua, Kellogg, Mollick, Rao, Mehrotra, Lifshitz-Assaf, Ju, Nikolova, and Lakhani's 2023 BCG + Harvard Business School field experiment with GPT-4 — *Navigating the Jagged Technological Frontier* ([paper](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321)) — gives the current best framing for this decision. This chapter translates that framing into a concrete method you can run on your team's actual task inventory. Exercise 01 is where you apply it.

## Core concepts

### The frontier metaphor

Dell'Acqua et al. ran a field experiment with ≈758 BCG consultants. They gave half of them access to GPT-4 and measured performance on two sets of tasks: one set where the AI tool was genuinely useful ("inside the frontier"), one set where it was not ("outside the frontier"). Two findings stick:

- **Inside the frontier**, consultants with AI significantly outperformed consultants without — the reported paper figures include completing ~12% more tasks, ~25% faster, with a notable quality lift on tasks within the model's capability envelope.
- **Outside the frontier**, consultants with AI performed *worse* than consultants without — the AI output was confidently wrong, and consultants were less able to catch it than a baseline peer would have been.

The two load-bearing properties of the frontier:

1. **It is jagged.** It is not a smooth boundary. Capability on neighbouring-looking tasks differs sharply. Writing a marketing memo from a brief: inside. Combining two numeric tables from a brief: outside. Writing a competitive summary citing recent news: unreliable in a hard-to-spot way.
2. **It is invisible from the outside.** You cannot tell by looking at a task whether it falls inside the frontier. You find out by *running the task through the model* and judging the output. That is what the task sort in this chapter is for.

Treat these as working hypotheses from one well-run experiment, not as physical constants. The frontier shifts with each model generation; an "outside" task today may move inside in six months. The method matters more than any specific list.

### Two work postures Dell'Acqua et al. observed

Dell'Acqua et al. also surfaced two patterns in how workers used the model:

- **Centaur.** A clean division of labour — human does some subtasks, AI does others, they are composed together.
- **Cyborg.** A deeply intertwined back-and-forth — iteration between human and AI within a single subtask.

Both can work. Which is right for a given task depends on how much judgment the task needs mid-stream. A roadmap that says "AI does step A, human does step B" is centaur. A roadmap that says "pair with the model throughout, reviewer checks the final" is cyborg. You will mix both on a real team. Chapter 3's adoption-mode choice (pilot / rollout, opt-in / mandate) interacts with this: a cyborg workflow typically needs more enablement (see [`mod-105`](../mod-105-team-ai-enablement-programs/)) before it becomes a default.

### A six-dimension task-sort rubric

To sort your team's tasks against the frontier, score each candidate task on six dimensions. Keep it short — one score, one note — so you can run the exercise across twenty or forty tasks in a session without it becoming a thesis.

1. **Capability fit (1–5).** On a few representative instances, does the model produce output a reviewer would call useful? This is the *inside-the-frontier* check. Run three real examples before scoring; don't score from gut.
2. **Verifiability (1–5).** Can a human reviewer verify the output in bounded time? A unit test runs; a numeric claim can be checked against a source; a short memo can be read. Non-verifiable output (long-form reasoning with no ground truth) is a red flag regardless of capability fit.
3. **Blast radius (1–5, inverted — higher means safer).** If the model is wrong and the reviewer misses it, how bad is the outcome? Customer-visible, regulated, or hard-to-reverse outputs score low here; sandboxed, reversible outputs score high.
4. **Frequency (1–5).** How often does your team do this task? High-frequency, moderate-stakes work is where the roadmap gets its ROI; low-frequency work is rarely worth a pilot.
5. **Judgment density (1–5, inverted — higher means safer).** How much tacit, context-dependent judgment does the task need — about team norms, people, in-flight politics, downstream consumers the model cannot see? Feedback writing, promotion packets, incident narratives, and go/no-go calls are judgment-dense; a test skeleton is not.
6. **Reversibility (1–5).** If you ship a wrong AI-drafted output and catch it an hour later, can you take it back? Code behind a feature flag, yes. A customer email that already went, no.

Sum or threshold. A rough and workable rule of thumb: tasks that score ≥18 across the six dimensions with no single score ≤2 are good *AI-first* candidates for the quarter. Tasks that score ≤12 or have any score of 1 in blast radius / verifiability / judgment density are *human-led* this quarter. Tasks in the middle are *pilot candidates* — route a couple through a scoped pilot (Chapter 3) and let the pilot resolve the question.

The rubric is a scaffold; it is not a formula. Use it to force the conversation, not to replace it. A high-blast-radius task with score 18 is still human-led.

### Four outcome buckets

The task sort should end with every task placed in one of four buckets. This is the output you will transcribe into section 2 of the roadmap artifact in Chapter 1:

- **AI-first this quarter.** Clear inside-the-frontier tasks with workable verification and tolerable blast radius. Example families: PR descriptions, test skeletons, ADR first drafts, SQL skeletons, runbook edits, non-customer-facing summaries.
- **AI-assisted with review-only.** The model may draft, but the artifact only ships after a specified human pass. Example families: customer-facing error messages, external docs, moderate-stakes code in high-traffic paths.
- **Human-led this quarter.** The model may be used for scratch thinking but does not produce the shipped artifact. Example families: employee feedback, performance input, promotion packets, incident post-mortems, security-sensitive code, legal-facing communications.
- **Not yet decided — pilot this quarter.** The rubric does not resolve it; the only honest move is to pilot it. Example families: anything dependent on a new model version, anything where the team is split, anything where capability fit is uncertain.

The buckets are deliberately the same shape as the C1 table in the human/machine contract ([`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) Chapter 3). The two documents should match. A task that is *AI-first* in the roadmap must also be *AI-may-draft* in the contract; a *human-led* task in the roadmap must be *AI-may-not-draft* in the contract. If they disagree, one of them is out of date — fix the contract first, then the roadmap.

### Running the sort as a team

Two posture choices matter:

1. **Who sources the task list?** You, from the team's actual work — PR titles over the last two months, ticket categories, stand-up topics, meeting types. Not from a template and not from a tool's marketing page. The task list has to be the team's real work, or the sort is theatre.
2. **Who does the scoring?** You, with 2–3 senior ICs who do the work daily. Not solo — solo sorts bias to the manager's model of the team's day. Not the whole team — whole-team sorting is a long meeting with a flat sort. 2–3 ICs is enough to catch the manager's blind spots and short enough to run in 90 minutes.

The sort re-runs **every quarter** at minimum, and after any of: a model generation upgrade, a new tool rolled into the team, an incident ([`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/)) that revealed a mis-routed task, or a change in the C1 contract.

### Where the sort connects downstream

- **Chapter 3** uses the pilot-candidate bucket to decide sequencing (pilot vs. rollout, opt-in vs. mandate).
- **Chapter 4** uses industry-survey evidence to pressure-test the sort. Microsoft's *Work Trend Index* and the Stack Overflow Developer Survey tell you where other teams land; your sort should reconcile against theirs, not blindly copy.
- **Chapter 5** uses the AI-first bucket to decide which tasks need Platform-owned infrastructure (shared Cursor-rules deployment, token-cost dashboards) vs. team-owned configuration.
- **Chapter 6** takes the final sort into the roadmap one-pager and the exec pre-read.
- **[`mod-103`](../mod-103-review-standards-and-eval-commissioning/)** encodes the verification requirements for AI-first and AI-assisted tasks into standards-as-code.
- **[`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/)** redesigns the actual workflow for each AI-first task family (where agents fit, which tools, which guardrails).
- **[`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/)** guards against skill atrophy on the human-led bucket — when you route a task to AI, the human skill behind it still has to be practised deliberately or it decays.

## Example: a 10-engineer platform team's task-sort session

Illustrative, not prescriptive. One 90-minute session, manager + 3 senior ICs, in a shared doc:

| Task | Capability fit | Verifiability | Blast radius (↑ safer) | Frequency | Judgment density (↑ safer) | Reversibility | Sum | Bucket |
|---|---|---|---|---|---|---|---|---|
| PR description drafting | 5 | 5 | 4 | 5 | 5 | 5 | 29 | AI-first |
| Unit test skeleton | 5 | 5 | 4 | 4 | 5 | 5 | 28 | AI-first |
| ADR first draft | 4 | 4 | 4 | 3 | 3 | 5 | 23 | AI-first |
| SQL against lakehouse | 4 | 4 | 3 | 5 | 4 | 4 | 24 | AI-first |
| Customer-facing error copy | 4 | 4 | 2 | 4 | 3 | 3 | 20 | AI-assisted (review-only) |
| On-call runbook edit | 4 | 4 | 3 | 3 | 3 | 4 | 21 | AI-assisted (review-only) |
| Migration sequencing plan | 3 | 2 | 2 | 1 | 2 | 2 | 12 | Human-led |
| Incident post-mortem | 3 | 2 | 1 | 1 | 1 | 1 | 9 | Human-led |
| Employee feedback | 3 | 2 | 1 | 2 | 1 | 1 | 10 | Human-led |
| Golden-task eval authoring | 3 | 3 | 3 | 2 | 3 | 4 | 18 | Pilot candidate |

The team now has: six AI-first families to design into the roadmap, two AI-assisted families with explicit review bars, three human-led families to protect against drift, and one pilot candidate to trial in the quarter. The sort fits on a page; every decision is visible; the sort survives model churn because each cell is a judgment the team made on today's model, dated and attributed.

## Summary

- The jagged technological frontier (Dell'Acqua et al. 2023) is the current best framing for which tasks route to AI first. Inside it, AI lifts you; outside, AI drags you; the boundary is not visible from the outside.
- You cannot pick AI-targeted tasks from a tool's marketing page. You have to sort your team's **actual** tasks, in a scored rubric, with ICs who do the work.
- Score each candidate task on six dimensions: capability fit, verifiability, blast radius, frequency, judgment density, reversibility. Push each task into one of four buckets: AI-first, AI-assisted, human-led, pilot candidate.
- The task sort is the input to the roadmap's sequencing (Chapter 3) and to the artifacts (Chapter 6). It is also the operational twin of the C1 section of the human/machine contract — they must stay consistent.
- Re-run the sort every quarter and after model generation changes, tool additions, incidents, or contract updates. The sort is a living document.
