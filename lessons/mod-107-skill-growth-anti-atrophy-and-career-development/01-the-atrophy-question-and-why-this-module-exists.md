# Chapter 1 — The Atrophy Question and Why This Module Exists

> *AI is reshaping the distribution of skill inside your team in ways that will not show up in next quarter's output and may not show up in next year's. By the time it does, two things are broken: the judgement muscle the senior ICs used to apply, and the growth path the junior ICs were supposed to walk up. This module is the operational response — before the breakage, not after.*

## Motivation

The 25-posting evidence base that seeds this track lists *prevent skill atrophy and preserve judgment — deliberate practice, career-development ladder under AI augmentation* as requirement **R10**, with a posting frequency of **0.08** in the sample (see [`JOB_REQUIREMENTS.md`](../../JOB_REQUIREMENTS.md)). Two postings in the 25-sample name this work explicitly — the rest do not. By the strict 0.30 threshold this track applies to posting-based requirements, R10 would not have its own module.

It has one anyway, for a specific reason: the authoritative empirical research on how generative AI reshapes skill distribution in knowledge work is strong enough, published enough, and consistent enough across three independent studies that absence of this module would be a defect in a level-40 team-manager track regardless of what the current posting language says. The research anchors are:

- [Brynjolfsson, Li, Raymond, *Generative AI at Work* (NBER WP 31161)](https://www.nber.org/papers/w31161) — AI productivity gains in a real deployment concentrate at lower-tenure / lower-skill workers; experienced workers see little gain. Chapter 2.
- [Noy & Zhang, *Experimental evidence on the productivity effects of generative AI* (Science 2023)](https://www.science.org/doi/10.1126/science.adh2586) — generative AI on realistic writing tasks compresses the top-to-bottom performance gap and lifts bottom-tier output more than top-tier. Chapter 3.
- [Dell'Acqua et al., *Navigating the Jagged Technological Frontier* (HBS WP 24-013)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321) — AI-augmented workers on tasks outside the AI's capability frontier *defer* to AI output and produce plausible-but-wrong answers at higher rates than the control group. Chapter 4.

The three findings are not a single phenomenon — they describe distinct channels by which AI reshapes a team's skill base. Read individually, each supports a specific team-level policy. Read together, they describe a managerial problem that does not solve itself and that is nearly invisible at the quarterly-output level until the senior IC whose judgement held the team together leaves or the junior IC who shipped successfully for 18 months fails on the first problem the AI cannot handle. The curriculum policy ([`JOB_REQUIREMENTS.md`](../../JOB_REQUIREMENTS.md)) names R10 explicitly: *keep as a dedicated module because the empirical research grounds the practice regardless of current posting-frequency signal, and the frequency is expected to rise as the market codifies the risk*.

This chapter does three things. First, it names the shape of the atrophy problem — what it is, what it is not, and why its signal is lagged. Second, it names the five pieces of mod-107 that respond to it. Third, it draws the scope boundary against HR, mod-108 (hiring and performance), and mod-109 (incident response).

## Core concepts

### The three channels of atrophy, named plainly

The managerial problem is not *"the team is getting worse."* It is three distinct effects composing into a slow drift that will not trigger a quarterly alarm.

- **The growth-path channel.** Brynjolfsson, Li, Raymond's call-center study shows AI gains concentrate at low tenure. In the *short run* this is a feature — junior ICs ship work faster than they could have unassisted. In the *long run* the junior ICs' skill-growth curve changes shape: the mistakes they used to make, recover from, and learn from are now absorbed by the model before the artifact reaches a reviewer. Chapter 2 is the operational read of this channel.
- **The differentiation channel.** Noy & Zhang's writing experiment shows generative AI compresses the top-to-bottom performance gap: the bottom quartile improves more than the top quartile, and dispersion of output quality narrows. The problem is not that the bottom quartile ships better work; that is the win. The problem is that *promotion signal* — which is historically differentiation of output — stops working. Chapter 3 is the operational read, feeding Chapter 6's ladder work.
- **The deference channel.** Dell'Acqua et al.'s BCG experiment shows AI-augmented workers on outside-frontier tasks *do worse* than the control group because they defer to AI output they cannot evaluate. The second-order pattern Dell'Acqua et al. call the *uncritical consumer* is the specific deskill risk this module addresses. Chapter 4 is the operational read, feeding Chapter 5's deliberate-practice work.

The three channels compound. A junior IC on an AI-augmented team will grow more slowly on the fundamentals (Channel 1), look stronger on measured output than their actual judgement warrants (Channel 2), and acquire deference habits that will fail them on outside-frontier work (Channel 3) — simultaneously. A manager who waits for the compounded signal to surface at promotion time has waited too long.

### Why the signal is lagged by 12–36 months

Three features of the problem make it lag.

- **The failure mode is subtle.** The engineer who defers to AI output does not produce *visibly* worse PRs; they produce plausibly-correct PRs that fail later, in production, on the outside-frontier slice. Review catches the obvious; what is hard to catch is the absence of the judgement that *would have* caught the subtle error.
- **The output metrics look fine.** Noy & Zhang's finding is that the bottom quartile *improves* on measured output. DORA and DX Core 4 numbers for an AI-adopting team almost always improve in Year 1 (see mod-104 Chapter 5). The dashboard shows a win. The atrophy is a story the dashboard is not instrumented to tell.
- **The feedback loop is slow.** Junior ICs grow through 18–24 months of carefully-exposed problem-solving. If the exposure is structurally different for the first 24 months of their career, you will not see the gap until month 25 — long past the point at which the training approach could have been changed.

The managerial implication is not *"wait for the signal."* It is *"instrument for the leading indicators and act on them before the lagging indicator appears."* Chapter 7's 1:1 prompts and retro design are the leading-indicator instrumentation; Chapter 5's deliberate-practice carve-outs are the acting-before-the-lagging-indicator intervention.

### The five pieces of mod-107

A mod-107-literate manager produces five composed artifacts over the course of this module.

| Piece | What it does | Chapter(s) | Exercise |
|---|---|---|---|
| **Three-paper research read + policy translation** | Reads Brynjolfsson, Noy-Zhang, and Dell'Acqua at manager fluency; translates each finding into a team-level policy move with a single-sentence rationale per policy | 2, 3, 4 | [Exercise 01](exercises/exercise-01-empirical-research-into-team-policy.md) |
| **Deliberate-practice carve-out schedule** | A quarterly schedule naming paired-review rotations, periodic AI-off artifacts, and judgement-weighted review passes — the operational response to the deference channel | 5 | [Exercise 02](exercises/exercise-02-deliberate-practice-carve-out-schedule.md) |
| **Career-development ladder under AI augmentation** | The team's ladder updated to reward judgement — not throughput — including what a promotion packet looks like when the IC's output is co-authored with an agent | 6 | [Exercise 03](exercises/exercise-03-career-ladder-under-ai-augmentation.md) |
| **Burnout and over-reliance 1:1 and retro prompts** | A working set of 1:1 and retro prompts that surface deference, dependency, and burnout — grounded in Edmondson's psychological-safety frame and Westrum's culture typology | 7 | [Exercise 04](exercises/exercise-04-burnout-and-over-reliance-1on1-prompts.md) |
| **IC development-plan template refresh** | The individual development-plan (IDP) template used in 1:1s, refreshed so growth plans under AI augmentation name the judgement muscle the IC is building and how it will be measured | 5, 6 | [Exercise 05](exercises/exercise-05-ic-development-plan-template-refresh.md) |

Chapters 1 and 8 bracket the module: Chapter 1 opens with the research grounding and the scope statement; Chapter 8 closes with the ownership boundary against HR.

### What this module is *not*

The adjacent-but-distinct work matters.

- **Not an HR course.** Formal employment actions — performance improvement plans, terminations, compensation freezes, levelling calibration — belong to HR / employee-relations partners. Chapter 8 is the full boundary statement. This module covers what the manager observes, instruments, documents, and raises; HR owns what happens next in the formal process.
- **Not a hiring-loop course.** Interview-loop redesign for AI-augmented candidates, performance-review authoring under AI augmentation, and feedback-cycle adaptation are [`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/)'s remit. mod-107 feeds mod-108 — the judgement-weighted career ladder authored here is the ladder the promotion case in mod-108 is built against — but the hiring and review mechanics live there.
- **Not an IC-mechanics course on AI tool fluency.** The actual mechanics of using Cursor, Claude Code, or Copilot — prompt patterns, agent authoring, eval-rig construction — belong to [`ai-assisted-software-engineer`](https://github.com/ai-engineering-curriculum/ai-assisted-software-engineer-learning) (level ~25). mod-107 treats IC fluency as a prerequisite (`PREREQUISITES.md`) and is about the team-level structure around that fluency, not the fluency itself.
- **Not an engagement-survey authoring course.** The 1:1 and retro prompts in Chapter 7 are specifically designed to *replace* annual-engagement-survey theatre for this problem, because the signal the survey produces arrives too late and too aggregated to act on. Chapter 7 is explicit on why.
- **Not a psychology course.** Edmondson's psychological-safety construct and Westrum's culture typology are used here as diagnostic vocabulary, not as a comprehensive treatment. The references in Chapter 7 point to the primary texts for managers who want to go deeper.
- **Not a universal theory of deliberate practice.** Chapter 5 uses Anders Ericsson's deliberate-practice framing as the anchor for the carve-outs; the chapter does not re-derive the broader deliberate-practice literature.

### Where mod-107 sits in the track

Back-links:
- The human/machine contract drafted in [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) Chapter 3 is the contract this module sharpens on the *development* axis — clause C3 (*who is on the hook*) implies a growth story for the humans who are on the hook, and this module provides it.
- The review standards authored in [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) are the standards Chapter 5's judgement-weighted review pass amends. The amendment is additive — reviewers ask the standard's checklist *plus* the judgement question Chapter 5 defines.
- The productivity measurement work in [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) is the dashboard that *will not show* the atrophy. Chapter 1's "signal is lagged" argument is a direct read of the mod-104 dashboard's gap.
- The enablement program in [`mod-105`](../mod-105-team-ai-enablement-programs/) is where the junior IC's growth path *starts*; mod-107 is where it is sustained past the first 90 days.
- The workflow redesign in [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) names the task-routing matrix; mod-107 asks what happens to the human skill base once the routing is in place.

Forward-links:
- The hiring-loop and performance-review work in [`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/) uses the ladder authored here as its standard.
- The incident-response work in [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) is where the *consequence* of the deference channel shows up — an incident caused by an IC who shipped AI output they could not evaluate is in scope there.
- The ritual-calendar work in [`mod-112`](../mod-112-cross-functional-leadership-and-ritual-calendar/) is where Chapter 5's carve-outs land on the team calendar and where Chapter 7's retro prompts find a running cadence.

Sideways-links:
- HR partnership: see Chapter 8. Formal processes belong to HR; the manager-side framing is this module.
- Up to [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) (level 45) for org-wide skill-growth programming, cross-team capability tracking, and enablement at scale beyond a single team.

## Example: the signal that should have arrived earlier

A single composite example to make the atrophy pattern concrete; treat as calibration, not a case study.

A team adopts an AI coding assistant in Q1. By end of Q2 the dashboards tell a win story: DORA deployment frequency is up, DX Core 4 self-reported satisfaction is up, PR throughput is up ~25%, review latency is down. The team manager writes the mid-year narrative citing the quantitative improvement. Junior IC A ships 30% more PRs than the baseline; junior IC B is similar. Senior IC C and senior IC D produce roughly the same output as before AI adoption (consistent with the Brynjolfsson finding — gains concentrate at lower tenure).

Q3 — the junior ICs continue to ship. In 1:1s they report feeling productive and happy. There is no engagement-survey red flag. The senior ICs mention in passing, separately, that they are doing more code review than before but it feels different — less *"did they miss a case?"* and more *"does this look like something a thoughtful engineer would have written?"*. The manager notes the comments but has no instrument to act on them.

Q4 — an incident. Junior IC A ships a feature whose critical path handles a corner case subtly incorrectly. The PR passed review (the reviewer was time-pressured and the diff looked clean). The incident post-mortem surfaces that the AI suggested the implementation and the IC accepted it without constructing the mental model of why the suggestion was *not* the right one for this specific context. Junior IC A describes the pattern in the post-mortem review candidly: *"I didn't know to question it."* The IC is not under-skilled; the IC's skill-growth curve has been shaped by 10 months of successful AI deference and the model of *when to doubt* did not develop.

The atrophy signal was present in Q2 and Q3 — in the senior ICs' side comments, in the junior ICs' lack of narrative vocabulary for *"I pushed back on the AI and chose differently,"* in the retro content. The instrument to surface it did not exist. Chapter 7 is the instrument.

## Summary

- R10 (prevent skill atrophy and preserve judgment) sits at **0.08 posting frequency**, below the 0.30 threshold. It has a dedicated module because [Brynjolfsson, Li, Raymond](https://www.nber.org/papers/w31161), [Noy & Zhang](https://www.science.org/doi/10.1126/science.adh2586), and [Dell'Acqua et al.](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4573321) ground three distinct channels of atrophy that compound below the quarterly output signal.
- **The growth-path channel** (Brynjolfsson) — AI gains concentrate at lower tenure; junior ICs grow through a different curve than their unassisted predecessors. Chapter 2.
- **The differentiation channel** (Noy & Zhang) — AI compresses the top-to-bottom gap in measured output; promotion signal based on output volume stops differentiating. Chapter 3.
- **The deference channel** (Dell'Acqua) — on outside-frontier tasks, AI-augmented workers defer to AI output and produce more plausibly-wrong answers than the control; the *uncritical consumer* pattern. Chapter 4.
- The atrophy signal lags 12–36 months behind the policy decisions that produced it. Waiting for the lagging indicator is too late; Chapter 7 is the leading-indicator instrument.
- mod-107 produces five composed artifacts: the **research-to-policy translation** (Exercise 01), the **deliberate-practice carve-out schedule** (Exercise 02), the **career-development ladder under AI augmentation** (Exercise 03), the **burnout and over-reliance 1:1 and retro prompts** (Exercise 04), and the **IC development-plan template refresh** (Exercise 05).
- mod-107 is *not* an HR course (formal actions link to HR; Chapter 8), not a hiring course ([`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/)), not an IC-mechanics course ([`ai-assisted-software-engineer`](https://github.com/ai-engineering-curriculum/ai-assisted-software-engineer-learning) at L25), and not a replacement for the engagement survey (it is deliberately designed to not look like one).
