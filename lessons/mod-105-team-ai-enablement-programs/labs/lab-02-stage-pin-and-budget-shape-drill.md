# Lab 02 — Stage-Pin and Budget-Shape Drill on a Fictional Roster

**Duration:** 45–60 minutes.
**Chapters exercised:** Chapter 4 (the four-stage ladder; everyone-gets-the-seat; usage-based pricing shape; the seniority-banded anti-pattern; the budget-assessment conversation), with side-checks against Chapter 1 (Failure B, the licence drop; the learning-stage-not-seniority load-bearing move), Chapter 2 (cohort composition: mixed stage, not mixed seniority), and Chapter 7 (the Platform-partner failure pattern "hard cap on tokens").
**Complements, does not duplicate:** Exercise 02 asks you to author the tool-budget distribution rubric for **your own** team. This lab hands you a fixed, deliberately mis-allocated budget policy for a fictional team — twelve engineers with brief described behaviours, a proposed seniority-banded seat plan, and a proposed flat token cap — so you can calibrate the stage-pinning and budget-shape moves before you spend real hours rubric-writing. The exercise is an authoring task on your team; the lab is a diagnostic drill against a known answer key.

## Objective

Read a curated sample: (a) a twelve-engineer fictional team's one-paragraph descriptions of each engineer's current observed behaviour on Claude Code (the usage-based tool in question), (b) the proposed seniority-banded seat allocation, and (c) the proposed flat 300k-token-per-month cap Finance is pushing. Pin each engineer to a stage (1–4) per the Chapter 4 rubric, identify every Chapter-4 anti-pattern in the two proposed policies, and write the correct budget shape for the team. Target: **you pin at least 10 of the 12 engineers to within one stage of the answer key**, and your rewritten budget shape passes the Chapter 4 acceptance bar (everyone gets the seat; usage shaped by stage; an explicit non-ask back to Finance on the hard cap).

## Prerequisites

- Chapter 4 read end-to-end (the four stages; everyone gets the seat; usage-based pricing shape; seniority-banded anti-pattern; the budget-assessment conversation).
- Chapter 1 skimmed (Failure B; the learning-stage-not-seniority distinction).
- Chapter 2 skimmed (cohort composition — mixed stage, not mixed seniority).
- Chapter 7 skimmed (the Platform-partner failure pattern "hard cap on tokens").
- A blank file for your stage pins, policy audit, and rewrite.
- A timer.

## The fictional context

> **"Ingest Platform" team, NorthBay Logistics.** 12 engineers (2 staff, 4 senior, 6 mid/junior). Owns the shared data-ingest service plus three ingest-adapter repos. Agents in use: Cursor Business (12 seats, provisioned 2 weeks ago), Copilot Business (12 seats, provisioned 18 months ago), **Claude Code via team gateway (usage-based, provisioned 2 weeks ago)** — the focus of this lab is Claude Code, the newly-rolled-out usage-based tool. The team's L&D partner (M. Osei) has delivered a 60-minute vendor onboarding for everyone; the manager (you, in the lab) is about to run the Day-0 budget conversations. Finance has proposed the token policy below ahead of those conversations.

## The twelve engineers (observed behaviour on Claude Code to date)

Read all twelve descriptions end-to-end before pinning anyone. Do not scroll to the answer key.

