# Exercise 01 — Team Incident Runbook Authoring

**Estimated effort:** 3 hours.

## Objective

Produce **v0.1 of your team's AI-incident runbook**: a 5–8 page artifact covering the seven steps of [Chapter 2](../02-operating-the-accountability-contract-end-to-end.md) — detection channels, severity ladder, incident-class picker, contain checklist, trace-preservation checklist, structured report template, close-out routing — plus a short scope statement and a change-log entry.

The deliverable is the runbook the incident commander will run against when something goes wrong, authored in cold light so that the live-incident hour is spent on case-specific decisions rather than on improvising the infrastructure. The methodological anchor is [`mod-103` Chapter 5](../../mod-103-review-standards-and-eval-commissioning/05-the-accountability-contract-ai-generates-humans-own.md)'s accountability contract composed with [Google SRE *Managing Incidents*](https://sre.google/sre-book/managing-incidents/) and [NIST SP 800-61 Rev. 2](https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-61r2.pdf).

## Prerequisites

- [Chapter 1](../01-the-ai-incident-problem-and-why-this-module-exists.md) — the five pieces of mod-109 and the scope boundary.
- [Chapter 2](../02-operating-the-accountability-contract-end-to-end.md) — the seven steps and each step's AI-specific content.
- [Chapter 4](../04-ai-specific-incident-taxonomy-and-triage.md) — the four AI-specific incident classes; the picker embeds here.
- [`mod-103` Chapter 5](../../mod-103-review-standards-and-eval-commissioning/05-the-accountability-contract-ai-generates-humans-own.md) — the accountability contract the runbook operationalises.
- Your team's **existing incident-response runbook** (if any), whether an SRE runbook, a security-IR runbook, or an organisation-wide IR policy. The exercise extends what exists; it does not author a parallel system.
- Access to the agents / harnesses your team operates (Claude Code, Cursor, Copilot, bespoke) and the observability tooling that captures their traces (LangSmith, Weave, Arize, or none).
- 30 minutes with the on-call engineer, the `ai-risk-engineer` peer (if present at the organisation), and the security-operations (SOC) lead, to validate detection channels and trigger lines.

## Problem statement

Your team runs AI-augmented engineering work. The mod-103 accountability contract is pinned. There is no AI-specific runbook; when something goes wrong, the response will be improvised. The runbook is the specific, written-down version of Chapter 2's seven steps that the team can run in minute 10 of a hot incident without consulting anyone.

The exercise's scope is specifically *operational* — detection, triage, containment, trace preservation, report, routing. The *post-mortem template* is Exercise 02; the *routing contract with specialist peers* is Exercise 04. The runbook names *when* those exercises' artifacts are invoked and *where* to find them; it does not re-author them.

The common failure mode the exercise prevents: a runbook that lists the steps in the abstract but does not answer the specific questions the incident commander will actually have. *Which Slack channel? What phone number? What is the on-call rotation for pager-vs-Slack-only detections? What does the severity "Sev-2" exactly mean this quarter? Who is the person to call on the SOC when it is 10pm?* A runbook that does not answer those is a runbook that will not survive its first live incident.

## Steps

