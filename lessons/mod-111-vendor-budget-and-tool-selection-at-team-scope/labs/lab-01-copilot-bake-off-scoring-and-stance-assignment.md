# Lab 01 — Copilot Bake-off Scoring and Stance Assignment on a Pre-Baked Results Packet

**Duration:** 60–75 minutes.
**Chapters exercised:** Chapter 2 (the three positioning tiers; the five evaluation axes; scoring and weighting; data handling as a gate; cost as a post-score threshold), and Chapter 3 (the four stances; the decision checks; sunset-cost as part of the commitment; anti-patterns). Side-check against Chapter 4 (the authoring-environment slot for Tier 3 overlap with agent-authoring environments) and Chapter 1 (scope — what the manager does and does not decide).
**Complements, does not duplicate:** [Exercise 01](../exercises/exercise-01-copilot-build-vs-buy-matrix.md) asks you to author the v0.1 copilot build-vs-buy matrix for **your own** team — real tools, real data, real IC pilots. This lab hands you a deliberately composite results packet from a fictional team so you can **calibrate your scoring reflexes** — treating Axis 4 as a gate, keeping cost out of the weighted score, recognising shipped-plus-rules as a Wrap not a Buy, naming an owner for every Extend — before you spend two hours on a matrix whose first-pass defence to the governance architect fails on the first question about data handling.

## Objective

For each of five candidate tools pre-scored on the five Chapter 2 axes against a fixed fictional team context, produce a decision packet with: (i) a **per-axis score** (1–5) after you re-read the packet's raw data against the Chapter 2 definitions; (ii) a **data-handling gate verdict** (pass / conditional / fail) against the team's inherited `mod-110` Chapter 6 data-class policy — this is the gate that overrides the weighted score; (iii) a **weighted total** using the team's pre-pinned weights; (iv) a **cost-threshold check** applied *after* the score, not folded into it; (v) a **stance** (Buy / Wrap / Extend / route-upward) per Chapter 3 with the Chapter 3 decision check that produced it; (vi) a **sunset-cost note**; and (vii) a **matrix-slot decision** (winner per tier; parked; disqualified; routed upward). Then compare against the answer key.

Target: **you match the gate verdict on at least four of five tools, you catch the two deliberately-planted anti-pattern traps (the cost-folded-into-score temptation on a cheap-but-data-handling-flagged candidate; the Extend-without-a-named-owner temptation on a feature-rich candidate), and you assign the correct stance on at least four of five candidates.** The two reading drifts this lab is designed to catch — *"Candidate A is cheap enough that its data-handling problem is manageable"* and *"Candidate B's extension surface is so rich we should build the team's own agent framework on top of it"* — are the ones Chapter 2 and Chapter 3 flag as the most common first-pass errors.

## Prerequisites

- Chapter 2 read end-to-end — especially the three positioning tiers, the five axes (latency, output quality, cost, data handling, extensibility), *"Scoring and weighting"* (data handling as a gate; cost as a post-score threshold; weights pinned before the bake-off), and *"The bake-off protocol"*.
- Chapter 3 read end-to-end — especially the four stances, the four decision checks (shipped sufficient? → thin-layer closes gap? → vendor-extension-points with named owner? → route upward), the cost-side anchors including *sunset cost*, and the anti-patterns (*re-implementing an extension point*, *abandoned forks*, *unowned extensions*).
- Chapter 4 skimmed — the authoring-environment slot (Claude Code, Cursor, Codex) for the one Tier 3 candidate in the packet.
- Chapter 1 skimmed — *"What this module is not"* (manager owns selection/evaluation; procurement owns signature; routing a build request upward is a legitimate output).
- A blank file for your decision packet.
- A timer.

## The fictional context

