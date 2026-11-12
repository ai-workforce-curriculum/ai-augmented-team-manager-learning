# Quiz 01 — Metrics, Cost, and AI ROI

**Format:** 12 multiple-choice questions.
**Coverage:** All nine chapters of mod-104.
**Scoring:** 1 point per question. 9/12 is a pass. Below that, re-read the chapter named in the answer explanation before moving on.

Each question tests whether you can apply the chapter, not whether you can quote it. Pick the single best answer.

---

## Question 1

Your Monday pre-read currently leads with three numbers: *"78% of engineers used Copilot this week; 42% suggestion-acceptance rate; engineers self-report 7 hours/week saved."* A VP reads it and asks, *"so what did we actually get for the licence spend?"* Per Chapter 1, the strongest critique of the dashboard is:

- A. The numbers are too old — refresh to weekly.
- B. **All three are the Chapter-1 "theatre" shapes — *adoption-count*, *suggestion-acceptance*, and *uncorrected self-reported time saved*. Each is a legitimate leading indicator but *none* is a throughput or quality number. A dashboard that stacks A, B, and C without pairing with at least one throughput metric and one quality metric that the audience can independently anchor is theatre by construction. The VP's "so what" question is diagnostic — it is the question the current dashboard is not set up to answer.**
- C. Self-reported time saved should be weighted higher because engineers are closest to the work.
- D. The dashboard is fine; the VP is asking the wrong question.

## Question 2

A skip-level manager asks, *"Can you send me the PR-count-per-engineer breakdown? I want to see who the top performers are on the AI tooling."* Per Chapter 2, the strongest response is:

- A. Send the breakdown — individual numbers are the only honest way to track activation.
- B. Refuse because PR-count is noisy; suggest commits-per-engineer instead.
- C. **Decline the decomposition in writing, grounded in the framework authors. Both SPACE (Forsgren et al. 2021) and DX's Core 4 guidance *explicitly warn* against using these dimensions for individual performance evaluation, for two reasons: Goodhart (the metric becomes a target engineers optimise for, which corrupts the behaviour within a quarter — PR-count rated engineers produce more, smaller, lower-quality PRs) and attribution (lead time / change failure / deployment frequency are team-shaped signals; decomposing them to the individual is a methodological error). The posture is not evasive; it is methodological, and it should be stated on the dashboard's "known limits" sidebar in writing.**
- D. Send the breakdown but caveat that the numbers are "directional only."

## Question 3

Your new dashboard carries five tiles: Speed, Effectiveness, Quality, Impact, and AI-cost ratio. A peer manager points out that your dashboard is "missing a column for AI-attributable productivity per engineer on each tile." Per Chapter 2, the correct move is:

- A. Add the column; AI attribution is R4's central ask.
- B. Add the column, but only to the Quality tile.
- C. **Do not add the column. Chapter 2 is explicit: "Attribution should happen in the narrative (Chapter 7), not inside every tile. A column labelled 'AI contribution %' on Change Failure Rate is theatre; a paragraph in the exec pre-read that walks the composed signal is substance." The ROI number is a composed read across the five tiles plus the cost denominator plus the qualitative signal (Chapter 8), not a per-tile percentage. The per-engineer version is the same methodological error as Question 2 at the tile altitude.**
- D. Replace Impact with "AI-attributable Impact" so there is one AI column.

## Question 4

Your team has rolled out an agentic workflow this quarter. Deployment frequency rose 15%, lead-time median dropped from 2.4 to 2.0 days, change failure rate rose from 11% to 15% on the broadened definition, and recovery-time median rose from 1.3 to 1.7 hours. Per Chapter 3, the correct reading is:

