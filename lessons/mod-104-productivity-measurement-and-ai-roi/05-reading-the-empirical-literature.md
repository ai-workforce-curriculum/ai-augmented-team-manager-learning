# Chapter 5 — Reading the Empirical Literature as Evidence

> *You will be told that AI makes engineers 25% / 30% / 55% more productive. All three numbers come from real studies. The manager who can say which studies, on which population, measuring what endpoint, is the manager who sets the honest number for their team.*

## Motivation

R4 names the empirical literature as evidence for metric choice, not only for ROI defence. The postings expect the manager to read the primary research, not the blog posts that cite it. Five bodies of work, each cited by name in the posting language or in the curriculum scaffolding:

- **Peng et al.** on GitHub Copilot productivity ([arXiv:2302.06590](https://arxiv.org/abs/2302.06590))
- **Ziegler et al.** on Copilot productivity in Communications of the ACM ([cacm.acm.org](https://cacm.acm.org/research/measuring-github-copilots-impact-on-productivity/))
- **Noy & Zhang** on knowledge-work generative-AI productivity, Science 2023 ([science.org DOI](https://www.science.org/doi/10.1126/science.adh2586))
- **Brynjolfsson, Li, Raymond** on gain distribution across tenure (NBER WP 31161 — [nber.org/papers/w31161](https://www.nber.org/papers/w31161))
- **Dell'Acqua et al.** on the jagged technological frontier (BCG + HBS; [SSRN 4573321](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321))

The chapter's goal is not literary completeness. It is to equip you with: *what each paper actually measured, what it found, what it does not claim, and how to cite responsibly in a quarterly review.* Exercise 02 is the deliverable — your own one-page digest.

## Core concepts

### Peng et al. (2023): a controlled lab study, a single task, a large effect

**Citation.** Sida Peng, Eirini Kalliamvakou, Peter Cihon, Mert Demirer, *The Impact of AI on Developer Productivity: Evidence from GitHub Copilot*, arXiv:2302.06590, 2023.

**Design.** A randomised controlled trial. Participants (N = 95 professional developers recruited through freelance platforms) were asked to implement an HTTP server in JavaScript. Treatment group had access to Copilot; control did not. Primary endpoint: *time to task completion*.

**Finding.** The Copilot-enabled group completed the task **~55% faster** than the control group, with a reported statistically significant effect.

**What this does and does not say:**

- *It does say* that for a specific, bounded, greenfield coding task, Copilot access substantially reduced completion time in a controlled setting.
- *It does not say* that software engineers in production environments are 55% more productive. The task is single, greenfield, well-specified; real work is multi-task, brownfield, under-specified.
- *It does not say* that *every* developer sees this gain. The population is professionals recruited through freelance platforms; team-tenure, codebase-familiarity, and language-familiarity are not the primary drivers studied.

**How to cite responsibly.** "A 2023 controlled study on a bounded HTTP-server task found a ~55% completion-time improvement with Copilot access ([Peng et al. 2023](https://arxiv.org/abs/2302.06590))." Avoid: "developers are 55% more productive with Copilot."

### Ziegler et al. (Comm. ACM): observational study, acceptance rate as signal, self-report endpoint

**Citation.** Albert Ziegler, Eirini Kalliamvakou, X. Alice Li, Andrew Rice, Devon Rifkin, Shawn Simister, Ganesh Sittampalam, Edward Aftandilian, *Measuring GitHub Copilot's Impact on Productivity*, Communications of the ACM. ([cacm.acm.org](https://cacm.acm.org/research/measuring-github-copilots-impact-on-productivity/))

**Design.** A large-N observational study of Copilot usage telemetry paired with a survey. Primary endpoint: correlation between *suggestion acceptance rate* and *self-reported productivity* (SPACE-style survey).

**Finding.** Suggestion acceptance rate is the single strongest telemetry predictor of self-reported productivity — stronger than other usage metrics such as suggestions shown, lines of code generated, or raw engagement.

**What this does and does not say:**

- *It does say* that acceptance rate is a defensible *leading indicator* of developer-felt productivity when you have no better instrument available.
- *It does not say* that accepted suggestions equal shipped value. A suggestion accepted may still be wrong (`mod-103` territory).
- *It does not say* that higher acceptance rate across teams is comparable. Acceptance rate is a within-individual signal; cross-team comparisons require care.

**How to cite responsibly.** "Ziegler et al. find that suggestion acceptance rate is the strongest telemetry correlate of self-reported productivity — meaning it is a reasonable leading indicator of developer-felt experience, not of shipped output." The chapter 1 "theatre B" warning is grounded here.

### Noy & Zhang (Science, 2023): generative AI on knowledge work, writing tasks

**Citation.** Shakked Noy and Whitney Zhang, *Experimental evidence on the productivity effects of generative artificial intelligence*, Science vol. 381, 2023. ([DOI link](https://www.science.org/doi/10.1126/science.adh2586))

**Design.** A pre-registered online experiment (N = 453 college-educated professionals). Participants completed a mid-level professional writing task (press release, short report, email, analysis plan); treatment group had access to ChatGPT. Primary endpoints: *time to completion* and *output quality* (blind-graded by independent reviewers).

**Finding.** The ChatGPT group completed tasks **~40% faster** and produced **~18% higher quality** output as rated by independent graders. Quality variance within the group *decreased* — the lower-rated workers benefited more.

**What this does and does not say:**

- *It does say* that for mid-level professional writing tasks, generative AI access produced measurable gains on *both* speed and quality simultaneously.
- *It does say* that the gain was **distributed unevenly**, with lower-rated workers improving more — the earliest formal evidence of what Brynjolfsson et al. would later elaborate (next section).
- *It does not say* that this generalises to coding, operations, design, or management work. The endpoints are writing tasks.

**How to cite responsibly.** "Noy & Zhang 2023 find a ~40% time improvement and ~18% quality improvement on mid-level writing tasks, with disproportionate benefit to lower-rated workers." Useful when discussing documentation, PR descriptions, or any writing-adjacent agent use; not directly transferable to coding.

### Brynjolfsson, Li & Raymond (NBER 31161): the field study on customer-support agents, and the tenure-gain-distribution finding

**Citation.** Erik Brynjolfsson, Danielle Li, Lindsey R. Raymond, *Generative AI at Work*, NBER Working Paper 31161, 2023 (revised). ([nber.org/papers/w31161](https://www.nber.org/papers/w31161))

**Design.** A field study on a software firm's customer-support agents (N > 5,000). The firm rolled out a generative-AI-based assistant progressively; the authors used the staggered rollout to estimate causal effects. Primary endpoints: *issues resolved per hour*, *resolution rate*, *customer satisfaction*.

**Finding.** The AI assistant increased productivity by **~14% on average** (issues resolved per hour), with the gain concentrated among *low-experience workers* (34% for the least-experienced agents) and *minimal* for the most-experienced agents. Customer sentiment and retention improved as well.

**What this does and does not say:**

- *It does say* — most importantly for mod-104 — that **the productivity gain is distributed unevenly across tenure**. Junior workers benefit the most; senior workers benefit the least.
- *It does not say* that this transfers directly to software engineering. The population is customer-support agents; the task is more bounded than most engineering work. But the *shape* of the distribution has since been replicated in several contexts and is the single most important qualitative claim from the literature for a team manager.

**How to cite responsibly.** "Field evidence from a customer-support setting shows a ~14% average productivity gain, concentrated among junior workers (34% for the least-experienced tier) and much smaller for senior workers (Brynjolfsson, Li & Raymond, NBER 2023)."

**What this implies for the team dashboard.** An average productivity gain for your team is almost certainly masking a *distribution* — your juniors and your seniors are not seeing the same number. Chapter 8's qualitative instrument is where this distribution gets surfaced; Chapter 7's narrative must acknowledge it. A team ROI story that quotes only the average is miscalibrated by construction.

### Dell'Acqua et al. (BCG + HBS): the jagged frontier

**Citation.** Fabrizio Dell'Acqua, Edward McFowland III, Ethan Mollick, Hila Lifshitz-Assaf, Katherine Kellogg, Saran Rajendran, Lisa Krayer, François Candelon, Karim R. Lakhani, *Navigating the Jagged Technological Frontier: Field Experimental Evidence of the Effects of AI on Knowledge Worker Productivity and Quality*, HBS Working Paper 24-013 / SSRN 4573321, 2023. ([SSRN](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321))

**Design.** A field experiment with BCG consultants (N > 750). Participants completed one of two tasks: an "inside the AI frontier" task (one where GPT-4 is likely to perform well) and an "outside the frontier" task (one where GPT-4 is likely to produce plausible-but-wrong output). Three treatment arms: no AI, AI with basic access, AI with training.

**Finding.** On tasks *inside* the frontier, AI-assisted consultants were substantially faster and produced higher-quality work (~40% quality improvement, ~25% speed). On tasks *outside* the frontier, AI-assisted consultants were *19% more likely to produce incorrect solutions* than the no-AI control — because they trusted plausible-looking output. The authors also observe the **"centaur" vs. "cyborg"** division — consultants who treated the AI as a collaborator (centaur) vs. a work-replacement (cyborg) had different quality profiles.

**What this does and does not say:**

- *It does say* that AI assistance is **not uniformly productive**. There is a frontier; on one side the AI helps, on the other the AI reliably makes work worse.
- *It does say* that the frontier is **jagged** — not smooth, not predictable from the task's apparent difficulty. The people designing the experiment had to pre-identify inside- and outside-frontier tasks empirically.
- *It does not say* that engineers will correctly identify the frontier for their own tasks. In the study, consultants *did not* reliably tell which side of the frontier a task was on.

**How to cite responsibly.** "Dell'Acqua et al. 2023 show that AI assistance improves consultant task quality on 'inside-frontier' tasks and *degrades* it on 'outside-frontier' tasks — and that workers do not reliably identify the frontier without training (BCG + HBS field experiment)."

**What this implies for the team dashboard.** The "frontier" framing is already baked into [`mod-102`](../mod-102-team-ai-adoption-and-roadmap/) Chapter 2 as the task-sort anchor. For mod-104, the implication is the following: the average productivity number on your dashboard is a composite of *inside-frontier tasks where the gain is real* and *outside-frontier tasks where the gain is negative or theatre*. A measurement programme that does not surface the split will produce a flattering average that masks real quality erosion on specific workstreams.

### Reading the five studies together

Three cross-cutting observations survive the particulars of any single study.

- **The effect size depends on task.** Peng's ~55% is a greenfield single-task; Noy & Zhang's ~40% is writing; Brynjolfsson's ~14% is customer support; Dell'Acqua's +40%/-19% is task-side-of-frontier dependent. **There is no single AI productivity number**, and a manager who quotes one has stopped reading.
- **The distribution matters more than the mean.** Junior workers gain more (Brynjolfsson, Noy & Zhang's lower-quartile effect); task-side-of-frontier determines sign (Dell'Acqua). A reported-mean dashboard hides both.
- **Self-report and system-signal diverge.** Ziegler's acceptance-rate correlates with felt productivity; whether felt productivity correlates with shipped value is a different question none of the studies answers cleanly. This is why mod-104 composes quantitative with qualitative (Chapter 8).

### Using the literature in the quarterly narrative

Two writing moves that keep the citation honest in a one-pager:

- **Cite the finding, name the task.** *"The 55% figure from Peng et al. describes a greenfield HTTP-server task; it is a ceiling for narrow coding tasks, not a team-average claim."* One sentence buys credibility a VP will not forget.
- **Use the distribution as a feature, not a problem.** Your team's gain is distributed. Report the distribution if you can measure it (Chapter 8 qualitative instrument), and tell the team that this is what the published research shows is normal. Engineers who read the papers will see you have read them too.

### What *not* to do with the literature

- **Do not invent compound claims.** "Research shows 30% productivity improvement" without a citation is theatre. "Peng et al. 2023 found 55% on a single bounded task; Brynjolfsson et al. 2023 found 14% averaged across customer-support agents; our team's own measurement was X" is substance.
- **Do not cite industry marketing surveys as if they were peer-reviewed research.** The McKinsey / Microsoft / Gartner surveys — covered as *inputs* in [`mod-102`](../mod-102-team-ai-adoption-and-roadmap/) Chapter 4 — belong in the "industry adoption" paragraph, not in the empirical-evidence paragraph.
- **Do not let the literature freeze.** The five papers are 2023-era anchors. New work accumulates quickly; every ~4 quarters, refresh the literature digest (Exercise 02). The papers above are load-bearing; they are not the entire relevant literature a year from now.

## Example: a two-paragraph literature paragraph for the exec pre-read

Treat as calibration.

> **What the research says about AI productivity.** Published effect sizes range widely by task — Peng et al. (2023) found ~55% completion-time improvement on a greenfield HTTP-server task; Noy & Zhang (Science, 2023) found ~40% time improvement and ~18% quality improvement on mid-level writing; Brynjolfsson, Li & Raymond (NBER, 2023) found a ~14% average gain among customer-support agents, concentrated in junior workers (34% for the least-experienced tier). Dell'Acqua et al. (BCG + HBS, 2023) show that gains are positive on "inside-frontier" tasks and *negative* on "outside-frontier" tasks where models produce plausible-but-wrong output. There is no single AI productivity number.
>
> **What this team's own measurement says.** On our team, combined-tool spend was $X per 100 PRs merged over Q2; DORA change failure rate held at 11% while deployment frequency rose 15%; DX developer-experience index rose 4 points. We do not claim a published-study-sized gain for this team — the task distribution is mixed, and our two S2 incidents in Q2 both touched Dell'Acqua-style outside-frontier work (config / feature-flag changes). Our Q3 plan narrows the agent usage to the task classes where the frontier is clearest.

Two paragraphs; literature cited precisely; the team's own number is the subject, not the published study.

## Summary

- Five anchor studies to be fluent in: **Peng et al. 2023** (Copilot, bounded task, ~55% time); **Ziegler et al.** (Copilot, acceptance rate ↔ self-reported productivity); **Noy & Zhang 2023** (writing, ~40% time, ~18% quality, uneven distribution); **Brynjolfsson et al. 2023** (support agents, ~14% avg, 34% for juniors); **Dell'Acqua et al. 2023** (jagged frontier, +40%/-19%).
- Cross-cutting findings: no single "AI productivity number"; distribution over tenure and task-type matters more than the mean; self-report and system-signal diverge.
- Cite the finding and name the task. One sentence of specific citation buys credibility.
- The literature is a 2023-era anchor set; refresh the digest every ~4 quarters.
- Exercise 02 is the one-page literature digest you own.