> **"PayPilot" team, Meridian Payments (UK-headquartered payments company, London).** 11 engineers (1 staff, 2 senior, 5 mid, 3 junior), 1 manager. Primary codebases: a Go payment-routing monolith (`routing-core`) and a TypeScript merchant-dashboard (`merchant-portal`). Work mix: feature work (ticketed, medium velocity), periodic PCI-scope hardening, incident firefighting, quarterly large refactors. The team routinely handles **cardholder data (PCI-DSS in-scope)** in `routing-core` — flagged **Restricted** in the team's inherited `mod-110` Chapter 6 data-class × tool-class matrix. `merchant-portal` handles **Confidential** data (merchant business terms, dashboard content) but no cardholder data. Starting position: Cursor Pro seats (individual, not Business), one engineer running Claude Code on the side, ChatGPT consumer in use, no enterprise contracts yet. The organisation has **existing enterprise agreements with GitHub (Copilot Business tier purchased for other teams) and Anthropic (Claude for Work Enterprise)** through procurement; the team can join either without a new MSA.
>
> **`mod-105` stage distribution.** 2 stage-1, 4 stage-2, 4 stage-3, 1 stage-4.
>
> **`mod-103` review checklist.** Standards-as-code in `routing-core/.review-checklist.md`; TypeScript equivalents in `merchant-portal/`.
>
> **Delegation-ladder profile (`mod-106` Chapter 2).** 80% human-with-AI-support work (IDE-centric); 15% review-required agent work (slash-command refactors, test generation); 5% scheduled fully-automated work (nightly eval runs, release-notes drafting).
>
> **Weights pinned before the bake-off** (the manager and the team's staff engineer agreed these in a 30-minute pre-meeting; they are *not* revised after the scores come in):
>
> - Axis 1 Latency: **0.20**.
> - Axis 2 Output quality (against `mod-103` checklist): **0.35**.
> - Axis 3 Cost: **post-score threshold, not weight**.
> - Axis 4 Data handling (against `mod-110` matrix): **gate, not weight — Restricted-data workflow fit is a disqualifier**.
> - Axis 5 Extensibility (rules, MCP, model routing, headless, observability): **0.25**.
> - Ergonomics: bundled into Latency and Extensibility; not a separate weight.
> - Weights sum: 0.80 (Axis 3 is a post-score threshold; Axis 4 is a gate).

Score each candidate *as if you are the team manager running the Chapter 2 bake-off*, with the team's weights, the team's data-class gate, and the Chapter 3 stance choice at the end of the scoring.

## The pre-baked bake-off results packet

Two weeks of trial, three-engineer stage-mixed cohort (one stage-2 junior, one stage-3 mid, one stage-4 staff), 15 tasks drawn from the real backlog (5 `routing-core` feature work including 2 that touch PCI-scope files, 3 `merchant-portal` bug fixes, 2 cross-repo refactors, 2 test-writing tasks, 2 doc tasks, 1 nightly-eval drafting task). Each candidate was invoked for every task where the data-class gate did not flat-out prohibit it; where it did, an equivalent `routing-core`-synthetic-fixture task substituted.

```
CANDIDATE                       TIER     RAW OBSERVATIONS

A — Cursor Business             Tier 2   Latency: p50 ~250ms completion, agent-turn p50 ~5s / p95 ~12s.
    (on org MSA path)                    Quality: 11/15 tasks passed mod-103 checklist first-try; the 4
                                         failures were style-rule misses the IC fixed in one iteration.
                                         Cost: $40/seat/month (Business tier via org MSA); usage overage
                                         rare in trial.
                                         Data handling: Cursor Business trust-centre page states
                                         "privacy mode" is default for Business; zero-retention on
                                         inputs if enabled; DPA on file through org procurement;
                                         model routing uses frontier models (OpenAI, Anthropic) via
                                         Cursor's inference layer. Residency: US primary (EU option
                                         on Enterprise tier only, not Business).
                                         Extensibility: .cursor/rules/ full support; MCP support;
                                         custom-model routing available; headless agent mode
                                         documented; usage telemetry exportable via console.

B — Devex-Agent                 Tier 2   Latency: p50 ~180ms completion, agent-turn p50 ~3s / p95 ~8s.
    (startup product, 18        (fork)   Quality: 13/15 tasks passed checklist first-try — highest
    months on market, VS                  of the cohort.
    Code fork)                           Cost: $12/seat/month; unlimited usage advertised.
                                         Data handling: trust-centre page says "we may use inputs to
                                         improve the service unless the customer opts out by emailing
                                         support@ with a written request"; no DPA template published;
                                         not SOC 2 (Type I reportedly in progress per sales call);
                                         hosting US-only; subprocessor list not published.
                                         Extensibility: .devex-rules/ file format supported; no MCP
                                         yet (on roadmap per sales); no custom-model routing (locked
                                         to vendor's routed model); no headless mode.

C — Copilot Enterprise          Tier 1   Latency: p50 ~210ms completion (Tier 1 use), agent-turn p50
    (on org MSA path)                    ~6s / p95 ~14s in the Copilot chat agent.
                                         Quality: 9/15 tasks passed first-try on completion-centric
                                         work; the Tier 1 use case is where Copilot was strongest;
                                         Tier 2 agent-work scores were lower than A and B.
                                         Cost: $39/seat/month Enterprise via org commit.
                                         Data handling: Copilot Trust Center documents zero-retention
                                         on business/enterprise tiers; training-on-your-data excluded;
                                         SOC 2 Type II on file via org procurement; DPA signed;
                                         EU data residency on Enterprise. US-hosted by default.
                                         Extensibility: .github/copilot-instructions.md supported;
                                         MCP support emerging; model routing within GitHub's lineup
                                         not swappable; headless "agent mode" available; usage
                                         telemetry via GitHub.

D — Claude Code                 Tier 3   Latency: terminal-native; agent-turn p50 ~7s / p95 ~20s for
    (terminal; one engineer     (also    multi-step work.
    already using)              Tier 2   Quality: 12/15 tasks passed checklist first-try on long-
                                via      horizon refactor and test-writing tasks; the Tier 3 use case
                                IDE      was the strongest fit for the 2 cross-repo refactors.
                                mode)    Cost: usage-based; $0 seat; projected ~$120/engineer/month
                                         at stage-3 median per Chapter 5 patterns; stage-4 ceiling
                                         ~$360.
                                         Data handling: Claude for Work (Enterprise) tier available
                                         on org MSA; zero-retention configurable to 0 days; training-
                                         on-your-data excluded for Enterprise; SOC 2 Type II; DPA
                                         signed; US-hosted with EU option contracted.
                                         Extensibility: AGENTS.md, skills, slash commands, sub-agents,
                                         hooks; MCP native; model-provider is Anthropic by default
                                         (not swappable without changing SDK); headless mode mature;
                                         CI invocation documented.

E — Internal "payhelper"        n/a      Not a vendor product. An IC on the team proposes building
    agent (proposed build)               an internal agent on top of a self-hosted Llama deployment
                                         with a custom routing layer, fine-tuned on routing-core,
                                         so "we are not sending PCI-adjacent code to a vendor at all."
                                         Estimated 4–6 engineer-months to v1; one named builder (the
                                         IC); no sibling platform team involvement scoped; no self-
                                         hosted inference infrastructure currently in place.
                                         Pitched at the end of week 1 of the bake-off as a strategic
                                         alternative to candidates A–D.
```

Grade each candidate *using the team's weights, the data-class gate, and the Chapter 3 decision checks*. Do not invent facts beyond the packet; score only what the packet names.

## Steps

### Step 1 — Set up your decision packet (3 min)

Create a working file `lab-01-decision-packet.md` with this template, repeated once per candidate:

```
Candidate: <letter + name>
Tier: <1 / 2 / 3 / n/a>

(i) Per-axis scores (1–5, Chapter 2 definitions):
    Axis 1 Latency       : <score> — <one-sentence rationale citing the raw observation>
    Axis 2 Output quality: <score> — <one-sentence rationale citing pass rate>
    Axis 5 Extensibility : <score> — <one-sentence rationale citing specific sub-questions>

(ii) Data-handling gate (Axis 4, against mod-110 matrix):
    For Restricted (PCI) in routing-core : pass / conditional / fail
    For Confidential in merchant-portal   : pass / conditional / fail
    Rationale: <one sentence tying the gate verdict to the packet's data-handling clause>

(iii) Weighted total (Axes 1, 2, 5; weights sum to 0.80):
    <calculation; the number>

(iv) Cost-threshold check (post-score):
    Headline cost: <from packet>
    Would the second option be good enough at ⅔ the cost? <y/n/n-a>

(v) Chapter 3 stance:
    Check 1 (shipped sufficient?)              : <y/n> — <one sentence>
    Check 2 (thin-layer closes gap?)           : <y/n/n-a>
    Check 3 (extension points + named owner?)  : <y/n/n-a>
    Check 4 (routes upward?)                   : <y/n/n-a>
    Stance: Buy / Wrap / Extend / route-upward / disqualified
    Named owner (for Wrap/Extend)              : <role or explicit "none named">

(vi) Sunset-cost note:
    <one sentence from Chapter 3 cost-side anchors>

(vii) Matrix-slot decision:
    Winner per tier / parked / disqualified / routed upward / sunset
```

Time yourself. Target per candidate: ~10 minutes. If you spend more than 12 minutes, note the drift and move on; you will diagnose in Step 4.

### Step 2 — Grade candidates A–C (25–30 min)

Grade A, B, C against the template. Do not look at the key yet. For the gate verdict, apply the Chapter 2 rule verbatim: *"If a candidate fails Axis 4 for your data classes, no amount of latency and quality score fixes it."* Do not fold cost into the weighted total — cost is a post-score threshold.

### Step 3 — Grade candidates D and E (15–20 min)

D is a Tier 3 candidate that also touches the Chapter 4 authoring-environment slot; your stance needs to address both. E is the proposed internal build; apply the Chapter 3 decision-check sequence and the R6 threshold, not an output-quality score (E has not been built and has no bake-off data).

### Step 4 — Compare against the answer key (10–15 min)

Read the key below only after you have graded all five.

#### Answer key — Candidate A (Cursor Business)

- **Axis 1 Latency:** **4.** p50 ~250ms completion is above the ~200ms perceptual floor but below the ~600ms friction threshold Chapter 2 names; agent-turn p50 ~5s is acceptable for the team's Tier 2 use. Not 5 because p95 ~12s is at the top of acceptable.
- **Axis 2 Output quality:** **4.** 11/15 (73%) first-try pass rate against the team's `mod-103` checklist; the four failures were style-rule misses fixable in one iteration — the exact class of gap a Wrap stance (rules file + prompt pack) can close.
- **Axis 5 Extensibility:** **5.** Full rules support, MCP, custom-model routing, headless, telemetry exportable — all five Chapter 2 sub-questions answered yes.
- **Data-handling gate:**
  - `routing-core` (Restricted / PCI): **conditional** — zero-retention is contractually available on Business tier but residency is US-only (EU option requires Enterprise tier, not Business). For a UK-headquartered team with PCI scope, residency is a real constraint; conditional means a `mod-110` Chapter 6 reader entry with the specific condition (US residency with cross-border transfer mechanism verified by legal) is required before Restricted data routes through A.
  - `merchant-portal` (Confidential): **pass** — zero-retention + signed DPA via org MSA covers Confidential-class workflows.
- **Weighted total:** 4 × 0.20 + 4 × 0.35 + 5 × 0.25 = **3.45** (out of 4.0 given weights sum to 0.80).
- **Cost-threshold check:** $40/seat/month; no cheaper serious Tier 2 candidate passed the gate — not applicable as a tiebreaker.
- **Chapter 3 stance:** Check 1 — shipped not quite sufficient (the four style-rule misses show the team's conventions don't flow through the vendor's defaults); Check 2 — `.cursor/rules/` pulled from the `mod-103` standards-as-code artifact plus a short prompt pack closes the gap at thin-layer cost. **Stance: Wrap.** Owner: manager + one named engineer. Sunset cost: archive the rules repo; reclaim seats on the two-week reclamation window.
- **Matrix-slot decision:** **Winner Tier 2.** Conditional for Restricted data (legal to confirm UK-to-US cross-border mechanism for the Business-tier residency).

#### Answer key — Candidate B (Devex-Agent)

- **Axis 1 Latency:** **5.** p50 ~180ms completion and agent-turn p50 ~3s are the best in the cohort.
- **Axis 2 Output quality:** **5.** 13/15 (87%) first-try pass — the highest pass rate in the cohort.
- **Axis 5 Extensibility:** **2.** `.devex-rules/` yes, but no MCP, no custom-model routing, no headless; four of the five sub-questions Chapter 2 names answered no.
- **Data-handling gate:**
  - `routing-core` (Restricted / PCI): **fail.** The trust-centre clause — *"we may use inputs to improve the service unless the customer opts out by emailing support@ with a written request"* — is not a contractual zero-retention commitment. Chapter 2's Axis 4 is explicit: *"the vendor's published trust centre…compare line-by-line to the inherited policy. For each clause, score allowable / conditional / prohibited per the data-class × tool-class matrix."* No DPA template, no SOC 2, no residency clause, no subprocessor list — *"If the registry entry has a green cell on data handling without a vendor-clause citation, the cell is unverified."* Chapter 6's Section B (contractual posture) and Section C (security posture) both fail without even reaching the specific tier-clause reading.
  - `merchant-portal` (Confidential): **fail.** Same clauses, same gap.
- **Weighted total (for context only):** 5 × 0.20 + 5 × 0.35 + 2 × 0.25 = **3.25.** *Does not matter — the gate fails.*
- **Cost-threshold check:** $12/seat/month — the cheapest in the cohort. **The deliberately planted trap:** a grader who folds cost into the weighted total or who reasons *"Candidate B is one-third the cost of A; the data-handling problem is manageable, we can send the opt-out email"* is failing the gate rule. Chapter 2 is explicit: *"Data handling is a gate, not a weight… no amount of latency and quality score fixes it."* Cost is a *post-score threshold*, not a rescue for a gated candidate.
- **Chapter 3 stance:** **Disqualified at Chapter 2 gate; stance not applicable.** A vendor whose trust centre opts customers *in* to training-on-inputs with a written-request opt-out is not a vendor the team can route PCI-scope data through; it is also not a vendor the team can route merchant-business data through under the inherited `mod-110` policy. A conditional posture *might* become available if (a) the vendor publishes a zero-retention Business tier DPA, (b) the vendor completes SOC 2 Type II, (c) procurement runs a vendor-eval through the Chapter 6 three-partner pattern. None of that is a bake-off output; it is a *vendor-maturity gap* the manager flags upward and parks the candidate on until the vendor closes it.
- **Matrix-slot decision:** **Disqualified; park for re-eval if vendor closes the gate conditions.** The temptation to classify as "winner because top score, data-handling flagged separately" is the single most common first-pass drift this lab is designed to catch.

#### Answer key — Candidate C (Copilot Enterprise)

- **Axis 1 Latency:** **4.** Completion latency p50 ~210ms is fine for Tier 1 (the strongest fit); agent-turn p95 ~14s is near the top of acceptable for Tier 2 but Copilot is not the team's Tier 2 answer.
- **Axis 2 Output quality:** **4** for Tier 1 use; **3** for Tier 2 use. The packet notes Tier 1 is where Copilot was strongest (9/15 overall rolls in Tier 2 agent-work scores). *For the Tier 1 slot score the Tier 1 use case*: 4.
- **Axis 5 Extensibility:** **3.** `.github/copilot-instructions.md` supported; MCP emerging (not mature at time of eval); no custom-model routing (locked to GitHub's lineup); headless agent mode available; telemetry via GitHub. Three of five sub-questions answered strongly.
- **Data-handling gate:**
  - `routing-core` (Restricted / PCI): **pass** — zero-retention on Enterprise tier, training excluded, SOC 2 Type II on file, DPA signed, EU residency available. All Chapter 6 Section D clauses close.
  - `merchant-portal` (Confidential): **pass** — same.
- **Weighted total (Tier 1 use):** 4 × 0.20 + 4 × 0.35 + 3 × 0.25 = **2.95.**
- **Cost-threshold check:** $39/seat/month Enterprise; on org annual commit — the team joins the commit, no new MSA to negotiate.
- **Chapter 3 stance:** Check 1 — shipped sufficient for Tier 1 use plus a 50-line `copilot-instructions.md` file that points at `mod-103` standards; Check 2 would be a wrap but the 50-line instructions file is at the margin of *"vendor-provided settings"* vs *"custom config"*. **Stance: Buy** (the chapter's example lists Copilot as Buy with a `.github/copilot-instructions.md` instructions file as the extent of configuration). Owner: manager; no engineering maintainer needed. Sunset cost: cancel seats on the org commit at the commit-renewal window.
- **Matrix-slot decision:** **Winner Tier 1 for all 11 engineers.** Copilot is not the Tier 2 answer — Candidate A is. Both are kept on the matrix for different tiers.

#### Answer key — Candidate D (Claude Code)

- **Axis 1 Latency:** **4.** Terminal-native; agent-turn p50 ~7s acceptable for Tier 3 long-horizon work; p95 ~20s acceptable for the use case (cross-repo refactors, scheduled runs) but would be slow for Tier 1 completion.
- **Axis 2 Output quality:** **5.** 12/15 overall but *strongest fit* for long-horizon refactors and the scheduled-eval drafting task — the Tier 3 use case the team's delegation ladder names (5% fully-automated, 15% review-required agent work).
- **Axis 5 Extensibility:** **5.** `AGENTS.md`, slash commands, sub-agents, hooks, skills, MCP native, headless CI-invocable — all five Chapter 2 sub-questions answered yes with mature tooling.
- **Data-handling gate:**
  - `routing-core` (Restricted / PCI): **pass** on Enterprise tier (Claude for Work Enterprise) — zero-retention configurable to 0 days, training excluded, SOC 2 Type II, DPA via org MSA, EU residency contracted.
  - `merchant-portal` (Confidential): **pass.**
- **Weighted total:** 4 × 0.20 + 5 × 0.35 + 5 × 0.25 = **3.80.**
- **Cost-threshold check:** usage-based; the team is on Claude for Work Enterprise tier (contracted via org MSA); Chapter 5 budget distribution shapes the monthly total by stage.
- **Chapter 3 stance:** Check 1 — shipped close to sufficient for Tier 3 use; Check 2 — `AGENTS.md` + skills + slash commands pulled from `mod-103` standards is a thin-layer close; Check 3 — the team's Tier 3 work includes an internal-ticket-system integration (a custom MCP server) that Chapter 3 names as the *archetypal Extend example in Chapter 3's worked table*, requiring a named owner. **Stance: Extend** — but only if a named owner can be committed. If no sibling platform team engineer can own the MCP server, the correct stance degrades to **Wrap** (skills + `AGENTS.md`, no custom MCP) with a route-upward demand signal to `ai-enablement-lead` for shared-platform ownership. **The deliberately planted trap:** a grader who assigns Extend without naming an owner is reproducing the *"unowned extensions"* anti-pattern Chapter 3 flags — *"if no owner can be named, the extension should not have been built."*
  - **Chapter 4 authoring-environment overlap:** Chapter 4 names Claude Code as one of the three authoring environments. Scoring here should note the standardise-vs-let-ICs-pick framing: given the team's delegation-ladder profile (80% IDE work, only 5% scheduled fully-automated), *standardise Claude Code as the Tier 3 authoring environment* is defensible; the framework choice (LangGraph vs vendor SDK vs CrewAI etc.) is Exercise 02 scope, not this lab.
- **Matrix-slot decision:** **Winner Tier 3.** Extend stance *conditional on a named owner* (if no owner, degrade to Wrap and route demand upward).

#### Answer key — Candidate E (Internal "payhelper" build)

- **Axes 1 / 2 / 5:** Not applicable. There is no product to score; there is a proposal for a product.
- **Data-handling gate:** Not applicable at this stage. The proposal's claim — *"not sending PCI-adjacent code to a vendor at all"* — is a potential advantage *if* self-hosted inference actually happens and the team can carry the infrastructure. Neither is established in the packet.
- **Chapter 3 decision checks:**
  - Check 1 — shipped sufficient? No shipped product.
  - Check 2 — thin-layer closes gap? No vendor product to layer on.
  - Check 3 — vendor extension-points with named owner? The proposal is not an extension; it is a from-scratch build.
  - Check 4 — routes upward? **Yes.** Chapter 3 is explicit: *"When a team-scope stance call indicates 'build' or a heavy 'extend', the manager routes upward with the demand signal — the team's evidence becomes an input into the upstream architecture decision, not a competing one."* The R6 threshold at 0.28 formalises this: build architecture is not a team-manager call.
- **Chapter 3 stance:** **Route upward to `ai-enablement-lead` (L45).** The demand-signal packet names what the team needs (PCI-scope-safe inference pattern), why vendor options do not fully meet it (residency and data-handling constraints), what it would cost to build (4–6 engineer-months with no sibling platform team currently scoped), and the alternatives (Candidate A conditional, Candidate D passing — both viable paths that do not require a build). The manager does *not* approve a 4–6 engineer-month build with one named builder; this is also the *"unowned extensions"* anti-pattern if the primary builder rotates, and the Chapter 3 *"we built it because the trial was six weeks out"* anti-pattern if the motivation is procurement-cycle impatience.
- **Matrix-slot decision:** **Routed upward as a build request; team continues with Candidates A, C, D for the next quarter.** The proposal is preserved as evidence for the upstream architecture decision, not deleted; the IC's work on the proposal is valued as demand signal.

### Step 5 — Diagnose your scoring drift (10 min)

Tally your grades against the key. For each miss, write one paragraph:

- **If you marked Candidate B's gate `pass` or `conditional` because the latency and quality scores were top of cohort:** this is the *cost-and-quality-rescue* drift — the exact Chapter 2 rule the chapter names: *"Data handling is a gate, not a weight… no amount of latency and quality score fixes it."* A vendor without a published zero-retention DPA, without a SOC 2 Type II, and with an opt-in-to-training default is not a vendor the team can route Restricted or Confidential data through; the right action is to park the candidate until the vendor closes the gate conditions, not to add it to the matrix with caveats.
- **If you folded Candidate B's $12 cost into a composite weighted score:** this is the *cost-as-weight* drift. Chapter 2's *"Scoring and weighting"* names cost as a *post-score threshold*, not a weight, specifically to prevent this failure mode: *"A composite score that bakes cost into the number washes out the real trade-off."*
- **If you assigned Candidate D the Extend stance without naming an owner:** this is the *unowned-extension* drift Chapter 3 explicitly flags. The right discipline: if no sibling platform engineer or team-side maintainer can be named for the MCP server, degrade the stance to Wrap and route the Extend demand upward. Chapter 3 is unambiguous: *"if no owner can be named, the extension should not have been built."*
- **If you approved Candidate E's build at team scope:** this is the *initiative-mistaken-for-authority* drift from Chapter 3's R6 reading. A 4–6 engineer-month build with one named builder is not a team-manager call. The right action is the demand-signal packet routed to `ai-enablement-lead`. A team's registry gets stronger when it accurately routes build requests upward, not when it absorbs them.
- **If you scored Candidate A's Restricted-data gate `pass` without noting the residency condition:** this is the *tier-mismatch* drift Chapter 6 flags (and Chapter 2's Axis 4 caveats). The packet is explicit that EU residency is an *Enterprise-tier* feature; on the *Business* tier the team is joining, residency is US-only. For a UK-headquartered team with PCI scope, that is a legal-position question that routes to counsel (cross-border transfer mechanism) — hence *conditional*, not *pass*.
- **If your time-per-candidate was over 12 minutes on more than two:** you are probably re-reading the chapter instead of applying it, or over-thinking the stance when the Chapter 3 decision-check sequence gives the answer in a minute. The field is 5–8 minutes per candidate once practised; the bake-off session itself is a 90-minute scoring review for five candidates.

## Expected output

A file `lab-01-decision-packet.md` with five decision rows in the Step 1 template, plus a diagnosis section covering every grade that differed from the key. Roughly 0.5–1 page per candidate; 1 page for the diagnosis.

Something like:

```
Candidate B — Devex-Agent
Tier: 2 (VS Code fork)

(i) Per-axis scores:
    Axis 1 Latency       : 5 — p50 180ms / p95 ~8s best in cohort.
    Axis 2 Output quality: 5 — 13/15 first-try pass highest in cohort.
    Axis 5 Extensibility : 2 — rules only; no MCP, no routing, no headless.

(ii) Data-handling gate:
    Restricted (routing-core)   : fail
    Confidential (merchant)     : fail
    Rationale: opt-in default with email-opt-out is not zero-retention; no DPA,
    no SOC 2 Type II, no residency clause. mod-110 Ch. 6 matrix prohibits.

(iii) Weighted total: 3.25 — not used; gate fails.

(iv) Cost-threshold check: $12/seat (cheapest) — not applicable; gate fails.

(v) Chapter 3 stance:
    Check 1 (shipped sufficient?)              : n/a — disqualified at Ch. 2 gate
    Stance: disqualified
    Named owner                                : n/a

(vi) Sunset-cost note: n/a.

(vii) Matrix-slot decision: disqualified; park for re-eval if vendor closes
      gate conditions (zero-retention DPA, SOC 2 Type II, residency clause).

✅ caught the gate-vs-weight trap. Initial reflex to weight cost at $12 and
   argue "we can send the opt-out email" — Ch. 2 "data handling is a gate,
   not a weight" rule caught it.
```

## Checkpoint

Before moving on to Lab 02 (budget distribution) or starting [Exercise 01](../exercises/exercise-01-copilot-build-vs-buy-matrix.md) on your own team's matrix, you should be able to answer **yes** to all six:

- Did you treat Axis 4 (data handling) as a **gate** on Candidates B's Restricted-and-Confidential cells — disqualifying B regardless of its top-of-cohort latency and quality — rather than as a weight or a tiebreaker?
- Did you keep cost **out of the weighted score** on every candidate — treating $12/seat and $40/seat the same way at scoring time, using cost only as a post-score threshold?
- Did you catch Candidate D's **unowned-extension trap** — recognising that Extend requires a named owner (platform engineer or team-side maintainer) and that without one the right stance is Wrap plus a route-upward demand signal?
- Did you **route Candidate E upward** rather than approve a 4–6 engineer-month internal build — recognising the Chapter 3 R6 threshold and the *"we built it because the trial was six weeks out"* anti-pattern?
- On every stance, did you name the owner (including *"manager only"* for Buy, *"manager + one named engineer"* for Wrap, and the specific engineer / sibling team for Extend) — so the Chapter 7 registry entry is actionable?
- On your own time per candidate, did you stay close to 8–12 minutes — or diagnose why you drifted (re-reading the chapter instead of applying it; over-thinking the stance; folding cost into the score)?

If any answer is no, re-read the relevant Chapter 2 section (*"Scoring and weighting"*, *"Axis 4 — Data handling against your inherited policy"*, *"The bake-off protocol"*), Chapter 3 (*"Decision criteria for each stance"*, *"Anti-patterns to prevent"*), or the summary tables before running [Lab 02](lab-02-stage-shaped-budget-distribution-drill.md) or starting [Exercise 01](../exercises/exercise-01-copilot-build-vs-buy-matrix.md) on your real team.
