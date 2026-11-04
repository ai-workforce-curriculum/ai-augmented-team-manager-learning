# Chapter 4 — The Deferral Rubric: Down, Sideways, and Up

> *Half of this job is knowing when a question is not yours to answer.*

## Motivation

Chapter 1 named the ladder. Chapter 3 named the contract. This chapter gives you the **rubric** — a working decision procedure for every incoming question that might belong to a neighbour instead of you.

A level-40 team manager typically gets, in a week, between twenty and fifty incoming asks that are shaped like AI-related manager questions. Many are straightforwardly yours. Many are not — they belong to the governance analyst, the risk engineer, the product manager, the enablement lead, the engineering manager, the head of governance, legal, HR, or security operations. Taking on work that belongs to a neighbour is the single most common cause of manager burnout in AI-augmented teams this cycle. Letting work drift onto the wrong neighbour is how a team's AI posture becomes incoherent.

The rubric is cheap. Three questions, answered in sixty seconds, route 90% of asks correctly. The remaining 10% are where you earn your pay.

## Core concepts

### The three questions

Ask, in order:

1. **Is this at team scope, or beyond it?** If beyond (multi-team, org-wide, board-level, regulator-facing), route **up**.
2. **Is this operational legwork I should be consuming, not producing?** If yes (intake, inventory, crosswalks, first-draft impact assessment), route **down**.
3. **Is this a peer discipline's craft, where I commission but do not re-build?** If yes (engineered risk eval, red-team rig, product-ROI framing, infra delivery), route **sideways**.

If "no" to all three, it is yours.

### Route **down**: operational governance legwork

Below you on the AI-governance ladder sits `ai-governance-analyst` at level 15 (AI Governance family). That role owns the operational legwork this role **consumes** at team scope. Specifically, route **down** to the governance analyst when the question is:

- **Intake and triage.** "Is this new tool / use case / vendor approved?" The analyst runs the intake form, routes to risk and legal, logs the use case in the inventory.
- **Model / AI-system inventory.** "What do we actually have in prod?" The analyst maintains the inventory; you contribute entries for your team.
- **Framework crosswalks.** "How does our control X map to NIST AI RMF GOVERN 1.1 / ISO/IEC 42001 clause Y / EU AI Act Article Z?" The analyst does the crosswalk; `mod-110` teaches you to read the output.
- **First-draft impact assessment.** The analyst drafts; you review and sign at team scope; a higher-level role (senior architect or head of governance) signs at program level.
- **Jurisdictional regulatory tracking.** The analyst watches for new guidance; you act on it when it changes your team.
- **Model / system / dataset card authoring at analyst tier.** The analyst drafts the cards; you confirm the team-scope entries are correct.

What you own, conversely, is the **team-scope translation** of that work: "given the analyst's output, what does my team do differently this quarter?" That is `mod-110`.

Below you on the IC ladder sit `ai-assisted-software-engineer` (level 25) and `ai-augmented-analyst` (level 20). Route **down** to them when the question is:

- **IC-mechanics of AI tool use.** "What is the right Cursor rules syntax to constrain this behaviour?" You stay fluent enough to review (Chapter 5); you do not re-teach it.
- **IC-mechanics of agent authoring.** "How do I wire an MCP server for this tool?" The IC curriculum covers the mechanics; you commission and review the design (`mod-106`).
- **Day-to-day prompt craft on a specific artifact.** Mentor by example, but do not write the IC's prompts.

### Route **sideways**: peer disciplines you commission from

Three peers matter most:

**`ai-risk-engineer`** (peer, level 25, AI Governance family). Route sideways when the question is:

- Engineered **risk evaluation** of a specific AI feature or agent — adversarial tests, jailbreak probes, dangerous-capability checks.
- Engineered **guardrails** — input filters, output filters, tool-authorisation policies at the implementation layer.
- **Red-team** engagements against your team's AI artifacts.

You **commission** this work with a brief, consume the evidence, and act on findings at team scope. You do not build the harness. `mod-103` and `mod-109` are where you practice the commissioning.

**`ai-augmented-product-manager`** (peer, level 30, AI Workforce family). Route sideways when the question is:

- **AI-feature product scope** — what the AI feature does, for which customer, at what price.
- **Product-level ROI framing** — revenue, retention, NPS, unit economics.
- **Customer-facing explanation** of model behaviour.

You both read DX Core 4 / SPACE / DORA; the PM frames product ROI, you frame team ROI (`mod-104`). You share the dashboard; you do not share the ownership.

**`ai-infra-team-lead`** (peer / lower-adjacent, level 35, Infra family). Route sideways when the question is:

- Infra-specific delivery scope (platform availability, capacity, inference cost at infra tier).
- Infra-specific team practice.

Your track is discipline-agnostic; infra-specific depth lives there.

### Route **up**: scope beyond one team

Three higher-level roles matter most:

**`ai-enablement-lead`** (level 45, AI Workforce family). Route up when the question is:

- **Multi-team coordination** — rolling the same program to three teams at once.
- **Org-wide enablement** — company-wide bootcamps, communities of practice bigger than your team, cross-department fluency bars.
- **Procurement at scale** — company-wide tool contracts, cross-team cost pooling.
- **Pilot graduation** — a team-scope pilot of yours is ready to become a company-wide product. You hand off the pilot package.

**`ai-engineering-manager`** (level 50). Route up when the question is:

- **Manager-of-managers scope** — multiple engineering teams reporting into one manager; portfolio planning; cross-team architecture decisions.
- **Engineering-specific** second-line manager work.

**`senior-ai-governance-architect`** (level 50) / **`head-of-ai-governance`** (level 60) / **`chief-ai-officer`** (level 70). Route up when the question is:

- **Control-library architecture** (L50), **policy taxonomy**, **cross-jurisdiction reconciliation**.
- **Governance program leadership**, **board reporting**, **regulator engagement** (L60).
- **Executive scope** (L70) — enterprise AI strategy, external communication.

### Route **out**: not in the family at all

Three destinations are always out of scope for this role:

- **Legal counsel.** You do not deliver legal opinion. If a question needs a legal opinion — regulatory interpretation, contract language, employment-law application to a specific case — route to counsel and act on what they tell you.
- **HR / employee-relations partners.** Formal employment actions (PIP, termination, compensation calibration, protected-class complaints) route to HR. You own the manager-side framing (`mod-108`); HR owns the formal process.
- **Security operations / DFIR.** SOC-side incident handling (threat actor attribution, forensic investigation, law enforcement coordination) routes to SecOps. You feed AI-specific signal to them (`mod-109`); you do not run the SOC-side chain.

### The ambiguous 10%

Some asks sit on the boundary. A short heuristic:

- **If the question is "should we use this tool for this work?"** — team-scope says yes/no with the analyst's intake behind it; cross-team or company-wide says routes to `ai-enablement-lead`.
- **If the question is "why did the AI produce X?"** — if it's about engineering the guardrail, route to `ai-risk-engineer`; if it's about who is on the hook for what shipped, it is yours (`mod-109`).
- **If the question is "how do we talk to the board about AI?"** — above your altitude; route to `head-of-ai-governance` or executive scope.
- **If the question is "how do we structure OKRs under AI leverage?"** — team-scope is yours (`mod-104`, `mod-108`); multi-team is `ai-enablement-lead`.
- **If the question is "we need a lawyer to look at this"** — do not pretend to be the lawyer. Route.

When in doubt, write the ask down with a sentence explaining why it's ambiguous, and route both to the likely neighbour and to your own manager. You will be right on the route 90% of the time within six months of running the rubric.

## Example: five Monday-morning asks, routed

Five asks arrive before your first coffee. Run the rubric.

1. "A new eng VP wants to know how our team measures AI ROI." — **Yours.** `mod-104`.
2. "Platform is asking for your team's Cursor rules file to canonicalise org-wide." — **Up.** `ai-enablement-lead`; hand off the rules file with a note on what's generalisable.
3. "Can we use Claude Code for a new customer-data workflow?" — **Down first** (governance analyst runs intake), **then yours** (team-scope decision when the intake comes back), **sideways** (`ai-risk-engineer` to red-team if intake flags).
4. "Our product counterpart wants a joint ROI review of the AI feature." — **Sideways.** PM owns product ROI; you own team ROI. Attend the review; do not run it.
5. "HR says one of my ICs filed a complaint that another IC is using AI to over-ship and squeeze them out." — **Out** (HR owns the formal process), **and yours** (manager-side framing — review standard, workload, pairing). Partner with HR; do not front-run.

All five are routed in under ninety seconds. None are wrong.

## Summary

- Three routing questions: beyond team scope? operational legwork? peer craft? → route **up / down / sideways** respectively.
- Route **down** to `ai-governance-analyst` (L15) for operational governance legwork; to `ai-assisted-software-engineer` (L25) and `ai-augmented-analyst` (L20) for IC-mechanics.
- Route **sideways** to `ai-risk-engineer` (L25) for engineered risk/guardrail/red-team; to `ai-augmented-product-manager` (L30) for product ROI; to `ai-infra-team-lead` (L35) for infra delivery.
- Route **up** to `ai-enablement-lead` (L45) for org-wide and multi-team; to `ai-engineering-manager` (L50) for manager-of-managers; to `senior-ai-governance-architect` (L50), `head-of-ai-governance` (L60), `chief-ai-officer` (L70) for governance architecture / program / executive scope.
- Route **out** to legal (opinion), HR (formal employment action), SecOps (SOC-side incident).
- Exercise 04 asks you to encode this as a one-page rubric and test it against ten real asks from your inbox.
