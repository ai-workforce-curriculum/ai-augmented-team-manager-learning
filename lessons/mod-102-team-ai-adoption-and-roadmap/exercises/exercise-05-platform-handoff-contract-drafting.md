# Exercise 05 — Platform Hand-Off Contract Drafting

**Estimated effort:** 3 hours.

## Objective

Draft the full **graduation package** for one pilot from your Exercise 02 sequence — either to Platform (shared mechanism) or to `ai-enablement-lead` (org-wide rollout) — and walk it past the relevant partner. The output is a three-to-five-page package plus artifact files, cross-linked and pinned, and a captured response from the partner. You are rehearsing the conversation now so that when the real graduation moment lands, the artifact is already shaped.

## Prerequisites

- Chapter 5 of this module.
- Exercise 01 (task sort) and Exercise 02 (pilot sequence and charters).
- A partner contact for the walkthrough — your Platform lead, your DevEx lead, or your `ai-enablement-lead`. Pick based on where the pilot would most plausibly graduate.
- The current state of your team's shared-infrastructure dependencies (which Cursor-rules deployment, which AGENTS.md convention, which MCP servers, which allowed-model list, which token-cost dashboard).

## Steps

1. **Pick a pilot.** From your Exercise 02 sequence, pick the pilot most likely to graduate — a successful pilot that either (a) built a mechanism a second team would reuse (candidate for Platform) or (b) is a reproducible workflow where the main scaling cost is enablement rather than infrastructure (candidate for `ai-enablement-lead`). State which type of graduation you are drafting.
2. **Simulate pilot completion.** For the chosen pilot, write a two-paragraph "end-state" sketch: what the week-N measurements look like, which success criteria cleared the bar, what would not clear. Be realistic — a graduation package for a pilot that marginally cleared is more honest than one that imagines a perfect outcome.
3. **Author the package, section by section.** The eight sections from Chapter 5:
   - **Pilot charter.** Copy from Exercise 02 unchanged.
   - **Evidence of success.** The measurements that landed against the committed criteria. Where any did not clear, state it honestly.
   - **Team-context signals.** Why this worked on your team. Team shape, tool surface, review bar, prior enablement, any team-specific context.
   - **ROI narrative.** One paragraph. Team-level now; scaled to the org in a second paragraph *if* this is a graduation to enablement lead. State assumptions.
   - **Enablement artifacts.** The Cursor-rules file, AGENTS.md, prompt library, review checklist, data-handling note, 30-minute onboarding deck — whatever the team used. Attach by reference; do not inline.
   - **Known risks and failure modes.** What nearly killed the pilot, what you watch for, what the kill criteria would catch.
   - **Hand-off decision and open questions.** What you are proposing and what you are leaving to the recipient to decide.
   - **Your continuing role.** Reference user; cross-team contributor; do-not-call; or time-bounded advisory.
4. **Cross-link.** Each section references the upstream artifact (task sort, charter, decision log entry). The package links back to your roadmap one-pager, and your roadmap one-pager links forward to the package in the decision log. Do the cross-linking as you write — adding it later is almost always skipped.
5. **Length check.** 3–5 pages plus the artifact files. If it is longer, you are describing a programme, not a hand-off. Cut.
6. **Walk the package past the partner.** 30 minutes. Share the package 24 hours ahead. In the meeting, ask three questions: *Is this the right destination?* *What is missing from the package?* *What is the recipient's capacity to take this on, and on what cadence?* Capture responses verbatim.
7. **Revise or log.** If the partner's feedback changes the package, revise. If the partner's feedback is a counter-argument you do not accept, log it in the decision log with your reasoning. Either response is legitimate; silence is not.

## Starter guidance

- The package is for a partner, not for a lawyer. Flat voice, specific, short. "We think this graduates to Platform because…" beats "it is our recommendation that this initiative transition to…"
- The honesty of section 2 (evidence of success) is the whole package's foundation. A package that overstates evidence poisons the hand-off; the recipient will discover the overstatement under scale.
- Section 3 (team-context signals) is the one most often skipped and the most useful. The recipient needs to know what to replicate and what is you-specific. A pilot that worked because a particular senior IC coached the cohort will not work without that coaching at scale — say so.
- Section 7 (hand-off decision and open questions) is where the rubber meets the road. State what you are proposing; state what you are explicitly *not* deciding. Ambiguity here produces the "who owns this?" emails three months later.
- Section 8 (your continuing role) must be explicit. If you want to be out of the loop after hand-off, say so. If you want a reference-user role, name the cadence. Silence defaults to "the manager is on the hook forever."
- The "no graduation this quarter" package is a valid output of the exercise. If the pilot's end state is "team-local, no graduation," write the one-paragraph note that documents the decision.

## Acceptance criteria

The deliverable is complete when:

- A pilot has been picked and tagged as a Platform-graduation or an enablement-graduation candidate (or explicitly a no-graduation documented decision).
- The eight sections are all present. No "TBD." No overstated evidence.
- Enablement artifacts are attached by reference.
- The package is 3–5 pages plus artifacts; longer sections have been cut to supporting docs.
- Cross-links are in place both ways: package ↔ roadmap, package ↔ charter, package ↔ decision log.
- A partner has reviewed the package; the response is captured, and the package has been either revised or the counter-argument has been logged.
- The "your continuing role" section names a specific cadence (reference-user monthly, time-bounded advisory for 4 weeks, do-not-call, etc.), not a vague commitment.

## Stretch goals

- Author both a Platform-graduation package and an enablement-graduation package for the same pilot, to force the comparison. In almost every case one is a better fit; writing both makes the fit explicit.
- Pre-write the *receive-side* perspective: what would the recipient's roadmap look like six months after accepting the hand-off? If that story is unclear, the hand-off is premature.
- Walk the package past a second partner, not the one who is the natural recipient. A partner adjacent to the destination will catch assumptions a direct recipient will not.
- Add a section 9: *What goes wrong if we do not graduate.* The null option is a legitimate part of the comparison.
- Map the package's success evidence to the DX Core 4 / SPACE / DORA metric family used across the org (see [`mod-104`](../../mod-104-productivity-measurement-and-ai-roi/)). Metric alignment to the enablement-lead's instrumentation accelerates the hand-off.
