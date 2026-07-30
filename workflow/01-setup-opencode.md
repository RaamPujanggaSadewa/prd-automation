# 01 — Setup

Goal: a terminal AI agent that can read and write files in your PRD repo.

One-time. About ten minutes.

---

## Install OpenCode

Pick whichever fits your machine:

```bash
brew install sst/tap/opencode
```

```bash
npm install -g opencode-ai
```

```bash
curl -fsSL https://opencode.ai/install | bash
```

Check it landed:

```bash
opencode --version
```

---

## Connect a provider

```bash
opencode providers login
```

This opens an interactive picker. `opencode auth login` is an alias for the same thing, if that's the muscle memory you already have.

See what you actually have access to:

```bash
opencode providers list
opencode models
```

---

## About the model — pick whatever you actually have

**Use whatever model your setup gives you access to.** I use Claude Haiku because that's what my company provides on our OpenCode account — not because it's the strongest model available. Nothing in this workflow needs a frontier model; the reasoning happens in steps 2 and 3, which are entirely human, done before the AI is ever opened. What the model does in step 4 is draft against context I've already assembled, which a mid-tier model handles fine.

If your company gives you a specific model, use that. If you're paying out of pocket, pick on cost. Don't treat the model choice in this repo as a recommendation — it's just what I run.

**OpenCode also includes free models you can use with no separate provider account** — anything in `opencode models` ending in `-free`:

```bash
opencode models | grep free
```

There's a real downside: free-tier models are typically rate-limited and less capable than a paid model from the same family, and quality on longer or more technical PRD sections can be noticeably worse. Fine for trying the workflow out or for a low-stakes document; I wouldn't rely on one for anything going to a stakeholder without reading it closely.

Whatever you land on, confirm the exact string before continuing:

```bash
opencode models
```

That string is what goes in `opencode.json` below.

---

## Configure the project

Two files at the root of your PRD repo.

### `opencode.json`

```json
{
  "$schema": "https://opencode.ai/config.json",
  "model": "opencode/claude-haiku-4-5"
}
```

Copy from [`templates/opencode.json`](../templates/opencode.json), then replace the model string with whatever `opencode models` showed you.

### `AGENTS.md`

OpenCode reads this automatically at the start of every session and treats it as standing instructions. It's the highest-leverage file in the setup — it stops you re-explaining the ground rules every time.

Copy [`templates/AGENTS.md`](../templates/AGENTS.md). The rules that matter most:

- **Never invent evidence.** No user numbers, research findings, or business metrics that aren't in the context I've given it. Flag gaps instead of filling them.
- **Edit the file, don't reprint it.** Modify `PRD.md` in place.
- **Plain language.** No "leverage", "synergy", "seamless", "delight".

That first rule is the one doing the real work. Without it, a model asked for a PRD will happily produce `"users abandon at 34%"` because PRDs contain numbers like that, and the number is fabricated but looks exactly like a real one.

---

## Two ways to run it

**Interactive** — a TUI session, good when you're going back and forth with it on a section:

```bash
opencode
```

**One-shot** — good for a single, well-defined request:

```bash
opencode run "your prompt here"
```

Useful flags:

| Flag | Does |
|---|---|
| `-m, --model` | Override the model for one run |
| `-c, --continue` | Continue the previous session |
| `-f, --file` | Attach a file to the message |
| `--session` | Resume a specific session by ID |

Attaching a file is how context gets in — this is how the current-vs-new folder from [step 03](03-design-and-context.md) reaches the model in [step 04](04-generate-prd.md):

```bash
opencode run -f context/current/notes.md -f context/new/notes.md "Read both attached files and summarise what changed between the two versions. Don't write anything to disk yet."
```

If that comes back with an accurate summary and no invented detail, your setup is working.

---

## Keep credentials out of git

OpenCode stores provider credentials in `auth.json`. The [`.gitignore`](../.gitignore) in this repo already excludes it, along with `.env` and `*.key`. If you're starting a repo from scratch rather than forking this one, copy that file across before your first commit.

---

**Next → [02 — Requirement gathering](02-requirement-gathering.md)**
