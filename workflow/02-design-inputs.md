# 02 — Design Inputs

**No AI in this step.** This is the part where being a designer is the advantage, and it's the step that determines whether everything after it is worth reading.

Output: a filled-in [`design-brief.md`](../templates/design-brief.md) — two to three pages of specific, observed findings.

Budget 2–4 hours.

---

## Why this step exists

Ask any model for "a PRD for a music app redesign" and you'll get something like:

> **Problem:** Users struggle to discover new music that matches their tastes. The current discovery experience lacks personalisation and fails to surface relevant content, leading to reduced engagement.

Every clause is true of every music app ever built. It could have been written without opening the product. There's nothing in it a team could disagree with, which means there's nothing in it a team could act on.

Now the same problem, from a teardown:

> **Problem:** The home screen shows six horizontally-scrolling shelves before any of them are labelled by *why* they were recommended. "Made For You" and "Discover Weekly" sit adjacent and are visually identical, but one is generated from listening history and the other from collaborative filtering. Users I watched treated them as interchangeable, tried one, found it stale, and stopped trusting both.

Same product area. The second one is arguable — someone can push back on it, which means it's a real claim. It also implies a specific fix.

The difference isn't prompting. The first prompt had no evidence in it and the second did. **This step is where the evidence comes from.**

---

## The teardown

Open the product. Actually use it. Do the thing a real user is trying to do, and take notes while it's still annoying you.

I run [prompt 01](../prompts/01-heuristic-teardown.md) as a checklist — a set of lenses to look through, not a script to follow. Work through the primary flow screen by screen and write down what you find.

What I'm looking for:

- **Where the flow breaks down** — the specific step, not "onboarding is confusing"
- **What the interface asks of the user** that it could have figured out itself
- **Where the visual hierarchy contradicts the actual priority** of the content
- **Inconsistencies** between screens that do the same job
- **The moment I'd expect a real user to give up**, and why

Capture screenshots as you go. Annotate them. They're the PRD's supporting evidence and they're a large part of why it reads as design work rather than a text document.

### Make the findings specific

Each finding needs to survive a hostile "so what?".

| Too vague | Specific enough |
|---|---|
| The navigation is confusing | Five tabs, two of which ("Feed" and "Explore") show overlapping content with no stated distinction |
| Onboarding is too long | Seven screens before first value; three collect data the app could infer from first-session behaviour |
| The empty state is bad | Empty saved-items state shows an illustration and no action, dead-ending the primary flow's exit path |

The right-hand column is what makes a requirement writable later.

---

## Fill in the brief

Copy [`templates/design-brief.md`](../templates/design-brief.md) into your repo and work through it. Six sections:

| Section | What goes in it |
|---|---|
| **Product & scope** | What you're looking at, which surface, which flow. Be narrow. |
| **Who this is for** | The specific user in the specific situation. Not a demographic. |
| **Problems found** | 3–5 findings, each with evidence and a "so what". |
| **Design direction** | Your proposed approach, and the alternatives you rejected. |
| **Constraints** | Platform, technical, business. What's off the table. |
| **Open questions** | What you genuinely don't know. |

### On the open questions section

Fill this in honestly. It is the section that makes the difference between a document that helps a team and one that misleads it.

You do not have production analytics for someone else's app. You do not know their roadmap or why a decision that looks wrong was made. Writing `[NEEDS DATA] Current completion rate for this flow — unknown, would need instrumentation` is a stronger move than inventing a number, and any reader who has shipped anything will recognise it as the more credible document.

This also gives the model a legitimate place to put uncertainty, which is what stops it from smuggling uncertainty into the body text as false confidence.

### On scope

Pick one flow. One surface. Onboarding, or search, or checkout — not "the app".

A tight PRD on a single flow demonstrates more product thinking than a sprawling one across five, because scoping *is* the product skill being demonstrated. And the AI-generated sections stay dramatically more accurate when the subject is narrow.

---

## Before moving on

Check your brief against these. If any is a no, go back — the next step can't fix it.

- [ ] Every problem names a specific screen, step, or interaction
- [ ] Every problem has a "so what" a stakeholder would care about
- [ ] Nothing is stated as fact that you haven't observed or reasoned to
- [ ] Anything you'd need real data for is marked `[NEEDS DATA]`
- [ ] Your design direction says what you rejected, not just what you chose
- [ ] Scope is one flow, and you could name it in four words

That last one is the most commonly failed.

---

**Next → [03 — Generate](03-generate-prd.md)**
