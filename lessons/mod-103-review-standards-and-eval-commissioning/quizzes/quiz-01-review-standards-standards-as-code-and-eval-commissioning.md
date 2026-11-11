# Quiz 01 — Review Standards, Standards-as-Code, and Eval Commissioning

**Format:** 12 multiple-choice questions.
**Coverage:** All seven chapters of mod-103.
**Scoring:** 1 point per question. 9/12 is a pass. Below that, re-read the chapter named in the answer explanation before moving on.

Each question tests whether you can apply the chapter, not whether you can quote it. Pick the single best answer.

---

## Question 1

Your director says, *"Great — the tech lead can own the review standard for AI-generated code, and you just sign off."* Per Chapter 1, the strongest objection is:

- A. The tech lead cannot write a review standard without the staff engineer's input first.
- B. The posting language names the manager as the directly-responsible party for *owning* the standard and *rolling it out* — and it bundles the standard with the **accountability model**, which the tech lead cannot route. Delegating to the tech lead collapses R2 into a checklist-writing task and loses the rollout and accountability halves.
- C. Nothing — manager-signs-off-on-tech-lead-draft is the standard pattern across the postings.
- D. The standard belongs to `ai-risk-engineer` because it touches review; the manager-tech-lead argument is moot.

## Question 2

Chapter 1 argues that "LGTM" on a model-authored artifact compresses **five** distinct decisions. Which pair below is the one the chapter is most explicit about being *decisions* the manager must make explicit (rather than leave implicit for each reviewer)?

- A. "The reviewer liked the code style" and "the reviewer trusted the author."
- B. "The submitter read every line the model wrote" and "if the diff ships broken, the submitter and reviewer accept the regression (not the model)." The chapter says that a manager who has not decided which of the five is required for which artifact class has implicitly made them all optional; the checklist (Chapter 2) and the accountability contract (Chapter 5) are the operational forms of these two specifically.
- C. "The CI is green" and "the vendor is reputable."
- D. "The prompt was well-engineered" and "the reviewer is senior enough."

## Question 3

A reviewer on your team approves a model-authored PR in three minutes because "the diff was clean, tests passed, lint was green." Per Chapter 2, which section of the seven-section checklist is this reviewer most likely to be skipping *despite* the green signals?

- A. **Provenance** — they probably did not note which model version produced the diff.
- B. **Context fit** — the review question on a model-authored diff is specifically *does this match what the model could not see* (team norms, downstream consumers, in-flight teammate work, political context), and clean-looking diffs are the exact class where this gets skipped. Chapter 2 says review of model-authored work takes *at least* as long as a comparable human-authored review.
- C. **Verification run** — a green CI is sufficient proof of verification.
- D. **Accountability** — this is a signature line, not substantive review.

## Question 4

Chapter 2's per-artifact-class table lists several classes as *"not AI-drafted at all on most teams."* Which pair below is correctly on that list?

- A. Unit tests and SQL queries.
- B. PR descriptions and ADRs.
- C. **Employee feedback / promo / performance input** and **incident post-mortems** — the chapter is strict on both: if allowed at all, the manager rewrites end-to-end, and Chapter 5 is explicit on post-mortems.
- D. Runbooks and customer-facing error messages.

## Question 5

The PR queue has doubled since your team adopted an agent workflow. A senior IC proposes: *"Let's drop the Context-fit checkbox for small model-authored PRs so reviews don't back up."* Per Chapter 2's review-time-budget discussion, the correct response is:

- A. Agree — the budget is blown, so lower the bar on small PRs.
- B. **Throttle production**, not the bar — reduce the agent-authored-PR count per IC per day, require two submitters per model PR, or restrict the classes the model is allowed to draft. The queue is the team's defence against review-compression; the fast-path "it was drafted by a model" does not exist.
- C. Agree only if the small PRs are already type-checked and linted clean.
- D. Delegate the decision to the tech lead to avoid conflict.

## Question 6

A peer manager tells you, *"Our standards-as-code stack is a single `CONTRIBUTING.md`. It has every rule."* Per Chapter 3, the strongest critique is:

- A. `CONTRIBUTING.md` should be `AGENTS.md` instead because coding agents do not read the former.
- B. A standard that lives in a single file is caught at exactly one failure mode (review time, or author time, or commit time — not all three). Chapter 3 argues for a **layered stack** (Cursor rules → AGENTS.md → ADR template → lint / type / security linter → pre-commit → CI → PR template) because each layer catches a different failure mode. One file is a wiki page; a stack is a durable norm.
- C. `CONTRIBUTING.md` is deprecated in favour of `AGENTS.md` across the industry.
- D. Nothing — a single source of truth is best.

## Question 7

You are classifying which norms go into the standards-as-code stack and which stay in the human/machine contract. Which of the following is correctly identified by Chapter 3 as *out-of-stack* (i.e., stays in the contract, not in the toolchain)?

