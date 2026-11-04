# Exercise 04 — The AI-ROI Story for the Exec Pre-Read

**Estimated effort:** 3 hours.

## Objective

Author the **AI-ROI one-pager** your sponsor (VP-of-engineering, CTO staff, or equivalent) would read 24 hours before your quarterly review, using the five-section structure from Chapter 7. The output is a single Markdown file (`docs/ai-roi-one-pager-[YYYY-QN].md`) that is decision-shaped, defensible, and reads in ~90 seconds.

This is the central synthesis artifact of the module. Exercises 01–03 feed into it; Exercises 05–06 keep it honest over time.

## Prerequisites

- Chapters 1, 2, 5, 6, 7 of this module.
- Exercise 01 complete (you have the metric crosswalk; your dashboard tiles are picked).
- Exercise 02 complete (you have the literature digest; you can cite responsibly).
- Exercise 03 complete (you have the reconciled cost and activation numbers).
- Enough quarter-to-date data to populate at least four of the five tiles. If you are joining mid-quarter and your first one-pager will be partial, name the partial-data status explicitly and write the one-pager anyway — the draft is a muscle.
- Chapter 6 of [`mod-102`](../../mod-102-team-ai-adoption-and-roadmap/) if you have gone through it — the adoption-artifact one-pager shares DNA with this one.

## Problem statement

The one-pager is the single most-read artifact of the mod-104 programme and the most likely to be judged. A manager who ships a technically dense, qualified, hedged, non-decision-shaped three-page memo has produced an update, not a decision document. A manager who ships a decision-shaped one-pager with the "what we got wrong" paragraph intact has produced the artifact the postings pay for.

Your job is the latter. You are writing for your actual sponsor (not a composite executive), about your actual team (not an aspirational one), for the actual next quarter's decisions. Keep it concrete.

## Steps

1. **Identify the actual sponsor.** By name. What decisions do they make, on what cadence, and what format do they prefer? If their house style is a slide deck, you will attach the one-pager as the backing doc; if it is a doc, the one-pager *is* the artifact.
2. **Write Section 1 (Headline and decision ask) first.** Three lines. The ask (continue / grow / roll back a specific thing), the TL;DR of the metric picture, and whether any rollback criterion has fired. If Section 1 does not read as a decision ask, go back and rewrite.
3. **Write Section 2 (Composed metric picture).** One short paragraph using the five tiles from Exercise 01. Lead with throughput, follow with quality, end with cost. Three to five sentences.
4. **Write Section 3 (Literature and own-read).** One short paragraph citing one or two anchors from Exercise 02. Place your team's own measurement next to the published range. Call out the known limits of the signal. 3–5 sentences.
5. **Write Section 4 (Risks and what we got wrong).** One short paragraph, honest. Include at least one specific thing that went differently from Q-1's prediction, whether positively or negatively. If this is your first one-pager, include at least one thing that did not go according to plan this quarter — there will be something.
6. **Write Section 5 (Decision ask and dependencies).** 3–5 lines. The specific ask, the specific dollar amount (if applicable), the dependencies on platform / security / procurement / governance, the next review date.
7. **Format to one page.** 12-point font, standard margins. If it does not fit, cut; do not shrink the type.
8. **Dry-run on your actual sponsor.** Not for sign-off — for read-through. Spend 90 seconds timing their read. Ask: *after reading this, what did you understand we are asking for? Did anything confuse you? What did you expect to see that was not here?* Note their answer.
9. **Revise.** The most common revisions after the first dry-run: Section 1 was not decision-shaped (rewrite); Section 4 was too soft (add specificity); Section 2 led with an activity metric instead of throughput (reorder).
10. **Freeze v1 for the quarter.** Title: `AI-ROI One-Pager — [team] — [YYYY-QN]`. Date, author, dependencies on Exercise 01 / 02 / 03 artifacts listed by path.
11. **Schedule the next-quarter refresh.** The one-pager is quarterly. Put the draft date for Q+1 on your calendar — ideally 1 week before the Q-review so the dry-run has time.

