# Quiz 01 — Scope, Contract, Deferral, Fluency

**Format:** 10 multiple-choice questions.
**Coverage:** All five chapters of mod-101.
**Scoring:** 1 point per question. 8/10 is a pass. Below that, re-read the chapter named in the answer explanation before moving on.

Each question tests whether you can apply the chapter, not whether you can quote it. Pick the single best answer.

---

## Question 1

A team you manage grows from 9 ICs to 22 ICs after a re-org. The AI-augmented workflow stays the same. Which of the following is the most accurate read of your level?

- A. The team is now too large for L40; graduate the role to `ai-engineering-manager` (L50) immediately.
- B. The team is now too large for L40; graduate the role to `ai-enablement-lead` (L45) because you are running enablement at scale.
- C. The team is still within L40 scope — the 5–30 band — and the L40 responsibilities continue to apply.
- D. You should split the team; L40 scope is capped at 10 ICs.

## Question 2

Your vendor ships a new model and deprecates the one your team uses in 90 days. Which of the following is the **L40** slice of that work?

- A. Open Cursor rules, test three prompts against the new model, and file a ticket when the diff-summary prompt regresses.
- B. Decide whether the upgrade changes the company-wide tool standard and coordinate procurement renegotiation.
- C. Re-check every prompt and review habit the team relies on, update the team's AGENTS.md and review checklist, run a short enablement session, re-cost token spend, and update the quarterly ROI one-pager.
- D. Rewrite the eval harness so it covers the new model's behaviour differences.

## Question 3

Chapter 2 names Grove, Fournier, Larson, and Zhuo as the assumed baseline. Which statement best describes what this track *does* with those four texts?

- A. Re-teaches their core frameworks (1:1 cadence, feedback structure, TRM, team sizing) in AI-augmented form.
- B. Treats them as prerequisite reading and layers AI-augmentation moves on top of their output/leverage model without re-teaching the fundamentals.
- C. Replaces them — the AI-augmented manager role requires a new output model that Grove, Fournier, Larson, and Zhuo do not cover.
- D. Uses them only for hiring and interviewing content; the rest of the track is independent of their frameworks.

## Question 4

A peer manager tells you their team "runs on the slogan *AI generates, humans own*" and does not have a written contract. According to Chapter 3, the strongest objection to that posture is:

- A. The slogan is wrong — humans should generate too, not just own.
- B. The slogan compresses three decisions (what AI drafts, what humans must check, who is on the hook) but cannot resolve any single incident on its own; without a written C1–C5 artifact, the team operates on vibes that break under incident.
- C. The slogan is outdated; the current phrasing in the field is "AI co-authors, humans edit."
- D. The slogan is fine as long as the vendor's SLA covers accountability; the written contract is only needed if the vendor refuses the SLA.

## Question 5

In the C3 accountability stack, a model ships a broken PR, a reviewer approves it without reading every line, and the IC submits it. Where does accountability for the **choice to use AI on this class of work in the first place** sit?

- A. The vendor — they shipped the model.
- B. The IC — they submitted the artifact.
- C. The reviewer — they approved the artifact.
- D. The manager — they own the system (the standard, the enablement, the reviewer bandwidth, and the decision that AI was appropriate for this class).

## Question 6

Your team's human/machine contract names C1 (what AI may draft), C2 (verification bar), C3 (accountability), C4 (what to do when AI is wrong), and C5 (what AI may see). One section, per Chapter 3, is "not optional" because without it the contract drifts invisibly. Which section is that?

- A. C1 — the artifact-class table.
- B. The change log.
- C. C5 — the data-handling boundary.
- D. The vendor SLA appendix.

## Question 7

A Monday-morning ask arrives: "Platform wants to canonicalise your team's Cursor rules file as the org standard." Using the Chapter 4 rubric, the correct route is:

- A. **Mine** — rules files are an L40 standards-as-code concern; keep ownership.
- B. **Down** — route to `ai-governance-analyst` (L15) for intake and inventory.
- C. **Up** — route to `ai-enablement-lead` (L45); hand off the rules file with a note on what is generalisable.
- D. **Sideways** — route to `ai-risk-engineer` (L25) to red-team the rules before they generalise.

