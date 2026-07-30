# Project Rules

<!--
Copy this file to the ROOT of your PRD repo as AGENTS.md.
OpenCode reads it automatically at the start of every session and treats it
as standing instructions, so you don't re-explain the ground rules each time.

Claude Code reads CLAUDE.md instead — same content works, just rename it.
-->

This repo contains a product requirements document. You are helping write it.

## What this document is

A PRD built from a stakeholder conversation and a folder showing the product's current version against a proposed new version. `requirement-notes.md` and the `context/current/` and `context/new/` folders are the source of truth for every factual claim in the PRD. The reasoning and the design judgment belong to the author; your job is drafting from the evidence you've been given, staying consistent, and flagging gaps.

## Hard rules

**1. Never invent evidence.**

Do not write statistics, percentages, user counts, completion rates, research findings, competitor data, industry benchmarks, revenue figures, latency numbers, or platform limitations unless they appear in `requirement-notes.md` or the context folder.

This applies to figures that sound plausible, conservative, or obviously illustrative. A made-up number is indistinguishable from a real one once it's in the document, which is exactly what makes it dangerous.

When a section would read better with a figure you don't have, write `[NEEDS DATA]` and describe what would need measuring. That is always the correct move.

**2. Never assume technical capability.**

Do not assert what a backend, API, third-party service, or platform can or cannot do. If a requirement depends on it, mark it `[NEEDS DATA]` and name what needs confirming.

**3. Distinguish observation from inference.**

If something was stated in the notes, it can be written as fact. If it's your reasoning from what was stated, the wording must show that — "this suggests", "the likely consequence is". Never present inference as established fact.

**4. Edit files in place. Don't reprint them.**

Modify `PRD.md` directly. Do not dump the whole document into the conversation. Summarise what changed in two or three sentences after editing.

**5. Every requirement traces to something.**

Requirements trace to `requirement-notes.md` or a specific difference between `context/current/` and `context/new/`. If you cannot fill in that trace, do not write the requirement. Never write a plausible-sounding trace to something that doesn't exist in the source material.

**6. If asked to review rather than draft, report — don't silently rewrite.**

If the request is to review or critique what's already there, list the findings and stop; don't fold fixes in unasked. A rewrite folded into a critique tends to soften a weak claim until it can't be challenged, rather than actually supporting or removing it — the author should decide what happens to each finding.

## Writing style

**Plain language.** Never use: leverage, synergy, seamless, delight, robust, empower, streamline, holistic, best-in-class, move the needle, actionable insights, frictionless, elevate, unlock.

Write the way a person explains a problem to a colleague who will ask follow-up questions.

**No untestable acceptance criteria.** Never use intuitive, clear, easy, obvious, simple, fast, clean, user-friendly, or delightful in an acceptance criterion. These cannot be tested. Replace with the observable thing actually meant.

**No filler.** Every sentence carries information. Cut anything that only restates a heading or transitions without adding content.

**British or American spelling — match whatever the existing document uses.** Don't switch mid-document.

## Scope discipline

`requirement-notes.md` states what was actually asked for. Don't add requirements for adjacent features that weren't part of the conversation — however reasonable they seem. If something genuinely looks like a gap, say so in your summary rather than adding it unasked.

## Repo layout

| Path | What |
|---|---|
| `PRD.md` | The document being written |
| `requirement-notes.md` | From the stakeholder conversation — source of truth for the ask |
| `context/current/` | Screenshots and notes on the product as it exists today |
| `context/new/` | Screenshots and notes on the proposed version |
| `prompts/` | The prompt |
| `templates/` | Starting templates — don't edit these when working on a real PRD |

## Git

Commit as you go, with messages like `PRD: draft from context folder` or `PRD: rewrite problem statement by hand`. Small commits make the review diffs readable.

Never commit `.opencode/auth.json`, `.env`, or anything containing credentials.
