# Quiz 01 — Team-Scope AI Enablement Programmes

**Format:** 12 multiple-choice questions.
**Coverage:** All eight chapters of mod-105.
**Scoring:** 1 point per question. 9/12 is a pass. Below that, re-read the chapter named in the answer explanation before moving on.

Each question tests whether you can apply the chapter, not whether you can quote it. Pick the single best answer.

---

## Question 1

Your HR business partner emails you: *"Great news — L&D has an off-the-shelf AI-literacy curriculum and three of their instructors are available to deliver it to your team end-to-end next quarter. We'll own it from here."* Per Chapter 1, the strongest response is:

- A. Accept — this frees up your calendar for review work and the team still gets AI training.
- B. Accept but ask for the slide deck first so you can verify it mentions Cursor.
- C. **Decline the end-to-end hand-off. Chapter 1 is explicit that delivery is delegable but **authoring and measurement are not** — "you author, your partners deliver, your team practices, you measure." A curriculum written by an external function cannot encode your team's actual workflow (the proprietary ORM, the specific review standard, the delegation patterns in use), and the measurement rubric the fluency-growth artifacts map to is your mod-103 / mod-104 artifact set, not L&D's. The right counter is "deliver sessions I have scoped; I retain the curriculum pen and the measurement rubric." Accepting the hand-off is Failure A (the one-shot generic workshop) and Failure C (the vanity bootcamp without on-the-job artifacts) in combination.**
- D. Accept the delivery but require L&D to co-sign the stage sheets so measurement stays shared.

## Question 2

Your team has had Cursor seats for six weeks. Telemetry shows seven of thirty engineers log in daily; the other twenty-three have opened the IDE twice. A peer manager suggests emailing the twenty-three a reminder with the vendor's quick-start guide. Per Chapter 1, the strongest critique of this plan is:

- A. The email is fine but should come from the VP, not the manager.
- B. The quick-start guide is the wrong artifact — send Peng et al. 2023 instead.
- C. **The licence-drop failure (Failure B) is not fixed by a nudge email. The symptom — twenty-three stage-1 engineers with unused seats — is the absence of a cohort-shaped practice loop around the tool, not an awareness gap. Chapter 1: "a ~$600/engineer/year licence fee that funds a fluency delta of near-zero" is prevented by *Day-0 stage pins + Day-30 PR checkpoints + cohort delivery*, not by withholding seats or sending reminders. The right next move is to run the Chapter 2 cohort structure on the twenty-three (overlapping cohorts of 5) with the Chapter 4 stage-pin conversation at Day 0.**
- D. Replace Cursor with Copilot since adoption telemetry is lower on Cursor.

## Question 3

You are forming the first cohort for your rolling programme. Your team has four engineers you could place together: a staff engineer who has never used Claude Code (stage 1), a senior engineer who built their own agent harness as a side project last year (stage 3), a mid-level engineer who has used Claude Code on side projects but not shipped production with it (stage 2), and a new grad who has used it in school projects (stage 2). Per Chapter 2, the best cohort composition decision is:

- A. Split by seniority — put the staff engineer with other seniors and the new grad with juniors.
- B. **Keep the four together — this is exactly Chapter 2's "mixed stage, not mixed seniority" sweet spot (one at stage 1, two at stage 2, one at stage 3). The stage-2 engineers learn from the stage-3 engineer specifically; the stage-1 staff engineer learns the questions to ask by hearing the stage-2 engineers ask them. A seniority-shaped split would pair the staff engineer (stage 1) with other seniors who may themselves be stage 1, producing a cohort of four stage-1 engineers that learns slower by construction (Brynjolfsson-Li-Raymond and Dell'Acqua from Chapter 4 ground the move).**
- C. Pull the staff engineer out of the cohort entirely — seniors don't need this.
- D. Make the new grad wait until next quarter so this cohort stays "focused."

## Question 4

Your first cohort hits Day 30. Of four engineers, only one has a merged PR with the team's primary AI coding assistant. The other three have drafts open but nothing merged. Per Chapter 2, the correct manager-side reading is:

- A. Three of four engineers are underperforming — note it in their 1:1s.
- B. The cohort is on track — PR merging is lagging and will catch up.
- C. **Day-30 PR slippage is a *programme-design signal, not a performance signal* on the engineers. Chapter 2 names three causes to check: (a) the primary tool does not fit the team's work; (b) the pair-with-mentor phase (Days 11–20) did not actually happen; (c) the production repo has review-standard barriers that prevent an in-progress learner from merging. The manager owns the remediation — potentially an extension or a tool-fit reconsideration at the Chapter 8 graduation-decision scale — not a shaming conversation. A manager who routes the slippage to engineer performance has misread the instrument.**
- D. Lower the Day-30 bar to "draft PR open" for this cohort.

## Question 5

Your team is standing up what you keep calling a "community of practice." Current state: a Slack channel called `#ai-practice` with 14 messages in it from February and a Confluence page with five vendor-blog links. Per Chapter 3, what is the strongest diagnosis of the current state against the Wenger-Trayner structural elements?

- A. The CoP exists but needs more members — invite adjacent teams.
- B. **The current state has (partial) *domain* and (partial) *practice* but no *community*. All three Wenger-Trayner elements — domain (shared area of concern), community (people who care and interact regularly), practice (shared repertoire of resources and ways of handling recurring problems) — must be present or the CoP is a shell (Chapter 3). A Slack channel is one tool the CoP may use; a wiki of links is not a practice; neither substitutes for the recurring interaction a community produces. The right next move is to stand up the recurring cadence (bi-weekly show-and-tell, monthly pattern-library review) with a facilitator rotation of 3–5 engineers.**
- C. The CoP is fine — Slack and Confluence are the delivery mechanisms.
- D. Replace the Slack channel with a Microsoft Teams channel; the tooling is the issue.

## Question 6

A senior IC proposes running a *single 90-minute session* called "Copilot bootcamp" for the whole team at the next all-hands. Per Chapter 3, the strongest critique is:

- A. 90 minutes is fine — scale down to 60 minutes to make it fit.
- B. **A single 90-minute session is not a bootcamp; it is a workshop at best (or a demo at worst) with an over-ambitious scope. Chapter 3 is explicit that a bootcamp is "concentrated, cohort-based, tool-specific" with 3–5 sessions over two weeks, hands-on on real code, and Session 4's pair-with-mentor time is where "the bootcamp earns its name." Running one session at an all-hands collapses the cohort structure, the concentration, and the real-repo practice loop — "no cohort means no bootcamp." The right reframe is either: run it as one workshop on a specific skill (not "Copilot"-as-a-tool), or run an actual bootcamp as a 5-session sequence for a 3–6-engineer cohort.**
- C. Run it twice so everyone attends — bootcamps scale by replication.
- D. The IC is right; the "bootcamp" label just needs to be used more loosely in this org.

## Question 7

At the Day-0 budget conversation, a stage-1 engineer (never used the tool at work) asks whether they get a Cursor seat now or have to "earn it." A Finance partner is pushing you to allocate seats only to engineers with demonstrated prior usage, to manage spend. Per Chapter 4, the correct response is:

- A. The Finance partner is right — withhold seats from stage-1 until they demonstrate usage.
- B. Allocate a lower-tier Cursor seat to stage-1 engineers and the enterprise tier to stage-3+.
- C. **Allocate the full seat to the stage-1 engineer. Chapter 4 is explicit: **everyone gets the seat**. "Earn the seat by proving you'll use it" is a budget policy that mathematically guarantees stage-1 engineers stay there — door-opening friction keeps them from crossing into stage 2, and a cohort with missing seats is broken by construction. What *varies* is the usage expectation, not the seat allocation. The licence-drop failure (Chapter 1 Failure B) is prevented by Day-0 pins and Day-30 PR checkpoints, not by withholding access. The Finance partner's concern is addressed through the stage-shaped usage projection and the mod-104 AI-cost-ratio tile, not through seat withholding.**
- D. Ask the stage-1 engineer to sign a "will use within 30 days" commitment in exchange for the seat.

## Question 8

Your Platform partner proposes a hard cap of 500k tokens/month per engineer on the usage-based tool, applied uniformly across the team, to protect against runaway spend. Per Chapter 4 and Chapter 7, the strongest objection is:

