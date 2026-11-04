# Chapter 7 — The AI-ROI Narrative: One-Pager, Dashboard, and the "What We Got Wrong" Ritual

> *The one-pager a VP signs is not a report. It is a decision instrument. Write it so the recipient knows what to decide before they finish the second paragraph.*

## Motivation

R4's final named deliverable is the **AI-ROI narrative** — the artifact a VP, a sponsor, or an exec staff reads to make three decisions: *keep paying, grow the investment, roll some of it back*. The posting language is explicit: *"author the AI-ROI story for leadership,"* *"present the quarterly productivity story,"* *"own the narrative for the AI investment on this team."*

This chapter walks the three sub-artifacts of that narrative — the **one-pager**, the **dashboard** it reads from, and the **"what we got wrong last quarter" retro ritual** that keeps the one-pager honest over time. Exercise 04 produces the one-pager; Exercise 06 produces the retro. Chapter 2's dashboard composition is the tooling that feeds both.

## Core concepts

### The decision the narrative exists to drive

A productivity report that does not force a decision is an update. R4's posting language is specifically about *defensible spend* — this is a decision document. Three decisions it must enable:

1. **Continue.** Keep the current AI investment unchanged; signal is positive, no major concerns.
2. **Grow.** Expand (new tool, more seats, broader workflow coverage); signal is positive and the next investment is defensible.
3. **Roll back.** Narrow, pause, or cancel a specific workflow / tool / seat allocation; signal has fired one of the rollback criteria (Chapter 6).

Write the one-pager so the reader can tell within the first paragraph which decision is being asked for. "The quarter went well" is not a decision; "we recommend continuing the Copilot + Claude Code investment unchanged and expanding Cursor by 4 seats onto the data-pipeline workstream" is.

### The one-pager structure

One page. Twelve-point font. Two columns if your org's convention permits, one if not. Section headings bold; prose paragraphs short. A VP spends ~90 seconds on the first read; the structure must allow that read to be sufficient.

**Section 1 — Headline and decision (2–3 lines).** The ask, the TL;DR, and the rollback-criteria-fired statement. One sentence of each.

> *Decision asked: continue current AI investment unchanged for Q3. TL;DR: ~15% rise in deployment frequency, change failure rate flat at 11%, combined tool-spend $1,432 per 100 PRs merged; no rollback criteria fired.*

**Section 2 — The composed metric picture (one short paragraph).** DX Core 4 or your dashboard's five tiles, in prose. Lead with the throughput number; follow with the quality number; end with the cost number. Two or three sentences.

**Section 3 — What the literature predicts, and what we actually see (one short paragraph).** Cite one or two of the empirical anchors (Chapter 5) honestly. Place your team's own measurement next to the published range. Name the limits.

