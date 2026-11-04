# Chapter 3 — Pilot vs. Rollout, Opt-In vs. Mandate, and the Change-Management Story

> *"A pilot you cannot kill is not a pilot. A mandate you cannot explain is not a mandate."*

## Motivation

Two sequencing decisions dominate the middle of the roadmap. First: **pilot vs. rollout** — which AI-targeted task families start as a scoped pilot with 2–5 ICs and clear kill criteria, and which can jump straight to a team-wide rollout. Second: **opt-in vs. mandate** — which uses are available to any IC who wants them, which are the default (opt-out), and which are required of everyone.

Both decisions sound administrative. They are not. The pilot/rollout choice determines whether you *learn* before you *commit*. The opt-in/mandate choice determines whether the team *keeps its agency* or gets *pushed*. Get either wrong at team scope and you spend the quarter unpicking it. This chapter names the choices, the criteria, and the change-management story that must sit under both.

The downstream artifact — the pilot charter, the rollout decision log, and the "why this and not that" exec note — lands in Chapter 6. This chapter is the method.

## Core concepts

### Why pilot at all

Three reasons, in roughly this order of weight:

1. **The task's frontier status is uncertain.** Chapter 2's sort put a task in the *pilot candidate* bucket because the six-dimension rubric did not resolve it. The pilot's job is to resolve it with real evidence from your team.
2. **The workflow cost is unknown.** Even an "inside-the-frontier" task may be net-negative on your team if the review bar, the tool-setup cost, or the reviewer bandwidth kills the gain. Running a scoped pilot measures the full-workflow cost, not just the capability cost.
3. **The change-management risk is real.** A rollout you cannot roll back is a rollout you cannot honestly try. A pilot is how you earn the right to roll out, by showing the team (and leadership) you knew what the kill criteria looked like before you ran.

Pilots that do not meet all three bars tend to become "mini-rollouts in disguise" — they do not generate evidence, they do not get killed when they should, and they do not build political permission for the real rollout.

### The pilot charter — what a pilot must have before it starts

Write the charter *before* the pilot runs. One page, pinned next to the roadmap. Required fields:

1. **The task and the workflow.** The task family from Chapter 2's sort. The specific workflow — repo, tool, prompt pattern, review step — you are piloting.
2. **The pilot cohort.** Named ICs (2–5, representative, opt-in). Not a self-selected enthusiast club, not a draft from across the whole team.
3. **The horizon.** Short — 2–6 weeks is the usual team-scope span. Longer than 8 weeks and it is no longer a pilot.
4. **The success criteria.** A handful of pre-committed, measurable thresholds: adoption rate, time delta, reviewer-reported quality bar, cost. These should be the same metrics you intend to measure at rollout scale, not a separate pilot-only set.
5. **The kill criteria.** What causes you to stop the pilot and not promote it: a sustained quality regression, a reviewer-burnout signal, cost over the seat budget, an incident ([`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/)), or simply "no measurable improvement by end of horizon." If you cannot name the kill criteria, you have not committed to a pilot.
6. **The decision owner and the decision date.** You. A specific date on which the promote-or-kill call is made and logged in the roadmap decision log.
7. **The data collection plan.** How you will measure, who collects, where it lives. [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) covers the measurement depth; the pilot's job is to apply it.

If a pilot ships without those seven fields, it will not produce evidence — it will produce anecdotes.

### When to skip the pilot and go straight to rollout

Pilots have cost: they slow the roadmap and they split the team into haves and have-nots for a few weeks. Skip the pilot and go straight to a team-wide rollout only when all of:

- The task is cleanly inside the frontier per Chapter 2 (score ≥25 with no cell ≤2).
- A peer team or a published case has already piloted the same workflow at similar scale with reported evidence, and your adaptation is modest.
- The tool itself is already in team use for adjacent work, so you are not also absorbing a new-tool adoption cost.
- The blast radius if you are wrong is small — for example, the workflow is behind an opt-out and the artifact class is reversible.

Most team AI-adoption work in a role's first year does *not* clear this bar. Default to pilot. Pilot-skip is a judgment call you should be ready to defend in the exec pre-read (Chapter 6).

### Opt-in, opt-out (default-on), and mandate — the three adoption modes

For every AI-targeted task family, pick one of:

- **Opt-in.** Any IC who wants to use the AI workflow may; nobody is asked to. Appropriate during a pilot, and for tasks where the gain is personal-productivity-flavoured and the review bar is unchanged. Low change-management load; low adoption velocity; preserves agency.
- **Opt-out (default-on).** The AI workflow is the default; ICs can opt out for a stated reason, recorded in the decision log. Appropriate after a successful pilot, for tasks where consistency across the team matters (e.g., PR-description format, AGENTS.md conventions). Medium change-management load; medium adoption velocity; the opt-out column is doing real work — read it monthly.
- **Mandate.** The AI workflow is required; opting out is not a team-scope decision. Appropriate when regulation, policy, or an executive decision has already made the call (e.g., security-mandated review tooling, legally required disclosures). High change-management load; the "why" must come from above you. This is a documentation role for the team manager, not a design role.

The default is **opt-in during pilot, opt-out after a successful pilot, mandate only when the mandate came from somewhere else.** Managers who start with mandate usually have to climb back down to opt-out within a quarter — the climb-back is expensive and visible.

### Choosing between the three

Four questions resolve most decisions:

1. **Is there a legitimate reason an IC should not do this with AI this quarter?** (Context the model cannot see; a specific client constraint; an in-flight incident; a personal-skill protection window per [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/).) If yes, opt-in or opt-out, not mandate.
2. **Does consistency across the team add real value?** (Shared conventions, shared outputs, shared review bar.) If yes, opt-out. If no, opt-in may be enough.
3. **Did someone above you (security, legal, enablement-lead, exec) already say "yes, this is required"?** If yes, mandate — and your job is to translate it, not re-litigate it. If no, do not make it a mandate from your altitude.
4. **Will the review bar hold at full-team scale?** A rollout at opt-out or mandate scale puts pressure on reviewers (see C2 in the human/machine contract). If your reviewer bandwidth cannot carry the load, step back to opt-in or shrink scope.

### Change management for the team — the narrative

The adoption-mode choice is half of the decision. The other half is *how you tell the team about it*. Change-management research (John Kotter's eight-step model is the industry reference; Everett Rogers's *Diffusion of Innovations* explains the shape of adoption across innovators, early adopters, early majority, late majority, laggards) converges on a small number of things that matter at team scope:

- **A stated reason.** Not "AI is the future." Instead: the specific tasks, the specific review bar, the specific metric, the specific horizon. The reason has to be falsifiable — a reason that cannot be wrong is not a reason.
- **A named owner and a decision date.** You. The team needs to know who to come to when the workflow breaks and when the next decision lands.
- **A visible kill switch.** Especially during pilots, especially under opt-out. "This is rolling back if…" is a confidence signal, not a weakness signal.
- **Two-way channels.** A #channel or a standing 10-minute slot where ICs raise frustrations without having to open a formal incident ticket. The silent frustrations are what torpedo adoption.
- **Honest sequencing of hard decisions.** If a task family is going to end up as human-led per Chapter 2, say so early. The team needs to know what is *not* being automated as much as what is.

Change-management writing at team scope is terse. One paragraph in the roadmap one-pager; one paragraph in the pilot charter; a short paragraph in the exec pre-read; a short team-channel note when a decision changes. The volume of change-management prose is inversely proportional to its honesty — long announcements are a smell.

### Change management for leadership — the exec read

Leadership reads the roadmap differently than the team. Two concerns dominate:

- **Risk framing.** What is the blast radius if we are wrong, and what is our stopping rule? Chapter 2's blast-radius score and this chapter's kill criteria answer this directly.
- **ROI framing.** What are we trading for the change-management cost? The pilot's success criteria and [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/)'s ROI narrative answer this.

A one-paragraph "why this and not that" note (template in Chapter 6) satisfies both. It names one or two things you considered but did *not* pick, with the reason. Leadership trusts a roadmap that shows its alternatives more than one that shows only its chosen path.

### Pilots that graduate out of the team

A successful pilot does not always graduate to a team-wide rollout. It sometimes graduates *out* of the team entirely — to Platform / DevEx / `ai-enablement-lead`. Chapter 5 is the method for that hand-off. The relevant signal here: if the pilot succeeds and the task family is not actually team-specific, the right rollout is org-wide, not team-wide. Running an opt-out team-wide rollout on a workflow that should be org-wide burns change-management budget on a boundary mistake.

### Pilots that are actually contract revisions

Sometimes the "pilot" is really a renegotiation of the C1 bucket in the human/machine contract. If the pilot's purpose is to decide whether a task family moves from *human-led* to *AI-assisted*, the real artifact is the contract update, and the roadmap decision log should reference it. Keep the two documents coupled — see Chapter 2 and [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) Chapter 3.

## Example: one quarter of pilot/rollout choices for a 10-engineer team

Illustrative, not prescriptive. For each task family from Chapter 2's example sort:

| Task family | Bucket | Mode decision | Reasoning |
|---|---|---|---|
| PR description drafting | AI-first | Opt-out after week 3 pilot | Capability fit high; consistency across the team adds value in reviews. |
| Unit test skeleton | AI-first | Opt-out after week 3 pilot | Verifiable (tests run); consistency adds value for coverage. |
| ADR first draft | AI-first | Opt-in this quarter | Lower frequency; consistency less important; allow ICs to keep their own voice. |
| SQL against lakehouse | AI-first | Opt-out after week 4 pilot | Verifiability depends on a review step; pilot tests the review bar. |
| Customer-facing error copy | AI-assisted | Opt-in, review-only | Blast radius lower but non-trivial; mandated review by sr IC. |
| On-call runbook edit | AI-assisted | Opt-in, review-only | Low-frequency, context-dense; opt-in avoids forcing the workflow. |
| Migration sequencing plan | Human-led | n/a | Blast radius high, judgment-dense; off the roadmap this quarter. |
| Incident post-mortem | Human-led | n/a | Contract C1 "AI may not draft"; off the roadmap. |
| Employee feedback | Human-led | n/a | Contract C1 "AI may not draft"; off the roadmap. |
| Golden-task eval authoring | Pilot candidate | 4-week pilot with ai-risk-engineer peer | Resolve whether to own in-team or commission ([`mod-103`](../mod-103-review-standards-and-eval-commissioning/)). |

Two pilots run this quarter (PR + SQL combined pilot, eval-authoring pilot). No mandates. Two opt-out rollouts post-pilot. Four opt-ins. Three explicitly human-led. One pilot candidate with a clear decision date at week 4.

Every line is defensible against "why not mandate?" and against "why pilot at all?" because each answer is traceable back to Chapter 2's scored rubric and this chapter's four questions.

## Summary

- Two sequencing decisions dominate the middle of the roadmap: pilot vs. rollout, and the adoption mode (opt-in, opt-out/default-on, mandate).
- A pilot without a pre-committed charter — cohort, horizon, success criteria, **kill criteria**, decision owner and date, data plan — is not a pilot.
- Skip the pilot and go straight to rollout only when the task is cleanly inside the frontier, a comparable case is already published, the tool is in-use, and blast radius is small. Default to pilot.
- The adoption-mode default is: opt-in during pilot, opt-out after a successful pilot, mandate only when the mandate came from above. Manager-origin mandates usually have to be walked back.
- Change-management writing is terse and falsifiable. Give the team a stated reason, a named owner, a kill switch, and two-way channels. Give leadership a risk framing, an ROI framing, and a short "why this and not that" alternative discussion.
- If a pilot succeeds on a non-team-specific workflow, the right rollout is org-wide; hand off per Chapter 5 rather than running a team-wide rollout on infrastructure that should be shared.