- A. "Shipped more, broke no more" — this is the defensible AI-productivity narrative.
- B. The lead-time improvement is the headline — celebrate it in the exec one-pager.
- C. **This matches Chapter 3's "Composition B — the appearances vs. reality story" (frequency ↑ and change failure rate ↑ and recovery time ↑). Change failure rate is the *load-bearing* key under AI-augmented work (Caveat 2), and the composed signal is more diagnostic than any one of the three alone. The manager-side action is almost always a `mod-103` checklist review, not a DORA investigation — the review bar from the Chapter 3 caveat is not holding. Rising recovery time (Caveat 3) also flags responder-of-record ambiguity and rollback-readiness mismatch on agent-drafted changes.**
- D. The quarter is noisy; wait another quarter before reacting.

## Question 5

A peer manager proposes narrowing the DORA change-failure definition to *"only changes the author rolled back themselves"* so that silently-broken agent-authored changes do not inflate the number. Per Chapter 3, the strongest objection is:

- A. The DORA report specifies a narrower definition, so the peer is correct.
- B. **The move is backwards. Chapter 3 is explicit: under agent-era conditions, *widen* the operational definition to include *any rollback, any hotfix within 24h, any incident-ticket raised with severity ≥ S2 attributed to the deploy*, independent of who filed it. A team whose definition is "the author raised a rollback" will miss the case where an agent-authored change broke something nobody noticed to roll back — which is precisely the agent-era failure mode the metric exists to catch. Define it explicitly; apply consistently; name it in the data-dictionary sidebar.**
- C. The definition is fine; change failure rate is a lagging indicator anyway.
- D. Replace change failure rate with recovery time instead.

## Question 6

Six weeks after rolling out Copilot and Cursor, your team's Flow Velocity rose from 11 to 14 items/sprint while Flow Efficiency dropped from 17% to 12% and Flow Load (WIP) climbed. The team *feels* busier and the dashboard looks like a win. Per Chapter 4, the correct reading is:

- A. The investment is landing — Flow Velocity rising is the signal we wanted.
- B. Flow Efficiency is a proxy for engagement; the drop is fine.
- C. **This is the specific warning Chapter 4 names: *"a team that adopts AI tooling and sees Flow Efficiency drop while Flow Velocity rises is a specific warning — the team is now producing work faster than the review pipeline can absorb it, Flow Load is climbing, and work is accumulating in a waiting state. This is a common real pattern and it is bad."* AI tooling changes the *active* side of flow (drafting, scaffolding, test-writing) but does not change the *wait* side (review latency, staging queues, cross-team blocks). The right action is removing the wait state — likely a review-latency intervention with the DevEx / Platform partner — not more AI.**
- D. Adopt the full Kersten Flow Framework to get better signal.

## Question 7

In the exec pre-read's Section 3, you want to claim an AI productivity gain for the team. A draft reads: *"Research shows 25% productivity improvement from AI tools; our team is in line with this."* Per Chapter 5, the strongest critique is:

- A. The number should be 30%, not 25%.
- B. **"Research shows 25%" is the composite-rough mis-cite Chapter 5 warns against. There is no single AI productivity number — effect sizes depend on task: Peng et al. 2023's ~55% is a greenfield single-task; Noy & Zhang's ~40% is writing; Brynjolfsson et al. 2023's ~14% is customer support with 34% for juniors; Dell'Acqua et al. 2023's +40%/-19% is task-side-of-frontier dependent. The responsible shape is "the published range is X–Y on these specific tasks; our team's own read on the same instrument is Z, for these specific reasons." One sentence of specific citation buys credibility; "research shows 25%" invites correction from any engineer who has read the papers.**
- C. Cite McKinsey's enterprise survey instead — bigger N.
- D. Drop the research citation entirely; the exec does not care.

## Question 8

Two senior ICs on the data-pipeline workstream report that the agent is making their work *worse* — they catch plausible-looking-wrong output but it costs more time to verify than it saves. The feature-team ICs are seeing strong gains on the same tool. Per Chapter 5, this is best framed as:

