# 03 — Design & Context

**AI shows up here only if the design needs a starting point.** This step and [step 04](04-generate-prd.md) aren't strictly sequential — I go back and forth between designing in Figma and writing the PRD, each one informing the other.

---

## Designing

**If the direction is straightforward, just design it.** Most changes are — you know the pattern, you know the constraint, there's no ambiguity worth pausing over.

**If it's not straightforward — you're not sure what the right pattern is, or the obvious approach doesn't feel right — look for a starting point before staring at a blank frame:**

- **[Figma Make](https://www.figma.com/make/)** — Figma's AI UI generation. Describe the screen or flow and get a rough version to react to. I use this for inspiration and starting points, not for output — it rarely survives contact with your actual design system unedited.
- **[Mobbin](https://mobbin.com)** — a library of real, shipped app screens organized by flow and pattern. Useful for seeing how other products solved the same problem before you commit to your own answer.

Both are a way to get unstuck, not a shortcut past designing. Whatever comes out gets reworked to fit the actual product — its components, its constraints, its voice.

---

## Building the context folder

Before I write a word of the PRD, I put together a folder with everything the AI needs to actually understand the product. This is the single most important habit in the whole workflow — it's the difference between the AI drafting from a real understanding of the product and the AI guessing.

### Structure

```
[project-name]/
├── current/
│   ├── screens/        Screenshots of the product as it exists today
│   └── notes.md         What this version is, and what's wrong with it
├── new/
│   ├── screens/        Screenshots or Figma exports of the proposed version
│   └── notes.md         What changed, and why
└── requirement-notes.md  From step 02
```

### `current/notes.md`

Describe the current version and the problem in plain terms — enough that someone who has never seen the product could understand it from this file plus the screenshots. Use [`templates/version-context.md`](../templates/version-context.md) as a starting point.

Cover:
- What this screen or flow does today
- What's wrong with it — the actual problem, tied back to what came out of [step 02](02-requirement-gathering.md)
- Anything about the current implementation that constrains what can change

### `new/notes.md`

Same template, describing the proposed version:
- What changed, screen by screen or step by step
- Why each change addresses something from the current-version notes — if a change doesn't trace back to a stated problem, that's worth noticing before you write the PRD, not after
- Anything you deliberately left unchanged, and why

### Why both versions, not just the new one

Handing the AI only the new design and asking it to write a PRD gets you a document that describes what the new screens look like. It won't explain why anything changed, because it has no idea what changed *from*. The before/after pairing is what lets it write requirements and acceptance criteria that make sense — a requirement is much easier to state precisely when you can point at the specific thing it's fixing.

This also means the AI's understanding of "the problem" is as good as your notes, not as good as your actual understanding. If your notes are thin, the PRD will read thin in exactly the same places.

---

## Screenshots

Doesn't need to be polished — the point is coverage, not presentation. For each flow or screen you're changing:

- The current version, as it actually looks in production
- The new version, from Figma

Name them so the pairing is obvious (`checkout-01-current.png` / `checkout-01-new.png`) — makes life easier both for you re-reading this later and for the AI matching them up.

---

**Next → [04 — Generate the PRD](04-generate-prd.md)**
