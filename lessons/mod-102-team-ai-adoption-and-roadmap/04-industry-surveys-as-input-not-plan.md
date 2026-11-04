# Chapter 4 — Industry Surveys as Input, Not as Your Plan

> *"The survey tells you what other teams are doing. Your team is not the average team."*

## Motivation

Every quarter, four or five high-profile industry surveys drop on this topic: Microsoft's *Work Trend Index* ([link](https://www.microsoft.com/en-us/worklab/work-trend-index)), McKinsey's *State of AI* ([link](https://www.mckinsey.com/capabilities/quantumblack/our-insights/the-state-of-ai)), GitHub's *Octoverse* ([link](https://github.blog/news-insights/octoverse/)), Stack Overflow's *Developer Survey* ([link](https://survey.stackoverflow.co/)), and periodically WEF *Future of Jobs* ([link](https://www.weforum.org/publications/the-future-of-jobs-report-2025/)), the OECD's future-of-work briefings ([link](https://www.oecd.org/future-of-work/)), Gartner AI research ([link](https://www.gartner.com/en/topics/artificial-intelligence)), and academic reports from MIT Sloan Management Review and the like. Leadership forwards them to you. Your inbox turns into a highlight-reel of other people's adoption stories.

Two failure modes result. The common one: you copy the survey's narrative into your roadmap verbatim — "75% of knowledge workers use AI; we will too" — and end up with a plan that is not anchored in your team's actual tasks. The rarer but more expensive one: you ignore the survey data entirely, and later get asked by a VP, "what does the industry say?" and have no answer. This chapter is the discipline that keeps both from happening.

## Core concepts

### What the surveys do well, and what they do not

Each survey has a specific population, sample, and question set. Reading them as a group — triangulating rather than trusting any one — is the discipline.

- **Microsoft *Work Trend Index***. Broad knowledge-worker population (tens of thousands of respondents across many countries); strong on *how* workers use AI tools day-to-day, especially Microsoft 365 Copilot. Useful for: directional signals on knowledge-worker AI usage, patterns of "bring your own AI," and friction with managers and policy. Less useful for: deep engineering-task specifics; organisational-level rollout decisions; discipline-specific breakdowns.
- **McKinsey *State of AI***. Enterprise-executive population (hundreds to a few thousand respondents, C-suite and function leaders); strong on *where* organisations are deploying GenAI, cost patterns, and governance maturity. Useful for: leadership-facing framing of your roadmap. Less useful for: the day-to-day IC-workflow level you actually manage at.
- **GitHub *Octoverse***. Developer-behaviour population (millions of developers via GitHub telemetry + survey overlay); strong on *what* developers are doing at scale — language usage, repo activity, Copilot adoption in aggregate, open-source trends. Useful for: calibrating your team's engineering practice against the global baseline. Less useful for: non-engineering disciplines; management-practice questions.
- **Stack Overflow *Developer Survey***. Developer-sentiment population (tens of thousands of respondents, self-selected community); strong on *what developers think* of AI tools — trust, satisfaction, intent-to-use. Useful for: anticipating your team's sentiment and the "cool / not cool" dynamics of a given tool. Less useful for: measured productivity or quality outcomes.
- **Academic empirical research** (Peng et al. on Copilot; Noy & Zhang on writing; Brynjolfsson, Li & Raymond on customer-service; Dell'Acqua et al. on consultants). Narrower populations, random assignment, quantified outcomes. Useful for: the strongest available causal claims about AI's effect on specific task classes. Less useful for: breadth-of-adoption narratives (that is what the surveys are for).

No single source is "the" source. The useful read is the *intersection* — where two or three of the surveys agree, you can treat the signal as reasonably stable; where they disagree, the disagreement itself is information.

### Three failure modes to avoid

1. **Copy the headline into the plan.** "75% of workers use AI, so our team will" is not a plan. It is the setup for the plan. The plan is what tasks go onto an AI-augmented path on your team *given* your team's context, risk posture, and task sort.
2. **Trust a single data point.** Survey respondents self-select; survey definitions vary across years; survey wording shapes answers. Any single "X% of teams do Y" line is weak evidence on its own. Report ranges, not point estimates.
3. **Ignore the surveys because they are "marketing."** Each of the four named surveys publishes methodology; each is imperfect; none are pure marketing. "Marketing bias" is a reason to read them critically, not a reason to drop them. The thing to drop is the executive summary; read the method and the per-industry breakdown instead.

### Four questions to ask of any survey before quoting it

Before a survey number lands in your roadmap or in an exec pre-read, answer these for yourself:

1. **Who is in the sample?** Role, size, geography, industry. Is my team in that sample? If not, is the finding transferable?
2. **How is the key term defined?** "Uses AI at work" could mean "has typed into ChatGPT once" or "ships daily AI-drafted code." The headline rarely carries that nuance; the methodology section does.
3. **Compared to what?** Is this a *change* from last year's number, a *cross-sectional* snapshot, or a *correlation* dressed up as an effect? Correlations are useful; they are not causation.
4. **Does the finding match the other surveys and the academic empirical research?** If MS WTI, Stack Overflow, Octoverse, and the Copilot productivity study agree directionally, the signal is relatively robust. If only one says it, treat it as hypothesis-grade.

A number that survives these four questions is worth putting in your exec pre-read. A number that does not is worth leaving out.

### Using surveys to pressure-test your task sort

This is the most useful move in the chapter. Take the Chapter 2 task sort — your AI-first / AI-assisted / human-led / pilot-candidate buckets — and ask against each surveyed source:

- **What does the Microsoft Work Trend Index say about this category of work across the broader knowledge-worker population?** Are workers already doing it with AI, or not yet? If workers are, but your team is not, why?
- **What does the Stack Overflow Developer Survey say about developer sentiment on the tool you are about to pilot?** High trust and intent-to-use, or sceptical? Sentiment shapes adoption velocity whether or not it tracks productivity.
- **What does Octoverse say about activity patterns in the language, repo shape, or org shape your team works in?** Octoverse at-scale telemetry can give you a baseline your single team cannot.
- **What does McKinsey State of AI say about where enterprises in your sector are investing?** Useful for leadership framing and for pre-empting the "aren't we behind?" question.
- **What does the academic empirical research** (Dell'Acqua, Peng, Noy & Zhang, Brynjolfsson-Li-Raymond) **say about the causal effect on this task class, if it has been studied?** The empirical work is narrower but far better evidence than survey self-report.

Where the surveys and your task sort agree, the sort is strengthened. Where they disagree, you now have a specific question to answer in the pre-read: "the broader data suggests AI drafts this, our team's sort puts it under review-only this quarter — here is why for us."

### Reading surveys at refresh cadence, not announcement cadence

Reading each survey the day it drops is poor use of your time — the press-release framing is the loudest and the least useful. A reasonable cadence:

- **Quarterly.** Pull the most recent *Microsoft Work Trend Index* and the latest *Stack Overflow Developer Survey* AI section into your roadmap refresh. Update any numbers you quoted in the pre-read.
- **Annually.** Pull the latest *McKinsey State of AI*, *GitHub Octoverse*, and *WEF Future of Jobs* at the quarter where they drop. Rebaseline the "where is the industry" paragraph in your pre-read.
- **Opportunistically.** When an exec forwards you a survey with a highlight, respond with the four-question check, not with a yes.
- **On model-generation events.** When a vendor ships a new model generation, re-read the survey evidence on capability and sentiment before committing to a pilot — adoption velocity shifts with each generation.

### What goes into the roadmap, and in which voice

The roadmap and the exec pre-read use survey data in two different ways:

- **Roadmap body.** The surveys inform the task sort and the sequencing; they generally do not quote numbers. The body says "AI-first this quarter for PR descriptions" because your team's sort landed it there, not because MS WTI said so. Quote a survey only when the quote carries weight that your evidence alone cannot (e.g., "our sort puts this AI-first, consistent with the most recent WTI sample in which $N\%$ of knowledge workers report using AI for drafting on a daily basis" — and even then only if the four-question check passes).
- **Exec pre-read.** A one-paragraph "industry context" sits at the top, with two or three ranges rather than point estimates, and one or two tensions where your plan diverges from the industry baseline — with the reason. This is the paragraph that pre-empts "aren't we behind?" and "aren't we ahead?" as tangents in the exec review.

### Translating across disciplines

The AI-augmented team manager role is discipline-agnostic. If your team is design, analytics, content, support, or research, the heavy-engineering surveys (Octoverse, Stack Overflow) will under-represent you. Two moves keep the translation honest:

1. **Use the broad-knowledge-worker surveys as the primary anchor.** MS WTI and McKinsey State of AI sample across functions. They are not perfect for your discipline either, but they are better than Octoverse for non-engineering work.
2. **Add discipline-specific references explicitly.** Analytics: NewVantage Partners' annual *Data and AI Leadership Executive Survey*. Design: the NN/g research on AI-in-design workflows. Support: Brynjolfsson, Li & Raymond's customer-service study. The cadence (quarterly / annual / opportunistic) applies the same way.

The roadmap is not an engineering artifact. If yours only cites engineering surveys, you have lost the translation at the input step.

## Example: a half-page "industry context" paragraph for the exec pre-read

Illustrative; adjust for your horizon and the current round of reports:

> **Industry context (Q1 2027).** The most recent *Microsoft Work Trend Index* reports broad knowledge-worker AI usage in a range consistent with the prior year's reading, with "bring your own AI" and manager-oriented friction as the notable new themes. *Stack Overflow Developer Survey 2026* shows developer sentiment on AI assistants in roughly the same band as last year, with trust still below intent-to-use. *McKinsey State of AI 2026* reports enterprise GenAI deployment growing, with cost and governance maturity now the most-cited challenges; its sector breakdown puts fintech in the upper band. *GitHub Octoverse* reports continued growth in AI-related repos and Copilot adoption. Academic work (Peng et al. on Copilot; Dell'Acqua et al. on consulting) corroborates the directional claim that inside-the-frontier work sees double-digit productivity gains and outside-the-frontier work does not.
>
> **Where our plan is consistent with the industry baseline.** AI-first routing of PR descriptions, test skeletons, ADR first drafts, and SQL skeletons — all inside the frontier per Chapter 2's sort, all consistent with the pattern reported across MS WTI, Octoverse, and Peng et al.
>
> **Where our plan diverges from the industry baseline.** We are *not* mandating this quarter, against some of the industry language around "AI-first everywhere." The reason: our team is three months into a re-org, mandate change-management budget is low, and opt-out at scale is the honest rollout mode this quarter. We revisit in Q2.
>
> **Sources.** [Microsoft WTI], [Stack Overflow DS 2026], [McKinsey State of AI 2026], [GitHub Octoverse 2026], [Peng et al. 2023], [Dell'Acqua et al. 2023] — each cited with release date, methodology link, and the specific figure referenced.

<!-- needs-research: before this paragraph lands in a real exec pre-read, pull the latest editions of each survey and replace the hand-waved "range" language with the current figure, correctly dated and sourced. The goal of the example is the structure, not the numbers. -->

## Summary

- The industry surveys (Microsoft WTI, McKinsey State of AI, GitHub Octoverse, Stack Overflow Developer Survey, plus WEF, OECD, Gartner, MIT Sloan) are **input** to the roadmap; they are not the roadmap. Copying their headlines in verbatim is the standard failure.
- Triangulate across surveys; a signal is only reasonably stable where two or three agree. Report ranges, not point estimates.
- Four questions before quoting: who is in the sample, how is the key term defined, compared to what, does it match the other sources?
- Use surveys to pressure-test Chapter 2's task sort — where the sort and the industry baseline agree, you are strengthened; where they disagree, you now have a specific thing to explain in the exec pre-read.
- Refresh cadence: quarterly for the knowledge-worker-level surveys; annually for McKinsey, Octoverse, WEF; opportunistically for exec forwards; on every model-generation event.
- The roadmap body uses surveys to inform sequencing, not to decorate the narrative. The exec pre-read gets a one-paragraph industry-context section that explicitly names where the plan is consistent with and divergent from the baseline.
- For non-engineering disciplines, use MS WTI and McKinsey as the primary anchor and add a discipline-specific reference. Do not let the engineering-heavy surveys squeeze out the translation.
