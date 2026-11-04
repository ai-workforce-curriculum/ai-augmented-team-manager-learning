# Chapter 5 — The Manager's AI-Fluency Bar: Enough to Review and Model, Not to Out-Ship

> *You do not need to be the fastest AI user on the team. You need to be the one who can read the output and judge it.*

## Motivation

The uncomfortable half of this role: you are not an IC anymore, and you cannot try to be. If you spend your week racing your most senior engineer to see who can ship more PRs through Cursor, you are (a) burning out, (b) undercutting your own authority to set standards, and (c) doing L25 work on an L40 salary. Neither your team nor your leadership is paying for that.

The other uncomfortable half: a manager who cannot *read* what the team's AI tools produce — cannot open Cursor and see the context the agent is using, cannot look at a Promptfoo report and know which signal is load-bearing, cannot read a LangSmith trace and spot the retrieval that returned the wrong document — has no business setting the review standard, approving the ROI narrative, or calling an incident post-mortem.

This chapter draws the line between "enough fluency" and "too much." It names five tools you must be able to read and model on, the artifacts you should personally be comfortable producing, and the IAPP AIGP vocabulary layer you add on top for cross-functional work.

## Core concepts

### The two-sentence bar

- **Can you open the tool your team uses most, run through the workflow they run, and come out with an artifact you would approve from them?** If no, your fluency is too low.
- **Are you shipping PRs to production from the team's main workflow?** If yes, your fluency has crossed into IC work and you are competing with your team instead of managing them.

Hold both tests. Most of what follows is the operational detail of the first.

### The five tools you must be fluent-enough in

Not an exhaustive tool list — a working minimum. Adjust to what your team actually uses; the shape of the requirement does not change.

**1. One AI coding assistant.** Pick whichever your team uses: **Cursor**, **GitHub Copilot**, **Claude Code**, **Windsurf**, or similar. You should be able to:

- Open a repo, use the assistant to make a small change, read the diff, and judge whether the change is safe.
- Read the rules file / project instructions (Cursor rules, AGENTS.md, `.github/copilot-instructions.md`) your team uses, and propose an edit.
- Spot when the assistant has pulled the wrong context into its window (wrong file, stale doc, truncated).
- Ask it to produce a PR description or an ADR first draft and know what to delete.

**2. One general-purpose AI assistant.** **Claude** (claude.ai or Claude Code), **ChatGPT**, or **Gemini**. You should be able to:

- Use projects / workspaces to give the model repeatable context.
- Draft a one-pager, a decision memo, or an exec pre-read — and edit heavily enough that the output is yours, not the model's.
- Recognise and refuse an overlong, over-hedged, confidently-wrong draft on a topic you know.

**3. One eval tool at reading level.** **Promptfoo**, **LangSmith**, **Inspect AI**, **Langfuse**, or **Arize Phoenix**. You should be able to:

- Open an eval report from one of these tools and know what a pass / fail / regression means.
- Ask the right follow-up questions on a judge-model report (is the judge calibrated? is the dataset representative? did the pass bar change?).
- Commission a new eval with a one-page brief (`mod-103` is where you practice this; the reading-level fluency is the prereq here).
- Read a LangSmith trace end-to-end for a simple agent run and spot the retrieval step.

**4. One agent-authoring environment at reading level.** **Claude Code** (as agent harness), **LangGraph**, **CrewAI**, **PydanticAI**, or whatever your team uses. You should be able to:

- Read an AGENTS.md file and understand the delegation ladder.
- Read an MCP tool-authorisation policy and understand which tools the agent can reach.
- Approve or block a proposed new tool connection on grounds a non-engineer leader could challenge you on.

**5. The team's standards-as-code conventions.** This is the stack your team uses to encode the human/machine contract. Typically: Cursor rules / AGENTS.md / ADR templates / lint policies / pre-commit hooks / CI gates. You should be able to:

- Read every file in the stack.
- Propose a change (not necessarily implement it) when a standard is drifting.
- Explain to a VP why the standard looks the way it does.

### Artifacts the manager personally produces

