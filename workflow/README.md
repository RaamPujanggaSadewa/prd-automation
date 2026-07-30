# The Workflow

Five steps, in order. Each page has the exact commands and the reasoning behind them.

| Step | What happens | AI involved? |
|---|---|---|
| **[01 — Setup](01-setup-opencode.md)** | Install OpenCode, pick the model, write the project rules | Setup only |
| **[02 — Design inputs](02-design-inputs.md)** | Heuristic teardown → design brief | **No** — this is designer work |
| **[03 — Generate](03-generate-prd.md)** | Six sequential prompts build the PRD section by section | Yes |
| **[04 — Critique](04-critique-and-refine.md)** | Adversarial pass; the model attacks its own draft | Yes |
| **[05 — Publish](05-publish-to-pages.md)** | Commit, push, enable GitHub Pages, share | Commit via CLI |

## How long it takes

Rough timings from my own runs, for a single-feature PRD:

| Step | Time |
|---|---|
| 01 — Setup | ~10 min, once ever |
| 02 — Design inputs | **2–4 hours** |
| 03 — Generate | 20–30 min |
| 04 — Critique | 30–45 min |
| 05 — Publish | ~5 min |

Look at the shape of that table. Step 2 — the step with no AI in it — takes longer than everything else combined.

That's not a flaw in the workflow. That *is* the workflow. The AI compresses the writing, not the thinking. If your step 2 takes twenty minutes, your PRD will read like it.

## Two rules I follow

**1. One section at a time.** I never ask for a whole PRD in one prompt. Six focused prompts, each reading the file the previous one wrote. Each output is small enough that I can actually check it, and any mistake is contained to one section instead of smeared through the whole document.

**2. Every claim is traceable.** If the draft asserts something — a user behaviour, a business impact, a technical constraint — I can point to where in my brief it came from. When I can't, that line comes out. This is the single habit that separates a real PRD from a plausible-sounding one, and no prompt can do it for you.

## A caveat worth stating

This workflow is good at turning evidence into a well-structured document. It is not a substitute for research, and it won't tell you whether your idea is any good. A confidently-written PRD built on a weak premise is more dangerous than a messy one, because the polish hides the weakness.

Do the research. Then use this to write it up.

---

**Start here → [01 — Setup](01-setup-opencode.md)**
