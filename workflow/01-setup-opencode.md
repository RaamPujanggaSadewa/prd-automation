# 01 — Setup

Goal: a terminal AI agent that can read and write files in your PRD repo, running Claude Haiku 4.5.

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

There are two routes to Haiku, and they use **different model strings**. This trips people up, so check which one you're on:

```bash
opencode providers list
```

| If you see | Your model string is |
|---|---|
| **OpenCode Zen** | `opencode/claude-haiku-4-5` |
| **Anthropic** | `anthropic/claude-haiku-4-5` |

Both run the same underlying model. OpenCode Zen is a hosted gateway — one login, no separate API key to manage. The Anthropic route uses your own key from [console.anthropic.com](https://console.anthropic.com) and bills you directly.

Confirm what's actually available to you:

```bash
opencode models | grep haiku
```

Whatever that prints is the string to use everywhere below. The examples in this repo use the OpenCode Zen form.

---

## Why Haiku 4.5

| | Claude Haiku 4.5 |
|---|---|
| Model string | `claude-haiku-4-5` |
| Context window | 200K tokens |
| Cost | $1 / $5 per million tokens (in / out) |

A 200K context window holds a design brief, a full PRD draft, and a conversation about it several times over. For this workload that's ample.

The reason to pick the small model is that **the reasoning in this workflow is mine, not the model's.** Steps 2 and 4 are where the thinking happens, and both are human-driven. What I need from the model is structuring, consistency, and drafting from evidence I hand it. Haiku does that well, returns fast enough that iterating feels like editing rather than waiting, and costs so little that a complete PRD lands in the tens-of-cents range.

Reaching for a frontier model here would be paying a premium for judgment I'm not delegating.

If you want to swap it, change one line in `opencode.json` — nothing else in the workflow depends on the model choice.

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

Copy from [`templates/opencode.json`](../templates/opencode.json). Swap the model string if `opencode models` told you something different.

### `AGENTS.md`

OpenCode reads this automatically at the start of every session and treats it as standing instructions. It's the highest-leverage file in the setup — it stops you re-explaining the ground rules every time.

Copy [`templates/AGENTS.md`](../templates/AGENTS.md). The rules that matter most:

- **Never invent evidence.** No user numbers, research findings, or business metrics that aren't in the brief. Flag gaps as `[NEEDS DATA]` instead of filling them.
- **Edit the file, don't reprint it.** Modify `PRD.md` in place. Don't dump the whole document into the chat.
- **One section per request.** Don't run ahead into sections I haven't asked for.
- **Plain language.** No "leverage", "synergy", "seamless", "delight".

That first rule is the one doing the real work. Without it, a model asked for a PRD will happily produce `"users abandon at 34%"` because PRDs contain numbers like that. The number is fabricated and it looks exactly like a real one.

---

## Two ways to run it

**Interactive** — a TUI session, best for step 4 where you're going back and forth:

```bash
opencode
```

**One-shot** — best for step 3, where each prompt is a discrete job:

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

Attaching a file is how the design brief gets in:

```bash
opencode run -f design-brief.md "Read the attached brief and summarise the three problems it identifies. Don't write anything to disk yet."
```

If that comes back with an accurate summary and no invented detail, your setup is working.

---

## Keep credentials out of git

OpenCode stores provider credentials in `auth.json`. The [`.gitignore`](../.gitignore) in this repo already excludes it, along with `.env` and `*.key`. If you're starting a repo from scratch rather than forking this one, copy that file across before your first commit.

---

**Next → [02 — Design inputs](02-design-inputs.md)**
