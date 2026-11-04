# Chapter 7 — Partnering with HR, L&D, and Platform on Delivery

> *You author the curriculum and the measurement rubric. Your partners deliver sessions, run intake, provision tooling, and backfill the formal learning record. The division of labour is explicit, in writing, and respects the altitude of each function.*

## Motivation

R5 is explicit on the partner shape: *"partner with HR / L&D / Platform on the delivery side."* The chapter title names three partners; in practice, a mod-105 programme typically touches more — Vendor Success teams, Procurement, Security, Legal, and in larger orgs a dedicated AI enablement office that sits at the `ai-enablement-lead` (L45) altitude. Chapter 8 handles the specific L45 graduation case; this chapter handles the ongoing partner interfaces while the programme runs at team scope.

Two orientations to carry through:

- **The manager authors; partners deliver.** Chapter 1 named this, and every chapter since has reinforced it. The partner-side chapter is where the division of labour gets operational — who does what, who signs for what, what the contract looks like in writing.
- **Partner functions have their own altitude and their own backlogs.** An L&D partner working with your team is also working with four other teams. A Platform partner running the Cursor enterprise rollout is handling it for three thousand engineers, not just your twenty. Requests that respect the partner's altitude and timing land; requests that treat the partner as a vendor to be dispatched do not.

This chapter sketches the three primary partner interfaces, a shared partnership contract shape, and the escalation / scope-creep patterns that actually come up.

## Core concepts

### The three primary partners and what each owns

**HR partner (HRBP / People Business Partner).** The HR partner's altitude is the *formal employment relationship* — job levels, performance review structure, compensation bands, policy. What they own that touches your programme:

- *Policy framing.* Any time your programme touches the formal learning record (tracked hours for compliance, L&D budget attribution, promotion-criteria wording), HR is the owner of the underlying template. You contribute content; they own form.
- *Formal recognition.* The stage-4 pattern-contribution recognition from Chapter 4 may touch job-level descriptions or merit criteria. HR owns how that gets written into the levelling doc.
- *Compliance posture.* If your organisation has an EU AI Act Article 4 AI-literacy obligation for deployers (the manager is the operational owner at team scope — see `mod-110`), HR is often the compliance-side counterpart who tracks completion across the org.

What HR *does not own.* The curriculum content. The measurement rubric. The specific tool choices. HR does not deliver the bootcamp.

**L&D / Learning & Development partner.** The L&D partner's altitude is *instructional design, delivery logistics, and the LMS*. What they own that touches your programme:

- *Delivery logistics.* Scheduling the cohort sessions, booking rooms, running registration, handling the calendar at scale.
- *Instructional-design review.* A reasonable L&D partner will offer to review your curriculum for pedagogy — session pacing, cognitive-load limits, assessment design. Accept the review where it adds value; reject where it tries to genericise the content. This is the most common site of partner-authored drift.
- *LMS integration where required.* If your organisation runs a formal LMS (Workday Learning, Cornerstone, Degreed, internal-build), L&D owns the pipe into it. Your programme's completion records may need to route there for compliance.
- *Delivery capacity.* L&D may have internal instructors who can deliver workshops. Use them where their expertise overlaps your content; do not hand them the curriculum pen (Chapter 1).

What L&D *does not own.* The curriculum content for a team-shaped programme. The measurement rubric. The team's specific review standards or tooling. L&D cannot author mod-105 artifact 1 (first-successful-PR-with-tool) because the artifact lives in your production repo under your review standard.

**Platform / DevEx partner.** The Platform partner's altitude is *tooling and the developer platform*. In many organisations this is also where the enterprise AI tooling rollout lives — the Cursor / Copilot / Claude Code enterprise contract, SSO integration, admin console, telemetry pipeline. What they own:

- *Tool provisioning.* Seats, SSO, access control, security posture of the tool.
- *Usage telemetry.* The pipe from the AI tooling vendor into your organisation's observability stack (if present). This is the data source for the mod-104 AI-cost ratio tile and for the Chapter 4 usage-budget monitoring.
- *First-run technical onboarding.* Walking new users through SSO, installation, workspace setup. A one-hour technical session at the start of Chapter 2's Day 1–10 bootcamp block.
- *Policy enforcement.* If your organisation has a tool-authorisation policy (no public models for customer data, etc.), Platform is often the enforcement layer.

What Platform *does not own.* The curriculum content. The learning-stage rubric. The team's specific pattern library. Platform can tell you how many tokens an engineer burned; they cannot tell you whether the engineer's fluency grew.

### A single written partnership contract per partner

