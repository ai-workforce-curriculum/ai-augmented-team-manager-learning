# Chapter 8 — Qualitative Signal Against Activity Theatre

> *The quantitative dashboard will eventually drift into a story the team does not recognise. The qualitative instrument is the circuit breaker. Build it on purpose.*

## Motivation

A central claim of the mod-104 posture — Chapter 1, Chapter 2's SPACE discussion, and the "what we got wrong" ritual in Chapter 7 — is that quantitative measurement of AI productivity drifts into theatre the moment it stops being cross-checked against lived experience. SPACE's "S" dimension (Satisfaction & well-being) is the research-side acknowledgement of this; the Brynjolfsson / Noy-Zhang findings on uneven distribution (Chapter 5) are its empirical consequence. A dashboard-only measurement programme hides the distribution.

The posting language names *"retro prompts, 1:1 questions, pulse surveys"* as expected manager fluency. The qualitative instrument is not optional and it is not a nice-to-have; it is the *corrective* against the recognisable failure modes of the quantitative half.

This chapter covers *what to ask, how often, who to ask, and what to do with the answers.* Exercise 05 is the deliverable — your team's qualitative-instrument design.

## Core concepts

### The three instruments that actually work at team scope

Larger frameworks exist (quarterly engagement surveys, 360-reviews, external developer-experience audits). At the mod-104 altitude — once a quarter, with ~5–30 engineers, on an ongoing basis — three instruments carry the load.

**Instrument 1 — the AI-specific retro prompt (6-week cadence).** Three to five prompts woven into the regular team retro, specifically for AI-tool-and-workflow signal. The prompts should be *stable* (same questions every cycle) so the signal reads longitudinally.

Candidate prompt set:

- *Which AI-assisted workflow saved you the most time this cycle? Which cost you the most time?*
- *Was there a point this cycle where you trusted agent output and shouldn't have? Was there a point you didn't trust it and should have?*
- *What did your 1:1 look like with the model this cycle — what questions did you learn to stop asking it?*
- *If we had to roll one AI-assisted workflow back tomorrow, which would hurt the least?*
- *What is a task class where you believe the agent is helping other people on the team but hasn't helped you?*

Five prompts, 15–20 minutes in the retro, every 6 weeks. The specific prompts should be adapted for your team's actual tooling and workflows; the structure (one positive, one negative, one trust-calibration, one rollback-readiness, one distribution) is load-bearing.

**Instrument 2 — the standing 1:1 questions (every 2–3 1:1s).** Not every 1:1 — the signal fatigue is real. Every second or third 1:1, two questions that specifically probe the AI-work-under-this-engineer dimension.

Candidate pair:

- *When did you use AI tooling in the last week, and what came out of it? Walk me through one concrete moment, good or bad.*
- *Is there a part of your work where you feel the pressure to use AI tooling even when it is not helping? Who or what is that pressure from?*

The second question is the one most skipped and most load-bearing. Teams absorb peer pressure, manager pressure, promotion-cycle pressure to *appear* AI-fluent even when the tool is not helping their actual work. The qualitative instrument surfaces this; the dashboard never will.

