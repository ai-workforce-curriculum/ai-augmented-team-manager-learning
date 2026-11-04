# Chapter 3 — Levelling and Promotion Criteria Refresh

> *The ladder [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/) authored names three new axes — judgement under AI augmentation, mentorship of judgement, review craft on AI-assisted work. This chapter is what those axes do during a real levelling cycle: which axes are weighted most heavily at which transition, how the rubric reads in a calibration meeting, how the promotion packet reads from a reviewer's seat, and how to keep AI-amplified throughput from quietly becoming the dominant signal again.*

## Motivation

mod-107 Chapter 6 authors the ladder update — new axes, level-descriptor amendments, promotion-packet structure. That chapter answers *what the ladder says*. mod-108 Chapter 3 answers *what the ladder does* in the operational cycle: how the rubric gets applied in a live calibration meeting, how the promotion committee reads a packet written against it, how a manager runs a promotion-case conversation with an IC six months before the packet is due, and how the levelling criteria stay honest when throughput is up 25% across the board.

The two chapters compose. mod-107 Chapter 6 writes the ladder; mod-108 Chapter 3 runs the review and promotion case against it. Exercise 02 produces the team-scope refresh artifact; Exercise 03 (OKRs with AI leverage) composes with it so the goal-set the IC pursues is calibrated to the ladder.

## Core concepts

### What the levelling-criteria refresh adds on top of mod-107

The mod-107 ladder update gives the team three new axes and level-descriptor amendments. The mod-108 refresh adds four things on top:

- **A weighting rubric at each transition.** The three new axes are not equally weighted at every level transition. Judgement (Axis A) is most weight-bearing at the senior → staff transition because that is where deference failures compound; mentorship of judgement (Axis B) is most weight-bearing at the senior → staff transition; review craft (Axis C) is weight-bearing across senior and staff. Junior → mid is the transition where throughput signal is hardest to unlearn; the refresh is explicit about de-weighting it.
- **A reviewer-reading guide.** A short document (one page) the promotion-committee reviewer reads before reviewing a packet, naming what signal each axis is supposed to produce and what the common misreads are. Without the reading guide, reviewers default to reading the packet against the pre-AI rubric they have internalised.
- **A pre-cycle conversation script.** Six months before a packet is due, the manager and the IC have an explicit conversation about which axes the IC's work is producing signal on and which axes need the next two quarters to build. The script is the rubric made actionable in 1:1 conversation.
- **A calibration-defence note.** A one-paragraph note the manager brings to the calibration meeting naming how the three axes will be compared across candidates from different teams. This is the manager's defence against the *"isn't this subjective?"* challenge and the *"my IC produced more PRs"* challenge.

### The weighting rubric, stated

Weights are approximate and are tools for the calibration conversation, not scorecards. The specific weights are tuned to your team's levels in Exercise 02.

| Transition | Axis A (judgement) | Axis B (mentorship of judgement) | Axis C (review craft) | Throughput / impact | Scope / ownership |
|---|---|---|---|---|---|
| Junior → mid | Moderate | Low | Moderate | Moderate | Moderate |
| Mid → senior | High | Moderate | High | Moderate | High |
| Senior → staff | Very high | Very high | High | Low (de-emphasised) | Very high |
| Staff → principal | Very high | Very high | Very high | Low | Very high (cross-team) |

Three observations:

- **Throughput is never zero-weighted, and it is never dominant above junior → mid.** Noy & Zhang's finding predicts that output signal compresses enough at senior tiers that using it as the dominant signal produces bad calibration.
- **Mentorship-of-judgement grows sharply at the senior → staff transition.** A senior IC can be a strong individual contributor without mentoring anyone. A staff IC whose work has not produced growth in other ICs on the team is miscast in the role.
- **Review craft grows at every transition after junior → mid.** The ability to run the judgement-weighted review pass on AI-assisted work is a capability the team needs more of at every level, and the ladder is what makes it a promotable capability.

### The reviewer-reading guide

The guide lives at the top of each promotion packet (one page, inserted by the hiring manager before submitting to the committee). It names, in short form:

- *What signal Axis A is supposed to produce on this packet.* "The packet should show three narratable judgement moves — a review catch, a push-back, a redirect — not a count of decisions."
- *What signal Axis B is supposed to produce.* "The packet should name specific ICs whose capacity grew under this candidate's pairing, with before-and-after artifact evidence."
- *What signal Axis C is supposed to produce.* "The packet should show the candidate's contribution to the review standard (mod-103) or the routing matrix (mod-106) — not just that the candidate reviewed PRs."
- *What the most common misread is.* "The most common misread of Axis A is treating 'used AI effectively' as the signal; the signal is specifically about judgement under AI augmentation — knowing when to override the AI."

