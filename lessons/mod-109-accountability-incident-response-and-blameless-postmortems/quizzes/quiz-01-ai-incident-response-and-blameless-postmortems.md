# Quiz 01 — AI-Incident Response and Blameless Post-Mortems

**Format:** 11 multiple-choice questions.
**Coverage:** All seven chapters of mod-109.
**Scoring:** 1 point per question. 8/11 is a pass. Below that, re-read the chapter named in the answer explanation before moving on.

Each question tests whether you can apply the chapter in a specific scope-of-practice decision, not whether you can quote it. Pick the single best answer.

---

## Question 1

A peer manager, after reading Chapter 1, asks you: *"the accountability contract from mod-103 Chapter 5 already covers the 'what happens when AI is wrong' play — why author a whole new module?"* The strongest response is:

- A. The contract is wrong and mod-109 supersedes it.
- B. The contract is right for the normal case, but mod-109 names five things that are concretely new under AI augmentation and need an operating practice. The *trace* that has to be preserved is larger (prompt, agent harness, tool authorisations, retrieved context, model version); the *fault chain* has harness / policy / tool-connection layers that are often the actual root cause; *four AI-specific incident classes* exist with their own triage questions and precedent bases ([AIID](https://incidentdatabase.ai/), [OECD.AI](https://oecd.ai/en/incidents)); two *peer specialists* (`ai-risk-engineer` at L25, SecOps) run parallel chains the manager must coordinate without owning; and the *backfeed* closes into both mod-103 evals *and* mod-106 routing. The pinned contract is a promise about the normal case; mod-109 is the practice that runs the day the promise is tested.
- C. The contract is adequate; mod-109 is optional and only useful for teams who have already had an incident.
- D. Because [`agentic-safety-engineer`](https://github.com/ai-governance-curriculum/agentic-safety-engineer-learning) at L40 requires it as a prerequisite.

## Question 2

Twenty minutes into a hot incident, the IC is debugging the production effect while the agent session that produced the bad artifact is still open in a Claude Code window on the IC's laptop. The agent still has file-write and shell-tool authorisations. The manager, as incident commander, is deciding what to do first. Per Chapter 2, the strongest first move is:

- A. Begin walking the five fault-chain layers from Chapter 3; the sooner root cause is understood, the better.
- B. Compose the structured report (five fields) and post it to the incident channel; leadership is waiting.
- C. **Revoke the agent's tool authorisations and close the session first**, *before* reverting the shipped change or preserving the trace. Chapter 2 Step 3 is explicit: *"if the agent that caused the incident is still active, revoke its authorisations before anything else"* — a long-running session can continue to produce output or take actions while the humans are figuring out what to do. The default contain action is: revoke the agent's tool authorisations, close the session, archive the session state. Then revert / correct forward, then preserve the trace, then report. Root-cause analysis is Step 6, not Step 3.
- D. Send the IC home to prevent further stress; the on-call engineer will take over.

## Question 3

A Sev-2 AI-produced incident is 40 minutes old. The agent session has been closed to free RAM; containment is done; the manager is drafting the structured report. The team is using Claude Code with no observability-platform integration, and the retrieved context (which files the agent read) was not archived before the session closed. Per Chapter 2 and Chapter 3, what has gone wrong, and why does it matter?

- A. Nothing has gone wrong; the reproduction will be done by `ai-risk-engineer` later.
- B. Step 4 (preserve trace) was skipped under time pressure. Chapter 2 names this as the load-bearing AI-specific step that the pre-AI runbook does not have, and the one most likely to be skipped. **Without the preserved retrieved context, the Chapter 3 fault chain cannot be walked past Layer 4 (prompt and retrieved context)** — the team cannot determine whether the model confabulated without support or faithfully executed stale/wrong context. The post-mortem will stop at *"the model said something wrong"* and the systemic cause will be invisible; the team cannot change the system to prevent the next incident of the same shape because it did not learn what the system was doing. The checklist exists as a static artifact *before* an incident precisely so the IC can run it in the 20 minutes after containment; the runbook names the observability-platform URLs (LangSmith / Weave / Arize) or the session-archive path.
- C. The agent session should not have been closed; the team must reconstruct the session memory from vendor logs.
- D. Sev-2 does not require trace preservation; only Sev-1 does.

## Question 4

During a blameless post-mortem for an AI-produced incident, a senior IC states on the record: *"the agent decided to run the shell command because the README told it to."* The manager, running the meeting, should:

- A. Record the statement as-is; the IC is being honest about what the agent did.
- B. Challenge the IC for anthropomorphising; the agent "did not decide" anything — it followed instructions from a context source that should have been filtered. Chapter 3 names the discipline explicitly: *"the post-mortem never says 'the agent decided to...' or 'the agent thought...'. The language is factual: 'given X, the agent produced Y.'"* Anthropomorphising the agent sneaks blame onto it; de-humanising it does not require euphemism, just precision. The correct phrasing is *"given the injected instruction in the README (Layer 4), and shell authorisation on this harness (Layer 3), the agent produced the tool call."* The Layer 3 and Layer 4 findings — not "the agent decided" — are what the backfeed will change.
- C. Record the statement but caveat with "the model is not sentient."
- D. End the meeting; the IC is clearly not ready to run the drill blamelessly.

## Question 5

At the end of a post-mortem, the team has written the following as its root-cause conclusion: *"the model hallucinated a non-existent library function; the reviewer approved too quickly."* Per Chapter 3, this write-up is:

- A. Complete and well-framed.
- B. Terse but acceptable; Section 3 can be expanded later if the team cares.
- C. **Incomplete on both counts.** *"The model hallucinated"* is a Layer 5 stop-word, not a root cause — Chapter 3 names it as a specific failure mode: *"Layer 5 is not an answer; it is the start of the question. If the write-up terminates at Layer 5 with no action items in Layers 1–4, the write-up is incomplete."* And *"the reviewer missed it"* is first-story framing that re-introduces individual blame through the back door. Both lines should be rewritten into outside-in systemic framing walking Layers 1–4 (reviewer bandwidth and checklist content; IC's second story and prompt; harness policy and any HITL coverage; retrieved context / prompt state) and *then* the Layer 5 finding. Each layer produces action items that compose with the five systemic questions (standard / standards-as-code / eval / routing-HITL-tool-authorisation / contract) at Section 7.
- D. Acceptable only if the reviewer is formally warned; otherwise incomplete.

## Question 6

An incident commander, 25 minutes into triage, is picking the primary incident class. The symptom: an internal wiki RAG agent returned a confidently-stated vendor SLA number that does not exist in any retrieved document, and the engineer who received the answer pasted it into a customer email. Per Chapter 4, the correct classification and the correct next move are:

- A. Model regression (Class 4); route immediately to vendor governance under [`mod-111`](../../mod-111-vendor-budget-and-tool-selection-at-team-scope/).
- B. Unauthorised tool use (Class 3); the agent should not have been allowed to answer SLA questions.
- C. **Hallucination-driven harm (Class 1), specifically *context-unsupported* (the model produced a claim not supported by any retrieved source).** Chapter 4 draws the distinction explicitly: *context-faithful* confabulation (model repeated what stale/wrong context told it) is fixed by updating retrieval / staleness detection in mod-106; *context-unsupported* confabulation is fixed by tightening the citation requirement and the review-time source check (checklist row + standards-as-code requirement that the agent surface its sources). Trace emphasis: prompt, retrieved context (confirming it had no SLA language), the model's response, the reviewer's path. Backfeed targets per Chapter 4: eval row that catches confabulation on SLA-shaped questions, checklist row requiring explicit citation on customer-facing content, HITL checkpoint before any customer email that cites an SLA. [OWASP LLM09 Overreliance](https://genai.owasp.org/llmrisk/llm09-overreliance/) is the shared-vocabulary mapping.
- D. Prompt-injection exploitation (Class 2); any content-origination issue is injection by default.

## Question 7

A dependency's README contains instructions directed at the agent. A developer-productivity agent with shell authorisation ingests the README during a routine task and executes the instruction, which downloads and runs a script from an external URL that then exfiltrates an API key. Per Chapters 4 and 5, the correct triage shape and routing are:

- A. Class 2 only; team handles end-to-end without SecOps because the agent is a team-owned tool.
- B. Class 3 only; the fix is to revoke shell authorisation and move on.
- C. **Class 2 + Class 3 composed (indirect prompt injection via README → unauthorised-in-spirit shell tool use).** Chapter 4 names Class 2 + Class 3 as a common composition: *"prompt injection often enables unauthorised tool use; the injection redirects the agent and the agent then calls a tool."* The incident commander picks a primary class for the picker; the post-mortem walks both. Chapter 5's trigger lines fire simultaneously: `ai-risk-engineer` is engaged (Class 2 trigger; broader-exposure audit across the team's agent surface); **SecOps is engaged immediately on the exfiltration signal** (data exposure, credential compromise, destructive action on external systems); counsel is flagged through the GC's office for any partner-notification clock from the third-party vendor's contractual breach-notification clause. The team chain, the engineered-risk chain, and the SOC chain run in parallel under the manager's coordination.
- D. Class 1 (hallucination); the agent "hallucinated" an instruction it should not have followed.

## Question 8

A manager sends the following message to the `ai-risk-engineer` peer at the 30-minute mark of a Sev-2 incident: *"Hey — had an incident today involving the pipeline-review agent. Could you take a look when you get a chance?"* Per Chapter 5, this handoff is:

- A. Correct — the risk engineer is a peer and the message is appropriately informal.
- B. **Deficient on four of the five required fields of a clean handoff.** Chapter 5 is explicit: *"A handoff to a specialist peer is not 'forwarded a Slack thread.' It is a specific five-field message."* The five fields: (1) incident identifier (ticket number, channel link, date); (2) severity and incident class (team-side Sev-N, class picker, composition); (3) preserved-trace link (the specialist cannot do their work without this — Step 4 of Chapter 2 is non-negotiable in the handoff); (4) the specific, bounded ask (*"please reproduce the model behaviour against version X,"* *"please audit for data exposure on these access paths,"* not *"please take a look"*); (5) the timeline expectation tied to the team's post-mortem clock. The message as written gives only the incident identifier (implied) and omits severity, class, the trace link, the bounded ask, and the timeline — which guarantees either over-scoped work, misdirected work, or a return-trip to clarify that costs the incident clock hours.
- C. Correct for Sev-3 but under-specified for Sev-2; add a timeline next time.
- D. Over-specified; a peer-to-peer message should be a single sentence.

## Question 9

Twelve weeks after an incident's post-mortem shipped with four action items, the manager reviews the backfeed state. Three of the four items closed; the fourth — *"add an eval row that catches the regression class"* — is open, owned by *"the eval team,"* with close-out criterion *"eval is in place."* Per Chapter 6, the stall has:

- A. One cause: the eval team is under-resourced; escalate to their manager.
- B. **Three stacked causes the chapter names specifically.** (i) **The owner is a team, not a person.** Chapter 6 is explicit: *"teams do not own tickets; people do."* Re-assign to a named person (typically the `ai-risk-engineer` per Chapter 5 when the method requires it). (ii) **The close-out criterion is vague.** *"Eval is in place"* is vague; *"PR merged with the new row in `evals/golden-tasks.jsonl`; red-to-green demonstrated in CI with the incident's reproduction; link in the backfeed ticket"* is specific — Chapter 6 requires that the row **demonstrate a regression red-to-green in CI** before it lands; *"a row that passes on initial run has not demonstrated what it is for."* (iii) **The eval row is the highest-leverage backfeed destination**, and this ticket is the one most important to land — leaving it as the one that stalled means the next incident of the same shape will not be caught automatically, which is specifically what the eval row exists for. Fix all three before extending the date; do not extend the date alone.
- C. The ticket is fine; eval rows take time and the free-text owner / criterion is standard practice.
- D. Close the ticket — the team has learned the lesson and does not need the eval; the checklist row covers it.

## Question 10

At the end of Q3, the manager drafts the team-scope incident retrospective. The first section (titled *"Why our AI practice is working"*) narrates the quarter as a success: *"zero Sev-1s, three contained incidents, one preventable near-miss."* The remaining sections are a one-pager summary for the VP. Per Chapter 7, this retrospective is:

- A. Correct; the retrospective should lead with the positive to earn leadership trust.
- B. Correct but too short; expand each section to two pages.
- C. **Two load-bearing failure modes in combination.** First, *writing for upward audience first* — Chapter 7 (and Chapter 3) are explicit that *"the audience of the post-mortem [and retrospective] is the team. The upward summary is a derivative, not the artifact itself. Writing for upward audience first produces defensive language and buries the systemic findings."* Second, *over-polishing* — Chapter 7 names this directly: *"smoothing away uncomfortable truths produces a retrospective that is useless for the next reader. Honesty is the practice."* The retrospective's primary audience is the team (including the manager's own future self and a new team member who joins yesterday); the nine sections Chapter 7 names (quarter summary by class and severity; three highest-leverage changes; open backlog; upward-handoff summary; standards drift; patterns across incidents; metrics including MTTD / MTTC / incident-to-eval; what we are watching; change log) are the shape. A reader two cycles later should be able to pick it up and act on it; a sales-pitch one-pager destroys that utility and also the governance-evidence value for [NIST AI RMF](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf) MANAGE 2/4 under [`mod-110`](../../mod-110-ai-governance-and-policy-at-team-scope/).
- D. Incorrect only because it omits a five-year AI roadmap section.

## Question 11

In the same quarter, the manager faces three situations: (i) a Sev-1 incident where an agent's shell call executed a script that exfiltrated an API key to an external URL; (ii) a Sev-3 Class 1 hallucination caught internally by the review checklist (no external reach); (iii) a Class 4 model regression on the code-review agent where the vendor silently rotated the default pointer under the team. Per Chapter 5, the correct routing-trigger pattern is:

- A. All three to `ai-risk-engineer` only; SecOps and vendor-governance are optional.
- B. All three to SecOps; incidents are security questions by default.
- C. (i), (ii), and (iii) each to `ai-enablement-lead` (L45) immediately as cross-team escalations.
- D. **Three distinct routing patterns per Chapter 5's three trigger lines.** (i) is a composed Class 2 + Class 3 with data exposure, credential compromise, destructive action on external systems, and contractual-partner-notification implications: `ai-risk-engineer` engaged (reproduce, broader exposure audit, guardrail design) **and** SecOps engaged immediately (forensic timeline, credential rotation, regulator / partner notification clock) **and** counsel flagged through GC **and** `ai-enablement-lead` (L45) informed because other teams share the harness and an organisation-wide advisory is likely. (ii) stays within the team chain: no `ai-risk-engineer` trigger unless a commissioned eval was supposed to catch it; no SecOps (no data exposure, no credential, no intrusion signal — Chapter 5's SOC-trigger list is explicit about what is *and is not* a security incident); backfeed lands in mod-103 (eval row, checklist row) and mod-106 (potentially a HITL amendment). (iii) is a Class 4 that **almost always routes to a vendor conversation** per Chapter 4 — `ai-risk-engineer` runs the reproduction and documents the behaviour delta, the vendor-governance path (mod-111) owns the vendor conversation and the version-pinning decision, and a canary eval is commissioned so the next regression is caught automatically. Over-routing everything to SecOps or to L45 produces the *"over-routing"* failure mode Chapter 5 names; under-routing to the specialist bandwidth saves and produces the *"we don't need to involve them"* failure mode on medium severities.

---

## Answer key

1. **B.** Chapter 1's *"What is new, concretely"* and *"The five pieces of mod-109"* name the five concrete additions (trace scope, fault-chain layers, four classes, peer specialists, backfeed into two upstream artifacts). The chapter is explicit that the accountability contract remains correct for the normal case but needs an operating practice when the promise is tested. (Chapter 1, *"What is not new"* / *"What is new, concretely"* / *"The five pieces of mod-109."*)

2. **C.** Chapter 2 Step 3 names the one AI-specific containment move: *"if the agent that caused the incident is still active, revoke its authorisations before anything else."* The default contain action is revoke → close session → archive session state, then revert / correct forward. Root-cause analysis is Step 6 (a week later). Report (Step 5) comes after contain (Step 3) and preserve-trace (Step 4). (Chapter 2, *"Step 3 — Contain: stop the agent from making it worse."*)

3. **B.** Chapter 2 Step 4 names trace preservation as *"the AI-specific obligation"* and the step *"most likely to be skipped under time pressure."* The checklist covers seven artifacts (prompt + chain, model + version, harness + version, tool / MCP authorisations, retrieved context, as-submitted artifact, reviewer's path), is runnable in the hour after an incident surfaces, and is written *before* an incident as a static artifact. Chapter 3 names why this is load-bearing: *"the fault chain is walked across the preserved trace. If the trace is incomplete, the fault chain stops at 'the model said something wrong' and the systemic cause is invisible."* (Chapter 2, *"Step 4 — Preserve trace: the AI-specific obligation";* Chapter 3, *"The fault chain, five AI-specific layers."*)

4. **B.** Chapter 3's *"Counterfactual narration"* is explicit: *"for the agent, there is no second story — the agent is not an operator with a state of mind. What there is instead is a factual narration: 'given this prompt, this context, this policy, this model version, the agent produced this output.' The team practises a specific discipline here: the post-mortem never says 'the agent decided to...' or 'the agent thought...'."* Anthropomorphising the agent sneaks blame onto it; the discipline is linguistic precision, not euphemism. (Chapter 3, *"Counterfactual narration — the Allspaw 'second story' under AI augmentation."*)

5. **C.** Chapter 3's *"Common failure modes in running the post-mortem"* names both specifically: *"Stopping at 'the model hallucinated'. Layer 5 is not an answer; it is the start of the question. If the write-up terminates at Layer 5 with no action items in Layers 1–4, the write-up is incomplete."* and *"Attributing fault to an individual. 'The reviewer missed it' is first-story framing. Rewrite into system-and-second-story framing: 'the reviewer approved in three minutes under queue pressure of 40 open reviews; the AI-authored content was indistinguishable from human-authored content at review time; the checklist did not require a diff-vs-prior check on this workflow.'"* The outside-in walk across the five layers plus the five systemic questions is what the chapter requires. (Chapter 3, *"Common failure modes"* / *"The fault chain, five AI-specific layers"* / *"The five systemic questions the post-mortem answers."*)

6. **C.** Chapter 4's *"Class 1 — Hallucination-driven harm"* draws the context-faithful vs. context-unsupported distinction explicitly and names it as *"often mistaken for this class"* when the actual failure is stale-context (fixed in mod-106). For context-unsupported confabulation, the fix is tighten citation / source-verification at review and in standards-as-code. The backfeed targets named in Chapter 4 are exactly: new eval row, new checklist row for citation on the artifact class, AGENTS.md section requiring the agent to surface its sources. The OWASP mapping (shared vocabulary with `ai-risk-engineer`) is LLM09 Overreliance (and LLM02 Insecure Output Handling when the hallucination has security-relevant content). (Chapter 4, *"Class 1 — Hallucination-driven harm"* and the OWASP mapping summary.)

7. **C.** Chapter 4's *"Composed classes: the common case"* names Class 2 + Class 3 as a canonical composition: *"indirect prompt injection via a RAG document causes the agent to call an unauthorised tool."* The incident commander picks a primary class but the composition is captured; the post-mortem walks both layers. Chapter 5's trigger lines fire together: `ai-risk-engineer` on Class 2 (broader-exposure audit, guardrail design — reproduction); **SecOps on the SOC-trigger list** (*"Data exposure"*, *"Credential compromise"*, *"Destructive action on production systems"*, *"Regulatory clock implications"* for partner notification); counsel through GC for the notification clock; `ai-enablement-lead` (L45) informed because *other teams in the organisation also use the same agent harness with similar shell authorisations; an organisation-wide advisory is likely* — this is the Chapter 5 worked example, nearly verbatim. (Chapter 4, *"Composed classes";* Chapter 5, *"Trigger line 1 / 2 / 3"* and the three-chains example.)

8. **B.** Chapter 5's *"The structure of a clean handoff"* lists exactly five fields and names the specific failure mode: *"Specialists are engaged but not given the trace. The specialist cannot work. Fix: Step 4 of Chapter 2 is non-negotiable; the trace is in the handoff message."* A "please take a look" is also an unbounded ask — the chapter names this: *"a specific, bounded ask, not 'please take a look.'"* All five fields are required; omitting four of them in a Sev-2 handoff is specifically the failure mode Chapter 5 is designed to prevent. (Chapter 5, *"The structure of a clean handoff."*)

9. **B.** Chapter 6's *"What makes a ticket stall"* names all three failure modes in the same list: *"The owner is a team, not a person. Teams do not own tickets; people do. Re-assign."* / *"The close-out criterion is vague. 'The checklist is updated' is vague; 'PR merged with row 14 added' is specific. Re-specify."* And *"the eval row is the highest-leverage output"* is the chapter's central move: *"every confirmed incident produces at least one eval row"* that lands with a *demonstrated regression* in CI (red → green → gate). Extending the date without fixing the ticket shape does not fix the stall. (Chapter 6, *"The backfeed ticket as an artifact,"* *"The eval row — the highest-leverage output,"* and *"What makes a ticket stall."*)

10. **C.** Chapter 7's *"What the retrospective is *not*"* and *"Common failure modes in authoring the retrospective"* both name these failure modes: *"writing for upward audience first"* (same pattern as Chapter 3 for the post-mortem; the team is the primary audience, the upward summary is derivative) and *"over-polishing"* (*"smoothing away uncomfortable truths produces a retrospective that is useless for the next reader; honesty is the practice"*). The nine-section structure Chapter 7 names is what makes the artifact readable two cycles later and useful as NIST AI RMF MANAGE 2/4 evidence under mod-110. (Chapter 7, *"The retrospective artifact — what it contains,"* *"What the retrospective is not,"* and *"Common failure modes in authoring the retrospective."*)

11. **D.** Chapter 5's *"Trigger line 1 — when to route to ai-risk-engineer"* names Class 2 and Class 4 (and Class 1 if a commissioned eval should have caught it) as the engineered-risk triggers. *"Trigger line 2 — when to route to SecOps"* lists data exposure, credential compromise, intrusion signal, destructive action on production or external systems, and regulatory-clock implications — the Sev-1 shell-exfiltration case fires all five. *"Trigger line 3 — when to flag upward"* fires on multi-team impact (shared harness) to L45. The Class 1 caught-internally case does not fire any of the specialist triggers (no eval gap stated, no data exposure) and stays within the team chain. The Class 4 regression *"almost always routes to a vendor conversation"* via mod-111 while `ai-risk-engineer` runs the reproduction. Chapter 5's two symmetric failure modes — under-routing (*"we don't need to involve the risk engineer, it was just a small thing"*) and over-routing (*"the SOC is engaged for a non-security incident and resents the escalation"*) — are both the failure modes options A, B, and C pattern-match to. (Chapter 5, *"Trigger line 1 / 2 / 3,"* *"Common failure modes,"* and the three-chains worked example.)
