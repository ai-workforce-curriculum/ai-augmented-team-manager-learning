# Exercise 03 — Human/Machine Contract, First Draft

**Estimated effort:** 3 hours.

## Objective

Draft the **first version** of your team's human/machine contract against the C1–C5 framework from Chapter 3. The output is a one-to-two-page document — not a policy memo, not a legal artifact — pinned to your team wiki and ready to review with your team in a dedicated 30-minute session. The goal is not to produce the final contract (that is a quarters-long iteration); it is to produce the artifact your team can *start arguing with*.

## Prerequisites

- Chapter 3 of this module.
- A clear sense of your team's current AI tool surface (which assistants, which agents, which tool connections, which classes of work they currently touch).
- Access to your organisation's existing AI policy, if any — team-scope translations do not contradict org policy.
- Done or in-flight: Exercise 01 (so you know the neighbours this contract hands off to) and Exercise 02 (so you know your manager-output baseline).

## Steps

1. **List the artifact classes your team ships.** Code, tests, docs, PR descriptions, ADRs, status updates, incident post-mortems, 1:1 prep, hiring materials, customer comms, dashboards, queries, analyses, and whatever else is specific to your team. One line per class.
2. **Fill in C1 — what AI may draft.** For each artifact class, mark: *AI may draft · AI may draft, review-only · AI may not draft*. The default **is not** "may draft." Make the decision deliberately; leave a short note next to any class that was contested with yourself.
3. **Fill in C2 — the verification bar per class.** For each class where AI may draft or may draft-review-only, write the minimum verification requirement: read every line, run / execute, check against source, judge for context. State the realistic review budget (time / effort) you expect a reviewer to spend. If the budget is impossible for the class ("ten-line commit encodes a three-hour judgment call"), demote the class in C1.
4. **Fill in C3 — the accountability stack.** Four lines: IC submitter, reviewer, manager (you), vendor. State each party's accountability in one sentence. Do not let any line read "the model."
5. **Fill in C4 — what we do when AI is wrong.** Five bullets: how to report, where to report, how to pull the artifact back, how to preserve the trace, how the finding feeds back into C1/C2. Point forward to `mod-109` as the longer-form incident flow.
6. **Fill in C5 — what AI may see.** Short list: data classifications your team handles, approved tool with approved enterprise tier, retention / opt-out posture of the vendor, secrets / credentials / PII rules. Link to the org DPA. If the org has no AI data-handling policy, flag that as a finding to route up to `ai-enablement-lead`.
7. **Assemble the artifact.** One-to-two pages, headings matching Chapter 3's list: *Scope · C1 · C2 · C3 · C4 · C5 · Change log*. The change log must contain at minimum one entry: v0.1, today's date, your name, "first draft."
8. **Pressure-test it against three scenarios.** Write a one-paragraph response, using the contract alone, to each:
   - An IC submits a PR with a model-drafted test that passes CI, and the reviewer approves it without reading the lines. In production, the test asserted the wrong behaviour.
   - An IC pastes a chunk of customer data into a non-enterprise AI tool to summarise it.
   - A reviewer argues that the model-authored ADR is "good enough" to skip the second-reader rule.
   If the contract does not resolve any of the three, revise it.

## Starter guidance

- The sample contract at the end of Chapter 3 is a sketch, not a template. Do not copy it; use it to calibrate length and tone.
- "AI may not draft" is a live option and often the right one. Promotions, compensation, employee feedback, legal-facing comms, and incident narratives are the usual candidates.
- Keep the contract readable to a non-engineer stakeholder. If a VP of operations cannot parse it in two minutes, shorten it.
- Do not invent a review budget longer than what your reviewers can actually give. Dishonest review budgets produce dishonest approvals.
- Do not promise what you cannot enforce. If C4 says "preserve the trace," the team has to have a way to preserve the trace — otherwise you are writing a wish list, not a contract.

## Acceptance criteria

The draft is complete when:

- All five commitments (C1 through C5) are explicitly filled in — no "TBD," no "we'll figure it out later."
- At least three artifact classes carry the *AI may not draft* marker, deliberately decided.
- The accountability stack names IC, reviewer, manager, and vendor by role (not by name).
- The data-handling section links to the actual org DPA / policy, or flags the gap if none exists.
- The three pressure-test scenarios each receive a one-paragraph response grounded in the contract.
- The change-log entry exists with today's date.
- Total length is one-to-two pages.

## Stretch goals

- Run a 30-minute review with your team against the draft. Capture at least three disagreements; revise to v0.2.
- Walk the draft to one neighbour — your governance analyst (L15), risk engineer (L25), or enablement lead (L45). Capture whether their view changes any line of the contract.
- Map each of C1 / C2 / C5 to the NIST AI RMF GOVERN sub-category and ISO/IEC 42001 clause it most closely corresponds to. (This is a `mod-110` skill; a rough first mapping is fine here.)
- Propose which lines of the contract will be encoded as standards-as-code in `mod-103` (Cursor rules, AGENTS.md, ADR template, lint policy, pre-commit hook, CI gate) rather than kept as prose.
