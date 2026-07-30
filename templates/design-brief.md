# Design Brief — [Product / Flow]

> This is the input to everything else. Every AI-drafted section of the PRD is derived from this file.
>
> Fill it in properly. A thin brief produces a generic PRD, and no amount of prompt work will fix that — the prompts have nothing specific to work from. Budget 2–4 hours. See [workflow/02](../workflow/02-design-inputs.md).
>
> Delete this blockquote when you're done.

---

## 1. Product & scope

**Product:** [What you're looking at]

**Surface:** [Mobile app / web / specific platform]

**Flow under examination:** [One flow. If you can't name it in four words, it's too broad.]

**Version / date examined:** [What you actually tested, and when — products change]

---

## 2. Who this is for

**Primary user:**

[A specific person in a specific situation. What they're trying to do, what they know, what constraints they're under, what device and context.

Situations produce requirements. Demographics don't — nothing follows from "millennials who value convenience".]

**Secondary users, if any:**

[Only if they genuinely affect the design. Omit rather than pad.]

---

## 3. Problems found

Three to five. Each one needs all three parts. This is the core of the brief.

### Problem 1 — [Short name]

**Observation:** [The specific screen, step, or interaction. Not a category.]

**Evidence:** [What you saw, counted, or tried. Screenshot reference.]

**So what:** [What this costs the user or the business. If you can't answer this, it's a preference, not a problem — cut it.]

### Problem 2 — [Short name]

**Observation:**

**Evidence:**

**So what:**

### Problem 3 — [Short name]

**Observation:**

**Evidence:**

**So what:**

---

### Specificity check

Before moving on, read each observation and ask: could this have been written without opening the product?

| Fails the check | Passes |
|---|---|
| "Navigation is confusing" | "Five tabs; two show overlapping content with no stated distinction" |
| "Onboarding is too long" | "Seven screens before first value; three collect data inferable from first-session behaviour" |
| "Poor empty state" | "Empty saved-items state shows an illustration and no action, dead-ending the flow's only exit" |

If any of yours reads like the left column, rewrite it or drop it.

---

## 4. Design direction

**Proposed approach:**

[What you'd change and the principle behind it. Two or three paragraphs.]

**Alternatives considered and rejected:**

| Option | Why not |
|---|---|
| [Alternative] | [Reason] |
| [Alternative] | [Reason] |

Fill this in even if it feels obvious in hindsight. It's the clearest evidence of design judgment in the whole document, and it stops the PRD reading as though your first idea was the only idea.

---

## 5. Constraints

**Platform:** [OS versions, screen sizes, offline behaviour, accessibility requirements]

**Technical:** [What you know about the existing system. Mark anything you're assuming as an assumption.]

**Business:** [Commercial or organisational limits. If you're working on someone else's product from the outside, you mostly don't know these — say so.]

**Explicitly out of scope:**

- [Thing a reader might assume is included]
- [Another]
- [Another]

State the boundary here. If it's only implied, the AI will drift past it and add requirements for adjacent features.

---

## 6. Open questions

What you genuinely don't know. Be honest — this section is what makes the rest trustworthy.

- [ ] `[NEEDS DATA]` [Metric you'd need but don't have]
- [ ] [Something about user behaviour you're inferring rather than observing]
- [ ] [A technical unknown]
- [ ] [A decision that isn't yours to make]

If you're analysing a product you don't work on, this list should be long. You don't have their analytics, their roadmap, or the context behind decisions that look wrong from outside. Writing that down is stronger than filling the gaps with plausible guesses — and it gives the model a legitimate place to put uncertainty instead of smuggling it into the body text as false confidence.

---

## Ready?

- [ ] Every problem names a specific screen, step, or interaction
- [ ] Every problem has a "so what" a stakeholder would care about
- [ ] Nothing stated as fact that you haven't observed or reasoned to
- [ ] Anything needing real data is marked `[NEEDS DATA]`
- [ ] Design direction names rejected alternatives
- [ ] Out-of-scope list is written, not implied
- [ ] Scope is one flow, nameable in four words

All boxes ticked → [workflow/03 — Generate](../workflow/03-generate-prd.md).
