# Chapter 4 — AI-Specific Incident Taxonomy and Triage

> *"The AI was wrong" is not a diagnosis. It is a cell at the top of a decision tree. Under that cell sit four genuinely distinct incident classes, each with its own triage questions, trace-preservation needs, routing implications, and precedent base. This chapter is the taxonomy the incident commander uses at Step 2, and the lens the post-mortem uses at Step 6.*

## Motivation

Chapter 2 of this module names an "incident-class picker" at the triage step. Chapter 3 names "incident class" as the shape that determines which of the five fault-chain layers is in focus. Both steps depend on there being a taxonomy that fits in the incident commander's head during a high-pressure moment and has enough structure that the subsequent response is not improvised.

Under AI augmentation, four incident classes cover the overwhelming majority of what the team will encounter:

1. **Hallucination-driven harm** — the model produced confidently wrong content that was treated as correct and caused downstream harm.
2. **Prompt-injection exploitation** — untrusted input (RAG document, tool output, user-supplied text) hijacked the agent's behaviour.
3. **Unauthorised tool use** — the agent took an action the policy did not authorise or that the authorisation covered but should not have.
4. **Model regression** — a previously-working behaviour silently changed, typically following a vendor model-version change.

The four classes compose with existing security taxonomies — notably the [OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/) and [MITRE ATLAS](https://atlas.mitre.org/) — rather than replace them. The chapter maps the four classes to those taxonomies so the engineered-risk peer (Chapter 5) can pick up the thread in their preferred frame without a translation layer.

Two public precedent bases ground the practice:

- The **[AI Incident Database](https://incidentdatabase.ai/)** (AIID), run by the [Responsible AI Collaborative](https://incidentdatabase.ai/about/), catalogues publicly-reported real-world AI incidents with structured fields (actor, harm, deployment context) and open data. As of late 2026 it contains over a thousand incidents.
- The **[OECD.AI AI Incidents Monitor](https://oecd.ai/en/incidents)** (AIM), launched 2023 by the OECD AI Policy Observatory, tracks incidents at policy-relevant granularity with international scope.

Both are free to read and public. A team that reads one adjacent case per month gets a precedent base before it needs one. Exercise 03 is the rehearsal.

## Core concepts

### Class 1 — Hallucination-driven harm

**Definition.** The model produced output that was confidently wrong — a fact, a number, a citation, a code behaviour — and the output was treated as correct. The wrongness reached a human, a downstream system, or an external party before being caught.

**Trace emphasis at Step 4.** Prompt (what did the human ask); retrieved context (was the context giving the model wrong information, or was the model producing the error without context support); the model's chain of reasoning if the harness exposes it; the as-submitted artifact; the reviewer's path (did the reviewer have the means to catch this).

**Triage questions at Step 2.**

- Was the confabulation *context-faithful* (the model repeated what a stale or wrong context told it) or *context-unsupported* (the model produced a claim not supported by any retrieved source)?
- Did the artifact pass through a human review step, and if so, was the human able to catch it given what they saw?
- What was the blast radius — did the wrong content reach external parties?
- Is a commissioned eval in scope that should have caught the regression?

**Fault-chain emphasis at Step 6 (Chapter 3).** Typically weighted on Layers 1 (reviewer saw the wrong output and did not catch it), 2 (IC trusted the output), and 4 (retrieved context).

**Backfeed targets at Step 7.** New eval row (mod-103 Chapter 4); checklist row requiring explicit citation / source-verification for the artifact class (mod-103 Chapter 2); AGENTS.md section requiring the agent to surface its sources (mod-103 Chapter 3).

**OWASP / ATLAS mapping.** Maps to [OWASP LLM09 Overreliance](https://genai.owasp.org/llmrisk/llm09-overreliance/) and, where the hallucination has security-relevant content (e.g., fabricated package names, fabricated API behaviour), [LLM02 Insecure Output Handling](https://genai.owasp.org/llmrisk/llm02-insecure-output-handling/). MITRE ATLAS does not have a direct tactic for hallucination as such; the mapping is weak here and the OWASP frame is preferred.

**Public precedent patterns to read.** The AIID has catalogued incidents involving fabricated legal citations in filed briefs, incorrect medical or dosing information in consumer-facing chatbots, and fabricated factual assertions in AI-generated news summaries. Pick a case that is *adjacent to your team's domain* (data platform → data-quality-adjacent cases; eng team → code-adjacent cases) rather than a dramatic cross-domain case; adjacent reads adapt better in Exercise 03.

**What is often mistaken for this class.** A stale-context incident (the retrieved context was wrong; the model faithfully repeated it) is often mis-classified as hallucination. The distinction matters because the fix differs — stale-context is fixed by updating the retrieval or context-staleness detection (mod-106 Chapter 6), whereas confabulation-without-support is fixed by tightening the citation requirement and the review-time source check. The Chapter 1 example is a stale-context case under the hallucination class.

### Class 2 — Prompt-injection exploitation

**Definition.** Untrusted input entered the agent's context — through a RAG document, a tool call return, user-supplied text, a file the agent read — and successfully redirected the agent's behaviour away from the human's instructions. The agent did something the human did not ask for, because the untrusted content *asked it to*.

**Trace emphasis.** Where the untrusted content entered the context (which tool call, which document, which user input); the full prompt chain including the injected content; the agent's response to the injection; what the agent did in consequence; any security-relevant outputs (credentials, protected data, destructive actions).

**Triage questions.**

- What was the injection source? (Document retrieved via RAG; tool-call return; user-supplied text in a different context; file read; external web content.)
- Was the injection *direct* (the human saw the injected content and the agent was redirected in a single turn) or *indirect* (the content came in via a tool call or a RAG hit that the human did not see)?
- Did the agent take an action as a consequence, or did it only produce text output? If an action, what was authorised?
- Was any sensitive data exfiltrated, exposed, or at risk?
- Is this a security incident (data exposure, intrusion) that routes to SecOps (Chapter 5)?

**Fault-chain emphasis.** Typically weighted on Layer 3 (harness and policy — did the harness enforce output or action guardrails that should have stopped the hijacked behaviour) and Layer 4 (prompt and retrieved context — where the untrusted content came from). Layer 5 (model behaviour) is present but the model cannot be "fixed" in response; the fix is Layer 3.

**Backfeed targets.** Tool-authorisation policy amendment (mod-106 Chapter 6 — tighter scoping of what the agent is allowed to do when consuming untrusted content); input-sanitisation guardrail at the ingestion step; HITL checkpoint before any destructive action triggered after consumption of external content (mod-106 Chapter 4); AGENTS.md section on prompt-injection resistance.

**OWASP / ATLAS mapping.** Maps directly to [OWASP LLM01 Prompt Injection](https://genai.owasp.org/llmrisk/llm01-prompt-injection/) — the number-one entry in the OWASP LLM Top 10 for a reason. In ATLAS, maps to techniques under the [AML.T0051 LLM Prompt Injection](https://atlas.mitre.org/techniques/AML.T0051) family. Also potentially touches [OWASP LLM02 Insecure Output Handling](https://genai.owasp.org/llmrisk/llm02-insecure-output-handling/) when the injected instruction causes insecure output, and [LLM06 Sensitive Information Disclosure](https://genai.owasp.org/llmrisk/llm06-sensitive-information-disclosure/) when exfiltration is involved.

**Public precedent patterns to read.** AIID and OECD.AI both track prompt-injection cases; the broader security community (e.g., [Simon Willison's blog on prompt injection](https://simonwillison.net/tags/prompt-injection/)) has documented many classes of indirect injection via RAG and tool calls. For the team's rehearsal in Exercise 03, pick an indirect-injection case rather than a direct one — indirect injection is the harder class to prevent and is more likely to surface on an AI-augmented engineering team.

**SOC involvement trigger.** If the injection led to data exposure, credential compromise, or destructive action affecting production systems or external parties, the incident is a SOC-side incident and SecOps owns the response. The manager coordinates per Chapter 5 and does not try to run SOC-side containment or forensics with the team alone.

### Class 3 — Unauthorised tool use

**Definition.** The agent called a tool it was not authorised to call, or called an authorised tool with arguments outside the authorised scope, or took an action that the authorisation covered but the policy should not have permitted on reflection. The action caused harm or near-harm.

**Trace emphasis.** Tool authorisations configured at the time; tools actually called in the session, with arguments and returns; the sequence of agent reasoning that led to the call; whether a HITL checkpoint existed and whether it triggered; the destructive-action undo path if applicable.

**Triage questions.**

- What tool was called? Was it on the authorised list?
- If authorised, were the arguments within the scope the policy implied?
- Was a HITL checkpoint supposed to trigger before this action (mod-106 Chapter 4)?
- Is the action reversible? If not, what is the recovery path?
- Is this a security incident — did the action expose data or affect systems outside the authorised scope?

**Fault-chain emphasis.** Weighted entirely on Layer 3 (harness and policy — the tool-authorisation surface is the policy). Layer 2 (IC's prompt invoking the tool indirectly) and Layer 4 (context causing the agent to choose the tool) can be contributing causes but Layer 3 is where the fix lands.

**Backfeed targets.** Tool-authorisation policy amendment (mod-106 Chapter 6 — remove the authorisation, scope it tighter, move it to HITL-required). New HITL checkpoint for the action class (mod-106 Chapter 4). AGENTS.md or MCP server configuration update. Change-log entry on the mod-103 contract if the C1 decision that permitted this class of agent action needs revisiting.

**OWASP / ATLAS mapping.** Maps to [OWASP LLM08 Excessive Agency](https://genai.owasp.org/llmrisk/llm08-excessive-agency/) directly — the risk entry specifically names this failure mode. Also potentially [LLM02 Insecure Output Handling](https://genai.owasp.org/llmrisk/llm02-insecure-output-handling/) when the tool call was conditioned on model output that was not sanitised.

**Public precedent patterns to read.** Agent-system incidents involving file-system writes outside the intended scope, API calls with unintended side effects, or cross-tenant actions in multi-tenant systems. The AIID and OECD.AI have fewer of these catalogued than hallucination cases (agent systems are newer and the reporting is sparser), but the pattern recurs in security advisories for MCP servers, agent harnesses, and plugin ecosystems; `ai-risk-engineer` typically has a reading list here.

**Relationship to Class 2.** Prompt injection often *enables* unauthorised tool use; the injection redirects the agent and the agent then calls a tool. In practice, many real incidents are Class 2 + Class 3 composed. The incident commander picks the primary class for the picker at Step 2; the post-mortem walks both at Step 6.

### Class 4 — Model regression

**Definition.** A previously-working behaviour silently stopped working. The most common cause is a vendor-side model-version change (the default model pointer was updated, the model was deprecated, the fine-tune was rotated); less common causes include a retrieval-pipeline change, a tool-API change, or an environmental drift.

**Trace emphasis.** The model version at the time of the regression (and the vendor's changelog or deprecation page for that model); the model version at the time the behaviour previously worked (if preserved in prior traces or eval runs); the eval baseline that was passing and is now failing (if commissioned); the prompt and context that produced different behaviour across versions.

**Triage questions.**

- What is the specific behaviour change? Can it be reproduced side-by-side?
- Did the vendor announce a model-version change on the dates in question (changelog, deprecation page, email notification)?
- Is a commissioned eval capturing the behaviour? If so, when did it start failing?
- Is the regression a *silent default rotation* (the vendor rotated a default pointer under us) or a *known upgrade path* (the team had agreed to migrate and did not)? The first is a vendor-governance issue; the second is a team-governance issue.
- Is the regression *behaviour* (output quality) or *performance* (latency, cost) or both?

**Fault-chain emphasis.** Weighted on Layer 5 (model behaviour) *and* on the vendor side of the accountability stack. Layer 5 is where the specific regression manifests; the vendor is in the chain because the version change is what triggered it.

**Backfeed targets.** Version-pinning amendment (mod-106 Chapter 6 — pin to a specific version rather than a rolling default). Commissioned eval for the behaviour that regressed (mod-103 Chapter 4 — a canary eval that would have caught it next time). Vendor-governance ticket (mod-111 — vendor-communication SLA, version-change notification SLA, model-deprecation policy). Routing-matrix amendment (mod-106 Chapter 2) if the regressed behaviour justifies a different routing for the affected workflow.

**OWASP / ATLAS mapping.** Does not map cleanly to a single OWASP LLM Top 10 entry — the OWASP frame is security-focused and regression is a reliability concern. Touches [LLM03 Training Data Poisoning](https://genai.owasp.org/llmrisk/llm03-training-data-poisoning/) and [LLM05 Supply Chain Vulnerabilities](https://genai.owasp.org/llmrisk/llm05-supply-chain-vulnerabilities/) when the regression cause is upstream (training data or supply chain). ATLAS has a model-update family of tactics worth reading.

**Public precedent patterns.** The AIID catalogues several cases of silent model behaviour shifts affecting downstream users; the OECD.AI monitor is slower-moving on this class but has policy-relevant discussion. The team's own eval dashboard is often a better precedent base than the public databases for this class, because the regression surface is specific to the team's prompts and workflows.

**Vendor engagement.** Unlike the other three classes, Class 4 incidents almost always route to a vendor conversation. The mod-111 vendor-governance framework names the escalation ladder. Chapter 5 of this module names the manager-level handoff: the manager flags the trigger; the vendor-management path (which may be the manager themselves, may be procurement, may be `ai-enablement-lead` at L45) owns the vendor conversation.

### Composed classes: the common case

Many real incidents compose two or three of the four classes. Examples:

- **Class 2 + Class 3.** Indirect prompt injection via a RAG document causes the agent to call an unauthorised tool.
- **Class 4 + Class 1.** A silent model upgrade causes the model to hallucinate on a class of prompts it previously handled correctly. The eval regression caught the change (Class 4 signal); the specific wrong output reaching a human is the Class 1 harm.
- **Class 1 + Class 3.** The model hallucinated a tool argument; the agent called the tool with the hallucinated argument.

The triage at Step 2 picks the *primary* class for the picker. The post-mortem at Step 6 walks all the classes present, not only the primary. The runbook's incident-class picker is a one-of-four field; an "additional classes" field captures the composition.

### The triage one-pager

The incident commander uses a one-page triage matrix in the first 30 minutes. Suggested shape:

| Class | Primary trace priority | Primary triage question | Primary routing trigger |
|---|---|---|---|
| **1. Hallucination-driven harm** | Prompt + retrieved context + as-submitted artifact | Context-faithful or context-unsupported? Reach? | Commission eval; tighten checklist |
| **2. Prompt-injection exploitation** | Prompt chain + injection source + tool-call trace | Direct or indirect? Data exposure? | SecOps if security-visible; else risk engineer |
| **3. Unauthorised tool use** | Tool authorisation config + session tool-call log | Authorised scope breach? Reversible? | Tool-authorisation amendment; HITL add |
| **4. Model regression** | Model version + eval baseline + side-by-side reproduction | Silent rotation or known upgrade? | Vendor-governance (mod-111); version pin |

The one-pager fits on an A4 pinned next to the runbook. It is the artifact that stops the incident commander from going blank in minute 10 when they are trying to remember which class is which.

### Reading the AIID and OECD.AI as precedent

A short practice. For a team that has never had an AI incident:

- Monthly, one person on the team (rotated, often the on-call engineer) picks one case from the [AIID](https://incidentdatabase.ai/) adjacent to the team's domain. They spend 20 minutes. They produce a two-paragraph note: what happened, which of the four classes it is, what the team's runbook would have done.
- Quarterly, the team picks one case from the [OECD.AI Incidents Monitor](https://oecd.ai/en/incidents) with policy or regulator implications. They spend 30 minutes. They produce a one-paragraph note on what the policy implications would have meant for their team.

The practice is low-effort and builds the pattern recognition that is otherwise only built by having incidents. Exercise 03 is the formal version.

The reading discipline is to resist pattern-matching superficially. A cross-domain dramatic case ("the AI did X at Y company and X does not sound like anything we do") is not useful; the lesson from such a case is at a level of abstraction that does not help the team's runbook. A quiet, adjacent, domain-matched case is more useful — "a data platform at a mid-sized company shipped a wrong number via an AI-authored pipeline change" is the case that calibrates the runbook.

### Composition with existing security taxonomies

The four classes are team-scope operational categories. They compose with, rather than replace, the security-oriented taxonomies the engineered-risk peer uses:

- **[OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)** (2025 revision — `genai.owasp.org`). The ten entries map as noted above. The OWASP frame is security-oriented; mod-109's four classes include reliability concerns (Class 1 and 4) that OWASP addresses lightly.
- **[MITRE ATLAS](https://atlas.mitre.org/)** (Adversarial Threat Landscape for AI Systems). ATLAS is a tactic/technique matrix (ATT&CK-style) focused on adversarial threats. Prompt injection (Class 2) maps cleanly; the other three classes are less well-covered in ATLAS and route into other frameworks.
- **[NIST AI RMF 1.0](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf)** — the MAP and MANAGE functions discuss incident categories at a higher abstraction level; the four classes slot inside MANAGE 2 and MANAGE 4.
- **[ISO/IEC 42001:2023](https://www.iso.org/standard/81230.html)** — AI management system standard with an incident-handling clause; the four classes compose under the ISO clause.

The engineered-risk peer typically works in OWASP + ATLAS + NIST (and possibly ISO). When the manager routes a Chapter 2 incident to the risk engineer per Chapter 5, the mapping above is the shared vocabulary. Exercise 04 co-authors the routing contract and the shared vocabulary.

## Example: four shaped triage cases

Four one-paragraph illustrative examples, one per class. Carries forward where sensible from the Chapter 2 running example. Shaped, not verified.

**Class 1 — Hallucination.** Internal wiki search is backed by a RAG agent. A customer-support engineer asks the agent about a partner's SLA. The agent returns a confidently-stated SLA that does not exist (confabulated — the retrieved context did not contain SLA language for this partner). The engineer uses the SLA in a customer-communication draft; the draft is sent before a human review. Severity Sev-2 (external reach to one customer; reversible via a correction email). Triage class: hallucination-driven harm, context-unsupported. Trace: the prompt, the retrieved context (which had no SLA content for this partner), the model's response, the engineer's path. Action items: tighten the agent to require cited sources; eval row that catches confabulation on SLA-shaped questions; HITL checkpoint before any customer-communication draft that cites an SLA.

**Class 2 — Prompt injection.** A developer-productivity agent ingests README files and other docs across the codebase. One of the dependencies' README files contains instructions-to-model that direct the agent to run a specific shell command "to verify installation." The agent, which has shell tool authorisation, runs the command. The command is benign (a `echo`), but a near-miss — the pattern could have been destructive. Severity Sev-3 (potential-harm learning case; no external reach; caught by the engineer watching the session). Triage class: prompt-injection exploitation, indirect (via README). Trace: the README source with injected content; the agent's response to the instruction; the tool call. Action items: input-sanitisation guardrail on README ingestion; HITL checkpoint before any shell tool call that originated from external content; `ai-risk-engineer` engaged for a broader audit of injection surfaces in the team's agent systems.

**Class 3 — Unauthorised tool use.** A data-platform agent has authorised read access to a production database for query-generation workflows. Through a sequence of agent reasoning on an ambiguous prompt, the agent elected to call the database with a query that scanned a sensitive table outside the intended scope. The query succeeded; no data was exfiltrated, but the audit log flagged the access. Severity Sev-3 (internal only; no exfiltration; detected via audit log). Triage class: unauthorised tool use, within-scope-authorisation-breach. Trace: the prompt; the tool authorisation config; the query sequence; the audit log entry. Action items: tighter scoping on the database tool (schema-level allow-list rather than database-level); HITL checkpoint for database queries that reference sensitive tables; SecOps notified for awareness (not primary owner).

**Class 4 — Model regression.** The team's code-review agent has been using `anthropic/claude-sonnet-4-5` for six months. Over a three-day window the eval dashboard for a specific reviewer-agreement eval drops from 0.87 to 0.71. The vendor's changelog shows the default pointer for `claude-sonnet-4-5` was rotated two days earlier (hypothetical shape — verify against vendor's actual changelog before quoting). Side-by-side reproduction confirms the behaviour change on a held-out set. Severity Sev-2 (no harm shipped; eval caught it before human-visible impact). Triage class: model regression, silent default rotation. Action items: pin to the specific prior version via the vendor's version-pinning API (if available); canary eval added for the next regression; vendor-governance ticket (mod-111) escalates the notification-SLA gap. The engineered-risk peer reproduces and documents the behaviour delta.

## Summary

- Four AI-specific incident classes: **hallucination-driven harm, prompt-injection exploitation, unauthorised tool use, model regression**. The incident commander picks one as primary at Step 2; the post-mortem walks all present at Step 6.
- **Each class has its own triage questions, trace emphasis, fault-chain focus, and backfeed targets.** The one-page triage matrix fits on an A4 next to the runbook.
- **Composition is the common case.** Class 2 + Class 3, Class 4 + Class 1, Class 1 + Class 3 are all common composed shapes.
- **The four classes compose with security taxonomies**, not replace them: [OWASP LLM Top 10](https://genai.owasp.org/) (LLM01 maps to Class 2; LLM08 maps to Class 3; LLM09 maps to Class 1; LLM03/05 touch Class 4), [MITRE ATLAS](https://atlas.mitre.org/), [NIST AI RMF](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf) MANAGE, [ISO/IEC 42001](https://www.iso.org/standard/81230.html).
- **Public precedent bases:** the [AI Incident Database](https://incidentdatabase.ai/) (Responsible AI Collaborative) with over a thousand catalogued incidents; the [OECD.AI AI Incidents Monitor](https://oecd.ai/en/incidents) with policy-level scope.
- **Reading discipline:** monthly adjacent-case read from AIID (20 min); quarterly OECD.AI policy-adjacent read (30 min); resist cross-domain dramatic cases; prefer quiet domain-matched ones.
- **Class 2 can route to SecOps** when the incident involves data exposure or intrusion; **Class 4 almost always routes to vendor governance** (mod-111); Classes 1 and 3 typically land in the mod-103 + mod-106 backfeed.
- **The runbook includes an incident-class picker** (one-of-four plus an additional-classes field) at Step 2; [Exercise 01](exercises/exercise-01-team-incident-runbook-authoring.md) produces it, [Exercise 03](exercises/exercise-03-ai-incident-database-case-read-and-adapt.md) rehearses it against a published case.
- **Composes with** [`mod-103`](../mod-103-review-standards-and-eval-commissioning/) (standards, eval, standards-as-code — backfeed destination for Classes 1 and 4), [`mod-106`](../mod-106-workflow-redesign-and-agent-delegation/) (routing, HITL, tool-authorisation — backfeed destination for Classes 2 and 3), [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/) (vendor governance for Class 4), and [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) ([OWASP](https://genai.owasp.org/), [ATLAS](https://atlas.mitre.org/), [NIST AI RMF](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf), [ISO/IEC 42001](https://www.iso.org/standard/81230.html) — the governance stack the four classes compose into).
