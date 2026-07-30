# Prompt Library

One prompt. Used once you have the context folder from [step 03](../workflow/03-design-and-context.md) — current version, new version, and requirement notes all assembled.

| # | Prompt | Used in |
|---|---|---|
| 01 | [Generate PRD](01-generate-prd.md) | [Step 04](../workflow/04-generate-prd.md) |

---

## File convention

**The prompt file is pure prompt text.** No commentary, nothing that isn't meant to reach the model — because it's meant to be piped straight in:

```bash
opencode run -f context/current/notes.md -f context/new/notes.md -f requirement-notes.md "$(cat prompts/01-generate-prd.md)"
```

All the explanation lives here and in the [workflow pages](../workflow/README.md). If you edit the prompt, keep this convention — an added aside like "*review this part carefully*" becomes an instruction the model will act on, since it can't tell your notes-to-self apart from the request.

---

## Why one prompt, not several

The real workflow is: assemble everything the AI needs to know — current version, new version, why the change was requested — then ask it to draft against a template in one pass. That's a single request, not a multi-step pipeline. Splitting it into several sequential prompts would be a structural choice this workflow doesn't make; it just wasn't how the process actually works.

In practice the first draft usually isn't the last thing asked for in the session — you'll keep talking to the model from there, in the interactive TUI, correcting specific sections as you review. That's ordinary back-and-forth, not a second prompt file.

---

## Tool-agnostic

Plain text. Nothing here is OpenCode-specific or Claude-specific.

| Tool | How to use it |
|---|---|
| **OpenCode CLI** | `opencode run -f <files> "$(cat prompts/01-generate-prd.md)"` |
| **Claude Code** | Same shape, or save as a slash command in `.claude/commands/` |
| **ChatGPT / Gemini / Claude web** | Paste the prompt, then paste in your notes and describe or attach your screenshots |
| **Notion / Linear AI** | Paste into an AI block on the doc |

In a chat interface you lose direct file editing — you'll copy the output back into your PRD yourself, and you'll need to re-paste your notes if the conversation resets. The prompt itself works the same.

---

## Adapting it

**Section names** — if your PRD template differs from [ours](../templates/prd-template.md), update the section names the prompt references.

**The `[NEEDS DATA]` marker** — change the string if you like, but keep some explicit marker for "I don't have this." It gives the model a legitimate place to put uncertainty instead of quietly inventing a plausible-sounding number.

**Keep the anti-fabrication rules even if you change everything else.** They're not part of the process structure — they're a guardrail against the one failure mode that's hardest to catch by eye, because a fabricated statistic reads exactly like a real one sitting next to it.
