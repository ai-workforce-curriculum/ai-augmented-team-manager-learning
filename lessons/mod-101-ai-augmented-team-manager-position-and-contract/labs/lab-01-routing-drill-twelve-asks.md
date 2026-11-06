# Lab 01 — Routing Drill: Twelve Asks Through the Rubric

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 1 (the ladder), Chapter 4 (the deferral rubric).
**Complements, does not duplicate:** Exercise 04 asks you to route ten real asks from *your own* inbox. This lab gives you a fixed curated set of twelve asks — including the Chapter 4 Monday-morning five plus seven harder cases — so you can calibrate your rubric against a known answer key before trusting it on live inputs.

## Objective

Run twelve asks through the three-question rubric from Chapter 4, write a one-line routing decision and reason for each, then compare against the answer key. The target is **under 30 seconds per ask by the end** of the drill and zero disagreement on the five Monday-morning asks that come straight from the chapter.

## Prerequisites

- Chapter 1 read (ladder and neighbour table).
- Chapter 4 read (three routing questions; routing destinations down / sideways / up / out; the ambiguous 10%).
- A timer or clock you can check per question.
- A blank text file or notebook for your routing decisions.

## Steps

### Step 1 — Set up your scratch file (2 min)

Create a working file `lab-01-routing.md` somewhere convenient. Add this header:

```
# Lab 01 — Routing drill

Rubric reminder (Chapter 4):
Q1. Is this at team scope, or beyond it? → up
Q2. Is this operational legwork I should be consuming? → down
Q3. Is this a peer discipline's craft, where I commission but do not re-build? → sideways
If "no" to all three → mine
Always-out: legal (opinion), HR (formal employment action), SecOps (SOC-side incident).

Routing destinations:
- down: ai-governance-analyst (L15); ai-assisted-software-engineer (L25); ai-augmented-analyst (L20)
- sideways: ai-risk-engineer (L25); ai-augmented-product-manager (L30); ai-infra-team-lead (L35)
- up: ai-enablement-lead (L45); ai-engineering-manager (L50); senior-ai-governance-architect (L50);
      head-of-ai-governance (L60); chief-ai-officer (L70)
- out: legal | HR | SecOps/DFIR
- mine: L40, mod-NNN
```

### Step 2 — Route the twelve asks (30–40 min)

Below are twelve asks. For each: **start the timer**, write (a) your one-sentence read, (b) the routing decision, (c) the reason in one short sentence pointing to which routing question (Q1 / Q2 / Q3) resolved it, and (d) time elapsed. Then stop the timer before moving on.

Do **not** scroll to the answer key until you have routed all twelve.

Asks 1–5 are the Chapter 4 Monday-morning set, slightly reworded; 6–12 are harder.

1. A new engineering VP sends a Slack asking how your team measures AI ROI and whether the number is defensible.
2. The platform team wants to canonicalise your team's Cursor rules file as the org-wide default and asks if you can hand them the latest version.
3. A product counterpart asks whether the team can adopt Claude Code for a new workflow that will touch customer data.
4. Your AI-feature PM wants to schedule a joint ROI review of the AI feature you jointly ship.
5. HR forwards a complaint from one of your ICs that another IC on the team is using AI to over-ship and squeeze them out.
6. A direct report asks the exact Cursor rules syntax to constrain the agent from editing migrations.
7. Legal forwards a question: does the current EU AI Act obligation on the new assistant pilot change what you can enable this quarter?
8. Your director asks for a one-pager describing how your team would respond if a model produced an incident on a customer-facing surface tomorrow.
9. A risk partner asks you to sign off on a red-team report for the agent one of your ICs built; they want you to interpret the dangerous-capability findings and decide what ships.
10. A peer L40 manager in a sister division asks whether both of your teams can run the same enablement curriculum next quarter.
11. Your CFO asks for a slide on how AI-augmented productivity is changing OKR-setting across the engineering org.
12. A direct report asks if they can paste a chunk of production customer data into the personal (non-SSO) tier of a popular chat tool to summarise it for a design doc.

### Step 3 — Score against the answer key (10 min)

For each ask, compare your routing to the key below. Count hits (same destination) and near-misses (correct spirit, wrong neighbour).

#### Answer key

