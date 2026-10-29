---
name: xp-analysis
description: Analyze a concluded A/B experiment using platform results and a project scoping document, producing a detailed analysis, plain-language summary, and outcome-specific Slack draft.
---

# XP Analysis

## When to use this skill

Use for a concluded A/B experiment when the PM provides:

- Experiment platform results: readable screenshots or an equivalent export showing the recommendation, metric results, and available uncertainty estimates.
- A project context or scoping document explaining what was tested and why.

If either input is missing or unreadable, ask for it before forming a conclusion. Do not guess at metrics or context.

Follow `AGENTS.md` for context loading and source ownership. Read the linked project document live, or request its relevant content if access is unavailable. Use `context/current-quarter.md` for configured KPIs, guardrails, constraints, and decision owners. Flag conflicts with the experiment configuration rather than silently choosing metrics.

## What to do

### 1. Read the platform's top-level assessment

Extract experiment status, traffic allocation, recommendation, and explanation before interpreting metrics. Preserve the platform's labels and explain them in plain language. Distinguish operational status, analytical recommendation, and the team's actual decision; none establishes the others.

If a field is unavailable, say so. Do not infer rollout status from a recommendation.

### 2. Identify the primary metric

Identify the metric explicitly designated as primary for this run. Report its name, relative percentage difference, and the platform's status or significance label. Include the confidence level when supplied. One line per primary metric is usually enough; do not transcribe the entire platform table.

Use these default terms throughout the analysis:

- **Primary metric:** The outcome the experiment aims to improve.
- **Guardrail metrics:** Outcomes that must not worsen beyond agreed limits.
- **Secondary metrics:** Supporting signals that help explain the result.

If the platform uses labels such as “Hypothesis Metric” or “Overall Evaluation Criterion” (OEC), establish their configured meaning and map them to the appropriate metric role. OEC is not automatically a guardrail or a separate metric. Preserve the source label in parentheses only when it helps readers reconcile the analysis with the platform. Do not count a metric appearing in multiple tables as independent evidence.

If primary metrics are unclear or conflict with the scoping document, resolve the ambiguity before recommending an outcome.

### 3. Evaluate guardrail and secondary metrics

For each configured guardrail, report its metric name, agreed limit, relative or absolute difference as appropriate, and status against the configured decision rule. Mark missing limits or results as unavailable.

Report relevant secondary metrics with their direction, magnitude, and uncertainty. Use them to explain the result; do not promote a favorable secondary metric to the primary success criterion after seeing the data.

An inconclusive result means the available evidence does not establish the tested effect. It does not prove equivalence, no harm, or a cleaner experience without trade-offs. Claim a guardrail passed only when the configured decision rule supports that conclusion.

Cross-check relevant supporting metrics from quarterly context. Flag negative guardrail movements even when not significant, while distinguishing an observed movement from a confirmed regression or breached threshold. Mark unmeasured guardrails as unavailable.

### 4. Call out key business metrics

For business metrics relevant to this experiment, report control versus variant values, absolute difference, and relative percentage difference where supplied or computable. Include both per-user and aggregate measures when available and meaningful. Preserve units, currency, population, and time window.

Revenue is an example, not a required primary metric. Attribute each figure to the table and metric role shown by the source. Do not automatically label revenue as the primary metric or duplicate the same result as independent evidence.

Distinguish percentage-point changes from relative percentages. Do not compute relative change from a zero baseline. Do not compare aggregates as causal effects without accounting for allocation, exposure, and the platform's estimation method.

### 5. Report estimated impact at the requested cadence

If the platform provides estimated impact at full rollout, preserve that qualification. A projected impact does not mean the experiment has already been rolled out.

When the source reports a daily estimate and a weekly presentation is appropriate:

- Weekly incremental outcome = daily incremental outcome × 7.
- Weekly incremental revenue = daily incremental revenue × 7, when revenue is relevant and available.
- Scale both bounds of the corresponding interval by 7 as well.

This is a unit conversion assuming the daily rate applies across the week, not a new forecast or evidence of significance. Preserve the source's population and rollout assumptions. Do not scale a cumulative total, percentage, per-user rate, or already-weekly value this way. Do not rescale traffic allocation unless the source method supports it.

State the interval type and confidence level when provided. For a matching two-sided confidence interval for a difference, exclusion of zero supports significance at that interval's stated level; inclusion of zero does not. Do not apply this rule to an unlabeled interval, ratio interval, or a different statistical framework. Preserve platform adjustments and inconclusive labels. Flag discrepancies rather than overruling the platform from incomplete screenshots.

If the estimate or uncertainty is missing, report it as unavailable; do not infer significance or fabricate impact.

### 6. Summarize the experiment context

From the scoping document, extract:

- The problem and opportunity.
- The solution tested, including UX, messaging, feature, or model changes as relevant.
- The hypothesis.
- The audience, eligibility, allocation, and requested segment cuts.