- A. A tool-fit issue specific to Cursor — try a different tool on data-pipeline.
- B. A training issue — the data-pipeline ICs need more agent-fluency time.
- C. **The Dell'Acqua et al. (BCG + HBS, 2023) "jagged frontier" pattern: AI assistance improves quality on "inside-frontier" tasks (~+40%) and *degrades* it on "outside-frontier" tasks (~-19% more likely to produce incorrect solutions), and workers do not reliably identify the frontier without training. The average productivity number on the dashboard is masking a composite of *inside-frontier tasks where the gain is real* and *outside-frontier tasks where the gain is negative or theatre*. The implication for the dashboard: the team's average masks the distribution; the mod-104 move is to surface the split in the qualitative narrative (Chapter 8) and to narrow the agent's scope on the data-pipeline workstream rather than invest more training against a frontier the ICs cannot reliably identify.**
- D. A minority of ICs is always slower to adopt — expect the gap to close next quarter.

## Question 9

Your first-ever adoption-vs-activation measurement shows: adoption 93%, activation (under *material-use*) 50% for Cursor. Three engineers are in the "tried-and-stopped" cohort, concentrated on the data-pipeline workstream. A peer manager suggests a reminder email and a short internal demo to push activation up. Per Chapter 6, the strongest response is:

- A. Agree — adoption-to-activation gap closure is a Chapter 6 priority.
- B. **The tried-and-stopped cohort is the *diagnostic*, not the rollout failure. These are engineers who gave the tool a real try and concluded, for their current work, it is not helping — the signal of fit issues, friction, or wrong-tool-wrong-task mismatch. The right response is a 1:1 question (Chapter 8) to surface *why* they stopped, not a nudge email. Pushing them back onto the tool will degrade trust in the measurement programme and will likely surface again as a Dell'Acqua outside-frontier pattern (Question 8) when the quarter's change-failure data lands. Chapter 6: "treat them as a signal, not as a rollout failure."**
- C. Agree only if the reminder is from the staff engineer, not the manager.
- D. Agree and also require a weekly screenshot of Cursor usage from each IC.

## Question 10

Your Q2 data: activation dropped to 28% of adopted seats on one tool for the second consecutive quarter; AI-cost ratio rose 18% QoQ while change-failure-rate is flat and Quality-tile numbers are stable. Per Chapter 6's four rollback triggers, the correct reading is:

- A. No rollback trigger has fired yet — wait another quarter.
- B. **Two of the four Chapter 6 rollback triggers have fired: (1) *activation below floor (~30%) for two consecutive quarters* — you are paying for licences the team is not using; and (2) *cost ratio moving the wrong way while Quality tile is flat* — the spend is not landing on the product line (Flow Efficiency, Chapter 4). The rollback-criteria doc exists precisely to convert the question from "are we rolling back" (identity-laden) to "did the pre-agreed condition fire" (procedural). The written criteria are what makes rollback possible without a political crisis — the doc's purpose is not to make rollback likely, it is to make it possible.**
- C. Only the first trigger has fired — activation is the only one that matters.
- D. All four triggers must fire together before rollback is justified.

## Question 11

A peer manager shows you their Q-review one-pager. It opens with *"This quarter went well across the board. We saw strong adoption of AI tooling, good team morale, and continued investment in our AI-first future."* Per Chapter 7, the strongest critique is:

- A. The tone is too cautious — add stronger claims.
- B. Add a chart to Section 1 for density.
- C. **The opening paragraph does not contain a decision. Chapter 7 is explicit that the one-pager is a *decision instrument*, not a status report — the reader should know within the first paragraph whether the ask is *continue / grow / roll back*. "The quarter went well" is a status statement; "we recommend continuing the Copilot + Claude Code investment unchanged and expanding Cursor by 4 seats onto the frontend workstream, pausing expansion onto data-pipeline" is a decision. A document that could be filed and forgotten will be; the specific ask in Section 5 is non-optional, and Section 1 must telegraph it. The hedged / non-committal language ("strong," "good," "continued") is itself a signal that the measurement work has not been done.**
- D. Replace "across the board" with "in most dimensions."

