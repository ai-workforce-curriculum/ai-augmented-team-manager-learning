# Chapter 3 — Delivery Formats: Bootcamps, Workshops, Communities of Practice

> *A bootcamp is a concentrated event. A workshop is a focused drill. A community of practice is a social commons. Each does a specific job. A programme that uses one format for all three jobs is a programme that fails two of them.*

## Motivation

R5's verbatim posting language names *"internal bootcamps, workshops, communities of practice"* as the three delivery formats. These are not interchangeable labels — they are three different interventions that do three different jobs, with roots in distinct traditions. A manager who treats "workshop" as a synonym for "bootcamp" ends up with a 2-hour cram session carrying the weight of a 10-day cohort experience; a manager who treats "community of practice" as "a Slack channel" ends up with the sustainment layer failing silently after the kickoff.

Each format maps to a specific slice of the Chapter 2 timeline:

- **Bootcamp** carries Days 1–10 of the 30/60/90 — concentrated, cohort-based, same people meeting repeatedly, focused on one or two tools.
- **Workshop** carries Days 11–60 (overlapping with pair-with-mentor time) — focused drills on specific skills, typically 60–90 minutes, run weekly or bi-weekly.
- **Community of practice** carries Days 61–90 and beyond — the sustaining format. Chapter 7 goes into the partnership mechanics; this chapter establishes what it is and how it starts.

This chapter sketches each format: what it is, what it is not, how to run it, when it breaks.

## Core concepts

### Bootcamps: concentrated cohort learning on one or two tools

A bootcamp is a **concentrated, cohort-based, intensive** format focused on one or two tools. The word "bootcamp" is doing work here — it is not a marketing label. The format inherits a specific shape:

- **Cohort**. Same 3–6 engineers at every session. Chapter 2's cohort composition guidance (mixed stage, not mixed seniority) applies.
- **Concentrated**. Three to five sessions over two weeks, not a monthly drip. The concentration is load-bearing: the cohort's shared reference frame builds through repetition in a short window. A bootcamp stretched over six months is not a bootcamp; it is a workshop series.
- **Tool-specific**. A bootcamp targets *one* tool or at most a tightly-coupled pair (e.g. Cursor + the team's main AGENTS.md convention; Claude Code + the team's eval harness). A bootcamp that tries to cover "all AI tools" is a vendor-demo day in a different costume.
- **Hands-on, on real code.** Not a demo sandbox. Chapter 1's Failure B is largely a bootcamp-that-stayed-in-sandbox problem. Every session should produce or edit at least one file in the team's actual repo.

A workable bootcamp sequence for one tool (e.g. Cursor):

| Session | Length | What happens |
|---|---|---|
| 1 — Opening | 90 min | Setup, rules file walk, first change to the real repo with the tool. Pair with a stage-3 engineer. |
| 2 — Context and rules | 60 min | How the team's Cursor rules / AGENTS.md shape the tool's behaviour. Make one proposed edit, discuss. |
| 3 — Review the tool's output | 90 min | Walk three recent agent-authored PRs the team has merged. What did reviewers catch; what did they miss. |
| 4 — Pair-with-mentor task | 2 hours | In-the-flow, each engineer paired with a stage-3 mentor on a real work item. Not scheduled lecture. |
| 5 — Retro | 60 min | Each engineer describes one thing that surprised them. Patterns surfaced go into the pattern library (see CoP, below). |

Five sessions, roughly 7 hours of scheduled time, spread over two weeks, gated on the real-code work happening between sessions. Session 4 is often the one managers try to drop — don't. It is where the bootcamp earns its name.

**Who delivers the bootcamp.** Not necessarily the manager. The default pattern: the manager authors the curriculum and the measurement rubric (per Chapter 1); a senior IC on the team (or two) delivers Sessions 1–3; the pair-with-mentor time in Session 4 pairs each engineer with a different IC; the manager facilitates Session 5. L&D handles scheduling and intake. Vendor trainers run Session 1 or 2 *only if* their material has been curriculum-reviewed by the manager and deliberately scoped to this team. A vendor trainer running the full five sessions off-the-shelf is the Failure-A one-shot-workshop pattern again.

