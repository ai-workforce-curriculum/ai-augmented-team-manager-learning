# Quiz 01 — Hiring, Performance, and Compliance Under AI Augmentation

**Format:** 12 multiple-choice questions.
**Coverage:** All eight chapters of mod-108.
**Scoring:** 1 point per question. 9/12 is a pass. Below that, re-read the chapter named in the answer explanation before moving on.

Each question tests whether you can apply the chapter in a specific scope-of-practice decision, not whether you can quote it. Pick the single best answer.

---

## Question 1

A peer manager on another team asks you — the mod-108 reader — to write "the one-pager that picks the AI coding tool our hiring loop will use." Per Chapter 1, the strongest response is:

- A. Produce the one-pager; vendor selection in the hiring loop is a Pillar-1 artifact.
- B. Decline and route the vendor-selection question to [`mod-111`](../../mod-111-vendor-budget-and-tool-selection-at-team-scope/). Chapter 1 is explicit that mod-108 is *not* an AI-tool-selection course — it names *categories* of tooling the hiring loop touches and the Chapter 6 compliance framing, while specific vendor choices live in mod-111. Similarly, the module is not a legal-opinion course (counsel through HR), not an HR-process course (formal actions through HR), not a cross-team workforce-planning course (L45 / L50), and not a career-ladder-*authoring* course (the ladder is authored in mod-107 and *used* here).
- C. Delegate to the ai-enablement-lead (L45) as cross-team scope.
- D. Bundle the vendor pick under Exercise 05 as a compliance deliverable.

## Question 2

A peer manager, redesigning their technical screen, opens the conversation by saying: *"the first thing to decide is whether we allow AI in the screen — if we do, we write the rubric around what the agent can do; if not, we write it around unassisted capability."* Per Chapter 2, the strongest critique is:

- A. The peer should always allow AI because the role is AI-augmented.
- B. The peer should always disallow AI to see "the real candidate."
- C. The peer should run every stage as a take-home with walk-through.
- D. The peer has inverted the load-bearing step. Chapter 2's Step 1 — the stage-level signal statement (*what is the stage supposed to produce? how does it differentiate hire from no-hire?*) — is authored *before* the AI-use policy. Teams that pick the policy first produce a loop whose scoring is inconsistent across raters because the raters are scoring different things. Once the signal is written per stage, the policy choice is downstream: some stages reward effective agent use (AI-permitted, encouraged), some require disclosure, at most one should be AI-off, and a mix is typical. Writing the signal first is the chapter's load-bearing move; skipping it is the most common authoring failure.

## Question 3

In a disclosure-required live-coding stage, a rater scores two candidates: one narrated their prompts / acceptances / overrides throughout; the other ran the full session in near-silence while the agent generated the artifact. The rater asks whether to score the silent candidate at the middle of the 1–5 scale on the narration criterion ("neither narrated well nor badly"). Per Chapter 2, the correct answer is:

- A. Yes — silence is a stylistic choice; score at 3.
- B. No — the narration criterion is scored *down* for silence, not scored neutrally. The signal the disclosure stage is designed to measure (decision-making under AI augmentation) is specifically *absent* in the silent run, and that is what the rubric records. The rater is not scoring refusal to disclose; the rater is scoring that the signal the stage was designed to produce was not produced. Rate accordingly. The rater also interrupts — *"pause — I want to understand your thinking there"* — when the agent produces a subtle wrong answer and the candidate accepts it silently; interruption is part of the stage design.
- C. Rescore the entire stage AI-off for the silent candidate.
- D. Flag the silent candidate as adverse-impact exposure and withdraw the stage.

## Question 4

At a cross-team calibration meeting, a peer manager argues: *"my IC shipped 30 more PRs than yours this year — the senior → staff packet reads strongly on impact. What's your counter?"* Per Chapter 3, the strongest move for the manager who did the mod-108 refresh is:

- A. Concede and withdraw the packet to avoid a throughput-dominated debate.
- B. Match the PR count with an alternative count-based metric.
- C. Produce the one-paragraph **calibration-defence note** written *before* the meeting. Chapter 3 names the specific move: *"peer manager X's IC produced more PRs than mine. I'm not going to argue with that number. I'm going to point at my IC's three narratable judgement moves — the review catch, the push-back on the stakeholder plan, the redirect of the routing matrix — and ask the committee to weight those as the Axis A signal the ladder calls for. Peer manager X's IC packet doesn't show any of those. On Axis A at the senior → staff transition, my packet is stronger."* The note cites Noy & Zhang on dispersion compression. Managers who try to compose this argument in the room under pressure lose to peer managers citing throughput numbers in real time.
- D. Escalate to HR for calibration-process arbitration.