- A. 500k is too low — raise to 2M and accept the cap.
- B. **A flat hard cap is Failure B (the licence drop) in FinOps costume. Stage-1 and stage-2 engineers are *learning* — burning tokens on exploratory prompts is the practice at those stages — and a hard cap at that level corrupts the measurement by throttling the learners mid-task, exactly where the programme's fluency investment needs to land. Chapter 4's correct shape is: soft usage floor at stages 1–2 (no cap), team-median at stage 3, named ceiling with quarterly review at stage 4. The right counter (Chapter 7's third partner failure pattern) is "the mod-104 cost tile is tracking this; the Chapter 4 learning-stage rubric is the allocation instrument; a hard cap would corrupt the measurement — can we instead set stage-sensitive alerts?"**
- C. Accept the cap but ask Platform to exempt staff engineers.
- D. Accept the cap; usage-based pricing is unsustainable without one.

## Question 9

A cohort member turns in their Day-60 pair-with-agent reflection. The *judgment* section reads: *"The agent did great on this task. I would definitely use it again — it saved me hours. I think everyone should try this approach."* Per Chapter 5, the correct reading of this reflection is:

- A. High signal — the engineer has internalised that delegation works.
- B. High signal on *attitude*; manager should note the enthusiasm in their next 1:1.
- C. **Low signal. Chapter 5 is explicit that the judgment section is the highest-signal section of the pair-with-agent reflection, and that "an engineer who writes 'the agent did great; I would use it for everything' has not done the pair-with-agent work." The artifact is grounded in Dell'Acqua et al.'s jagged-frontier finding — the fluency being measured is the engineer's internal map of which tasks to delegate and which not to. A reflection that reads as advocacy with no change-of-mind and no "what I would *not* delegate" is the Chapter 5 "honesty > polish" guardrail firing. Separately, this is the pattern Chapter 2 names as "Day-60 reflection vacuity" — if the whole cohort writes this shape, the delegation task was too small or too script-like, which is a programme-design signal, not a learner signal.**
- D. High signal — change-of-mind is only required at Day 90, not Day 60.

## Question 10

A peer manager's one-pager contains the sentence *"Josh Bersin research shows this programme design produces 30% more AI capability than vendor-run training, which is why we expect strong ROI next quarter."* Per Chapter 6, the strongest critique is:

- A. The number is low — Bersin's capability-academy research actually shows closer to 40%.
- B. Cite McKinsey instead — their enterprise surveys are more defensible for this claim.
- C. **Bersin's AI-in-L&D / capability-academy research is *directional and framework-shaped*, not experimental. It does not publish a quantitative comparative "X% more capability than Y" number, and wielding a Bersin cite as if it were a controlled trial is over-claiming (the specific failure Chapter 6 names). The right shape is to cite Bersin's *frame* ("the capability-academy pattern — cohort-based, artifact-producing, community-sustained") for the programme shape, and to use the Work Trend Index (with vendor-authored + self-report caveats) for the "learned in context of real work" corroboration. The peer-reviewed productivity numbers (Peng, Brynjolfsson, Dell'Acqua) come in at the mod-105 Chapter 5 *artifact* level, never attached to the Bersin frame.**
- D. The sentence is fine; add "approximately" before "30%".

## Question 11

Your L&D partner has started revising the first-successful-PR-with-tool reflection template to fit the organisation's LMS, including a numeric 1–5 rating field and routing the reflection to the engineer's learning record. Per Chapters 5 and 7, the correct response is:

- A. Agree — LMS routing improves visibility and the rating creates clearer signal.
- B. Agree on LMS routing but push back on the numeric rating only.
- C. **Push back on both. Chapter 5 is explicit that the three fluency-growth artifacts live where the team's work lives (the PR, the engineer's folder, the CoP pattern library) and that routing them through an LMS corrupts them — reflections drift toward LMS-formatting, and a numeric rating pushes the instrument into performance-management territory (Chapter 5's first scoring guardrail: "the artifacts are not for performance management"). Chapter 7's partnership contract has this precisely as an explicit non-ask for L&D ("L&D does not route the three fluency-growth artifacts through the LMS"). The right counter is "LMS carries the EU AI Act Article 4 baseline completion record (name + date only); the reflection content and any scoring stays with the team-scope stage sheet." If the push continues, Chapter 7's escalation path applies.**
- D. Agree to the rating field but keep the reflection off the LMS.

## Question 12

Your mod-105 programme has been running for two quarters. Three signals are now live: (1) the Developer Experience team has asked to send a few engineers to your next bootcamp; (2) your weekly delivery load has been 6 hours for six consecutive weeks; (3) your team has grown from 18 to 25 engineers. Which reading of the graduation question is correct per Chapter 8?

- A. All three signals mean the programme must graduate to L45 immediately.
- B. **Two of the four Chapter 8 graduation triggers have fired — scope creep across teams (Trigger 1, the Developer Experience request) and sustained manager delivery > 5 hours/week (Trigger 2, the 6-hour load for six weeks, not a one-week spike). The third signal is a *trap*: Chapter 8 is explicit that **a larger team is not a graduation trigger** — the trigger is multi-team, not team-size, and the overlapping-cohort model in Chapter 2 scales up to a 40-engineer single team. Two triggers firing makes graduation urgent; the right next artifact is Exercise 05 (the handoff contract to `ai-enablement-lead`), which preserves the team-shaped layer under the org-wide layer. If your org does not yet have an L45 role, the chapter's Posture A (name the gap) or Posture B (propose an interim owner) applies — do *not* solve the gap by becoming the L45 role de facto.**
- C. Only trigger (2) has fired — a single adjacent-team request is not scope creep yet.
- D. None has fired — Trigger 1 requires an org-wide mandate, not a single team's request.

---

## Answer key

1. **C.** Chapter 1 names the authoring-vs-delivery split as the load-bearing division of labour: "you author, your partners deliver, your team practices, you measure." Only the manager knows the team's actual workflow and owns the mod-103 / mod-104 measurement crosswalk; an end-to-end-handed-off L&D curriculum is the composite Failure-A/Failure-C pattern. The right response specifies that delivery can rotate (senior IC, L&D, vendor) but authoring and measurement cannot. (Chapter 1, "Why the manager authors the curriculum even when they do not deliver it" and "The division of labour.")

2. **C.** Chapter 1's Failure B (the licence drop) is prevented by the Chapter 2 cohort structure plus the Chapter 4 Day-0 stage pin plus the Day-30 PR checkpoint, *not* by nudge emails or seat-withholding. The twenty-three stage-1 engineers are not a comms gap; they are an absent practice loop. Overlapping cohorts of 5 running the full 90-day structure is the correct next move. (Chapter 1, "Failure B — the licence drop" and the five-piece-shape table pointing at Chapter 2.)

3. **B.** Chapter 2's cohort composition guidance is explicit: *"Mix engineers with different learning stages on the primary tool — e.g. two at stage 1 (never used), one at stage 2, one at stage 3."* This is Brynjolfsson-Li-Raymond and Dell'Acqua operationalised — stage-2 engineers learn from stage-3 engineers specifically; stage-1 learners pick up the questions to ask by hearing stage-2 ask them. Mixed seniority (especially mixed seniority-at-same-stage) is a weaker configuration for fluency gain. (Chapter 2, "Cohort sizing: 3 to 6 is the sweet spot" — mixed-stage-not-mixed-seniority bullet.)

4. **C.** Chapter 2's "When the programme breaks and how to notice" names Day-30 PR slippage specifically and lists three programme-design causes to check (tool fit, missing pair-with-mentor time, review-standard barriers). The explicit framing is "each failure signature is a programme-design signal, not a performance signal on the engineer." A manager who routes the signal to engineer performance has misread the artifact and will corrupt the Chapter 5 measurement guardrail against performance-management use. (Chapter 2, "When the programme breaks and how to notice.")

5. **B.** Chapter 3 names the three Wenger-Trayner structural elements — domain, community, practice — and is explicit that "a CoP that is missing one of the three is a shell": domain without practice = a Slack channel of links nobody tries; practice without community = a wiki nobody reads; community without domain = a weekly social with no throughline. A Slack channel plus a link-dump satisfies neither the community (recurring interaction) nor the practice (shared repertoire of doing) dimensions. The fix is the recurring cadence plus facilitator rotation, not a tooling swap. (Chapter 3, "Communities of practice: the sustaining layer" and "What a CoP is not.")

6. **B.** Chapter 3 is explicit that a bootcamp is "concentrated, cohort-based, tool-specific" with 3–5 sessions over two weeks and Session 4's pair-with-mentor time on real work, and names "one 90-minute session on Copilot is not a bootcamp; it is a workshop with an over-ambitious scope." No cohort → no bootcamp. The chapter also names the "workshop-as-bootcamp" and the reverse as a common first-assembly mistake. (Chapter 3, "Bootcamps: concentrated cohort learning on one or two tools" and "Common mistakes when first assembling the delivery mix.")

7. **C.** Chapter 4 is explicit: **everyone gets the seat even at stage 1**, for three named reasons (door-opening friction; cohort coherence; equity signal). The variable is usage expectation, not access. Chapter 1's Failure B is prevented by Day-0 pins + Day-30 PR checkpoints, not by withholding seats. The common first-assembly mistakes section specifically names "flat usage budget per engineer" and seniority-banded policies as anti-patterns that produce stage-1 dead-weight and stage-3 throttling simultaneously. (Chapter 4, "Why everyone gets a seat even at stage 1" and "The anti-pattern: tying budget to seniority bands.")

8. **B.** Chapter 4's usage-based-pricing shape is: soft floor (no cap) at stages 1–2, team-median at stage 3, named ceiling + quarterly review at stage 4. A flat hard cap at the learning stages is the licence-drop failure in FinOps costume because it throttles the engineers for whom exploratory token-burn *is the practice*. Chapter 7's third partner failure pattern ("Platform needs to enforce a hard cap on tokens") names the counter-move: stage-sensitive alerts via the mod-104 cost tile, not hard caps. If the push continues, the Chapter 7 partnership contract's explicit-non-asks line is where escalation sits. (Chapter 4, "Handling usage-based pricing" and Chapter 7, "Three failure patterns that show up in partner interfaces.")

9. **C.** Chapter 5 is explicit that the judgment section is the highest-signal section of the pair-with-agent reflection and that reflections reading as marketing copy for the tool are negative signals (Dell'Acqua et al.'s jagged frontier is the specific finding the artifact exists to catch — "workers who out-performed were the ones who had *internalised which tasks to delegate*"). A reflection with no change-of-mind and no "what I would *not* delegate" fails the specificity and honesty guardrails. If the whole cohort writes this shape, the signal is programme-design (task too small, cohort composition, mentor pairing), not the engineer (Chapter 2's "Day-60 reflection vacuity" diagnostic). (Chapter 5, "Artifact 2 — The pair-with-agent reflection" and "Keeping the measurement honest.")

10. **C.** Chapter 6 is explicit that Bersin's research is "directional and framework-shaped, not experimental" and that "a manager who wields a Bersin cite as if it were a controlled trial is over-claiming." The responsible citation form is the *frame* ("the capability-academy pattern — cohort-based, artifact-producing, community-sustained"), paired with Work Trend Index for the "real-work context" corroboration (with its vendor-authored + self-report caveats), and the peer-reviewed productivity studies (Peng / Brynjolfsson / Dell'Acqua) cited at the *artifact* level rather than the programme-shape level. Conflating industry framework-level research with peer-reviewed quantitative studies is the specific Chapter 6 common mistake. (Chapter 6, "Josh Bersin: AI-in-L&D and the capability-academy framing" and "Common mistakes when citing.")

11. **C.** Chapter 5 is explicit that the three fluency-growth artifacts live where the team's work lives — the PR, the engineer's folder, the CoP pattern library — not in an LMS, because "the reflections drift toward LMS-formatting." A numeric rating field compounds the problem by pushing the artifact into performance-management territory, which is Chapter 5's first scoring guardrail ("the artifacts are not for performance management"). Chapter 7's example L&D partnership contract carries exactly these as explicit non-asks: "L&D does not route the three fluency-growth artifacts through the LMS" and "artifact content does not route to LMS." The LMS carries the Article 4 completion-record name-and-date only. (Chapter 5, "What this chapter is *not*" and Chapter 7, "Example: a one-page partnership contract with an L&D partner.")

12. **B.** Chapter 8 lists four graduation triggers: scope creep across teams; sustained manager delivery > 5 hrs/week; formal workforce-level compliance obligations landing at org altitude; procurement-scale budget conversations. In the scenario, triggers (1) and (2) have fired. The team-growth-from-18-to-25 signal is the specific *trap* Chapter 8 names under "What does not graduate to L45": "A larger team does not automatically mean graduation … The trigger is multi-team, not team-size." Chapter 2's overlapping-cohort model is designed to carry single-team growth up to ~30+ engineers. The right next artifact is Exercise 05's handoff contract, and if no L45 role exists, Posture A (name the gap) / Posture B (propose an interim owner) — never Posture of-becoming-L45-de-facto. (Chapter 8, "The four graduation triggers" and "What does *not* graduate to L45.")
