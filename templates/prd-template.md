# PRD — [Feature / Flow Name]

| | |
|---|---|
| **Status** | Draft |
| **Author** | [Your name] |
| **Last updated** | [Date] |
| **Scope** | [The one flow this covers, in four words] |

> Delete this blockquote before publishing.
>
> Sections marked **AI-drafted** are filled by the [prompt library](../prompts/) and then reviewed by hand. Sections marked **Write yourself** should be in your own words — they carry your point of view and a model can only restate what you already told it.
>
> `[NEEDS DATA]` marks anything requiring a figure or fact you don't have. Leaving these visible in a published PRD is a feature, not an omission — it shows the boundary of what you actually know.

---

## Problem

**AI-drafted, then rewrite yourself.**

What is broken, for whom, and what it costs. Two to four paragraphs.

Lead with the user's experience, then the consequence. Not the solution.

---

## Context

**AI-drafted.**

What surface this covers, which flow, where it sits in the product.

### Out of scope

- [Thing a reader might assume is included but isn't]
- [Another]
- [Another]

State this explicitly. An unstated scope boundary is the most common reason a PRD gets misread.

---

## Goals

**AI-drafted.**

1. [A change in user or business outcome — not a feature]
2. [Another]
3. [Another]

---

## Users & Stories

**AI-drafted.**

### Primary user

[A specific person in a specific situation. Not a demographic.]

### Stories

**US-01** — As a [user in situation], I want to [action], so that [outcome].
- **Traces to:** [problem from the brief]

**US-02** — As a [user in situation], I want to [action], so that [outcome].
- **Traces to:** [problem from the brief]

---

## Design Direction

**Write yourself.** This is the section that makes it design work.

### Approach

[What you're proposing, and the principle behind it.]

### Why this and not the alternatives

| Option | Why not |
|---|---|
| [Alternative you considered] | [Why you rejected it] |
| [Another] | [Why you rejected it] |

This table is the highest-value thing in the document for anyone assessing your product thinking. Showing what you rejected and why demonstrates judgment; showing only your chosen answer demonstrates nothing.

### Screens

[Embed or link annotated screens. Reference them from the requirements below.]

---

## Requirements

**AI-drafted.** Review the acceptance criteria most carefully — this is what gets built from.

### Must have

**REQ-01** — [What the product must do.]
- **Why:** [goal or story ID]
- **Acceptance criteria:**
  - [Objectively testable condition]
  - [Objectively testable condition]
- **Edge cases:** [empty / offline / interrupted / limits, or `None identified`]

**REQ-02** — [What the product must do.]
- **Why:** [goal or story ID]
- **Acceptance criteria:**
  - [Objectively testable condition]
- **Edge cases:** [...]

### Should have

**REQ-03** — [...]

### Could have

**REQ-04** — [...]

---

## Success Metrics

**AI-drafted.** Highest risk section for invented numbers — check every figure.

**M-01 — [Metric name]**
- **What it measures:** [the countable thing]
- **Why it matters:** [goal ID]
- **Current baseline:** [figure, or `[NEEDS DATA] requires instrumentation`]
- **Target:** [only with a real baseline; otherwise state direction]
- **How to measure:** [specific event or funnel step]

**M-02 — [Counter-metric — what must not get worse]**
- [...]

Include at least one counter-metric. Every real change trades something off, and a metrics section that only measures the hoped-for outcome isn't measuring.

---

## Open Questions

**Write yourself.** Be honest here.

- [ ] [Something you genuinely don't know]
- [ ] [Something needing data you don't have]
- [ ] [A decision that needs someone else's input]

This section is a credibility signal, not a weakness. Any reader who has shipped something will trust a document that names its unknowns over one that doesn't appear to have any.

---

## Appendix

### Design brief

[Link to the brief this was built from.]

### Method

[Optional: how this document was produced. Being straight about what the AI drafted and what you wrote earns more credibility than implying it was all hand-written.]