## Question 5

A manager drafts the one-page **reviewer-reading guide** that the promotion-committee reviewer will read before scoring the packet. The draft is framed as "why this candidate is ready" with a section per axis making the case for the IC. Per Chapter 3, this is:

- A. Correct — the reading guide is the manager's advocacy artifact.
- B. A wrong-audience framing. Chapter 3 is explicit that the reviewer-reading guide is written for the **reviewer's frame** — what signal each axis is supposed to produce on a packet, what the common misreads are, what a strong packet looks like — *not* the manager's "why ready" frame. The guide is one page because reviewers are time-pressured; longer guides don't get read. Audience-shift before shipping. The manager's advocacy lives in the packet narrative and the calibration-defence note, not in the reading guide.
- C. Correct but too short; expand to five pages for thoroughness.
- D. Replace with the Exercise 03 OKR document.

## Question 6

An IC proposes their next-quarter OKR: *"Objective — adopt AI across my daily workflow. KR1 — use Cursor on 90% of PRs. KR2 — ship 3 AI-assisted PRs per week. KR3 — reduce PR cycle time by 30% via AI-assisted development."* Per Chapter 4, the strongest critique is:

- A. The KRs are too modest; bump to 100%, 5/week, and 50%.
- B. Add a satisfaction KR to the mix and ship.
- C. The OKR confuses mechanism for outcome — AI usage is the *how*, not the *what*. Chapter 4's Principle 1 is explicit; KRs that read *"use AI more,"* *"N AI-assisted PRs per week,"* or *"reduce cycle time via AI-assisted development"* all reward the mechanism (AI usage) with no reference to whether the underlying outcome improved. The shape also rewards the exact compression pattern Noy & Zhang's finding predicts — the metric goes up, differentiation goes down, and the incentive structure is aligned against the mod-107 anti-atrophy work. Rewrite: name the customer-visible or system-state outcome, let AI be one of the means available; for an IC-scope OKR, weight ladder-aligned growth moves (narratable judgement moves, review-standard contributions, mentorship-of-judgement outcomes).
- D. Replace the objective with *"master Claude Code by end of cycle."*

## Question 7

After reading Chapter 4, a manager runs all five of the rotating questions (judgement-move, pairing, frontier, anti-deference, time-and-attention) in a single 1:1 to be "thorough." Per Chapter 4, this is:

- A. Appropriate — using every tool at once is efficient.
- B. A quiz-style failure mode. Chapter 4 names the five questions as **rotation prompts** the manager shapes a conversation with, not a quiz the IC runs through. Asking all five in one 1:1 reads as an interrogation and collapses the 1:1 architecture that reserves time for the IC's agenda, forward-looking planning, and one specific feedback moment. The correct cadence rotates through the questions across four to six 1:1s, with the manager keeping a log of which questions ran recently so the rotation is not accidental, and uses the monthly reflective 1:1 as the structured moment where patterns across prior weeks surface.
- C. Appropriate if the IC is a senior.
- D. Appropriate only on the first 1:1 after rollout.

## Question 8

A manager observes that an IC's throughput is roughly 30% below the team baseline and reports: *"this is obviously a motivation issue — I've seen this pattern before; let me open the HR conversation."* Per Chapter 5, the correct response is:

- A. Agree; manager intuition on performance is a strong signal and the drill is a formality.
- B. Run the drill's six questions in parallel with the HR conversation to save time.
- C. Skip to the Handoff-1 conversation with HR and let HR run the drill.
- D. Run the drill's six questions in strict order — shape-of-work, tool-access, enablement, pairing, workflow-friction, human-signal — *before* reaching a conclusion. The ordering is Chapter 5's load-bearing move. Manager intuition under AI augmentation is miscalibrated; the first five questions re-calibrate it. The failure mode the ordering prevents is specific: a manager who treats a routing/tooling gap as a performance problem, opens an HR escalation, and surfaces in the first check-in that the IC was being routed outside-frontier work with no paired-review rotation and a missed Day-90 bootcamp piece. The IC's trust, the team's trust, and the manager's credibility are all damaged. Only after questions 1–5 are answered with specific evidence does the drill turn to the human-signal question.

## Question 9