**What a bootcamp is not:**

- *Not a talk.* A one-hour talk is a workshop at best, a demo at worst. No cohort means no bootcamp.
- *Not a certification pipeline.* If your bootcamp ends with a certificate, you have optimised for the wrong artifact. The Chapter 5 fluency-growth artifacts are the output; a certificate is window dressing.
- *Not a vendor roadshow.* A vendor's generic enablement is an input you can commission a session from; it is not the programme.

### Workshops: focused drills on specific skills

A workshop is a **focused, topic-specific, 60–90-minute session on a concrete skill**, typically run weekly or bi-weekly during Days 11–60. Where the bootcamp is tool-first, the workshop is skill-first.

Workshop topics that earn their time on a mod-105 programme:

- *Reviewing an agent-authored PR.* The team's mod-103 review standard applied to a specific agent-generated PR. 60 min. Run every cohort.
- *Authoring a prompt for a code-review assistant.* The team's prompt conventions (if any) applied to a specific code-review case. 60 min.
- *Composing context for the tool.* How to point Cursor / Claude Code / Copilot at the right files, docs, and prior conversations. 60 min.
- *Reading an eval report.* The team's eval tool (Promptfoo / LangSmith / Inspect AI) opened on a real report. 60 min. Overlap with `mod-103`.
- *Delegating a task to an agent.* Walking through the delegation checklist from `mod-106`. 90 min.
- *Writing a rollback-trigger note for a tool.* When you would turn the tool off, who signs, what evidence is needed. 60 min. Overlap with `mod-104` and `mod-110`.

Workshop shape:

- **Topic-specific** — one skill per session, not a survey.
- **Hands-on in the last third** — every workshop produces a small artifact (an annotated PR, an edited rules file, a half-page reflection). Even a 60-minute workshop can end with 20 minutes of practice.
- **Attended by cohorts in-progress, not one-off.** Engineers at Day 20 and Day 45 attend together. The stage-mixing is a feature.
- **Recurring on a cadence.** Weekly during the first quarter of a cohort's cycle. Bi-weekly thereafter.

**Who delivers workshops.** Rotate. A pattern that works: the manager runs ~1 of 5 workshops per quarter (modelling the practice from `mod-101`); a senior IC runs ~2 of 5; a cross-team peer (an engineer from `ai-assisted-software-engineer` scope on a neighbouring team) runs ~1 of 5; an external speaker (sparingly) runs ~1 of 5. Full-manager delivery burns the manager out; full-vendor delivery drifts the curriculum off the team's work.

**What a workshop is not:**

- *Not a bootcamp.* One 90-minute session on "Copilot" is not a bootcamp; it is a workshop with an over-ambitious scope.
- *Not a lunch-and-learn.* The format with no artifact and no follow-up is the oldest failure mode in corporate L&D. Call it what it is; don't put it on the mod-105 calendar.

### Communities of practice: the sustaining layer

The **community of practice (CoP)** is the sustaining layer. Chapters 2 and 3 land engineers into fluency through cohorted delivery; the CoP keeps the fluency alive after the 90 days.

The concept comes from Etienne and Beverly Wenger-Trayner's social-learning theory. Three structural elements define a community of practice ([*Communities of Practice: A Brief Introduction*, Wenger-Trayner](https://www.wenger-trayner.com/introduction-to-communities-of-practice/)):

- **Domain** — a shared area of concern that members are invested in. For your team: *AI-augmented software engineering practice* for this team's work. Not "general AI"; not "all of coding."
- **Community** — people who care about the domain and interact regularly. The members are *your team plus occasional peers from adjacent teams*.
- **Practice** — a shared repertoire of resources, experiences, stories, tools, ways of handling recurring problems. Not a book club; a shared body of *doing*.

