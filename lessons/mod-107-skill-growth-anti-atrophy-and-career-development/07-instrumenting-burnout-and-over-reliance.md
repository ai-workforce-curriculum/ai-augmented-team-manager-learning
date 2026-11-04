# Chapter 7 — Instrumenting Burnout and Over-Reliance via 1:1s and Retros

> *The engagement survey will tell you about the atrophy pattern eighteen months after you needed to know. The 1:1 and the retro will tell you about it next week — but only if the team feels safe enough to tell you and only if you have the vocabulary to hear it. Edmondson and Westrum are how you build the vocabulary; the prompts in this chapter are how you ask.*

## Motivation

Chapters 2–4 established *what* the atrophy risks are; Chapters 5 and 6 built the operational interventions. This chapter is the diagnostic layer: how a manager detects — early, routinely, without theatre — that the atrophy is forming on their specific team, and uses the detection to tune the carve-outs and the ladder.

The premise is that the right instrument is not a survey. Annual engagement surveys aggregate, lag, and anonymise; by the time the signal arrives it is too late and too blunt. The right instrument is the two conversations a team manager already runs every week: the 1:1 and the retro. The manager's job is to design the prompts in both so that deference, dependency, and burnout surface in conversation when they can still be acted on.

The diagnostic vocabulary comes from two canonical sources:

- [Amy Edmondson, *The Fearless Organization*](https://fearlessorganization.com/the-fearless-organization-book) and the [Edmondson 1999 ASQ paper, *Psychological Safety and Learning Behavior in Work Teams*](https://journals.sagepub.com/doi/10.2307/2666999) — the *psychological-safety* construct and the behaviours it enables.
- [Westrum, *A typology of organisational cultures* (BMJ Quality & Safety, 2004)](https://qualitysafety.bmj.com/content/13/suppl_2/ii22) — the pathological / bureaucratic / generative typology, used extensively in the DORA research.

Exercise 04 produces the working set of 1:1 and retro prompts. This chapter is the grounding.

## Core concepts

### Edmondson's psychological safety, at manager-fluency

Edmondson's construct, in one sentence: *psychological safety is the shared belief that the team is safe for interpersonal risk-taking — that one can speak up with a question, a concern, a bad idea, or a mistake without being punished or embarrassed.* It is distinct from and complementary to (a) accountability and (b) comfort — a high-performing psychologically safe team is both highly accountable and sometimes uncomfortable.

For this module, the construct is load-bearing for one specific reason: deference to AI output is often *silent*. An IC who defers to the AI without judgement, in a culture of low psychological safety, will not say so in their 1:1. They will not flag in retro that the AI is doing the work they used to think through. The deference is present; the signal is not. Without psychological safety, the atrophy hides.

The *behaviours* Edmondson's work predicts are present on a psychologically safe team — and which are the behaviours this module needs — include: candid admission of uncertainty (*"I don't know if this AI output is right"*), surfacing mistakes without defensiveness (*"I shipped this; the review missed something that in hindsight I should have caught"*), asking "why" questions of senior ICs and the manager without ritual (*"why is the routing on this task-type what it is?"*), and expressing a difference of opinion about a decision without positioning it as a complaint.

A manager who has not built psychological safety cannot run Chapter 5's carve-outs effectively — ICs will experience the AI-off artifact as a test, the paired-review as surveillance, the judgement question as an interrogation. The carve-outs produce the opposite of their intended signal.

### Westrum's culture typology, at manager-fluency

Westrum (originally writing about healthcare and aviation safety) distinguishes three kinds of organisational culture by how they handle information:

- **Pathological** cultures — *power-oriented*. Information is a political resource. Problems are hidden; messengers are punished; novelty is crushed. Responsibility is shirked and risks are not surfaced.
- **Bureaucratic** cultures — *rule-oriented*. Information travels through sanctioned channels. Problems are surfaced but the response is procedural compliance, not resolution. Novelty is tolerated in approved forms. Responsibility is narrow and territorial.
- **Generative** cultures — *performance-oriented*. Information flows freely toward whoever needs it. Problems are surfaced and investigated. Novelty is welcomed. Responsibility is shared across the mission.

The DORA research uses the typology as a predictor of software-delivery outcomes; the typology also applies cleanly to how a team handles the specific information class this module cares about: *"the AI got this wrong, and I noticed."*

In a pathological team, the IC who notices does not tell anyone — the information is dangerous to carry. In a bureaucratic team, the IC files the finding in a retro ticket that goes nowhere. In a generative team, the IC messages the senior IC within the hour, the senior IC reroutes the task-type, and the routing matrix updates by end of week. The three cultures produce three different atrophy outcomes from the same underlying event.

### Why the 1:1 and the retro, not the survey

Four reasons:

- **Cadence.** The 1:1 happens weekly; the retro happens per sprint or per fortnight. The engagement survey happens annually or semi-annually. The lag in the survey is the lag mod-107 explicitly cannot afford (Chapter 1's lagged-signal argument).
- **Attribution.** The 1:1 is attributed by construction — the manager knows who said what, which is exactly what you need to act specifically. The survey is anonymised, which is correct for its purpose (aggregate signal, free-expression safety) and wrong for this purpose (specific-signal, specific-response).
- **Follow-through.** The 1:1 permits the manager to follow up on a comment next week. The survey does not. If an IC says *"I've started accepting more AI suggestions than I used to"* in week 3, the manager can check back in week 6 — did the pattern change? The survey has no week-6.
- **Candour.** Edmondson's and the DORA/Westrum research both find that candour lives in the relationships where the person speaking trusts the person listening. The 1:1 is the primary site of that relationship on a functioning team. The survey is an abstraction.

The survey still has a role — aggregate-level culture measurement, cross-team comparison, trend-over-years — but it is the wrong instrument for the atrophy signal. Running it as the atrophy instrument is what this module means by *survey theatre*.

### The prompts, by category

Exercise 04 produces the full working set. This chapter sketches the four categories.

**Category 1 — deference prompts (addresses Dell'Acqua's channel).** Asked in 1:1s on a rotation, not every week. Variants:

- *"Walk me through a time this week you accepted an AI suggestion without changing it. What made it right to accept?"* The IC's answer either grounds the acceptance in judgement (*"it was a mechanical refactor, I've done hundreds, the diff looked right"*) or surfaces deference (*"it looked plausible and I was running short on time"*). The answer is diagnostic.
- *"Walk me through a time this week you rejected or modified an AI suggestion. What tipped you off?"* If the IC cannot name a single case over a month of 1:1s, the deference channel is likely active.
- *"On [specific outside-frontier task-type from the routing matrix] — do you feel you could do this without the AI if the AI were unavailable tomorrow? What would be harder?"* The honest answer here is where the Chapter 5 Carve-out 2 artifact gets scoped.

**Category 2 — dependency prompts (addresses Brynjolfsson's growth-path channel).** More appropriate in 1:1s with junior ICs; asked sparingly.

- *"What's one thing you're doing with AI today that six months ago you were doing yourself — and do you think you could still do it?"* The answer tells you whether the IC has an internal model of what they have delegated.
- *"What's one thing you've learned to do *with* AI that you couldn't have done at all before?"* This is the positive-growth version; the two together calibrate whether the AI is net-growing the IC or net-substituting.
- *"If the AI gave you a wrong answer right now, how would you know?"* A question Dell'Acqua's work directly motivates; the IC's answer is diagnostic.

**Category 3 — burnout prompts (addresses the Dell'Acqua "attention shift" and the Noy & Zhang over-work risk).** 1:1-appropriate, sparingly.

- *"What's the thing you're doing more of, now that AI handles the routine slice? Does it feel like better work or just different work?"* mod-106 Chapter 7's attention-shift risk; the IC's answer reveals whether the post-automation attention is going somewhere productive.
- *"What's the longest you've stared at an AI output recently before deciding what to do with it? Was the staring time cognitively expensive?"* The paradoxical finding in the field is that AI-mediated work sometimes *feels* harder because the IC is doing more judgement work and less producing — the question surfaces this.
- *"On a scale where 1 is 'I feel I'm coasting' and 5 is 'I feel I'm drowning' — where were you this week?"* Direct, under-specified, cheap. The number itself is less interesting than the direction of change week-over-week.

**Category 4 — retro prompts (team-level; added to the existing retro).** Asked quarterly or when the retro has capacity.

- *"Name one case this [quarter / sprint] where the AI suggested something and we made the judgement call to go another way. What made the judgement call work?"* The prompt builds the team's narrative muscle around judgement moves — the artifacts the mod-107 ladder (Chapter 6) will reward.
- *"Name one case this [quarter / sprint] where we accepted an AI output and later wished we hadn't. What was missing from the review?"* The blameless framing (mod-109) matters here — the prompt is not *who* accepted it, but *what review signal was absent*. The answer feeds the next quarter's Chapter 5 Carve-out 3 scope.
- *"On the three outside-frontier task-types in the routing matrix, which feels like our judgement is weakest? What would strengthen it?"* The team's own signal on which carve-outs to prioritise for the next quarter.

### What makes the prompts work

- **Specificity.** *"Walk me through a time"* is a stronger prompt than *"how do you feel about AI."* The specificity invites a narrative; the narrative surfaces the behaviour.
- **Non-judgemental tone.** The deference prompts can read as interrogative if the manager's affect is sharp. The right tone is *curious*, not *audit-like*. If the IC feels examined, the next week's prompt gets a performative answer.
- **Rotation.** Asking the same prompt every week produces survey-fatigue. The categories rotate; a given prompt is asked on a given IC's 1:1 maybe once a month.
- **Follow-through in the next 1:1.** *"Last week you mentioned you weren't sure if the AI's suggestion on X was right — did you get a chance to come back to it?"* The follow-through demonstrates that the earlier conversation was heard. It is also the single strongest psychological-safety signal in the manager's weekly repertoire.

### The hard conversation: an IC whose candour reveals a pattern

Composite example; treat as calibration. Over a month of 1:1s, a junior IC answers Category 1 and Category 2 prompts in ways that suggest a settled deference pattern — the IC cannot name a rejection of an AI suggestion, cannot describe a case where the AI was wrong and they caught it, and reports relying on AI for sub-tasks they used to do themselves (and does not seem concerned about it).

Three features of a good manager response:

- **Separate the behaviour from the person.** The IC is sincere. The *pattern* is a problem; the IC is not. The conversation names the pattern, not the IC's intent.
- **Use the ladder conversation to re-contextualise.** *"At your current level we expect you to accept AI suggestions when they're right. At the next level, the differentiator is judgement — being able to tell when they're wrong. Here is what growing on that axis looks like, and here is Carve-out 2 for this quarter."*
- **Keep the specific conversation inside the 1:1.** The conversation is not a performance improvement plan. It is a growth conversation. If the pattern persists over two quarters of specific interventions and no visible change — then and only then does the manager coordinate with the HR partner for the Chapter 8 handoff. The conversation is explicitly not a PIP at this stage.

### Common failure modes with the instrumentation

- **Turning the 1:1 into an atrophy audit.** Four categories, one prompt per 1:1 on a rotation — not four prompts per 1:1. The 1:1 is not about this module; this module is one thread in it.
- **Treating low psychological safety as the IC's problem.** It is the manager's problem. If ICs are not surfacing deference, the fix is not to ask the question louder — it is to repair the safety base. Edmondson's four-step practice (frame the work, invite participation, respond productively, acknowledge fallibility) is the right reading.
- **Using the prompts as a substitute for Chapter 5's carve-outs.** The prompts surface signal; the carve-outs intervene. A manager who runs the prompts without the carve-outs produces conversations that go nowhere.
- **Skipping retros because the team is on deadline.** The retro is the team-level signal for this module. A team that skips three retros in a quarter has broken the diagnostic layer. mod-112's ritual-calendar work is the defence — retros on the calendar, not retros when there is time.
- **Documenting the 1:1 content in a way that makes ICs stop telling you things.** 1:1 notes are a personal manager tool; sharing them with HR without the IC's knowledge or consent breaks psychological safety permanently. Chapter 8 is explicit on when and how to escalate.

### What the retro layer specifically adds

The 1:1 catches individual-level signal; the retro catches team-level signal. The team-level signal is where the Westrum culture typology shows up — in the retro you can observe whether the team is a generative culture around AI-wrong events, a bureaucratic culture, or (worst) a pathological one. The signs:

- **Generative signs.** A retro surfaces *specific*, named AI-wrong cases; the team discusses the decision without blaming the IC who shipped; the routing matrix or review standard gets amended by end of the retro; the next retro's prompts refer back.
- **Bureaucratic signs.** AI-wrong cases are mentioned in categories (*"we had a few issues with AI suggestions this sprint"*) without specifics; the retro assigns a generic action item that does not get followed; the next retro does not reference the current one.
- **Pathological signs.** AI-wrong cases are not mentioned at all, or mentioned only to be reassigned to the IC who shipped (*"IC X made a mistake"*); the retro's narrative is about blame; the deference pattern is both present and silent.

The manager's intervention when they see bureaucratic or pathological signs is not to run a culture-change workshop. It is to model the generative response in the next retro they attend — raise a specific case themselves, name their own role in the decision, and route it to a mechanism (routing matrix, standard, carve-out). The modelling is the intervention.

## Example: a month of rotated prompts for one IC

Composite calibration example; not a template.

- **Week 1 (deference, Category 1).** *"Walk me through a time this week you accepted an AI suggestion without changing it."* IC describes a mechanical refactor; the answer is grounded. Manager notes: judgement active on this task-shape.
- **Week 2 (follow-up on the carve-out schedule, not from the prompts above).** *"How did the AI-off artifact go? What did you learn about what the AI usually does for you?"* IC describes the comparison; the conversation is the deliberate-practice feedback step.
- **Week 3 (dependency, Category 2).** *"If the AI gave you a wrong answer right now, how would you know?"* IC describes a general heuristic (*"I'd check the tests"*); the heuristic is partial. Manager notes: probe this further on the next outside-frontier task.
- **Week 4 (burnout, Category 3).** *"What's the thing you're doing more of, now that AI handles the routine slice?"* IC describes doing more code review of other ICs' AI-assisted PRs and finding it tiring. Manager notes: possible attention-shift burnout; adjust the paired-review rotation next quarter.

Four prompts across four weeks, one minute of 1:1 time each. The month's answers compose into a picture that is neither alarming nor negligible — and which the manager can act on through Chapters 5 and 6, not through escalation.

## Summary

- The **diagnostic instrument** for the atrophy pattern is the 1:1 and the retro, not the engagement survey. The survey lags, aggregates, and anonymises; the signal mod-107 needs is immediate, specific, and attributed.
- Grounded in **Edmondson's psychological-safety construct** (the enabling condition for candid admission of deference) and **Westrum's culture typology** (the team-level predictor of how AI-wrong events flow).
- **Four categories of prompts:** deference (Dell'Acqua), dependency (Brynjolfsson), burnout (attention-shift and over-work), and retro (team-level). Rotated across 1:1s so a given IC sees one prompt per week, not four.
- **The prompts surface signal; the carve-outs (Chapter 5) and the ladder (Chapter 6) are the interventions.** Running the prompts without the interventions produces conversations that go nowhere.
- **The retro layer** adds the Westrum lens — a generative culture names specifics, names mechanisms, and refers back; a bureaucratic culture names generalities; a pathological culture names blame. The manager's intervention is to *model* the generative response, not to run a culture-change initiative.
- **Common failure modes:** turning the 1:1 into an audit; treating low psychological safety as the IC's problem; skipping retros under deadline; documenting 1:1 content in ways that break trust; using the prompts as a substitute for the carve-outs.
- **The hard case — a settled deference pattern — is a growth conversation, not a PIP.** Chapter 8 is explicit on when and how the manager escalates to HR if the pattern does not shift under two quarters of specific interventions.
