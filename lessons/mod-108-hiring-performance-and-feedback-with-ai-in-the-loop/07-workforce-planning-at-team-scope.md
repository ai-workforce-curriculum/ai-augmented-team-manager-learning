# Chapter 7 — Workforce Planning at Team Scope: Headcount, Levelling, and Role-Mix Under AI Augmentation

> *The headcount request you write this cycle has to answer a question your previous requests did not — "why does the team need another human when productivity is up 25% and AI tooling spend is up 60%?" The answer is not a defensive argument. It is a clear workforce-planning narrative that names the role-mix shift the team needs, the capability gap the new hire closes, and the reason that gap is a human-shaped gap rather than a tooling-shaped gap. This chapter writes that narrative.*

## Motivation

Requirement R9 (AI-era workforce planning, hiring, and levelling) is kept at team scope specifically for this chapter. R9 at cross-team and org-wide scope belongs to [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) (level 45) and [`ai-engineering-manager`](https://github.com/ai-engineering-curriculum/ai-engineering-manager-learning) (level 50). The team-manager-sized slice is: the headcount request for the team's next hire, the levelling-rationale note the manager carries to calibration, the role-mix observation that routes upward, and the handoff artifact that gives the L45 / L50 owner the inputs they need.

Exercise 06 produces the headcount justification exec pre-read — a one-pager (two at most) the manager writes for the exec stakeholder who signs off on the hire. The chapter covers what goes in it, what is conspicuously out of scope, and when the manager's workforce-planning observation is signal they themselves should act on and when it is signal to pass up a level.

## Core concepts

### What a 2026 headcount request has to answer

A pre-AI headcount request answered three questions: what work needs to get done, why can't the current team do it, and what role and level does the new hire need to be. All three are still in scope. Under AI augmentation, four more questions compose:

- **What has AI leverage done to the team's capacity?** The dashboards from [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) say something specific here. The request has to acknowledge the AI-driven capacity increase and then name why that increase does not close the gap this hire is addressing. "We're up 25% on PR throughput and still can't ship the migration" is a *specific* claim that requires a *specific* explanation — the migration work is outside-frontier, the throughput increase is on in-frontier work, the two are not substitutable.
- **What AI tooling spend is the team already carrying, and what does this hire's AI spend look like?** Headcount cost has an AI-tooling component now. A new senior IC costs base + benefits + (say) $X/month in AI seats + Y% of the team's token budget. The spend is small relative to total compensation but is non-trivial and visible to finance stakeholders. Not naming it reads as either not knowing or hiding.
- **Why is this specifically a human-shaped gap?** The strongest challenge to a 2026 headcount request is "can AI tooling close this instead?" The request has to answer that specifically. Judgement-shaped gaps (the ladder's Axis A at the senior level) are human-shaped. Mentorship-shaped gaps (Axis B) are human-shaped. Outside-frontier task shapes (Dell'Acqua) are often human-shaped. Toil-shaped gaps are tooling-shaped and should be solved there first.
- **What is the role-mix shift the hire represents?** A team that is hiring a third senior IC while its most recent three hires were junior ICs is signalling something about where the team's gap sits. The request names the mix shift directly rather than letting the exec stakeholder infer it.

### The structure of the exec pre-read

A specific suggested structure for Exercise 06; adapt to your organisation's template.

- **One-line summary.** The role, level, and the specific capability gap the hire closes. *"Hire a senior engineer with a system-X background to close the judgement-and-ownership gap on the migration workstream."*
- **Paragraph 1 — the capability gap.** What work the team needs to do that the current team cannot. Specifically the parts that AI leverage has not closed and will not close in the planning horizon. Reference the mod-104 dashboards for what the team has already gained from leverage; name what the dashboards do not show that the hire addresses.
- **Paragraph 2 — the role-mix shift.** Where the team sits today (counts by level), what the mix is becoming after this hire (counts by level), what the mix is supposed to become by end of fiscal year (counts by level if the plan continues on trajectory). Named explicitly so the exec sees the direction.
- **Paragraph 3 — why human, not tooling.** The specific reason this gap is not closable by better AI tooling, more seats, or an enablement bootcamp. Grounded in the ladder axes where applicable — "the gap is at Axis A at the senior tier; this is a judgement-and-mentorship role, not a throughput role."
- **Paragraph 4 — cost framing.** Base + benefits (per HR's standard), plus AI tooling spend attributable to this hire, plus the enablement ramp cost (mod-105 Day 0–90 pairing time). Names the whole-cost so the exec is not surprised later.
- **Paragraph 5 — alternatives considered.** What else was considered. "A contractor for the migration slice specifically" — rejected because the gap is judgement-and-ownership, not just capacity. "Reducing scope" — explain. "More tooling spend" — explain. The paragraph pre-empts the exec's "did you consider X?" question.
- **Paragraph 6 — upward handoff, if applicable.** If the role or the mix shift exceeds team-manager scope — e.g., the hire is at the manager's own level or above, or the mix shift implies a cross-team reorganisation — name the upward handoff explicitly. L45 / L50 / exec own the cross-team question; the manager's note is the input.
- **Appendix — the levelling rationale.** For a mid / senior / staff hire, the levelling rationale is a half-page that names the ladder axes the hire is being levelled against (composing with [`mod-107` Chapter 6](../mod-107-skill-growth-anti-atrophy-and-career-development/06-career-ladder-under-ai-augmentation.md)) and the specific signal the interview loop (Chapter 2) will read for.

The pre-read is two pages, max. An exec will read two pages; an exec will not read ten. The appendix is for the levelling calibration, not for the headcount decision itself.

### The role-mix shift — when it is team-scope, when it routes up

Three role-mix observations the team manager is likely to have under AI augmentation:

- **"We have too many junior ICs relative to the mentorship capacity on the team."** This is a team-scope observation. The intervention is either to hold junior hiring and hire mid / senior next (team-scope, the manager's call with HR) or to add senior-IC mentorship bandwidth through specific pairings (team-scope, the manager's work). If the ratio is extreme (e.g., ratio of juniors to seniors above 3:1 consistently), the observation is also signal to pass to the L45 owner that the organisation's role-mix policy may need to shift.
- **"The team's work mix has shifted — outside-frontier work has grown relative to in-frontier work."** This is partly team-scope (routing matrix updates per mod-106; mentorship ramp) and partly cross-team. If the organisation's AI roadmap is pushing more outside-frontier work to the team, the team-scope answer is a senior / staff hire; the cross-team answer is a scope conversation with the team's exec stakeholder.
- **"The role categories themselves are shifting — we need less 'engineer' and more 'engineer with product judgement,' or we need a new role like 'agent operations engineer.'"** This is almost always a cross-team observation. The L45 track owns role-architecture; the team manager's job is to feed the signal and operate the current categories. Attempting to redefine the role at team scope creates calibration problems across teams.

The rule: if the mix-shift observation would change the *role definitions* the organisation uses, route up. If it changes *which levels and counts* the team is filling, stay at team scope.

### The levelling rationale appendix

The appendix exists so the hiring decision is calibrated when the offer is written. It names:

- The ladder-axis signal the interview loop was designed to read for (composing with Chapter 2's loop redesign).
- The specific level-descriptor amendments from [`mod-107` Chapter 6](../mod-107-skill-growth-anti-atrophy-and-career-development/06-career-ladder-under-ai-augmentation.md) the hire is expected to hit within 6–12 months.
- The ramp plan (mod-105 Day 0–90), with specific Axis-A / B / C milestones the new hire is expected to demonstrate.
- Any level-boundary ambiguity resolved in advance. If the hire is being offered at senior and the interview surfaced staff-level moments, the appendix names *why* the offer is at senior and what the staff-promotion criteria would require.

The rationale appendix prevents a common failure: the hire comes in at senior-level compensation, operates at mid-level for two quarters because the ramp plan didn't account for the team's outside-frontier work mix, and the IC concludes the level is wrong. The appendix names the bar in advance and gives both parties an anchored conversation.

### The AI-cost side of headcount

A note that catches finance stakeholders' attention when it is missing. A 2026 engineering headcount's fully-loaded cost typically includes:

- Base + benefits (the organisation's standard load).
- AI seat / tool spend. Conservative estimate per IC in a well-tooled engineering team: tens to low hundreds of USD per month for the core coding-agent subscription, plus organisation-shared infrastructure (eval, observability, data). The number is organisation-specific; the manager cites the org's actual per-head AI-tooling budget.
- Token / inference spend. For teams running agent-heavy workflows, per-head monthly token spend can add further dollars per IC per month at sustained usage. The manager's mod-104 cost dashboard is the reference.
- Enablement cost. The mod-105 Day 0 / 30 / 60 / 90 ramp pulls senior-IC time on the team as pair time; even if un-costed, it is a real capacity hit.

The pre-read names these line items. The specific numbers are from the organisation's actual data; this chapter does not propose benchmarks because team-level AI costs are organisation-specific and benchmarking against external claims is hazardous. The point is: the exec sees the whole-cost picture, not just the compensation component.

### The upward scope handoff

Three specific questions that are team-manager-adjacent but route up:

- **Role architecture.** New roles (e.g., "agent operations engineer," "AI enablement engineer within a team," "evaluation specialist on a specific product"). The L45 / L50 owner authors role categories; the team manager's observation feeds in.
- **Cross-team workforce planning.** Rebalancing headcount between teams, moving ICs between teams, consolidating duplicate roles across teams — all cross-team scope. The team manager's role is to flag, document, and stay in their lane.
- **Organisational-level levelling architecture.** Adding or removing ladder levels, changing level-descriptors company-wide, shifting the comp-band structure — org-scope work. The team manager's ladder refresh from Chapter 3 is a team-scope artifact that composes with the org ladder; wholesale changes to the org ladder are upstream.

The handoff artifact is a short note — one paragraph — the manager writes to the L45 / L50 owner that names the observation, the team-scope signal, and the specific upward question. The note is the input; the L45 / L50 owner's response may be "handle at team scope" or "I'll bring this to the next level-wide calibration." Either response gives the manager a boundary; working without the upward conversation produces team-scope decisions that implicitly set org-scope precedents.

### What *not* to do

- **Do not argue headcount by invoking AI tooling against yourself.** A headcount request that reads "AI has made us X% more productive but we still need more people" without naming the specific gap reads as a request for more without a reason. Name the gap.
- **Do not inflate levelling to attract the candidate.** A senior-level offer to someone who interviewed at mid is tempting in a competitive market. The ladder has a bar; running around it creates calibration problems on the team that outlast the hire.
- **Do not request headcount without confirming the tooling / enablement baseline.** If the team is understaffed on seats or if the bootcamp hasn't been run in two cycles, the "need more capacity" argument is confounded with the "need better enablement" argument. Close the tooling / enablement gap first; the headcount case is cleaner after.
- **Do not treat the exec pre-read as an internal artifact.** The pre-read is written for the exec stakeholder and will be used in the sign-off conversation. Write it with the exec's time and attention in mind.
- **Do not route role-architecture changes as team-scope headcount requests.** A request for "a new kind of role we haven't had before" is a role-architecture conversation, not a headcount conversation. Open the architecture conversation first with the L45 / L50 owner; the headcount request follows.
- **Do not submit a headcount request without the levelling-rationale appendix.** Offers written without the appendix tend to be miscalibrated, and the miscalibration is the single biggest driver of early-tenure dissatisfaction for senior-IC hires.

### Common failure modes

- **The pre-read reads defensive.** Managers under budget pressure over-explain and the exec reads anxiety instead of plan. Confident, specific, short.
- **The AI-cost section is absent.** Finance notices. The sign-off conversation gets stuck on "what's the all-in cost here?" when the pre-read could have answered it.
- **The levelling rationale is generic.** "Senior because they have 8 years of experience." Not sufficient under the ladder refresh from Chapter 3. Cite the ladder axes and the specific interview signal.
- **The mix-shift narrative is implicit.** The exec infers "another senior" rather than "the team is shifting from a flat junior-heavy mix to a stratified mix because the work is stratifying." Name the shift.
- **The upward handoff is skipped.** Observation that should have gone to L45 / L50 gets implemented at team scope and creates a precedent the organisation didn't intend. Pass the signal; let the level above decide the scope.
- **The pre-read is written once per year and never updated.** Headcount requests are cycle-aligned. The template is drafted once; each request re-authors the specifics. A pre-read that reads the same for every hire is one nobody is reading.

## Example: a senior-IC headcount request, pre-read

Composite example; calibration, not a template. Elide the organisation-specific numbers.

> **One-line summary.** Hire a senior engineer with migration-planning experience to close the judgement-and-ownership gap on the Service-X migration workstream.
>
> **Capability gap.** The team completed its in-frontier throughput work on schedule this half — PR throughput up [N%], review latency down [M%] — but the Service-X migration specifically requires sustained outside-frontier judgement work the team has not been producing at the rate the scope demands. The specific gap is Axis-A (judgement under AI augmentation) at the senior tier; two mid-level ICs on the migration have done well on paired reviews but the migration needs an IC who can own the design decisions end-to-end and mentor the junior ICs through the outside-frontier parts. The mod-104 dashboards reflect the in-frontier gain; the gap is in the part of the work the dashboards do not measure.
>
> **Role-mix shift.** Current mix: [N] juniors, [N] mid, [N] senior, [N] staff. After hire: [+1] senior. By end of FY on current trajectory: [plan]. The mix shift is toward stratification — AI leverage is compressing the output difference between junior and mid on in-frontier work, which argues for fewer new juniors next cycle and more senior-tier hires until the mentorship ratio recovers.
>
> **Why human, not tooling.** The migration's judgement calls — which services to migrate in which order, which risk the rollback plan accepts, which stakeholders to brief before which cutovers — are outside the AI's capability frontier on our stack as evaluated in [mod-103 eval work / mod-106 routing matrix]. Additional AI tooling would reduce toil in the migration *execution*; it would not close the *judgement-and-ownership* gap, which is the bottleneck.
>
> **Cost.** Base + benefits per the HR comp band for senior-tier in [geography]. AI tooling spend attributable to one IC: [$X/month] seat + [est $Y/month] token budget per the mod-104 cost dashboard. Enablement ramp: ~40 hours of senior-IC pair time over Day 0–90 per mod-105.
>
> **Alternatives considered.** Contractor for the migration slice: rejected — the migration is a 12+ month commitment and ownership-shaped; a contractor handoff would be worse than the gap. Scope reduction: possible on the non-critical services, saves ~[N weeks] but does not address the ownership-shaped work. More tooling: already running the budget for the team's current needs; additional tooling spend would be marginal relative to the gap.
>
> **Upward handoff.** None — the request is team-scope. The underlying trend (shift toward senior-tier hiring) is being flagged separately to [L45 owner / exec sponsor] as team-level signal for the broader role-mix conversation.
>
> **Appendix — levelling rationale.** The senior-tier offer is calibrated against the mod-107 Chapter 6 ladder axes A/B/C. The interview loop (Chapter 2) is designed to produce signal on Axis A via the design round's AI-off sub-stage, on Axis B via the behavioural "walk us through a time you mentored someone through a decision" prompt, on Axis C via the pair-coding round's narration criterion. Expected Day-90 milestones: one documented judgement-move artefact, one paired-review rotation with [junior IC], one review-standard amendment proposed.

The pre-read fits on two pages at the organisation's standard formatting. The exec reads it; the sign-off conversation addresses specific questions ("why is the token-spend estimate that high?", "does the L45 conversation change anything?") rather than re-litigating whether the hire is justified.

## Summary

- **R9 at team scope** = headcount justification, levelling rationale, role-mix shift observation for the manager's own team; R9 at cross-team / org scope goes to [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) (L45) or [`ai-engineering-manager`](https://github.com/ai-engineering-curriculum/ai-engineering-manager-learning) (L50).
- **A 2026 headcount request answers seven questions:** what work, why can't the current team do it, what role / level — *plus* what has AI leverage done to capacity, what AI-tooling cost comes with the hire, why human not tooling, what's the role-mix shift.
- **The exec pre-read is two pages max** with a specific structure: one-line summary, capability gap, role-mix shift, why human not tooling, cost (including AI), alternatives considered, upward handoff, levelling-rationale appendix.
- **Role-mix observations route up when they would change role definitions**; they stay at team scope when they change levels and counts within existing roles.
- **The levelling rationale appendix** composes with [`mod-107` Chapter 6's ladder](../mod-107-skill-growth-anti-atrophy-and-career-development/06-career-ladder-under-ai-augmentation.md) and Chapter 2's interview loop so the offer is calibrated when it is written.
- **AI cost is an explicit line item** in the pre-read — seat / token / enablement — read against the [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) cost dashboard; not naming it reads as hiding.
- **Upward handoff** is a one-paragraph note to the L45 / L50 owner; it is signal, not a decision request.
- **What not to do:** argue headcount by invoking AI tooling against yourself, inflate levelling to close a candidate, submit without the levelling-rationale appendix, route role-architecture changes as headcount, skip the upward handoff.
- **Composes with** [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) (cost dashboard), [`mod-105`](../mod-105-team-ai-enablement-programs/) (ramp plan), [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) (routing / frontier observation), [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/) (ladder), [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) (tooling budget).
