---
name: slack-writeups
description: Draft concise Slack status updates, decisions, stakeholder pings, launch announcements, live experiment updates, and asks for a specified audience. Route concluded A/B experiment readouts to skills/xp-analysis.md.
---

# Slack Writeups

## When to use this skill

Use when the PM wants a Slack draft for a status update, decision record, stakeholder ping, launch or heads-up announcement, live experiment update, or ask for input.

For concluded A/B experiments, use [experiment analysis](xp-analysis.md), which owns experiment-result messages. Do not duplicate those templates here.

## Inputs required

- Raw content: bullet points, a document, a paragraph, or a verbal description.
- The channel or audience. If neither the request nor available context establishes it, ask: “Which channel or who's the audience?”
- Any relevant document, experiment dashboard, or PRD link.

Follow `AGENTS.md` for context loading and source ownership. Use recorded audience preferences and decision owners from `context/current-quarter.md` when relevant. Do not invent names, channel names, links, dates, traffic allocations, results, or commitments. Mark missing details for confirmation.

## What to do

1. Identify the message type and audience.
2. Draft the whole message in one pass using Draft: full mode.
3. Lead with the point. The first line should tell a busy reader why to read and what, if anything, they need to do.
4. Match the register: technical for engineering audiences, business outcomes for business partners and leadership, and plain language for broader product audiences.
5. Use emoji sparingly and purposefully: one or two to signal type or status.
6. Make asks explicit, with a confirmed owner and date. Leave placeholders when either is unknown.

Produce a ready-to-review draft in the conversation. A request to draft does not authorize posting or messaging anyone.

## Message types and shapes

### Status update

For a team channel:

```text
:round_pushpin: [Project] update
Where we are: [One line]
Shipped / in progress:
- [Item]
- [Item, if needed]
Blocked on / need: [Name + what, or None if confirmed]
[Link, if available]
```

### Decision record

Make the decision searchable later:

```text
:white_check_mark: Decision: [What was decided]
Context: [One line on why this came up]
Decision: [The call, stated plainly]
Rationale: [One or two lines]
Owner / next: [Name — next action]
```

Use this shape for an actual decision. If it is a proposal awaiting approval, label it as proposed rather than presenting it as decided.

### Stakeholder ping

For a business partner, leader, or PM in another product area:

```text
[Business outcome or what the reader cares about — one line]
[One or two lines explaining what is happening and why it matters to them]
[Explicit ask or FYI: No action needed / Need your input on X by date]
[Link, if available]
```

### Launch / heads-up

```text
:rocket: [What's launching] — [When]
Who's affected: [Audience / allocation / product area]
What changes: [One or two lines]
Watch for: [Guardrail or thing to monitor]
[Link, if available]
```

Describe a launch as live only when the source confirms it; distinguish planned launches from completed ones.

### Company-wide experiment launch / live update

Use plain language for a nontechnical audience. Lead with the exact confirmed experiment identifier and live traffic percentage. Explain what is being tested and the user-facing change without model or architecture terminology. State success in business and experience terms, and name the scope explicitly.

```text
:rocket: [EXPERIMENT_NAME] is live at [X]% traffic.

This experiment in [product area] tests [change], based on [plain-language rationale or sourced prior evidence].

- Scope: [User groups or markets], [platforms]
- Success: [Primary outcome] without negatively affecting [business and experience guardrails]

[What users may notice. Mention unaffected behavior only when confirmed and useful.]
```

Keep internal model names out of the explanation; retain a technical name only when it is part of the supplied experiment identifier. Do not imply that a prior result generalizes to a new audience without evidence. If allocation or launch status is unknown, leave it for confirmation rather than claiming the experiment is live.

### Ask for input

```text
:speech_balloon: Need input: [Topic]
[One or two lines of context, just enough to answer]
Question: [Specific decision or opinion needed]
By: [Date] — [Person or group being asked]
```

## Style notes

- Use short sentences and one idea per line. Skip preambles such as “Hi team, just wanted to…”.
- For company-wide channels, explain the effect on users and the business in plain language.
- Avoid passive voice and executive summaries.
- Make clear what happened and what, if anything, the reader should do next.
- Name trade-offs between revenue, conversion, or other configured goals. Identify the relevant decision owner from context; do not invent a stakeholder or resolve an unowned trade-off silently.
- Ground every number in a supplied experiment, document, or named source. Label estimates and preserve links when available.
- Omit unused template lines rather than filling them with invented content.
