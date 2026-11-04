# Exercise 05 — LLM-as-Judge, Promptfoo, LangSmith: The Reading-Level Walkthrough

**Estimated effort:** 3 hours.

## Objective

Reach **reading-level fluency** — the bar defined in [`mod-101`](../../mod-101-ai-augmented-team-manager-position-and-contract/) Chapter 5 — on at least two of the three named eval tools (Promptfoo, LangSmith, Inspect AI) by running a small, documented eval end-to-end, inspecting the resulting report and traces, and writing a one-page "how I would read this if a peer sent it to me" guide for your team. You are not building a production eval harness; you are earning the right to commission one and read the result.

## Prerequisites

- Chapter 4 of this module and the Chapter 5 fluency bar in [`mod-101`](../../mod-101-ai-augmented-team-manager-position-and-contract/).
- Exercise 04 — the commissioning brief. This exercise's walkthrough should ideally run against the workflow you drafted a brief for, so the two outputs reinforce each other.
- API credentials for at least one model provider (Anthropic / OpenAI / Google / Azure OpenAI / local Ollama). A free tier is fine for this scale; the eval is small.
- Developer-tooling comfort — you will install CLI tools and run them. If you are not in a position to do so, work through the docs' hosted / cloud equivalents (Promptfoo Cloud, LangSmith SaaS, Inspect's `inspect eval --model`).
- Links: Promptfoo quickstart (<https://www.promptfoo.dev/docs/intro>), LangSmith docs (<https://docs.smith.langchain.com/>), Inspect AI docs (<https://inspect.aisi.org.uk/>), G-Eval paper (<https://arxiv.org/abs/2303.16634>).

## Problem statement

The commissioning role (Chapter 4 + Exercise 04) depends on being able to read the harness's output and challenge it. "Pass / fail is enough" fluency is below the bar. You need to be able to:

- Open a Promptfoo report, state what moved and what did not, and name the specific tests that fired.
- Read a LangSmith trace end-to-end for a judge run and point to the prompt, the retrieved context (where applicable), and the specific judgement the judge issued.
- Read an Inspect AI eval log and know the sample size, pass rate, and any confidence interval the harness reports.
- Challenge a judge rubric — notice when the rubric rewards the wrong behaviour (e.g., verbose-as-faithful), when the judge model is too small / too same-family, or when the dataset is biased.

This exercise builds that fluency on a small, real example and leaves you with a reading-guide you can send to a new IC or a hiring-loop candidate when they ask "how does your team use these tools?"

## Steps

1. **Pick two of the three tools.** At least one must be Promptfoo (the CLI-first eval runner) or Inspect AI (the UK AISI eval framework), because those two give you the cleanest "harness + report" shape. The second can be LangSmith (for traced judge runs with dataset management), or the other of Promptfoo / Inspect AI.
2. **Pick a tiny, real task.** Three to ten test cases. Candidates: PR-description drafting (input: a diff hunk; output: a PR description; ground truth: the human-written version), SQL-query generation (input: a question; output: SQL; ground truth: a known-good query), hypothetical-ticket drafting against a style guide. Keep it small. The exercise is about reading tools, not building datasets.
3. **Build the Promptfoo config.** `promptfoo init` scaffolds a config; adapt it to your task. Add at least one `llm-rubric` assertion (the Promptfoo LLM-as-judge mechanism) and one deterministic assertion (contains / regex / JavaScript). Run `promptfoo eval`.
4. **Inspect the Promptfoo output.** Read the CLI report; open the `promptfoo view` web UI if available. For each test case, note which assertions passed / failed and why. Write down one surprise.
5. **Build a minimal Inspect AI eval (or the other tool you chose).** Follow the Inspect quickstart — define a `Task` with a dataset, a solver (the model call), and a scorer (deterministic or model-graded). Run `inspect eval`. Open the eval log viewer.
6. **If LangSmith is one of your two:** set up tracing on the judge-model call by setting the `LANGCHAIN_TRACING_V2` / `LANGSMITH_API_KEY` environment variables (see docs). Re-run your Promptfoo or Inspect eval with tracing enabled. Open the LangSmith run view. Note what you can see about the judge's inputs, outputs, and latency that was *not* visible in the standalone report.
7. **Adversarially read one judge decision.** Pick one test case where the judge scored the output as "pass" or "high quality." Read the judge's prompt, the model's output, and the judge's rationale. Would you have scored it the same? If not, write down the specific wording in the judge rubric that produced the divergence.
8. **Do a mini-calibration pass.** Score 5 of your test cases by hand on the same 1–5 rubric your judge uses. Compare to the judge's scores. Compute Spearman correlation informally (does the ranking match on the top 2 and bottom 2?). This is the single most important muscle for the commissioning role.
9. **Write the reading guide.** One page, team-oriented. Structure:
   - *What this tool does.*
   - *Where the report lives when a peer runs it.*
   - *How to open the report and the trace.*
   - *The three questions I always ask of a report from this tool.* (E.g., "Is the dataset fresh?", "Has the judge been calibrated?", "Did any deterministic assertion fire that I need to read before reading the judge score?")
   - *The two things I distrust by default.* (E.g., "same-family judge," "judge rubric that rewards length.")
10. **Walk the guide with the senior IC from Exercise 04.** Specifically: *"If I sent you this report, is this the reading I would want you to do before we talked?"* Note divergences. Iterate.

## Starter guidance

- Three to ten cases, not thirty. The exercise is tool-fluency, not harness-building.
- Pair the deterministic and the model-graded assertion in Promptfoo — the deterministic one is cheap, lets you sanity-check the judge, and often catches obvious failures before the judge is even consulted.
- Use a different-family judge from the model you are grading. Mixing families reduces one of the common LLM-as-judge biases. Document the choice.
- If your API bill is a concern, set `temperature=0` on the judge and small `max_tokens`; this exercise should cost under a dollar per run.
- Inspect AI's log viewer and LangSmith's trace view are each worth 30 minutes of poking even if your eval is tiny. The UX is the point — you are learning what a peer would see when they open the tool.
- The adversarial read (step 7) is where most of the learning is. A judge that is 90% aligned with you has a 10% blind spot; the blind spot is where the rubric needs tightening, and finding it is a manager skill, not an IC one.
- Do not open Promptfoo for production use after this exercise — you are at reading level, not operating level. Chapter 7's boundary applies.

## Acceptance criteria

The deliverable is complete when:

- Two of the three tools (Promptfoo / LangSmith / Inspect AI) have been used end-to-end on a tiny, real task with 3–10 cases.
- A Promptfoo or Inspect report has been opened, read, and at least one specific finding written down.
- (If LangSmith chosen) a traced judge run has been inspected and one thing visible in the trace that was not in the report has been named.
- A mini-calibration pass has been performed on five cases with an informal correlation to the judge.
- A one-page reading guide has been written with the structure above, including the "three questions I always ask" and the "two things I distrust by default."
- A senior IC has walked the guide and provided feedback; feedback either reflected or logged.
- The reading guide is saved to the team wiki or an equivalent location where a new IC or candidate could find it.

## Stretch goals

- **Third tool.** Do the walkthrough for the tool you did not pick. Many teams find Inspect AI's structured eval shape most useful for safety / capability claims; others find Promptfoo's CLI fit for CI integration. The compare-and-contrast exercise sharpens commissioning judgement.
- **G-Eval replication.** Read the G-Eval paper (Liu et al. 2023, <https://arxiv.org/abs/2303.16634>) and build one Promptfoo `llm-rubric` that follows the paper's form-filling + chain-of-thought construction. Compare to a naïve one-line rubric on the same task. Note the quality difference.
- **Dataset-in-the-wild.** For one open-source eval (EleutherAI's `lm-eval-harness`, HELM, AlpacaEval 2.0, Inspect AI's bundled evals), open the dataset and the eval code. Note one thing you learned about the shape of community evals that applies to your team's internal commission.
- **Judge-model shootout.** Run the same Promptfoo config with three different judge models (same-family, different-family, different-size). Record the divergence. The exercise gives you an intuition for how much the judge choice moves the number.
- **Trace-to-standard link.** For one failure in your tiny eval, trace back from the failing case to which section of your Exercise 01 PR template, Exercise 02 AGENTS.md, or Exercise 03 standards-as-code would have caught it. The exercise is the point of the module — the eval is a signal that feeds the stack.
