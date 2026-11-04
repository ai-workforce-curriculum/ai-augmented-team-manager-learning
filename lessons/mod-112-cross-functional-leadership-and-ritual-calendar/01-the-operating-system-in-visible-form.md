# Chapter 1 — The Team Operating System in Visible Form

> *The team's AI-augmented operating system is whatever is left on the calendar, the shared drive, and the decision log when the manager is on sabbatical. If a competent peer cannot pick up the team on Monday morning from those three artifacts alone, the operating system is in the manager's head — which is to say, it is not an operating system at all.*

## Motivation

By the end of mod-111 the team manager has eleven artifacts on the wiki: the contract and job spec ([`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/)), the adoption roadmap ([`mod-102`](../mod-102-team-ai-adoption-and-roadmap/)), the review standards and eval commissioning record ([`mod-103`](../mod-103-review-standards-and-eval-commissioning/)), the productivity and AI-ROI dashboard ([`mod-104`](../mod-104-productivity-measurement-and-ai-roi/)), the enablement-program design ([`mod-105`](../mod-105-team-ai-enablement-programs/)), the workflow catalog and tool-authorisation policy ([`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/)), the growth plan ([`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/)), the hiring and performance posture ([`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/)), the incident and post-mortem discipline ([`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/)), the governance evidence packet ([`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/)), and the tool registry ([`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/)). Each artifact is defensible in isolation. The problem the track has not yet solved is composition: the artifacts only generate value if someone *runs* them on a cadence, routes information between them, surfaces the outputs to peers and leadership, and keeps the whole stack legible to the next person who will own it.

mod-112 is where composition becomes the deliverable. It is the module that converts eleven artifacts into one *operating system* — a ritual calendar that generates the ongoing cadence, a cross-functional partnership map that locates decisions in the right room, an upward communication posture that lets leadership read the team without re-interviewing the manager, and a one-pager / decision-log hygiene that keeps the whole thing legible to a successor. Done well, the team operating system is boring in the best way: it runs, the evidence stacks up on cadence, decisions have provenance, and the manager is replaceable without rediscovery cost.

Three failure modes the module exists to prevent:

- **Calendar rot.** The ritual calendar accrues meetings that were justified when they were added and never audited against the measurement framework from [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/). Half the team's maker time is consumed by meetings whose decisions could be an async thread; the other half is in meetings the team no longer reads notes from. [Lencioni's *Death by Meeting*](https://www.tablegroup.com/product/death-by-meeting/) framing (four meeting types with distinct purposes) is ignored; every meeting becomes "the weekly" that drifts between tactical and strategic.
- **Cross-functional ambiguity.** The team ships, Product plans, Platform / DevEx ships infrastructure, Design ships patterns, Data owns analytics, AI-Governance owns the policy — and nobody has written down the decision rights. Each quarter a decision is made twice (once in each room), or not made at all. [Google re:Work's Project Oxygen](https://rework.withgoogle.com/en/guides/managers-identify-what-makes-a-great-manager/) manager behaviours — empowers the team; is a good coach; expresses interest in team members' success — lose their force when the cross-functional joints are undefined; the manager's good behaviours do not translate across function lines without explicit structure.
- **Upward illegibility.** The manager produces [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) productivity narratives, [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) incident retrospectives, [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) governance evidence, and [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) tool registry updates — and the four streams land on leadership as four unrelated reports. The reports are each individually clean; the story is fragmented. Leadership reads them separately, loses the connective tissue, and either over-corrects on one signal or under-reads the aggregate. The manager's operating-system effort is invisible in the one place it most needs to be legible.

This chapter does three things. First, it names the four composed pieces of mod-112 — the ritual calendar (Chapter 2), the cross-functional decision-rights map (Chapter 3), the upward communication posture (Chapter 4), and the one-pager / decision-log hygiene (Chapter 5) — plus the two reinforcing pieces (Chapter 6 on certifications as shared vocabulary; Chapter 7 on composition and ownership boundary). Second, it draws the scope boundary against the specialities the module deliberately does not try to own — board-level communication, program-wide ritual design, cross-team management, enterprise-change comms. Third, it names the Monday-morning *successor test* — the practical readability check the whole module optimises for.

## Core concepts

### What a team operating system means at this scope

A workable definition. The team operating system is the composition of:

- **A ritual calendar** — the rhythm at which planning, review, retro, demo, 1:1, office-hours, community-of-practice, incident, governance, and vendor-registry work actually happens, justified against the measurement framework.
- **A decision-rights map** — who decides what, with whom, on what cadence, across the Product / Platform-DevEx / Design / Data / AI-Governance partnership surface.
- **An upward communication posture** — the shape of the quarterly packet and the exec pre-read that composes the productivity, governance, incident, and tool-registry evidence into one coherent narrative.
- **A one-pager** — the artifact a new peer or new leadership partner can read in ten minutes and understand the team's shape, pattern of work, measurement, governance posture, and current initiatives.
- **A decision log** — the dated record of team-scope decisions, with rationale and reversal conditions, that lets a successor read the team's history without re-interviewing the departing manager.

The operating system is not a document. It is the set of practices that produce and maintain those five artifacts. The artifacts are the *evidence* the operating system is running; the practices are the system itself.

### The scope boundary — what this module deliberately does not own

This is a level-40 team-scope module. The boundary against adjacent and upward specialities is:

- **Not a board-governance course.** Board-level AI reporting, public commitments, and executive-suite AI narrative belong at [`head-of-ai-governance`](https://github.com/ai-governance-curriculum/head-of-ai-governance-learning) (L60) and [`chief-ai-officer`](https://github.com/ai-governance-curriculum/chief-ai-officer-learning) (L70). mod-112 covers the *board-adjacent* deck — the quarterly packet the manager produces that feeds the program-level roll-up those roles do for the board. The manager does not write the board narrative; the manager produces the evidence that lets someone else write it well.
- **Not a program-wide ritual-design course.** Multi-team ritual coordination — sister-team demo circuits, org-wide community-of-practice programs, enterprise-change comms — lives at [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) (L45) and [`ai-engineering-manager`](https://github.com/ai-engineering-curriculum/ai-engineering-manager-learning) (L50). mod-112 covers the team's own ritual calendar and the hooks that let the team participate in org-wide rituals cleanly.
- **Not an executive-coaching or leadership-theory course.** The module leans on two primary sources — [Lencioni's *Death by Meeting*](https://www.tablegroup.com/product/death-by-meeting/) and [Google re:Work Project Oxygen](https://rework.withgoogle.com/en/guides/managers-identify-what-makes-a-great-manager/) — as empirical anchors; it does not survey the broader leadership literature. The module's goal is practical competence at L40, not a theory of leadership.
- **Not a Scrum / Agile-method course.** Framework-level ritual canon — sprint ceremonies, scaled-agile cadence, Kanban governance — is prerequisite or orthogonal to this module. mod-112 asks "which ritual earns its slot on *this* team's calendar against *this* team's measurement framework", not "which framework does the team follow". A team on Shape Up, a team on classical Scrum, and a team on continuous-flow Kanban all run mod-112 with different inputs and the same discipline.
- **Not an exec-comms branding course.** Narrative is a means to an end: making the team's work legible so leadership can make better decisions and the team can be compared fairly in aggregate. The module does not teach storytelling as persuasion; it teaches it as a honest compression of real evidence.

A useful shorthand: the manager owns **cadence, legibility, and cross-functional interface** at team scope. Program architecture, board narrative, and multi-team coordination are the upward roles the manager's operating system *feeds*.

### The six pieces of mod-112

A mod-112-literate manager produces or refreshes six composed artifacts over the course of this module.

| Piece | What it does | Chapter | Exercise |
|---|---|---|---|
| **Ritual calendar** | The audited, measurement-justified calendar of all team rituals — planning, review, retro, demo, 1:1, office hours, CoP, governance retro, vendor-registry review, incident retro — with Lencioni meeting-type classification and calendar-budget accounting | 2 | [Exercise 01](exercises/exercise-01-ritual-calendar-audit-and-refresh.md) |
| **Cross-functional decision-rights grid** | The partnership map across Product, Platform / DevEx, Design, Data, AI-Governance, with decision rights per joint-work surface and the ritual cadence per partner | 3 | [Exercise 02](exercises/exercise-02-cross-functional-decision-rights-grid.md) |
| **Exec pre-read** | The quarterly packet that composes [`mod-102`](../mod-102-team-ai-adoption-and-roadmap/) roadmap, [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) productivity, [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) incident, [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) governance, and [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) tool-registry evidence into one coherent narrative | 4 | [Exercise 03](exercises/exercise-03-exec-pre-read-connecting-roadmap-to-roi-to-governance.md) |
| **Team one-pager + decision log** | The successor-readable one-pager that explains the team in ten minutes; the dated decision log that records team-scope decisions with rationale and reversal conditions | 5 | [Exercise 04](exercises/exercise-04-one-pager-and-decision-log-hygiene.md) |
| **Certifications portfolio** | The manager's own credential portfolio ([IAPP AIGP](https://iapp.org/certify/aigp/), [ISO/IEC 42001 lead implementer](https://www.iso.org/standard/81230.html) where applicable, others) and the shared cross-functional vocabulary it establishes | 6 | [Exercise 05](exercises/exercise-05-certifications-portfolio-planner.md) |
| **Composed operating system** | The composition of the above into a single artifact a successor can pick up without re-discovery | 7 | — (synthesis) |

Chapters 1 and 7 bracket the module. Chapter 1 names the problem, the pieces, and the scope. Chapter 7 is the composition chapter — how the pieces compose into the operating system and where the ownership boundary against upward and sideways specialities sits.

### The Monday-morning successor test

The whole module is optimised against a single scenario: a competent peer manager, hired externally or rotated in from a sister team, picks up the team on Monday morning with the current manager unavailable. By end of day Monday they must be able to:

- **Run the week.** They know which rituals happen on which days, who attends, what the purpose of each ritual is, and what the current open loops are. This requires the ritual calendar (Chapter 2) plus the current week's ritual notes and the one-pager (Chapter 5).
- **Answer a peer-partner message.** A Product partner messages about a joint decision. The successor knows who owns it, which room it is decided in, and what the current state is. This requires the decision-rights grid (Chapter 3) plus the decision log (Chapter 5).
- **Be legible to leadership.** Leadership asks for the state of the team on their next 1:1. The successor can read the last exec pre-read (Chapter 4), the one-pager (Chapter 5), and give a structured answer without inventing anything. The narrative has provenance; the numbers trace to source artifacts.
- **Flag the triggers.** The successor can see which governance triggers (from [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/)) and which incident-review items (from [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/)) are in flight and who owns them. This requires the decision log and the composed upward packet.

The test is practical. It is not an abstraction. The operating system either passes it or does not; the pieces of mod-112 exist so that it passes.

### How mod-112 composes with the rest of the track

- **Back-links.** Every other module's outputs land on this module's calendar or in this module's packet:
  - [`mod-102`](../mod-102-team-ai-adoption-and-roadmap/) roadmap reviews are a ritual on the Chapter 2 calendar and a section of the Chapter 4 pre-read.
  - [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) eval commissioning and review-standard audits land on the calendar.
  - [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) dashboard review is the measurement anchor that justifies every ritual; the AI-ROI narrative is the headline of the Chapter 4 pre-read.
  - [`mod-105`](../mod-105-team-ai-enablement-programs/) community-of-practice and office-hours are rituals; stage-ladder reviews land on the calendar.
  - [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) workflow catalog reviews land on the calendar; the tool-authorisation policy is cited in the pre-read.
  - [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/) growth 1:1s are a ritual; anti-atrophy signals surface in the pre-read.
  - [`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/) performance cycles are rituals with hard calendar anchors.
  - [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) incident retrospectives are a ritual; incident index is a section of the pre-read.
  - [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) governance retrospective is a ritual; the upward evidence packet from mod-110 Chapter 7 is the governance section of the Chapter 4 pre-read.
  - [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) tool-registry review is a ritual; the registry rollup is a section of the pre-read.
- **Forward links.** There is no mod-113 in this track; mod-112 closes the module sequence. The forward links are *upward* to [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning), [`ai-engineering-manager`](https://github.com/ai-engineering-curriculum/ai-engineering-manager-learning), [`senior-ai-governance-architect`](https://github.com/ai-governance-curriculum/senior-ai-governance-architect-learning), [`head-of-ai-governance`](https://github.com/ai-governance-curriculum/head-of-ai-governance-learning), and [`chief-ai-officer`](https://github.com/ai-governance-curriculum/chief-ai-officer-learning) — each of whom consumes the mod-112 artifacts in their own composition.
- **Sideways links.** The cross-functional partners — Product leadership, Platform / DevEx engineering management, Design leadership, Data / Analytics leadership, AI-Governance at team scope — each own their own operating system; mod-112 is the manager's side of the interface, not a replacement for the partners' practices.

## Example: the Monday-morning handoff that works

A composite shaped example — calibration, not a case study.

A level-40 engineering-team manager at a mid-sized SaaS company goes on a four-week sabbatical starting on a Monday. A peer manager from a sister team — hired six months ago, no prior exposure to this team — is asked to cover. The departing manager has run mod-112 for the last two quarters. The handoff is a 45-minute conversation on the preceding Friday afternoon.

What the peer manager reads over the weekend:

- **The one-pager.** Ten minutes. Team shape (8 engineers across 3 stages per [`mod-105`](../mod-105-team-ai-enablement-programs/)), workflow mix (product features ~55%, platform ~25%, incident response ~10%, discovery ~10%), measurement anchors ([`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) dashboard URL), current roadmap arc ([`mod-102`](../mod-102-team-ai-adoption-and-roadmap/) link), tool registry (link to [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) artifact), governance posture ([`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) upward packet link), named cross-functional partners (one line each), three open loops with named owner and expected resolution date.
- **The ritual calendar.** The next four weeks of rituals, each with purpose, attendees, last-session notes link, and classification (Lencioni type). The peer manager sees that Wednesday afternoon is the governance retrospective (reads the Q1 note before attending); Friday morning is the vendor-registry monthly check-in; Monday-Tuesday of week three is the quarterly review week with the exec pre-read due that Thursday.
- **The decision log.** The last six months of team-scope decisions, dated, with rationale and reversal conditions. The peer manager skims the last two weeks — sees that the team decided to pilot an agent framework (Chapter 3 "Wrap" stance from [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/)), sees the reversal condition ("if the wrap-layer maintenance exceeds two IC-days per month we revert to the vendor's default workflow"), sees the next review is in six weeks.
- **The decision-rights grid.** One page. Who decides what with whom on what cadence across the five partner functions. The peer manager sees that any roadmap item touching Design-system patterns needs joint sign-off from the Design partner at the Wednesday roadmap ritual.

Monday morning the peer manager:

- Runs standup; reads the roadmap at the right level of detail because they read the one-pager; defers the one tactical question they cannot answer to the IC who holds the context.
- Receives a message from the Product partner asking about a pilot's status; checks the decision log, finds the entry, replies with the current state without needing to ask the team.
- Gets a page from the governance program requesting the quarterly packet by Friday; the pre-read template is in the team drive with four of six sections pre-filled from the artifacts that already exist; the peer manager drafts the remaining two from the decision log.

By Wednesday the team is noticing the handoff worked. The peer manager is not performing the departed manager's judgement — they are running the operating system the departed manager left behind. The judgement calls that only the departed manager can make (specific people decisions, specific partnership-history nuances) have been flagged as *routed to return* or *held for cover's own call with the team's advisory*. The team keeps shipping. The quarterly packet lands on cadence. Leadership does not know the manager is away unless they check the signature.

This is the operating system passing the Monday-morning successor test. It is the practical deliverable of mod-112.

## Summary

- **The team operating system** is the composition of a ritual calendar, a decision-rights map, an upward communication posture, a one-pager, and a decision log — the practices that produce and maintain those artifacts, not the artifacts themselves.
- The failure modes the module prevents: **calendar rot**, **cross-functional ambiguity**, **upward illegibility**. The composed deliverable is a system a competent peer can pick up on Monday morning without rediscovery cost.
- **Six artifacts over the module**: [ritual calendar](exercises/exercise-01-ritual-calendar-audit-and-refresh.md), [cross-functional decision-rights grid](exercises/exercise-02-cross-functional-decision-rights-grid.md), [exec pre-read](exercises/exercise-03-exec-pre-read-connecting-roadmap-to-roi-to-governance.md), [one-pager + decision log](exercises/exercise-04-one-pager-and-decision-log-hygiene.md), [certifications portfolio](exercises/exercise-05-certifications-portfolio-planner.md), and the composed operating system (Chapter 7).
- **Scope boundary**: not board-level comms (upward to [`head-of-ai-governance`](https://github.com/ai-governance-curriculum/head-of-ai-governance-learning) L60 and [`chief-ai-officer`](https://github.com/ai-governance-curriculum/chief-ai-officer-learning) L70); not program-wide ritual design (upward to [`ai-enablement-lead`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning) L45 and [`ai-engineering-manager`](https://github.com/ai-engineering-curriculum/ai-engineering-manager-learning) L50); not leadership theory; not framework-canon agile; not comms branding.
- **The Monday-morning successor test**: a peer manager picks up the team cold, runs the week, answers the partner message, reads legibly to leadership, flags the triggers — all from the artifacts the operating system has produced. The whole module is optimised against this test.
- **Composes with every other module**: each module's outputs land on this module's calendar or in this module's packet. mod-112 is not independent content; it is the *composition* of the other eleven modules into a coherent cadence.
