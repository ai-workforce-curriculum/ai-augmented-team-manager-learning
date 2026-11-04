# Exercise 07 — The Accountability Contract, v0.1

**Estimated effort:** 2 hours.

## Objective

Draft **v0.1 of the team accountability contract** — the pinned, team-signed document that specifies who is on the hook when AI-produced work ships broken and how the team routes, learns, and avoids blame. The deliverable is a one-to-two-page artifact that extends the C3 and C4 sections of the human/machine contract from [`mod-101`](../../mod-101-ai-augmented-team-manager-position-and-contract/) Chapter 3 with the operational depth from Chapter 5 of this module.

## Prerequisites

- Chapter 5 of this module.
- Chapter 3 of [`mod-101`](../../mod-101-ai-augmented-team-manager-position-and-contract/). The accountability contract extends C3 / C4 of your existing human/machine contract; if you do not have the parent contract at v0.1 yet, pause and draft it first (Exercise 03 of mod-101).
- Exercises 01–06 of this module. The contract references the checklist, the standards-as-code stack, the commissioning backlog, and the OWASP crosswalk.
- Read Google SRE *Postmortem Culture* (<https://sre.google/sre-book/postmortem-culture/>) and John Allspaw's *Blameless Post-Mortems* (<https://www.etsy.com/codeascraft/blameless-postmortems/>) before starting. The vocabulary carries over to AI-produced incidents unchanged.

## Problem statement

"AI generates, humans own" is the slogan. The contract is the system. The contract makes four assertions explicit — who is accountable for the submission, for the approval, for the system, and for the vendor SLA — and attaches each to specific operational behaviours (trace preservation, incident channel, time windows, post-mortem norms).

You will author a single document — `/docs/accountability-contract.md` or equivalent — that your team can point at *before* any incident and that the `mod-109` runbook can plug into when one happens. The document is signed off by the team-manager (you) and reviewed by your Platform or `ai-risk-engineer` peer.

## Steps

1. **Start from the C3 / C4 sections of your mod-101 human/machine contract.** Copy the existing text if any; this exercise extends it, does not replace.
2. **Name the four parties explicitly** and the accountability each carries. Do not use generic phrasing — name roles (IC, reviewer, manager, vendor) and, where it matters, the specific human or team.
3. **Specify what the IC is on the hook for.** One paragraph. The submission; using the agent and the prompt and the retrieved context; clicking submit. "The model wrote it" is not a defence.
4. **Specify what the reviewer is on the hook for.** One paragraph. The approval against the Chapter 2 verification bar (link to Exercise 01's PR template). The reviewer's accountability is for *having performed the review*, not for omniscience.
5. **Specify what the manager (you) is on the hook for.** One paragraph. The standard (Exercise 01); the standards-as-code stack (Exercises 02–03); the commissioned evals (Exercises 04–05); the OWASP crosswalk (Exercise 06); the reviewer bandwidth; the decision to permit AI authorship on each artifact class this quarter.
6. **Specify what the vendor is on the hook for.** One short paragraph. The SLA — availability, documented behaviour, published guardrails. The vendor is not accountable for your choice of use.
7. **Write the "When AI is wrong" play.** A numbered list, five to seven steps, covering:
   - Pull back / correct forward.
   - Report in a named channel within a named time window.
   - Preserve the trace — specify the fields (prompt, model + version, tool-authorisation surface, retrieved context, as-submitted artifact).
   - Run a blameless post-mortem within one week (hand off to [`mod-109`](../../mod-109-accountability-incident-response-and-blameless-postmortems/)).
   - Feed learning back into the four artifacts (checklist, stack, commissioning, crosswalk).
   - Publish the write-up blamelessly within two weeks.
8. **Write the "We do not practise blame" paragraph.** Cite Google SRE and Allspaw. State the team's stance: role-attribution, system-level improvements, no punitive consequences for surfacing a fault.
9. **Make the manager's *not-on-the-hook* explicit.** A short section naming what the manager is *not* accountable for — the specific line-by-line correctness of every model-authored diff, the behaviour of a vendor model version shipped without notice before a regression gate was added, a vendor outage under SLA. This prevents the "manager on the hook for everything" burnout pattern.
10. **Write the OWASP + governance hand-off paragraph.** The C4 trace fields map to several OWASP Top 10 rows (LLM01, LLM02, LLM06, LLM07, LLM09 among them); the team-scope evidence rolls up through [`mod-110`](../../mod-110-ai-governance-and-policy-at-team-scope/) to the governance crosswalk. Point readers to the mapping document (Exercise 06) and the governance snippet (mod-110's exercise set).
11. **Add a change log.** Date, author, reason for every revision. v0.1 gets dated today.
12. **Review with a peer** — your Platform lead, your PM peer, or your `ai-risk-engineer` peer. Fifteen minutes. Specifically ask: *"If I handed this to a VP, can they read it in five minutes and know what the team does? If I handed it to a new IC, do they know who is on the hook on their first AI-authored PR?"*
13. **Sign and pin.** Pin the document in the team wiki next to the human/machine contract. Reference it from the PR template's Accountability section (Exercise 01).

## Starter guidance

- Keep the document short. One to two pages. A six-page contract will not be read on the morning of an incident.
- Do not name individuals in the contract where naming a role is sufficient — "the on-call reviewer" rather than "@sam"; "the team-manager" rather than "@you." The roles survive the people rotating; the document stays useful.
- The *not-on-the-hook* section is the one managers most often skip. Including it is itself a signal of thoughtfulness — a VP reading this will notice whether you have drawn the line between system-accountability and over-ownership.
- Resist adding punitive language. Even phrases like "the reviewer is responsible if …" shade toward blame; prefer "the reviewer is accountable *for the approval itself*." Google SRE and Allspaw are precise here for a reason.
- The trace fields in step 7 should be specific enough that a new IC could enumerate them from the document. Vague phrasing ("preserve relevant context") will produce incomplete traces when the pressure is on.
- The contract is a living document. v0.1 is the kick-off; expect v0.2 after your first real AI-produced incident, and a quarterly refresh otherwise. The change log is the visible record of the team's AI-accountability maturity.
- This contract is the artifact a hiring-loop candidate (per [`mod-108`](../../mod-108-hiring-performance-and-feedback-with-ai-in-the-loop/)) and a governance partner (per [`mod-110`](../../mod-110-ai-governance-and-policy-at-team-scope/)) can both read in five minutes. Write it for both.

## Acceptance criteria

The contract is complete when:

- A single document (`/docs/accountability-contract.md` or equivalent) exists at one to two pages.
- The four parties (IC, reviewer, manager, vendor) are named with one paragraph of accountability each.
- The "When AI is wrong" play has five to seven numbered steps including the specific trace fields to preserve.
- The "We do not practise blame" paragraph cites Google SRE and/or Allspaw and names the role-attribution and system-improvement stance.
- The "manager is *not* on the hook for" section is present and names at least three specific things.
- The document references Exercises 01–06 of this module (checklist, stack, commissioning, crosswalk) and the human/machine contract from mod-101.
- A peer review has been performed and feedback either reflected or logged.
- The document carries a title, date, authorship, and a change log with at least the v0.1 entry.
- The PR template from Exercise 01 references this document in its Accountability section.

## Stretch goals

- **Incident reconstruction exercise.** Pick a hypothetical AI-produced incident on your team (or adapt a real one from a public source like the AI Incident Database, <https://incidentdatabase.ai/>, or OECD.AI Incidents Monitor, <https://oecd.ai/en/incidents>). Walk it through the contract. Does v0.1 handle it? Where does it bend?
- **Blameless-post-mortem template.** Draft the AI-specific post-mortem template that [`mod-109`](../../mod-109-accountability-incident-response-and-blameless-postmortems/) will formalise. Name the sections: expected, actual, system questions, root causes (plural — Allspaw on multiple-root-causes), remediation, changes to the four artifacts.
- **Trace-fidelity audit.** On the next AI-authored PR that ships this week, confirm you could reconstruct the C4 trace fields after the fact. If not, identify which fields are not being preserved by your tooling and make the fix. Pair with Exercise 02 / 03 for the mechanical side.
- **Governance roll-up.** Translate your accountability contract into one paragraph of team-scope evidence for your team's quarterly governance snippet. Hand to your governance partner or `ai-governance-analyst` peer. Pair with [`mod-110`](../../mod-110-ai-governance-and-policy-at-team-scope/).
- **Signature ritual.** Decide how the team signs the contract. Options: everyone signs v0.1 as part of a kickoff meeting; the manager signs and the team acknowledges via a Slack thumbs-up; the contract is git-versioned and every revision requires reviewer approval in the repo. The ritual matters — a contract no one has explicitly acknowledged is weaker than one they have.
- **Public publication.** Scrub your contract of team specifics and publish it as a generic template. The field benefits from more public team-scope accountability contracts. Pair with [`mod-112`](../../mod-112-cross-functional-leadership-and-ritual-calendar/).
