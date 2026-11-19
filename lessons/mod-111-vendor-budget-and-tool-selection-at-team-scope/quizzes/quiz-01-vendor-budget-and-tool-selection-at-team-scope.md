# Quiz 01 — Vendor Selection, Tool Budget, and Build-vs-Buy at Team Scope

**Format:** 11 multiple-choice questions.
**Coverage:** All seven chapters of mod-111.
**Scoring:** 1 point per question. 8/11 is a pass. Below that, re-read the chapter named in the answer explanation before moving on.

Each question tests whether you can apply the chapter to a specific team-scope decision the manager actually faces — not whether you can quote it. Pick the single best answer.

---

## Question 1

A peer manager pushes back on the module's premise: *"If procurement signs the contract, SecOps runs the security assessment, legal reads the DPA, FinOps architects the commit, and `ai-enablement-lead` owns the org-wide tool framework, what is actually left for a level-40 manager to decide about vendors?"* The strongest response is:

- A. The manager owns the master service agreement because the team is closest to the work; procurement counter-signs the manager's draft.
- B. **The manager owns *selection and evaluation* within the organisation's framework — which tools the team runs, which tier the team runs them on, which seats and tokens go to whom, and when to sunset — and produces the composed tool registry that upstream rollups read.** Chapter 1's shorthand is explicit: *"the manager owns selection and evaluation; procurement owns negotiation and signature; SecOps owns security assessment depth; legal owns clause interpretation; FinOps owns commitment architecture; `ai-enablement-lead` owns the org-wide tool framework. Selection is runnable, logged, and dated."* The manager is not a residual — the manager is the smallest unit at which vendor choice becomes real behaviour on a team, and the registry is the composed evidence an audit actually reads. The role the manager does *not* play is master-agreement signatory; the role the manager does play is per-team integrator who fills the due-diligence checklist from the specialists' outputs, allocates seats and tokens by stage, and keeps the registry dated.
- C. The manager is a pass-through — forward the vendor's trust-centre link; the specialists do the rest.
- D. The manager only acts on new-tool requests; steady-state vendor management lives entirely upstream.

## Question 2

A team has run Cursor + Claude.ai + ChatGPT consumer accounts for twelve months. Each IC bought their own seat on expense; the team has no evaluation rationale, no data-handling position per tool, and no answer to "which tool saw our codebase this quarter." A manager inherits the team and asks what shape the problem is. Per Chapter 1, this is:

- A. An early-lock enterprise-commit problem; the team should negotiate a multi-year rate now.
- B. **Default-tool drift.** Chapter 1 names the three failure modes mod-111 exists to replace, and this is the first: *"The team uses whatever each IC installed first. The budget is a trailing sum of consumer-tier charges; the data posture is undefined; the question 'which model saw our codebase this quarter' has no answer."* The fix is not a faster contract — it is the composed deliverable: a dated tool registry with an evaluation rationale (Chapter 2), a build-vs-buy stance (Chapter 3), a stage-shaped budget (Chapter 5), a due-diligence record (Chapter 6), and a sunset condition (Chapter 7) per entry. Jumping to an enterprise commit without the matrix produces failure mode two (early-lock), which is as bad as drift and more expensive to unwind.
- C. A governance-theatre problem; the team should write a tool-authorisation policy and move on.
- D. An ergonomics problem; the team should standardise on whichever product the senior engineers prefer.

## Question 3

A manager runs a two-week bake-off of three Tier-2 agentic IDEs against fifteen real-backlog tasks. Latency is parity; output-quality scores are close but Candidate A edges B and C; cost is $20/seat/month (A), $25 (B), $40 (C); extensibility: A is model-locked, B and C support MCP, rules, and bring-your-own model; data handling: A's current-tier DPA says *"inputs may be used to improve the service unless the customer opts out via a form and emails support@…"* — the team's inherited policy treats customer-data classes as restricted. Per Chapter 2, the correct read is:

