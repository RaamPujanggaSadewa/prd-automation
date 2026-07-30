# Templates

Copy these into your own project. Plain markdown — nothing tool-specific except `opencode.json`.

| File | Copy to | What it's for |
|---|---|---|
| [`design-brief.md`](design-brief.md) | your repo root | **Start here.** The input to everything else. |
| [`prd-template.md`](prd-template.md) | your repo root as `PRD.md` | Section skeleton the prompts fill in |
| [`AGENTS.md`](AGENTS.md) | your repo root, same name | Standing rules OpenCode reads every session |
| [`opencode.json`](opencode.json) | your repo root, same name | Model selection |

```bash
cp templates/design-brief.md  ./design-brief.md
cp templates/prd-template.md  ./PRD.md
cp templates/AGENTS.md        ./AGENTS.md
cp templates/opencode.json    ./opencode.json
```

---

## Notes on each

**`design-brief.md`** — the only one you fill in by hand, and the one that determines whether the rest is any good. A thin brief produces a generic PRD no matter how well the prompts are written, because the prompts have nothing specific to work from.

**`prd-template.md`** — sections are labelled **AI-drafted** or **Write yourself**. The split isn't arbitrary: the structural, high-volume sections (requirements, acceptance criteria, edge cases) are where AI drafting genuinely helps and is easy to verify. The judgment sections (problem statement, design rationale, open questions) are where a model can only restate what you already told it, so the restatement is strictly worse than writing it yourself.

**`AGENTS.md`** — the highest-leverage file in the setup. It stops you re-explaining the ground rules every session, and its first rule — never invent evidence — is what keeps fabricated statistics out of the draft. Using Claude Code instead? Rename it `CLAUDE.md`; the content is unchanged.

**`opencode.json`** — one line that matters:

```json
{ "model": "opencode/claude-haiku-4-5" }
```

Check yours with `opencode models | grep haiku`. If you authenticated with an Anthropic API key rather than OpenCode Zen, the string is `anthropic/claude-haiku-4-5` instead. Both run the same model; the prefix is the provider route. See [workflow/01](../workflow/01-setup-opencode.md).

---

## Using a different AI tool

Only `opencode.json` and `AGENTS.md` assume OpenCode. The brief and PRD templates are plain markdown and work anywhere — including pasted into ChatGPT, Gemini, or a Notion AI block. See [prompts/README.md](../prompts/README.md) for the per-tool notes.
