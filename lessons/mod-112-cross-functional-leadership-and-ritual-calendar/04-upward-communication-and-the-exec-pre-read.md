# Chapter 4 — Upward Communication and the Exec Pre-Read

> *Leadership will decide something about your team this quarter. If the decision is made from your pre-read, it will be a better decision than if it is made from a Slack thread or a half-remembered 1:1. The pre-read is not a status report; it is the artifact that lets a VP think about your team with the same resolution you do, in twenty minutes of their time.*

## Motivation

The manager who has run mod-101 through mod-111 has a lot of evidence: a roadmap with dated adoption commitments ([`mod-102`](../mod-102-team-ai-adoption-and-roadmap/)); review and eval artifacts ([`mod-103`](../mod-103-review-standards-and-eval-commissioning/)); a productivity dashboard with DORA, SPACE, DX Core 4 and flow tiles ([`mod-104`](../mod-104-productivity-measurement-and-ai-roi/)); a stage-ladder enablement program ([`mod-105`](../mod-105-team-ai-enablement-programs/)); a workflow catalog with tool-authorisation policy ([`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/)); growth plans ([`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/)); hiring posture ([`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/)); incident retrospectives ([`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/)); a governance evidence packet ([`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/)); a tool registry ([`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/)). Eleven artifacts. Each has a defensible shape. Each has an audience inside the team or in a specific partner function.

