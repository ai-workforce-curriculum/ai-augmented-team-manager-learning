# Chapter 6 — Adoption Artifacts: Roadmap One-Pager, Pilot Charter, Decision Log, Exec Pre-Read

> *"If you cannot write it on one page, you have not thought through it. If you can, you have."*

## Motivation

The roadmap is the deliverable. The artifacts are how the roadmap travels. Four artifacts, in increasing formality, carry a team-level AI-adoption programme through its first two quarters: the **roadmap one-pager**, the **pilot charter** per pilot in flight, the **rollout decision log**, and the **"why this and not that" exec pre-read note**. Every one of them is short on purpose. Every one of them has to survive an exec read.

This chapter sets the shape and writing discipline for each artifact. Exercise 06 is where you author the full set for your team. The upstream chapters (1–5) are the content; this chapter is the form.

## Core concepts

### Why four artifacts, not one

A single document trying to be the roadmap, the pilot charter, the decision log, and the exec pre-read ends up being none of them. Each artifact has a different audience, a different cadence, and a different half-life:

| Artifact | Audience | Cadence | Half-life |
|---|---|---|---|
| Roadmap one-pager | Team + leadership | Refreshed quarterly; edited on each roadmap-level decision | 3 months |
| Pilot charter | Pilot cohort + manager + partner functions | Written before pilot starts; closed on promote/kill call | 2–6 weeks |
| Rollout decision log | You (primary); auditable | Appended continuously | Permanent |
| Exec pre-read | Leadership | Quarterly, before the exec review | 1 quarter |

The roadmap body is where the *current plan* lives. The charter is where a *single pilot* commits to its own kill switch. The decision log is the *audit trail*. The pre-read is the *conversation starter* with leadership. Separate artifacts, cross-linked.

### Artifact 1 — The roadmap one-pager

The seven sections from Chapter 1, in one legible page:

1. **Scope.** Team name, size, discipline, horizon, named owner (you).
2. **Task sort.** The output of Chapter 2 — AI-first, AI-assisted, human-led, pilot-candidate — one-sentence rationale per row. Dated.
3. **Sequence.** The ordered list of pilots and rollouts across the horizon with named owners, review partners, start/end dates. Chapter 3's method.
4. **Adoption mode per step.** Opt-in / opt-out / mandate per step. Chapter 3's four questions should have resolved each.
5. **Success and kill criteria.** The handful of metrics per step; the pre-committed kill triggers. Measurement depth lives in [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/).
6. **Partner coupling.** Short paragraph per partner function (Platform, DevEx, Product, Security / `ai-risk-engineer`, enablement lead). Chapter 5's view.
7. **Decision log stub.** Pointer to the full log; last 3–5 decisions quoted inline.

Writing discipline:
- **One page in a readable monospace or 10–11pt sans at team-doc default width.** If it does not fit, something is a supporting doc, not the body.
- **No marketing adjectives.** "Innovative" / "transformative" / "cutting-edge" are a tell. Keep the voice flat.
- **Named owners everywhere.** "The team" is not an owner; "Platform" is not an owner; `@name` or role-slug is.
- **Dated everything.** Every decision in the log, every start/end, every revision in the version line at the bottom.
- **One version per roadmap, not per section.** v0.1, v0.2, etc. Track version on the artifact, not inside it.

The one-pager is pinned in the team wiki and dropped into the team's planning space and the exec share-point. One source of truth; all other pointers link to it.

### Artifact 2 — The pilot charter

The seven fields from Chapter 3's pilot-charter spec:

1. **Task and workflow.** Task family (from Chapter 2's sort); specific workflow (repo, tool, prompt pattern, review step).
2. **Cohort.** Named ICs (2–5, representative, opt-in).
3. **Horizon.** 2–6 weeks.
4. **Success criteria.** Pre-committed, measurable, same metrics you intend to use at rollout scale. See [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) for measurement depth.
5. **Kill criteria.** Pre-committed. What causes stop-and-not-promote.
6. **Decision owner and decision date.** You; a specific date on which the promote-or-kill call is made and recorded in the decision log.
7. **Data collection plan.** How, who, where.

Writing discipline:
- **Written before the pilot starts.** A charter authored after the pilot runs is a retcon; it does not count.
- **Half a page, max one page.** If it is longer, it is not a charter, it is a design doc.
- **Shared with the pilot cohort and the partner functions before start.** Partners should see the kill criteria before they fund the measurement.
- **Closed, not deleted.** Each closed charter is appended to the decision log with the outcome, the data, and one-line hindsight note.

The charter's usefulness is in *writing it*, not in *reading it later*. Managers who skip the charter and go straight to "let's try this" are the ones whose roadmaps drift.

### Artifact 3 — The rollout decision log

One file. Append-only. Each entry three to six lines. Fields per entry:

- **Date** (ISO-format; YYYY-MM-DD).
- **Decision owner** (you, almost always; occasionally a named IC or partner).
- **Decision in one line.** "Promote PR-description workflow to opt-out, team-wide." "Kill SQL-skeleton pilot — reviewer bandwidth."
- **Why in one-to-three lines.** The evidence, the trade-off, the context the model could not see.
- **Alternatives considered in one line.** What you did not pick. (The pre-read uses this.)
- **Next review** (optional). The date on which the decision is up for revision.

Writing discipline:
- **Decisions, not activities.** Running a pilot is not a log entry; deciding whether to run it, or to promote it, is.
- **Append-only, dated.** Edits are new entries, not rewrites; a corrected decision is a new entry superseding the old one, with a pointer.
- **Legible to a VP.** The log is the audit trail that lets the roadmap survive leadership change.
- **Short per entry.** Three to six lines. Longer entries get their own named doc and are referenced from the log.

The decision log, over a year, is the quietest but most useful artifact. It shows how the team's AI posture matured — which is what a Q4 performance review, a hiring loop, and a VP's "tell me the story" all need.

### Artifact 4 — The exec pre-read ("why this and not that")

One page, plus pointers. Audience: your VP, skip-level, or the first-cross-functional-leader cell you will present the roadmap to. Written in the *voice of the question they will ask*, not in the voice of your plan.

Section shape:

1. **One-sentence summary of the plan.** "This quarter we move four engineering workflows onto AI-first paths, pilot two more, and hand one workflow to Platform."
2. **Industry context.** One short paragraph using the Chapter 4 discipline — surveys as ranges, honest about where we agree with the baseline and where we diverge.
3. **Risk framing.** Blast radius per step (Chapter 2's scores); kill criteria per pilot (Chapter 3); the human-led bucket that we are *not* automating and why.
4. **ROI framing.** One paragraph. Team-level, [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/)-flavoured; honest about the measurement maturity this quarter.
5. **Why this and not that.** The alternatives you considered and did not pick. Two or three lines each: what, why not, what would change our mind. **This is the section that earns exec trust.**
6. **Partner couplings in one paragraph.** From Chapter 5.
7. **What we are asking for.** Resource, coverage, signal, or decision from the leader reading it. A pre-read with no ask is a status update, not a pre-read.

Writing discipline:
- **One page.** Pointers to the roadmap, charters, decision log, and measurement dashboard for depth.
- **Written in their vocabulary.** If the VP uses "throughput" rather than "velocity," match the vocabulary. If the VP asks every quarter about "cost," lead with cost framing.
- **No surprises from above you.** If something above you has already made a decision (procurement envelope, mandated tool, security policy), name it; do not re-litigate it in the pre-read.
- **Falsifiable commitments only.** "We expect X by week 6" is useful. "We will transform the team" is not.

The "why this and not that" section is the differentiator. A plan that cannot name its alternatives is a plan that has not been thought through — and leadership can usually smell it.

### The cross-link map

Each artifact points to the others. In order:

- **Roadmap one-pager** points to pilot charters (per in-flight pilot), decision log (for history), exec pre-read (for leadership framing), human/machine contract (for C1 consistency, see [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) Chapter 3), measurement dashboard ([`mod-104`](../mod-104-productivity-measurement-and-ai-roi/)), and relevant modules ([`mod-103`](../mod-103-review-standards-and-eval-commissioning/) for eval commissioning, [`mod-105`](../mod-105-team-ai-enablement-programs/) for enablement, [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) for workflow depth, [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) for incident flow, [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) for governance, [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) for vendor/budget).
- **Pilot charter** points to the roadmap step it serves, the measurement dashboard, the decision log entry where the promote-or-kill call is recorded.
- **Decision log** points back to the roadmap step and to the closed charter (if the decision closed a pilot).
- **Exec pre-read** points to the roadmap one-pager (the "read this next" link) and to the measurement dashboard.

Cross-linking is not cosmetic. It is the mechanism by which a leader (or a future-you reading this a year later) can traverse from "what did we decide?" to "why did we decide that?" to "what evidence did we have?" in under three minutes.

### Version control and refresh

- **Roadmap one-pager** version bumped on any change to task sort, sequencing, adoption mode, or success/kill criteria. Minor bumps for partner-coupling edits and decision-log pointer updates.
- **Pilot charter** versioned v0.1 at write; the only legitimate v0.2 is a scope correction before the pilot starts. In-flight charter changes are a sign the pilot should be re-chartered.
- **Decision log** is append-only; no versioning.
- **Exec pre-read** is versioned per quarter (q1-2027, q2-2027, …) and archived.

The refresh cadence: roadmap every quarter minimum (and on any roadmap-level decision); pre-read before each quarterly exec review; charters on pilot start and close; decision log continuously.

### The failure modes to notice in yourself

Three writing failure modes to watch for:

1. **Marketing voice.** "Transforming our team's velocity." If you catch yourself writing this, stop and rewrite in a flat voice. Leadership trusts flat.
2. **Hedging.** "We may consider piloting" / "could potentially" / "aim to explore." The pre-read is a commitment document; the roadmap is a commitment document. Hedging is for the decision log, not the forward-facing artifacts.
3. **Drift between contract and roadmap.** If the C1 bucket in the human/machine contract says a task is *AI may not draft*, but the roadmap routes it as *AI-first*, you have a drift. The roadmap is wrong, or the contract is wrong — fix one before shipping either.

The honest voice, named owners, dated decisions, and tight page count are the writing discipline that makes these artifacts legible to a team, a VP, and a future auditor at the same time.

## Example: a sketched "why this and not that" paragraph

Illustrative of the voice and the shape, not a template to adopt:

> **Why we are *not* mandating this quarter.** Considered — WTI and Octoverse both show mandate-heavy adoption programmes landing at other orgs this cycle. Not chosen because our team is three months into a re-org, mandate-mode change-management budget is low, and opt-out at scale is the honest rollout mode we can execute without reviewer burnout. We revisit in Q2; the trigger is "adoption > 70% under opt-out *and* reviewer-survey quality bar holds."
>
> **Why we are *not* graduating the eval-authoring pilot to Platform this quarter.** Considered — Platform has capacity. Not chosen because we do not yet have a second team asking for the same pattern, and the pilot cell on *verifiability* (Chapter 2 rubric) came in at 3/5 — we want to tune the review bar at team scope first. Platform hand-off re-scored in Q2.
>
> **Why we are *not* using tool X.** Considered — the vendor pitched it in August. Not chosen because our C5 data-handling boundary (see [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) Chapter 3) rules out personal-tier tooling, and the enterprise-tier contract is unapproved. Revisit if the enterprise-tier contract lands.

Three short paragraphs, one per alternative, in the voice of the question leadership will ask. The pre-read's job is done.

## Summary

- Four artifacts carry the team AI-adoption programme: the roadmap one-pager (plan), the pilot charter (per-pilot commitment), the rollout decision log (audit trail), and the exec pre-read (leadership conversation).
- Each is short on purpose. Roadmap one page. Charter half to one page. Decision log entries three to six lines. Pre-read one page. If an artifact grows, split it; do not let it bloat.
- Named owners, dated decisions, falsifiable commitments, flat voice, cross-linked artifacts. These are the writing disciplines that make the set legible to the team, to leadership, and to a future-you reading it a year later.
- The "why this and not that" section of the pre-read is the differentiator — the alternatives you did not pick, with the reason. A plan that cannot name its alternatives is a plan that has not been thought through.
- Watch for drift between the roadmap's task sort and the C1 bucket in the human/machine contract ([`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) Chapter 3). If they disagree, fix one before shipping the other.
- Cadence: roadmap refreshed quarterly and on any roadmap-level decision; charters on pilot start and close; decision log appended continuously; pre-read before each quarterly exec review.
