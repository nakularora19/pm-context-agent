---
name: prd-writing
description: Write a phase-level PRD from an aligned opportunity scoping document, covering requirements, success metrics, risks, and launch planning for one phase.
---

# PRD Writing

## When to use this skill

Use this after an opportunity scoping document is complete and aligned on, to write requirements for **one phase** of that project. Run once per phase, not once per project. If a phase is small enough to fit in a single ticket, write the ticket directly.

## Inputs required

- The completed opportunity scoping document for the project.
- Which phase this PRD covers. Ask if there are multiple phases and the intended phase is unclear.
- Relevant team constraints, stakeholders, and output preferences from `pm-profile.md`, `context/current-quarter.md`, and any additional context supplied by the PM. Read `context/team-charter.md` when decision rights or team scope matter.

Follow `AGENTS.md` for context ownership, conflicts, and shared-document approval. Read the linked scoping document live before drafting. If access is unavailable, ask for the relevant content rather than assuming what it says.

If team constraints or stakeholders are not recorded, proceed using the scoping document and mark what needs confirmation in Sections 7 and 8. Never invent capacity, lead times, reviewers, owners, dates, or metric values. Ask only when missing information would materially change the result.

## How to run it

Infer this workflow from a request to write requirements for a phase; no special invocation is required.

Draft section by section, in order. After each section, pause for the PM's review before moving to the next. Do not draft the full PRD in one pass unless the PM explicitly asks for a full draft upfront.

## Document structure and methodology

### Section 1: Phase overview

Three to five sentences covering:

- Which phase this is and what project it belongs to.
- What this phase delivers and for whom.
- How it fits into the broader phased roadmap from the scoping document.
- A reference to the parent scoping document.

This is the orientation for anyone reading the PRD without prior context.

### Section 2: Problem reminder

One to two sentences only. Restate the core problem from the scoping document in the context of this phase. Reframe it at the phase level rather than copying it verbatim. Keep requirements grounded in the user problem.

### Section 3: Goals and success metrics

Restate the phase-specific goal in one sentence. Then list the metrics for this phase from the scoping document. For each metric, confirm:

- Metric name.
- Baseline.
- Target or direction.
- Type: primary, guardrail, or secondary. Identify secondary metrics used to monitor unintended effects.

If this phase has experiment-specific metrics not in the scoping document, add them and flag them as phase-specific. Mark unknown baselines or targets as not recorded rather than supplying estimates without evidence.

### Section 4: Scope

**In scope:** List what this phase will deliver. Be specific; vague scope leads to late-stage disagreements.

**Out of scope:** List what this phase excludes. If something obvious is missing, explain why it is deferred.

**Open questions:** List unresolved decisions needed before or during build. Record an owner and deadline for each. If either is unknown, mark it as needing confirmation rather than inventing an assignment or date.

### Section 5: User stories and requirements

The core of the PRD. For each key user story:

- **User story:** As a [user type], I want to [action] so that [outcome].
- **Acceptance criteria:** Testable conditions that must be true for the story to be done.
- **Edge cases:** Scenarios outside the happy path that engineering needs to handle.

Group related stories by flow if the phase has multiple distinct flows. Keep requirements at the product level: describe what the experience should do rather than prescribing implementation details.

### Section 6: Design and UX notes

Reference any design files, prototypes, or research informing this phase. If designs are not ready, state what decisions are outstanding and who owns them, marking unknown ownership for confirmation. Flag UX constraints or non-negotiables. If no design work exists yet, say so explicitly rather than leaving the section blank.

### Section 7: Dependencies and risks

**Dependencies:** List everything this phase depends on outside direct control, such as other teams, infrastructure, third-party systems, review requirements, or data availability. State each dependency's owner and known lead time. Use recorded constraints from `context/current-quarter.md`; mark missing constraints, owners, or timing for team confirmation.

**Risks:** List the two to three things most likely to go wrong. For each, state likelihood, impact, and mitigation. Never list a risk without a mitigation; distinguish proposed mitigations from agreed commitments.

### Section 8: Stakeholder and launch plan

Who needs to be informed or involved before, during, and after this phase ships? Use the recorded stakeholder context and any list supplied by the PM. If stakeholders are unknown, ask when necessary or leave explicit role placeholders such as `[design lead — confirm owner]`.

For each stakeholder, state:

- When they are involved.
- What they need to know or approve.
- Who owns that communication.

Include a brief launch checklist covering what must be true before shipping, such as experiment setup, required sign-offs, communication drafts, and metric instrumentation. Do not imply that approvals or launch checks are complete without evidence.

## Output format

Produce a clean Markdown document with the eight sections above as headers, ready for review by engineering, design, and stakeholders.

Tone: precise and unambiguous. Every requirement should have one clear interpretation. If something could be read two ways, rewrite it.

Length: as short as possible while covering all eight sections completely. Cut anything that does not directly help the team build or decide.

Draft in the conversation first. Update a shared project document only after the PM approves the draft, following `AGENTS.md`.

## Notes for adapting this skill

- Run once per phase, not once per project.
- Section 4 open questions need owners; unknown owners must remain explicitly unconfirmed.
- Section 5 acceptance criteria must be testable. If QA cannot verify a criterion, rewrite it.
- If a phase fits in a ticket, write the ticket rather than a full PRD.