The guide is short deliberately. Reviewers who are time-pressured (which is all reviewers) will not read a five-page guide; they will read one page.

### The pre-cycle conversation script

Six months before the packet is due, the manager runs a 1:1 conversation that is explicitly about levelling. The script, reduced:

1. *Which axes is your work currently producing signal on?* The IC names the axes and the specific artifacts.
2. *Where do you see the gap?* The IC names where the signal is thin. If the IC does not see a gap on an axis the manager sees a gap on, the manager names it directly.
3. *What are the next-two-quarter growth moves?* For each gap axis, the manager and IC agree on a specific move — a paired-review rotation (mod-107 Chapter 5), a specific review-standard contribution, a mentorship pairing with a named junior IC.
4. *What does the packet need to show six months from now?* The manager translates the growth moves into packet evidence — "you'll be able to name three narratable judgement moves, one of which is a push-back on a stakeholder plan."

The script is run explicitly as a levelling conversation, not merged into a generic 1:1. The distinction matters because the IC needs to know the conversation's character and have the time to respond.

### The calibration-defence note

The calibration meeting is where the manager advocates for the IC against peer managers' ICs. Under AI augmentation, the specific line the manager has to be ready to say is some version of:

> *"Peer manager X's IC produced more PRs than mine this cycle. I'm not going to argue with that number. I'm going to point at my IC's three narratable judgement moves — the review catch, the push-back on the stakeholder plan, the redirect of the routing matrix — and ask the committee to weight those as the axis A signal the ladder calls for. Peer manager X's IC packet doesn't show any of those. On Axis A at the senior → staff transition, my packet is stronger."*

The note is one paragraph long. It names the specific calibration argument before the meeting, with the ladder axis and the research citation (Noy & Zhang on output compression) in hand. Managers who go into calibration without this note find themselves arguing against a throughput number in real time and losing.

### The three failure modes the refresh prevents

- **The "shipped a lot" packet that passes committee.** An IC who shipped 30 PRs more than the prior year produces a packet that looks strong on throughput-measured impact. Under the refreshed rubric, the packet is read against Axes A/B/C and the thinness becomes visible. The committee has the language to push back.
- **The "quiet senior" packet that fails committee.** A senior IC whose output looks flat in throughput but whose mentorship moved two junior ICs' capacity visibly, and whose review catches saved three incidents, produces a packet that reads weakly against a throughput rubric. Under the refreshed rubric with Axis B weighted heavily at senior → staff, the packet reads clearly.
- **The "I have no idea" staff packet.** Staff-level work is diffuse. Under AI augmentation it gets more diffuse. The refreshed rubric at the staff transition is explicit that review-standard contributions (mod-103), routing-matrix updates (mod-106), and ladder-and-carve-out contributions (mod-107) are the work. Reviewers now have a place to look for the signal.

### How this composes with mod-104, mod-106, and mod-107

- **mod-104 (productivity measurement).** The DX Core 4 / SPACE dashboards from mod-104 are team-level outcome instruments, not individual-level levelling instruments. Chapter 4 names the division; Chapter 3's refresh is explicit that the DORA / DX dashboards do not produce promotion signal.
- **mod-106 (workflow redesign and agent delegation).** The routing-matrix artifact is one of the specific places staff-tier Axis C ("review craft on AI-assisted work") shows up. Staff ICs' contributions to the matrix are packet-evidence.
- **mod-107 (skill growth).** The ladder authored in mod-107 Chapter 6 is the standard. The refresh is explicitly about *using* that ladder in a real cycle, not about re-authoring it. If your team has not yet done the mod-107 Chapter 6 work, do it first — the refresh assumes the ladder exists.

### What *not* to do

- **Do not add a fourth AI-specific axis.** The mod-107 ladder has three. Adding more dilutes signal and burdens the committee. If the refresh keeps growing, the signal is lost.
- **Do not remove throughput from the rubric entirely.** Output still matters. The ladder weights throughput down at senior and staff; it does not zero it. An IC whose throughput is dramatically below the team's baseline has a performance conversation (Chapter 5), not a promotion packet.
- **Do not calibrate against peer teams that have not done the refresh.** Calibration across teams is harder under the refresh because peer teams may still be reading against the pre-AI rubric. The manager's job is to make the case; the organisation's job is to standardise. If calibration is systematically disadvantaging ICs whose managers did the refresh, escalate to the levelling owner (your head of engineering or HR partner) to get the broader refresh moving.
- **Do not let "used AI effectively" become a rubric criterion on its own.** It is not an axis; it is a *how*. The axes score what the IC did with AI, not that they used it.

### Common failure modes in running the refresh