The anti-pattern on all three partner interfaces is *informal, meeting-by-meeting coordination*. A reasonable partnership becomes drift because nobody wrote down what each party was signing for.

The fix is a one-page partnership contract per partner, written once at the programme's inception, revised at the quarter boundary. A workable shape:

| Section | HR partner example | L&D partner example | Platform partner example |
|---|---|---|---|
| Programme name | mod-105 team AI enablement — Platform Team | same | same |
| Period | Q1 2026, reviewed quarterly | same | same |
| Manager-owned | Curriculum, measurement rubric, stage pinning, artifact scoring, graduation decisions | same | same |
| Partner-owned | Policy template review; formal-record alignment; compliance crosswalk | Scheduling + intake; LMS completion records (if required); instructional-design review | Tool provisioning; usage telemetry; first-run onboarding; policy enforcement |
| Explicit non-asks | HR does not author content, deliver sessions, or score artifacts | L&D does not author team-specific curriculum, override the measurement rubric, or route artifacts through the LMS | Platform does not author curriculum, assess learners, or enforce usage caps on stage-1/2 engineers in-cohort |
| Review cadence | Quarterly 30-min sync | Bi-weekly 15-min sync during cohort delivery | Weekly 15-min sync during cohort kickoff; monthly thereafter |
| Escalation | Mod-108 performance interactions, mod-110 compliance interactions | Vendor-trainer scoping conflict; LMS integration disputes | Tool access incidents; usage telemetry gaps |

The explicit non-asks column is the load-bearing one. A partner who agrees in writing that they are not the content author cannot drift into authoring without renegotiating.

### The vendor-trainer slot

Most vendors on your stack (Cursor, Anthropic, GitHub, Microsoft) will offer enablement sessions as part of the enterprise contract. These are a legitimate input, with two scoping rules:

- **Scope the vendor session into your curriculum, not around it.** If the vendor is delivering a session, it is one of your Chapter 3 workshop slots or one of your Chapter 2 bootcamp sessions. The curriculum is still yours. Pre-brief the vendor on your team's specific workflow, review standards, and the specific skill the session should target.
- **Review the vendor's material before delivery.** The vendor's default is generic; your request is team-specific. A 30-minute pre-brief with the vendor trainer, with your curriculum doc in hand, aligns the session to the cohort's actual learning need.

Signs the vendor-trainer slot is drifting: the vendor runs the same session across multiple teams in your org without pre-briefing; the vendor's material is a product demo; the vendor is pushing an upsell during the session. Each is a signal to pull the vendor-trainer slot back.

### Managing the delivery-load distribution

Chapter 3 named the authoring-vs-delivery split. In practice, the delivery load for a running cohort looks approximately like this (for one cohort in bootcamp + workshop + CoP phase simultaneously):

| Role | Approx. time/week in delivery | What they deliver |
|---|---|---|
| Manager | 2–3 hours | 1 of 5 workshops; the Day-0 kickoff; the Day-30 / Day-60 / Day-90 checkpoints; facilitation of some CoP sessions |
| Senior IC #1 (volunteer) | 1–2 hours | 2 of 5 workshops; pair-with-mentor time |
| Senior IC #2 (volunteer) | 1–2 hours | Pair-with-mentor time; a show-and-tell in the CoP |
| L&D partner | 2 hours | Scheduling + intake across all active cohorts; LMS record if required |
| Platform partner | ~1 hour | Technical onboarding at the Day 1–10 block; monthly telemetry review |
| Vendor trainer | 1 hour per cohort (sparingly) | One session per cohort, pre-briefed by manager |

The manager's 2–3 hours/week is the budget line to hold. Sliding past 5 hours/week in delivery for a sustained period is a signal that the programme has not actually distributed delivery; renegotiate at the quarter boundary. Chapter 8 goes further: if the whole-of-organisation delivery load does not fit in the manager-plus-ICs-plus-partners envelope, the programme may need to graduate to L45.

### Three failure patterns that show up in partner interfaces

- **"We already have a corporate AI literacy course."** The corporate course is a compliance baseline, not a programme. The right response is *"we take the compliance baseline; the programme runs additionally."* Not instead-of; not inside-of. Chapter 1 Failure A is this same pattern on the receiving end.
- **"L&D will handle the curriculum."** A partner function offering to lift the curriculum authoring is often well-meaning and is always the wrong move for a team-shaped programme (Chapter 1). The right response is *"L&D handles instructional-design review and delivery logistics; team-specific curriculum stays with the manager."* If this response is pushed back on repeatedly, the issue is sitting at an altitude above you — see Chapter 8's L45 graduation case.
- **"Platform needs to enforce a hard cap on tokens."** The default FinOps posture is to impose a cap. For a mod-105 programme in flight, especially on stage-1 and stage-2 engineers, a hard cap is Failure B from Chapter 1 dressed as governance. The right response is *"the mod-104 cost tile is tracking this; the Chapter 4 learning-stage rubric is the allocation instrument; a hard cap would corrupt the measurement — can we instead set stage-sensitive alerts?"* Usually lands; occasionally doesn't; when it doesn't, escalate per the explicit-non-asks line of the partnership contract.