## Starter guidance

- A reader who finishes the first sentence should be able to tell you what decision you are asking for. If they cannot, Section 1 has failed.
- Use specific numbers everywhere. "Deployment frequency rose 15%" is a number; "deployment frequency improved" is a hedge.
- Cite the literature once in the one-pager, and specifically. "The published range is Peng's 55% on bounded tasks to Brynjolfsson's 14% average in support; our team's composed read is X" is the pattern. "Studies show AI helps" is theatre.
- Section 4 is non-optional and non-softening. If your draft's Section 4 reads positively, you have not written honestly. Every quarter has misses worth naming.
- Do not promote the dashboard into the one-pager. The dashboard is the backing instrument; the one-pager is the narrative. A one-pager with four charts is not a one-pager.
- Make the decision ask *actionable*. "Continue the Copilot investment" is actionable only if there is an alternative being considered; otherwise it is a status statement. "Continue Copilot, expand Cursor by 4 seats on frontend, pause expansion on data-pipeline" is actionable.
- The one-pager is not where product-feature ROI goes. If your team shipped an AI-powered product feature this quarter, acknowledge it as a dependency / collaboration artifact; the product-ROI story is in the PM's one-pager (Chapter 9).
- If your organisation has a house template for executive pre-reads, use it. Chapter 7's structure fits inside most house templates; do not fight the house style for the sake of this exercise.

## Acceptance criteria

The one-pager is complete when:

- The artifact is exactly one page in your organisation's preferred font / margins (or two, if your house style is for a longer brief — document the choice).
- Five sections are present in the order: headline + decision ask; composed metric picture; literature and own-read; risks and what we got wrong; decision ask and dependencies.
- Section 1 contains a concrete decision ask that the reader can act on. "Continue" is a legitimate ask only if there is a stated alternative.
- Section 2 uses specific numbers for throughput, quality, developer experience, and cost. The order is throughput → quality → cost.
- Section 3 cites one or two specific empirical anchors from Exercise 02; your team's own number sits next to them.
- Section 4 names at least one specific miss. "Everything went well" is not acceptable.
- Section 5 names a dollar delta (or explicitly "zero"), partner dependencies, and a next-review date.
- Rollback-criteria status is stated in Section 1 or Section 4.
- At least one dry-run with the actual sponsor is complete and revisions reflect the feedback.
- The artifact is titled, dated, lists contributors and backing artifact paths, and lists the next-quarter draft date.

## Stretch goals

- **Side-by-side with Q-1.** When this is your second or later one-pager, lay the Q-1 and Q-N versions next to each other. Compare the Section 4 predictions from Q-1 to the outcomes in Q-N; use the comparison to *strengthen* the credibility of this quarter's Section 3 and 4.
- **Dashboard back-link audit.** For every number in the one-pager, verify there is a dashboard tile or a backing-artifact link that produces it. A number without a traceable source is a liability.
- **Peer manager review.** Before the sponsor dry-run, swap with a peer manager and read each other's one-pagers. Specifically ask: *does my Section 4 feel honest to you, or is there a miss I am smoothing?* Peer managers catch smoothing you cannot see.
- **The "what if the sponsor skips Sections 2 and 3" test.** A 90-second read is often a 30-second read. Does Section 1 alone carry the ask? If not, Section 1 is too dense; cut.
- **Rollback-case drill.** Write a parallel version of the one-pager in which the ask is *roll back a specific tool*. Run through the exercise end-to-end. The rollback one-pager will be easier to produce in a real crisis if you have rehearsed it; Exercise 06 formalises the rollback-criteria half.
- **Prepare a 3-minute verbal version.** The spoken version of the one-pager should be ~3 minutes, same structure. Rehearse it. Executives frequently skip the written artifact and expect the live summary.
