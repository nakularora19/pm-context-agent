---
name: opportunity-scoping
description: Validate a problem, size an opportunity, and define a phased plan for a single opportunity or portfolio before writing PRDs.
---

# Skill: Opportunity Scoping

**Purpose:** Produce an opportunity scoping doc — the "why and what" document that validates a problem, sizes the opportunity, and lays out a phased approach to solving it. Written before any phase-level PRD.

**When to use:** When you have a problem signal (user feedback, data finding, engineering observation) and need to validate it, size it, and align stakeholders before writing requirements.

**Context dependencies:** Load `pm-profile.md` and `context/current-quarter.md` before running this skill. Company goals and KPIs are defined there.

**Inputs required:** A problem statement or raw signal (user feedback, data finding, engineering observation, etc.) to start from.

**Output:** A completed opportunity scoping doc. This becomes the input for `skills/prd.md` when moving into phase-level requirements.

---

## How to use this workflow

Infer this workflow from a request to validate or scope an opportunity; no special invocation is required. Follow `AGENTS.md` for context ownership and shared-document approval. Read the relevant linked project document when one exists; if access is unavailable, request the relevant content rather than assuming it.

Work through the sections in order. Do not skip ahead to solutions before the problem and proof points are solid. If the problem statement is weak or vague, sharpen it before continuing.

## Document structure and methodology

Draft Sections 1–7 in order, one or two sections at a time, and pause for the PM's review before continuing. Write Section 0 last and place it first in the final document. If the PM explicitly requests a full draft, produce it in one pass while preserving the evidence gate before the hypothesis.

Link to the parent strategy, roadmap bet, and relevant OKR when recorded in `context/current-quarter.md`. Flag missing parent links rather than inventing them.

**Single opportunity vs. portfolio.** Most scoping docs cover one opportunity with one phased roadmap, where each phase becomes a PRD. But some problems are large enough that solving them spins off several parallel initiatives, each with its own phase-level PRDs (e.g. a service migration running alongside a workflow redesign and measurement improvements). When that is the case, you are writing a *portfolio scoping doc*, not a single-opportunity doc. Decide which you are writing before you start:

- **Single opportunity:** one problem, one roadmap, phases that build on each other. Default.
- **Portfolio:** one problem umbrella, multiple initiatives that may run in parallel and each lead to phase-level PRDs. Use the portfolio variants noted in Section 6 (initiative-level sizing table) and Section 7 (initiative × phase execution table).

The section order and methodology below are the same for both; the portfolio case just adds an initiative dimension to sizing and roadmap.

---

### Section 0: TL;DR (write this last, place it first)

Every scoping doc opens with a TL;DR so a skimmer gets the whole story in one screen without reading the detail below. Draft it **after** the rest of the document is solid, then place it at the top. Everything after the TL;DR is detail for readers who want the evidence and the plan.

The audience is usually senior leadership. Write each narrative sub-section as **tight prose — one short paragraph of two to three sentences that flows**, not bullet fragments or note-form. Lead with the consequence, then the mechanics. No throat-clearing, no restating the header.

The TL;DR has exactly these sub-sections, in order:

- **Problem** — two to three sentences. Open with what it costs, then why it happens.
- **Why this, and why now** — two to three sentences on what de-risks the bet and what forces the timing (a hard dependency, a closing window, a compounding cost of waiting).
- **Opportunity sizing** — two to three sentences. Lead with the headline number, then its basis. Pull the top line from Section 6.
- **OKR impact** — one short paragraph covering **business** (movement on the north star KPI from `context/current-quarter.md`) and **user** (what materially improves for the person using the product). Use `Business:` / `User:` as inline lead-ins, not as separate bullets.
- **Phased roadmap** — drop in the **actual execution table** from Section 7 (phase, initiative, timeline, target), not a prose paraphrase of it. The table is the single source of truth; do not restate it in sentences.

Keep it tight. If a reader only reads this section, they should be able to state the problem, why it matters now, how big it is, who it helps, and how it's sequenced. Follow the TL;DR with a Markdown horizontal rule (`---`) and a separate “Details” heading.