1. **Pull the existing IR process onto one page.** Even if your team has no AI-specific runbook, the organisation almost certainly has a security IR process or an SRE runbook. Capture its detection channels, its severity ladder, its on-call rotation, and its escalation path. The AI-specific runbook extends this, it does not replace it. Where the existing process is silent on AI, call out the gap.
2. **Author the scope statement.** One paragraph. What this runbook covers (AI-produced wrongness at team scope), what it does *not* cover (pure-infrastructure outages — route to existing SRE runbook; security incidents — route to SecOps; performance-management conversations — route to [`mod-108`](../../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/)). The scope statement is the first page of the runbook.
3. **List detection channels.** For each of the four categories in Chapter 2 Step 1 (operational, eval-regression, downstream-consumer, vendor-side), name the specific channel on your team's stack (Slack channel name, email alias, dashboard URL, alert routing, etc.) and the specific human or on-call rotation that responds. If a category has no channel today, mark it as a gap and name the owner for adding one.
4. **Author the severity ladder.** Four levels. For each: a one-sentence definition, a reach-and-reversibility test, examples in your team's domain, and the comms cadence expected at that severity. Compose with but do not duplicate the organisation's SOC severity ladder (write the mapping line per Chapter 5).
5. **Author the incident-class picker.** One-of-four (per Chapter 4's taxonomy) plus an "additional classes composed" field. For each class, a one-sentence definition and a specific "example in our team's domain" sentence.
6. **Write the contain checklist.** Specific, ordered, 6–10 bullets. The first bullet is *"revoke the agent's tool authorisations if the session is still active."* Subsequent bullets cover revert / correct-forward / SOC engagement / downstream notification pauses. The checklist is runnable in 20 minutes by an engineer who has never run it before.
7. **Write the trace-preservation checklist.** Specific, ordered, one bullet per artifact (prompt, model + version, harness + version, tool authorisations, retrieved context, as-submitted artifact, reviewer's path). For each: where it lives on your team's stack (session archive path, observability platform URL, repo path). If any of the seven cannot be captured reliably today (e.g., retrieved context is not logged), mark it as a gap and name the owner for addressing it.
8. **Author the structured-report template.** Five fields: what happened, severity + class, who is on it, blast radius, triggers flagged. One page. Include the specific Slack / email / ticket template text, formatted for copy-paste. Include the distribution list (who gets this report — IC, reviewer, manager, specialist peers, upward).
9. **Author the close-out routing.** The Step 7 backfeed destinations, listed with specific paths on your team's stack: review checklist path, standards-as-code repo and rule files, eval repo and backlog location, routing-matrix document, HITL-checkpoint document, tool-authorisation policy document, accountability-contract change-log location. Each destination with its specific artifact author / owner (not a role, a person).
10. **Validate with the on-call engineer.** 30 minutes. Walk the runbook with the senior IC on the on-call rotation. *"If you got paged at 2am on a Thursday and had to run this cold, could you? What would you look up and not find?"* Record specific friction points and corrections in the runbook's change-log.
11. **Validate with the SOC lead and the risk engineer peer.** 30 minutes each, independently. The SOC lead reads the SOC-routing triggers and the severity-ladder mapping. The risk engineer reads the trace-preservation checklist and the incident-class picker. Record their specific corrections.
12. **Decide rollout.** Default: runbook v0.1 is live for all incidents the week after validation. Any incident that happens before validation runs under the prior (improvised) practice; post-mortem explicitly compares against what v0.1 would have produced, as calibration.

## Starter guidance

- **The runbook is the artifact that fits in the 10th minute.** Author so that the incident commander, in minute 10 of a hot incident, can open the runbook and find the specific thing they need without reading five pages of framing. The scope statement is page 1; the actionable checklists are pages 2–6.
- **No "TBD" survives into v0.1.** Every section either has content or an explicit gap marker with an owner. A section marked TBD will be treated as "we have a runbook" by the organisation but will produce an improvised response during an incident. If a gap exists, name it as a gap, with owner and date.
- **Detection channels are plural, and the downstream-consumer channel is the one teams forget.** The Chapter 1 running example (wrong number reached a partner before the pipeline team knew) is this failure mode. Name the specific non-engineering channels that will see AI-produced wrongness before the engineering team does.
- **Specific over generic.** "Slack" is not a channel; `#eng-ai-incidents` is. "On-call" is not a rotation; the rotation link in the organisation's on-call tool is. "Observability platform" is not a location; `https://smith.langchain.com/o/<org>/projects/<team>` is.
- **The incident-class picker's "example in our team's domain" line is load-bearing.** The picker is useless if the incident commander cannot translate the generic class to "oh, this one." A concrete, team-domain-matched example per class — three sentences — is what makes the picker runnable in minute 10.
- **Do not author a standalone SOC IR runbook.** The organisation almost certainly has one. The AI-specific runbook names the trigger lines (per Chapter 5) and the handoff; the SOC's runbook runs from there. Duplicating the SOC runbook creates a maintenance liability.
- **The change-log is the first thing on page 1 after the scope statement.** Future readers (including you) need to know what version this is, when it was authored, who validated it, and what has changed.
- **Length guidance.** 5–8 pages total. Scope + change-log on page 1; detection channels on page 2; severity + class picker on page 3; contain + trace-preservation checklists on pages 4–5; structured report on page 6; close-out routing on page 7; appendices (observability-platform screenshots, example templates filled in) as needed.
- **Do not over-write the comms templates.** The report template is 5 fields, not 15. Live-incident writing is faster if the template is spare.

## Acceptance criteria

The runbook is complete when:

- A scope statement is on page 1, naming what this runbook covers and what it routes elsewhere.
- A change-log entry is present with authors, validators, and date.
- Four detection-channel categories (operational, eval-regression, downstream-consumer, vendor-side) each have a specific channel and a specific responder, or an explicit gap marker with owner and date.
- A four-level severity ladder has one-sentence definitions, reach-and-reversibility tests, team-domain examples, and comms cadences.
- An incident-class picker lists all four classes from [Chapter 4](../04-ai-specific-incident-taxonomy-and-triage.md), with one-sentence definitions and team-domain example sentences.
- A contain checklist is ordered, specific, and runnable in 20 minutes; the first bullet is tool-authorisation revocation.
- A trace-preservation checklist names all seven artifacts (prompt, model + version, harness + version, tool authorisations, retrieved context, as-submitted artifact, reviewer's path), each with the specific location on your team's stack or an explicit gap marker.
- A structured-report template has the five required fields and is formatted for copy-paste into your team's channel.
- A close-out routing section names all seven backfeed destinations (per [Chapter 6](../06-regression-fixture-backfeed.md)) with specific paths and owners.
- Validation records exist from the on-call engineer, the SOC lead, and the `ai-risk-engineer` peer (where each exists).
- An incident commander who has never seen the runbook could open it in minute 10 of a hot incident and find the thing they need.
- A rollout date and communication plan are named.

## Stretch goals

- **Tabletop exercise.** Pick a composite incident (e.g., a modified version of the Chapter 5 shell-injection case, or a case from the AIID adjacent to your team's domain). Run the runbook against it with the on-call engineer and one or two senior ICs; measure elapsed time to complete each step. The exercise surfaces specific friction in the runbook before a real incident does. Record findings and amend.
- **Wire the observability platform into the trace-preservation checklist.** If your team uses LangSmith / Weave / Arize, add the specific URLs and the specific "capture-and-archive" buttons/commands to the checklist. The checklist should be clickable, not conceptual.
- **Compose with [Exercise 04](exercise-04-routing-contract-with-risk-engineer-and-secops.md).** Once the routing contract is authored, cross-reference the trigger lines in the runbook's structured-report template so that triggers flag reliably to the specialist peers.
- **Author a candidate-facing version.** For incidents that engage partner teams or external parties, produce a one-page sanitised version of the report template that is safe to share outside the organisation. The version does not include preserved traces or specialist-engineering detail; it names what happened, what was done, and what is being changed.
- **Pre-fill the runbook for one historical near-miss.** Walk the most recent AI-related near-miss on your team through the runbook retrospectively. Produce the structured report as if the runbook had been live at the time. Surfaces gaps; calibrates the severity ladder.
- **Compose with the quarterly retrospective.** The runbook's close-out routing should name the specific quarterly retrospective where its backfeed outcomes are reported ([Chapter 7](../07-team-scope-retrospective-and-ownership-boundary.md)). The retrospective cadence should land on the [`mod-112`](../../mod-112-cross-functional-leadership-and-ritual-calendar/) ritual calendar.
