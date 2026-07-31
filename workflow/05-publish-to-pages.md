# 05 — Publish

The PRD is markdown in a git repo, so publishing is mostly a settings toggle. About five minutes.

---

## Why this actually needs to be in GitHub

Not just why it's convenient — why it matters. At my company, engineering doesn't get the PRD handed to them as a document to read once and set aside. They pull it directly from the repo to build from. Increasingly, that means feeding it straight into an AI coding tool as context for generating the implementation — the PRD isn't only a spec a person reads, it's an input another tool consumes.

I don't know how universal this is elsewhere — every company's process is its own — but it's clearly not just us; AI-assisted engineering workflows that read repo context directly are becoming ordinary rather than novel. Worth assuming your reader might be a tool as well as a person.

Two consequences that follow from this, worth keeping in mind while you're still in [step 04](04-generate-prd.md):

- **Precision matters more than it would in a doc only a human skims.** An acceptance criterion that's slightly vague reads fine to a person who can ask a follow-up question in the hallway. Fed into a code-generation tool with no one to ask, that same vagueness becomes a wrong guess baked into the implementation.
- **The repo, not the Pages site, is the artifact engineering actually uses.** GitHub Pages (below) is for anyone who wants to read the PRD in a browser — a stakeholder, a reviewer, someone sharing it around. The raw files in the repo are what gets cloned, referenced by commit, or pointed at by a coding tool. Both matter; they're not the same audience.

---

## Commit and push

If OpenCode has been writing to `PRD.md` throughout, most of this is already committed. Final pass:

```bash
git add .
git commit -m "PRD: final draft, ready for engineering"
git push
```

Starting from scratch — create the repo and push in one go:

```bash
gh repo create prd-automation --public --source=. --remote=origin --push
```

`gh` needs to be authenticated (`gh auth status` to check). Use `--private` if you'd rather review before it's visible; you can flip it public later.

### Check what you're about to publish

Pushing a repo public makes everything in it public, including history. Before the first push:

```bash
git status --short          # what's staged
git log --oneline           # what's already committed
```

Confirm no credentials, no `auth.json`, no `.env`, no client-confidential material. The [`.gitignore`](../.gitignore) here covers the usual suspects, but it only helps if it was in place before the commit that would have caught the secret. If something sensitive is already in history, rotate it — removing the file in a later commit does not remove it from the repo.

---

## Enable GitHub Pages

In the repo on github.com:

1. **Settings** → **Pages**
2. Under **Build and deployment**:
   - **Source:** Deploy from a branch
   - **Branch:** `main`
   - **Folder:** `/ (root)`
3. **Save**

First build takes a minute or two. Your site lands at:

```
https://<username>.github.io/<repo-name>/
```

`README.md` becomes the homepage. Every other markdown file is served at its path — `workflow/04-generate-prd.md` → `/workflow/04-generate-prd`. Relative links between files keep working.

### Why deploy-from-branch and not Actions

GitHub also offers "GitHub Actions" as a Pages source, with more control over the build. Branch deploy is the better choice here:

- **No workflow file**, so nothing to maintain and nothing that can break your publish.
- **No `workflow` token scope needed.** Pushing anything under `.github/workflows/` requires a token with `workflow` permission — a common and confusing failure if your token doesn't have it. Branch deploy sidesteps it entirely.
- For rendering markdown, the extra control buys nothing.

### The `_config.yml`

[`_config.yml`](../_config.yml) at the root is what turns raw markdown into a styled page. Without it, Jekyll produces unstyled HTML — technically working, visually bare.

```yaml
title: PRD Automation
description: ...
theme: jekyll-theme-primer

defaults:
  - scope:
      path: ""
    values:
      layout: default
```

The `defaults` block applies the theme layout to every page, which is what lets the markdown files stay clean — no YAML front matter needed at the top of each one.

`jekyll-theme-primer` is GitHub's own theme, so it's already available on Pages with nothing to install. Swap in `minima` or any [supported theme](https://pages.github.com/themes/) if you prefer a different look.

---

## Troubleshooting

| Symptom | Cause |
|---|---|
| 404 on the site URL | Build hasn't finished, or the branch/folder in Settings doesn't match where your files are |
| Unstyled HTML | No `_config.yml`, or no `theme:` line in it |
| Markdown showing as raw text | A `.nojekyll` file is present — delete it; you *want* Jekyll here |
| Some pages 404 | Check the path case; `README.md` in a folder resolves to that folder's index |
| Front matter rendering as a table | A file has YAML front matter but the theme isn't applied — the `defaults` block handles this |

Build status and errors are under **Actions** in the repo, even with branch deploy — Pages runs its build there.

---

## Handing it to engineering

This is the part that actually matters, separate from anyone reading it for interest. Give engineering the repo, not the Pages link — they need the raw files, not the rendered page. In practice that's: the repo URL, and if it's useful to them, the direct path to `PRD.md` and the `context/` folder alongside it. If their tooling reads repo context directly, having the PRD committed and pushed *is* the handoff — there's no separate step where you export it into whatever they're using.

## Sharing it more broadly

For anyone reading it for interest rather than building from it — a stakeholder, a reviewer, your own network — the Pages link is what you send:

- **The link, not a PDF.** A URL that opens in one tap gets read; an attachment gets saved for later and never opened.
- **One specific finding**, not a summary of the process. "Two shelves on this screen look identical and are generated completely differently" starts a conversation. "I used AI to write a PRD" starts nothing.
- **The workflow link second.** People who want the method will follow it; leading with the method buries the work.
- **What the AI did and didn't do.** Being straight about this earns more credibility than implying it was all hand-written, and considerably more than implying the AI did the thinking.

The reason to make the workflow reusable is that a method other people can run is a more durable thing to be known for than a single document.

---

**Back to [the workflow index](README.md)** · **See [the result](../case-study/README.md)**