Distinguish traffic allocation from the prevalence of the underlying user problem. Analyze specified segments only when data is available; mark unavailable cuts rather than inventing them.

### 7. Determine the outcome and recommend an action

Use the platform recommendation, primary result, guardrails, estimated impact, and project hypothesis together. Explicitly classify the result as **win**, **loss**, **neutral/inconclusive**, or **retest proposed/agreed**, explaining the basis and remaining uncertainty.

- **Win:** Evidence supports the intended improvement and the configured guardrail decision criteria permit rollout. Recommend rollout only when justified; distinguish the recommendation from an approved commitment.
- **Loss:** Evidence shows a material negative outcome or a breached guardrail. Explain the basis for recommending rollback or iteration.
- **Neutral/inconclusive:** The intended effect is not established. A platform recommendation to confirm may coexist with inconclusive metrics; explain that combination without presenting it as proof of safety or benefit. A UX-based rollout requires an explicit rationale, guardrail review, and decision-owner alignment.
- **Retest:** An inconclusive overall result may support a targeted follow-up when a segment signal has a plausible hypothesis. Label exploratory segment findings and account for multiple comparisons, sample size, and power limitations. A directional segment is not a proven win and does not guarantee a significant rerun. Distinguish a proposed retest from one the team has agreed to or launched.

Take a position when evidence supports one. Otherwise state what additional evidence or decision is needed. Name unresolved trade-offs and their recorded decision owners.

### 8. Produce all three outputs

Use Draft: full mode. Produce the three sections below in a single response, in order. Drafting does not authorize posting to Slack or updating a shared document.

## Output format

### Section 1: XP Analysis

Write one or two short paragraphs covering, in order:

1. Platform status, recommendation, and explanation.
2. Primary metric result.
3. Guardrail results and relevant secondary metric findings.
4. Relevant per-user and aggregate business metrics, attributed to their actual roles.
5. Estimated weekly impact, if available, with units, uncertainty, and significance.
6. Recommended action, material surprises, and unresolved issues.

Keep the narrative concise. Use a compact table only when needed to make several values or variants readable. Cite the supplied source for claims and label derived calculations.

### Section 2: High-Level Summary

Explain what was tested, why, the audience and allocation, key learning, and outcome for someone unfamiliar with the experiment. Separate observed results from recommendations and confirmed next actions.

### Section 3: Slack Summary

Draft a concise message for the supplied experiment-results audience. Use short sentences, sparing emoji, and a clear explanation of the user-facing change. Choose the relevant template and adapt it to the evidence and confirmed decision.

The brackets below are template fields. Use verified input values; if a required field is missing, ask or mark the draft as needing confirmation rather than inventing a value. Omit optional lines without data.

#### Win

```text
:rocket: Experiment win: [EXPERIMENT_NAME]
[What improved for users and how it supports the hypothesis.]

Key highlights:
- [Primary metric: effect, uncertainty or significance]
- [Guardrail findings]
[Confirmed next action, or explicitly labeled recommendation]
[Source link, if available]
```

#### Neutral / inconclusive

```text
:bar_chart: [EXPERIMENT_NAME] — inconclusive
We tested [change] to address [problem] for [audience].

- Primary metric: [effect and status]
- Guardrail metrics: [result and remaining uncertainty]
- Estimated weekly impact: [estimate, units, interval, and significance, if available]

[Confirmed next action, or recommendation and decision still needed]
[If rollout is agreed for UX reasons, state that rationale without claiming metrics proved no trade-offs.]
[Source link, if available]
```

#### Loss / rollback

```text
:warning: [EXPERIMENT_NAME] — [negative outcome]
We tested [change] to address [problem].
Results showed [supported negative finding].

- Primary metric: [effect and status]
- Guardrail metrics: [result]
- Estimated weekly impact: [estimate and uncertainty, if available]

[Confirmed rollback / iteration action, or clearly labeled recommendation]
[Source link, if available]
```

#### Retest / targeted follow-up

```text
[EXPERIMENT_NAME] — [retest proposed / agreed / relaunched, as confirmed]
The overall result was inconclusive. [Segment] showed [directional result and significance status], which suggests a follow-up hypothesis rather than a confirmed win.

Hypothesis: [Why the effect might differ in this segment, labeled as inference where appropriate]
Scope: [Confirmed or proposed audience and platforms; allocation only if known]
Next: [Confirmed action or proposed validation plan]
[Source link, if available]
```

Do not say a rerun is live, approved, or certain to reach significance unless the relevant fact is supported; future significance cannot be promised.

## Style notes

- State the outcome and recommended or agreed action explicitly.
- Use plain language and explain necessary statistical terms.
- Preserve exact experiment identifiers only from supplied inputs; never include a private worked example in this public template.
- Ground every number and link in the inputs. Label estimates and calculations.
- Never convert inconclusive evidence into a claim of no harm or benefit.
- Use [Slack writeups](slack-writeups.md) for launch and live-status messages that are not concluded experiment readouts.
