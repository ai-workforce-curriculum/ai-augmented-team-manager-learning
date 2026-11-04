# Chapter 5 — The Routing Contract with AI-Risk Engineer and SecOps

> *Under AI augmentation, the manager runs two coordination lines simultaneously during a non-trivial incident — one to the engineered-risk peer who owns the model-and-guardrail chain, and one to the SOC peer who owns the data-and-intrusion chain. Neither reports to the manager. Both have their own practice, their own vocabulary, and their own clock. Without a routing contract authored in cold light, the manager invents the handoff during a hot incident and loses the week after it to cleaning up the resulting confusion. This chapter is the contract.*

## Motivation

The accountability stack from [`mod-103` Chapter 5](../mod-103-review-standards-and-eval-commissioning/05-the-accountability-contract-ai-generates-humans-own.md) names four parties — IC, reviewer, manager, vendor. In a serious incident two more roles come into play that are *not* in the four-party stack because they are peer specialists outside the manager's reporting line:

- **`ai-risk-engineer` (peer, level 25, AI Governance family).** Owns engineered-risk depth: red-team reproduction, guardrail design, model-level evaluation, threat modelling. Manager-scope mod-109 commissions this work and acts on it; the engineer owns the method.
- **SecOps / DFIR** (depending on the organisation's structure, this is the Security Operations Center, a DFIR team, or a security-engineering function). Owns the SOC-side chain: forensic timeline, eradication, recovery, regulator-facing timeline when the incident touches data exposure, credential compromise, or intrusion.

The manager's job is not to replicate either specialty. It is to **recognise the trigger that routes an incident to each**, **run a clean handoff**, and **keep team-scope communication coherent while the specialists run their parallel chains**. The failure modes are symmetric and common:

- *Under-routing.* The manager tries to run the incident alone to avoid "escalating." The engineered-risk work is not done properly; the SOC-side exposure is missed; the post-mortem is incomplete; the executive stakeholder is told a story that will be contradicted when the specialists arrive later.
- *Over-routing.* The manager escalates every incident to both peers; the peers' bandwidth is spent on small cases; the team learns that routing to the specialists is always slow and expensive, and starts not reporting incidents. The specialists stop treating the manager's routing as useful signal.

The routing contract is the written agreement that makes the triggers specific. Exercise 04 co-authors it with the actual humans (or roles) at the organisation.

## Core concepts

### Three parallel chains in a serious incident

A workable mental model: in a serious AI-produced incident, three chains run in parallel.

- **The team chain.** Detection, triage, containment, trace preservation, team-side communication, post-mortem, backfeed. Manager-owned. The subject of Chapters 2 and 3.
- **The engineered-risk chain.** Reproduction of the model behaviour, side-by-side testing against a different prompt / version / policy, guardrail design, broader exposure audit (does this failure mode exist elsewhere in the team's AI systems?), long-form red-team work. `ai-risk-engineer`-owned.
- **The SOC chain.** Forensic timeline, data-exposure assessment, credential-rotation decisions, intrusion-containment, regulator-notification clock. SecOps-owned.

The three chains compose around a shared timeline and a shared trace. The manager's coordination job is to make sure (a) the right chains are running (not all three run on every incident), (b) the chains are not duplicating work, and (c) the comms to leadership and stakeholders are consistent across the three chains.

### Trigger line 1 — when to route to `ai-risk-engineer`

The engineered-risk peer should be engaged on an incident when one or more of the following triggers:

- **The incident class is Class 2 (prompt injection) or Class 4 (model regression).** Both have engineered-risk work that only the specialist can do (reproduction, guardrail re-design, broader exposure audit).
- **The incident class is Class 1 (hallucination) and a commissioned eval was supposed to catch it.** The question "why did the eval not catch this" is an engineering question for the engineer who authored the eval.
- **The incident class is Class 3 (unauthorised tool use) and the agent policy was authored with the engineer.** If the engineer owns the agent policy being updated, they own the update.
- **The post-mortem's Section 3 Layer 5 (model behaviour) analysis requires model-level reproduction.** Any analysis that needs to say "the model does X on prompt Y" requires reproducing it; the engineer does the reproduction.
- **The incident has broader exposure implications.** A failure mode on one of the team's AI systems is probably not unique to that system; the engineer runs the audit across the organisation's AI surface.

What *not* to route to the engineer for: incident commander duties, team-side communication, team-specific policy decisions, scope decisions on which workflows the team allows AI on, performance-management conversations. The engineer is the method specialist, not a replacement for the manager.

### Trigger line 2 — when to route to SecOps

The SOC should be engaged when one or more of the following triggers:

- **Data exposure.** Sensitive data (personal data, customer data, financial data, authentication secrets, proprietary code) was potentially exposed to an unauthorised party, including via the model's training-data update path if that is in question.
- **Credential compromise.** Any credential (API key, OAuth token, service account, user credential) was potentially exposed, used, or exfiltrated.
- **Intrusion signal.** The incident suggests an unauthorised party interacted with the team's AI systems — e.g., a prompt injection with evidence of a deliberate adversary; a tool call that exfiltrated to an external destination; unusual access patterns on an agent endpoint.
- **Destructive action on production systems.** An agent took a destructive action affecting production data, production infrastructure, or external systems where the organisation has obligations.
- **Regulatory clock implications.** The incident potentially triggers a regulator-notification clock (GDPR breach notification, state breach-notification laws, sector-specific regulators, EU AI Act Article 73 serious-incident reporting for high-risk systems). SecOps and legal counsel together manage the clock; the manager flags the trigger.

What *not* to route to SecOps for: pure-quality failures with no security-visible aspect (Class 1 hallucination with no data exposure), Class 4 regressions with no data-handling change, Class 3 unauthorised-tool-use that was contained within the team's authorised scope.

A SOC incident has its own severity ladder and its own timeline obligations. When SecOps is engaged, the SOC-side severity typically overrides the team-side severity for external communication and regulator-facing clocks; the team-side severity continues to apply for team-internal work. The manager runs team-side; SecOps runs SOC-side; the two coordinate on shared stakeholders.

### Trigger line 3 — when to flag upward

Three upward handoffs exist:

- **To `ai-enablement-lead` (L45) or `ai-engineering-manager` (L50).** When the incident affects more than one team, when the fix requires a change beyond the manager's team's scope (e.g., an organisation-wide tool-authorisation change), or when the incident needs to be communicated to multiple teams whose AI practice could be affected.
- **To `head-of-ai-governance` (L60) or `chief-ai-officer` (L70).** When the incident has board-level implications, when a regulator is engaged, when public disclosure is in play, or when program-level governance changes are warranted.
- **To counsel through HR or GC.** When the incident has legal exposure — regulator notification obligations, contract-breach questions with a customer or partner, employment-law implications (rare but possible when the incident involves an IC's conduct), external-disclosure questions.

The upward handoff is distinct from the specialist handoff. The specialists do technical work on the incident; the upward handoff informs or hands off leadership-level decisions. The manager runs the upward handoff themselves; the specialists participate as technical advisors.

### The structure of a clean handoff

A handoff to a specialist peer is not "forwarded a Slack thread." It is a specific five-field message:

1. **The incident identifier.** Ticket number, channel link, date.
2. **The severity and incident class.** The team-side severity (Sev-N) and the class picker (one of the four plus any composition).
3. **The preserved trace.** Link to the trace archive (per Step 4 of Chapter 2). The specialist cannot do their work without this.
4. **The specific ask.** "Please reproduce the model behaviour side-by-side against version X" / "Please audit for data exposure on the following access paths" / "Please tell us whether the failure mode exists elsewhere in our agent surface." A specific, bounded ask, not "please take a look."
5. **The timeline expectation.** When the manager needs the specialist's output to meet the team's post-mortem clock (within one week, typically) and any upward-communication clock.

The specialist responds within their own SLA (typically published or agreed at Exercise 04 time). If they do not, the manager escalates up their reporting line, not down their own team. Specialist-bandwidth problems are a management-to-management conversation.

### The shared vocabulary

The specialists work in a different vocabulary than the team-scope manager. Three pieces of shared vocabulary that need to be agreed in Exercise 04:

- **Incident-class mapping.** The team uses the four classes from Chapter 4. The engineer may use OWASP LLM Top 10 numbering, MITRE ATLAS techniques, or NIST AI RMF categories. The mapping (per Chapter 4's summary) is the shared vocabulary.
- **Severity mapping.** The team-side severity (Sev-1..4) may not match the SOC-side severity (which is typically a security-incident ladder — Critical/High/Medium/Low). The mapping is agreed at Exercise 04.
- **Trace-archive location.** Everyone has to be able to find the trace. Whether it is a specific observability platform (LangSmith, Weave, Arize), a ticket system (Jira, Linear, GitHub Issues with specific labels), or a shared drive, the location is agreed and documented in the runbook.

### Leadership-ready communication

While the three chains run in parallel, the manager keeps the executive-stakeholder communication coherent. A workable discipline:

- **One update, one voice.** One person writes the update to the executive stakeholder, even if three chains have contributed. Typically the manager, or in Sev-1 incidents the incident commander with the manager's review.
- **Three fields.** What happened (one sentence), what is being done (three bullets covering team, engineered-risk, SOC if applicable), what is next (one sentence with a time). The three-field discipline is the same discipline as the structured report in Step 5 of Chapter 2, but tuned for a non-engineering audience.
- **Timeline discipline.** Updates on a predictable cadence (every 2 hours during active incident response for Sev-1; every 4 hours for Sev-2; end-of-day for Sev-3). Not "I'll update when I know more" — that produces anxious upward-poking. A predictable cadence lets leadership plan.
- **No speculation on root cause until the specialists say so.** Speculation that is later contradicted costs the manager credibility twice — once for the wrong speculation, once for the correction. If the engineer has not reproduced yet, the update says "reproduction in progress; expected by EOD."
- **One final write-up.** The post-mortem from Chapter 3 is the final artifact. Earlier updates are superseded, not stacked. The post-mortem is the record; the Slack updates are workflow.

### The quarterly routing-contract review

The routing contract is not authored once and forgotten. A quarterly review ritual (co-authored in Exercise 04) walks:

- Incidents in the quarter that engaged the specialists: did the triggers fit the contract? Any mis-routes?
- Incidents that did *not* engage the specialists but perhaps should have: anything the manager now wishes had routed differently?
- Changes in the specialists' availability, team structure, or scope.
- Changes in the organisation's SOC procedures, incident-response SLAs, or regulator-notification procedures.
- The vocabulary mapping — any new incident patterns needing an addition to the mapping.

The review is a 30-minute meeting with the specialists; the output is a change-log entry on the routing contract. [`mod-112`](../mod-112-cross-functional-leadership-and-ritual-calendar/)'s ritual calendar is where this lands.

### What this contract is *not*

- **Not a substitute for a security IR process.** The organisation's existing security IR runbook is the authority. The routing contract names *when the team's incident becomes a security incident* and the handoff; the security IR process runs from there.
- **Not a procurement SLA with a vendor.** The routing contract is with internal peers. Vendor engagement (Class 4 incidents, OWASP-category security issues with vendor products) is a vendor-governance question (mod-111) and is co-authored by vendor management, not here.
- **Not a political document.** The contract is operational. It names triggers and handoffs; it does not negotiate scope between the manager and the specialist. Scope is negotiated at the manager-to-manager or specialist-to-leadership level.
- **Not legal counsel.** Legal notification obligations and regulator-facing decisions are counsel's domain. The routing contract names the triggers that get counsel engaged; counsel decides what to do with them.

### Common failure modes

- **Specialists find out about an incident from a leadership channel, not from the manager.** This is a routing failure; the manager should be the first inbound to the specialist, not the last. Fix: the trigger lines above are checked at triage, not at post-mortem.
- **"We don't need to involve the risk engineer, it was just a small thing."** Often correct for Sev-4, often wrong for Sev-2 and Sev-3. The engineer's bandwidth is finite but their broader-exposure audit is specifically what prevents the next incident; the trigger is a floor, not a ceiling.
- **The SOC is engaged for a non-security incident and resents the escalation.** Over-routing. Fix: the SOC-trigger list is explicit about what is *and is not* a security incident; the manager reads it and defaults to not-routing when unsure, then follows up with the SOC lead on the call.
- **Specialists are engaged but not given the trace.** The specialist cannot work. Fix: Step 4 of Chapter 2 is non-negotiable; the trace is in the handoff message.
- **Two parallel comms streams to leadership — one from the manager, one from the specialist — contradict each other.** Fix: one update, one voice. Specialists feed into the manager's update; they do not write the update to the executive stakeholder themselves unless explicitly agreed.
- **The contract exists on paper but is never reviewed.** Three quarters later the specialists have changed roles and nobody knows who owns the routing. Fix: quarterly review ritual.

## Example: the three chains in a composed incident

Illustrative composite. Carries forward from Chapter 4 the Class 2 (prompt-injection via README) case but makes it more serious.

The agent was authorised to run shell commands. A dependency's README contained an injected instruction. The agent ran the command. The command *downloaded and executed a script from an external URL.* The script exfiltrated an environment variable containing an API key for a third-party service. The IC caught it in the terminal output 20 minutes later. The team manager gets paged.

**Team chain (manager).** Severity Sev-1 (external exfiltration, non-reversible, partner-facing impact). Triage class: Class 2 + Class 3 composed (injection + unauthorised-in-spirit tool use). Incident commander: senior IC on the team. Contain: agent session terminated; shell tool authorisation revoked team-wide pending review; API key rotated. Trace preserved: the injected README, the agent session, the tool-call sequence, the exfiltrated environment. Report posted in `#eng-ai-incidents`. The manager flags all three trigger lines simultaneously.

**Engineered-risk chain (`ai-risk-engineer`).** Engaged within 20 minutes of the trigger flag. Scope of ask: *reproduce the injection, identify what other agent systems on the team's surface have similar shell authorisation, author the guardrail that would have prevented this.* Timeline: reproduction by EOD day 1; broader audit by EOD day 3; guardrail design by EOD day 7. The engineer runs the method; reports findings into the team's post-mortem on day 5.

**SOC chain (SecOps).** Engaged immediately on the exfiltration signal. Owns: forensic timeline (what the script actually did, whether the API key was used downstream, whether there is any evidence of a deliberate adversary behind the injected README), credential-rotation decisions (API key rotated; any other credentials in scope), vendor-partner notification clock (the third-party API vendor has a contractual breach-notification clause). The SOC-side severity is "High" by the organisation's security IR ladder.

**Upward.** The manager informs `ai-enablement-lead` (L45) because other teams in the organisation also use the same agent harness with similar shell authorisations; an organisation-wide advisory is likely. The manager flags counsel through the GC's office for the partner-notification clock. No board-level escalation yet; that decision is `ai-enablement-lead`'s to make upward.

**Leadership comms (manager).** One update to the VP at the 1-hour mark: *what happened (one sentence), what is being done (team contain + risk audit + SOC forensic in progress), what is next (next update at hour 3).* Cadence maintained every 2 hours until EOD day 1; every 4 hours day 2; EOD daily thereafter. No speculation on "whether we were targeted" until SOC finishes its timeline on day 2.

**Post-mortem (day 7).** Blameless post-mortem run per Chapter 3. Attendance: manager, IC, reviewer (who approved the agent authorisation at the time), incident commander, risk engineer, SOC lead, `ai-enablement-lead`. Fault chain walked outside-in: reviewer (approved the shell authorisation six months ago under different threat model); IC (invoked the agent without knowing the injection surface); harness (did not sandbox shell authorisations); context (the injected README); model behaviour (faithfully followed the injected instruction — Layer 5 action item is *none*; Layer 3 is where all the action is).

**Action items.** (1) Revoke shell authorisation across the team's agent systems; re-authorise only with sandboxing and explicit per-invocation HITL (mod-106 Chapter 6 + Chapter 4). (2) README ingestion goes through an input-sanitisation layer (mod-103 Chapter 3 standards-as-code stack). (3) New eval row: injection-detection on README-shaped content (mod-103 Chapter 4 via risk engineer). (4) Organisation-wide advisory authored by `ai-enablement-lead` using the team's post-mortem as source. (5) Vendor-governance ticket (mod-111) on the third-party vendor's notification SLA.

**Backfeed completed within two weeks.** Routing contract updated with a change-log entry: *shell-tool authorisation incidents now auto-trigger SOC engagement regardless of exfiltration signal.*

The scenario is unpleasant but survivable. The three chains running in parallel, with the manager coordinating, is what makes it survivable. The three chains improvised during the incident would have been chaos.

## Summary

- **Three parallel chains** run in a serious AI incident: the team chain (manager-owned), the engineered-risk chain (`ai-risk-engineer`-owned), the SOC chain (SecOps-owned). The manager coordinates; the specialists own their methods.
- **Trigger line 1 (`ai-risk-engineer`):** Class 2 or Class 4 incidents; Class 1 incidents where a commissioned eval should have caught it; incidents with broader-exposure implications; any post-mortem analysis requiring model-level reproduction.
- **Trigger line 2 (SecOps):** data exposure; credential compromise; intrusion signal; destructive action on production or external systems; regulator-notification clock implications.
- **Trigger line 3 (upward):** multi-team impact → `ai-enablement-lead` (L45) / `ai-engineering-manager` (L50); board / regulator / public disclosure → `head-of-ai-governance` (L60) / `chief-ai-officer` (L70); legal exposure → counsel through HR or GC.
- **Clean handoff = five fields:** incident identifier, severity + class, preserved trace link, specific bounded ask, timeline expectation.
- **Shared vocabulary** agreed in [Exercise 04](exercises/exercise-04-routing-contract-with-risk-engineer-and-secops.md): incident-class mapping (team 4-classes ↔ [OWASP](https://genai.owasp.org/) ↔ [ATLAS](https://atlas.mitre.org/) ↔ [NIST AI RMF](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf)), severity mapping (team ladder ↔ security ladder), trace-archive location.
- **Leadership comms discipline:** one update, one voice; three fields; predictable cadence; no root-cause speculation until specialists confirm; one final post-mortem write-up.
- **Quarterly review** of the routing contract — triggers, mis-routes, availability changes, vocabulary updates — lands on the [`mod-112`](../mod-112-cross-functional-leadership-and-ritual-calendar/) ritual calendar.
- **Common failure modes:** specialists learn from leadership not from the manager; "we don't need to involve them" on medium severities; over-routing to the SOC; handing off without trace; two parallel comms streams contradicting; contract never reviewed.
- **Not a substitute for** the organisation's security IR process, vendor-governance SLA, or legal counsel. Manager flags triggers; specialists and counsel own the decisions in their domains.
- **Composes with** [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) (eval commissioning with the risk engineer), [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) (routing / HITL / tool-authorisation amendments that follow handoffs), [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) (policy stack the specialists work in), [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) (vendor governance for Class 4 trigger), and [`mod-112`](../mod-112-cross-functional-leadership-and-ritual-calendar/) (ritual calendar).
