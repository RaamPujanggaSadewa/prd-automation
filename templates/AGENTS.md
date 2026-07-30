# Project Rules

<!--
Copy this file to the ROOT of your PRD repo as AGENTS.md.
OpenCode reads it automatically at the start of every session and treats it
as standing instructions, so you don't re-explain the ground rules each time.

Claude Code reads CLAUDE.md instead — same content works, just rename it.
-->

This repo contains a product requirements document. You are helping write it.

## What this document is

A PRD built from a design brief written by a designer. The brief is the source of truth for every factual claim in the PRD. The reasoning and the design judgment are the author's; your job is structuring, drafting from supplied evidence, and consistency.

## Hard rules

**1. Never invent evidence.**

Do not write statistics, percentages, user counts, completion rates, research findings, competitor data, industry benchmarks, revenue figures, latency numbers, or platform limitations unless they appear in the design brief.

This applies to figures that sound plausible, conservative, or obviously illustrative. A made-up number is indistinguishable from a real one once it's in the document, which is exactly what makes it dangerous.

When a section would read better with a figure you don't have, write `[NEEDS DATA]` and describe what would need measuring. That is always the correct move.

**2. Never assume technical capability.**

Do not assert what a backend, API, third-party service, or platform can or cannot do. If a requirement depends on it, mark it `[NEEDS DATA]` and name what needs confirming.

**3. Distinguish observation from inference.**

If something was observed, it can be stated as fact. If it's reasoning from what was observed, the wording must show that — "this suggests", "the likely consequence is". Never present inference as established fact.

**4. Edit files in place. Don't reprint them.**

Modify `PRD.md` directly. Do not dump the whole document into the conversation. After editing, summarise what changed in two or three sentences.

**5. One section per request.**

Write only the section asked for. Do not run ahead into sections that haven't been requested, and do not modify sections outside the request — earlier sections may have been hand-edited since you wrote them.

**6. Everything traces to something.**

Requirements trace to goals or stories. Stories trace to problems in the brief. If you cannot fill in a trace, do not write the item. Never write a plausible-sounding trace to a finding that doesn't exist.

**7. When critiquing, don't fix.**

If asked to review or critique, report findings only. Do not edit. A critique that rewrites as it goes softens weak claims until they can't be challenged, rather than supporting or removing them.

## Writing style

**Plain language.** Never use: leverage, synergy, seamless, delight, robust, empower, streamline, holistic, best-in-class, move the needle, actionable insights, frictionless, elevate, unlock.

Write the way a person explains a problem to a colleague who will ask follow-up questions.

**No untestable acceptance criteria.** Never use intuitive, clear, easy, obvious, simple, fast, clean, user-friendly, or delightful in an acceptance criterion. These cannot be tested. Replace with the observable thing actually meant.

**No filler.** Every sentence carries information. Cut anything that only restates a heading or transitions without adding content.

**British or American spelling — match whatever the existing document uses.** Don't switch mid-document.

## Scope discipline

The brief states what's out of scope. Respect it. Do not add requirements for adjacent features — notifications, sharing, settings, analytics dashboards — however reasonable they seem. If something genuinely seems like a gap, say so in your summary rather than adding it.

## Repo layout

| Path | What |
|---|---|
| `PRD.md` | The document being written |
| `design-brief.md` | Source of truth for all evidence |
| `prompts/` | The prompt library |
| `templates/` | Starting templates — don't edit these when working on a PRD |

## Git

Commit after each completed section, with a message like `PRD: add requirements section`. Small commits make the review diffs readable, which is the main reason this document lives in git.

Never commit `.opencode/auth.json`, `.env`, or anything containing credentials.
