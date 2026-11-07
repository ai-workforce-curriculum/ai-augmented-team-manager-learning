# Quiz 01 — Roadmap, Task Sort, Rollout, and Artifacts

**Format:** 12 multiple-choice questions.
**Coverage:** All six chapters of mod-102.
**Scoring:** 1 point per question. 9/12 is a pass. Below that, re-read the chapter named in the answer explanation before moving on.

Each question tests whether you can apply the chapter, not whether you can quote it. Pick the single best answer.

---

## Question 1

A VP asks you to send over your team's "AI roadmap." You draft a one-page document that lists the four AI tools your team plans to use this quarter, with vendor names, seat counts, and renewal dates. Per Chapter 1, the strongest objection to shipping this as the roadmap is:

- A. It needs more vendor detail — procurement is the roadmap's primary question.
- B. It is a tool procurement plan, not a roadmap; procurement is owned at team scope in `mod-111` and the roadmap *consumes* the procurement outcome. A roadmap answers *what to automate, in what order, with whom, and how we will know it worked* — tools come downstream of that.
- C. It is too short — a one-page roadmap signals the plan has not been thought through.
- D. The roadmap should be owned by `ai-augmented-product-manager` (L30) since it discusses tools customers will see.

## Question 2

Dell'Acqua et al.'s *Navigating the Jagged Technological Frontier* has two load-bearing properties, per Chapter 2. Which pair best describes them?

- A. The frontier is **stable** across model generations and is **visible** to any well-trained reviewer looking at the task description.
- B. The frontier is **jagged** (capability on neighbouring-looking tasks differs sharply) and **invisible from the outside** (you cannot tell by looking whether a task falls inside; you find out by running the task through the model and judging the output).
- C. The frontier is **smooth** (capability degrades gradually as tasks get harder) and **publicly mapped** by the model vendor's documentation.
- D. The frontier is **jagged** but **predictable** from the task's domain — engineering tasks are inside, writing tasks are outside.

## Question 3

Your team sorts a new task — *drafting customer-facing refund emails* — against the Chapter 2 six-dimension rubric. Scores: capability fit 4, verifiability 3, blast radius 1, frequency 5, judgment density 3, reversibility 1. Sum: 17. Per Chapter 2's rule of thumb, the correct placement is:

- A. **AI-first** — the sum of 17 is close enough to the ≥18 threshold.
- B. **Pilot candidate** — the rubric is ambiguous and a pilot will resolve it.
- C. **Human-led this quarter** — blast radius is scored 1 and reversibility is scored 1; a score of 1 in blast radius / verifiability / judgment density pushes the task into human-led regardless of the sum.
- D. **AI-assisted (review-only)** — the sum is in the 15–17 band.

## Question 4

You have written a pilot charter that includes task, workflow, cohort, horizon, success criteria, decision owner, decision date, and a data collection plan — but the kill-criteria field reads: *"We will stop if the pilot shows no measurable improvement."* Per Chapter 3, what is wrong with that?

- A. Nothing — "no measurable improvement" is a clean kill trigger.
- B. The kill criteria should be numeric with a specific percentage (e.g., "<10% time saving").
- C. It is a hedge, not a kill criterion. Chapter 3 says at least one kill trigger should be operational — about reviewer burnout or an incident signal — so the pilot has a non-numeric stopping rule that will actually fire. "No measurable improvement by end of horizon" is one acceptable rule but cannot be the *only* rule.
- D. The kill criteria field is optional in a charter as long as the success criteria are specific.

## Question 5

Chapter 3 names three adoption modes — opt-in, opt-out (default-on), and mandate — with a default sequence per task family. Which statement best captures the default?

- A. Mandate during pilot (to get clean data), opt-out after promote, opt-in for low-stakes workflows.
- B. Opt-in during pilot, opt-out after a successful pilot, mandate *only* when the mandate came from somewhere above you (security, legal, enablement lead, exec). Manager-origin mandates usually have to be walked back within a quarter.
- C. Opt-out from the start for every AI-first workflow; opt-in is appropriate only for human-led tasks.
- D. The modes are interchangeable — pick based on team personality.

## Question 6

Your team is twelve weeks into a successful pilot of a Cursor-rules convention and an AGENTS.md pattern. A second team's manager pings you asking if they can adopt the same mechanism unchanged. Per Chapter 5, which graduation is most consistent with this signal?

- A. Team-wide rollout — promote to opt-out on your own team and ignore the sibling team's ask.
- B. Graduate to Platform ownership — a mechanism that a second team would adopt unchanged belongs to Platform as shared infrastructure; your team becomes a reference user of the shared version.
- C. Graduate to `ai-enablement-lead` — any multi-team interest means org-wide enablement rollout.
- D. Keep team-local and politely decline the sibling team's ask.

