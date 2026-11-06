# Lab 03 — Fluency-Floor Sanity Check

**Duration:** 45–75 minutes.
**Chapters exercised:** Chapter 5 (two-sentence bar; five tools; weekly rhythm).
**Complements, does not duplicate:** Exercise 05 asks you to write a **dated 90-day fluency plan** with drift tests. This lab is the one-time baseline **test** that tells you where the plan needs to start — a single session that runs Chapter 5's weekly rhythm end-to-end so you know, concretely, what reading-level fluency feels like on each of the five tools.

## Objective

Spend one working session running the weekly fluency rhythm from Chapter 5 against a toy change in a disposable repo. By the end, produce a one-paragraph self-rating per tool category (fluent / adequate / weak / not yet) grounded in what you just observed yourself doing — not what you remember doing last quarter.

The lab is deliberately small. It is **not** a Cursor tutorial, a Promptfoo tutorial, or an eval authoring lab. It is a reading-level sanity check calibrated to the manager-altitude bar.

## Prerequisites

- Chapter 5 read (two-sentence bar; the five tools; the weekly / monthly / quarterly rhythm; what stays IC and what stays L45+).
- Access to **one** AI coding assistant you (or your team) use — Cursor, GitHub Copilot, Claude Code, Windsurf, or equivalent. The specific tool does not matter; the reading skill does.
- Access to **one** general-purpose assistant — Claude, ChatGPT, or Gemini.
- A disposable local directory you can safely edit. We will not touch any team repo.
- A blank text file for your observations.

If your team uses an eval tool (Promptfoo / LangSmith / Inspect AI / Langfuse / Phoenix) and an agent-authoring environment (Claude Code / LangGraph / CrewAI / PydanticAI / …), the optional steps 5 and 6 below exercise those. If you have no access, write `<!-- needs-research: no team tool in this category available at session time -->` in your observation file and skip — do not fabricate.

## Steps

### Step 1 — Prepare a disposable repo (5 min)

Create a throwaway working directory. We want a tiny, boring project — no team code, no production surface.

```bash
mkdir -p ~/lab-03-fluency && cd ~/lab-03-fluency
git init
cat > README.md <<'EOF'
# lab-03-fluency

Disposable project for mod-101 Lab 03. Not production.
EOF
cat > greet.py <<'EOF'
def greet(name):
    return "Hello, " + name

if __name__ == "__main__":
    print(greet("world"))
EOF
git add . && git commit -m "init"
```

Expected: `git log` shows one commit; `python3 greet.py` prints `Hello, world`.

### Step 2 — Coding-assistant reading drill (10–15 min)

Open the repo in your AI coding assistant. Ask it to do a *small*, *boring* change — not an impressive one. Suggested prompt:

> "Add a `greet` call for the name `"team"` and a unit test for the existing `greet` function. Keep the change minimal."

When the assistant proposes a diff, do these four things in order and jot one short line per step in your observation file:

1. **Read every line it produced.** No skimming. If it inserted an import you did not expect, write down what and why. If it added error handling, write that down.
2. **Check what context it pulled.** In Cursor / Claude Code this is a context pane or `@file` chips; in Copilot it is less visible — note what you can and cannot see. Chapter 5: "spot when the assistant has pulled the wrong context into its window (wrong file, stale doc, truncated)."
3. **Spot one thing you would reject if an IC submitted it as a PR.** There will be something — over-eager hedging, an extra docstring you didn't ask for, a test that asserts the wrong thing, a stylistic choice that doesn't match the repo. Write it down.
4. **Apply the change, run it, and verify it works.** `python3 -m pytest` or equivalent. Then `git diff HEAD` and re-read the final state.

Observation-file line (fill in from what you saw): `Coding assistant: I could / could not read the context pane; I caught [specific issue]; I would accept / reject this as a PR.`

### Step 3 — General-purpose assistant drill (8–10 min)

Open your general-purpose assistant (Claude / ChatGPT / Gemini). Ask for a short manager-altitude artifact on a non-sensitive topic. Suggested prompt:

> "Draft a 150-word Slack message announcing a 30-minute team review of our human/machine contract next Thursday. Audience: 10 engineers. Tone: direct, not performative."

When the draft comes back:

1. **Edit heavily.** Chapter 5: "edit heavily enough that the output is yours, not the model's." Count the words you kept verbatim vs. the words you replaced.
2. **Spot one overlong / over-hedged / confidently-wrong element.** Write down what you spotted.
3. **If the model confidently invented a detail** (a specific day, a specific room, a specific policy clause), note it. That is the Chapter 5 behaviour you must be able to recognise and refuse.