- **The refresh is drafted but never applied to a live cycle.** The refresh has to run against a real packet to be legitimate. Pick one packet in the next cycle and run it under the new rubric; the exercise catches most calibration mistakes before they scale.
- **The reviewer-reading guide is written for the manager, not the reviewer.** Managers write the guide for their own frame — "why this candidate is ready." Reviewers need the inverse — "what should I look for and what are the common misreads." Audience-shift the guide before shipping.
- **The pre-cycle conversation is deferred.** The 6-month conversation feels early. It is not early; it is the window in which the IC can still produce the signal the packet needs. Deferring to 3 months out is too late for Axis B (mentorship takes time to produce artifacts).
- **The calibration-defence note is not written down.** The note has to exist on paper. Managers who try to compose the argument in the room under pressure lose to peer managers citing throughput numbers. Written, cited, one paragraph.
- **The refresh is applied to interview rubrics without mapping explicitly.** The interview rubric (Chapter 2) and the levelling rubric (Chapter 3) share axes but are not identical. The interview rubric scores a 2–4 hour window; the levelling rubric scores a 12–18 month window. Mapping naively between them collapses the distinction.

## Example: a senior → staff packet, read under the refresh

Composite example; treat as calibration, not a template.

**Packet under the pre-AI rubric:**

- Impact: "Shipped 22 features. Led migration from service-X to service-Y."
- Craft: "Consistently high-quality implementations. Clean PRs."
- Collaboration: "Responsive on Slack. Shows up to meetings."
- Ownership: "Owned the migration from start to finish."

The reviewer reads the packet and thinks: "This is a solid senior IC. Is this staff? Hard to tell."

**Same IC's packet under the refreshed rubric:**

- Impact: "Led the decision to run the service-X migration through the human-reviewed routing path. Caught two incorrect agent-generated migration scripts at review that would have broken downstream consumers. Shipped 22 features."
- Judgement (Axis A): "Three narratable moves: (1) pushed back on a stakeholder proposal to let the agent own schema migration, naming the specific failure mode that would have surfaced; (2) rejected the agent's suggested caching layer in the ad-auction path and wrote the alternative, citing the latency variance the agent could not model; (3) redirected the routing matrix to route schema changes through the human-reviewed path after one incident surfaced the gap."
- Mentorship of judgement (Axis B): "Paired with Junior IC A for two quarters on outside-frontier work in the migration. Junior IC A's PR-review notes in Q3 show three specific decision-vs-AI learnings; by Q4 Junior IC A was running the judgement move independently on their own PRs, with evidence in the review-comment log."
- Review craft (Axis C): "Contributed two amendments to the team's mod-103 review standard after retros surfaced gaps on AI-generated migration scripts. Contributed one amendment to the mod-106 routing matrix."
- Ownership: "Owned the migration end-to-end, including the three judgement moves above."
- Peer feedback (one specific prompt): "Name a decision this IC made that you would not have expected from someone at the senior level." Three peers cite the push-back on the schema migration.

The reviewer reads the packet and thinks: "This is a staff IC. The signal is specific, narratable, and distinguishes clearly from senior-tier work."

The *substance* of the IC's work did not change between the two packets. The *signal* the packet produces is different because the rubric is different.

## Summary

- The levelling refresh adds four things on top of the [`mod-107` ladder](../mod-107-skill-growth-anti-atrophy-and-career-development/06-career-ladder-under-ai-augmentation.md): **weighting rubric per transition**, **reviewer-reading guide**, **pre-cycle conversation script**, **calibration-defence note**.
- **Weighting:** judgement (Axis A) and mentorship-of-judgement (Axis B) grow sharply at senior → staff; throughput is weighted down above junior → mid. Grounded in [Noy & Zhang](https://www.science.org/doi/10.1126/science.adh2586) on dispersion compression.
- **Reviewer-reading guide** is written for the reviewer's frame (what to look for, common misreads), not the manager's frame.
- **Pre-cycle conversation** happens six months before the packet is due; defers Axis B evidence otherwise.
- **Calibration-defence note** is one paragraph, written down before the meeting, names the ladder axis and the research citation in the specific comparison.
- **Three failure modes prevented:** the "shipped a lot" packet, the "quiet senior" packet, the "no idea what staff does" packet.
- **Composes with** [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) (dashboards are team-level, not individual-level signal), [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) (routing matrix contributions are staff-tier Axis C evidence), [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/) (ladder is the standard; refresh does not re-author it).
- **Handoff to Chapter 4:** the OKRs / KPIs an IC pursues this cycle should be calibrated to the ladder axes the IC is building toward; Exercise 03 composes with Exercise 02.
- **Handoff to Chapter 5:** when a packet reads weakly on every axis, the next conversation is not the next packet — it is the underperformance root-cause drill.