## Question 7

An exec forwards the latest *Microsoft Work Trend Index* with a highlighted stat — "75% of knowledge workers use AI at work" — and asks what this means for your roadmap. Per Chapter 4, your strongest response is:

- A. Add a line to the roadmap body saying "we will match the 75% baseline this quarter."
- B. Reply with the four-question check — who is in the sample, how is "uses AI at work" defined, compared to what, does the finding match MS WTI's peer surveys and the academic empirical research? Report ranges rather than a point estimate in anything that lands in the pre-read.
- C. Decline to engage — survey headlines are marketing and should not inform the roadmap.
- D. Reply that your team already exceeds the 75% baseline, then update the roadmap only if asked.

## Question 8

Chapter 4 names a specific *refresh cadence* for the surveys: quarterly for the knowledge-worker-level surveys, annually for McKinsey / Octoverse / WEF, opportunistically for exec forwards, and on every model-generation event. Which of these cadence slots is the *weakest* use of your time per the chapter?

- A. Quarterly pull of the most recent *Microsoft Work Trend Index* and *Stack Overflow Developer Survey* AI section into the roadmap refresh.
- B. Annually, reading the methodology appendix of *McKinsey State of AI* when it drops.
- C. Reading each survey cover-to-cover on the day it is announced — the press-release framing is the loudest and least useful section.
- D. Re-reading the survey evidence on capability and sentiment on every model-generation event, before committing to a new pilot.

## Question 9

You are drafting the exec pre-read. Under "why this and not that," you write a single paragraph that says, "We considered mandating this quarter but chose opt-out because mandate is premature." Per Chapter 6, this paragraph is thin in a specific way. What is missing?

- A. The paragraph needs a one-line emoji marker showing confidence level.
- B. It should quote at least one survey point estimate for authority.
- C. A *trigger-to-revisit* and a *falsifiable commitment* — the chapter says the pre-read must name what would change our mind, in the vocabulary of the specific exec reading it. "Premature" without a trigger is a hedge, not a reasoned alternative; a stronger version names the threshold ("revisit mandate if adoption >70% under opt-out *and* reviewer quality bar holds for 6 weeks").
- D. It should be longer — "why this and not that" is where the pre-read earns its page count.

## Question 10

A peer manager tells you their team's roadmap is "the team's AGENTS.md plus the Cursor rules file." Per Chapter 1, the strongest critique is:

- A. The AGENTS.md should be versioned with semantic versioning, not just "v1."
- B. Tool configuration files are *downstream* of the roadmap — the roadmap decides what tasks route to AI first (Chapter 2) and in what mode (Chapter 3); only after that do you pick tools and configure them. Treating configuration files as the roadmap means the team has skipped the task sort and the sequencing, and cannot defend "why this and not that."
- C. AGENTS.md is a Platform-owned artifact; the team should not own it at all.
- D. Nothing — a team's AGENTS.md and Cursor rules file *are* the operational substance of the roadmap.

## Question 11

Chapter 2 says the four task-sort buckets (AI-first, AI-assisted, human-led, pilot candidate) are "the operational twin" of a specific section of a specific other artifact. Which?

- A. The success-criteria section of the pilot charter (Chapter 3).
- B. The partner-coupling section of the roadmap one-pager (Chapter 5).
- C. The C1 artifact-class table in the team's human/machine contract (mod-101 Chapter 3). The roadmap and the contract must stay consistent; if they disagree, fix the contract first, then the roadmap.
- D. The DX Core 4 metric family instrumented by DevEx (mod-104).

## Question 12

Your team's successful 6-week pilot of a lakehouse-SQL authoring workflow is coming up for a hand-off decision. Per Chapter 5, which item is *most often skipped* in the graduation package to `ai-enablement-lead` and, when skipped, produces the most problems at scale?

- A. The pilot charter itself.
- B. The team-context signals section — why this worked on *your team* (team shape, tool surface, review bar, prior enablement). Without it, the enablement lead cannot tell what to replicate and what is you-specific, and the rollout fails at scale on invisible dependencies.
- C. The ROI narrative.
- D. The enablement artifacts (Cursor-rules file, AGENTS.md, onboarding deck).

---

## Answer key