Fluency is measured by the artifacts you produce without delegation. At this level, you personally write (or heavily edit a model's draft of):

- The team's human/machine contract (Chapter 3; Exercise 03).
- The team's quarterly adoption roadmap one-pager (`mod-102`).
- The team's ROI narrative for the quarter (`mod-104`).
- The team's post-mortem narrative for an AI-produced incident (`mod-109`).
- The team's annual governance crosswalk snippet that rolls up to the governance analyst (`mod-110`).
- Hiring loop structure, interview rubrics, levelling / promotion criteria under AI augmentation (`mod-108`).

Everything else — the PR, the test, the design doc, the dashboard query, the agent code — you review, you do not author. If you find yourself authoring one of those in a given week, it is because you are unblocking the team or because you are modelling the practice in a single targeted session. It is not your steady-state work.

### IAPP AIGP vocabulary for cross-functional work

The IAPP **AI Governance Professional (AIGP)** body of knowledge is the most widely-cited cross-functional AI-governance credential this cycle. You do not need the certification itself to do this job, but you will be in rooms with people who do — legal, compliance, risk, governance program managers — and they will use AIGP vocabulary. Working fluency means:

- Being able to read the AIGP body of knowledge and recognise the core structure: AI fundamentals, risk understanding, laws / frameworks (NIST AI RMF, EU AI Act, ISO/IEC 42001), organisational AI governance, ongoing use and lifecycle.
- Being able to translate your team-scope artifacts into that vocabulary when asked ("our team review standards address NIST GOVERN 1.1 and MANAGE 2.3 at the team-scope translation layer; the governance analyst holds the org-level crosswalk").
- Being able to defer gracefully when a legal / compliance partner reaches past your altitude ("that's a question for `head-of-ai-governance`; I can give you our team evidence as input").

`mod-110` is where this vocabulary layer is practiced in depth. Chapter 5's expectation is only that you know it exists, know what it covers, and know when to pull it into conversation.

### What stays IC and what stays L45+

Three cuts worth naming explicitly.

**Do not** try to reach IC-mechanics depth in:

- Writing the eval harness yourself. Commission it; read it. `ai-risk-engineer` (peer, L25) and `ai-eval-engineer` (peer, L30, AI Engineering family) build; you commission (`mod-103`).
- Writing production agent code. `ai-assisted-software-engineer` (L25) and agent-platform-engineer (AI Engineering family) build; you commission (`mod-106`).
- Statistical / benchmark methodology depth. `model-evaluation-engineer` (peer, L30, ML Engineering family) owns methodology; you own the choice of what to measure (`mod-104`).

**Do not** try to reach L45+ depth in:

- Org-wide procurement at scale. `ai-enablement-lead` (L45); you contribute your team's evidence.
- Control-library architecture. `senior-ai-governance-architect` (L50).
- Regulator engagement. `head-of-ai-governance` (L60) / `chief-ai-officer` (L70).

**Do** reach for:

- Team-scope readings of all of the above. You should be able to look at a legal partner's procurement question or a program architect's control taxonomy and say what it means for your team this quarter.

## Example: a weekly fluency routine

A sustainable rhythm that keeps the bar met without crossing into IC work:

- **Weekly (30–60 min):** open Cursor / Claude Code / Copilot on a toy change in a repo. Not team production. Sanity-check that the tool still behaves the way you remember. Note any default or behaviour change since last week.
- **Weekly (30 min):** read one eval report from your team's main workflow. In LangSmith or Promptfoo. If there is no report, that is itself a signal — follow up with `mod-103` work.
- **Monthly (2 hours):** re-read your team's human/machine contract and standards-as-code stack. Propose one edit, however small, if anything has drifted.
- **Quarterly (half-day):** work through a non-trivial change end-to-end with your team's exact tool stack. Pair with an IC on it. This is the "can I still review this honestly?" test.

Add a cross-functional reading rotation — one NIST AI RMF Playbook section, one EU AI Act article, one AI Incident Database entry per month — and you have the fluency floor covered without crossing the IC line.

## Summary

- The bar is **enough fluency to review and model**. Over the bar is out-shipping your team; under the bar is managing a system you cannot read.
- Five tools worth being fluent-enough in: one AI coding assistant, one general-purpose assistant, one eval tool (reading level), one agent-authoring environment (reading level), the team's standards-as-code stack.
- Personally author the manager-altitude artifacts (contract, roadmap, ROI, post-mortem narrative, governance snippets, hiring structure); review but do not author the IC artifacts.
- Keep an active IAPP AIGP vocabulary layer so cross-functional conversations route cleanly.
- Keep a sustainable weekly / monthly / quarterly rhythm so the bar stays met.
- Exercise 05 is where you draft your own 90-day fluency baseline plan.