- A. A wins on weighted score; proceed with A because the team can send the opt-out email.
- B. A wins on cost-adjusted score; cost is the tiebreaker.
- C. **A fails the Axis 4 data-handling gate and is disqualified for workflows touching restricted data regardless of latency, quality, or cost.** Chapter 2 is explicit: *"Data handling is a gate, not a weight. If a candidate fails Axis 4 for your data classes, no amount of latency and quality score fixes it. The matrix marks it out of scope for workflows handling the failing data class."* A contractual position that requires an *opt-out by email to support* is not a contractual zero-retention commitment; the team's restricted-data workflows cannot route through A. B wins the Tier 2 slot (equivalent extensibility, data posture to verify at tier, acceptable cost). C is parked unless B is eliminated on another axis. Cost is a *post-score threshold* per Chapter 2 (*"rank by the weighted score first, then ask 'is the best option affordable?' and 'would the second option be good enough at ⅔ the cost?'"*), not a weight that can rescue a gated candidate.
- D. A should be accepted conditionally for non-restricted workflows; the matrix can carry both A and B.

## Question 4

A manager planning a Chapter 2 bake-off picks the four most senior engineers on the team as the pilot cohort — they are the fastest reviewers and the most articulate about what they like. Per Chapter 2, this cohort composition is:

- A. Correct — the senior cohort will produce the cleanest signal.
- B. Correct for Tier 1 (IDE-native) tools; stage mixing matters more for Tier 3.
- C. **A Failure-B pattern waiting to happen.** Chapter 2's bake-off protocol is explicit about cohort composition: *"Three to five engineers, picked across stages per `mod-105` Chapter 4 (not all stage-3 engineers — a tool that works only for stage-3 users is a Failure-B pattern waiting to happen)."* A tool that scores well with four senior stage-3/4 engineers and badly for the stage-1/2 cohort will be adopted on the senior-cohort evidence and then quietly abandoned by the junior cohort — reinstating Failure-B from `mod-105` Chapter 1 (the IC turns the tool off because it is in the way) for the half of the team the enablement programme is trying to reach. The right cohort is stage-mixed: at least one each from stage-1 or stage-2 and stage-3 or stage-4, so the matrix sees the tool's full-team signal rather than its best-case signal.
- D. Correct provided the senior engineers log latency rigorously.

## Question 5

A manager scores the Chapter 2 matrix and the Tier-2 IDE winner is Cursor. The team's review standards live in `mod-103`'s standards-as-code repo; ICs routinely re-paste the style guide into Cursor's chat window. The vendor supports `.cursor/rules/`, custom instructions, MCP servers, and slash commands. Per Chapter 3, the correct stance for Cursor is:

- A. Buy — the shipped experience is sufficient; standards drift is an IC-discipline problem.
- B. **Wrap.** Chapter 3 names wrap as *"the most commonly correct stance"* and describes the exact signal shape here: *"engineers routinely re-explain the team's conventions to the tool"* is a *"signal shipped is not sufficient"*; the *"vendor's extension layer closes the gap at thin-layer cost"* (rules + instructions + a prompt pack is a Check 2 YES) — so stance is Wrap. The team adds a `.cursor/rules/` directory pulled from the `mod-103` standards-as-code artifact, plus a short `project.md`, plus a few slash commands; ~1 engineer-week to initialise, ~1 engineer-week per quarter to refresh; named owner (manager + one engineer); archive-the-wrap-repo sunset. Jumping to Extend (production-grade MCP servers, custom routing) would be a Check 3 question — and Chapter 3 warns that *"Extend is the stance most commonly done badly at team scope"* when the actual gap is closable by rules and prompts.
- C. Extend — stand up an internal MCP server that enforces the standards from the server side.
- D. Build — fork Cursor to add a native standards-enforcement mode the vendor does not ship.

## Question 6

An IC at the end of the Chapter 2 bake-off argues the team should build an internal "team-coach" agent that reads PR history, links commits to tickets, and generates a weekly performance digest. The IC estimates six engineer-months to v1; the manager has one engineer who would be the primary builder. Two commercial products (Linear AI, Jellyfish) cover ~70% of the value. Per Chapter 3, the manager's correct move is:

- A. Approve the build; the IC's estimate is credible and the fit is better than commercial alternatives.
- B. Approve a thin wrap on top of one of the commercial products and build the missing 30% in-house.
- C. **Route upward with a demand-signal packet to `ai-enablement-lead`, not approve the build.** Chapter 3's R6 reading is explicit: *"R6 in the role contract scores the manager's build-vs-buy ownership at 0.28, below the 0.5 threshold at which the role owns the deep architecture question. The manager owns the stance call per tool (buy / wrap / extend) at team scope. The manager does not own the organisation-wide build architecture. When a team-scope stance call indicates 'build' or a heavy 'extend', the manager routes upward with the demand signal."* A six-engineer-month internal-tooling build with one named engineer is also the archetype of *"unowned extensions"* and *"we built it because the trial was six weeks out"* anti-patterns; when the primary builder rotates in Q[N+2], the team is left maintaining an internal product. The demand-signal packet — what the team needs, why vendor options do not meet it, what it would cost — becomes an input into the org-level architecture decision, not a parallel team-side project.
- D. Decline permanently; "team-coach" is not a defensible use of engineering time.