---

### Section 1: Problem definition

Write a clear, specific articulation of the problem. One to three sentences maximum.

A strong problem definition:

- Names the specific user or stakeholder experiencing the problem
- Describes what is happening and what the consequence is
- Avoids implying a solution

A weak problem definition is vague, too broad, or already implies a fix. If it reads like a solution brief, rewrite it.

Establish who has this problem and what happens to them because of it. Ask only if the supplied context does not answer these questions.

---

### Section 2: Proof points

This section validates that the problem is real. List every signal you have that confirms the problem exists. Signals can be qualitative or quantitative.

Valid signal types:

- User feedback: direct quotes, support tickets, NPS verbatims, research findings
- Quantitative data: drop-off rates, error rates, low engagement metrics, funnel gaps
- Engineering feedback: known technical pain points affecting user experience
- Design observations: usability issues surfaced during research or reviews
- Commercial or partner feedback: signals from sales, account managers, or partners
- Internal user feedback: observations from people inside the company who use the product

Minimum bar: one strong, clear signal is enough to proceed. It does not need to be exhaustive. What matters is that at least one proof point is specific and credible, not that you have covered every source.

For each proof point, state: the source, what it shows, and why it is relevant to the problem.

If no strong proof point exists, flag this explicitly. Do not proceed to the hypothesis until the problem has at least one real signal behind it.

---

### Section 3: Hypothesis

One to two sentences only. State clearly what you believe will happen if you solve this problem and why.

A strong hypothesis:

- Takes a clear point of view. No hedging.
- Connects the solution direction to a specific outcome
- Is falsifiable: you could prove it wrong with data

Format to follow:

> If we [solution direction], then [expected outcome] because [reasoning].

A weak hypothesis is vague, covers multiple bets at once, or reads like a goal statement rather than a belief. Rewrite it until it takes a clear position.

---

### Section 4: Goal

One sentence. What does success look like at the project level?

This is not a metric. It is the outcome you are pursuing. The metric comes in the next section.

Example: "Help users complete their task without avoidable friction."

---

### Section 5: Success metrics

List the metrics that will tell you whether you achieved the goal. Pull from `context/current-quarter.md` for north star and supporting metrics where relevant.

For each metric, state:

- Metric name
- Current baseline (if known)
- Target or direction of movement
- Type: primary, guardrail, or secondary; identify secondary metrics used to monitor unintended effects

Keep this list short. Two to four metrics is usually right. If you have more than five, you are measuring everything and optimizing for nothing.

---

### Section 6: Opportunity sizing

This is where you make the case for why this is worth solving now. Connect the problem to the numbers.

Include:

- How many users are affected and how often
- What the current metric looks like and what it could look like if solved
- The downstream impact: what does a X% improvement in this metric mean for conversions, revenue, or retention? Reference the north star KPI from `context/current-quarter.md` to anchor this.
- Any time sensitivity: is there a reason to solve this now versus later?

Be specific with numbers. Use ranges only when evidence supports them, and state assumptions explicitly. If no defensible estimate exists, use TBD rather than inventing a number. Distinguish percentage-point changes from relative percentages. Sum only comparable estimates over the same time period; explain overlap and avoid double-counting.

**Quantified uplift table.** Wherever you can attach a number to the opportunity, present it as a table tied directly to the north star KPI, not as prose. Every row must show its basis so a reader can challenge the estimate:

| Phase / Initiative | Expected uplift (north star unit) | Basis |
|---|---|---|
| [Name] | [Estimate, or 0 by design for an enabler] | [Derivation, source, assumptions, and guardrail for an enabler] |
| [Name] | TBD | Not yet estimated |
| **Total quantified to date** | **[Sum of comparable, non-overlapping estimates]** | [Aggregation assumptions] |

Rules for the table:

- Use the north star's actual unit (e.g. additional completed tasks per week), not a generic "impact."
- Enablers and migrations that deliberately move no metric should say "0 by design" with the guardrail stated, not be omitted — that is a feature of the plan, not a gap.
- Unestimated initiatives stay in the table as "TBD" so the reader sees the full surface area, not just the parts you've quantified.
- Always show a "total quantified to date" line so the headline number in the TL;DR has a clear source. If every estimate is TBD, the total is "Not yet estimated", not zero. Zero by design applies only to an intentional enabler with a stated guardrail.

For a **single-opportunity** doc, the rows are phases. For a **portfolio** doc, the rows are initiatives (which may each span phases).

---

### Section 7: Phased roadmap

Lay out how you would approach solving this problem in phases. Each phase should represent a meaningful increment of value, not just a chunk of engineering work.

For each phase:

- Phase name (e.g. MVP, Phase 2, Phase 3)
- One sentence on what this phase delivers and for whom
- Key scope inclusions: what is in
- Key scope exclusions: what is explicitly out
- Dependencies or prerequisites
- Rough sizing if known (S, M, L or weeks estimate)

Each phase will get its own PRD using `skills/prd.md`. The scoping doc does not need to define requirements at that level.

Note: if a phase is small enough that requirements can be captured in a single ticket, state that explicitly rather than planning a full PRD for it.

Use an execution table with phase, initiative, timeline, and target for a single opportunity too, so the TL;DR can reuse the actual table without inventing dates. Mark unknown timelines and targets as TBD.

**Portfolio variant.** If you are writing a portfolio doc (multiple parallel initiatives), lead this section with an execution table mapping initiatives to sequencing before the per-phase detail:

| Phase / Initiative | What it delivers | Timeline | Target |
|---|---|---|---|
| 1a [Name] | [One line] | [Duration or sprint window] | [Target quarter or milestone] |
| 1b [Name] | [One line] | [Duration or sprint window] | [Target quarter or milestone] |
| 2a [Name] | [One line] | [Scoping window] | [Target quarter or milestone] |

Group initiatives into phases (Phase 1 = foundation/enablers, Phase 2 = iteration, etc.), make parallelism explicit (which initiatives run in the same sprint window), and call out which initiatives are hard dependencies for others. Then give the per-initiative detail (scope in/out, dependencies, sizing) using the bullet structure above. Each initiative links to its own scope; create a separate PRD for each substantial delivery phase via `skills/prd.md`, not one PRD combining multiple phases.

---

## Output format

Produce the scoping doc as a clean markdown document with the sections above as headers: the TL;DR (Section 0) first, followed by a divider, then Sections 1 through 7 as the detail layer. Use the document as if it will be pasted into a wiki or shared with stakeholders directly.

Tone: clear and direct. Write for someone who will read this without any prior context on the problem. No jargon, no filler, no passive voice.

Length: aim for one to two pages for a single opportunity. For a portfolio, keep the TL;DR to one screen and link to initiative detail rather than dropping essential evidence or dependencies to meet a page limit. Keep the strongest proof points and tighten sizing explanations.

---

## Notes for adapting this skill

- The proof points section is the most commonly skipped. Do not skip it. A scoping doc without validated proof points is a solution looking for a problem.
- The hypothesis must take a position. If it could apply to any project, it is too generic.
- The opportunity sizing section should always connect to the north star KPI in `context/current-quarter.md`. If you cannot draw that line, reconsider whether this is the right problem to solve right now. Use the quantified uplift table with an explicit basis per row — a number without a basis is not defensible in a prioritization conversation.
- The TL;DR is written last but read first. It is the section most stakeholders will actually read. If it cannot stand alone, the rest of the doc will not save it.
- Decide single-opportunity vs. portfolio up front. Forcing a multi-initiative program (a migration plus a workflow redesign plus measurement improvements) into a single linear roadmap hides the parallelism and the dependencies that matter most for planning.
- Each phase in the roadmap will become its own PRD using `skills/prd.md`. Keep phase scope tight enough that a PRD is achievable without becoming unwieldy.