**Instrument 3 — the quarterly pulse survey (quarterly, short).** 5–8 questions, 5-point-Likert-scale plus one free-text at the end. Anonymous (if your organisation's culture supports it; non-anonymous but promised-aggregate otherwise). Run as a standalone artifact, not combined with the DX developer-experience survey (the DX survey is a different instrument at different cadence).

Candidate questions:

- *"Rate the degree to which AI tooling helped you ship your most meaningful work this quarter."* (1–5)
- *"Rate the degree to which you felt pressure to use AI tooling for work where it did not help."* (1–5)
- *"Rate your confidence in the team's current review bar for AI-generated work."* (1–5)
- *"Rate your perceived risk that AI tooling is eroding a skill you need."* (1–5)
- *"Compared to last quarter, your AI-tool fluency has:"* (improved a lot / improved somewhat / unchanged / declined)
- *"What is one AI-related change you would make to this team if you could?"* (free text)

The pulse survey's job is not to produce a number for the dashboard; it is to surface the *divergences* between individual and the team average. A team-average 4.1/5 on "AI helped me ship meaningful work" with a standard deviation of 0.3 is a very different signal from a team-average 4.1/5 with a standard deviation of 1.4, and only the distribution tells you what to do.

### Reading the qualitative signal: the four failure-mode patterns

Three retro cycles + one pulse survey + two or three 1:1-question rounds in a quarter is enough signal to recognise one of four recurring patterns. Each has a specific recommended action.

**Pattern 1 — Quant up, qual up, aligned.** Dashboard shows gain; retro / 1:1 / pulse reports gain. Continue; the ROI story is robust. Chapter 7's one-pager writes itself.

**Pattern 2 — Quant up, qual flat.** Dashboard shows gain; qualitative signal flat. The specific risk: the measurement is picking up a change that the team is not experiencing as productivity. Common causes: metric defined in a way that captures a non-productivity change (e.g. PR count rose because PR sizes got smaller); Hawthorne effect wearing off; the gain is concentrated in a small subset whose lived experience dominates the number without being typical. *Action:* audit the metric definition; look at the distribution.

**Pattern 3 — Quant flat, qual down.** Dashboard flat; qualitative signal negative. The signal to catch early. Common causes: the review bar is tightening legitimately (which costs time and feels bad) but has not yet affected the shipped-output metrics; tool fatigue; one specific workflow is costing the team more time than it saves and is going uncounted. *Action:* believe the qualitative signal. Investigate before the quantitative catches up (it will). Chapter 6's rollback criteria may be close to firing.

**Pattern 4 — Quant down, qual up.** Dashboard regressing; team reports feeling good. The specific risk: the team has adopted a tool or workflow that is enjoyable but not productive. Often shows up when a new agentic tool first lands on the team. *Action:* sanity-check that the metric is right; if it is, surface the tension directly. Enjoyment is a legitimate second-order signal (well-being, retention) but is not the ROI answer.

The four patterns are not exhaustive; they are the four most common and the four every quarterly review will produce at least one of. A manager who can name the pattern their quarter sits in, and write the action in the one-pager's *What we got wrong* section honestly, has done the mod-104 work.

### The distribution question the qualitative instrument surfaces

Chapter 5's Brynjolfsson finding — gains are concentrated among junior workers — is a *distribution* finding. The dashboard reports means. The *distribution* of the team's AI gain is only visible through the qualitative instrument.

Three operational instruments for surfacing the distribution:

- **Tenure-segmented pulse-survey reading.** When you review the pulse, compute the average separately for early-tenure (< 1 yr), mid-tenure (1–3 yr), senior (3+ yr). If the pattern follows the literature (early-tenure benefits most), the *team-average* number is defensible; if it is inverted or flat, you have a specific finding.
- **Workstream-segmented 1:1 signal.** Keep notes on the 1:1 questions; segment by workstream (frontend / backend / data / infra). The jagged-frontier finding (Dell'Acqua) predicts the segmentation will be lumpy. Report the segmentation in the qualitative narrative.
- **Named-cohort retro reading.** When reviewing retro notes, mark which cohort (e.g. the data-pipeline group) raised which concerns. Patterns that appear in one cohort twice in a row are a signal to action; patterns that appear across cohorts are the team-wide picture.

A quarter's qualitative output is thus not "sentiment is positive / negative"; it is a two-sentence distributional summary. That is the input the one-pager's Section 4 ("Risks and what we got wrong") depends on.

### Governance and privacy: what you can and cannot do with qualitative output

Three principles that keep the qualitative instrument from eroding trust:

- **Anonymity promise is a contract.** If the pulse survey is promised anonymous, it is anonymous. Do not attempt to deanonymise ("Alex, your pulse survey said…"); do not report the survey at a decomposition level that effectively deanonymises (a 4-person team with a sub-cohort read on a 2-person sub-cohort is deanonymising). If your team is small enough that even the aggregate deanonymises, run the survey less frequently and at the department level only.
- **1:1 signal is confidential by default.** 1:1s are a confidential channel. Specific quotes do not go into the one-pager or the retro doc. Aggregate observations ("multiple engineers raised review-latency as a frustration") do, with your judgement that the observation is shareable.
- **Retro content is more ambiguous.** Retros happen in front of the team; what is said is not confidential in the 1:1 sense. But broadcasting a specific person's retro point upward without their explicit consent erodes retro candour over time. The norm: retro findings go upward *in aggregate* with the author's consent, or *unattributed* without it.

[`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) handles the broader data-governance posture; what matters at mod-104 is that the qualitative instrument's output is *treated as team-internal data* by default, not as a public artifact.

### What the qualitative instrument is not

- *Not a substitute for the dashboard.* Qualitative is the corrective, not the measurement. "I feel the team is more productive" without a Core 4 / DORA number is theatre in the opposite direction.
- *Not a performance-review instrument.* The retro / 1:1 / pulse is for the measurement programme. Performance evaluation uses different instruments and lives in [`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/).
- *Not a vendor-selection instrument.* The question *"which tool should we buy next"* uses different signal and is [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) work; the qualitative instrument informs it only indirectly.
- *Not a one-off.* The value is longitudinal. A single pulse survey produces a snapshot; four consecutive quarterly pulses produce a trend. The pattern recognition in the section above requires the trend.

### Common mistakes

- **Running a pulse every two weeks.** Survey fatigue is real; a biweekly pulse will degrade response rate and quality within a quarter. Quarterly is the sustainable cadence for the pulse.
- **Letting the retro prompts drift.** Prompts changing every cycle means no longitudinal signal. Keep the structure stable; vary the wording minimally.
- **Treating free-text answers as anecdote.** A single free-text answer is anecdote; three independent engineers raising the same free-text concern across a quarter is data. Aggregate, do not dismiss.
- **Collecting the qualitative signal and never citing it in the one-pager.** The qualitative instrument's job is to feed the narrative. A signal that does not travel is not functioning as a circuit breaker.
- **Running the pulse survey once and declaring the instrument working.** The instrument's value is in its iteration — question wording tightens over time; which items carry signal vs noise becomes clearer. The first run is a baseline, not a report.

## Example: a two-paragraph qualitative reading for the exec pre-read

Treat as calibration.

> **Qualitative signal, Q2.** Pulse survey (12 respondents / 14 team members, 86% response rate). Team average on "AI helped me ship my most meaningful work this quarter" = 3.8/5 (unchanged Q1). Tenure segmentation: early-tenure 4.3, mid-tenure 3.9, senior 3.1 — consistent with the Brynjolfsson pattern (Chapter 5). "Felt pressure to use AI tooling for work where it did not help" = 2.1/5 (down from 2.6 — improvement, probably attributable to the Q1 `mod-103` work normalising the review bar). Free-text themes: review-latency as the top perceived bottleneck (6 mentions across retros and the pulse), data-pipeline agent fit (3 mentions), skill-atrophy concern (2 mentions, both senior).
>
> **What the quant-vs-qual composition tells us.** The quantitative gain is real but concentrated — matches the distribution finding in the literature. Pattern 1 (aligned-up) on the feature workstreams; emerging Pattern 3 (quant flat, qual down) on the data-pipeline workstream, which is why we are pausing expansion there. The senior-cohort skill-atrophy concern feeds forward into [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/) Q3 work; the review-latency theme feeds the Flow-Efficiency work with the DevEx platform team.

Two paragraphs. Distribution surfaced. Pattern named. Decisions traced to signal.

## Summary

- Three instruments carry the qualitative half at team scope: **AI-specific retro prompts (6-week)**, **standing 1:1 questions (every 2–3 1:1s)**, **quarterly pulse survey**. Together they cost roughly 2 hours of team time / quarter plus your reading time.
- Four quant-vs-qual patterns to recognise each quarter: *aligned-up*, *quant up / qual flat*, *quant flat / qual down* (catch early), *quant down / qual up*. The pattern is the action-relevant finding.
- The qualitative instrument is the only place the *distribution* of AI gain across tenure and workstream surfaces. Chapter 5's Brynjolfsson finding is not visible on the dashboard; it is visible in the tenure-segmented pulse.
- Governance: **anonymity is a contract**, **1:1 signal is confidential**, **retro findings upward only in aggregate or unattributed**. `mod-110` is the depth repository.
- Not a substitute for the dashboard, not a performance instrument, not a vendor-selection instrument. The value is longitudinal.
- Common traps: over-frequent pulse; drifting retro prompts; dismissing free-text; collecting signal that never reaches the one-pager; declaring the instrument working on the first run.
- Exercise 05 produces your team's instrument design.