### The "who signs" question

For the formal artifacts your programme produces — one-page exec pre-read, stage-pin sheets, graduation decisions, handoff contracts — you need to know whose signature matters. A working rubric:

- **Stage-pin sheet.** Signed by the engineer and the manager. HR does not sign. (It is not a formal performance record.)
- **90-day graduation decision.** Manager signs. If the decision is "off-ramp this tool for this engineer," the manager also notes it in the manager-only 1:1 log; does not route to HR unless the engineer agrees in writing.
- **Exec pre-read (one-pager) for the quarter's enablement review.** Manager authors; VP of engineering (or equivalent) signs; HR partner, L&D partner, and Platform partner are cc'd.
- **Handoff contract to `ai-enablement-lead` (L45).** Manager authors; L45 signs; VP cc'd. See Chapter 8.

A programme whose signatures drift upward — HR starts routinely signing stage pins, for example — has usually also drifted the authorship pen. Renegotiate.

## Example: a one-page partnership contract with an L&D partner

Treat as calibration, not a template.

> **Programme:** mod-105 team AI enablement — Platform Infra team (18 engineers).
> **Period:** Q1 2026, reviewed quarterly at the Q-boundary.
>
> **Manager-owned (J. Ferguson, team manager):**
> - Curriculum design, session content, workshop topics, bootcamp sequencing.
> - Measurement rubric and artifact definitions (stage-pin rubric; first-successful-PR; pair-with-agent; review-of-your-review).
> - Stage pinning and budget conversations with engineers.
> - Artifact scoring and graduation decisions.
> - Exec pre-read authorship.
>
> **L&D partner-owned (A. Rivera, L&D BP):**
> - Cohort scheduling, room booking, calendar logistics across 3 active cohorts.
> - Intake flow (invite, pre-read distribution, Day-0 prep).
> - Instructional-design review of the manager's curriculum (advisory, not authorising).
> - LMS completion records for compliance — mod-110 EU AI Act Article 4 literacy baseline (name of record, completion date only; artifact content does not route to LMS).
> - Vendor-trainer scheduling (one session per cohort, pre-briefed by manager).
>
> **Explicit non-asks on L&D:**
> - L&D does not author or alter team-specific curriculum without manager sign-off.
> - L&D does not route the three fluency-growth artifacts (PR + reflection, pair-with-agent reflection, review-of-your-review) through the LMS.
> - L&D does not deliver bootcamp Sessions 1–4; bootcamp Session 5 (retro) is manager-facilitated.
>
> **Review cadence:** 15-minute bi-weekly sync during active cohort delivery; 30-minute quarterly sync at Q-boundary; escalation path via VP of Engineering if non-asks are breached.
>
> **Signed:** J. Ferguson (manager), A. Rivera (L&D BP), 2026-01-08. Review date: 2026-04-01.

One page, specific, auditable, with the non-asks visible.

## Summary

- Three primary partners: **HR** (formal employment relationship + policy), **L&D** (instructional design + delivery logistics + LMS), **Platform** (tooling + telemetry + policy enforcement). Each owns specific pieces; none owns the curriculum or the measurement.
- Partnership contract per partner, in writing, revised quarterly. The *explicit non-asks* column is load-bearing.
- Vendor-trainer slot is an input you scope *into* your curriculum, not around it. Pre-brief; review material; limit to ~1 session per cohort.
- Delivery load approximately: 2–3 hours/week manager, 1–2 hours/week each of 2 senior IC volunteers, 2 hours/week L&D, 1 hour/week Platform, 1 hour/cohort vendor. Sliding past 5 hours/week manager is a graduation signal.
- Three partner failure patterns: corporate-course-as-programme; L&D-as-curriculum-author; Platform-as-hard-capper.
- Know whose signature matters: stage pins (engineer + manager); graduation (manager); exec pre-read (VP); handoff (L45 + manager). Signatures drifting upward mirror authorship drift.
- Exercises 01 and 04 produce artifacts that the partnership contracts need to reference.
