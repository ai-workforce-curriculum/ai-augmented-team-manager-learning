# Exercise 04 — A Community of Practice Charter for Your Team

**Estimated effort:** 2 hours.

## Objective

Produce a **community-of-practice (CoP) charter** for your team that stands up the sustaining layer of the mod-105 programme. The output is a one-to-two-page artifact — `docs/mod-105-cop-charter.md`-style — that names the domain, the community, and the practice (the three Wenger-Trayner elements from Chapter 3), specifies the operating cadence, assigns a rotation of facilitators, defines the pattern-library mechanism, and names the sunset / scale-up triggers.

## Prerequisites

- Chapter 3 of this module.
- The [Wenger-Trayner introduction to communities of practice](https://www.wenger-trayner.com/introduction-to-communities-of-practice/) at reading level — 10 minutes.
- Your team roster plus any adjacent-team engineers you might reasonably invite as regular visitors.
- Awareness of whether a company-wide community of practice already exists (if so, the charter should name it and define the relationship, not compete with it).

## Problem statement

Your team is one quarter into a mod-105 programme. Cohort A has graduated past Day 90; Cohort B is at Day 60; Cohort C is about to kick off. The bootcamp-and-workshop phases carry the first 60 days; the sustaining layer that keeps fluency growing after Day 60 is the community of practice. Without a CoP, graduates regress — their fluency plateaus, workshop-learned patterns don't propagate, and new engineers joining the programme get a diluted version of what the first cohorts received.

The failure modes are all easy to walk into:

- **Slack-channel-only CoP.** "We have a #ai-practice channel." The channel is not the CoP. It is one tool the CoP may use.
- **Manager-run CoP.** You facilitate every session, curate every pattern, and the team reads the whole thing as a manager-led show. Participation drops.
- **Book-club CoP.** The sessions are consistently reading-together on vendor blog posts. The practice dimension is missing.
- **One-time-launch CoP.** You run the kickoff, mean to continue, and don't. Six months later the thing is a ghost channel.

Your job is to stand up the CoP with enough structural scaffolding that it survives the first six months, with a rotation that prevents any single person — including you — from becoming the single point of failure.

## Steps

1. **Name the domain.** One sentence on what this CoP is *about* for your team. Not "AI in general." Something like "AI-augmented practice on the Platform Infra team's workflows — our review standards, our delegation patterns, our tooling-specific patterns." Specific. If you cannot name the domain in one sentence, the CoP does not yet have a reason to exist.
2. **List the community.** Who is a member by default (the full team; typically ~15–25 engineers for a mod-105-sized team), who is a regular visitor (e.g. 3–5 engineers from adjacent teams who work closely with yours), who is a sponsor (you, the manager). Specify how people join (default on team join; opt-in for adjacent-team engineers), how people leave (default on team leave; explicit opt-out otherwise).
3. **Name the practice elements.** The shared repertoire. At minimum: the pattern library (where it lives — a repo, a Confluence space, a Notion doc), the show-and-tell format (10 min walk, 15 min Q&A, 15 min pattern extraction), the review-of-the-review quarterly session format.
4. **Set the operating cadence.** Specify, with concrete dates for the first two months: show-and-tell cadence (Chapter 3 recommends bi-weekly 45 min); pattern-library review cadence (monthly 30 min); review-of-your-review session cadence (quarterly 90 min); cross-team visit cadence (quarterly).
5. **Assign the facilitator rotation.** A rotation of 3–5 engineers across the first two quarters, each facilitating one or two sessions. You, the manager, are on the rotation but not as a majority. Specify: who facilitates each of the first ~8 scheduled sessions, who curates the pattern library (rotating quarterly or longer).
6. **Specify the pattern-library mechanism.** How does a pattern get *into* the library? Who writes it? What is the format (a title, a problem shape, a response shape, a reference to the originating work)? When does a pattern age out?
7. **Write the no-ops.** Explicitly state what the CoP is *not* (per Chapter 3): not a Slack channel, not a book club, not a working group, not an org-wide initiative. Each of these is a failure mode the charter prevents.
8. **Define the relationship with any pre-existing CoP in your org.** If your organisation already has a company-wide AI community of practice (often owned at `ai-enablement-lead` level — see Chapter 8), name it, name how it differs in domain scope, and name the interface (cross-visits? attend each other's sessions? share pattern-library entries selectively?).
9. **Set the health check.** A single line in the charter: *"this CoP is healthy if the facilitator rotation is holding, at least one new pattern lands in the library per month, and at least 60% of the team attends at least one session per quarter."* Put the review date in your calendar.
10. **Set the sunset / scale-up triggers.** Three one-line triggers for charter review: (a) the community has grown past 30 members (scale-up trigger — see Chapter 8); (b) the facilitator rotation has collapsed to one person (sunset or restart trigger); (c) the pattern library has had no new entries for two consecutive months (dormancy trigger).
11. **Freeze v0.1.** Title: `mod-105 Community of Practice Charter v0.1 — [team name] — [YYYY-MM-DD]`. Author (you). Reviewers (one of the facilitator-rotation engineers; one visitor from an adjacent team if you have agreement to include them). Scope-and-caveats paragraph. Change log. Review date six months out.

## Starter guidance

- The CoP charter is the programme's *least-used* artifact day-to-day but the most-referenced when the sustainment layer is wobbling. Write it so that it can carry the CoP through one bad quarter.
- The three Wenger-Trayner elements (domain, community, practice) are the structural check. Walk the first draft and point at the sentence in the charter that establishes each. If any of the three is missing, the CoP is a shell per Chapter 3.
- Facilitator rotation of 3–5 is the minimum. Fewer than 3 is a manager-run show; more than 5 is diffuse and the quality of session preparation drifts.
- The pattern library is the CoP's *persistent artifact*. Sessions are ephemeral; the library is durable. If the library is empty after three months, the CoP is not generating long-term value even if attendance is strong.
- Budget your manager time: ~45 min bi-weekly for CoP attendance; ~30 min monthly for pattern-library review participation; ~90 min quarterly for the self-review session. ~5 hours/quarter. This is on top of the per-cohort delivery time from Exercise 01.
- The cross-team visit cadence is often where the most leverage is. An engineer from a neighbouring team presenting a specific pattern they invented brings fresh signal and keeps your CoP from going insular. Don't skip this one.
- Avoid letting the CoP become a project tracker. Patterns are not tickets. If engineers are using the pattern library as a backlog, the mechanism has drifted — reset at the next monthly review.

## Acceptance criteria

The charter is complete when:

- The three Wenger-Trayner elements — domain (one sentence), community (membership), practice (named elements) — are each explicitly stated.
- An operating cadence is specified with concrete dates for at least the first two months.
- A facilitator rotation of 3–5 engineers is assigned across at least the first 8 sessions; the manager is in the rotation but not the majority.
- A pattern-library mechanism is specified: location, format, contribution process, aging-out criterion.
- An explicit no-ops section names the four Chapter 3 failure modes and states they do not apply.
- The relationship with any pre-existing org-wide CoP is named (or an explicit "no such CoP exists" note).
- A health-check line is stated with specific thresholds.
- Three one-line sunset / scale-up triggers are stated.
- The artifact is titled, dated, lists contributors, carries scope-and-caveats and a change log, and has a six-month review date.
- The manager time budget for CoP participation is explicit.
- The charter fits on one to two printed pages.

## Stretch goals

- **A pre-populated pattern library.** Seed the library with three to five patterns drawn from your team's recent work — often sourced from the Day-60 pair-with-agent reflections from Cohort A. A library that starts non-empty gets its first contributions faster than one that starts blank.
- **A cross-team visit calendar.** Line up the first two quarterly cross-team visits in advance. Named teams, named presenters. Rarely do these happen if they are not scheduled in advance.
- **A manager-handoff note.** Write a half-page note to a hypothetical next manager on *how the CoP works* — specifically the rotation and the pattern library, which are the parts that fail silently under a change of leadership. Keep this with the charter.
- **A visitor invitation template.** Draft the one-paragraph invite you would send to engineers in adjacent teams inviting them to attend as regular visitors. Short, specific, names what they will get (fresh signal, cross-team pattern access) and what you ask (attendance at ~2 sessions/quarter).
- **A dormancy-recovery plan.** For the dormancy trigger (two months no new patterns), write a one-paragraph plan for what you will do. Usually: pick a specific recent work item from the team, pair-with-an-engineer to extract the pattern, publish it, and schedule the next show-and-tell to feature it.
