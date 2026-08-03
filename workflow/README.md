# The Workflow

Five steps. This is the actual process I use at work, not a generic "AI writes your PRD" pipeline — the AI shows up in step 4, once there's real context to give it.

| Step | What happens | AI involved? |
|---|---|---|
| **[01 — Setup](01-setup-opencode.md)** | Install OpenCode, pick a model, write the project rules | Setup only |
| **[02 — Requirement gathering](02-requirement-gathering.md)** | Get the real context — a conversation with whoever asked (CEO, sales, ops), or a research insight the data surfaced first | **No** |
| **[03 — Design & context](03-design-and-context.md)** | Design in Figma; build a folder showing current vs. new, with the reasoning | Only if the design needs a starting point |
| **[04 — Generate the PRD](04-generate-prd.md)** | Hand the AI the context folder and a template; it drafts, I edit | Yes |
| **[05 — Publish](05-publish-to-pages.md)** | Commit, push, enable GitHub Pages — this is how engineering gets it, not just how other people read it | No |

## Steps 3 and 4 aren't strictly sequential

Design and PRD writing happen alternately, not one after the other. I'll draft part of the PRD, realize a requirement doesn't make sense until I've settled a design decision, go back into Figma, then return to the PRD with that decision made. The numbering here is for reference, not a strict order to follow top to bottom.

## Why this order

The AI only enters at step 4, and by then there's real material to give it: what the stakeholder actually asked for, what the product looks like today, what it looks like after the change, and why. That context is what makes step 4 fast — the AI isn't guessing at a product it's never seen, it's reading two versions side by side and drafting from the difference.

Skip straight to step 4 without steps 2 and 3 and you get the same problem any AI-first PRD has: a document with nothing behind it.

---

**Start here → [01 — Setup](01-setup-opencode.md)**
