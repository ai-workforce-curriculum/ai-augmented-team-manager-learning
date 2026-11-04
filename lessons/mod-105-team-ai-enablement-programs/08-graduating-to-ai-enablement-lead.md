# Chapter 8 — Knowing When the Programme Graduates to `ai-enablement-lead` (L45)

> *Your mod-105 programme is a one-team programme. The org has (or will have) more than one team. When the programme needs to apply across teams, it is not yours to scale — it is yours to hand off, with a written contract, to the role whose altitude is org-wide enablement.*

## Motivation

R5 is explicit on the handoff: *"know when a program needs to graduate to org-wide ownership at `ai-enablement-lead` (level 45)."* R14 of `JOB_REQUIREMENTS.md` names the same boundary from the other direction — *org-wide AI enablement programmes beyond a single team* are the L45 role's responsibility, not the team-manager's.

Why this chapter exists as a stand-alone concern: in practice, successful team-scope programmes face strong pull to scale. Neighbouring teams see your pattern library, your three fluency artifacts, your stage-shaped budget rubric, and ask "can we run this?" The right answer is almost never "yes, I will scale it for you." The right answer is a *handoff contract* — a written document that transfers programme ownership (or stands up a parallel L45 programme that absorbs the team-scope one) at the correct altitude.

Three reasons to resist the "just scale it" temptation even when the request is flattering:

- **Scaling a team-scope programme is a different job.** Multi-team enablement is org-wide procurement, cross-team pedagogy, enterprise LMS integration, cross-functional influence, and (often) a direct line into HR and People Operations. Those are an L45 job, not an L40 side project. A manager who tries to do both does neither well.
- **Your own team's programme regresses.** The capacity you spent authoring curriculum, scoring artifacts, and running cohort checkpoints is now spread across three teams. The one team that was yours now gets one-third of your enablement attention. Chapter 2's four checkpoints start to slip.
- **The second team deserves its own stage-specific design.** The curriculum you wrote is *your team's workflow*. It is not the neighbouring team's workflow. Running your curriculum on their engineers is Chapter 1's Failure A (one-shot generic workshop) in a slightly different costume.

This chapter sketches the graduation triggers, the handoff contract, the L45 role's altitude, and the specific case where your organisation does not yet have an L45 role to hand off to.

## Core concepts

### The `ai-enablement-lead` (L45) role in one paragraph

