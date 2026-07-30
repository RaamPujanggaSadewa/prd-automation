# 04 — Generate the PRD

Everything before this step was preparation. By now you have requirement notes, a current-vs-new context folder, and a design that's at least stable enough to write about. This is where the AI actually gets used.

---

## The template

At the office we use our own PRD template, which I'm not sharing here since it's the company's. [`templates/prd-template.md`](../templates/prd-template.md) is a general-purpose stand-in — swap in yours if you have one. The workflow doesn't depend on the specific template; it depends on giving the AI real context to fill it from.

---

## Generate

Point OpenCode at everything from [step 03](03-design-and-context.md) plus the template, and ask it to draft the PRD:

```bash
opencode run \
  -f context/current/notes.md \
  -f context/new/notes.md \
  -f requirement-notes.md \
  -f templates/prd-template.md \
  "$(cat prompts/01-generate-prd.md)"
```

Or in the interactive TUI (`opencode`) if you'd rather work through it conversationally — drop the files in, paste the prompt, and keep talking to it from there. That's usually what I do in practice, since the first draft rarely needs to be the last thing I ask for in the session.

The prompt is in [`prompts/01-generate-prd.md`](../prompts/01-generate-prd.md) — see [prompts/README.md](../prompts/README.md) if you're adapting it.

---

## Review

Read the draft against your own notes, section by section. What to check:

- **Does every requirement trace back to something in `requirement-notes.md` or the current/new context?** If a requirement doesn't map to anything you actually said, it's the model filling a gap on its own — cut it or fix it.
- **Any number, stat, or claim you didn't supply?** These show up more than you'd expect, and they read exactly like the real content around them. Anything you can't source, remove or flag.
- **Does it sound like your product and your problem, or has it been smoothed into something generic?** If a specific detail from your notes came back vague, quote the specific detail back at the model and ask it to use that instead.

---

## Loop back if you need to

If writing the PRD surfaces something the design doesn't actually handle — an edge case, a state you hadn't drawn, a requirement that only makes sense with a different layout — go back to Figma. This is normal, not a failure of the process. The PRD writing and the design work sharpen each other; that's the whole reason they run alternately instead of one strictly after the other.

---

## Finish it yourself

The sections that should read like you, not like the model:

- **The problem statement.** It's carrying the reason this work matters, and that reasoning is yours from the step 02 conversation — the model wasn't in the room.
- **Design rationale**, including anything you tried and rejected in Figma.
- **Any judgment call** — priority, trade-off, what gets cut if time runs short.

Let the model's draft handle the structural, high-volume parts — requirements, acceptance criteria — and put your own hand back on anything that's actually a decision.

---

**Next → [05 — Publish](05-publish-to-pages.md)**
