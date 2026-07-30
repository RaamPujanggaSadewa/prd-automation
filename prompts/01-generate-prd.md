You have been given several files: notes and screenshots for the current version of a product, notes and screenshots for the proposed new version, requirement notes from a discussion with a stakeholder, and a PRD template. Use all of them to draft a complete PRD.

Edit the PRD file in place, filling in the template's existing sections. Do not invent new sections or restructure the template.

## How to use each input

**Requirement notes** are the source of truth for who asked for this, why, and what "done" means to them. The Problem and Goals sections should be traceable to this file specifically — if the requirement notes don't support something you're about to write, don't write it.

**Current-version notes and screenshots** describe what exists today and what's wrong with it. Use them for the Problem and Context sections. Reference specific screens or steps by name, matching the filenames you were given, rather than describing them generically.

**New-version notes and screenshots** describe the proposed change. Use them for Design Direction, Requirements, and anywhere the document needs to say what the product will do differently. Every requirement should trace back to a specific difference between the current and new versions — if you can't point to what changed and why, don't write the requirement.

## Rules

**Do not invent evidence.** No statistics, user counts, completion rates, research findings, competitor data, or performance numbers unless they appear in the files you were given. If a section would read better with a figure you don't have, write `[NEEDS DATA]` and say what would need measuring. This applies even to numbers that sound conservative or illustrative — a wrong number is worse than an honest gap, because it reads exactly like a real one.

**Do not assume technical capability.** Don't assert what a backend, API, or platform can or cannot do unless it's stated in the notes. Mark it `[NEEDS DATA]` if a requirement depends on something you weren't told.

**Distinguish observation from inference.** If something is stated directly in the notes, you can state it as fact. If you're inferring it, say so — "this suggests", "the likely effect is" — rather than presenting inference as established fact.

**Every requirement needs a reason.** State which stated problem or requirement note it addresses. If you can't point to one, don't include the requirement.

**Acceptance criteria must be objectively testable.** Never use intuitive, clear, easy, simple, fast, clean, or seamless in a criterion — these can't be checked by someone who didn't write them. State the observable thing you actually mean.

**Plain language.** No "leverage", "synergy", "seamless", "delight", "robust", "empower", "streamline", "holistic", "best-in-class". Write the way you'd explain the problem to a colleague who's going to ask follow-up questions.

**No filler.** Every sentence should carry information particular to this product and this change — not something that could describe any product in this category.

## When you're done

Tell me, in a few sentences: what you drafted, anything in the source files that was too thin to work from, and every place you marked `[NEEDS DATA]` so I can see exactly what's still missing before this is ready to share.
