# Lab 03 — Backfeed-Ticket Conversion from a Post-Mortem's Section 7

**Duration:** 45–60 minutes.
**Chapters exercised:** Chapter 6 (the backfeed ticket shape — title / source incident / destination artifact / named person owner / close-out criterion / date; the eval row as the highest-leverage output with the *demonstrated red-to-green in CI* requirement; the seven backfeed destinations — review checklist, standards-as-code, eval, routing matrix, HITL checkpoint, tool authorisation, contract change-log; *"what makes a ticket stall";* the incident-to-eval metric), with side-checks against Chapter 2 (Step 7 Close as the step the tickets open under), Chapter 3 (Section 7 of the post-mortem template as the source of the free-text action items being converted), and Chapter 5 (ticket ownership that belongs to `ai-risk-engineer` when the method requires it — specifically eval rows requiring a fixture framework or an LLM-as-judge rubric).
**Complements, does not duplicate:** [Exercise 05](../exercises/exercise-05-regression-fixture-backfeed-ritual.md) asks you to design the **recurring weekly cadence** that keeps the backfeed moving quarter over quarter — the standing calendar slot, the dashboard, the escalation path for stuck tickets — and run it against a worked case. This lab is the **narrower, upstream step**: given a post-mortem that has already shipped with free-text action items, convert each into a specific Chapter 6 ticket before the ritual ever gets to see it. A team whose post-mortems hand the ritual free-text action items will stall at the first ritual (Chapter 6's *"what makes a ticket stall"* list is exactly the failure modes a free-text hand-off triggers); a team whose post-mortems hand the ritual tickets in the Chapter 6 shape will have the ritual's close-out check actually land.

## Objective

Given a shipped **post-mortem write-up (v1)** for a fictional composed Class 1 + Class 3 incident, (i) **convert each of the four free-text Section 7 action items into a Chapter 6 backfeed ticket** with the six required fields (title, source incident, destination artifact — specific file path or doc, named human owner, close-out criterion, date); (ii) **identify which of Chapter 6's seven backfeed destinations** each ticket lands against (review checklist / standards-as-code / eval / routing matrix / HITL checkpoint / tool authorisation / contract change-log) and flag any destination the write-up has missed; (iii) **demonstrate the eval row's red-to-green plan** per Chapter 6's requirement that *"a row that passes on initial run has not demonstrated what it is for";* and (iv) **compare against the answer key**.

Target: **all four tickets have all six fields with a named human owner (not a team or a role), destination artifacts are specific file / doc paths (not categories), the eval-row ticket names a red-to-green demonstration plan with a specific reproduction fixture, and you identify the one backfeed destination the write-up has missed** (Chapter 6's incident-to-eval discipline: *every confirmed incident produces at least one eval row*; this write-up will fail that check if the missing destination is not added).

## Prerequisites

- Chapter 6 read end-to-end — the backfeed ticket shape, the seven destinations, the eval-row discipline with the red-to-green requirement, *"what makes a ticket stall,"* and *"common failure modes."*
- Chapter 2 Step 7 skimmed — the close-out destinations the tickets land against.
- Chapter 3 Section 7 (*"Action items"*) skimmed — the post-mortem template's action-items section is the source of the free-text to convert.
- A blank file for your tickets.
- A timer.

## The fictional context

> **Sev-2 incident at Lumen Routing**, an 11-engineer platform team (1 staff, 3 senior, 7 mid). Owns a customer-support agent (*"RouteAssist"*) that drafts replies to tier-1 tickets and a customer-tooling repo. RouteAssist runs on Claude Code via the organisation's shared gateway; the agent has authorisations to read the customer-config database (`cust_config` schema, read-only) and to call the internal knowledge-base RAG. On **2026-10-21**, an engineer who was debugging a flaky RouteAssist session asked the agent to *"check whether this customer's routing policy has changed recently"*. The agent — through a sequence of reasoning on the ambiguous prompt — called the `cust_config` read tool with a query that returned a JSON blob containing the customer's routing policy **and** an adjacent field (`internal_sla_notes`) that the engineer did not have the business role to see, then included the `internal_sla_notes` content *verbatim in the drafted customer reply*. The engineer caught it before sending. No external exposure. The engineer flagged the incident; post-mortem ran the following Friday. The write-up shipped on 2026-10-29. The team's accountability contract (mod-103 Chapter 5) is pinned; the runbook v0.2 names the backfeed destinations per Chapter 6. The weekly backfeed ritual runs Monday 10:00-10:20; this is Thursday 2026-10-29 and the next ritual is Monday 2026-11-02. `ai-risk-engineer` is a peer (L25, AI Governance family) reachable via `#ai-risk`.

Score the conversions against *Chapter 6's ticket discipline as written*, not against an idealised "thorough write-up." Chapter 6 is explicit: *"the specificity matters. 'Update the review checklist' is not actionable; 'add row 14 to `/docs/ai-review-checklist.md` requiring diff-vs-prior snapshot for AI-authored pipeline changes' is."*

## The post-mortem v1 — Section 7 as shipped

Pin this to a scratch file. You will convert each action item in Step 2.

```
# Post-mortem — 2026-10-21 RouteAssist cross-field-leak incident
#                 (v1 — shipped 2026-10-29)

## 1. Summary
On 2026-10-21 the RouteAssist agent, in the course of a tier-1 customer
support ticket draft, included `internal_sla_notes` content (which the
drafting engineer does not have the business role to see) verbatim in the
draft reply. The engineer caught it before sending; no external reach.
Severity Sev-2. Incident class: Class 1 (hallucination-driven harm —
treating internal content as customer-safe) + Class 3 (unauthorised tool
use — the `cust_config` read authorisation was scoped at the schema level
when it should have been scoped at the field level), composed.

## 2. Impact
Zero external reach. The incident surfaced that the `cust_config` read
authorisation is one level too loose (schema-wide instead of field-level)
and that RouteAssist's reply-drafting policy does not include a step that
separates "retrievable" from "customer-safe-to-include."

## 3. Root causes
Walked outside-in per Chapter 3.
- Layer 1 (reviewer): the engineer caught the content pre-send, so the
  human catch worked. But the catch was on the specific wording of the
  content, not on the authorisation surface; a different wording on the
  same content would have passed.
- Layer 2 (IC/prompter): the engineer's prompt was ambiguous ("check
  whether this customer's routing policy has changed recently"). Second
  story: the engineer did not realise the `cust_config` tool returns
  adjacent fields in the same JSON blob.
- Layer 3 (harness and policy): the `cust_config` read tool is scoped at
  the schema level in the harness configuration; the policy intent was
  "routing policy only" but the authorisation is schema-wide. No HITL
  checkpoint exists between the agent's tool-call return and the reply
  draft for the content-safety classification.
- Layer 4 (prompt and retrieved context): the JSON blob returned by the
  tool call included `internal_sla_notes` as an adjacent field; the
  agent included it in the draft because the context implied it was
  relevant to the "routing policy" question.
- Layer 5 (model behaviour): the model's behaviour is a Chapter 4 Class 1
  harm (confidently treating internal content as customer-safe), downstream
  of the Layer 3 + Layer 4 findings. No Layer 5 action item on its own;
  the fix is at Layer 3 (authorisation + HITL) and Layer 4 (tool-return
  filtering).

## 4. Trigger
Engineer prompted RouteAssist at 14:02; drafted reply visible at 14:03;
engineer caught the leak at 14:05.

## 5. Resolution
Engineer deleted the draft; RouteAssist session terminated; no further
action. Full containment in under 10 minutes.

## 6. Detection
Caught by the drafting engineer before send. The downstream-consumer
detection channel did not fire because nothing shipped.

## 7. Action items
1. Tighten the `cust_config` authorisation. It's currently schema-wide;
   it should be narrower. Team manager will look at this.
2. Add a thing to the AGENTS.md file so RouteAssist doesn't paste
   `internal_sla_notes` into customer-facing content. Someone on the
   team needs to write this.
3. The review checklist for RouteAssist-drafted replies probably needs
   a row about checking for internal-only fields in the draft. We will
   add this.
4. The engineered-risk peer will be informed and the engineer will chat
   with them about what guardrails look like.

## 8. Lessons learned
- What went well: the engineer caught the leak pre-send.
- What went wrong: the authorisation surface was wider than the policy
  intent, and the agent had no tool-return filter.
- Agent-behaviour note: given the tool-return JSON including the
  adjacent field, the agent produced a reply that incorporated it.
  (Factual narration per Ch. 3.)
- Where we got lucky: the engineer noticed. A fresher engineer or a
  busier queue might not have.

## 9. Timeline
- 2026-10-21 14:02 — engineer prompted RouteAssist.
- 2026-10-21 14:03 — RouteAssist drafted reply with `internal_sla_notes`
  verbatim.
- 2026-10-21 14:05 — engineer caught; session killed.
- 2026-10-24 10:30 — Friday post-mortem meeting.
- 2026-10-29 — write-up shipped.

## 10. Supporting evidence
- Claude Code session archive: <link to session JSON in LangSmith trace archive>
- Tool-call return JSON: <link to the `cust_config` return payload>
- As-submitted draft (before delete): <link to the draft message>
- Checklist in effect: `/docs/routeassist-review-checklist.md` v2.1
- AGENTS.md revision: 2026-09-15
- Tool authorisation config: `/config/cust-config-tool-auth.yaml`
- No commissioned eval covered this behaviour.
```

Note the **four free-text action items in Section 7**. The rest of the write-up is in reasonable Chapter 3 shape (outside-in walk, factual narration, Section 10 trace links). Section 7 is where Chapter 6's ticket discipline has to land, and v1 as shipped has not landed it.

## Steps

### Step 1 — Set up your ticket sheet (3 min)

Create a working file `lab-03-backfeed-tickets.md`. For each of the four action items in the write-up's Section 7 plus any destination you add, produce one ticket block in this template:

```
Ticket <N>: <short-title-in-imperative-mood>

| Field                | Content |
|---------------------|---------|
| Source incident      | 2026-10-21 RouteAssist cross-field-leak (link to
                        write-up v1)
| Destination artifact | <specific file path OR Chapter 6 destination category +
                        specific document> — one of:
                        - mod-103 Ch. 2 review checklist      (e.g., /docs/*.md)
                        - mod-103 Ch. 3 standards-as-code     (e.g., AGENTS.md
                                                               section, Cursor
                                                               rule, lint policy)
                        - mod-103 Ch. 4 eval                  (e.g., evals/*.jsonl)
                        - mod-103 Ch. 5 contract change-log   (e.g., /docs/
                                                               ai-accountability-
                                                               contract.md)
                        - mod-106 Ch. 2 routing matrix        (e.g., /docs/
                                                               routing-matrix.md)
                        - mod-106 Ch. 4 HITL checkpoint set   (e.g., /docs/
                                                               hitl-checkpoints.md)
                        - mod-106 Ch. 6 tool-authorisation    (e.g., /config/
                                                               *-tool-auth.yaml)
| Owner                | <one named person — "team manager" is acceptable only
                        if the manager is named; "the team" or "eval-engineer
                        role" is NOT acceptable>
| Close-out criterion  | <what has to be true for the ticket to close —
                        specific, verifiable; for an eval row, must include
                        red-to-green demonstration in CI>
| Date                 | <two weeks from post-mortem by default; longer only
                        with a stated reason>
```

### Step 2 — Convert the four action items (25 min)

Walk the four Section 7 items in order. For each, (a) identify the Chapter 6 destination category, (b) specify the destination artifact as a file path or specific document, (c) name a human owner, (d) write a specific close-out criterion, (e) pick a date. For item 4 (the engineered-risk-peer engagement), think carefully about whether it is a ticket at all in Chapter 6's shape or whether it is a *coordination step* — and if it is a coordination step, whether the eval-row ticket Chapter 6 requires has an owner.

As you convert, keep a running note of Chapter 6's seven destinations (review checklist, standards-as-code, eval, routing matrix, HITL checkpoint, tool authorisation, contract change-log) and tick off which ones the v1 write-up covers. At the end of Step 2, before Step 3, you should have a clear view of which of the seven destinations are **missed by v1**.

### Step 3 — Add the missed destinations (10 min)

Chapter 6 is explicit: *"of the backfeed destinations in Chapter 2's Step 7, the commissioned eval row is the highest-leverage,"* and *"every confirmed incident produces at least one eval row unless there is a specific reason (the post-mortem names it) that no eval row is possible. 'No eval row possible' is rare."*

Also: *"the eval row lands with a demonstrated regression in CI. That is: the row first reproduces the incident's failure (red), the fix is validated (green), and the row goes into the regression gate."*

Produce a ticket for any Chapter 6 destination the v1 write-up has missed, following the same template. For the eval-row ticket specifically, your close-out criterion must include **the red-to-green demonstration plan**: what fixture reproduces the incident's failure, what the agent currently produces (red), what the fixed agent produces (green), and where the row lands in the regression gate. Chapter 5 is also explicit that the eval row's method owner is typically `ai-risk-engineer` when the method requires a fixture framework or an LLM-as-judge rubric — name them specifically in the owner field.

Also consider the HITL checkpoint and the contract change-log, both of which are named in the write-up's Section 3 Layer 3 finding but are not called out as a Section 7 action item. If the write-up's Section 3 names a Layer 3 finding, it should produce a Section 7 ticket at the Chapter 6 shape.

### Step 4 — Compare against the answer key (10 min)

Read the key below only after Steps 2 and 3 are complete.

#### Answer key — the four conversions from the v1 Section 7

**Ticket 1 — Tighten `cust_config` tool authorisation from schema-wide to field-level.**

| Field | Content |
|---|---|
| Source incident | 2026-10-21 RouteAssist cross-field-leak (link to post-mortem v1) |
| Destination artifact | `/config/cust-config-tool-auth.yaml` — update the authorisation stanza to field-level allow-list (`routing_policy`, `routing_policy_updated_at`); remove schema-wide read. mod-106 Chapter 6 destination. |
| Owner | **Named senior IC on the Lumen Routing team** (not "team manager will look at this"; manager-as-owner is acceptable if specifically the manager is named and the manager actually owns the config change, but for a tool-auth change the senior IC who owns the harness configuration is the typical owner). The ticket as-written in v1 fails Chapter 6's *"owner is a team, not a person"* and *"owner lacks authority"* stall-shapes. |
| Close-out criterion | PR merged to `/config/cust-config-tool-auth.yaml` moving `cust_config` read from schema-level to field-level allow-list (two named fields); CI validation confirms the field-level filter rejects adjacent fields in tool-return JSON; the next RouteAssist session that hits a `cust_config` adjacent-field access logs a denial. |
| Date | 2026-11-12 (two weeks from post-mortem publication). |

The v1 phrasing *"the team manager will look at this"* violates all three of Chapter 6's "ticket stall" patterns at once: ownership is vague ("look at" is not a verb that closes), the owner-as-person is not named (if the manager is the owner they must be named), and the close-out criterion is absent.

**Ticket 2 — Add AGENTS.md section restricting `internal_sla_notes` from customer-facing drafts.**

| Field | Content |
|---|---|
| Source incident | 2026-10-21 RouteAssist cross-field-leak (link) |
| Destination artifact | `/AGENTS.md` — new section *"Customer-facing reply drafting"* under the RouteAssist agent definition, naming the internal-only fields set (`internal_sla_notes`, `internal_escalation_tier`, `internal_billing_flags`) and the rule: *"when drafting customer-facing replies, the agent must NOT include content from the internal-only fields set, even when retrieved as part of a tool-return JSON; if the fields are retrieved, surface a note to the user and exclude them from the draft."* mod-103 Chapter 3 standards-as-code destination. |
| Owner | **Senior IC who maintains the team's AGENTS.md** (named; the v1 phrasing *"someone on the team needs to write this"* is exactly what Chapter 6 flags as a stall-shape). |
| Close-out criterion | PR merged to `/AGENTS.md` with the new section; a manual test shows RouteAssist on a fixture prompt that returns a tool-return JSON including `internal_sla_notes` produces a draft that excludes the field; the new section is referenced in the v2.2 review checklist (Ticket 3). |
| Date | 2026-11-12. |

**Ticket 3 — Review-checklist row: reviewer verifies no internal-only fields in RouteAssist-drafted replies.**

| Field | Content |
|---|---|
| Source incident | 2026-10-21 RouteAssist cross-field-leak (link) |
| Destination artifact | `/docs/routeassist-review-checklist.md` v2.2 — new row (likely row 7 or 8 depending on current count): *"reviewer confirms the drafted reply does NOT contain content from the internal-only fields set as defined in `/AGENTS.md § Customer-facing reply drafting`. Check the tool-call returns attached to the draft (visible in the session trace) for adjacent fields that were retrieved but should be excluded."* mod-103 Chapter 2 destination. |
| Owner | **Team manager** (named by name — the manager owns the checklist per mod-103 Chapter 2). |
| Close-out criterion | PR merged to `/docs/routeassist-review-checklist.md` bumping the version to v2.2 with the new row; the checklist change is announced in `#eng-routeassist` so reviewers see it; the next reviewer-run on a RouteAssist PR exercises the row and the review comment references the checklist row number. |
| Date | 2026-11-05 (one week — checklist updates are smaller than config / eval changes and land faster). |

The v1 phrasing *"we will add this"* is precisely the vague *"the checklist is updated"* form Chapter 6 flags; the Chapter 6-shaped version names the row content, the file path, and the version bump.

**Ticket 4 — Engineered-risk peer engagement is *coordination*, not a Chapter 6 ticket in this shape.**

The v1 Section 7 Item 4 (*"the engineered-risk peer will be informed and the engineer will chat with them about what guardrails look like"*) is **not** a backfeed ticket; it is a Chapter 5 **handoff**. The handoff should have fired at Step 5 of Chapter 2's flow (within one working hour of triage for a Sev-2), not been deferred to the post-mortem's action items. Chapter 5's five-field clean handoff shape is (identifier, severity + class, preserved-trace link, specific bounded ask, timeline expectation).

What a Chapter 6 ticket here looks like is the **artifact the handoff produces**, specifically the eval row. See Ticket 5.

#### Answer key — the destinations the v1 write-up missed

Walking Chapter 6's seven destinations against the v1 Section 7:

| Destination | v1 Section 7 coverage | Status |
|---|---|---|
| mod-103 Ch. 2 review checklist | Item 3 (as-rewritten in Ticket 3) | Covered. |
| mod-103 Ch. 3 standards-as-code | Item 2 (as-rewritten in Ticket 2) | Covered. |
| **mod-103 Ch. 4 eval** | — | **MISSED.** |
| mod-103 Ch. 5 contract change-log | — | Missed, but typically a change-log entry not a separate ticket. |
| mod-106 Ch. 2 routing matrix | — | Not warranted — the routing (RouteAssist drafts replies with human review) is not at fault. |
| **mod-106 Ch. 4 HITL checkpoint** | — | **MISSED** — Section 3 Layer 3 names the finding but Section 7 does not produce the ticket. |
| mod-106 Ch. 6 tool authorisation | Item 1 (as-rewritten in Ticket 1) | Covered. |

Two destinations are missed in v1. The eval row is the load-bearing miss (Chapter 6's *"every confirmed incident produces at least one eval row"* / the incident-to-eval metric targets 100% — missing it means the next incident of this shape will not be caught automatically). The HITL checkpoint is the second miss (the Section 3 Layer 3 finding specifically names *"no HITL checkpoint exists between the agent's tool-call return and the reply draft for the content-safety classification"* — a finding at Layer 3 that has no action item is a Chapter 3 completeness gap).

**Ticket 5 — Commission an eval row for the RouteAssist internal-field-leak regression class.**

| Field | Content |
|---|---|
| Source incident | 2026-10-21 RouteAssist cross-field-leak (link) |
| Destination artifact | `evals/routeassist/internal-field-leak.jsonl` — a golden-task row that supplies a fixture tool-return JSON including `internal_sla_notes`, prompts the agent to draft a customer reply, and asserts the draft does **not** include the field verbatim. Add a mutation variant that renames the sensitive field to confirm the check is robust to field-rename. mod-103 Chapter 4 destination via Chapter 5's `ai-risk-engineer` commissioning route. |
| Owner | **Named `ai-risk-engineer`** (not "the engineered-risk peer" generically — one specific person at the organisation, matching Chapter 6's owner-is-a-person requirement). The engineer is the method owner for the fixture framework the team uses; Chapter 5 is explicit that *"golden tasks and mutation tests are often team-authorable; LLM-as-judge rubrics and adversarial tests typically route through the risk engineer"* — field-leak detection on tool-return JSON fixtures is at the border, and in Lumen Routing's shape the engineer owns the fixture framework. |
| Close-out criterion | **Red → green → gate.** (a) Red: the row runs against the current (pre-fix) RouteAssist and reproduces the incident — the draft contains `internal_sla_notes` content verbatim, the assertion fails. (b) Green: the row runs against the fixed RouteAssist (post-Ticket-1 and post-Ticket-2) and the assertion passes — the draft excludes the field. (c) Gate: the row is added to the nightly regression gate for RouteAssist and the mutation variant also passes; failure on either variant in CI alerts `#eng-routeassist`. |
| Date | 2026-11-26 (four weeks — eval rows take longer than config / checklist changes and the engineer has their own queue; longer-than-two-weeks has a stated reason per Chapter 6, which is that the engineer is the method owner and their queue accommodates the row within four weeks). |

This is the ticket the v1 write-up most needed and did not produce. Without it, the incident-to-eval metric on this quarter is 0/1 (or at least 0/this incident); Chapter 6's target is 100%.

**Ticket 6 — Add HITL checkpoint between agent tool-call return and reply draft.**

| Field | Content |
|---|---|
| Source incident | 2026-10-21 RouteAssist cross-field-leak (link) |
| Destination artifact | `/docs/hitl-checkpoints.md` — new checkpoint under *"RouteAssist reply drafting"*: *"after a `cust_config` tool-call return and before the agent drafts the customer-facing reply, the agent must present the retrieved JSON to the drafting engineer and surface a warning if any field in the internal-only fields set (per `/AGENTS.md § Customer-facing reply drafting`) is present. The drafting engineer confirms the retrieved fields are customer-safe before the draft is produced."* mod-106 Chapter 4 destination. |
| Owner | **Named senior IC on the Lumen Routing team** (same owner as Ticket 1 if the senior IC owns both the harness config and the HITL checkpoint doc; name them specifically). |
| Close-out criterion | PR merged to `/docs/hitl-checkpoints.md` with the new checkpoint; the harness is updated to enforce the checkpoint (a config change that gates the draft step on the engineer's confirmation); a fixture test shows the checkpoint triggers on a fixture tool-return that includes `internal_sla_notes`. |
| Date | 2026-11-19 (three weeks — the checkpoint doc change is fast, but the harness-side enforcement is the slower step). |

**Ticket 7 (optional — contract change-log entry) — Note the C2 verification-bar tightening in the accountability contract.**

| Field | Content |
|---|---|
| Source incident | 2026-10-21 RouteAssist cross-field-leak (link) |
| Destination artifact | `/docs/ai-accountability-contract.md` change-log section — new one-line entry: *"2026-11-12: verification bar tightened for RouteAssist-drafted customer-facing replies — new HITL checkpoint before draft on internal-only fields, new review-checklist row, AGENTS.md section on internal-only fields, eval row commissioned (ref. 2026-10-21 cross-field-leak post-mortem)."* mod-103 Chapter 5 destination. |
| Owner | **Team manager** (named; the contract's authored owner). |
| Close-out criterion | PR merged with the change-log entry; the contract's visible pinned version in the team's handbook shows the updated change-log. |
| Date | 2026-11-12 (same week as the first batch of Tickets 1/2 land). |

This ticket is not required by Chapter 6 as a hard-fire — most incidents produce a change-log entry rather than a contract amendment, and the entry can be rolled up with other quarter's tightenings. But Chapter 6 lists it as one of the seven destinations and the Chapter 3 five-questions answer to Q5 requires a change-log entry when C2 tightens. In this incident's shape, the entry is the simple audit-trail move.

### Step 5 — Diagnose your drift (10 min)

Compare your tickets against the key. For each miss, write one short paragraph:

- **If your owners are "the team" / "eval-engineer role" / an unnamed generic:** this is Chapter 6's *"The owner is a team, not a person"* stall-shape, the single most common ticket-stall mode. Teams do not own tickets; people do. Re-read Chapter 6's *"What makes a ticket stall."*
- **If your close-out criteria are "the checklist is updated" / "AGENTS.md has the new section" without a PR + version + verification step:** vague close-out is the second ticket-stall mode. The close-out step has to be *verifiable by a non-author* at the weekly ritual; if the person running the ritual can only check "did the PR merge" and not "does the artifact actually do the thing," the ticket closes early and the next incident catches the regression.
- **If you did NOT add an eval-row ticket:** Chapter 6's incident-to-eval discipline is explicit — every confirmed incident produces at least one eval row with a demonstrated red-to-green, unless the post-mortem names a specific reason. This write-up names no such reason. The eval row is the highest-leverage output and the one Chapter 6 target of 100% hangs on.
- **If your eval-row close-out criterion is just "eval row is in CI":** missing the red-to-green demonstration requirement. Chapter 6 is explicit: *"a row that passes on initial run has not demonstrated what it is for."* The red step reproduces the incident; the green step validates the fix; the gate step prevents the regression. Without the red step your "eval row" is a passing test that cannot catch the thing it exists for.
- **If you treated Section 7 Item 4 (engineered-risk engagement) as a ticket:** Chapter 5's handoff shape is not a Chapter 6 ticket shape. The handoff is a coordination step that produces an artifact — the artifact (typically the eval row, sometimes a guardrail-design doc) is the ticket. Collapsing the two produces a ticket with no destination artifact and no close-out criterion.
- **If you did NOT add a HITL-checkpoint ticket:** the v1 Section 3 Layer 3 finding names the missing HITL checkpoint explicitly; a Layer finding in Section 3 that produces no Section 7 ticket is a Chapter 3 completeness gap (the five-systemic-questions answer to Q4 is empty). Routing / HITL / tool-authorisation should always be answered; "no change" is an acceptable answer when it is true, but when Section 3 Layer 3 explicitly names a gap, "no change" is not acceptable.
- **If you authored seven tickets when the key has five + two optional:** no drift; this is defensible. Chapter 6 does not cap the number of tickets per incident. A write-up that produces more specific, smaller tickets with named owners and specific close-out criteria is better than one that produces fewer, larger, fuzzier tickets. The ritual can close three small tickets as fast as one big one.

## Expected output

A file `lab-03-backfeed-tickets.md`, roughly 1.5–2 pages, containing:

- Four ticket blocks for the v1 Section 7 items (Items 1–3 as tickets; Item 4 explicitly noted as *coordination, not a ticket*).
- One eval-row ticket (Ticket 5) for the missed Chapter 6 eval destination, with the red → green → gate close-out.
- One HITL-checkpoint ticket (Ticket 6) for the Section 3 Layer 3 finding that v1 Section 7 missed.
- Optional: one contract-change-log ticket (Ticket 7).
- A short diagnostic paragraph per drift against the key.

Something like:

```
Ticket 1 — Tighten cust_config tool authorisation from schema-wide to field-level
  Source incident      : 2026-10-21 RouteAssist cross-field-leak <link>
  Destination artifact : /config/cust-config-tool-auth.yaml — field-level
                         allow-list (routing_policy, routing_policy_updated_at)
                         (mod-106 Ch. 6)
  Owner                : <named senior IC>
  Close-out criterion  : PR merged + CI validation confirms field-level filter
                         rejects adjacent fields + next RouteAssist session
                         logs denial on adjacent-field access
  Date                 : 2026-11-12
  ✅ match.

Ticket 5 — Commission eval row: RouteAssist internal-field-leak regression
  Source incident      : 2026-10-21 RouteAssist cross-field-leak <link>
  Destination artifact : evals/routeassist/internal-field-leak.jsonl — golden
                         task with fixture tool-return JSON containing
                         internal_sla_notes; assert draft does NOT include
                         field verbatim; plus mutation variant renaming the
                         sensitive field  (mod-103 Ch. 4 via ai-risk-engineer)
  Owner                : <named ai-risk-engineer>
  Close-out criterion  : RED (pre-fix reproduces incident; assertion fails)
                         → GREEN (post-fix draft excludes field; assertion
                         passes) → GATE (nightly regression + CI alerts
                         #eng-routeassist on failure; mutation variant also
                         passes)
  Date                 : 2026-11-26 (4 weeks; stated reason: eng. queue)
  ✅ match — this is the ticket v1 missed; without it, incident-to-eval metric
      is 0 on this incident and Ch. 6's target of 100% is blown this quarter.

Drift notes:
  First pass I had Ticket 1's owner as "team manager" — manager-as-owner is
  acceptable per Ch. 6 only if named AND if the manager actually owns the
  config. For a tool-auth YAML, the senior IC who owns the harness config
  is the right owner; I renamed to the senior IC.
  First pass I did NOT add the HITL ticket — Section 3 Layer 3 names it, but
  v1 Section 7 does not, so I inherited the gap. Re-read Ch. 3 five-questions
  Q4 — "routing/HITL/tool-authorisation" is a mandatory answer and this
  incident explicitly has a HITL gap. Added Ticket 6.
```

## Checkpoint

Before moving on to [Exercise 05](../exercises/exercise-05-regression-fixture-backfeed-ritual.md) (design and run the cadence against a real case), you should be able to answer **yes** to all five:

- Does every ticket you produced name a **specific human owner** (not "the team" or a generic role) and a **specific destination artifact** (a file path or a specific document + section)?
- Does the eval-row ticket's close-out criterion include **red → green → gate** — reproduce the failure, validate the fix, land the row in the regression gate — rather than just "eval row exists in CI"?
- Did you identify that **Section 7 Item 4 is coordination (a Chapter 5 handoff), not a Chapter 6 ticket**, and that the ticket version of the Chapter 5 handoff is the eval row (Ticket 5) that the handoff produces?
- Did you identify and add the **HITL-checkpoint ticket** (Ticket 6) that v1 Section 7 missed, matching the Section 3 Layer 3 finding?
- On every close-out criterion, is the close-out step **verifiable by a non-author at the weekly ritual** — i.e., the person running the ritual can check "does the artifact actually do the thing" and not just "did the PR land"?

If any answer is no, re-read Chapter 6's *"The backfeed ticket as an artifact"* and *"What makes a ticket stall"* before running Exercise 05 on a real-stakeholder case.