> *Published effect sizes range widely (Peng 2023: 55% on bounded tasks; Brynjolfsson 2023: 14% avg in support, 34% for juniors; Dell'Acqua 2023: positive inside the frontier, negative outside). Our team's composed read is consistent with a moderate real gain concentrated on well-specified feature workstreams and no gain on data-pipeline work, which matches the outside-frontier pattern.*

**Section 4 — Risks and what we got wrong (one short paragraph).** This is the single most trust-building section. Name what did not go according to plan. Specific, dated, no softening language.

> *Two S2 incidents in weeks 7 and 10 touched agent-drafted feature-flag changes — see incident log; recovery-time trend rose slightly as a result. Activation on the data-pipeline workstream is below our intended bar; we are not expanding there in Q3.*

**Section 5 — Decision ask and dependencies (3–5 lines).** The specific ask, the dollar ask (if there is one), the dependencies on other teams (platform, security, procurement, `mod-110` governance), and the next-review date.

> *Ask: continue, expand Cursor by 4 seats into the frontend workstream, pause expansion into data-pipeline pending the next frontier re-sort. Spend delta: +$1,080 / quarter. Review date: 2026-09-15.*

Five sections, one page, decision-shaped. Not a status report.

### What *not* to put on the one-pager

- *A chart of PR-count-per-engineer.* Theatre A from Chapter 1. If the dashboard behind the one-pager has it, fine; do not promote it to the one-pager.
- *A screenshot of the full dashboard.* The dashboard is the backing instrument; the one-pager is prose with numbers. Executives who want to see the dashboard will click through; the one-pager must stand on its own.
- *Every empirical study you read.* Pick one or two. The literature digest (Exercise 02) is the backing document.
- *Operational detail that belongs in the retro.* The exec pre-read is not where you process "what we got wrong" at depth. One paragraph of honest acknowledgement; the depth lives in Exercise 06's retro doc.
- *Hedged, non-committal language.* "We believe we may have seen some improvement" is a signal that you have not done the measurement work. "Deployment frequency rose 15% quarter-over-quarter" is a signal that you have.

### The dashboard that backs the one-pager

The dashboard is the *living* artifact. The one-pager is the *quarterly snapshot*. The dashboard should:

- Carry the five tiles from Chapter 2 at a glance.
- Carry the rollback-criteria tracker (are any of the four conditions in Chapter 6 near-firing?).
- Carry a "literature anchor" sidebar — a static text panel that cites the published effect ranges so an unfamiliar reader has context. Updated when the digest (Exercise 02) is refreshed.
- Carry a data-dictionary link. The dashboard's instruments are specific definitions; the definitions must be reachable in one click.

**What the dashboard should not do:** carry an AI-attribution column on every tile. Attribution happens in the one-pager's narrative paragraph, not in the tile. See Chapter 2's caveat.

The *plumbing* of the dashboard is [`ai-augmented-analyst`](https://github.com/ai-workforce-curriculum/ai-augmented-analyst-learning) (L20) work — SQL, warehouse joins, BI-tool configuration. You own the *pick* of what is on it and the *reading* of what it says. Chapter 9 draws the boundary explicitly.

### The "what we got wrong last quarter" ritual

The single most trust-building ongoing practice for the ROI narrative is a disciplined **"what we got wrong"** retro at the quarter boundary. Not a general team retro — a specific one, dedicated to the ROI story and the metric choices behind it.

**Structure (60 minutes, quarterly):**

1. *Walk the previous quarter's one-pager.* Specifically: the decision ask, the predictions, the risks named.
2. *Compare predictions to outcomes.* For each prediction ("we expect activation to rise 10pp"), write the actual outcome next to it. Keep the honest-framed language even when the number is flattering.
3. *Name the prediction misses, whether good or bad.* The symmetry matters — you build credibility by being as candid about good surprises (which signal that your prediction was conservative, which has its own cost) as about bad surprises.
4. *Identify the measurement that was lying.* If a metric moved in a direction that did not match the team's lived experience (either way), the instrument has a problem. Note it; schedule a revision for the next quarter's dashboard.
5. *Revise rollback criteria.* Chapter 6's four criteria are a starting set. Each quarter, check whether any criterion needs re-thresholding or any new one has emerged from the quarter's experience.
6. *Produce the one-paragraph follow-up.* A single paragraph goes into the next quarter's one-pager Section 4. The ritual's visible output.

**Why a dedicated retro vs. folding it into the team retro.** The team retro is about *the team's work*. The ROI retro is about *the manager's measurement work*. Different scope, different audience (you + 1–2 senior ICs or a peer manager), different tempo. A manager who conflates them ends up never doing the metric-side retro, and the one-pager drifts quietly.

Exercise 06 is the structured version of this retro and the rollback-criteria document that scaffolds it.

### How the narrative travels across the org

The one-pager has at least three readerships; each interacts with it differently.

- **The direct-upward VP or sponsor.** Signs it, uses it as the briefing document for *their* upward review, delegates the decision asks back to you. This is the primary reader.
- **The peer manager group.** Reads it for benchmarking — "how is the data team doing vs. the backend team on AI ROI." Your measurement choices should be *comparable* without being *identical* (every team's work is different); this is where `mod-102`'s and `mod-105`'s cross-team work starts to pay back.
- **The governance / finance partner.** Reads it to validate that the spend line is defensible and that the measurement programme is honest. `mod-110` (governance) and `mod-111` (budget) are the depth repositories for what they expect.

Write the one-pager for the primary reader; keep it readable to the other two. Avoid in-jokes, team-specific shorthand, or acronyms not already in common org usage.

### Common mistakes with the ROI narrative

- **Leading with the published effect size.** "McKinsey says AI will add $X trillion in value" is a slide-deck opener; it is not a team-scope narrative. Lead with *your team's own measurement* — the published work is a sidebar for context.
- **Avoiding the "what we got wrong" paragraph.** The paragraph is the single most trust-building element. Skipping it does not hide the misses; it hides them from the people reading your one-pager, which is a short-term win and a long-term credibility loss.
- **Shipping a one-pager quarterly and nothing else.** The one-pager is the summary artifact; the ongoing ritual (the retro) is where the honesty is enforced. Shipping only the summary is theatre at the quarterly cadence.
- **Not asking for a decision.** A document that could be filed and forgotten will be. Section 5's specific ask is non-optional.
- **Making the narrative about the tool, not about the team.** The tool is not the subject. The team's work, and what the tool enabled or did not enable, is.

## Example: an exec one-pager, in full

Treat as calibration. Edit for your org's house style.

> # Engineering Team Platform — AI Investment, Q2 Review
>
> **Decision asked.** Continue current Copilot + Cursor + Claude investment unchanged; expand Cursor by 4 seats into frontend; pause expansion into data-pipeline. Spend delta: +$1,080 / quarter. Review: 2026-09-15.
>
> **Metric picture (Q2).** Deployment frequency median 2.4 / engineer / week (↑ from 2.3 Q1); lead-time median 2.3 days (↓ from 2.4). Change failure rate 11% on broadened definition (flat; target ≤15%). DX developer-experience index 72/100 (↑ from 68). Flow Efficiency 19% (↑ from 17%). Combined AI tool-spend $1,432 / 100 PRs merged ($19,860 total; 1.1% of fully-loaded headcount cost; first-time measurement).
>
> **Literature and our own read.** Published effect sizes range widely (Peng 2023: 55% on bounded tasks; Brynjolfsson 2023: 14% avg in support agents with 34% for juniors; Dell'Acqua 2023: +40% inside the frontier, -19% outside). Our composed read is consistent with a moderate real gain concentrated on well-specified feature workstreams and ~no gain on data-pipeline work — matching Dell'Acqua's outside-frontier pattern. We do not claim a published-study-sized team gain.
>
> **Risks and what we got wrong.** Two S2 incidents in weeks 7 and 10 touched agent-drafted feature-flag changes; recovery-time trend rose from 1.3 to 1.4 hours. Q1 one-pager predicted 80% activation on Cursor; Q2 actual is 50% — specifically the data-pipeline cohort did not take up the tool. `mod-109` follow-up on the incidents is logged; `mod-103` review-checklist v0.2 ships week 1 of Q3.
>
> **Decision ask and dependencies.** Continue: Copilot, Claude Code, Cursor baseline. Expand: +4 Cursor seats, frontend. Pause: data-pipeline expansion pending Q3 re-sort against Dell'Acqua-style frontier task list. Depends on: Platform/DevEx bandwidth for the review-latency work targeted in the Flow Efficiency findings. Governance partner: no sign-off required; this is within approved AI-tool category. Next review: Q3 close, 2026-09-15.

One page. Five sections. Decision-shaped. Named misses. The audience knows what to decide.

## Summary

- The AI-ROI narrative is a **decision instrument**, not a status report. The reader should know within the first paragraph whether the ask is *continue / grow / roll back*.
- Three sub-artifacts: the **one-pager** (quarterly snapshot), the **backing dashboard** (ongoing instrument), and the **"what we got wrong" retro** (honesty ritual).
- The one-pager has five sections: *headline + decision*, *composed metric picture*, *literature vs. own-read*, *risks and misses*, *decision ask and dependencies*. One page, 90-second-readable.
- The backing dashboard carries the five tiles from Chapter 2, a rollback-criteria tracker, a literature-anchor sidebar, and a data-dictionary link.
- The "what we got wrong" retro is a **separate 60-minute quarterly ritual**, dedicated to the metric choices (not the team's work). Its output is one paragraph in the next quarter's Section 4.
- Three readerships: upward VP (primary), peer managers (benchmarking), governance / finance partner (validation). Write for the primary; stay readable to the other two.
- Common traps: leading with the published number, skipping the misses paragraph, no decision ask, making the narrative about the tool instead of the team.
- Exercise 04 produces the one-pager. Exercise 06 produces the retro + rollback criteria.
