# mod-103-review-standards-and-eval-commissioning: Review Standards, Standards-as-Code, and Commissioning Eval Frameworks

> Scaffolded by `aicg org execute-plan`. Lecture chapters and exercise content are authored on subsequent autonomous cycles.

**Estimated effort:** 18 hours

## Learning objectives

- Set team-level review standards for AI-generated work — PR / review checklists for AI-written code and documents, verification requirements, what 'LGTM' means when the author was a model — anchored in R2 (0.60, 6 in-window postings) and R3 (0.44)
- Encode standards-as-code — Cursor rules files, AGENTS.md conventions, ADR templates, lint policies, pre-commit hooks — so the same norms govern both human and agent authors
- Commission eval frameworks at the team scope — decide WHAT to evaluate, who owns the harness, how outputs feed back into team norms — using LLM-as-judge (G-Eval), Promptfoo, LangSmith, and Inspect AI as the working toolset; defer eval-harness IC mechanics to `ai-assisted-software-engineer` (level 25) and `ai-eval-engineer` (level 30, AI Engineering family)
- Author the accountability contract — 'AI generates, humans own' — including how the team routes blame when an agent is wrong (threads into mod-109)
- Map team review norms to the OWASP Top 10 for LLM Applications so prompt-injection, output-handling, and sensitive-data risks surface at review time
- Position the ownership boundary: engineered risk / guardrail depth lives at `ai-risk-engineer` (level 25, AI Governance family); managers commission and act on the evidence, don't rebuild the rig

## Structure

- `01-…md` … `0N-…md`: lecture chapters.
- `exercises/`: per-exercise prompts.
- `labs/`: long-form hands-on labs.
- `quizzes/`: knowledge checks.
- `resources.md`: external references.