The problem the chapter solves: leadership (the manager's manager, their VP, and the governance program above) does not read eleven artifacts. Leadership reads *one* artifact per quarter — a pre-read — that composes the relevant subset of the eleven into a narrative the VP can act on. The question is not *whether* to produce one; leadership will act on *something* each quarter regardless. The question is whether that something is the manager's structured pre-read or an unstructured impression stitched together from 1:1 memory, Slack, and the loudest signal of the week.

Three failure modes the chapter prevents:

- **Dashboards-as-narrative.** The manager forwards the [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) dashboard URL to the VP with a Slack message saying "numbers for the quarter." The VP looks at the tiles, infers a story that may or may not match the manager's, and makes decisions from that story. The manager finds out at the leadership review that the VP concluded something the data did not support. This is the failure mode [`mod-104` Ch. 7](../mod-104-productivity-measurement-and-ai-roi/07-the-ai-roi-narrative-for-leadership.md) addresses *at the narrative level*; this chapter addresses it *at the composition level*.
- **Four-separate-reports syndrome.** The manager produces four separate reports: productivity ([`mod-104`](../mod-104-productivity-measurement-and-ai-roi/)), incidents ([`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/)), governance ([`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/)), vendor spend ([`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/)). Each is clean. Leadership reads them separately; the connective tissue — *the incidents are retrospected because the governance posture requires it; the spend is distributed because the enablement stages require it; the productivity is what it is because the roadmap-and-adoption curve shaped it* — is invisible. Leadership makes locally reasonable decisions from each report that are globally incoherent for the team.
- **Board-level overreach.** The manager, excited to be read seriously by leadership, drafts an executive narrative in the voice of a board report. The board report exists at [`head-of-ai-governance`](https://github.com/ai-governance-curriculum/head-of-ai-governance-learning) L60 and [`chief-ai-officer`](https://github.com/ai-governance-curriculum/chief-ai-officer-learning) L70 scope. The L40 pre-read is *board-adjacent*: it feeds up to the roles that write the board narrative; it does not try to be one. Over-reaching here produces a document that is simultaneously too coarse for the team's own operation and too fine for the board's attention, and is therefore useful to neither.

This chapter does four things. First, it names the pre-read's structural shape at L40 — the sections, the length, the audience. Second, it describes the composition discipline — how to connect the four streams ([`mod-102`](../mod-102-team-ai-adoption-and-roadmap/) roadmap, [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) productivity, [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) incidents, [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) governance; [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) vendor) into one coherent story without flattening them. Third, it draws the boundary against the board-level narrative that lives at L60 / L70. Fourth, it describes the cadence and the delivery discipline — when the pre-read lands, who reviews it before leadership, how the response is handled.

## Core concepts

### The pre-read structure

A workable shape for the quarterly exec pre-read. Length: **4–8 pages** including the executive summary, exclusive of linked appendices. The appendices are the eleven backing artifacts; the pre-read is the composition, not the artifacts.

**Sections, in order:**

1. **Executive summary (half page).**
   - Team name, scope, period covered, author, date, version.
   - The *one-line claim* the pre-read is arguing (e.g., "The team hit its Q3 roadmap in full, AI-adoption is through enablement stages 1–3 for all ICs, and the governance posture has two open gaps routed upward"). This is the sentence the VP tells their manager in the hallway.
   - Three to five bullets — material facts the audience should hold while reading the rest.
   - Named sign-off (manager; where joint sign-off is practice, the governance peer and the PM counterpart).
2. **The roadmap-to-outcome arc (one page).**
   - What the team committed to for the period (back-link to [`mod-102`](../mod-102-team-ai-adoption-and-roadmap/)).
   - What landed; what slipped; what was swapped.
   - The *outcome tile movement* that corresponds. Not activity volume — outcome. The roadmap commitment is *in service of* an outcome; the pre-read ties them together.
3. **The productivity and AI-ROI narrative (one page).**
   - The [`mod-104` Ch. 7](../mod-104-productivity-measurement-and-ai-roi/07-the-ai-roi-narrative-for-leadership.md) narrative, compressed.
   - Headline tiles: DORA, DX Core 4, flow, AI-cost tile.
   - What moved, what did not; honest attribution of drivers (roadmap, enablement, tooling, external; not just AI).
   - The *anti-activity-theatre* paragraph ([`mod-104` Ch. 8](../mod-104-productivity-measurement-and-ai-roi/08-qualitative-signal-against-activity-theatre.md)): where qualitative signal contradicts or complicates the quantitative picture.
4. **The governance and incident posture (one page).**
   - Count of incidents in period by class ([`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) classes).
   - Headline change in [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) gap register: opened, closed, routed upward.
   - Material policy / standard changes landed on the team.
   - Any routed-upward flag (counsel trigger, program trigger) with its state.
5. **The vendor and tool-registry posture (half page).**
   - Headline AI-spend; delta vs prior period; projection for next period ([`mod-111` Ch. 5](../mod-111-vendor-budget-and-tool-selection-at-team-scope/05-tool-and-token-budget-distribution.md)).
   - Registry adds, keeps, sunsets in period.
   - Any trial-status tools with a dated deadline.
6. **People and enablement (half page).**
   - Stage ladder distribution across the team ([`mod-105`](../mod-105-team-ai-enablement-programs/)).
   - Headcount changes in period.
   - Growth-plan and [`mod-107`](../mod-107-skill-growth-anti-atrophy-and-career-development/) anti-atrophy signal (not individual performance; team-level indicators only).
   - Any hiring plans for the next period.
7. **The ask (half page).**
   - What the manager is asking leadership for. One or two items, named, with a decision requested, a decision deadline, and the consequence of missing the deadline.
   - If nothing is being asked, state so explicitly; "no asks this quarter" is a legitimate entry and signals the team is in steady state, which is itself information.
8. **The open loops and next period's shape (half page).**
   - Open loops carried forward: gaps, in-flight decisions, trials with deadlines.
   - Next period's roadmap at headline level.
   - Next period's calendar changes (ritual retirements, additions, cadence shifts).
9. **Appendices.** Linked, not duplicated. The eleven backing artifacts; the decision log; the current ritual calendar; the one-pager.

A pre-read following this structure prints to about 6 pages and reads in 15–20 minutes. The executive summary is readable in 3 minutes for a VP skimming before the review; the whole thing is readable before a leadership offsite. If the pre-read exceeds 10 pages, the composition has failed — detail has leaked out of the appendices into the body.

### The composition discipline — connecting the four streams

The pre-read's real work is composition. The manager is connecting four streams — adoption / roadmap, productivity / ROI, incidents, governance — into one story. The *shape* of the composition is the single most important choice in the whole module.

The default composition pattern (works most quarters, deviates when the quarter was unusual):

- **The roadmap is the spine.** The quarter is organised around what the team committed to and delivered. The productivity, governance, and incident sections are *in service of* the roadmap narrative.
- **The productivity section reads the spine.** "The roadmap commitments landed because X; the throughput enabling X came from these drivers (AI assist, team maturity, platform investment); the attribution is honest about which of those drivers was most load-bearing." Not: "here are our DORA numbers."
- **The governance section protects the spine.** "The roadmap was delivered within the governance posture — zero material incidents, two gaps opened and routed, the Article 14 workflow sheets for the shipped features are filed." Not: "here is the gap register."
- **The tool / vendor section funds the spine.** "The AI spend of $X supported the throughput noted in Section 3; the registry is current; the next-period projection is $Y." Not: "here are the tools we use."
- **The people section populates the spine.** "The stage ladder has moved; the team added one engineer; two are at a growth-plan inflection. The capacity to deliver the next period's roadmap is accurately projected because the enablement program has moved N engineers up a stage." Not: "we have 8 ICs."

Variations:

- **The quarter dominated by an incident.** Spine shifts to "the incident, the response, and what has changed." The roadmap, productivity, governance sections thread through that story. Treat the incident narrative with [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/) blameless-post-mortem discipline — the pre-read is not a punishment ritual; it is an accountability ritual.
- **The quarter where productivity moved markedly.** Spine shifts to the AI-ROI story; roadmap becomes evidence; governance and vendor become context. The anti-theatre discipline from [`mod-104` Ch. 8](../mod-104-productivity-measurement-and-ai-roi/08-qualitative-signal-against-activity-theatre.md) applies hardest here — a quarter with dramatic quantitative movement deserves extra qualitative scrutiny in the pre-read, not less.
- **The quarter dominated by a governance event.** New policy landed, external audit finding, regulator-adjacent inquiry. Spine shifts to the governance posture; the rest supports.

In all cases: *there is one spine*. A pre-read with four spines is four pre-reads stapled together, which is the failure mode this chapter names.

### The board-adjacent / board-level boundary

The L40 pre-read is explicitly *board-adjacent*, not *board-level*. The boundary:

| Attribute | Board-adjacent (L40 pre-read) | Board-level (L60 / L70 narrative) |
|---|---|---|
| Audience | Direct manager (VP or director); governance program peer (L50) and lead (L60); sometimes the function head (L50+) | Board of directors; audit committee; executive leadership team |
| Scope | One team | Program; organisation-wide |
| Horizon | One quarter; next quarter's shape | Fiscal year; multi-year strategic arc |
| Confidence | Precise ("Q3 shipped 12 of 14 roadmap items"); specific ("one Article 14 sheet for workflow X") | Aggregated ("the AI program delivered N% of portfolio objectives"); strategic ("the firm's AI posture is appropriate for the regulatory environment") |
| Regulatory and legal position | Routes triggers upward; does not interpret statute | Represents the firm's legal position (through counsel sign-off) |
| Audit evidence | Produces evidence; references audit artifacts by link | Represents the firm to external auditors |
| Public commitment | Does not make public commitments | May represent the firm's public responsible-AI commitments |

Two practical lines beyond the table:

- **Language register.** The board-level narrative uses language that is simultaneously broader and more conservative — "the firm's AI posture", "material risk", "appropriate mitigation". The L40 pre-read uses precise, specific language — "the team shipped X", "we routed Y to counsel". Writing in board-level register at L40 is a signal of over-reach that leadership will read as noise.
- **Signatures.** The L40 pre-read signs: manager, often PM, often governance peer. The board narrative signs: [`chief-ai-officer`](https://github.com/ai-governance-curriculum/chief-ai-officer-learning), with contributions from [`head-of-ai-governance`](https://github.com/ai-governance-curriculum/head-of-ai-governance-learning) and counsel. An L40 pre-read signed "on behalf of the AI program" is over-reach.

### Cadence and delivery discipline

The pre-read does not land on the day of the leadership review. A realistic timeline for a quarterly pre-read:

| Week | Activity |
|---|---|
| **Quarter end + 1 week** | Freeze the data; pull from dashboards, gap register, tool registry, incident index |
| **+ 1 week** | Draft the composition (spine, four stream connections). Primarily writing; not research |
| **+ 2 days** | Internal review: PM counterpart, governance peer read for honesty and shape |
| **+ 2 days** | Revision; address review notes |
| **+ 2 days** | Deliver to direct manager (VP) at least 48 business hours before the leadership review it informs |
| **+ 1 day** | Office hours with the VP if they want to push back or ask questions before the review |
| **Leadership review day** | VP reads the pre-read before the meeting; the manager is prepared with one slide, not the full document |

Two pieces of delivery discipline:

- **48 business hours is the floor.** A pre-read delivered the morning of the review is treated as an attempt to avoid scrutiny. A pre-read delivered a week ahead gives the VP time to form real reactions and the manager time to respond.
- **The pre-read is the artifact; the meeting is not the artifact.** The VP will read the document and decide most of what they are going to decide from it. The meeting is for discussing the one or two items the manager flagged as asks or the VP flagged for push-back. This is the opposite of the "I'll walk you through it" pattern, which is a sign the document cannot stand alone.

### Review discipline before leadership sees it

Three internal reviewers should see the pre-read before leadership:

- **PM counterpart.** Reads for roadmap-and-outcome honesty. Challenges where the manager has credited the team for an outcome driven by product, or vice versa.
- **Governance peer (or `ai-risk-engineer` peer at L25).** Reads for governance-and-incident honesty. Challenges where the manager has softened a gap-register entry or elided an incident class.
- **One peer manager from a sister team.** Reads for *structural* honesty — does the pre-read make sense to someone who does not live inside the team? Does the one-line claim actually support the detail?

The reviewers do not sign off; they review. Their feedback goes in the revision. The manager still owns the pre-read.

### What the pre-read is not

- **Not a dashboard dump.** The dashboard is linked in appendices; the pre-read interprets it.
- **Not a sales deck for the team.** The pre-read's job is honest compression; a pre-read that only shows wins is not trusted on the second quarter it is read.
- **Not a punishment artifact.** Incidents and gaps are reported in blameless framing. A pre-read that reads as accountability-theatre destroys the next quarter's ability to surface the same information.
- **Not a venue for new decisions.** Decisions that warrant a pre-read's "ask" section should already have been in discussion; the pre-read formalises the ask. New decisions landing in a pre-read ambush the VP, which is exactly the thing the structure is supposed to prevent.
- **Not a venue for personnel actions.** Individual performance, hiring, and termination decisions belong in 1:1 and performance-cycle channels ([`mod-108`](../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/)); the pre-read reports team-level signals, not individual actions.

## Example: the pre-read that moved a decision

Composite — calibration.

An L40 engineering-team manager has been running the quarterly pre-read for a year. The Q4 pre-read lands on the VP's desk on Tuesday morning; the quarterly leadership review is Thursday afternoon. The one-line claim at the top of the pre-read:

> "The team delivered its Q4 roadmap in full, AI-adoption is stabilised at Stage 3–4 across the team, and the DX Core 4 and flow tiles have moved materially — but the gain is being offset by a growing eval-regression backlog that needs dedicated capacity in Q1."

The pre-read's spine is the roadmap; the productivity section documents the DX and flow gains; the governance section notes zero material incidents and one open gap (routed); the tool-registry section is unchanged; the people section notes one hire landing in Q1. The *ask* section:

> "Request: allocation of ~15% of Q1 capacity to an eval-regression burndown, owned by the review-standard owner. Decision needed by Dec 15 (Q1 planning). Consequence of no decision: the team will carry the eval regressions into Q1 and the review-standard owner will be forced to triage ad-hoc, which will show up as either review-latency regression (DX Core 4 tile) or standard-adoption drift (mod-103 artifact) by end of Q1."

The VP reads the pre-read on Tuesday. Wednesday, in a 20-minute office hour, they push back: "Why can't the eval work be absorbed by the throughput gain?" The manager, prepared, says: "It is being absorbed by throughput gain — the gain is real. But the throughput is going to feature work per the PM's Q1 roadmap, which you signed last month. The 15% is *in addition to* that; if we don't name it explicitly, the eval work is what gets dropped." The VP: "Fine. Name it in the Q1 roadmap commit. I'll back you with the PM."

Thursday's leadership review: the pre-read is already read. The VP moves to the ask quickly; the item is agreed in two minutes. Three other teams' pre-reads are also on the agenda. The review ends on time.

Four weeks later, the eval-regression burndown is Q1 Week 2 work; the review-standard owner has capacity; the DX Core 4 review-latency tile is holding. In the Q1 pre-read the manager cites this as a worked loop — the Q4 ask produced a Q1 outcome.

The pre-read did its job. It compressed four streams into one spine. It made an ask concrete. The VP made a good decision quickly because the artifact let them. The review was the shorter and better for it.

## Summary

- The **exec pre-read** is a single composed artifact — 4–8 pages, delivered 48 business hours before leadership review — that connects [`mod-102`](../mod-102-team-ai-adoption-and-roadmap/), [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/), [`mod-109`](../mod-109-accountability-incident-response-and-blameless-postmortems/), [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/), and [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) evidence into one coherent narrative.
- The **composition discipline**: one spine (usually roadmap-to-outcome); other streams in service of the spine; no four-spines pre-read. Variations in exceptional quarters shift which stream is the spine; they do not add a second spine.
- The **sections**: exec summary, roadmap-to-outcome, productivity / ROI, governance / incidents, vendor / tool registry, people / enablement, the ask, open loops / next period, linked appendices.
- The **board-adjacent / board-level boundary** is explicit: L40 pre-read is specific, precise, single-team, quarterly; board-level narrative is aggregated, strategic, program-wide, annual, and belongs to L60 / L70 roles. Writing in board register at L40 is over-reach.
- **Cadence**: data freeze week 1 of new quarter; draft week 2; internal review; deliver 48 business hours pre-review; VP office hours before the review; one slide at the review itself.
- **Review discipline**: PM counterpart, governance peer, one sister-team peer manager read for honesty before leadership does.
- The pre-read is **not** a dashboard dump, a sales deck, a punishment artifact, a venue for new decisions, or a personnel-action channel. It is the compressed, honest, composed account of the team for the audience whose decisions shape the team.
