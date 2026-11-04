# Chapter 4 — Commissioning Eval Frameworks at Team Scope

> *You are not building the eval harness. You are the person who decides what to measure, who builds it, and what the team does when the number moves. Those are three manager decisions.*

## Motivation

R3 (0.44 of the posting sample; see [`JOB_REQUIREMENTS.md`](../../JOB_REQUIREMENTS.md)) names commissioning eval frameworks at the SDLC / workflow level as a named responsibility for this role. The verbatim phrasings are *"commission golden-task and regression evals,"* *"stand up LLM-as-judge for review signal,"* *"decide what to evaluate,"* *"own the feedback loop from eval into team practice."*

Note the verbs. Commission. Decide. Own the loop. The postings do not ask the manager to *build* the eval. The market has learned this much: eval-harness authoring is an IC-engineering activity owned by [`ai-assisted-software-engineer`](https://github.com/ai-engineering-curriculum/ai-assisted-software-engineer-learning) (L25, AI Engineering) and [`ai-eval-engineer`](https://github.com/ai-engineering-curriculum/ai-eval-engineer-learning) (L30, AI Engineering), with engineered-risk / red-team / guardrail depth owned by [`ai-risk-engineer`](https://github.com/ai-governance-curriculum/ai-risk-engineer-learning) (L25, AI Governance). The manager is on a different hook: *decide what the team's evals exist to answer, authorise the harness, and act on the results.*

This chapter is about doing that commissioning well. What to decide; what to delegate; what to read; where the feedback loop closes. The working toolset — LLM-as-judge in the G-Eval shape (Liu et al. 2023, <https://arxiv.org/abs/2303.16634>), [Promptfoo](https://www.promptfoo.dev/docs/intro), [LangSmith](https://docs.smith.langchain.com/), [Inspect AI](https://inspect.aisi.org.uk/) from the UK AI Safety Institute — is named so you have specific tools to point at in the commissioning brief, not to be reimplemented by you.

## Core concepts

### Three questions before any tool

A commission that skips these questions is a procurement conversation dressed as an eval conversation. Answer them first.

**Q1 — What is this eval going to *decide*?** An eval that is not attached to a team decision is a vanity metric. For each proposed eval, name the decision it informs:

- *Pass/fail of a new agent workflow going to default-on* (feeds the Chapter 3 adoption-mode decision in [`mod-102`](../mod-102-team-ai-adoption-and-roadmap/)).
- *Regression gate on a model-version bump* (the team's defence against silent degradation when the vendor rolls a new version; see also the vendor-posture discussion in [`mod-111`](../mod-111-vendor-budget-and-tool-selection-at-team-scope/)).
- *Review-bar calibration* (does the Chapter 2 checklist actually catch the OWASP LLM01 prompt-injection surface it claims to? Chapter 6 question).
- *Quality floor on an AI-produced artifact class* (e.g., auto-generated PR descriptions must achieve a judge score ≥ 4/5 on faithfulness).
- *ROI input* (per the measurement work in [`mod-104`](../mod-104-productivity-measurement-and-ai-roi/) — but note the eval is not itself the ROI number; it is an input).

If a proposed eval does not map cleanly to a decision like these, say no. There is always more to measure than there is capacity to act.

**Q2 — Who owns the harness?** Three options; pick one and name them in the brief.

- *A named `ai-risk-engineer` or `ai-eval-engineer` peer* (cross-functional ownership — your preferred option for anything that touches engineered risk, red-team, or jailbreak-resistance).
- *A senior IC on your team* (team-internal ownership — appropriate for a golden-task eval over your team's own repos; pair them with the external peer for review).
- *A platform / DevEx team* (platform ownership — appropriate when the eval harness is generic enough to serve multiple teams; the hand-off pattern from [`mod-102`](../mod-102-team-ai-adoption-and-roadmap/) Chapter 5 applies).

Shared ownership between two of the three is fine and common. "The team" is not an owner.

**Q3 — How does the output feed back into team practice?** An eval that produces a weekly report nobody reads is a tax on the owner. Before the first run, decide:

- *Where is the report delivered?* (A channel; a dashboard tile; a Q-review slide; the manager's Monday pre-read.)
- *Who reads it and what do they do with it?* (The tech lead triages; the manager is informed of trend; new findings become ADR drafts via Chapter 3's template.)
- *What is the threshold that triggers action?* (Named numerically — "judge-score drops ≥ 0.2 on the faithfulness eval for two consecutive runs → rollback or ADR.")
- *Who authorises the action?* (Usually: the tech lead for narrow fixes, the manager for workflow-level rollback, the sponsor plus governance for anything escalating.)

A feedback loop without a named reader is open.

### The four eval shapes most teams need, at team scope

You will not need every kind of eval. Most teams converge on three or four; the fifth and sixth are specialised and are commissioned when the specific failure mode is in-view.

**Shape A — Golden-task eval.** A small, hand-curated set of representative tasks (10–100 items is a typical start) with known-good outputs or known-good *acceptance predicates*. Run the AI workflow on each; score the output. Example: 20 PR-description-drafting tasks, each with the actual PR as ground truth, scored with a judge prompt on faithfulness and completeness.

- *Primary tool:* Promptfoo (<https://www.promptfoo.dev/docs/intro>) — a CLI / config-driven eval runner with built-in support for judge models, multiple providers, and CI integration. The commissioning brief should name the dataset location, the judge prompt, the pass bar, and the CI integration if any.
- *When to use:* workflow pass/fail; model-version regression gate.

**Shape B — LLM-as-judge (G-Eval shape).** A judge model is prompted with a rubric and asked to score the output. The G-Eval paper (Liu et al. 2023) formalised the use of chain-of-thought-prompted LLM judges with a form-filling paradigm; the pattern generalises to any case where the quality criterion is "would a careful reviewer accept this?"

- *Primary tools:* Promptfoo (has judge-model assertions built-in); LangSmith (<https://docs.smith.langchain.com/>) for traced judge runs and dataset management; Inspect AI (<https://inspect.aisi.org.uk/>) for structured evals with judge scorers.
- *When to use:* subjective quality (writing, summary, code-review feedback); workflow pass/fail.
- *Calibration caveat:* a judge is itself a model. Calibrate it against human judgements on a sample before trusting its score — this is the single most common mistake with LLM-as-judge and the commissioning brief should require calibration evidence. The G-Eval paper reports Spearman correlations against human judgement; the brief should require the harness owner to report theirs.

**Shape C — Regression / replay eval.** A fixed set of prompts (and recorded context, for RAG) replayed on a new model version or a new workflow revision; outputs compared to a baseline. The purpose is not absolute quality; it is *did anything move that we did not expect*.

- *Primary tools:* LangSmith (built for traced replay against datasets; supports experiments and comparison). Promptfoo supports this with assertions against prior outputs.
- *When to use:* model-version-bump gate; agent-prompt-change gate.

**Shape D — Capability / safety eval, in a standardised harness.** A structured eval against a named benchmark or against your team's own safety claims — can the agent refuse an obvious prompt-injection; does it leak PII; does it stop when it should.

- *Primary tool:* Inspect AI (<https://inspect.aisi.org.uk/>) — the UK AI Safety Institute's open-source eval framework, designed for structured, reproducible capability and safety evaluations. Integrates with many providers; Inspect-authored evals and community evals are both runnable.
- *When to use:* team posture statements that reference OWASP LLM Top 10 risks (Chapter 6); any claim of "the agent refuses X" that needs to be defensible.

A fifth shape — *production-sampled online eval* (sample a slice of real traffic through a judge in real time) — is specialised and commissioned when the team has the volume for it and the governance posture to collect the traffic. The caveat on judge calibration is the same, and the privacy posture needs review ([`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/)).

### What the manager produces: the commissioning brief

The deliverable from the manager side is a **commissioning brief** — one page, maybe two — that the peer who will build the harness can execute against without a follow-up meeting. The structure:

1. **Decision this eval exists to inform.** One sentence. (Q1 above.)
2. **Scope.** Which agent / workflow / artifact class; which model version(s); what repos / data / traffic the eval runs against; what is explicitly *out-of-scope*.
3. **Eval shape.** Golden-task / judge / regression / capability. One chosen; others listed as deferred if applicable.
4. **Dataset.** Where it comes from; who curates; how it is kept current; how it is stored (privacy / secrets posture matters — see [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/)).
5. **Judge configuration** (if applicable). Which model, which rubric, calibration evidence required against human judgement sample.
6. **Pass / fail / regression thresholds.** Specific numbers. "Faithfulness judge score ≥ 4.0/5.0 mean on the 50-task golden set; regression threshold ≥ 0.2 drop between consecutive runs." No fuzzy words.
7. **Tool choice.** Promptfoo / LangSmith / Inspect AI / other. Justified in one line.
8. **Owner and co-owner.** Named humans; who reviews the harness code (yes, the harness itself is reviewed to the Chapter 2 bar); who owns refreshing the dataset.
9. **Feedback loop.** Where the report lands; who reads it; what threshold triggers what action; who authorises the action.
10. **Review and sunset.** Quarterly review; sunset when the decision the eval informs is retired.

Not ten sections of theatre. Ten short answers that make the harness buildable and the result actionable.

### What *not* to delegate

Three decisions stay with you.

- **What to evaluate.** The harness owner can advise on feasibility and on toolchain; they do not get to decide which workflows the team cares enough about to evaluate. That is your call because you are the one holding the team's work prioritisation.
- **What constitutes pass / fail.** The harness owner can propose thresholds; the manager owns the final number. A reviewer-facing number is a social instrument — if you do not understand why 4.0 and not 3.5, you cannot defend the number to the team or to leadership.
- **What the team does when the number moves.** Rollback, block merges, open ADR, escalate — the response to signal is a team-practice decision, which is yours.

If you find yourself being asked to approve the choice of embedding model or the schema of the eval dataset, you are being pulled too deep. Push that back politely (*"that is a harness-owner decision; the brief says you decide, and I'll review the trade-off summary"*).

### What *to* read, and at what depth

The fluency bar from [`mod-101`](../mod-101-ai-augmented-team-manager-position-and-contract/) Chapter 5 applies here. You should be able to:

- Open a Promptfoo report and state: *what was the pass bar, what moved, what did not*.
- Read a LangSmith trace end-to-end for one judge run and point to the specific prompt + retrieved context that produced the score.
- Read an Inspect AI eval result and name the sample size, the pass rate, and the confidence interval if the harness reports one.
- Read a G-Eval-style rubric and challenge it (*"the faithfulness criterion as written also rewards verbosity; can we separate the two?"*).

You should *not* be writing the Promptfoo config or the LangSmith judge prompt. The read-and-challenge posture is where the manager earns the eval investment back.

### Where eval work hands off — and where it does not

Several nearby tracks own adjacent depth. The ownership map:

| Boundary | You | Them |
|---|---|---|
| Workflow-pass/fail eval on a team's own agent | Commission + act | IC-engineering build: [`ai-assisted-software-engineer`](https://github.com/ai-engineering-curriculum/ai-assisted-software-engineer-learning) (L25) |
| Eval harness / dataset / judge-calibration depth | Commission + read | Peer build + depth: [`ai-eval-engineer`](https://github.com/ai-engineering-curriculum/ai-eval-engineer-learning) (L30, AI Engineering) |
| Red-team, jailbreak, prompt-injection exploit construction, guardrail tuning | Commission + act | Peer build + depth: [`ai-risk-engineer`](https://github.com/ai-governance-curriculum/ai-risk-engineer-learning) (L25, AI Governance) |
| Benchmark methodology (statistical rigor, CI, effect size) | Commission + read | Peer depth: `model-evaluation-engineer` (L30, ML Engineering family) |
| Governance crosswalk (NIST AI RMF MEASURE, ISO 42001) | Contribute team evidence | Owner: [`mod-110`](../mod-110-ai-governance-and-policy-at-team-scope/); cross-track owner: `ai-governance-analyst` (L15) and `head-of-ai-governance` (L60) |

Chapter 7 draws the `ai-risk-engineer` boundary in more detail because it is the one most frequently blurred.

## Example: a two-paragraph commissioning brief

Treat as a calibration sketch, not a template to adopt wholesale.

> **Decision.** Should the Cursor-rules + AGENTS.md convention we piloted in Q1 go default-on across the payments team in Q2? The eval exists to answer that.
>
> **Scope.** The two agent workflows most used on `payments-api`: (a) PR-description drafting, (b) unit-test-skeleton generation. Model: claude-sonnet-4-6 and claude-opus-4-7 (compared). Not in scope this quarter: ADR drafting, incident runbooks, customer-comms.
>
> **Eval shape.** (a) Golden-task eval on 30 PR-description instances from Q1's actual history with the PR-description we shipped as ground truth; LLM-as-judge on faithfulness and completeness (G-Eval rubric; judge-model claude-opus-4-7; calibrated against a 10-instance human-rated sample with ≥ 0.6 Spearman required). (b) Golden-task on 20 unit-test cases with an acceptance predicate: *the generated test passes the referenced function's existing behaviour and fails a known-bad mutation*.
>
> **Pass bar.** Mean judge score ≥ 4.0/5.0 on (a); ≥ 80% of (b) passes both arms of the acceptance predicate. Regression threshold: ≥ 0.2 drop or ≥ 10 pp drop between consecutive runs blocks merges to the agent config.
>
> **Tool.** Promptfoo for both; LangSmith for judge-run tracing and dataset storage.
>
> **Owner.** `@ai-risk-engineer-peer` builds the harness; `@senior-ic-on-team` curates the dataset; I (manager) sign off on the pass bar and read the Monday report.
>
> **Loop.** Weekly report in `#payments-ai-eval`; monthly summary in the Q-review slide (per [`mod-112`](../mod-112-cross-functional-leadership-and-ritual-calendar/)). Below pass bar → rollback the agent config and open an ADR. Below bar twice → escalate to `ai-enablement-lead`.
>
> **Sunset.** Q3 review; if default-on has stuck without incident and the regression gate caught no issues for a full cycle, sunset (a) and reduce (b) to quarterly cadence.

One page in the wiki; buildable by the harness owner without a follow-up meeting.

## Summary

- R3 asks the manager to *commission* evals at team scope — decide what to measure, authorise the build, act on the results — not to build the harness.
- Three framing questions come before any tool: **What decision does this eval inform? Who owns the harness? How does the output feed back into team practice?**
- Four working eval shapes cover most team-scope needs: **Golden-task, LLM-as-judge (G-Eval), Regression / replay, Capability / safety.** Working toolset: Promptfoo, LangSmith, Inspect AI; add LangSmith for traced judge runs.
- Judges are models; they need calibration against human judgement before their score is load-bearing. Require calibration evidence in the brief.
- The commissioning brief is a one-pager with ten short answers — decision, scope, shape, dataset, judge config, thresholds, tool, owner, loop, sunset.
- Three decisions stay with you: *what to evaluate*, *what constitutes pass/fail*, *what to do when the number moves*. Delegate everything else.
- Ownership boundaries: harness build → `ai-assisted-software-engineer` (L25) / `ai-eval-engineer` (L30); red-team / guardrail depth → `ai-risk-engineer` (L25); benchmark methodology → `model-evaluation-engineer` (L30). Chapter 7 draws the `ai-risk-engineer` line.
- Exercises 04 and 05 are where you author the commissioning rubric and walk a judge-model / Promptfoo / LangSmith report end-to-end.
