# Templates

Copy these into your own project. Plain markdown — nothing tool-specific except `opencode.json`.

| File | Copy to | What it's for |
|---|---|---|
| [`requirement-notes.md`](requirement-notes.md) | your repo root | **Start here.** Written up right after the stakeholder conversation ([step 02](../workflow/02-requirement-gathering.md)). |
| [`version-context.md`](version-context.md) | `context/current/notes.md` and `context/new/notes.md` | Used twice, once per version ([step 03](../workflow/03-design-and-context.md)) |
| [`prd-template.md`](prd-template.md) | your repo root as `PRD.md` | Section skeleton the AI drafts into ([step 04](../workflow/04-generate-prd.md)) |
| [`AGENTS.md`](AGENTS.md) | your repo root, same name | Standing rules OpenCode reads every session |
| [`opencode.json`](opencode.json) | your repo root, same name | Model selection |

```bash
cp templates/requirement-notes.md ./requirement-notes.md
mkdir -p context/current context/new
cp templates/version-context.md context/current/notes.md
cp templates/version-context.md context/new/notes.md
cp templates/prd-template.md    ./PRD.md
cp templates/AGENTS.md          ./AGENTS.md
cp templates/opencode.json      ./opencode.json
```

---

## Notes on each

**`requirement-notes.md`** — the write-up from the stakeholder conversation. Whoever asked for this — CEO, sales, ops — this file is what stops their intent from getting lossy by the time it reaches the AI five steps later.

**`version-context.md`** — used twice, once for the current version of the product and once for the proposed new version. The pairing is what lets the generated PRD explain *why* something changed, not just describe what the new screens look like.

**`prd-template.md`** — sections are labelled **AI-drafted** or **Write yourself**. The structural, high-volume sections (requirements, acceptance criteria) are where AI drafting genuinely helps. The judgment sections (problem statement, design rationale) are where a model can only restate what you already told it, so the restatement is strictly worse than writing it yourself. If your company has its own PRD template, use that instead — this one exists because most people forking this repo won't have one to share.

**`AGENTS.md`** — the highest-leverage file in the setup. Its first rule — never invent evidence — is what keeps fabricated statistics out of the draft. Using Claude Code instead of OpenCode? Rename it `CLAUDE.md`; the content is unchanged.

**`opencode.json`** — one line that matters:

```json
{ "model": "opencode/claude-haiku-4-5" }
```

This is whatever model I have access to, not a recommendation. Check yours with `opencode models`, and see [workflow/01](../workflow/01-setup-opencode.md) for the note on free models if you don't have a paid provider.

---

## Using a different AI tool

Only `opencode.json` and `AGENTS.md` assume OpenCode. Everything else is plain markdown and works anywhere — including pasted into ChatGPT, Gemini, or a Notion AI block. See [prompts/README.md](../prompts/README.md) for the per-tool notes.