## Question 12

For two consecutive 6-week retros, your team's AI-ROI dashboard has shown stable throughput and quality numbers (quant flat). The retro signal has become increasingly negative — several ICs report that the review bar feels unsustainable and that one specific workflow costs more time than it saves. Per Chapter 8, the correct reading and action is:

- A. The dashboard is the authoritative signal; the retro is anecdotal — wait for the quant to confirm.
- B. Pattern 1 (aligned-up) — continue; the quant signal is the headline.
- C. **Pattern 3 from Chapter 8: *quant flat, qual down* — the signal to catch early. Common causes: a review-bar tightening legitimately (which costs time and feels bad) but has not yet affected the shipped-output metrics; tool fatigue; one specific workflow is costing the team more time than it saves and is going uncounted. The action is: *believe the qualitative signal. Investigate before the quantitative catches up (it will). Chapter 6's rollback criteria may be close to firing.* The qualitative instrument is the *corrective* against the recognisable failure modes of the quantitative half; dismissing it as anecdotal defeats the point of running it.**
- D. Run the pulse survey an extra time this quarter to collect more data.

---

## Answer key

1. **B.** Chapter 1 enumerates exactly three recognisable theatre shapes — adoption-count as productivity, suggestion-acceptance as output, and uncorrected self-reported time saved — and is explicit that "a dashboard that stacks A, B, and C without naming the limits of each is theatre by construction." A defensible dashboard pairs these leading indicators with at least one throughput and one quality metric the audience can independently anchor. (Chapter 1, "What 'AI theatre' looks like in a metrics dashboard.")

2. **C.** Chapter 2's "do not use for performance management" clause is load-bearing, not advisory, and grounded in both SPACE (Forsgren et al. 2021) and DX's own guidance. The two reasons the chapter names are Goodhart (any metric used for performance management becomes a target engineers optimise for, which corrupts the behaviour) and attribution (team-shaped instruments are a methodological error to decompose). The three enforcement moves are: name it in writing on the dashboard, refuse the decomposition upward, watch for the equivalent AI-attribution decomposition. (Chapter 2, "The 'do not use for performance management' clause, and how to enforce it.")

3. **C.** Chapter 2's common-mistakes section is explicit: "Letting 'AI-attributable' become a column on every tile" is a trap. Attribution happens in the narrative paragraph of the one-pager (Chapter 7), not inside every tile. A dashboard with an "AI contribution %" column on each tile is theatre; a paragraph in the exec pre-read that walks the composed signal is substance. (Chapter 2, "Common mistakes when first assembling the dashboard.")

4. **C.** Chapter 3's Composition B pattern — frequency ↑, change failure rate ↑, recovery time ↑ — is the "appearances vs. reality" signal. Change failure rate is the load-bearing key under AI-augmented work (Caveat 2) because agent-drafted diffs can look correct and ship wrong; rising recovery time (Caveat 3) is the leading indicator of agent-generated incident-response gaps (responder-of-record ambiguity, rollback-readiness mismatch). The composed read is diagnostic; the action is a `mod-103` review-bar review, not a DORA investigation. (Chapter 3, "Composing DORA with the rest of the dashboard" and Caveats 2–3.)

5. **B.** Chapter 3's Caveat 2 operational note is explicit: "A team whose definition of 'change failure' is 'the author raised a rollback' will miss the case where an agent-authored change broke something nobody noticed to roll back. Widen the definition to include *any* incident attributed to a deploy, independent of who filed it." Narrowing moves the definition the wrong way under agent-era conditions. (Chapter 3, Caveat 2 and the "Common mistakes with DORA under AI" section — "Not re-defining change failure for the agent era.")