A CoP that is missing one of the three is a shell:

- Domain without practice = a Slack channel of links nobody tries.
- Practice without community = a wiki nobody reads.
- Community without domain = a weekly social with no throughline.

**What a working team-scope CoP looks like.**

| Element | Concrete form |
|---|---|
| Domain | The team's AI-augmented workflow — the specific tools, review standards, and delegation patterns in use on this team |
| Community | ~20 engineers from this team + ~5 regular visitors from adjacent teams + the manager; a core group of 3–5 engineers rotates ownership of the sessions |
| Practice | A pattern library (a repo or Notion / Confluence doc) of recurring problems and the team's shared response; a session rotation; a show-and-tell cadence |

**Operational cadence that works.** This is one defensible shape among several; adjust to your team.

- *Show-and-tell, bi-weekly, 45 minutes.* One engineer brings a recent AI-augmented work slice. 10-minute walk, 15 minutes of Q&A, 15 minutes of pattern extraction. A rotating facilitator (not always the manager) captures the pattern into the library.
- *Pattern-library review, monthly, 30 minutes.* The library is treated as a document that ages. Old patterns get sunset or revised. A pattern that has not been referenced in six months is a candidate for removal.
- *Review-of-your-review session, quarterly, 90 minutes.* Several engineers walk their Day-90 self-reviews (Chapter 5) in small groups. The pattern across self-reviews often reveals a shared gap worth a next-quarter workshop.
- *Cross-team visit, quarterly.* An engineer from a neighbouring team presents their equivalent practice. Keeps the CoP from becoming insular.

**Facilitation rotation, not ownership concentration.** The most common CoP failure mode is "the manager is the CoP." If you are facilitating every session and curating every pattern, you have a manager-run show, not a community. Rotate facilitation among 3–5 engineers. Your role is *sponsor* and *honest-signal-in-review*; it is not master-of-ceremonies.

**What a CoP is not:**

- *Not a Slack channel.* A Slack channel is one tool the CoP may use. The CoP is the people, the domain, and the practice.
- *Not a book club.* Reading a book together is one *activity* a CoP may do once; a CoP that does only that is missing the practice dimension.
- *Not a working group.* A working group has a mandate and a deliverable; a CoP has an ongoing domain.
- *Not an org-wide initiative.* Org-wide AI practice communities are owned at `ai-enablement-lead` (L45). Chapter 8 covers the graduation.

### How the three formats compose

The reason mod-105 names all three formats is that they do different jobs and the programme needs all three. A sketch of the composition:

| Need | Format | Why that one |
|---|---|---|
| Move a stage-1 engineer to stage-2 on a specific tool | Bootcamp | Concentration + cohort + real-repo repetition |
| Teach a specific skill (reviewing an agent PR, composing context, reading an eval) | Workshop | Focused, bounded time, discrete skill |
| Keep the practice alive after the first cohort graduates | Community of practice | Social-capital anchor, shared repertoire |
| Spread a novel pattern an engineer invented across the team | Community of practice (show-and-tell) | Peer-to-peer legitimation, low ceremony |
| Fix a critical review-standard gap uncovered in retro | Workshop | Fast turnaround, specific skill |
| Onboard a new cohort to a brand-new tool | Bootcamp | Same shape as the original, scheduled fresh |

A programme without a bootcamp will have stage-1 engineers who never move. A programme without workshops will have cohort graduates who cannot articulate specific skills. A programme without a CoP will have 90-day graduates who regress by Day 180.

### Common mistakes when first assembling the delivery mix