[`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) sits at level 45 in the AI Workforce family in this curriculum's ladder. The role owns *org-wide* AI enablement programmes across multiple teams, central tooling procurement at scale, workforce-level AI literacy obligations (EU AI Act Article 4 at org level), multi-team cohort design, and the enablement-portfolio level of the AI investment narrative. It is the role you defer *upward* to when scope exceeds a single team — the same way `head-of-ai-governance` (L60) is the role `mod-110` defers to for regulator-level governance, and `ai-enablement-lead` is itself the role that `mod-105` graduates to for org-wide programmes.

What L45 *does not* own: individual team-shaped curricula. A healthy L45 programme runs an org-wide literacy baseline, provisions tooling at scale, holds the multi-team cohort cadence — and *leaves team-specific curriculum to the team manager*. The two altitudes compose.

### The four graduation triggers

A mod-105 programme is a candidate for graduation when any one of the following trips. Two or more tripping simultaneously makes the graduation urgent.

**Trigger 1 — Scope creep across teams.** The programme is being asked to serve a second team. This can arrive politely ("can we send a few engineers to your bootcamp?") or urgently ("Finance signed off on rolling this out org-wide"). Either way, the moment the programme is being *named* as a multi-team programme, it is at the L45 altitude.

**Trigger 2 — Manager delivery load > 5 hours/week sustained.** Chapter 7 named the ~2–3 hours/week manager delivery budget. Sliding past 5 hours/week sustained — not for a one-week spike during a cohort kickoff — is a signal the programme has outgrown the authoring-plus-modest-delivery envelope. Either the team is larger than the mod-105 shape sustains (try the Chapter 2 overlapping-cohort model first), or the scope has crept (see Trigger 1), or you have absorbed delivery that should have been distributed (renegotiate the Chapter 7 partnership contract).

**Trigger 3 — Formal workforce-level compliance obligations are landing.** EU AI Act Article 4 (deployer AI literacy obligation) at the organisation level, SEC human-capital disclosure requirements with AI workforce language, industry-specific regulator guidance on AI competency — these obligations attach at the *organisation* layer, not the team layer. When your organisation starts holding formal compliance evidence on AI enablement completion, the aggregation layer sits above your altitude. mod-110 covers the team-scope compliance crosswalk; the org-wide aggregation is L45's.

**Trigger 4 — Programme has become enterprise procurement-shaped.** The budget conversations from Chapter 4 start happening at a scale that touches multi-year enterprise contracts, cross-team seat pools, and FinOps negotiation posture. That is `mod-111` in part, but the organisation-wide enablement portfolio that justifies the spend is L45's.

A mod-105 programme that trips none of these can continue indefinitely at team scope. A mod-105 programme that trips two or more and is still being run solo by the team manager is one quarter away from quiet failure.

### The handoff contract

The handoff contract is a one-to-two-page document that transfers programme ownership (or stands up an org-wide programme that absorbs this one). It is the artifact Exercise 05 produces.

The contract's job is to prevent two failure modes:

- *Everything-transfers-and-nothing-lands.* The L45 takes full ownership and the team-specific adaptations evaporate. Six months later, your team is receiving the generic org-wide curriculum (Chapter 1 Failure A). Fix: the contract explicitly preserves the *team-shaped* layer under the L45's org-wide layer.
- *Nothing-transfers-and-everything-drifts.* The L45 "takes the programme" nominally but inherits no actual artifacts, documents, or ownership; six months later, three teams are each running their own ad-hoc version with no coordination. Fix: the contract explicitly transfers specific artifacts, with named receiving owners.

A workable handoff contract contains the following sections:

**1. Context.** One paragraph on *why* the graduation is happening (which of the four triggers tripped, when, with what evidence).

**2. Scope being transferred.** Which artifacts, which populations, which decision rights. For example:

> *Transferred to L45:* multi-team cohort scheduling; the organisation's shared Cursor / Claude Code enterprise contract terms and seat pool; org-wide AI literacy baseline (EU AI Act Article 4 compliance); cross-team pattern library; vendor-trainer master schedule; L45-owned central CoP (if any).
>
> *Retained at team scope (mod-105):* team-specific curriculum; team-specific review standards and the first-successful-PR artifact definition against them; stage-pin conversations with engineers on this team; team-specific graduation decisions.

**3. Interfaces.** Who meets with whom and on what cadence. The L45 and the team manager need a sync; usually monthly, sometimes weekly during a transition quarter.

**4. Artifact inventory.** The literal list of files/docs/records transferring and from where to where. The pattern library at `team/docs/mod-105/patterns/` — does it stay or move? The exec pre-read — does the team manager still author one, or does it fold into an L45-authored org-wide pre-read with a team-scope appendix?

**5. Measurement handoff.** How mod-104's AI-cost ratio tile and mod-105's three fluency-growth artifacts continue to produce evidence through the transition. The failure mode here is that the artifacts stop being scored because nobody knows whose job it is.

**6. Transition period.** A dated period (typically one quarter) during which both parties operate in a dual-run mode before the full handoff lands. The team manager still runs the current cohort through to Day 90; new cohorts start under the L45 framework.

**7. Sunset / revisit.** A date six to twelve months out where the handoff is reviewed. Did it land? Is the team-shaped layer preserved?

**8. Signatures.** Team manager, `ai-enablement-lead` (L45), VP of Engineering (or equivalent) as the altitude-above-both sign-off. HR partner as cc.

### The case where your org does not have an L45 role to graduate to

Many organisations do not yet have an `ai-enablement-lead` role in their ladder. This is common and not your personal problem to solve. Three postures worth knowing:

- **Posture A — name the gap.** In the quarter's exec pre-read, name that the programme is at the graduation threshold and that the organisation does not currently have an L45 role to receive it. This is useful signal for VP-of-Engineering-and-above planning; it may also trigger the organisation to *create* the role or expand an adjacent one.
- **Posture B — propose an interim owner.** The gap can be bridged by an interim owner — a Director of Engineering or a Head of Platform Engineering acting in an L45-adjacent capacity. The handoff contract is still written (see above), with the interim owner named. The "interim" status is noted in writing so the programme does not calcify under a role not designed for it.
- **Posture C — propose role creation evidence.** If the programme is running well and generating demand from other teams, you have evidence for the organisation to invest in the L45 role. Exercise 05 (the handoff contract) can be written *forward-looking* — as the specification for the role before it exists. That is a very different artifact from a "please promote me" request; it is a role-scoping artifact that names the altitude the work needs.

Do not solve the gap by *becoming* the L45 role de facto. Taking on the org-wide programme on top of your L40 role without the role-level authority is unsustainable and creates a precedent future managers inherit.

### What does *not* graduate to L45

A clarification against two common over-reads of the graduation trigger:

- **A larger team does not automatically mean graduation.** A 40-engineer team is still *one team*. Chapter 2's cohort model (5–6 overlapping cohorts of 5 over a half-year) scales up to this size. The trigger is multi-team, not team-size.
- **A high-signal pattern library is not graduation evidence.** If your team has produced an unusually strong pattern library, that is a success of the programme, not a signal it needs to leave your altitude. The right next move is to share it — into the L45 programme if one exists, into a public artifact if your org permits, into the CoP's cross-team visit cadence (Chapter 3).

### How this chapter connects to the rest of the track

The graduation decision is one of the handful of places in the AITM track where the manager's job is to *route work upward*. Other places include:

- `mod-110`: team-scope governance crosswalk rolling up to `head-of-ai-governance` (L60).
- `mod-111`: team-scope vendor selection rolling up to enterprise procurement (often L45 or `ai-enablement-lead`'s portfolio).
- `mod-109`: team-scope incident evidence feeding into the organisation's AI-incident response (SecOps + L60-adjacent governance).

Routing upward is a competence, not an abdication. A manager who holds everything at their altitude without ever routing upward is doing more than one job and (eventually) less than one job well.

### What this chapter is *not*

- **Not a promotion-to-L45 pitch.** The graduation contract is the artifact; the artifact is for the programme, not for your career. If your work on the programme is itself evidence for a promotion conversation with your own manager, that is downstream of the contract, not the contract's purpose.
- **Not an exhaustive L45 role spec.** For the full role specification, see [`ai-enablement-lead-learning`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning). The L45 track owns the detail of what the role does; this chapter owns the handoff interface from L40.
- **Not a reason to delay the team-scope programme.** "We should wait until we have an L45" is the wrong conclusion from this chapter. The team-scope programme runs regardless; the graduation is the exit gate when it is reached, not a prerequisite for starting.

## Example: a handoff contract outline

Treat as calibration, not a template.

> **Programme:** Team-scope AI enablement — Platform Infra team (currently 18 engineers).
> **Date:** 2026-04-01 (Q2 kickoff).
> **Graduation trigger:** Triggers 1 and 3 — the Developer Experience team and the Data Platform team have both requested to join the cohort structure (Trigger 1), and the organisation's Q2 compliance roadmap formally names EU AI Act Article 4 literacy as an org-wide baseline (Trigger 3). Manager delivery load projection crosses 5 hrs/week in Q2 if both teams join.
>
> **Transferred to L45 (newly-filled role as of 2026-03-15):**
> - Multi-team cohort scheduling and intake across Platform Infra, Developer Experience, and Data Platform (34 engineers combined).
> - Shared Cursor + Claude Code enterprise contract management.
> - EU AI Act Article 4 org-wide literacy baseline (defers to mod-110 team-scope crosswalk for team evidence).
> - Cross-team pattern library (new artifact; absorbs Platform Infra's existing library + stands up equivalents for the other two teams).
> - Vendor-trainer master schedule.
>
> **Retained at team scope (mod-105):**
> - Platform Infra-specific curriculum content; review standards from mod-103; stage-pin rubric specific to this team's primary tools.
> - Day-0 / 30 / 60 / 90 checkpoints with Platform Infra engineers.
> - First-successful-PR artifact against *this team's* review standard.
>
> **Interfaces:** Weekly 30-min sync between team manager and L45 during Q2 (transition quarter); monthly 30-min sync thereafter. Quarterly tri-manager sync across Platform Infra, Dev Experience, Data Platform.
>
> **Transition period:** Q2 2026 is dual-run. Current Platform Infra Cohort C runs to Day 90 under this contract's current terms. New cohorts starting Q3 run under the L45 framework with Platform Infra-specific curriculum appended.
>
> **Measurement handoff:** mod-104 AI-cost ratio tile continues at team scope; L45 adds a cross-team roll-up tile for the enablement portfolio narrative. Three fluency-growth artifacts remain team-authored and team-scored; aggregate metrics reported quarterly into the L45 portfolio view.
>
> **Sunset/revisit:** 2026-10-01. Review: did the team-shaped layer land? Did any artifacts regress? What did we get wrong?
>
> **Signatures:** [team manager], [L45], [VP Engineering]. HR partner cc'd.

One page, specific, auditable, preserves the team-shaped layer under the org-wide roll-up.

## Summary

- `ai-enablement-lead` (L45) is the role that owns *org-wide* AI enablement, central tooling procurement at scale, workforce compliance, and the enablement portfolio. The team manager routes upward to this role when scope exceeds one team.
- Four graduation triggers: (1) scope creep across teams; (2) sustained manager delivery > 5 hrs/week; (3) formal workforce-level compliance obligations landing at org altitude; (4) procurement-scale budget conversations.
- The handoff is a *written contract* (Exercise 05) that preserves the team-shaped layer under the org-wide layer. Eight sections including transferred scope, retained scope, artifact inventory, measurement handoff, transition period, sunset.
- If your organisation does not yet have an L45 role, do not solve the gap by becoming it de facto. Name the gap, propose an interim owner, or produce a forward-looking role-scoping artifact.
- A larger team is not a graduation trigger; multi-team is.
- Routing upward is a competence, not an abdication. mod-105 is one of several track-level routing points (alongside mod-109, mod-110, mod-111).
- Exercise 05 produces the handoff contract for your organisation.