## Question 7

A four-engineer internal-tools team's primary output is "patterns other teams adopt" — short-lived, single-maintainer agents experimenting with new approaches. Each engineer prefers a different authoring environment. The manager drafts an Exercise 02 output that mandates both the agent framework *and* the authoring environment team-wide. Per Chapter 4, this stance is:

- A. Correct — standardisation reduces onboarding cost.
- B. Correct provided the manager sunsets the mandate after the team scales past six engineers.
- C. **Over-standardised for this team's shape.** Chapter 4 names the different standardisation pressures explicitly: *"framework is where multi-engineer maintenance usually happens. Most teams should standardise on one framework (with experiment permission) because the maintenance-coherence matters: when the original builder rotates, someone needs to maintain the agent. Authoring environment is often more personal-ergonomics-heavy — some ICs produce more in Claude Code, some in Cursor, some in Codex. Let-ICs-pick on environment is often defensible for stage-3+ ICs, with the constraint that the artifacts the IC produces (rules, prompts, `AGENTS.md`, slash commands) live in team repos and are portable."* The chapter's *Team B* example is almost this scenario and reaches the same stance: *let-ICs-pick on framework* (single-maintainer agents, short lifecycles, pattern-sharing as output); *standardise authoring environment*; keep the authoring artifacts in a shared team repo so patterns compose. Mandating both wastes the team's structural fit for exploration without gaining the maintenance coherence standardisation exists to provide.
- D. Incorrect — the team should mandate the framework *and* let ICs pick the framework too.

## Question 8

A manager scoping Exercise 02 argues the team should adopt LangGraph "because the vendor SDKs — Anthropic's `claude-agent-sdk` and OpenAI's Agents SDK — are first-party and lock us in." The team's current work is a single agent doing structured data extraction, already written against Pydantic. Per Chapter 4, the strongest response is:

- A. Agree — framework lock-in is a smaller risk than vendor lock-in.
- B. Agree conditionally — adopt LangGraph for the extraction agent and vendor SDKs for future work.
- C. **Disagree: vendor SDK is a serious *buy* option Chapter 4 names explicitly, and the Chapter 3 build-vs-buy framing applies.** Chapter 4 is explicit: *"The vendor SDK is also an option. Anthropic's `claude-agent-sdk` and OpenAI's Agents SDK are first-party SDKs that compete with the third-party frameworks for the 'we need less abstraction' slot. The Chapter 3 build-vs-buy framing applies: if the vendor SDK ships what you need, that is a stronger buy than adding a framework dependency."* Adding LangGraph for a single structured-extraction agent already written against Pydantic is a Check-2 FAIL (shipped is not sufficient) that answers YES to Check 2 of Chapter 3 — a thin wrap around the vendor SDK (or PydanticAI if the type-level correctness matters more than the vendor relationship) is cheaper, has less surface area, and the Chapter 4 observation that *"all four frameworks support OpenAI, Anthropic, and open-weight models"* means framework choice is *not* where model-provider lock-in comes from. Portability sits in *model-provider portability* and *protocol portability* (MCP) — which the vendor SDK supports.
- D. Disagree — the team should run both and let them compete.

## Question 9

A monthly usage review shows one stage-2 IC is at 20 tasks/month on Claude Code against the `mod-105` floor of ~100. The manager drafts a response: *"Reduce their token budget by 80% next month — they are not using the tool, so we are paying for nothing."* Per Chapter 5, this response is:

- A. Correct — budgets should match observed usage.
- B. Correct provided the manager raises the budget back when usage rises.
- C. **Wrong in both direction and interpretation.** Chapter 5 is explicit: *"Floors are a review signal, not a procurement signal. If a stage-2 engineer is at 20 tasks/month instead of 100, that is not a budget-reduction trigger; it is a 1:1 signal that the engineer may be stuck on Failure-B (`mod-105` Chapter 1) — the tool is in the way, the engineer has turned it off, the `mod-105` programme is not landing for them. Reduce the budget on data, not on underuse."* Cutting the budget on stage-1/2 undershoot starves the enablement programme of the exploratory time it needs and reinstates Failure-B; it is also one of the *"common mistakes"* Chapter 5 names (*"caps on stages 1–2"*). The correct response is a 1:1 to diagnose what is blocking the IC — wrong tool fit, missing training, task mix that does not invite AI use — and route the finding into the `mod-105` programme, not into the budget plan.
- D. Correct only if the manager documents the cut in the registry.

## Question 10

A manager reporting to finance rolls seats + tokens + team-share-of-enterprise-commit into a single monthly line: *"Team AI tooling: $8,400/month."* The finance partner approves. Next quarter the token line rises 30% as the `mod-105` cohort progresses from stage 1 to stage 2. Per Chapter 5, this reporting shape is:

- A. Correct — a single number is easier for finance.
- B. Correct provided the manager explains the 30% rise in a note.
- C. **One of the Chapter 5 common mistakes; one of the three failure modes the chapter exists to prevent.** The chapter names it explicitly: *"One-number-to-finance. Rolling seats + tokens + enterprise-share into one line without the three-layer breakdown is a finance-partnership weakness; when one layer moves, the partner cannot see why."* It also names the related failure: *"No stage-shift projection. A budget that reports only current state projects as flat. The Chapter 5 projection is what makes the `mod-104` tile's narrative defensible."* The right shape is three layers broken out separately (seat budget linear in headcount; token budget with its stage distribution; enterprise commitment with the team's share and overage) plus a projection — *"the projected rise is the programme working, not budget drift"* — so when Q[N+1]'s number is 25–30% higher than Q[N]'s, the finance partner already knows why from the Q[N] narrative.
- D. Correct provided the manager's narrative matches the `mod-104` AI-cost tile exactly.

## Question 11

An IC on a Tuesday afternoon asks the manager: *"Our Claude for Work contract is zero-retention Enterprise tier, so I'm good to paste this restricted-class customer file into Claude.ai consumer to get a quick second opinion on the logic — same vendor, right?"* Per Chapter 6, the manager's correct response is:

- A. Agree — same vendor, zero-retention applies across their products.
- B. Agree conditionally — have the IC switch to the Enterprise tier before pasting.
- C. **Correct the IC: zero-retention is a *per-tier* contractual property and the DPA is tied to the service tier, not the vendor.** Chapter 6 is explicit: *"The DPA for Claude for Work is not the DPA for the Anthropic API; the SOC 2 scope for OpenAI Enterprise is not the SOC 2 scope for ChatGPT consumer; Copilot Business and Copilot Enterprise have different data posture. Record the tier explicitly."* The contracted-tier clause is *"Claude for Work (Enterprise)"*; the IC is proposing to route restricted data through *Claude.ai (consumer)*, where training-on-your-data and retention terms are different, no DPA covers the paste, and the data-class × tool-class matrix from `mod-110` Chapter 6 treats the consumer tier as a different tool class entirely. The fix path is to run the query in the Enterprise-tier Claude for Work surface the team is contracted for — or, if the IC has only consumer access to Claude.ai, to open a tool-authorisation-policy exception per `mod-106`. Chapter 6's broader discipline — *"Capture the tier the team actually uses"* — is the one the IC is missing.
- D. Defer — the IC is a stage-4 engineer and knows the contract better than the manager.

---

## Answer key

1. **B.** Chapter 1's *"What vendor selection means at team scope"* and the shorthand table (manager owns selection and evaluation; procurement owns negotiation and signature; SecOps owns security-assessment depth; legal owns clause interpretation; FinOps owns commitment architecture; `ai-enablement-lead` owns the org-wide framework) make the boundary explicit. The manager is the per-team integrator who produces the composed registry upstream rollups read. (Chapter 1, *"What vendor selection means at team scope"* and *"What this module is not"*.)

2. **B.** Chapter 1 names three failure modes — default-tool drift, early-lock enterprise commit, governance theatre — and the described team is the archetypal case of the first. The fix is the composed registry, not a faster contract or a one-paragraph policy. (Chapter 1, *"Motivation"* and *"The five pieces of mod-111"*.)

3. **C.** Chapter 2's *"Scoring and weighting"* is explicit: *"Data handling is a gate, not a weight. If a candidate fails Axis 4 for your data classes, no amount of latency and quality score fixes it."* An opt-out-by-email clause is not a zero-retention contract. Cost is a *post-score threshold*, not a weight. B wins the Tier 2 slot. (Chapter 2, *"Scoring and weighting"* and *"Axis 4 — Data handling against your inherited policy"*.)

4. **C.** Chapter 2's *"The bake-off protocol"* names the cohort shape verbatim: *"Three to five engineers, picked across stages per `mod-105` Chapter 4 (not all stage-3 engineers — a tool that works only for stage-3 users is a Failure-B pattern waiting to happen)."* A stage-3/4-only cohort evaluates the tool's best case, not its full-team signal. (Chapter 2, *"The bake-off protocol"*.)

5. **B.** Chapter 3 names wrap as *"the most commonly correct stance"* and describes this exact signal shape — ICs re-explaining conventions to the tool, extension points that close the gap at thin-layer cost. The decision checks run shipped-sufficient? → NO → thin-layer closes gap? → YES → Wrap. Extend would be an over-commitment; Build is out of scope at team level. (Chapter 3, *"The four stances"* and *"Decision criteria for each stance"*.)

6. **C.** Chapter 3's *"The R6 threshold and what it implies"* is explicit: at 0.28 below the 0.5 ownership threshold, build architecture is not a team-manager call. A six-engineer-month internal-tooling build with one named engineer is also the *"unowned extensions"* anti-pattern. The correct shape is a demand-signal packet routed to `ai-enablement-lead`. (Chapter 3, *"The R6 threshold and what it implies"*, *"Check 4"*, and *"Anti-patterns to prevent"*.)

7. **C.** Chapter 4's *"The standardise vs let-ICs-pick decision"* names the different pressures on framework (standardise for maintenance coherence) and environment (let-ICs-pick for ergonomics, with portable artifacts). The chapter's Team B example — a small team doing exploratory pattern work — is close to the described team and reaches a *let-ICs-pick on framework, standardise environment* stance. Mandating both over-standardises for the team's shape. (Chapter 4, *"The standardise vs let-ICs-pick decision"* and *"Team B"* example.)

8. **C.** Chapter 4 is explicit: *"The vendor SDK is also an option… if the vendor SDK ships what you need, that is a stronger buy than adding a framework dependency."* All four frameworks and the vendor SDKs support multiple model providers, so framework choice is not where model-provider lock-in comes from — portability lives in the model-provider and MCP axes. For a single structured-extraction agent already written against Pydantic, adding LangGraph is over-abstraction. (Chapter 4, *"The four agent frameworks in scope"*, *"Lock-in and portability"*.)

9. **C.** Chapter 5 is explicit on floors as review signals, not procurement signals: *"If a stage-2 engineer is at 20 tasks/month instead of 100, that is not a budget-reduction trigger; it is a 1:1 signal that the engineer may be stuck on Failure-B."* Caps on stages 1–2 are one of the *"common mistakes"* the chapter names. The right response is a 1:1 to diagnose and a route back into the `mod-105` programme. (Chapter 5, *"Token budget distribution"* and *"Common mistakes when first distributing"*.)

10. **C.** Chapter 5's *"Common mistakes"* names *"one-number-to-finance"* and *"no stage-shift projection"* explicitly. The right shape is three layers broken out separately plus a projection that anticipates the Q[N+1] rise as the programme working, not drift. The `mod-104` AI-cost tile narrative depends on this. (Chapter 5, *"The three allocation layers"*, *"Token budget distribution"*, *"Interaction with the `mod-104` AI-cost tile"*, and *"Common mistakes when first distributing"*.)

11. **C.** Chapter 6 is explicit: *"The DPA for Claude for Work is not the DPA for the Anthropic API; the SOC 2 scope for OpenAI Enterprise is not the SOC 2 scope for ChatGPT consumer; Copilot Business and Copilot Enterprise have different data posture. Record the tier explicitly."* Tier is the unit of due-diligence; zero-retention commitments are per-tier contractual properties, not vendor-wide. The matrix from `mod-110` Chapter 6 treats consumer-tier surfaces of the same vendor as different tool classes. (Chapter 6, *"Motivation"*, *"The due-diligence checklist — Section A"*, and *"DPA specifics in the AI-vendor context"*.)