| # | Role / tenure | Observed behaviour on Claude Code (last 14 days) |
|---|---|---|
| E1 | Staff engineer, 7 years at company | Attended the vendor onboarding. Has not opened Claude Code since. Described it to a peer as "I'll get to it when I have a quiet week." |
| E2 | Staff engineer, 4 years at company | Built their own agent-authoring prototype on a 2024 hackathon. Uses Claude Code daily on their current work; has written a half-page internal note on "when I don't use it" that circulated in the team Slack. |
| E3 | Senior engineer, 5 years at company | Used Claude Code on a Saturday side project last year. Opened it twice this sprint; produced one small PR with it in a non-production internal tool. |
| E4 | Senior engineer, 3 years at company | Daily user. Shipped three production PRs with Claude Code in the last two weeks. Declined to use it on a stored-procedure refactor last Thursday with a one-line Slack reply explaining why. |
| E5 | Senior engineer, 2 years at company | Attended the onboarding. Has had Claude Code open on their second monitor every day but has committed nothing with it yet; they are "watching it on another engineer's screen first." |
| E6 | Senior engineer, 8 months at company | Used Claude Code heavily at a previous employer. Shipping production with it daily here; has already written one pattern-library entry that the team is referencing; mentored two mid-level engineers on it this sprint. |
| E7 | Mid-level engineer, 2 years at company | Shipped two production PRs with Claude Code in the last two weeks. One PR was reverted (an edge case the agent missed); the engineer has written a short post-mortem in their notes. |
| E8 | Mid-level engineer, 1 year at company | Used Claude Code once, generated a draft, decided it wasn't helping, and has not opened it since. Explicitly told the manager in a 1:1: "for the code I'm writing right now, it's adding more review time than it's saving." |
| E9 | Mid-level engineer, 1.5 years at company | Experimented with Claude Code on a personal side project last summer. Attended the onboarding. Opened it twice this sprint; one small PR in a non-production internal tool. |
| E10 | Junior engineer, 7 months at company | Attended the onboarding. Claude Code has not been opened on their machine since. The engineer has mentioned being "scared of breaking something." |
| E11 | Junior engineer, 11 months at company | Shipped three small production PRs with Claude Code in the last two weeks. Pairs with E6 regularly; actively asks "when should I *not* use this?" questions in retros. |
| E12 | Junior / new grad, 3 months at company | Used Claude Code daily in a university capstone. Attended the onboarding. Opened it twice at work; produced nothing merged yet; "hesitant to use it until I understand the code review culture here." |

## Finance's proposed budget policy (under review)

### Policy A — seat allocation

