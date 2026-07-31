# PRD Automation

**A UI/UX designer's workflow for writing product requirement documents with AI — from a stakeholder conversation to a published, readable PRD.**

I'm a designer, not a PM. But I kept hitting the same wall: I'd sit with whoever needed something built, understand exactly what they were asking for and why, design the fix — and then have to hand that understanding to someone else to translate into a spec. Something always got lost in the handoff.

So I built a workflow that lets me write the PRD myself — where the conversation and the design *are* the input, and AI does the drafting once there's real material to draft from.

This repo is three things:

| | |
|---|---|
| **[The workflow](workflow/README.md)** | Five steps, start to finish. What I actually do, in what order. |
| **[The result](case-study/README.md)** | A complete PRD produced by this workflow, published and readable. |
| **[The toolkit](prompts/README.md)** | The prompt and templates, ready to fork and use on your own project. |

---

## The core idea

Most "AI writes your PRD" demos are one prompt: *"Write a PRD for a food delivery app."* You get four paragraphs of generic scaffolding that could describe any product. It reads like a PRD and says nothing.

The problem isn't the model. It's that the prompt contains no evidence.

By the time I open the AI, I've already sat with the person who asked for this, designed the change, and put together a folder showing the product before and after with my own notes on why. That's what turns a generic draft into a document that argues for a specific change — not a better prompt, more evidence.

So the workflow puts the AI at the end, not the start:

| I own | The AI owns |
|---|---|
| The stakeholder conversation — what was actually asked for | Drafting from the context I hand it |
| The design work in Figma | Structuring the PRD against a template |
| The before/after evidence and why it changed | Turning that evidence into requirements and acceptance criteria |
| Every judgment call — priority, scope, trade-offs | Catching gaps I missed |

**I bring the conversation and the design. The AI drafts the document around them.** Nothing in the output is a claim I haven't made myself.

---

## The workflow at a glance

```
  1. SETUP        OpenCode CLI + whatever model I actually have access to
        ↓
  2. REQUIREMENTS  Sit with the stakeholder — CEO, sales, ops — get the real ask  (no AI)
        ↓
  3. DESIGN & CONTEXT  Design in Figma, alternating with building a current-vs-new folder
        ↓
  4. GENERATE      Hand the AI the context folder + a template, review, refine
        ↓
  5. PUBLISH       Commit via CLI → GitHub Pages → shareable link
```

Full detail in **[the workflow](workflow/README.md)**. Steps 3 and 4 aren't strictly sequential — design and PRD writing go back and forth.

### Why these tools

**[OpenCode CLI](https://opencode.ai)** — an open-source terminal AI agent. It reads and writes files in the repo directly, so the PRD is a real file under version control from the first draft. Every revision is a commit.

**Whatever model I have access to.** In this repo that's Claude Haiku — because it's what my company provides on our OpenCode account, not because it's the strongest model out there. The reasoning in this workflow happens in steps 2 and 3, entirely by hand, before the AI is ever opened. What the model does in step 4 is draft against context that's already been assembled, and a mid-tier model handles that fine. If you're on a different model — including one of OpenCode's free options — see [workflow/01](workflow/01-setup-opencode.md) for the trade-offs.

**GitHub** — and this is the part that's easy to miss if you've only seen PRDs live in Notion or Google Docs. At my company, engineering pulls the PRD from GitHub to build from — sometimes literally feeding it into an AI coding tool as context for generating the implementation. The repo isn't a publishing convenience; it's where the document actually needs to live for the next step in the process to work. GitHub Pages on top of that is for people who just want to read it in a browser — the PRD being *in* GitHub is the part that matters to engineering, the Pages site is the part that matters to everyone else. More on this in [workflow/05](workflow/05-publish-to-pages.md).

---

## Use this yourself

No install, no account, no dependency on my setup. The templates are plain markdown — they work in OpenCode, Claude Code, ChatGPT, Gemini, or a Notion AI block.

```bash
git clone https://github.com/RaamPujanggaSadewa/prd-automation.git
```

Then:

1. Copy `templates/requirement-notes.md` and write it up after your own stakeholder conversation.
2. Copy `templates/version-context.md` twice — once for the current version of the product, once for the proposed new version — and fill both in alongside your Figma work.
3. Copy `templates/prd-template.md` into your own project as `PRD.md`, and hand everything to the AI with `prompts/01-generate-prd.md`.
4. Publish however you like.

If you're using OpenCode too, `templates/opencode.json` and `templates/AGENTS.md` will get you a matching setup in about two minutes — see **[workflow/01-setup-opencode.md](workflow/01-setup-opencode.md)**.

### A word on the parts with no AI in them

Steps 2 and 3 have no AI in them at all, and they're most of the work. A stakeholder conversation you actually understood, paired with a context folder that says specifically what changed and why, will give you a sharper PRD than any amount of prompt engineering on thin material.

If you take one thing from this repo, take that.

---

## Repo map

```
prd-automation/
├── workflow/          The five steps, in order
├── prompts/           The prompt — one, used in step 4
├── templates/         PRD template, requirement notes, version context, OpenCode config
└── case-study/        The worked example
```

---

## License

[MIT](LICENSE) — use it, fork it, change it, ship it. Attribution appreciated, not required.

Built by [Raam Pujangga Sadewa](https://github.com/RaamPujanggaSadewa).
