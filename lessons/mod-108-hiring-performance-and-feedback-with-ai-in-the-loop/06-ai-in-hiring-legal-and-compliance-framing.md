# Chapter 6 — AI-in-Hiring: Legal and Compliance Framing

> *You do not need to become a lawyer. You do need to know enough to set team practice that does not expose the organisation, to recognise the triggers that require legal review, and to route the hard questions to counsel through HR. This chapter is the manager's working knowledge of the three regimes in effect in 2026 — US EEOC guidance, NYC Local Law 144, EU AI Act Article 6 + Annex III — and the handoff to HR and legal counsel for everything beyond team practice.*

## Motivation

The compliance regime around AI in employment decisions is no longer theoretical in 2026. Three authoritative frameworks apply directly to the manager's work:

- The [US EEOC guidance on *The Americans with Disabilities Act and the Use of Software, Algorithms, and Artificial Intelligence to Assess Job Applicants and Employees*](https://www.eeoc.gov/laws/guidance/americans-disabilities-act-and-use-software-algorithms-and-artificial-intelligence) (May 2022) and the *Technical Assistance Document: Select Issues: Assessing Adverse Impact in Software, Algorithms, and Artificial Intelligence Used in Employment Selection Procedures Under Title VII* (May 2023) — together the EEOC's current position on how existing anti-discrimination law applies to AI-assisted hiring decisions.
- [NYC Local Law 144 (the Automated Employment Decision Tools law)](https://www.nyc.gov/site/dca/about/automated-employment-decision-tools.page), effective 2023-07-05 — requires bias audits for automated employment decision tools (AEDTs) used to screen candidates or employees for employment or promotion in New York City, plus candidate notification and audit publication.
- [EU AI Act (Regulation (EU) 2024/1689)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj), Article 6 and Annex III — classifies AI systems used for recruitment, selection, promotion, and termination as *high-risk*. High-risk-system obligations (risk management, data governance, logging, human oversight, transparency, accuracy, robustness, cybersecurity) apply on a phased timeline through 2026–2027.

The chapter covers what the manager has to understand to set team practice. Legal opinion — on specific vendors, specific employment decisions, specific candidate complaints, specific jurisdictional questions — is counsel's work through HR, not the manager's. The chapter is explicit on the line.

## Core concepts

### The three load-bearing questions at team scope

Before reading the regimes in detail, the manager's working practice reduces to three questions, asked for every AI tool or process the team uses in hiring or performance:

1. **Does the tool make, substantially assist, or substantially influence an employment decision?** The verbs matter. A tool that *summarises a transcript for a human reviewer* is different from a tool that *scores a candidate* or that *ranks candidates for the human to review in order*. The compliance footprint is very different; the triggers in all three regimes hinge on this verb.
2. **What demographic data does the tool consume, produce, or infer?** Even a tool that does not take demographic data as input can produce adverse-impact outcomes if its features correlate with protected classes. The EEOC's 2023 TA document is explicit about this.
3. **In which jurisdictions does the hiring happen, and where do the candidates live?** NYC Local Law 144 applies to jobs performed in NYC or where the candidate is located in NYC. EU AI Act applies to AI systems placed on the EU market or whose outputs are used in the EU. US EEOC guidance applies to US employment decisions broadly. A hiring loop that spans multiple jurisdictions picks up multiple obligations.

The answers go into a short team-scope register the manager maintains (Exercise 05 produces this). Counsel does not need to see the register for routine tools; the register is the artifact that makes the routing decision (routine vs. counsel) explicit.

### The EEOC frame: Title VII adverse impact applies to AI

The EEOC's 2023 Technical Assistance makes three load-bearing points for the manager:

- **Existing anti-discrimination law applies.** Title VII of the Civil Rights Act of 1964 prohibits disparate impact on protected classes (race, colour, religion, sex, national origin). The 2023 guidance says the *four-fifths rule* (if the selection rate for a protected group is less than 4/5 or 80% of the rate for the group with the highest selection rate, this is prima facie evidence of adverse impact) applies to AI-assisted employment decisions the same way it applies to any other selection procedure.
- **The employer is responsible.** When a vendor provides the AI tool, the EEOC's position is that the employer using the tool remains responsible for its outcomes. "The vendor's audit said it was unbiased" is not a defence.
- **Documentation matters.** The guidance expects employers to understand the tool, to document its use, and to be able to answer questions about its selection outcomes. The specific documentation requirements come from the broader Title VII and *Uniform Guidelines on Employee Selection Procedures* record-keeping obligations.

The 2022 guidance on the *Americans with Disabilities Act (ADA)* and AI adds a specific concern: AI systems that assess traits like personality, cognitive ability, or communication style can disadvantage candidates with disabilities. The guidance names specific concerns — e.g., video analysis that scores facial expressions or speech patterns is especially exposed.

For the manager, the EEOC frame produces three practice bullets:

- **Monitor selection outcomes by protected class across the loop**, if the organisation's scale supports it. Small teams may not have the statistical power to compute adverse impact meaningfully, but documenting outcomes makes trends visible over time.
- **Be prepared to explain any AI tool the loop uses**, in plain language, to a candidate or to an investigator. If the manager cannot explain how the tool scores a candidate, the tool is probably not appropriate for this loop; alternative routing (human-only screen) is sometimes the right answer.
- **Provide reasonable accommodations for candidates with disabilities**, as the ADA requires. If the AI tool is a barrier for a candidate, the manager coordinates with HR on the accommodation.

### The NYC Local Law 144 frame: bias audits and candidate notice

Local Law 144 applies to **automated employment decision tools (AEDTs)** used to **substantially assist or replace discretionary decision-making** in **hiring or promotion** when the candidate is a resident of or seeking employment in NYC. Three operational requirements:

- **Annual bias audit.** The AEDT must have been audited within the past year by an independent auditor against statistical standards specified in the rule. The audit's summary must be published on the employer's or the vendor's publicly accessible website and must include the selection rate for each protected class and the impact ratio.
- **Candidate notice.** Candidates must be notified at least ten business days before the AEDT is used, must be informed of the job qualifications and characteristics the AEDT assesses, and must be given a way to request an alternative selection process or accommodation. The notice can be a specific job-posting disclosure or a direct communication; the law is agnostic on channel but specific on content.
- **Data source and type disclosure.** On request, the employer must disclose the source and type of data the AEDT uses and its data retention policy.

The scope of "AEDT" and "substantially assist" has been narrowed by the NYC Department of Consumer and Worker Protection's final rules (2023) to tools that use machine learning, statistical modelling, data analytics, or AI to issue a simplified output (a score, a classification, a recommendation) used to make or substantially assist a hiring or promotion decision. A tool that summarises candidate materials for a human to then score independently is typically outside scope; a tool that ranks candidates by predicted job fit is typically inside scope.

The specific scope boundaries are legal determinations for counsel. The manager's job is to identify any tool that might be inside scope and route it for the compliance review.

### The EU AI Act frame: high-risk classification and obligations

The EU AI Act (Regulation (EU) 2024/1689) entered into force 2024-08-01, with phased application dates. The parts of the Act relevant to hiring:

- **Article 6 and Annex III.** AI systems intended to be used in recruitment or selection of natural persons, in particular for placing targeted job advertisements, screening or filtering applications, and evaluating candidates, are classified as **high-risk**. AI systems used to make decisions affecting terms of work-related relationships (promotion, termination, task allocation, performance evaluation) are also high-risk.
- **High-risk-system obligations (Articles 8–15, and 17 on the quality management system).** Providers and deployers of high-risk AI must comply with risk management, data governance, technical documentation, record-keeping (logging), transparency, human oversight, accuracy / robustness / cybersecurity, and quality-management-system requirements. Deployers specifically must ensure the system is used in accordance with its instructions, assign human oversight, keep logs, monitor the system in operation, and inform affected persons where required.
- **Article 4 — AI literacy.** Providers and deployers must take measures to ensure a sufficient level of AI literacy of their staff and other persons dealing with the operation and use of AI systems on their behalf. This article is in effect from 2025-02-02; the specifics are being clarified through [EU AI Office guidance](https://digital-strategy.ec.europa.eu/en/policies/ai-act).
- **Article 50 — transparency.** Providers of certain AI systems, including those generating synthetic content, must ensure users / affected persons are informed in accordance with the article.

The application dates to be aware of in 2026:

- **2025-02-02:** prohibited AI practices (Article 5) and AI literacy (Article 4) in effect.
- **2025-08-02:** general-purpose AI model obligations (Chapter V) and governance (Chapter VII) in effect.
- **2026-08-02:** high-risk AI system obligations for most Annex III systems (including hiring) in effect.
- **2027-08-02:** high-risk AI system obligations for systems that are components of products covered by other EU legislation listed in Annex I.

For hiring specifically, the 2026-08-02 date is the operative one for Annex III applications. The manager and HR partner need to be able to show, by that date, that any high-risk AI used in the team's hiring loop has the high-risk-system obligations met — typically via the vendor's conformity assessment (the vendor's responsibility) plus the deployer's own documented use (the organisation's responsibility).

Scope of application: the EU AI Act applies to providers placing AI systems on the EU market and to deployers using AI systems in the EU, as well as to providers and deployers outside the EU where the output is used in the EU. A team hiring remote candidates in EU member states, or a team based in the EU, is in scope.

### What the team-practice artifact looks like

Exercise 05 produces the team-scope artifact. The structure:

- **Section 1 — AI inventory in the hiring and performance pipeline.** List every tool with AI components the team uses in hiring (resume parsing, assessment platforms, interview scheduling, video analysis, interview-notes assistants, structured-interview scoring tools) and in performance management (review-note assistants, calibration tooling, OKR tools with AI-generated content). For each: vendor, what it does, what it outputs, which decision it influences.
- **Section 2 — Trigger assessment per tool.** For each tool, answer the three questions from the opening of this chapter. Produces a classification: "no AEDT trigger," "may trigger NYC LL 144 — route to HR/legal," "high-risk under EU AI Act Annex III — vendor conformity + deployer obligations," "ADA accommodation exposure — provide alternative."
- **Section 3 — Documentation state.** For each in-scope tool, the state of: bias audit (NYC LL 144), candidate notice (NYC LL 144), vendor conformity assessment (EU AI Act), deployer logs (EU AI Act), human oversight assignment (EU AI Act), AI literacy for the operating staff (EU AI Act Article 4).
- **Section 4 — Routing.** What stays at team scope (team practice bullets; the manager handles). What routes to HR (bias-audit review, candidate-notice drafting, accommodations, PIP compliance). What routes to legal counsel through HR (jurisdictional scope questions, conformity assessments, specific candidate complaints, vendor contract review).
- **Section 5 — Review cadence.** The artifact is re-run annually at minimum, and whenever a new tool is added or an existing tool materially changes. New hires on the team are inducted to the artifact as part of mod-105 Day 0 / 30.

The checklist does not replace legal counsel. It is the organising artifact that makes the routing decisions explicit, so the manager knows which questions belong to them and which belong upstream.

### What the manager does vs. what HR does vs. what legal does

| Activity | Manager | HR | Legal counsel |
|---|---|---|---|
| Inventory AI tools in the hiring pipeline | Owns | Partners | — |
| Decide a tool is in-scope under LL 144 / EU AI Act | Flags | Partners with manager; routes to legal | Determines |
| Draft bias-audit summary language | — | Owns (often with vendor) | Reviews |
| Write candidate notice for LL 144 | Reviews | Owns | Reviews / approves |
| Provide reasonable accommodation under ADA | Coordinates | Owns | — |
| Assign human oversight under EU AI Act | Owns on the team side | Approves the role | — |
| AI literacy training for staff using AI in hiring | Composes with [`mod-105`](../mod-105-team-ai-enablement-programs/) | Partners | — |
| Respond to candidate complaint | Flags and documents | Owns | Advises / responds if needed |
| Respond to regulator inquiry | — | Coordinates | Owns |
| Vendor contract with data-handling clauses | Flags requirements | Partners | Owns |

The table is not exhaustive and is organisation-dependent. The pattern: the manager owns inventory, flags triggers, and operates the team-scope practice; HR owns the formal mechanics; legal counsel owns opinion and regulator response.

### What the manager must *not* do

- **Do not approve a new AI hiring tool without routing it for compliance review.** The tool may be inside scope. The approval is HR / legal through the review; the manager's job is to flag.
- **Do not promise a candidate that the loop is "unbiased."** The claim is unverifiable, specifically contested by the EEOC guidance on vendor claims, and sets up a specific exposure if a selection outcome produces a disparate impact. Use accurate language: *"we use a structured interview process; here is what the stages assess."*
- **Do not run bias analyses yourself on protected-class data.** The data belongs to HR and, in many organisations, is restricted from managers for specific legal reasons. If the manager has access and is tempted to run adverse-impact numbers, route to HR instead.
- **Do not interpret the law.** The manager's compliance practice is behavioural (what to do, what to flag, when to route). The interpretation — "does our use fall under LL 144's AEDT definition? is this specific feature a high-risk use under Annex III?" — is counsel's. Managers who interpret the law into their own practice tend to be either over- or under-inclusive, both of which produce exposure.
- **Do not cite this chapter as legal opinion.** The chapter cites the authoritative references; the regulatory text and official guidance are the sources. Use the chapter to frame team practice; use counsel to answer the question *"is this actually compliant?"*

### How this composes with mod-110

[`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) covers AI governance and policy at team scope more generally, including [NIST AI RMF 1.0](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf) GOVERN → team practice, [ISO/IEC 42001](https://www.iso.org/standard/81230.html), and the EU AI Act Article 4 (AI literacy) frame. Chapter 6 of mod-108 is specifically the hiring and performance-management slice of that broader governance work. If your organisation has a company-wide AI governance programme and a governance analyst / enablement lead at scale, the team-scope hiring compliance checklist in Exercise 05 feeds into that broader programme rather than running independently.

### Common failure modes

- **Treating the compliance work as paperwork rather than practice.** The compliance regime is about actual behaviour, not about documentation theatre. Bias-audit publication without actually reading the audit is a failure mode LL 144 does not prevent; the manager has to actually engage with the audit's findings.
- **Letting the vendor's audit be the full answer.** The deployer's obligations exist independently of the vendor's audit under both LL 144 and EU AI Act. The vendor-side audit is a necessary but not sufficient part of compliance.
- **Not knowing which jurisdictions candidates live in.** A hiring loop that is "remote-friendly" without specific jurisdictional scoping tends to pick up compliance obligations without the team noticing. The sourcing partner / recruiter and HR need to be aligned on which jurisdictions are in play.
- **Treating "structured interview" as a shield against adverse-impact scrutiny.** Structured interviews reduce adverse-impact risk relative to unstructured interviews (this is the Google re:Work point). They do not eliminate adverse-impact risk or exempt the team from the Title VII obligations.
- **Deferring the AI literacy obligation.** EU AI Act Article 4 is in effect from 2025-02-02. Teams hiring EU candidates need staff AI literacy appropriate to the role and the system — composable with the [`mod-105`](../mod-105-team-ai-enablement-programs/) enablement work.

## Example: a compliance-checklist route for a resume-screening tool

Composite example; calibration, not legal advice.

A manager is evaluating a new resume-screening SaaS tool that, per the vendor's product page, "uses AI to rank candidate resumes against the job description."

Running the three load-bearing questions:

1. **Does it substantially assist an employment decision?** Yes. The tool ranks candidates; the manager typically reviews top-ranked candidates first and may not review candidates below a threshold.
2. **What demographic data does it consume or produce?** Vendor-stated: name and work history are consumed. The tool does not explicitly consume gender / race / etc. Features that correlate with protected classes (name patterns, graduation year as a proxy for age, gaps in employment history) are nevertheless consumed. The EEOC's 2023 TA is directly relevant.
3. **Jurisdictions?** The team hires remote globally, including NYC and several EU member states.

The classification:

- **NYC LL 144:** likely in scope as an AEDT. The tool ranks candidates to substantially assist a hiring decision. Requires bias audit within past year, candidate notice, published audit summary.
- **EU AI Act Annex III:** in scope. Resume screening falls under "screening or filtering applications."
- **EEOC / Title VII:** in scope; need to monitor selection outcomes and be able to explain the tool.

The routing:

- **Manager → HR:** flag the tool, share the three-question assessment, ask HR to coordinate the compliance review.
- **HR → Legal counsel:** route the LL 144 scope determination, the EU AI Act high-risk-system compliance review (including vendor's conformity assessment documentation), and any contract review.
- **HR → Vendor:** request the bias audit, data-handling documentation, conformity assessment, instructions-for-use documentation.
- **Manager → Team:** pause the tool's use until the review is complete. Fall back to human-only resume screening in the interim.

Six weeks later, the review concludes: vendor's bias audit is current and published, data handling is acceptable, conformity assessment for EU AI Act is in progress and the vendor commits to a timeline, candidate notice language is drafted jointly. HR approves use in NYC and non-EU jurisdictions with the notice in place. EU use is deferred until the conformity assessment is complete.

The manager's documented team-scope practice names the tool, the compliance state, the candidate notice process, the human oversight assignment (the manager personally reviews the top-K ranked candidates and at least K additional randomly-sampled candidates below the rank threshold, to catch adverse impact), and the review cadence.

## Summary

- **Three regimes in effect in 2026:** [US EEOC guidance on AI in employment](https://www.eeoc.gov/laws/guidance/select-issues-assessing-adverse-impact-software-algorithms-and-artificial) (Title VII adverse impact + ADA), [NYC Local Law 144](https://www.nyc.gov/site/dca/about/automated-employment-decision-tools.page) (AEDT bias audits + candidate notice), [EU AI Act Article 6 + Annex III](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) (high-risk-system obligations for hiring AI).
- **Three load-bearing questions per tool:** does it substantially assist an employment decision; what demographic data does it consume / produce / infer; in which jurisdictions.
- **US EEOC frame:** Title VII four-fifths rule applies to AI; employer is responsible even for vendor tools; ADA concerns on personality / cognitive / video analysis especially.
- **NYC LL 144 frame:** annual bias audit, candidate notice ≥10 business days, data source and type on request; applies to AEDTs that substantially assist hiring / promotion decisions in NYC. Scope boundaries clarified by DCWP final rules.
- **EU AI Act frame:** hiring / selection / promotion AI classified high-risk under Annex III; high-risk-system obligations (Articles 8–15, 17) apply from 2026-08-02 for Annex III; Article 4 AI literacy in effect from 2025-02-02; Article 50 transparency.
- **Team-practice artifact** (Exercise 05): AI inventory in hiring + performance pipeline, trigger assessment per tool, documentation state, routing map, review cadence.
- **Manager owns:** inventory, trigger flagging, team-scope practice, human oversight assignment. **HR owns:** formal mechanics, bias-audit publication, candidate notice drafting, accommodations, PIP compliance. **Legal counsel owns:** opinion, scope determination, regulator response, contract review.
- **Must not do:** approve new tool without compliance review, promise "unbiased," run bias analyses on protected-class data personally, interpret the law, cite this chapter as legal opinion.
- **Composes with** [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/) for broader AI governance at team scope; [`mod-105`](../mod-105-team-ai-enablement-programs/) for AI literacy obligations under EU AI Act Article 4.
