# Chapter 2 — Brynjolfsson, Li, Raymond and the Growth-Path Channel

> *The first thing AI changes is who learns fastest on your team. The gains concentrate in your junior ICs. The question Brynjolfsson, Li, and Raymond leave for the manager: are those ICs learning the thing the AI is doing for them, or are they learning to be good consumers of a model whose errors they cannot yet see?*

## Motivation

[Brynjolfsson, Li, Raymond, *Generative AI at Work* (NBER WP 31161, 2023 — revised 2024)](https://www.nber.org/papers/w31161) is the first large-scale real-deployment study of a generative-AI tool in production use. Unlike experimental studies that stage realistic tasks (Noy & Zhang, Chapter 3) or simulate one (Dell'Acqua et al., Chapter 4), this study observes >5,000 customer-support agents over a year of actual work, with a staged rollout producing a natural experiment on productivity.

The headline finding — productivity gains concentrate at low-tenure and low-skilled workers — is what the posting language and the industry press most often cite. The *managerial* finding is the question it leaves open: when the AI does the routine work on behalf of your junior ICs, and ships their output successfully for 18 months, what skill are those ICs actually accumulating? This chapter reads the paper at manager-fluency and translates the finding into the first of the three team-level policies this module will compose.

## Core concepts

### Reading the paper at manager-fluency

The study was conducted at a large US-based business-process outsourcing firm whose agents handle customer-support contacts for software products. The AI assistant is a conversational suggestion tool: it watches an ongoing customer chat, drafts responses for the agent, and summarises prior turns. Rollout was staged across agent teams and time, producing a difference-in-differences identification strategy. The sample is ~5,179 agents observed over ~12 months.

**Finding 1 — the average productivity effect.** Access to the AI assistant increases *issues resolved per hour* by roughly **14%** on average (the paper reports the specific number and full regression; the point estimate is in that range in the published versions). The effect is stable across operational-productivity measures (resolution time, number of chats handled) and is accompanied by a modest improvement in customer-sentiment measures.

**Finding 2 — the distributional effect.** The average masks a sharp distributional pattern. Gains are **concentrated at lower-tenure and lower-skilled agents**. The paper reports that agents in the lowest-skill quintile improve dramatically; agents in the highest-skill quintile improve little or not at all. The pattern holds whether skill is measured by prior-period productivity, by tenure, or by prior-period customer-sentiment scores. <!-- needs-research: the paper reports a specific quintile-level breakout; the text here cites the pattern qualitatively. Confirm the exact quintile numbers against the most recent published revision before putting them on a one-pager. -->

**Finding 3 — the mechanism the paper proposes.** The authors interpret the pattern as AI disseminating the implicit knowledge of the top performers across the rest of the workforce. The model has been trained, in part, on the outputs of high-performing agents; it surfaces what those agents would have done. The bottom of the distribution benefits because the model is handing them the high-performer playbook in-flight. The top of the distribution benefits little because they already know the playbook.

**Finding 4 — the second-order effect this module cares about most.** The paper also reports that AI access is associated with lower attrition, higher agent-reported job satisfaction, and a smaller promotion-related tenure gap. The *productivity* channel is one finding; the *workforce dynamics* channel is a second finding the paper explicitly discusses. Managers sometimes cite the productivity result and ignore the workforce-dynamics result; for this module, the workforce-dynamics result is the load-bearing one.

### What the finding does *not* say

Three limits worth internalising so you cite responsibly:

- **It is a study of customer-support work.** The task — reading an incoming chat, drafting a response grounded in product knowledge — is a knowledge-work task, not a software-engineering task. Generalising the quintile-level numbers to an engineering team is an extrapolation, not a cite. The *pattern* — gains concentrated at low tenure — is robust across the other two studies in this module and is defensible as a general manager-time claim; the *specific percentages* are not.
- **It measures productivity, not skill accumulation.** The paper reports outputs per hour, not the counterfactual *"what would these agents know in two years without AI access?"* The growth-path concern is what the data *allows you to be concerned about*, not a direct measurement. Chapter 4 (Dell'Acqua) is the closer measurement of the deskill channel.
- **It is a within-firm study.** The AI assistant was deployed by the firm, with the firm's training data and the firm's workflow around it. A different firm's deployment — with less rigorous training-data curation, worse prompt discipline, or a less-engaged workforce — could see different distributional effects. The Microsoft Research extension to this work on customer-support AI deployments is consistent in direction but varies in magnitude.

### Translating Finding 2 into a team-level policy move

The distributional pattern is the finding you act on. Three ways it reshapes the team manager's work:

**Policy move 1 — the junior-IC growth plan is now the load-bearing artifact.** Before AI, a junior IC's growth followed from exposure — they saw problems, tried solutions, had the reviewer catch the mistakes, learned from the catch. The growth was a side effect of the work. After AI, the exposure is mediated — the model absorbs the first-draft mistakes before the reviewer sees the artifact. The growth has to be *designed* because it no longer falls out of the work naturally. Exercise 05 (IC development-plan template refresh) is the operational response. The IDP changes shape: it now names the *judgement moves* the IC is building capacity on, with artifacts that would evidence growth even when the output quality is already acceptable.

**Policy move 2 — the first 12 months of a junior IC's tenure are now a design problem, not a default.** The onboarding path the team ran for its previous cohort — pair rotation, incremental ticket complexity, supervised code reviews — assumed AI was absent. With AI present, several steps on that path are compressed. The 2024 onboarding plan is not a reasonable 2026 onboarding plan. mod-105 Chapter 2 named the Day 0 / 30 / 60 / 90 structure for AI *fluency*; mod-107's addition is that the same structure needs a *skill-formation* overlay — specific learning milestones that are not satisfied by shipping AI-assisted output.

**Policy move 3 — the senior IC's role shifts from *shipping* to *teaching and reviewing*, and the team's structure should reflect it.** If AI gains concentrate at the bottom of the distribution, the senior IC's relative contribution to raw output volume compresses. The senior's leverage increasingly comes from their teaching and review work, not their individual shipping. The career ladder (Chapter 6) must reward this work explicitly; the carve-outs (Chapter 5) must schedule it; the one-pager measurement work in [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) Chapter 4 must surface it.

### The failure mode this chapter flags for Chapter 5

The paper's findings predict a specific failure mode the carve-outs in Chapter 5 are designed to prevent. The failure sequence runs:

1. AI is adopted; junior ICs ship work that passes review from Day 1.
2. Reviewers, time-pressured, confirm that the output is correct without probing whether the IC could *re-derive* it.
3. The IC's measured output quality is good; their internal mental model is thinner than it would be without AI.
4. Nine months pass. The team's dashboards show improvement. The IC receives reasonable feedback in 1:1s.
5. A problem arrives — an outside-frontier problem, in Dell'Acqua's language — for which the AI's suggestion is plausibly-wrong. The IC ships the suggestion. Review misses it. Incident.

The failure is the *compound* of Brynjolfsson's growth-path channel (the IC never built the model) and Dell'Acqua's deference channel (the IC does not know to doubt the AI). Chapter 5's carve-outs are explicitly designed to break step 2 — reviewers probe for re-derivation, the IC produces at least one solo-authored artifact per quarter, and the judgement question becomes a first-class review move.

### What this means for hiring (handoff to mod-108)

Two changes in interview-loop composition follow from the Brynjolfsson finding; mod-108 is the detailed treatment and this chapter names only the handoff.

- The *skill floor* for junior-IC hires is now higher-leverage per dollar of comp, because the AI will carry more of their first-year productivity. But the *skill ceiling* trajectory is lower if the growth plan is not designed well — making the Day-0-to-Day-365 design explicit at hiring time is now the differentiator.
- The *judgement question* needs its own interview signal. Interviewing for "can this candidate write the code" is a lower-signal question than before; the model will write much of the code. Interviewing for "can this candidate tell when the model is wrong" is the question to add.

Both are mod-108 content; mod-107's job here is to ensure the growth plan and the career ladder align with the signal the interview is now trying to catch.

### Common mistakes when citing this paper

- **Citing the 14% number without the distributional context.** The 14% average is the least interesting finding for a manager. The distributional pattern is the finding; cite that.
- **Citing it as if the agents are software engineers.** The generalisation from customer-support to engineering is defensible at the *pattern* level and not at the *percentage* level. Be explicit about which.
- **Treating "AI lifts the bottom" as an unqualified win.** The lift is real and valuable. The *curve of skill growth under the lift* is the thing the manager is now responsible for shaping; the lift itself does not shape it.
- **Ignoring the workforce-dynamics finding.** The attrition and satisfaction channel is the finding that most changes the team manager's job. If your cite ends with "productivity went up," you have stopped reading the paper too early.
- **Conflating "AI narrows skill gap" with "AI eliminates the need for senior ICs."** The paper does not say or imply this. The reverse is closer to what the paper implies: senior ICs become the source of the *judgement signal* that keeps the AI-mediated output honest.

## Example: using Finding 2 to justify a change in Day-30 check-in

An IC team adopts an AI coding assistant. The manager rewrites the Day-30 check-in for new-hire junior ICs. Before:

> *Day-30 check-in: review the first PR, confirm the engineer is on track, confirm no blockers, confirm the mentor pairing is working.*

After, citing Finding 2 as the rationale in the growth-plan memo:

> *Day-30 check-in: review the first solo-authored artifact (no AI assistance for a specific, scoped, low-stakes task) alongside the first AI-assisted PR; ask the engineer to narrate the two differently — what they could have done unassisted, and what the AI changed about the artifact. Confirm the mentor pairing is working, confirm the engineer has pushed back on an AI suggestion at least once in the prior two weeks, and name the next deliberate-practice carve-out on the calendar.*

The change is small. It is specifically grounded in Finding 2: because the AI will carry the junior IC's first-30-day productivity, the Day-30 instrument has to probe for the growth channel that the output itself no longer surfaces. Exercise 01 produces the memo that justifies this pattern of change across every growth-plan artifact on the team.

## Summary

- [Brynjolfsson, Li, Raymond (NBER WP 31161)](https://www.nber.org/papers/w31161) is a >5,000-agent natural-experiment study at a customer-support firm with staged AI-assistant rollout.
- **Headline finding:** ~14% productivity lift on average, concentrated at lower-tenure and lower-skilled agents.
- **Load-bearing finding for mod-107:** the *distributional* pattern — AI gains concentrate at the bottom of the skill distribution, and the workforce-dynamics channel (attrition, satisfaction, promotion tenure gap) is a distinct and real second-order effect.
- **Three team-level policy moves:** (a) make the junior-IC growth plan the load-bearing artifact, (b) redesign onboarding as a skill-formation plan, not a tool-fluency plan, (c) reward and schedule the senior IC's teaching and review work explicitly.
- **Failure mode flagged for Chapter 5:** reviewers do not probe for re-derivation; the IC ships good AI-assisted output; the internal model does not form; outside-frontier failure arrives 9–18 months later.
- **Cite responsibly:** quote the pattern, not the specific percentage, when generalising beyond customer-support work; include the workforce-dynamics channel in every citation; do not treat the lift as self-executing on skill growth.