Observation-file line: `General-purpose assistant: I kept ~N% of the draft verbatim; I caught [specific over-hedge / overclaim]; the output is / is not mine after editing.`

### Step 4 — Standards-as-code reading drill (5 min)

Open your team's actual standards-as-code stack — Cursor rules, AGENTS.md, `.github/copilot-instructions.md`, ADR template, lint policy, pre-commit hooks, CI gates. Open at least one file from the stack in read-only mode.

Pick one rule or one clause. Write two lines in your observation file:

- What does this rule enforce in plain language, and against what failure mode?
- If the rule drifted (e.g., your team started ignoring it), what would be the first signal?

If your team has no standards-as-code stack yet, write `<!-- needs-research: team has no standards-as-code stack at session time; mod-103 is the entry point -->` and move on.

### Step 5 (optional) — Eval report reading drill (10 min)

Chapter 5: "Open an eval report from one of these tools and know what a pass / fail / regression means."

If your team runs Promptfoo, LangSmith, Inspect AI, Langfuse, or Phoenix on a main workflow, open the most recent report. Spend ten minutes reading it and answer these in your observation file:

1. How many test cases were run, and what is the pass bar?
2. Which signal is load-bearing — the pass rate, a specific judge-model score, a regression against a baseline, latency, or cost?
3. If a judge model produced the pass/fail call, is the judge calibrated? When was it last re-validated?
4. Is the dataset representative of what the main workflow actually does?

If you cannot answer at least two of the four, your fluency on eval reports is weak — Chapter 5 flags this as the prereq to `mod-103`'s eval commissioning.

If your team runs no eval tool, write `<!-- needs-research: no team eval tool at session time; this is itself a mod-103 signal -->` and move on. The *absence* is a finding.

### Step 6 (optional) — Agent-authoring reading drill (10 min)

Chapter 5: "Read an AGENTS.md file and understand the delegation ladder. Read an MCP tool-authorisation policy and understand which tools the agent can reach."

If your team has an AGENTS.md or MCP configuration in production, open it and write two lines in your observation file:

- Which tools can the agent reach, and which are blocked?
- If a non-engineer leader challenged you on *why* the current authorisation set is approved, could you defend it in one paragraph? Draft the paragraph.

If your team has no agent in production, write `<!-- needs-research: no team agent at session time; mod-106 is the entry point -->` and move on.

### Step 7 — Self-rating paragraph per tool category (10 min)

Chapter 5 lists five tool categories. Write one short paragraph per category (4 lines max each) in your observation file, with this shape:

```
[Category name]: [tool you used] — rating [fluent / adequate / weak / not yet].
Observed evidence from today's drill: [one or two sentences, referencing what you actually did above].
Nearest Chapter 5 gap: [one short note on what you could not do that the chapter sets as the bar].
```

Five paragraphs: AI coding assistant · general-purpose assistant · eval tool · agent-authoring environment · standards-as-code stack.

Ratings must be grounded in what you did in steps 2–6, not in what you *think* you can do.

### Step 8 — Clean up (2 min)

```bash
rm -rf ~/lab-03-fluency
```

Delete the throwaway chat / conversation with the general-purpose assistant if the tool supports it. Do not leave AI context lying around.

## Expected output

A single observation file, roughly one page, containing:

- One short line per sub-drill in steps 2–4 (and 5–6 if run).
- Five self-rating paragraphs, one per tool category, grounded in evidence.
- Any `<!-- needs-research: ... -->` markers for categories you could not exercise.

## Checkpoint

Before moving on to Exercise 05 (where you draft the 90-day plan), you should be able to answer **yes** to all three:

- On the AI coding assistant, did you catch at least one thing you would reject if an IC submitted it as a PR? (If no, your reading is too fast — Chapter 5's "read every line" test is not being met.)
- On the general-purpose assistant, did you spot at least one over-hedge or confidently-wrong element? (If no, Chapter 5's "recognise and refuse" test is not being met.)
- Do you now have an honest, evidence-grounded rating on all five tool categories — including any marked `<!-- needs-research: ... -->` because the tool is not present on your team?

If any answer is no, repeat the relevant step before writing the Exercise 05 plan. A plan written on top of a self-flattering baseline will drift fast.