## Question 8

Another Monday ask: "Why did the AI produce this specific output?" Chapter 4 splits this question into two destinations depending on what is actually being asked. Which split is correct?

- A. Engineering the guardrail → `ai-risk-engineer` (sideways); accountability for what shipped → yours (`mod-109`).
- B. Engineering the guardrail → yours; accountability for what shipped → `ai-risk-engineer`.
- C. Both halves → `ai-governance-analyst` (down) for intake first.
- D. Both halves → `head-of-ai-governance` (up); any model-behaviour question is above L40.

## Question 9

Your HR partner forwards a complaint that one IC is using AI to over-ship and squeeze a peer. Chapter 4's rubric routes this as:

- A. Fully **out** to HR — do not engage.
- B. Fully **mine** — manager performance work.
- C. **Out** to HR (formal process) **and mine** (manager-side framing — review standard, workload, pairing). Partner with HR; do not front-run.
- D. **Up** to `ai-engineering-manager` (L50) — it is above L40 because HR is involved.

## Question 10

Chapter 5 sets two tests for the manager's AI-fluency bar. Which pair of behaviours best indicates the bar is correctly set?

- A. You ship the most PRs on the team through Cursor, and you can open any eval report in LangSmith.
- B. You personally write the team's production agent code, and you commission the eval harness.
- C. You can open the team's main AI tool, run the workflow, and produce an artifact you would approve from an IC; and you are **not** shipping production PRs from the team's main workflow.
- D. You delegate all tool use to ICs and read only the final narratives; you never open the tools yourself.

---

## Answer key

1. **C.** Chapter 1 defines the L40 team as 5–30 ICs, with graduation to L50 triggered by *sub-managers reporting in*, not purely by headcount. At 22 ICs with no sub-managers, you are still in L40 scope. (Chapter 1, "The level-40 definition" and the 5–30 band.)
2. **C.** Chapter 1's three-altitude example assigns the IC the per-prompt regression work (L25), the enablement lead the org-wide procurement/comms (L45), and the L40 the team-operating-system catch-up — checklist, AGENTS.md, enablement session, re-cost, ROI update. (Chapter 1, "Three managers, three altitudes, one model upgrade.")
3. **B.** Chapter 2 is explicit that Grove/Fournier/Larson/Zhuo are the assumed baseline and are *not* re-taught; the track layers AI-augmentation moves on top. The list of things this track skips (1:1 structure, feedback structure, hiring process fundamentals, planning cadence, delegation theory, team-size heuristics) is in the chapter's "What this track does NOT re-teach" section.
4. **B.** Chapter 3 says the phrase is useful shorthand but not a usable contract; it compresses three decisions (C1/C2/C3) and leaves gaps — especially at the reviewer — that break under incident. ("AI generates, humans own" is the slogan; the contract is the system.)
5. **D.** Chapter 3's C3 stack puts the manager on the hook for the system — the standard, the enablement, the reviewer bandwidth, and the choice to use AI on this class of work in the first place. The IC and reviewer own their layer; the vendor owns their SLA.
6. **B.** Chapter 3 states the change log is "not optional" — it is the quarter-by-quarter record of how the team's AI posture matured and the audit trail against drift. ("What a workable contract looks like on the page.")
7. **C.** Chapter 4 names this exact ask as an "Up" route to `ai-enablement-lead` (L45) — pilot graduation and multi-team/org-wide scope — and uses it as one of the five Monday-morning examples.
8. **A.** Chapter 4's ambiguous-10% heuristic explicitly splits this: "if it's about engineering the guardrail, route to `ai-risk-engineer`; if it's about who is on the hook for what shipped, it is yours (`mod-109`)."
9. **C.** Chapter 4's fifth Monday example is this one: formal process is **out** to HR, manager-side framing is **mine** — partner, do not front-run.
10. **C.** Chapter 5's two-sentence bar: can you open the tool, run the workflow, and come out with an approvable artifact? And are you *not* shipping production PRs from the team's main workflow? Over the bar is out-shipping; under it is managing a system you cannot read.