A manager, after one quarter of soft feedback, schedules "weekly growth check-ins with written milestones and performance-contingent consequences if milestones slip," and calls it a *growth plan* rather than a PIP "to avoid HR friction." Per Chapter 5 (and the Chapter 8 boundary), this is:

- A. Appropriate — weekly check-ins are a 1:1 cadence.
- B. Informal but harmless; the "growth plan" naming prevents HR complications.
- C. An **informal PIP**. Chapter 5 is explicit: scheduling weekly check-ins with explicit improvement milestones and performance-contingent consequences is a PIP whether it is called one or not. Naming does not change the shape; the shape is a formal employment action HR owns. The correct move is to run the Chapter 4 1:1 flow as a growth instrument (not a disguised performance process), or — if the pattern warrants a formal process — open the Handoff-1 conversation with HR as an *open question*, bring the two-quarter documented feedback artifacts and the Chapter 5 drill output, and let HR assess whether a formal PIP is appropriate. *"Keep working on it in 1:1s for another quarter, with sharpened structure"* is also a common outcome; the manager does not pre-decide the escalation.
- D. A manager-side artifact to be shared privately with the IC, bypassing HR.

## Question 10

A recruiter forwards a vendor demo of a new tool that *ranks candidate resumes against the job description* using ML. The team hires remote globally, including NYC and two EU member states. Facing a hiring push, the manager is inclined to approve the tool for the next requisition and notify legal afterwards. Per Chapter 6, the correct move is:

- A. Approve; the tool is low-risk and legal review would slow hiring.
- B. Approve for non-NYC, non-EU candidates; use human-only for NYC and EU to dodge the triggers.
- C. Read the DCWP final rules yourself and conclude the tool is out of scope because resumes are "unstructured data."
- D. **Pause the tool's use** entirely and run the three load-bearing questions from Chapter 6: (1) *does the tool substantially assist an employment decision?* — yes, ranking substantially assists; (2) *demographic data consumed or inferred?* — name and work-history, with features correlating with protected classes (EEOC 2023 TA directly applies); (3) *jurisdictions?* — US (EEOC / Title VII four-fifths rule), NYC (likely in-scope AEDT under LL 144 — annual bias audit, candidate notice ≥ 10 business days, data-source disclosure on request), EU member states (Annex III high-risk under EU AI Act; Articles 8–15 and 17 obligations from 2026-08-02). Flag to HR, who routes to legal counsel for scope determination and contract review. Fall back to human-only screening in the interim. Chapter 6 is explicit: the manager does **not** interpret the law, does **not** approve new hiring AI without the compliance review, and does **not** promise candidates the loop is "unbiased."

## Question 11

An exec reviewing the manager's headcount pre-read pushes back: *"DORA deployment frequency is up 40%, PR throughput is up 25%, DX Core 4 is up — why does the team need another senior engineer?"* Per Chapter 7, the strongest response is:

- A. Concede; the AI productivity gains close the gap.
- B. Re-cite the DORA / DX numbers more strongly.
- C. Re-route the request to the L45 enablement lead as cross-team scope.
- D. Name the gap specifically against the Chapter 7 structure. A 2026 headcount request has to answer *"why is this specifically a human-shaped gap?"* The mod-104 dashboards show in-frontier capacity gain (the instruments measure what AI compresses, not what AI does not); the gap this hire closes is Axis-A judgement at the senior tier on outside-frontier work the AI's capability frontier does not cover on this team's stack. Judgement-shaped, mentorship-shaped, and ownership-shaped gaps are human-shaped; toil-shaped gaps are tooling-shaped and should be solved there first. The pre-read also names the AI tooling spend attributable to the hire (seat + token budget per the mod-104 cost dashboard + enablement ramp cost) so the exec sees the whole-cost picture, and names what else was considered (contractor for the slice, scope reduction, more tooling) so the exec sees the alternatives. "AI has made us 25% more productive but we still need more people" without naming the specific gap reads as a request for more without a reason.

## Question 12

In one quarter a manager has (i) a vendor demo of a new structured-interview-scoring AI tool from a recruiter partner, (ii) an IC who after two quarters of growth work still shows thin Axis-A evidence despite the Chapter 5 drill addressing the workflow and tooling root causes, and (iii) an observed trend that the team's work has shifted toward agent-operations work that the current "senior engineer" role category describes imperfectly. Per Chapter 8, the correct routing is:

- A. All three to HR for coordinated handling.
- B. (i) approve bilaterally with the recruiter and inform HR afterwards; (ii) open an informal PIP under a "growth plan" label; (iii) author a new role category at team scope.
- C. All three upward to L45 / L50; the levels above decide which belongs where.
- D. Three distinct handoffs per Chapter 8. (i) is **Handoff A — compliance-review for a new hiring AI tool**: the manager runs the Chapter 6 three-question assessment, flags to HR, who routes to legal for LL 144 / EU AI Act scope determination and to procurement for contract review; the tool's use is paused until the review completes. (ii) is **Handoff B — the formal-performance-process handoff**: the manager opens the Handoff-1 conversation with HR as an *open question*, brings two quarters of documented feedback artifacts and the drill output excluding workflow/tooling causes, and lets HR assess whether a formal process is warranted; "continue in 1:1s with sharpened structure" is a common outcome. (iii) is **Handoff C — the role-architecture handoff upward**: a one-paragraph note to the L45 enablement lead that names the observation, the team-scope action already taken (routing-matrix updates, specific pairings), and the specific upward question (*"is 'agent operations engineer' a role the organisation is authoring? If yes, how should I slot the next senior hire?"*); the manager continues at team scope within existing role categories until the L45 owner responds. Routing everything to HR, upward, or deciding unilaterally are the three main failure modes Chapter 8 names.

---

## Answer key

1. **B.** Chapter 1 is explicit on the five things mod-108 is *not*: a legal-opinion course (Chapter 6; opinion stays with counsel), an HR-process course (Chapter 8; formal actions link to HR), a cross-team workforce-planning course (links to L45+), an atrophy course (the ladder is authored in [`mod-107`](../../mod-107-skill-growth-anti-atrophy-and-career-development/)), and an AI-tool-selection course (links to [`mod-111`](../../mod-111-vendor-budget-and-tool-selection-at-team-scope/)). The manager names tool *categories* and the compliance framing; specific vendor picks live in mod-111. (Chapter 1, "What this module is *not*.")

2. **D.** Chapter 2's "Common failure modes in authoring the loop" lists *"Writing the policy before writing the signal"* as the first and load-bearing failure mode. Step 1 — the stage-level signal statement — is the chapter's load-bearing move; the AI-use policy is Step 2 and is downstream of the signal. The common failure mode produces a loop whose scoring is inconsistent across raters because the raters are scoring different things. (Chapter 2, Steps 1–2 and "Common failure modes in authoring the loop.")

3. **B.** Chapter 2's "Operationalise the disclosure stage specifically" is explicit: *"Silence is scored down, not neutrally. A candidate who runs the entire stage in silence while their agent generates the artifact scores low on the narration criterion, because the signal the stage measures (decision-making under AI augmentation) is absent. The rater is not scoring refusal to disclose; the rater is scoring that the signal was absent."* Raters also interrupt on silent acceptance of a subtle wrong answer — the interruption is part of stage design, not a courtesy. (Chapter 2, "Operationalise the disclosure stage specifically.")

4. **C.** Chapter 3's "The calibration-defence note" is this exact pattern: a one-paragraph, pre-written note naming the specific comparison, the ladder axis, the research citation (Noy & Zhang on output compression), and the three narratable judgement moves the manager will point at. Managers who try to compose the argument in the room under pressure lose to peer managers citing throughput numbers. Written, cited, one paragraph. (Chapter 3, "The calibration-defence note" and the common failure mode "The calibration-defence note is not written down.")

5. **B.** Chapter 3's "The reviewer-reading guide" is explicit that the guide is written for the reviewer's frame (what to look for, common misreads, what a strong packet shows) and kept to one page because reviewers are time-pressured. The common failure mode "The reviewer-reading guide is written for the manager, not the reviewer" names this exact mistake. Audience-shift before shipping. (Chapter 3, "The reviewer-reading guide" and the common failure modes list.)

6. **C.** Chapter 4's Principle 1 is explicit: *"AI usage is the *how*, not the *what*."* The "What a bad OKR looks like, and why" section lists *"Increase AI tool adoption to 90% on the team,"* *"Reduce PR cycle time by 30% via AI-assisted development,"* *"Each engineer writes three AI-assisted PRs per week,"* and *"Master Claude Code / Copilot / Cursor by end of cycle"* as four of the five canonical bad OKR shapes. The IC-scope OKR should weight ladder-aligned growth moves (narratable judgement moves, review-standard amendments, Axis-B mentorship outcomes), not mechanism counts. The composition with Noy & Zhang's compression finding is the chapter's grounding. (Chapter 4, "OKRs or KPIs that reflect AI leverage" and "What a bad OKR looks like, and why.")