6. **C.** Chapter 4's Flow Efficiency discussion names this pattern specifically: Velocity ↑ with Efficiency ↓ and Flow Load ↑ is the warning that AI-eased authoring is producing work faster than the review pipeline can absorb. AI tooling changes the active side of flow; it does not inherently change the wait side. The right action is to remove the wait-state bottleneck (typically a review-latency intervention with Platform / DevEx), not more AI tooling. Full-framework adoption is a trap at team scope (another chapter-4 common mistake). (Chapter 4, "Flow Efficiency under AI-augmented conditions" and "Common mistakes.")

7. **B.** Chapter 5's "What *not* to do with the literature" section names the composite-rough claim ("Research shows 25% productivity improvement") as a mis-cite. The cross-cutting finding "there is no single AI productivity number" is Chapter 5's first bullet, and the responsible citation shape — name the study, task, population, effect size, and limit — is the entire point of Exercise 02. (Chapter 5, "Reading the five studies together" and "What *not* to do with the literature.")

8. **C.** Chapter 5 on Dell'Acqua et al. names this exact pattern: "AI assistance improves consultant task quality on 'inside-frontier' tasks and *degrades* it on 'outside-frontier' tasks — and workers do not reliably identify the frontier without training." The implication for the dashboard is that a team-average number masks a composite of inside-frontier and outside-frontier work; the mod-104 move is to surface the split through the qualitative instrument (Chapter 8) and to narrow agent scope on outside-frontier workstreams rather than chase the gap closed. (Chapter 5, "Dell'Acqua et al. (BCG + HBS): the jagged frontier" and "What this implies for the team dashboard.")

9. **B.** Chapter 6 is explicit: "the *tried-and-stopped* cohort is the diagnostic. These are the engineers who gave it a real try and concluded, for their current work, it is not helping. Treat them as a signal, not as a rollout failure." The right response is a 1:1 question (Chapter 8), not a nudge email. "Treating the 'tried-and-stopped' cohort as a rollout problem" is also named in Chapter 6's common-mistakes list; the response is diagnostic, not corrective. (Chapter 6, "Adoption vs activation" and "Common mistakes.")

10. **B.** Chapter 6's four rollback triggers are: activation below floor (~30%) for two consecutive quarters; cost ratio moving the wrong way while Quality tile is flat; change failure rate rising with agent-attributable incidents; qualitative / quantitative divergence for two consecutive cycles. *Any one* of the four should trigger an explicit rollback conversation. Two have fired here. The chapter is explicit that the doc's purpose is "not to make rollback likely; it is to make rollback *possible* without a political crisis. Written criteria convert the question from 'are we rolling back' (identity-laden) to 'did the pre-agreed condition fire' (procedural)." (Chapter 6, "When to roll back the AI tool investment.")

11. **C.** Chapter 7's opening is explicit: the one-pager is a *decision instrument*, not a status report, and the reader should know within the first paragraph whether the ask is *continue / grow / roll back*. The chapter names "Hedged, non-committal language" as a signal that the measurement work has not been done, and names "Not asking for a decision" and "Making the narrative about the tool, not about the team" as common mistakes. Section 5's specific ask is non-optional; Section 1 must telegraph it. (Chapter 7, "The decision the narrative exists to drive," "What *not* to put on the one-pager," and "Common mistakes with the ROI narrative.")

12. **C.** Chapter 8's Pattern 3 (quant flat, qual down) is explicitly named "the signal to catch early." The correct action is to *believe the qualitative signal and investigate before the quantitative catches up*, and the chapter notes that Chapter 6's rollback criteria may be close to firing. The "dashboard is authoritative / qualitative is anecdotal" frame is the specific trap Chapter 8 was written to counter — a dashboard-only measurement programme hides the distribution, and the qualitative instrument is the circuit breaker, not a decorative supplement. (Chapter 8, "Reading the qualitative signal: the four failure-mode patterns" and the chapter's opening framing.)