- A. Secret / credential / sensitive-data patterns.
- B. ADR requirement for non-trivial changes.
- C. **Accountability routing** (who is on the hook when something ships broken) and the **review-time budget** — the chapter says these are not tool-enforceable and belong in the social/contractual layer.
- D. The PR-template-field completeness gate.

## Question 8

A senior IC on your team offers to "just set up Promptfoo this weekend" so the team has evals running by Monday. Per Chapter 4's three framing questions (*Q1 what decision does this eval inform? Q2 who owns the harness? Q3 how does output feed back into team practice?*), the strongest response is:

- A. Say yes — any eval is better than no eval, and the IC's time is free.
- B. **Pause and answer the three framing questions first**, with the IC. Without Q1 attached to a team decision, the eval becomes a vanity metric; without Q3 naming a reader and a threshold, the loop is open; and the IC's offer needs to be grounded against Chapter 7's boundary — the manager commissions, with a named owner and co-owner in a brief.
- C. Redirect the IC to `ai-risk-engineer` because the manager cannot commission evals from their own reports.
- D. Build it yourself so the IC's time stays on product work.

## Question 9

Your harness owner reports that an LLM-as-judge eval of PR-description drafting hit a mean score of 4.3/5.0 on the 50-task golden set. Per Chapter 4, the single most important question to ask before trusting that number is:

- A. Which cloud region the judge ran in.
- B. **What calibration evidence does the judge carry against a human-rated sample?** A judge is a model; the G-Eval paper (Liu et al. 2023) reports Spearman correlations against human judgements as part of the method, and Chapter 4 says the commissioning brief must require the harness owner to report theirs. "The judge said 4.3" without calibration is a model-grading-another-model number, not a load-bearing number.
- C. Whether the judge's temperature was 0.0.
- D. Whether the dataset was stored on-premises.

## Question 10

An AI-produced artifact ships broken on your team. The reviewer who approved it asks, *"Was it my fault, or the IC's, or the model's?"* Per Chapter 5's four-party accountability stack, the clearest manager answer is:

- A. "The model is at fault — the vendor is on the hook via their SLA."
- B. "We don't assign fault; we do a blameless post-mortem and that's that."
- C. **"The IC is accountable for the submission, you are accountable for the approval against the stated bar, I am accountable for the system (standard, stack, commissioned evals, bandwidth, the C1 decision to permit AI authorship here), and the vendor is accountable for what their SLA says. That's four layers of accountability, not one — and none of them are blame. The post-mortem (per `mod-109`) is where the loop closes."**
- D. "The submitter and reviewer share accountability for the diff; the manager is only accountable if the vendor's SLA was breached."

## Question 11

Chapter 6's crosswalk deliverable is a *row-per-risk* table from the OWASP Top 10 for LLM Applications into three columns. Which column set below matches the chapter?

- A. Attack vector, exploit construction, red-team scenario.
- B. **Review-checklist section (Chapter 2), standards-as-code layer (Chapter 3), eval that catches regression (Chapter 4)** — with an explicit "out-of-scope + rationale" option for rows that do not apply at review-time altitude (e.g., LLM03 Supply Chain may legitimately be governance-time, not review-time, on your team).
- C. Severity, likelihood, residual risk.
- D. Vendor SLA, insurance coverage, legal opinion.

## Question 12

A VP asks, *"Who owns our LLM jailbreak-resistance?"* Per Chapter 7's boundary-in-one-sentence, your strongest answer is:

- A. "I do — it's a team-manager responsibility at level 40."
- B. "`ai-risk-engineer` does — I don't touch it."
- C. **"Red-team and guardrail depth sits with `@risk-engineer-peer` (`ai-risk-engineer`, L25, Governance family). I commission the work via a one-page brief, read the reports, and act on the findings in team practice. Would you like to see the current commissioning backlog, the most recent report, or the team-scope decisions we made because of it?"** The pattern: name both sides, name the artifact that connects them (the commissioning brief), invite follow-up.
- D. "The CISO owns it — it's an application-security concern."

---

## Answer key

1. **B.** Chapter 1 is explicit that R2 lands on the manager because the posting language says *own* and *roll out*, not *contribute to*, and because R2 bundles the review standard with the accountability model — which only a manager can route. Treating it as tech-lead work loses the rollout and accountability halves. (Chapter 1, "Why R2 lands on the manager and not on a senior IC.")

2. **B.** Chapter 1 enumerates the five decisions and says the checklist (Chapter 2) is the operational form of the "read, run, verify" subset and the accountability contract (Chapter 5) is the operational form of the "reviewer independently verified" and "submitter + reviewer accept the regression" subset. A manager who has not decided which is required for which artifact class has implicitly made them all optional. (Chapter 1, "'LGTM' is a decision about the system, not about the diff.")

3. **B.** Chapter 2 says the reviewer on a model-authored diff is answering a *different* question than on a human-authored one — *does this match what the model could not see?* — and clean-looking diffs are specifically the risk (models produce syntactically perfect code with logically wrong branches as standard). Context fit is the reviewer-judgment-heavy section where this catch lives, and the pagination example in the chapter illustrates it. (Chapter 2, "The question the reviewer is actually answering" and the pagination example.)

