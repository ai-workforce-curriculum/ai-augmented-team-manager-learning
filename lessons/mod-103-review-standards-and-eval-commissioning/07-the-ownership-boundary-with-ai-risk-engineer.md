# Chapter 7 — The Ownership Boundary: What Managers Commission and What `ai-risk-engineer` Owns

> *You are a buyer and user of risk evidence. They are a builder of the rig that produces it. The teams that confuse the two end up with no rig and a manager too deep in the weeds to use it.*

## Motivation

Two sibling tracks sit immediately adjacent to the review-and-eval work this module teaches, and they are the two most frequently blurred:

- [`ai-risk-engineer-learning`](https://github.com/ai-governance-curriculum/ai-risk-engineer-learning), level 25, **AI Governance** family. IC-engineering depth on engineered AI risk — red-teaming, guardrail design and tuning, jailbreak-resistance evaluation, prompt-injection corpora, output-filter implementation, safety-eval harness authoring.
- [`ai-eval-engineer-learning`](https://github.com/ai-engineering-curriculum/ai-eval-engineer-learning), level 30, **AI Engineering** family. IC-engineering depth on general-purpose eval harnesses — dataset curation, judge-model calibration, benchmark methodology, eval-as-product pipelines.

The team-manager (this track, level 40, AI Workforce family) is adjacent to both and *above* neither. All three tracks use overlapping vocabulary — *eval*, *harness*, *judge*, *regression*, *golden task*, *red team* — but they own different slices of the work.

The posting evidence is consistent on this: R2 and R3 use *commission*, *decide*, *own the loop*, and *act on findings*. R13 in the catalog (see [`JOB_REQUIREMENTS.md`](../../JOB_REQUIREMENTS.md)) is named as a **peer dependency**, not as a manager responsibility — *"Engineered AI risk, red-team, and guardrail depth (team consumes)"* with owner `ai-risk-engineer` (L25, AI Governance family) and coverage *"Commissioning contract in `mod-103`; engineering depth linked out."* This chapter writes that commissioning contract down.

Chapter 7's purpose is to make the boundary drawable in a conversation. When a VP asks you *"who owns our LLM jailbreak-resistance?"*, your answer is a sentence that names both sides of the boundary and the artifact that connects them.

## Core concepts

### The boundary, in one sentence

> *The team-manager commissions eval and risk evidence, authorises the scope, and acts on the findings in team practice. `ai-risk-engineer` builds the rig, runs it, and reports the evidence.*

Every row of the table below is a specialisation of that sentence.

### The boundary, in a table

| Activity | You (`ai-augmented-team-manager`, L40, Workforce) | Peer (`ai-risk-engineer`, L25, Governance) |
|---|---|---|
| **Risk inventory for the team's AI workflows** | Enumerate workflows; name candidate risks per workflow (using OWASP Top 10 crosswalk from Chapter 6 as the scaffold); prioritise by business impact | Formalise the risk model; produce threat scenarios with attacker goals and attack surfaces |
| **Red-team methodology** | Authorise scope and budget; read findings; act on them | Design the red-team; build the corpus; run the exercises; publish the report |
| **Guardrail design / output filter / content classifier** | Decide *whether* guardrails are required per workflow (per C1 of the human/machine contract); sign off on the UX trade-offs; commission | Design the guardrail; tune thresholds; evaluate false-positive/false-negative balance |
| **Prompt-injection corpus construction** | Commission; read the report; use the findings to inform the LLM01 row of the Chapter 6 crosswalk | Author the corpus; keep it fresh as attacks evolve; integrate into the capability eval harness |
| **Jailbreak-resistance evaluation** | Decide which claims the team *makes* that must hold under adversarial prompting (e.g., "the agent refuses to call tool X without authorisation"); commission the eval of those claims | Design and run the jailbreak eval; produce the pass/fail/regression evidence |
| **Guardrail roll-out and operations** | Decide roll-out cadence (behind a flag, canary, full); hold the review-time + eval roll-up; triage incidents | Operate the guardrail in production; respond to detection events; tune thresholds over time |
| **Incident response for engineered-risk failures** | Run the team-scope incident process (Chapter 5 + `mod-109`); name the system changes | Produce the engineered-risk forensic analysis; propose the technical mitigation |
| **Governance / regulatory evidence** | Package team-scope evidence for the governance crosswalk (`mod-110`) | Provide engineered-risk measurements to the governance analyst |
| **Benchmark methodology rigor** (statistical power, CI, effect size) | Read-and-challenge; require the harness to report sample size and uncertainty | Own the rigor; defer deepest methodology to `model-evaluation-engineer` (L30, ML Engineering family) |

Two directions of asymmetry worth naming:

- **Upward** — `ai-risk-engineer` is often a *peer* in your team or in a central security / governance org. They are not your reports. You coordinate through a commissioning brief (Chapter 4's artifact), not through a performance review.
- **Downward** — your relationship to `ai-assisted-software-engineer` (L25, Engineering) on your own team is manager-to-IC. That IC may *also* be the owner of eval-harness code for a team-internal workflow. Two things to hold: you are their manager, *and* you commission the eval work as a work product like any other. Treat the brief the same way you would with an external peer.

### Three failure modes on this boundary

**Failure mode A — "I'll build it myself."** The manager who learned Promptfoo in a weekend decides to own the eval harness. Short-term wins; long-term costs. The harness is under-tested because the manager's time is sliced; the manager's ability to set the standard erodes because they are now the standard's author and operator; the eval's results are less credible (the author is grading their own homework). The right move is to find the peer, pay the coordination cost, and write a clean brief.

**Failure mode B — "The risk engineer will tell us what to measure."** The manager who defers the *decision about what matters* to the engineered-risk peer. The peer is excellent at designing the rig for a stated risk; they are not the one who should be deciding which risks to prioritise for *this team's work*. That is a team-context decision. If you abdicate it, you will get a technically rigorous eval of the wrong thing.

**Failure mode C — "The risk engineer's report is self-explanatory."** The manager who assumes the published report will land with leadership on its own. It will not. The commissioning manager's job includes translating the report into team-scope decisions, exec summary, and governance roll-up. That is manager work. The peer should not be re-writing their rigorous report into a VP pre-read.

### The two-sentence script for each cross-functional conversation

Having the boundary drawable in one minute matters more than having it exhaustive. Carry these:

- *To a VP:* "Red-team and guardrail depth sits with `@risk-engineer-peer`; I commission the work, read the reports, and act on the findings in team practice. What would you like to see — the current commissioning backlog, the most recent report, or the team-scope decisions we made because of it?"
- *To a security partner:* "On OWASP LLM Top 10, our team-scope review checklist covers [enumerate]; the engineered side is a commissioning relationship with `@risk-engineer-peer`. Would you like to walk the crosswalk with me?"
- *To a governance analyst:* "Team-scope evidence for NIST AI RMF MANAGE and MEASURE is in our quarterly report; the engineered-risk evidence is produced by `@risk-engineer-peer` on commission; I roll both into my team's governance snippet for `mod-110`."
- *To a candidate (per `mod-108`):* "On this team, red-team and engineered-risk depth lives with a peer function. The manager role is to commission, read, and act. Did the roles at your last job split that way?"

The pattern: name both sides; name the artifact that connects them; invite follow-up.

### What the commissioning relationship looks like in cadence

A workable pattern on most teams:

- **Quarterly** — joint review of the commissioning backlog. What risks has the team taken on this quarter (new agent workflows, new tool connections, new data surfaces)? Which carry commissioned evals? Which are waiting? What has the peer delivered since last quarter and what did it change in team practice?
- **Per workflow** — a one-page commissioning brief (Chapter 4's shape) when a new workflow goes to default-on; a lighter re-commission when a model version changes.
- **Per incident** — the risk engineer is a named participant in post-mortems for engineered-risk failures (Chapter 5, `mod-109`); their forensic analysis goes into the write-up.
- **Per governance cycle** — the risk engineer's evidence feeds the team's governance snippet (`mod-110`) and the org-wide governance program.
- **Opportunistic** — a Slack channel or office-hours where the manager can ask quick "does this smell right?" questions without a formal brief. Preserves the relationship between the big commissions.

A rhythm; not a theatre. Cadence beats intensity on this boundary.

### What this chapter is *not*

- *Not a case against doing the IC work yourself at all.* You will occasionally set up a Promptfoo config as part of the fluency rhythm in [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) Chapter 5. That is reading-level fluency, not ownership. The line is: *is this a production harness the team relies on?* If yes, commission.
- *Not an org-chart assertion.* Some orgs put `ai-risk-engineer` inside the team; some in a central function; some in security; some in a platform team. The boundary of *who does what* is the same regardless of where the lines on the chart run.
- *Not final on specifics.* The exact split with your `ai-risk-engineer` peer will have team-specific nuances. The commissioning brief is where you resolve them.

## Example: a two-sentence cross-functional brief

Illustrative:

> **For an all-hands slide titled "How this team owns AI risk."**
>
> On AI-generated artifacts: our team-manager owns the review standard, the standards-as-code stack, the commissioning backlog, and the accountability contract (`/docs/human-machine-contract.md`). On engineered AI risk — red-team, guardrails, jailbreak-resistance, prompt-injection corpora — we partner with `@risk-engineer-peer` in the Security org; we commission the work, read the reports, and act on findings in team practice.

Two sentences; boundary drawable; the reader knows whose door to knock on.

## Summary

- The team-manager **commissions** eval and risk evidence, **authorises** scope, and **acts** on findings. `ai-risk-engineer` (L25, AI Governance family) **builds** the rig, **runs** it, and **reports** the evidence.
- The boundary is drawable in one sentence and expandable in one table. Carry both.
- Three failure modes to prevent: *building the rig yourself*, *letting the peer decide what matters*, *assuming the peer's report lands on its own*.
- Cadence over intensity: quarterly backlog review; per-workflow brief; per-incident inclusion in post-mortems; per-governance-cycle evidence; opportunistic office hours.
- Adjacent peer ownership map: harness depth → `ai-eval-engineer` (L30, AI Engineering); IC-tier eval builds on your own team → `ai-assisted-software-engineer` (L25); benchmark methodology rigor → `model-evaluation-engineer` (L30, ML Engineering); governance roll-up → `ai-governance-analyst` and `head-of-ai-governance` (via [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/)).
- The commissioning brief from Chapter 4 is the artifact that makes the boundary operational. The two-sentence script keeps it memorable in a cross-functional conversation.
