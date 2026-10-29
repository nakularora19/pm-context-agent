---
name: meeting-notes
description: Capture, structure, and file meeting notes linked to project and quarterly context, or recall decisions and commitments from existing notes.
---

# Meeting Notes

## When to use this skill

Use when the PM:

- Provides raw notes, a transcript, or a verbal recap and wants it filed.
- Asks what a past meeting decided or what someone committed to.

Capture notes once, structure them, and link them to the projects and quarterly context they touch so future scoping, PRDs, and stakeholder work can use the record.

Keep it simple. Notes live as dated Markdown files in [Notes/](../Notes/), indexed in [Notes/README.md](../Notes/README.md). Real meeting content belongs only in the PM's private working copy, following `AGENTS.md`.

## Inputs required

- Raw notes, transcript, or recap. Messy is fine.
- Meeting date, plus the topic and attendees when available.

Use today's date only when the PM explicitly identifies the meeting as today's, using their timezone. Otherwise ask for a missing or ambiguous meeting date before filing; do not substitute the filing date for the meeting date. Never invent attendees or owners.

Follow `AGENTS.md` for context loading and source ownership. If the current repository is still the public template, structure the draft in the conversation and establish a private destination before writing real notes into it.

## Filing a new note

1. **Structure the raw input** using the format below. Capture what was said and decided rather than adding opinions or recommendations to the record.
2. **Extract decisions and actions separately.** Every action needs an owner and, where stated, a due date. Mark missing ownership as “Not recorded — needs confirmation” and missing due dates as “No date set.” Distinguish proposals from decisions, and suggested actions from agreed commitments.
3. **Link to context.** Identify related active projects in [current-quarter.md](../context/current-quarter.md#active-projects) and the [project index](../ProjectScopingDocs/index.md). Use recorded project-document links; do not invent links or claim to have read inaccessible documents. If a decision changes live status, identify [now.md](../context/now.md); if it changes a quarterly goal or constraint, identify current-quarter.md. Offer the relevant context updates without applying them silently.
4. **Write the note** to `Notes/YYYY-MM-DD-<short-topic>.md` in the private working copy. Use a short, descriptive topic slug. If that filename already exists, inspect it and avoid overwriting a different meeting; use a distinguishing suffix when needed.
5. **Insert an index entry** below the introduction in Notes/README.md, keeping entries ordered by meeting date, most recent first. Use `- [YYYY-MM-DD — topic](YYYY-MM-DD-<short-topic>.md) — key decision/action in 10 words or fewer`. Use the actual filename if a suffix was needed. Avoid duplicate entries when updating an existing note.
6. **Report back** with the note path, decisions, actions with owners, and any project or quarter context that should change. Update those other context files only after the PM confirms, unless the request already explicitly authorized the specific updates. Shared-document writes follow the draft-approval rule in `AGENTS.md`.

Use Draft: full mode: structure and file the whole note in one pass once the date and private destination are established. The PM can edit once.

## Note file format

```markdown
# [Topic] — YYYY-MM-DD

**Attendees:** [Names, or Not recorded]
**Related projects:** [Recorded project-document links or local context entries, or Not recorded]

## Decisions

- [Decision stated plainly; decision owner when recorded. If none: No decisions recorded.]

## Actions

- [ ] [Agreed action] — **Owner:** [Name, or Not recorded — needs confirmation] — **By:** [Date, or No date set]

## Notes / discussion

- [Substance of the discussion, grouped by topic if long. Keep verbatim quotes only when exact wording matters.]

## Open questions raised

- [Unresolved question or ownership that needs confirmation.]
```

Use explicit “None recorded” entries for empty sections rather than leaving template instructions in a filed note. Resolve local links relative to the note file, not the workflow file.

## Recalling decisions and commitments

When the PM asks about a past meeting:

1. Search Notes/ and its index for relevant records.
2. Answer from the **Decisions** and **Actions** sections first.
3. Cite the note file supporting each decision or commitment. Distinguish recorded commitments from discussion or proposals.
4. If records conflict, surface the conflict and dates rather than assuming a later discussion superseded an earlier decision.
5. If nothing is filed, say so plainly. Do not reconstruct a decision from memory or imply a search found evidence it did not.

Recall is read-only unless the PM asks to change the record.

## Style notes

- Decisions and actions are the main output. Keep supporting discussion concise.
- Do not invent attendees, dates, owners, commitments, or decisions. Flag missing information.
- Surface agreed trade-off decisions and stakeholder commitments in Decisions. Keep unresolved trade-offs under Open questions rather than presenting them as settled.
- Use configured decision owners and metrics from context rather than hard-coded stakeholder names or business assumptions.