- **Over-booking.** Three formats × weekly cadence × team of 20 = a calendar nobody can sustain. Rate-limit: at most one workshop per week per cohort-in-progress; one show-and-tell every two weeks; bootcamp runs for the duration it needs and then sleeps until the next cohort.
- **Under-authoring.** The manager books the sessions and hopes the senior ICs figure out the content. Without a written curriculum (which the manager owns per Chapter 1), delivery drifts to whatever the IC remembered to prepare that morning. Chapter 7 handles the authoring-vs-delivery split.
- **Workshop-as-bootcamp.** Scheduling 14 weekly workshops and calling it a bootcamp. The social-capital effect of the cohort is lost; the concentration is lost; what you have is a workshop series.
- **CoP-as-launch-event.** Running a one-time "launch session" of the CoP and then never meeting again. The CoP is the recurring cadence, not the kickoff.
- **Vendor-roadshow drift.** Letting the three tool vendors on your team's stack each run their own bootcamp. You now have three bootcamps teaching three incompatible philosophies. The curriculum is yours; vendor input is a session, not the frame.

### The authoring-vs-delivery split (lightweight preview of Chapter 7)

A full workup of partnering with HR / L&D / Platform / vendors lives in Chapter 7. The one line to internalise here: **the manager authors the curriculum and the measurement rubric. The delivery can rotate — senior IC, cross-team peer, L&D partner, vendor trainer, platform partner. Authoring cannot rotate.**

If an L&D partner or vendor offers to "run the programme end-to-end," your answer is "deliver the sessions I have scoped; I retain the curriculum pen and the measurement rubric." A programme end-to-end-run by a partner function is the Chapter 1 failure mode.

## Example: a three-format week in a 20-engineer platform team

Treat as calibration, not a template.

> **Context.** Cohort A is at Day 12 (in bootcamp Session 3 week). Cohort B is at Day 42 (deep in workshop phase). Cohort C is at Day 75 (in the CoP). Five engineers have graduated to stage-3 and are pair-with-mentor volunteers.
>
> **Monday.** Workshop for Cohort B and C overlap: *Reading an eval report*. 60 min. Delivered by a senior IC who did the equivalent exercise in `mod-103`. Cohort A doesn't attend (they are in bootcamp).
>
> **Tuesday.** Cohort A bootcamp Session 3: *Reviewing agent-authored PRs*. 90 min. Delivered by the manager (the Session-3 slot is the modelling slot; manager runs it to carry the review standard).
>
> **Wednesday.** No scheduled session. Pair-with-mentor time for Cohort A (Days 11–20 in the pair-with-mentor phase); ad-hoc work for Cohort B; CoP prep for Cohort C.
>
> **Thursday.** CoP show-and-tell, 45 min. An engineer from Cohort C's cohort-mate presents a recent delegation-to-agent task they did. Open to cohorts B and C; pair-with-mentor volunteers attend; three visitors from adjacent teams attend.
>
> **Friday.** Cohort A bootcamp Session 4: pair-with-mentor on real work items. 2 hours blocked but running in-the-flow of actual work. No lecture.
>
> **Manager time this week.** 90 min authoring next week's workshop; 90 min delivering Tuesday's session; 45 min attending Thursday's CoP; 30 min pattern-library review; 30 min 1:1 with the senior IC running Monday's workshop. Roughly 5 hours including the delivery.

Three formats, three audiences, one coherent programme. The manager's time is spent authoring, modelling, and partnering — not delivering every session.

## Summary

- Three formats, three jobs. **Bootcamp**: concentrated, cohort-based, tool-specific, Days 1–10. **Workshop**: focused, skill-specific, 60–90 min, Days 11–60. **Community of practice**: sustaining, social-learning anchor, Days 61–90 and beyond.
- The CoP has three Wenger-Trayner structural elements: **domain, community, practice**. All three or it is a shell.
- Cohort sizing (from Chapter 2) carries through: 3–6 engineers, mixed stage, same cohort for 90 days.
- Facilitation rotates; curriculum authoring does not. The manager authors; senior ICs, L&D, vendors, cross-team peers deliver.
- Common mistakes: over-booking, under-authoring, workshop-as-bootcamp, CoP-as-launch-event, vendor-roadshow drift.
- The three formats *compose* — a programme missing any one of them fails in a specific predictable way.
- Exercise 04 produces the community-of-practice charter for your team.
