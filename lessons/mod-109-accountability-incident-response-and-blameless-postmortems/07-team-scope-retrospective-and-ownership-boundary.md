# Chapter 7 — The Team-Scope Incident Retrospective and the Ownership Boundary

> *The post-mortem is the record of one incident. The team-scope retrospective is the record of a quarter's worth. The retrospective is the artifact a reader two cycles later picks up, reads in 20 minutes, and uses to act on their own team — or the artifact the upward specialist uses to decide whether the team's standards have moved. This chapter closes the module by naming the retrospective shape and drawing the ownership boundary against counsel, SecOps, and the levels above.*

## Motivation

The chapters up to this point cover the operational practice around one incident — detect, triage, contain, preserve, report, learn, close. But the manager's job also has a *cumulative* dimension. Over a quarter the team runs multiple incidents of varying severity; over a year the standards stack, the eval set, the routing matrix, and the contract have all moved. The team-scope retrospective is the artifact that reports and reflects on the cumulative movement.

The retrospective has two audiences:

- **Future members of the team itself**, including the manager's own future self. The quarterly rhythm means that by the end of year two, the manager cannot remember the specific decisions and tradeoffs from four quarters ago. The retrospective is memory.
- **The upward specialist chain** — `ai-enablement-lead` at L45, `ai-engineering-manager` at L50, `head-of-ai-governance` at L60. The retrospective is one of the artifacts the upward chain reads when reviewing the team's AI practice at the quarterly or annual rhythm. It also feeds into [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/)'s NIST AI RMF MANAGE evidence base.

The chapter also serves as the module's **ownership-boundary** closer — every module in the track ends by naming the boundary against the specialties around the manager. mod-109's boundaries are sharper than most because engineered-risk, SecOps, legal counsel, and L45+ cross-team coordination all touch incident work. The boundary chapter prevents the overreach failure mode.

## Core concepts

### The retrospective artifact — what it contains

The team-scope incident retrospective is a 4–6 page document authored once per quarter by the manager (with input from the IC team and the specialist peers who were engaged). A workable table of contents:

1. **Quarter summary.** Count of incidents by severity and by class (per [Chapter 4](04-ai-specific-incident-taxonomy-and-triage.md)'s four classes). Any near-misses caught by commissioned evals. Any zero-severity signals worth noting.
2. **The three highest-leverage changes.** Of the backfeed actions that landed this quarter, which three produced the most compounding value? Usually: an eval row that caught a near-miss during the quarter; a routing-matrix amendment that moved a workflow; a tool-authorisation tightening that prevented a near-miss.
3. **The open backlog.** Backfeed tickets open > 2 weeks. The manager's commitment for the next quarter.
4. **Upward-handoff summary.** Incidents that engaged `ai-enablement-lead`, `ai-engineering-manager`, counsel, or `head-of-ai-governance`. A one-paragraph summary of the handoff and the current status.
5. **Standards drift.** The accountability contract's change-log for the quarter. The review checklist's new rows for the quarter. The eval set's new rows for the quarter. How the routing matrix moved.
6. **Patterns across incidents.** If the quarter had three incidents and they share a shape (e.g., all three were context-staleness Class 1s), that pattern names a structural gap bigger than any single incident's backfeed addresses. The retrospective names the pattern and what the next quarter addresses.
7. **Metrics.** Mean-time-to-detect by class. Mean-time-to-contain. Incident-to-eval rate (Chapter 6). Backfeed close-out percentage. The metrics are for the manager's calibration; a summary sentence to leadership is derived from them.
8. **What we are watching.** Public-precedent signals from the [AI Incident Database](https://incidentdatabase.ai/) and [OECD.AI Incidents Monitor](https://oecd.ai/en/incidents) that look adjacent to the team's work; vendor-side signals (model deprecations, changelog movements); published guidance updates (NIST AI RMF revisions, OWASP LLM Top 10 updates, EU AI Act Article 73 guidance).
9. **Change log.** Who authored this retrospective, who contributed, what prior retrospective it builds on.

The retrospective is explicitly **readable by a new team member who joined yesterday** and by an **upward specialist who has no context on the team's AI surface**. If a reader two cycles later picks it up and cannot act on it, the retrospective has failed as the memory artifact.

### What the retrospective is *not*

- **Not a status report.** Status reports are forward-looking; the retrospective is reflective. If the entire document is a project-plan narrative, it has drifted.
- **Not a performance review.** No individual is named for praise or criticism — *all attribution is to roles and to systems*, per the [Chapter 3](03-blameless-postmortems-adapted-for-ai.md) blameless frame. The manager's 1:1 and performance work is separate and lives in [`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/).
- **Not a sales pitch for AI.** The retrospective is honest. A quarter in which the team had three expensive incidents and the eval set did not catch them is a retrospective that says exactly that, with the action plan. Over-polishing the narrative up to leadership destroys the artifact's utility.
- **Not a weekly update stacked.** The weekly backfeed ritual's dashboard is a different artifact (Chapter 6). The retrospective is a reflective document, not a running log.
- **Not the post-mortem write-ups re-copied.** Post-mortems are per-incident; the retrospective is a quarter-scale view. It references the post-mortems; it does not re-paste them.

### The annual review of the stack

Alongside the quarterly retrospective, the manager runs an annual review of the full standards stack and eval set. The annual review:

- **Retires obsolete eval rows.** Rows authored for workflows that no longer exist; rows superseded by broader-coverage rows; rows that have been consistently green for a full year and no longer earn their compute.
- **Reviews the routing matrix against the year's incidents.** If the matrix routed workflows to AI-first that generated three incidents in the year, the routing choice is revisited.
- **Reviews the accountability contract.** Any C1 (scope), C2 (verification bar), C3 (accountability stack), C4 (process), or C5 (data scope) sections that the year's incidents have proved need revision.
- **Reviews the routing contract with specialist peers.** Per [Chapter 5](05-routing-contract-with-risk-engineer-and-secops.md)'s quarterly review ritual — the annual review is the fourth of those, with an extended scope that includes vocabulary, trigger-line coverage, and SLA satisfaction.
- **Composes with [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/)**'s NIST AI RMF practice. The annual review is the primary evidence-production event for the MANAGE function's annual review subcategory.

The annual review lands on [`mod-112`](../mod-112-cross-functional-leadership-and-ritual-calendar/)'s calendar; typically Q4 for a calendar-aligned organisation.

### Ownership boundary — the three sideways lines

mod-109's module scope is team-scope AI-incident response. Three sideways specialties genuinely own adjacent work; the boundary is explicit.

**Boundary 1 — `ai-risk-engineer` (L25, AI Governance family).**

- Manager-side: commission engineered-risk work; name the specific ask; act on findings; feed the findings into mod-103 eval commissioning and mod-106 routing updates; communicate findings to the team and to leadership.
- `ai-risk-engineer`-side: reproduce the model behaviour; design the guardrails; author the evals that require method depth; audit the broader surface; author the engineered-risk-side of the post-mortem (which is co-authored with the manager and typically appears as supporting evidence in the team's post-mortem write-up).
- Shared: the vocabulary (Chapter 5); the trace archive; the specific incidents; the cross-team patterns.

The engineer is a peer, not a subordinate. The commissioning relationship is a peer-to-peer contract, not a manager-to-IC assignment. [Exercise 04](exercises/exercise-04-routing-contract-with-risk-engineer-and-secops.md) co-authors the contract.

**Boundary 2 — SecOps / DFIR.**

- Manager-side: recognise SOC triggers at Step 2 triage; engage SecOps at Step 5 of Chapter 2's flow; participate in the organisation's security IR process per their runbook; communicate team-side status while SOC runs SOC-side; close out the team-side artifacts.
- SOC-side: forensic timeline; data-exposure assessment; credential-rotation decisions; eradication and recovery; regulator-notification clock management; vendor-partner notification where contractually required.
- Shared: the trace archive; the timeline of events; the shared stakeholders.

The organisation's existing security IR process is the authoritative runbook when SecOps is engaged. The manager runs team-side within that process; mod-109's runbook is additive, not substitutive.

**Boundary 3 — Legal counsel (through HR or General Counsel's office).**

- Manager-side: recognise the legal triggers at triage (regulator notification implications, contract breach, employment-law implications); flag them to counsel through the appropriate partner; preserve the trace that counsel will need; communicate factually with no legal speculation.
- Counsel-side: all legal opinion; all regulator engagement; all public disclosure decisions; all contract-interpretation decisions; all employment-law-visible actions.
- Shared: the factual trace; the timeline; the stakeholder list.

Legal opinion is outside this module's scope. The module's job is to make counsel's job easier by producing the factual record counsel needs. When counsel asks "walk me through what happened," the trace archive from Chapter 2 Step 4 is the answer.

### Ownership boundary — the three upward lines

**Upward 1 — `ai-enablement-lead` (L45, AI Workforce family).**

- Team-side: run the team's incident practice end-to-end; produce the retrospective; participate in cross-team coordination when a shared failure mode is identified.
- `ai-enablement-lead`-side: multi-team incident coordination; organisation-wide advisories when a single team's incident generalises; cross-team standards drift that spans teams.
- When to engage: incidents that affect more than one team's work; incidents where the fix is organisation-wide; patterns that suggest a cross-team standard is needed.

**Upward 2 — `ai-engineering-manager` (L50).**

- Team-side: same as upward 1.
- `ai-engineering-manager`-side: engineering-manager-of-managers incident coordination; multi-team manager-level comms; cross-team post-mortem authoring where multiple team managers' teams were involved.
- When to engage: incidents involving multiple engineering teams under the same L50 reporting line; patterns of incidents across teams that suggest an engineering-level process is needed.

**Upward 3 — `head-of-ai-governance` (L60) and `chief-ai-officer` (L70).**

- Team-side: provide the factual record, the post-mortem, the retrospective.
- L60/L70-side: program-level incident reporting; regulator engagement; board-level communication; public disclosure; cross-function coordination with legal and PR.
- When to engage: incidents with regulator-notification obligations; public-disclosure in play; incidents that warrant board-level attention; program-level governance changes.

The upward chain is informational for most incidents and action-oriented for Sev-1 incidents with external exposure. The manager's job is to flag the trigger and provide the artifacts; the upward chain owns the upward decisions.

### Ownership boundary — the three out-of-scope lines

- **Not `agentic-safety-engineer` (L40, AI Governance).** Frontier-capability red-teaming and alignment-eval depth belong to this specialty. Manager-scope incident response does not re-run this work; when an incident requires frontier-capability reproduction, it routes through `ai-risk-engineer` at L25 who may escalate further within their family.
- **Not org-wide procurement.** A Class 4 incident may surface a vendor-governance problem; the vendor-governance work routes to [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) and, at scale, to `ai-enablement-lead` for procurement across teams.
- **Not board-level or regulator-facing communication.** Even in a Sev-1 incident, the manager does not author board-level communication or regulator-facing statements. The L60/L70 chain and counsel own those; the manager provides the factual record.

### Where the retrospective lands on the governance stack

The retrospective is an evidence artifact for multiple governance frameworks:

- **[NIST AI RMF 1.0](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf) MANAGE 2 and MANAGE 4.** The retrospective is the primary team-scope artifact for the MANAGE function's incident-response and risk-response subcategories. [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) is where this crosswalks to the organisation's governance program.
- **[EU AI Act Article 14 (human oversight)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj).** The post-mortems and the retrospective together are evidence that human oversight is in place for the team's AI systems. Article 14 applies specifically to high-risk systems; for team-scope deployments that are not high-risk, the evidence is still relevant for the organisation's upward-rolling compliance posture.
- **[EU AI Act Article 73 (serious-incident reporting)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj).** For teams whose AI touches high-risk systems in EU scope, Article 73 imposes notification obligations. The manager's role is to flag the trigger per Chapter 5; counsel and the L60 chain own the Article 73 notification.
- **[ISO/IEC 42001:2023](https://www.iso.org/standard/81230.html).** The AI management system standard's incident-handling clause reads cleanly against the mod-109 artifacts. Where the organisation is pursuing ISO/IEC 42001 certification, the team-scope retrospective is the primary team-scope evidence.
- **[NIST AI RMF Playbook](https://airc.nist.gov/AI_RMF_Knowledge_Base/Playbook).** For organisations running the AI RMF, the Playbook's practice guidance for MANAGE maps to the mod-109 artifacts almost directly.

The manager does not have to author these governance artifacts themselves; the retrospective is the input from which they are composed. `mod-110` is the module that owns the composition.

### Common failure modes in authoring the retrospective

- **Writing for upward audience first.** Same failure mode as in Chapter 3 for the post-mortem. The team is the primary audience; the upward summary is a derivative.
- **Over-polishing.** Smoothing away uncomfortable truths ("we had three incidents from the same root cause") produces a retrospective that is useless for the next reader. Honesty is the practice.
- **Omitting near-misses.** Near-misses caught by evals or reviewers are the highest-leverage signal — they show what the standards *prevented*. Omitting them makes the standards invisible to upward audiences.
- **Writing one retrospective at the end of the year and none in between.** The quarterly rhythm is the rhythm the team's memory decays at; annual retrospectives are a different artifact.
- **Writing the retrospective without the specialist peers.** The engineered-risk peer's view on the quarter's patterns is often the most useful content. Not inviting them to contribute produces a one-sided retrospective.
- **No "what we are watching."** Without Section 8, the retrospective is backward-only. The watching list is where the team's forward attention lives.

## Example: a quarter's retrospective in outline

Illustrative — a composite outline, not a case study.

> **Q3 incident retrospective, team-scope.** Three incidents this quarter: Sev-2 hallucination (wrong number to executive dashboard), Sev-3 prompt-injection near-miss (README injection, caught before impact), Sev-2 model regression (eval dashboard caught the drop; no harm shipped). One near-miss the eval caught in week 10 — same shape as Q1 incident; the Q1 eval row did exactly what it was authored to do.
>
> **Three highest-leverage changes.** (1) Staleness detection in retrieval configuration — has caught two subsequent stale-context issues at author-time. (2) HITL checkpoint before shell tool calls from external content — prevented a potential Class 2+3 composed incident in week 9. (3) Version-pin on the code-review agent — caught another regression two weeks after the original.
>
> **Open backlog.** Two tickets open > 2 weeks: vendor-governance escalation on the Q3 regression's notification-SLA failure (owner: team manager; routed to `ai-enablement-lead` for broader action; blocker: vendor response). Next quarter's commitment: resolve vendor ticket by end of week 4; no other > 2-week stalls carried.
>
> **Upward handoffs.** `ai-enablement-lead` informed on the vendor-governance escalation; an organisation-wide advisory authored. Counsel not engaged this quarter. `head-of-ai-governance` not engaged this quarter.
>
> **Standards drift.** Accountability contract change-log: two entries (shell-tool authorisation tightening; staleness requirement in retrieval). Review checklist: one new row. Standards-as-code: one new Cursor rule on README ingestion. Eval set: three new rows (mutation test on aggregation; injection detection on README-shaped content; canary for the regressed model behaviour).
>
> **Patterns.** Two of three incidents involved retrieved context that was stale or untrusted. Pattern signal: the team's retrieval pipeline is a load-bearing layer that has had less attention than the agent policy. Next quarter: dedicated audit of the retrieval surface with `ai-risk-engineer`.
>
> **Metrics.** MTTD by class: hallucination 36 hours (unchanged QoQ); injection 20 minutes (improved — the HITL added last quarter caught it); regression 3 days (eval dashboard). MTT-contain: median 45 minutes. Incident-to-eval rate: 3/3. Backfeed close-out: 8/10 within SLA (the two open are the vendor ones).
>
> **What we are watching.** AIID — recent cluster of context-poisoning cases in RAG systems (adjacent to our retrieval work). OWASP LLM Top 10 — Q4 revision due. Vendor side — the vendor's deprecation notice for an older model used by one of our evals.
>
> **Change log.** Authored 2026-11-15 by manager; contributors: senior IC lead, `ai-risk-engineer`, SecOps lead. Builds on Q2 retrospective 2026-08-15.

The retrospective is four pages. A new manager inheriting this team reads it in 20 minutes and acts.

## Summary

- The team-scope incident retrospective is the quarterly artifact that reports and reflects on the team's incident practice. It is memory, not status, and it is written for the team first and leadership second.
- **Nine sections:** quarter summary; three highest-leverage changes; open backlog; upward-handoff summary; standards drift; patterns across incidents; metrics; what we are watching; change log.
- **An annual review** of the standards stack and eval set retires obsolete rows, revisits the contract, and composes with [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/)'s governance evidence. Lands on the [`mod-112`](../mod-112-cross-functional-leadership-and-ritual-calendar/) calendar.
- **Sideways ownership boundaries:**
  - [`ai-risk-engineer`](https://github.com/ai-governance-curriculum/ai-risk-engineer-learning) (L25) owns engineered-risk method depth; the manager commissions and acts.
  - SecOps / DFIR owns SOC-side chain; the manager participates per the organisation's security IR process.
  - Counsel owns legal opinion, regulator engagement, and disclosure; the manager flags triggers and provides the factual record.
- **Upward ownership boundaries:**
  - [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) (L45) for multi-team incident coordination and organisation-wide advisories.
  - [`ai-engineering-manager`](https://github.com/ai-engineering-curriculum/ai-engineering-manager-learning) (L50) for engineering-manager-of-managers scope.
  - [`head-of-ai-governance`](https://github.com/ai-governance-curriculum/head-of-ai-governance-learning) (L60) and [`chief-ai-officer`](https://github.com/ai-governance-curriculum/chief-ai-officer-learning) (L70) for program-level incident reporting, regulator engagement, board-level communication, and public disclosure.
- **Out-of-scope:** frontier-capability red-teaming ([`agentic-safety-engineer`](https://github.com/ai-governance-curriculum/agentic-safety-engineer-learning) L40 AI Governance); org-wide procurement at scale; board / regulator / public communication.
- **Governance stack composition:** the retrospective is evidence for [NIST AI RMF](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf) MANAGE 2/4, [EU AI Act](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) Article 14 and Article 73, [ISO/IEC 42001](https://www.iso.org/standard/81230.html), and the [NIST AI RMF Playbook](https://airc.nist.gov/AI_RMF_Knowledge_Base/Playbook). [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) owns the composition.
- **Common failure modes:** writing for upward audience first; over-polishing; omitting near-misses; annual retrospective only; writing without specialist peer input; no "what we are watching" section.
- **Composes with** every prior mod-109 chapter (the retrospective aggregates the module's artifacts) and with [`mod-103`](../mod-103-review-standards-and-eval-commissioning/), [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/), [`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/), [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/), [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/), and [`mod-112`](../mod-112-cross-functional-leadership-and-ritual-calendar/).