7. **B.** Chapter 4's "What the 1:1 is for, under AI augmentation" and "What *not* to do in the 1:1" are explicit: the five questions are *rotation prompts* across four to six 1:1s, mixed with the IC's agenda, with the manager keeping a log so the rotation is not accidental. *"Do not ask the five questions as a quiz. The questions are rotation-prompts the manager uses to shape a conversation. Asking all five in one 1:1 reads as an interrogation."* The monthly reflective 1:1 is the structured moment where patterns across prior weeks surface explicitly. (Chapter 4, "What the 1:1 is for, under AI augmentation" and "What *not* to do in the 1:1.")

8. **D.** Chapter 5's "The drill, as a short checklist" and "What *not* to do" are explicit on the ordering: *"The drill is explicit in its ordering. The first five questions surface workflow and tooling root causes. Only after those are excluded (or, if one is present, addressed with the right mod-105 / mod-106 / mod-111 intervention) does the drill turn to the human-skill question. The ordering prevents the failure mode of treating a routing problem as a performance problem."* *"Do not skip the first five questions because the human cause 'seems obvious.' The failure mode this chapter prevents is specifically the manager who skips the workflow and tooling questions because their intuition says it is the IC. Intuition under AI augmentation is miscalibrated; the first five questions re-calibrate."* (Chapter 5, "The drill, as a short checklist" and "What *not* to do.")

9. **C.** Chapter 5's "What *not* to do" is explicit: *"Do not open an informal PIP. … Scheduling weekly check-ins with explicit improvement milestones is a PIP whether it is called one or not. If the formal process is warranted, open it; if not, the Chapter 4 1:1 flow is the instrument."* The Handoff-1 conversation with HR is an *open question*, not a pre-decided recommendation; HR assesses, and "continue in 1:1s with sharpened structure" is a common outcome. Chapter 8 restates the same boundary. (Chapter 5, "What *not* to do" and "The PIP contract with HR, when it is warranted"; Chapter 8, "Must not do.")

10. **D.** Chapter 6's "The three load-bearing questions at team scope" and the worked resume-screening example match this scenario point-for-point. The tool substantially assists (ranks candidates), consumes features correlating with protected classes, and spans three regimes (US EEOC / Title VII, NYC LL 144 as a likely in-scope AEDT, EU AI Act Annex III high-risk). The manager flags and routes to HR → legal; the manager does *not* interpret the law, does *not* approve new hiring AI without the compliance review, and does *not* promise the loop is "unbiased." The tool's use is paused in the interim. (Chapter 6, "The three load-bearing questions at team scope," "What the manager must *not* do," and the "Example: a compliance-checklist route for a resume-screening tool.")

11. **D.** Chapter 7's "What a 2026 headcount request has to answer" names the four questions that compose on top of the pre-AI three: what has AI leverage done to capacity; what AI-tooling spend comes with the hire; why specifically a human-shaped gap (judgement / mentorship / ownership / outside-frontier task shapes are human-shaped; toil-shaped is tooling-shaped); what is the role-mix shift. The dashboards show the in-frontier gain but not the outside-frontier gap. "What *not* to do" is explicit: *"Do not argue headcount by invoking AI tooling against yourself. A headcount request that reads 'AI has made us X% more productive but we still need more people' without naming the specific gap reads as a request for more without a reason. Name the gap."* (Chapter 7, "What a 2026 headcount request has to answer," "The AI-cost side of headcount," and "What *not* to do.")

12. **D.** Chapter 8's "The three handoffs that are specifically mod-108" names Handoffs A, B, and C precisely in this shape — compliance-review for a new hiring AI tool (manager runs the Chapter 6 three-question assessment, flags to HR, who routes to legal; pause tool use); formal performance-process (Handoff-1 to HR as an open question with two quarters of documented feedback and the drill output); role-architecture signal upward (one-paragraph note to L45; continue at team scope until the owner responds). "What the manager must *not* do at the boundary" names the failures in options A, B, and C: not everything routes to HR; informal PIPs are explicitly named as a failure; routing team-scope decisions upward signals that the team manager is not operating at their own scope. (Chapter 8, "The three handoffs that are specifically mod-108," "What the manager must *not* do at the boundary," and "Common failure modes at the boundary.")
