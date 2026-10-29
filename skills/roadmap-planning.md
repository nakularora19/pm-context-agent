---
name: roadmap-planning
description: Build or refresh a one-screen Now / Next / Later product roadmap of outcome-framed bets linked to OKRs for one planning period and area.
---

# Roadmap Planning

## When to use this skill

Use once per planning period per area, and refresh as bets move between horizons. This workflow sits below the strategy document and its OKRs, and above opportunity scoping documents. Keep the roadmap to one screen: it decides which problems earn discovery time, not how to solve them.

## Inputs required

- The strategy document and current-period OKRs.
- Candidate problems from discovery, data, and stakeholders.
- A rough capacity picture for the period.

Follow `AGENTS.md` for context loading, source ownership, and shared-document approval. Use `context/current-quarter.md` for recorded OKRs and constraints, and `context/now.md` when checking active work. Read the linked strategy document when available; if access is unavailable, ask for the relevant content. Flag missing strategy, OKRs, evidence, or capacity rather than inventing them.

Infer this workflow from a request to build or refresh a roadmap; no special invocation is required. Use Draft: sectioned, pausing for review before continuing unless the PM explicitly requests a full draft.

## What the document contains

A Now / Next / Later board, organized by confidence rather than dates. Each entry is a bet or initiative and needs only:

- **Name:** The outcome or problem, never a feature. For example, “Help users complete their task successfully” rather than “Ship a redesigned interface.”
- **Maps to:** The objective or key result it serves. The commitment lives on the objective, not the feature.
- **Owner:** The recorded owner, or an explicit placeholder for confirmation.

Horizons:

- **Now:** Validated and actively being worked on.
- **Next:** A clear problem that is still being validated.
- **Later:** A bet not yet explored.

Confidence rises from Later to Now. The columns encode confidence, so dates and sizing are not required on every row. Use available evidence and capacity to support placement; flag uncertainty rather than implying a bet has been validated or staffed.

Enabler and platform bets still name the outcomes they enable, such as consistency, reliability, or delivery speed, so they can be prioritized against user-facing bets.

Keep a one-line **Parked** note for anything excluded, with the reason.

## Output format

Produce a Markdown table or board that fits on one screen, with outcome-framed titles throughout. A compact board can use this structure:

| Now | Next | Later |
|---|---|---|
| [Outcome] · [Objective / KR] · [Owner] | [Outcome] · [Objective / KR] · [Owner] | [Outcome] · [Objective / KR] · [Owner] |

**Parked:** [Bet — reason].

Detailed scope belongs in each bet's linked opportunity scoping document, not on the roadmap. Link the bet name to its scoping document when one exists; mark a missing document rather than inventing a link. For a bet with multiple scoping documents, keep their mapping in the project index or linked portfolio scoping document without expanding the board into detailed plans.

Draft in the conversation first. Update a shared roadmap only after the PM approves the draft.

## Notes for adapting this skill

- Each bet becomes an initiative with one or more linked opportunity scoping documents. Use multiple documents when the bet spans distinct opportunities; preserve the one-to-many mapping.
- Horizons encode confidence, not time. Do not add implicit dates or delivery commitments.
- Each bet links to the objective or key result it serves. If it maps to none, flag it for removal or reframing; do not invent an OKR connection.
- A planning period defines the review context, not a delivery date for every bet.
- Keep per-bet requirements, phases, and sizing in the scoping documents and phase-level PRDs.
