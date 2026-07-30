# PRD Automation

**A UI/UX designer's workflow for writing product requirement documents with AI — from design artifacts to a published, readable PRD.**

I'm a designer, not a PM. But I kept hitting the same wall: I'd finish a flow, understand exactly what was broken and why, and then have to hand that understanding to someone else to translate into a spec. Something always got lost in the handoff.

So I built a workflow that lets me write the PRD myself — where my design work *is* the input, and AI does the structuring instead of the thinking.

This repo is three things:

| | |
|---|---|
| **[The workflow](workflow/README.md)** | Five steps, start to finish. What I run, in what order, and why. |
| **[The result](case-study/README.md)** | A complete PRD produced by this workflow, published and readable. |
| **[The toolkit](prompts/README.md)** | Every prompt and template, ready to fork and use on your own project. |

---

## The core idea

Most "AI writes your PRD" demos are one prompt: *"Write a PRD for a food delivery app."* You get four paragraphs of generic scaffolding that could describe any product. It reads like a PRD and says nothing.

The problem isn't the model. It's that the prompt contains no evidence.

A designer already has the evidence — flows, screens, heuristic findings, the specific reason step 3 loses people. That material is the difference between a document that describes a product and one that argues for a change.

So the workflow inverts the usual split:

| I own | The AI owns |
|---|---|
| The problem — what's broken, for whom | Structure and sectioning |
| The evidence — screens, flows, teardown notes | Turning findings into requirements |
| The design decisions and their rationale | Drafting acceptance criteria |
| Scope calls — what's in, what's out | Consistency and cross-referencing |
| Final judgment on every claim | Catching gaps I missed |

**I bring the argument. The AI builds the document around it.** Nothing in the output is a claim I haven't made myself.

---

## The workflow at a glance

```
  1. SETUP          OpenCode CLI + Claude Haiku 4.5 + project rules
        ↓
  2. DESIGN INPUTS  Heuristic teardown → design brief  (designer work, no AI)
        ↓
  3. GENERATE       Six sequential prompts, each building on the last
        ↓
  4. CRITIQUE       Adversarial pass — the model attacks its own draft
        ↓
  5. PUBLISH        Commit via CLI → GitHub Pages → shareable link
```

Full detail in **[workflow/](workflow/README.md)**. Each step is its own page with the exact commands.

### Why these tools

**[OpenCode CLI](https://opencode.ai)** — an open-source terminal AI agent. It reads and writes files in the repo directly, so the PRD is a real file under version control from the first draft. Every revision is a commit. No copy-pasting out of a chat window, no "which version is current".

**Claude Haiku 4.5** — the small, fast, cheap model in the Claude family ($1 / $5 per million tokens in, out). Deliberate choice: this workflow doesn't need a frontier model, because the reasoning is mine. Haiku's job is structuring, consistency, and drafting from evidence I supply. It's fast enough that iterating feels like editing rather than waiting, and cheap enough that a full PRD costs pocket change.

**GitHub Pages** — the PRD is markdown in a repo, so publishing it as a readable web page is a settings toggle, not a deployment.

---

## Use this yourself

No install, no account, no dependency on my setup. The templates are plain markdown and the prompts are plain text — they work in OpenCode, Claude Code, ChatGPT, Gemini, or a Notion AI block.

```bash
git clone https://github.com/RaamPujanggaSadewa/prd-automation.git
```

Then:

1. Copy `templates/prd-template.md` into your own project as `PRD.md`.
2. Fill in `templates/design-brief.md` with your own findings. **Don't skip this** — it's the step that makes the rest work.
3. Run the prompts in `prompts/` in order, 01 through 06.
4. Publish however you like.

If you're using OpenCode too, `templates/opencode.json` and `templates/AGENTS.md` will get you a matching setup in about two minutes — see **[workflow/01-setup-opencode.md](workflow/01-setup-opencode.md)**.

### A word on the boring step

The design brief in step 2 is unglamorous and there's no AI in it. It is also the entire reason this produces something worth reading. A brief with three specific, observed problems will give you a sharper PRD than any amount of prompt engineering on an empty one.

If you take one thing from this repo, take that.

---

## Repo map

```
prd-automation/
├── workflow/          The five steps, in order
├── prompts/           Prompt library — 01 to 06, run sequentially
├── templates/         PRD template, design brief, OpenCode config
└── case-study/        The worked example
```

---

## License

[MIT](LICENSE) — use it, fork it, change it, ship it. Attribution appreciated, not required.

Built by [Raam Pujangga Sadewa](https://github.com/RaamPujanggaSadewa).