4. **C.** Chapter 2's per-class table names employee feedback / promo / performance input and incident post-mortems as *"not AI-drafted at all on most teams."* Chapter 5 reinforces post-mortems: if allowed at all, first draft only, human rewrites before publishing. Unit tests, SQL queries, PR descriptions, ADRs, runbooks, and customer-facing error messages are all on the list but with stated verification bars — they are not forbidden. (Chapter 2, "Verification requirements per artifact class.")

5. **B.** Chapter 2 is explicit: "If the team cannot review every model-authored PR to the stated bar in the stated budget, the response is *throttle production*, not *lower the bar*." Options include reducing agent-authored PRs per IC per day, requiring two submitters per model PR, or restricting the classes the model is allowed to draft. "There is no fast-path for 'it was drafted by a model.'" (Chapter 2, "The review-time budget is part of the standard.")

6. **B.** Chapter 3 argues for a seven-layer stack because each layer catches a different failure mode — Cursor rules at keystroke time, AGENTS.md at agent-task time, ADR templates at decision-authoring, lint/type/security linter at save/commit, pre-commit at `git commit`, CI at merge gate, PR template at review. A standard that only lives at one layer is either a wiki page or a disconnected code-quality rule. "A rule that lives in a wiki page is a rule the agents will not read." (Chapter 3, "Why 'norm + lint + PR template' is a stack, not a single file.")

7. **C.** Chapter 3's "What belongs in the standards-as-code stack and what does not" section is explicit: **in-stack** are testing requirements, lint/format/type rules, secret/credential rules, scope discipline, ADR requirement, PR-template-field gates, approved tool list. **Out-of-stack** are accountability routing (the social contract is not tool-enforceable), review-time budget, the *whether-may-AI-author* decision (C1), and incident response. Being honest about what the tools cannot enforce keeps the contract load-bearing. (Chapter 3, "What belongs in the standards-as-code stack and what does not.")

8. **B.** Chapter 4 opens with the three framing questions and says *"a commission that skips these questions is a procurement conversation dressed as an eval conversation. Answer them first."* Without Q1 (decision), the eval is a vanity metric; without Q3 (feedback loop), the harness produces a report nobody reads. Chapter 7 adds the boundary — this is commissioned work with a named owner and co-owner, not a weekend side-project. Chapter 7 Failure Mode A ("I'll build it myself") also applies. (Chapter 4, "Three questions before any tool"; Chapter 7, "Three failure modes on this boundary.")

9. **B.** Chapter 4's calibration caveat is explicit: *"a judge is itself a model. Calibrate it against human judgements on a sample before trusting its score — this is the single most common mistake with LLM-as-judge and the commissioning brief should require calibration evidence."* The G-Eval paper (Liu et al. 2023) reports Spearman correlations against human raters; the brief should require the harness owner to report theirs. "The judge said 4.3" is not a load-bearing number without calibration. (Chapter 4, "Shape B — LLM-as-judge (G-Eval shape)" and the commissioning-brief section item 5.)

10. **C.** Chapter 5's four-party stack: IC accountable for submission, reviewer for approval against the stated bar, manager for the *system* (standard, stack, commissioned evals, bandwidth, the C1 decision), vendor for what their SLA says. The ordering prevents the "it was the model" dodge at each layer. Accountability is not blame — Google SRE and Allspaw apply unchanged to AI-produced incidents, and the post-mortem (per `mod-109`) is where the loop closes with system changes. (Chapter 5, "The four parties on the hook" and "Accountability is not blame.")

11. **B.** Chapter 6's crosswalk has exactly those three columns: *review-checklist section (Chapter 2), standards-as-code layer (Chapter 3), eval that catches regression (Chapter 4)*, with an explicit out-of-scope + rationale option for rows that do not apply at review-time altitude. The chapter is clear that LLM03 Supply Chain and LLM04 Data and Model Poisoning may legitimately be governance-time rather than review-time; the *rationale* is the artifact for those rows. Red-team / exploit construction / severity are not the manager-scope columns — Chapter 7 is the hand-off. (Chapter 6, "The crosswalk table" and "A reading posture, not a certification.")

12. **C.** Chapter 7's boundary-in-one-sentence: *the team-manager commissions eval and risk evidence, authorises the scope, and acts on the findings in team practice; `ai-risk-engineer` builds the rig, runs it, and reports the evidence.* The two-sentence-script table in the chapter gives exactly this VP-facing answer, and the pattern — *name both sides; name the artifact that connects them; invite follow-up* — is drawable in one minute. "I do" (A) crosses into IC work; "I don't touch it" (B) abdicates commissioning; the CISO (D) is adjacent but not the primary owner. (Chapter 7, "The boundary, in one sentence" and "The two-sentence script for each cross-functional conversation.")