1. **Mine.** Team-scope AI ROI is L40 work (`mod-104`). Q1/Q2/Q3 all return "no."
2. **Up** to `ai-enablement-lead` (L45). Multi-team / org-wide standardisation is beyond team scope (Q1 → yes). Hand off the rules file with a note on what's generalisable. (This is the Chapter 4 Monday example #2.)
3. **Down first** to `ai-governance-analyst` (L15) for intake; **then yours** for the team-scope decision; **sideways** to `ai-risk-engineer` (L25) to red-team if intake flags. (Chapter 4 Monday example #3.)
4. **Sideways** to the PM. Product ROI is the PM's; team ROI is yours. Attend the review; do not run it. (Chapter 4 Monday example #4.)
5. **Out** to HR (formal process) **and mine** (manager-side framing — review standard, workload, pairing). Partner; do not front-run. (Chapter 4 Monday example #5.)
6. **Down** to `ai-assisted-software-engineer` (L25). IC-mechanics of tool use — mentor by example, do not write the IC's rules file for them. (Chapter 4, Route **down**.)
7. **Out** to legal for the opinion (Chapter 4, Route **out**: "do not deliver legal opinion"), **then yours** for what you do with the opinion at team scope. Any part that is cross-team goes **up** to `ai-enablement-lead`.
8. **Mine.** Team-scope AI incident response is L40 work (`mod-109`). A one-pager on your team's response is exactly the manager-altitude artifact Chapter 5 says you should personally produce.
9. **Sideways-commissioned, mine-to-decide.** The risk engineer built the eval; you consume the evidence and make the team-scope decision on what ships. You do not re-run the harness. (Chapter 1 and 4 — commission; do not re-build.)
10. **Up** to `ai-enablement-lead` (L45). Multi-team enablement is explicitly in the L45 column. (Chapter 1 neighbour table; Chapter 4 Route **up**.)
11. **Up** to `ai-enablement-lead` (L45) for the org-wide framing; **mine** for the team-scope OKR example you'd contribute as input. Chapter 4's ambiguous-10% heuristic: "how do we structure OKRs under AI leverage? — team-scope is yours; multi-team is `ai-enablement-lead`."
12. **Mine, and urgent.** This is a C5 data-handling violation in your team's human/machine contract (Chapter 3) and a `mod-109`-shaped near-miss. Not a routing question to a neighbour — it is an immediate manager action: stop the IC, preserve the trace, pull back the data, and feed the finding into C1/C4. (Chapter 3 C5; Chapter 4's "always-out" list does not apply because this is a team-internal policy breach, not a legal opinion or an HR formal action.)

### Step 4 — Diagnose misses (10 min)

For every miss (wrong destination) and every slow route (>60 seconds), write one paragraph:

- Which routing question did you skip or misapply?
- Was the ambiguity real (genuinely sits on a boundary) or avoidable (you just didn't scan Q1/Q2/Q3 in order)?
- What one-line rule would have routed it in under 30 seconds next time?

### Step 5 — Re-run the four ambiguous ones from memory (5 min)

Close the file, wait a minute, then re-route asks 3, 7, 9, and 12 from memory in under 30 seconds each. If any take longer, your rubric is not yet internalised; repeat this step tomorrow.

## Expected output

A scratch file with twelve routed asks, timings, a diagnostic paragraph for each miss or slow decision, and a re-run of the four ambiguous ones. Something like:

```
Ask 1: VP wants to know how we measure AI ROI.
  Route: mine (mod-104).
  Reason: Q1 team-scope yes; Q2 not legwork; Q3 not peer craft.
  Time: 12s.
  ✅ match.

Ask 3: Claude Code on a customer-data workflow.
  Route: down (analyst intake) → mine (team decision) → sideways (risk eval if flagged).
  Reason: Q2 yes first (intake), Q1 team-scope after, Q3 if risk flagged.
  Time: 47s.
  ✅ match.

...
```

## Checkpoint

Before moving on to Exercise 04 (which routes **your** inbox), you should be able to answer **yes** to all three:

- Did you match the answer key on all five Monday-morning asks (1–5)?
- Did you match on at least five of the seven harder asks (6–12)?
- Is your average time-to-decide under 30 seconds on the second pass?

If not, re-read Chapter 4's three-question block and the ambiguous-10% section before running Exercise 04.
