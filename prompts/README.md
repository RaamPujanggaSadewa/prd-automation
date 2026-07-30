# Prompt Library

Six prompts, run in order. Each builds on what the last one produced.

| # | Prompt | Used in | Writes to |
|---|---|---|---|
| 01 | [Heuristic teardown](01-heuristic-teardown.md) | [Step 02](../workflow/02-design-inputs.md) | Your notes (by hand) |
| 02 | [Problem framing](02-problem-framing.md) | [Step 03](../workflow/03-generate-prd.md) | Problem, Context, Goals |
| 03 | [User stories](03-user-stories.md) | Step 03 | Users & Stories |
| 04 | [Requirements](04-requirements.md) | Step 03 | Requirements + acceptance criteria |
| 05 | [Success metrics](05-success-metrics.md) | Step 03 | Metrics |
| 06 | [Adversarial critique](06-adversarial-critique.md) | [Step 04](../workflow/04-critique-and-refine.md) | Nothing — reports only |

---

## File convention

**Every file in this folder is pure prompt text.** No commentary, no explanation, nothing that isn't meant to reach the model. That's what makes this safe:

```bash
opencode run -c "$(cat prompts/04-requirements.md)"
```

All the explanation lives in this README and in the [workflow pages](../workflow/). If you edit a prompt, keep the convention — an added note like "*remember to check this section carefully*" becomes an instruction to the model, and models act on instructions.

---

## Tool-agnostic

These are plain text. Nothing is OpenCode-specific and nothing depends on Claude.

| Tool | How to use them |
|---|---|
| **OpenCode CLI** | `opencode run -c "$(cat prompts/NN-name.md)"` |
| **Claude Code** | Same shape, or drop them in `.claude/commands/` as slash commands |
| **ChatGPT / Gemini / Claude web** | Paste the prompt, paste your brief, paste the draft so far |
| **Notion / Linear AI** | Paste into an AI block on the doc |

The only thing you lose in a chat interface is direct file editing — you'll copy output back into your document yourself, and you'll need to paste the current draft in each time so the model has context. The prompts work identically.

---

## Two things to know before running any of them

**They assume a filled-in design brief.** Prompts 02–05 all read from it. Run them against an empty or thin brief and you get generic output — not because the prompts are weak, but because there's nothing specific to work from. See [step 02](../workflow/02-design-inputs.md).

**Prompt 06 deliberately doesn't fix anything.** It reports problems and stops. A model allowed to fix its own critique tends to rewrite around the criticism — softening a claim until it can't be challenged, rather than supporting it or cutting it. You want the findings, then your own decisions.

---

## Adapting them

The parts worth changing:

- **Section names.** If your PRD template differs from [ours](../templates/prd-template.md), update the section names the prompts write to.
- **Requirement ID format.** Prompt 04 uses `REQ-01`. Match whatever your tracker uses.
- **`[NEEDS DATA]` marker.** Change the string if you like, but keep *some* explicit marker. It gives the model a legitimate place to put uncertainty, which is what stops uncertainty from being smuggled into the body text as false confidence.

The parts worth keeping:

- **The "don't invent evidence" instruction.** It appears in every prompt on purpose. Repetition across prompts measurably reduces fabrication, and dropping it from one prompt is usually where a fabricated statistic gets in.
- **One section per prompt.** Merging prompts to save time reintroduces exactly the review problem the split was there to solve.
- **The plain-language constraint.** Without it, output drifts toward corporate register within a couple of sections.