> **Staff and senior engineers get the Claude Code "Enterprise" workspace with agent-mode and tool-use enabled. Mid-level engineers get the "Pro" workspace (no agent-mode). Junior engineers get the "Starter" workspace (limited to Claude Code's chat interface, no project context, no agent-mode).**

### Policy B — token cap

> **Flat cap: 300,000 tokens / engineer / month on Claude Code, applied uniformly across the team. Engineers who hit the cap mid-month lose access until month roll-over. Monthly review of all engineers against the cap.**

### Finance's rationale

> *"We don't want to pay for licences the team isn't using, and the token line is opex-sensitive. A flat cap is the easiest policy to defend to our FinOps team; we'll relax it once we see a track record of productive use."*

## Steps

### Step 1 — Set up your working file (3 min)

Create a working file `lab-02-stage-pins-and-budgets.md`. Add this header:

```
# Lab 02 — Stage pins + budget shape (Ingest Platform, Claude Code)

Chapter 4 stage ladder:
  1  Never used in a work context (opened twice and bounced counts)
  2  Side-project / exploratory at work; not shipped non-trivial
     production work yet
  3  Shipping production, with judgment; can articulate when NOT to
     use the tool
  4  Teaching others; contributed a pattern to the CoP library;
     another engineer has deferred to them on a tool-usage judgment

Policy audit buckets:
  A1  Seat tier banded by seniority
  A2  Access scoped by seniority (agent-mode / tool-use off for
      stages that need it most)
  A3  Flat usage cap across stages
  A4  Hard cap with mid-month loss-of-access
  A5  No stage-shaped alerting; monthly ceiling-only review

Pins:  E1=? E2=? ... E12=?
```

### Step 2 — Pin each engineer to a stage (12–15 min)

For each of the twelve engineers, pick a stage 1–4 against the Chapter 4 rubric. Keep each pin to one line with a one-clause rationale. **Target: no more than 60 seconds per engineer.**

Stage definitions (from Chapter 4), as a reminder:

- **1 — Never used in a work context** in the last 30 days (or has opened the tool for work twice and bounced).
- **2 — Side-project / exploratory at work.** Has used the tool but has not shipped production with it, or has shipped only trivial changes.
- **3 — Shipping non-trivial production work.** Makes judgment calls about when to use it and when not; has at least one case where they declined to use it on a piece of work and can articulate why.
- **4 — Teaching + pattern-contributing.** Shipping, teaching other engineers, contributed at least one pattern to the CoP's pattern library; at least one review where another engineer explicitly deferred to them on a tool-usage judgment.

Watch for the three specific traps the engineer descriptions are designed to surface:

- *A senior engineer at stage 1* (hint: E1). Seniority does not bump the pin. Chapter 1 is explicit: "a senior engineer who has never used an agent is a day-5 learner on that agent."
- *The "tried-and-stopped" engineer* (hint: E8). This is Chapter 6 of mod-104 referenced in mod-105 Chapter 5's framing — an engineer who honestly tried the tool and concluded it is not helping for *their current work* is a diagnostic signal, not a stage-1 pin. They may be a stage-2 pin on this tool with a tool-fit question or a stage-3 engineer on their primary tool but a stage-1/2 on this specific one. Note the distinction explicitly in your pin.
- *The university-capstone new grad* (hint: E12). Prior non-work usage counts toward the stage-2 pin ceiling but does not push past stage 2 until they ship production. The hesitancy around review culture is a programme-side signal (you own the Day-0 kickoff that resolves it), not a reason to pin lower.

### Step 3 — Compare your pins against the answer key (5 min)

#### Answer key — engineer stage pins on Claude Code

- **E1 — Stage 1.** Attended onboarding; has not opened the tool at work. Seniority does not bump; Chapter 1's "senior at stage 1 is a day-5 learner" applies directly.
- **E2 — Stage 4.** Built an agent-authoring prototype; daily shipping; wrote a "when I don't use it" note the team is referencing. The pattern-contribution + teaching dimension lands this at stage 4, not stage 3.
- **E3 — Stage 2.** One side-project experience last year + one non-production internal PR. Has not shipped production. Classic stage 2.
- **E4 — Stage 3.** Daily production shipping + a documented "declined to use it" judgment call. The Chapter 4 stage-3 definition names this specifically ("at least one case where you declined to use it on a piece of work and can articulate why").
- **E5 — Stage 1.** Open-on-second-monitor does not count. "Watching it on another engineer's screen first" is pre-stage-1 behaviour; the pin stays at 1 until they ship something. Note explicitly that this engineer is a high-potential stage-1, not a dead stage-1 — the cohort placement matters.
- **E6 — Stage 4.** Brought prior fluency in; shipping production daily; mentored two mid-level engineers; wrote a pattern-library entry already. All four stage-4 criteria in two weeks is unusual but the evidence is there.
- **E7 — Stage 3.** Shipping non-trivial production + a reverted PR *with a post-mortem*. The post-mortem is the judgment signal (stage-3 reads as "can articulate the trade-off", which the post-mortem documents). The revert does not demote; honest post-mortems are a stage-3 positive signal.
- **E8 — Stage 2 (with a tool-fit flag).** The engineer gave the tool a real try and concluded it is not helping for their *current* work. Chapter 5's "tried-and-stopped" cohort is the *diagnostic*, not a pin-at-1 default. The pin is stage 2 on Claude Code (opened + tried + a specific judgment), with a tool-fit question routed per mod-104 Chapter 6's treatment of the tried-and-stopped cohort. Do *not* read this as performance.
- **E9 — Stage 2.** Side-project last summer + a small non-production PR + the onboarding. Classic stage 2.
- **E10 — Stage 1.** Has not opened the tool. "Scared of breaking something" is a Day-0 budget-conversation signal (pair-with-mentor from Chapter 2 Days 11–20 is the direct fix), not a lower pin. Pin stays at 1.
- **E11 — Stage 3.** Shipping production + pairs with E6 + actively asks "when not to" questions. The "when not to" signal is the stage-3 definition's judgment dimension in formation; tenure does not block the pin. This is the specific Brynjolfsson-Li-Raymond case Chapter 1 cites — a junior shipping production with the tool outruns a senior at stage 1 on the same tool.
- **E12 — Stage 2.** University capstone counts toward stage 2 (used the tool, not in a work context). Two work logins + nothing merged keeps them at stage 2 until they ship production. The "hesitant about review culture" signal is a Day-0 programme-side signal (who they pair with; what the first-PR target looks like), not a stage-1 pin.

Count hits. **Ten or more within one stage of the answer key is the pass bar**; eight to nine means a re-read of Chapter 4's "The four-stage ladder" and "The budget-assessment conversation" sections; seven or fewer means re-read Chapter 4 end-to-end before starting Exercise 02.

### Step 4 — Audit the two proposed policies (10–15 min)

For each of the two Finance policies, write down which Chapter 4 anti-pattern(s) it matches and why. Keep each audit to 3–5 lines.

- **Policy A — seniority-banded seat tier.** Which Chapter 4 anti-pattern? Which engineers are harmed first (name at least two)? What does the "agent-mode off for juniors" clause break structurally (hint: Chapter 2 cohort composition with E11 the stage-3 junior vs. E1 the stage-1 staff)? What is the correct rewrite?
- **Policy B — flat 300k token cap + mid-month loss-of-access.** Which Chapter 1 failure does this reproduce? What happens to the stage-1 and stage-2 engineers (hint: Chapter 4's "soft usage floor, not a cap" at those stages)? What happens to E6 and E11? What is Chapter 7's correct partnership-contract counter-move?

#### Answer key — policy failures

**Policy A — seniority-banded tier + scoped access.** This is the pure Chapter 4 seniority-band anti-pattern plus a second-order compounding mistake. The Chapter 4 anti-pattern: *"Staff engineers get the top-tier plan; everyone else gets the standard plan"* and *"Only L25+ engineers get [agent-mode] enabled"* are two of the three seniority-banded policies the chapter names explicitly. The harms in this specific roster:

- E1 (staff, stage 1) sits on the senior tier as dead-weight; no fluency-growth outcome, full senior-tier spend.
- E11 (junior, stage 3) is throttled by the Pro / Starter tier and specifically by agent-mode being off — the stage where they would otherwise be moving toward stage 4.
- E12 (new grad, stage 2) is blocked from agent-mode + project context — exactly the configuration they need to produce their first-successful-PR-with-tool on this team's code.
- Cohort composition (Chapter 2) breaks: a mixed-stage cohort of E1 (staff, stage 1) + E11 (junior, stage 3) + E6 (senior, stage 4) + E12 (new grad, stage 2) + E9 (mid, stage 2) has *four different seat tiers across five people*, which is "broken by construction" per Chapter 4's cohort-coherence argument.

Rewrite: **everyone gets the same seat tier** (the full workspace with agent-mode and tool-use enabled). The Chapter 4 reasoning is explicit — door-opening friction, cohort coherence, equity signal; the usage-based spend is the lever, not seat access.

**Policy B — flat 300k cap with mid-month loss-of-access.** Chapter 1 Failure B (the licence drop) in FinOps costume. Chapter 4 is explicit: *stages 1–2 get a soft usage floor, not a cap*. A flat 300k cap at stage 1 means the stage-1 engineers (E1, E5, E10) burn through their cap exploring, hit the wall, and bounce — reproducing exactly the Failure-B pattern the seat structure was supposed to prevent. A flat 300k cap at stage 3–4 means E6, E11, E4, E7, and E2 get throttled mid-task and shift back to non-AI workflows, wasting the fluency investment the team made bringing them to those stages. Mid-month loss-of-access is the specific Chapter 7 "Platform needs to enforce a hard cap on tokens" failure pattern. Rewrite per Chapter 4's table:

- Stage 1 (E1, E5, E10): soft floor expectation of ~50 tasks / month. No cap until stage 2.
- Stage 2 (E3, E8, E9, E12): soft floor of ~100 tasks / month. No cap. First-successful-PR-with-tool at Day 30 is the leading indicator.
- Stage 3 (E4, E7, E11): run at team median. Monthly review on the mod-104 tile, not on the engineer.
- Stage 4 (E2, E6): no cap; quarterly review of pattern contribution (per Chapter 4).

The counter to Finance per Chapter 7: *"the mod-104 cost tile is tracking this; the Chapter 4 learning-stage rubric is the allocation instrument; a hard cap would corrupt the measurement — can we set stage-sensitive alerts instead?"*

### Step 5 — Write the budget shape rewrite + the Chapter 7 reply (10–12 min)

Produce two short artifacts.

**Artifact 1 — the Chapter 4 budget shape for this team.** A four-row table (stages 1–4), one row per stage, with:

- Seat/access (same tier for all, per the Chapter 4 "everyone gets the seat" rule).
- Expected usage shape (soft floor at 1–2; team-median at 3; uncapped-with-quarterly-review at 4).
- Monitoring cadence (no monthly ceiling at 1–2; monthly team-median read at 3; quarterly stage-4 review).
- Engineer count at this stage (from your step 2 pins).

Keep the table to eight rows total (header + 4 stages + a Qtotal line + a projected next-quarter line).

**Artifact 2 — the reply to Finance.** Three to five lines, written as the manager's reply to the Finance partner. Shape:

- Name the Chapter 4 anchors (Brynjolfsson-Li-Raymond, Dell'Acqua) in one sentence.
- Name the failure mode of the current policy in one sentence (Failure B, Chapter 1).
- Propose the stage-sensitive-alerts alternative from Chapter 7.
- Name the mod-104 cost-ratio tile as the ongoing instrument.

Example shape (do not copy verbatim):

```
Thanks for the policy sketch. Chapter-4-anchored view: Brynjolfsson 2023
and Dell'Acqua 2023 both show AI leverage follows learning stage,
not tenure — a flat per-engineer cap starves the stage-1 engineers
(where exploratory token-burn *is* the practice) and throttles the
stage-3 engineers (where the team's fluency investment is landing).
Alternative: soft floor at stages 1-2, team-median at stage 3, named
ceiling + quarterly review at stage 4, with stage-sensitive alerts
through the mod-104 AI-cost-ratio tile. Spend will rise in Q1 as
stage-1 engineers ramp — this is the intended direction. Draft rubric
attached; happy to walk at the Q-review.
```

If your reply leads with "we need the cap removed" or "Finance is wrong", it has drifted; revise toward a specific alternative instrument.

## Expected output

A single scratch file, roughly a page and a half, containing:

- Twelve stage pins (E1–E12), each with a one-clause rationale, matched against the answer key.
- Policy A audit (3–5 lines): anti-pattern, harmed engineers named, rewrite.
- Policy B audit (3–5 lines): failure mode, soft-floor shape, Chapter 7 counter-move.
- An eight-row stage-shape budget table with the current-quarter projection.
- A 3–5 line reply to Finance in Chapter 7 shape.

Something like:

```
E11 (junior engineer, 11 months) — Stage 3
  Rationale: shipping 3 production PRs; pairs with E6; actively asks
  "when not to" — judgment dimension in formation. Chapter 1 Brynjolfsson
  junior-outruns-stage-1-senior case applies.
  ✅ match.

Policy A audit:
  Anti-pattern: Chapter 4 seniority-bands (seat tier + agent-mode
    scoped by seniority).
  Harmed: E1 dead-weight at senior tier; E11 throttled at stage 3
    without agent-mode; E12 blocked from the configuration they need
    for first-successful-PR.
  Cohort breakage: a mixed-stage cohort would have 4 different seat
    tiers across 5 people — "broken by construction."
  Rewrite: everyone gets the same seat tier.
```

## Checkpoint

Before moving on to Exercise 02 (where you author the tool-budget rubric for **your own** team), you should be able to answer **yes** to all five:

- Did you correctly pin E1 (staff engineer, never used the tool at work) and E10 (junior, "scared") both to stage 1, without letting seniority or sentiment move either pin?
- Did you pin E11 (junior, 11 months, shipping production + judgment-in-formation) to stage 3, and recognise this as the Chapter 1 Brynjolfsson case (junior at stage 3 outranks senior at stage 1 on this tool)?
- Did you pin E8 (tried-and-stopped mid-level) to stage 2 with an explicit tool-fit flag — *not* to stage 1 as if they had not tried, and *not* read it as a performance signal?
- Did your Policy A audit name "everyone gets the same seat tier" as the rewrite rule, and your Policy B audit name "soft floor at stages 1–2" as the explicit replacement for the hard cap, with the Chapter 7 stage-sensitive-alerts counter-move?
- Did your reply to Finance name at least one Chapter-4 research anchor, propose a *specific alternative* instrument, and reference the mod-104 AI-cost-ratio tile as the ongoing measurement — *not* argue in generalities or ask for the cap to be removed without a replacement?

If any answer is no, re-read Chapter 4's "The four-stage ladder and what it funds," "Why everyone gets a seat even at stage 1," and "The anti-pattern: tying budget to seniority bands" sections, plus Chapter 7's "Three failure patterns that show up in partner interfaces," before starting Exercise 02 on your real team's rubric.