1. **B.** Chapter 1 explicitly names "a tool procurement plan" as the first of four common deliverables that are confused with the roadmap and are *not* it. Procurement is owned at team scope in `mod-111`; the roadmap consumes that outcome. The roadmap's four questions — what, order, with whom, how-we'll-know — are prior to the tool choice. (Chapter 1, "What the roadmap is *not*" and "The decision about *what to automate* is prior to *how*.")
2. **B.** Chapter 2 names the two load-bearing properties as **jagged** and **invisible from the outside**. The frontier shifts with each model generation (so it is *not* stable) and cannot be predicted by domain or task description (so it is *not* publicly mapped or predictable from task type). The sort method in Chapter 2 exists precisely because the frontier is invisible — you find out by running the task through the model. (Chapter 2, "The frontier metaphor.")
3. **C.** Chapter 2's rule of thumb: any score of 1 in blast radius, verifiability, or judgment density forces the task into *human-led* regardless of the sum. The refund-email task scores 1 on blast radius and 1 on reversibility — customer-facing, hard-to-reverse — which is exactly the pattern the chapter calls out. The ≥18 threshold is necessary but not sufficient. (Chapter 2, "A six-dimension task-sort rubric" and "Four outcome buckets.")
4. **C.** Chapter 3 says the kill-criteria field is the one that matters most and that a single hedge ("no measurable improvement") is not an operational kill switch. Exercise 02's starter guidance reinforces this: "make at least one kill criterion about reviewer burnout or incident signal so it is operational, not just numeric." A pilot whose only stop condition is a null-result reading at week 6 tends to drift into a mini-rollout. (Chapter 3, "The pilot charter — what a pilot must have before it starts.")
5. **B.** Chapter 3 states the default sequence verbatim: opt-in during pilot, opt-out after a successful pilot, mandate only when the mandate came from somewhere else. Managers who start with mandate usually have to climb back down to opt-out within a quarter, and the climb-back is "expensive and visible." (Chapter 3, "Opt-in, opt-out (default-on), and mandate — the three adoption modes.")
6. **B.** Chapter 5 names exactly this signal — "a second team is asking for the same thing in their own roadmap" — as a graduate-to-Platform signal. The mechanism (Cursor-rules convention, AGENTS.md pattern) is generic enough that a second team benefits, so it belongs to Platform as shared infrastructure; your team becomes a reference user. Graduation to `ai-enablement-lead` is for *programmes* where the bottleneck is people and enablement, not infrastructure. (Chapter 5, "Pilots that should graduate out of the team.")
7. **B.** Chapter 4's "Four questions to ask of any survey before quoting it" names the exact four — sample, definition, compared-to-what, cross-reference — and the chapter says explicitly that surveys inform sequencing but headlines do not land in the roadmap body; ranges, not point estimates, go in the exec pre-read. Chapter 4's cadence section says to respond to exec forwards *with the four-question check, not with a yes.* (Chapter 4, "Three failure modes to avoid" and "Four questions to ask of any survey before quoting it.")
8. **C.** Chapter 4 says "reading each survey the day it drops is poor use of your time — the press-release framing is the loudest and the least useful." The other three cadence slots — quarterly for the knowledge-worker-level surveys, annually for the deeper reports, on model-generation events — are explicitly recommended. (Chapter 4, "Reading surveys at refresh cadence, not announcement cadence.")
9. **C.** Chapter 6 names the "why this and not that" section as the differentiator and says a plan that cannot name its alternatives is a plan that has not been thought through. Exercise 06's stretch guidance makes the trigger-to-revisit explicit — alternatives without a trigger are "closed debates" rather than "live options." The chapter also says the pre-read is written in the voice of the question the exec will ask and uses the exec's vocabulary; pre-reads must carry falsifiable commitments. (Chapter 6, "Artifact 4 — The exec pre-read ('why this and not that')" and "The failure modes to notice in yourself.")
10. **B.** Chapter 1's "The decision about *what to automate* is prior to *how*" section says explicitly that the task sort (Chapter 2) comes first, the adoption mode (Chapter 3) comes second, and only *then* do you pick tools and configuration. A team that mistakes its AGENTS.md and Cursor-rules files for the roadmap has skipped the task sort and the sequencing, and will not be able to answer "why this and not that" from leadership. (Chapter 1, "The decision about *what to automate* is prior to *how*.")
11. **C.** Chapter 2 says the four buckets are "deliberately the same shape as the C1 table in the human/machine contract (mod-101 Chapter 3)" and that "the two documents should match. … If they disagree, one of them is out of date — fix the contract first, then the roadmap." Chapter 6's "writing failure modes" section reinforces drift between contract and roadmap as a failure mode to notice. (Chapter 2, "Four outcome buckets.")
12. **B.** Chapter 5 flags section 3 — team-context signals — as "the one most often skipped and the most useful." The reasoning: the enablement lead needs to know what to replicate and what is you-specific (team shape, review bar, prior enablement, the specific senior IC who coached the cohort). Without it, the rollout fails at scale on invisible dependencies. (Chapter 5, "The graduation package to `ai-enablement-lead`" and the starter guidance in Exercise 05.)
