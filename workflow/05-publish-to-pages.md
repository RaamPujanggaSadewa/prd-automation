# 05 — Publish

The PRD is markdown in a git repo, so publishing is mostly a settings toggle. About five minutes.

---

## Commit and push

If OpenCode has been writing to `PRD.md` throughout, most of this is already committed. Final pass:

```bash
git add .
git commit -m "PRD: final draft after critique pass"
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

`README.md` becomes the homepage. Every other markdown file is served at its path — `workflow/03-generate-prd.md` → `/workflow/03-generate-prd`. Relative links between files keep working.

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

## Share it

You now have a link that opens to a readable document instead of a file download.

What I include when I post it:

- **The link, not a PDF.** A URL that opens in one tap gets read; an attachment gets saved for later and never opened.
- **One specific finding**, not a summary of the process. "Two shelves on this screen look identical and are generated completely differently" starts a conversation. "I used AI to write a PRD" starts nothing.
- **The workflow link second.** People who want the method will follow it; leading with the method buries the work.
- **What the AI did and didn't do.** Being straight about this earns more credibility than implying it was all hand-written, and considerably more than implying the AI did the thinking.

The reason to make the workflow reusable is that a method other people can run is a more durable thing to be known for than a single document.

---

**Back to [the workflow index](README.md)** · **See [the result](../case-study/README.md)**
