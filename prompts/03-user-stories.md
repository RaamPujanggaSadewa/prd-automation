Write the "Users & Stories" section of PRD.md. Edit the file in place. Do not print the document back. Do not touch any other section.

## Primary user

One paragraph describing the specific user in the specific situation this PRD addresses.

Describe a situation, not a demographic. "Someone opening the app for the first time on mobile data, who has been recommended it by a friend and wants to hear one specific song" is useful. "Millennials aged 25–34 who value convenience" is not — nothing in a requirements document follows from it.

Take this from the brief. If the brief doesn't identify a user precisely, say so with `[NEEDS DATA]` rather than constructing a persona.

## Secondary users

Only if the brief identifies them. One or two sentences each. If it doesn't, omit this subsection entirely — do not invent stakeholders to fill it out.

## Stories

Five to eight user stories, in this format:

**US-01** — As a [specific user in a specific situation], I want to [action], so that [outcome].

Then, indented under each:
- **Traces to:** which problem from the brief this addresses

## Rules for stories

**Every story must trace to a problem in the brief.** The `Traces to` line is mandatory and must name a real finding. If you cannot fill it in, the story does not belong in this PRD — delete it rather than writing a plausible-sounding trace.

This is the most common failure in this section: stories that sound reasonable for a product of this type but address nothing the brief identified. They pad the document and weaken it, because a reader who checks will find them unsupported.

**The "so that" clause must be a user outcome, not a restatement of the action.**
- Bad: "...so that I can use the simplified onboarding"
- Good: "...so that I reach the song I came for without answering questions about genres I don't care about"

**No story should encode a solution.** "As a user, I want a skip button" is a design decision wearing a story's clothes. Write the need — "I want to get past setup steps that don't apply to me" — and let Requirements decide it's a skip button.

**Cover the failure paths.** At least one story should address what happens when things go wrong, are empty, or are interrupted. These are where real products break and where PRDs are usually silent.

**Do not invent evidence.** No frequencies ("users often…"), no percentages, no research findings not present in the brief.

**Plain language.** No "leverage", "seamless", "delight", "empower", "streamline".

When finished, list the story IDs and confirm each one's trace. If any story is weakly traced, say which and why — don't quietly leave it in.
