# Exercise 02 — Empirical Literature Read-and-Digest

**Estimated effort:** 3 hours.

## Objective

Produce a **one-page literature digest** of the five empirical anchor studies named in Chapter 5 — Peng et al. (2023), Ziegler et al. (CACM), Noy & Zhang (Science, 2023), Brynjolfsson, Li & Raymond (NBER 31161), Dell'Acqua et al. (BCG + HBS) — written *for your own reuse* in the Exercise 04 one-pager and in Q-review conversations. The output is a single Markdown file (`docs/ai-literature-digest.md` or equivalent) with one short block per study and a short cross-cutting-findings paragraph at the end.

This exercise exists to *equip you to cite the literature responsibly*, not to produce an academic literature review. A manager who can cite Peng et al. 2023 *and* name the task constraints that make it a bounded claim stops making careless comparisons.

## Prerequisites

- Chapter 5 of this module.
- The five primary papers themselves. Links:
  - Peng et al., [arXiv:2302.06590](https://arxiv.org/abs/2302.06590).
  - Ziegler et al., [Communications of the ACM](https://cacm.acm.org/research/measuring-github-copilots-impact-on-productivity/).
  - Noy & Zhang, [Science DOI: 10.1126/science.adh2586](https://www.science.org/doi/10.1126/science.adh2586) (abstract is public; full text via institutional access).
  - Brynjolfsson, Li & Raymond, [NBER Working Paper 31161](https://www.nber.org/papers/w31161).
  - Dell'Acqua et al., [SSRN 4573321](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321).
- 2–3 hours of uninterrupted reading time. The digest is not a model-draftable output; you should have read the primary sources yourself, with the assistance limit of Chapter 5 of [`mod-101`](../../mod-101-ai-augmented-team-manager-position-and-contract/) on model-assisted reading (model can help index; the understanding has to be yours).

## Problem statement

Teams repeatedly see "AI adds 25–55% productivity" numbers surface in exec decks and peer-manager Slacks. Several of the numbers are real; most are mis-cited. A manager who can pick the correct specific study, name the task, name the population, name the endpoint, and name the limit in one sentence has disproportionate credibility in the ROI conversation.

Your job is to produce your own one-page digest — not a copy of Chapter 5, but your *own* restatement of each study — so that when the moment comes to cite one in a VP conversation, the sentence is available and the backing understanding is yours.

## Steps

1. **Read Peng et al. (2023).** Note down: task, N, controls, primary endpoint, effect size, confidence interval (if reported), the study's explicit limits.
2. **Read Ziegler et al. (CACM).** Note down: methodology (observational vs experimental), telemetry variable identified as strongest correlate, endpoint (self-reported SPACE-style survey), reported effect, explicit limits.
3. **Read Noy & Zhang (Science, 2023).** Note down: task domain, N, treatment vs control, endpoints (time and quality, graded blind), effect size, the distribution finding (lower-rated workers benefit more).
4. **Read Brynjolfsson, Li & Raymond (NBER 31161).** Note down: setting (customer-support firm), N, identification strategy (staggered rollout), primary endpoint, average effect, tenure-distribution effect, downstream effects (satisfaction, retention).
5. **Read Dell'Acqua et al. (BCG + HBS).** Note down: population (BCG consultants), N, inside-vs-outside-frontier task design, effect inside, effect outside, the centaur/cyborg observation.
6. **Draft the digest.** For each study, write one short paragraph (4–6 sentences) in your own words. Structure of each paragraph:
   - Citation + venue.
   - One sentence on the design.
   - One sentence on the finding (with specific effect size).
   - One sentence on what the finding does *not* claim (the scope limit).
   - One sentence on how you will cite it — the specific one-sentence version you will use in future conversation.
7. **Write the cross-cutting paragraph.** 3–5 sentences summarising the *three* findings that survive across the studies: no single AI productivity number; distribution matters more than mean; self-report vs system-signal diverge. Cite each cross-cutting finding to the studies that support it.
8. **Add a "my own team's own measurement vs. these published ranges" section.** Even if you have not completed Exercise 03 / 04, write a placeholder paragraph saying *"when our Q-X measurement is complete, this is where its number goes."* The placeholder forces you to design the digest for reuse.
9. **Date it and schedule the refresh.** Add a header line: *"this digest is refreshed on [date, ~4 quarters out]."* Add the date to your calendar. The AI research landscape moves; this digest will be stale in a year.
10. **Walk the digest to one peer** who has not read all five papers. Specifically ask: *does my one-sentence citation for each study tell you what the study claims without being misleading?* Revise where their reading diverges from your intent.

## Starter guidance

- Favour your own words over quoted language. A one-sentence restatement that uses your own vocabulary is far more reusable than a quote you will not remember to attribute.
- Resist adding more studies. Chapter 5 anchors on five; your digest should also anchor on five. A digest of twenty studies is a literature review, not a decision-ready brief.
- For each study, the *hardest* sentence to write is "what the finding does not claim." That sentence is the one that saves you from mis-citation in practice. Spend disproportionate time on it.
- The one-sentence citation form matters. "Peng et al. (2023) found Copilot-enabled developers completed a bounded HTTP-server task ~55% faster than controls" is defensible. "Peng et al. found developers are 55% faster with Copilot" is the mis-cite the digest is supposed to prevent.
- If you have institutional access to secondary systematic reviews of generative-AI productivity research, read one as a cross-check — but keep the digest based on the five primary papers. Secondary sources drift fast and attribute carelessly.

## Acceptance criteria

The digest is complete when:

- Five short paragraphs, one per anchor study, each containing: citation + venue, design, finding with effect size, scope limit, one-sentence citation form.
- A cross-cutting paragraph (3–5 sentences) names at least the three findings: no single number; distribution over mean; self-report / system-signal divergence. Each cross-cutting claim is attributed to specific studies.
- A placeholder section exists for "this team's own measurement vs. published ranges" even if it is not filled in yet.
- The digest has a refresh date, roughly 4 quarters out, scheduled in your calendar.
- One peer has walked the digest and confirmed each one-sentence citation reads correctly without misleading.
- The digest fits on one page (12-point font, standard margins) — or two pages if your org's convention is for a longer brief.
- Each study's "what the finding does not claim" sentence is present and specific.
- Composite rough claims ("research shows AI helps") do not appear anywhere.

## Stretch goals

- **Replication / refutation scan.** For each of the five anchor studies, spend 20 minutes searching Google Scholar for subsequent work that replicates, extends, or refutes the finding. Note the state of the replication in a one-line comment on each study.
- **Operationalise the Brynjolfsson distribution finding on your own team.** Segment your Exercise 03 / 05 output by tenure (or proxies if tenure-data is sensitive). Add the comparison to the "own measurement" section as it develops.
- **Operationalise the Dell'Acqua frontier finding.** List the three task-classes your team ships most, and classify each (speculative is fine for the first pass) as inside / outside the current jagged frontier. Feed the classification into [`mod-102`](../../mod-102-team-ai-adoption-and-roadmap/) Chapter 2's task-sort work.
- **Peer swap.** Exchange digests with a peer manager in a different organisation (e.g. via your personal network). Compare which one-sentence citation forms you each use for the same study; adopt improvements.
- **Add the industry-survey caveat.** At the bottom of the digest, add one paragraph noting *"the following are industry surveys, not peer-reviewed research, and belong in the adoption paragraph rather than the empirical-evidence paragraph: Microsoft Work Trend Index, McKinsey State of AI, GitHub Octoverse, Stack Overflow Developer Survey, WEF Future of Jobs."* This matches the posture in [`mod-102`](../../mod-102-team-ai-adoption-and-roadmap/) Chapter 4 and keeps the citation discipline clean.
