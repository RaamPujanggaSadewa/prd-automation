Review the full PRD.md as a hostile reader. Your job is to find everything wrong with it.

**Do not edit the file. Do not fix anything. Report only.**

This constraint is deliberate. If you rewrite while critiquing, you will soften weak claims until they can no longer be challenged rather than either supporting them or removing them, and the document will get worse while appearing to improve. Produce the findings; I will decide what to do about each one.

Read it as three different skeptics in turn.

---

## Pass 1 — The engineer

You have to build this. For each requirement:

- Is there any acceptance criterion you could not objectively test? Quote it.
- Does any criterion use an untestable word — intuitive, clear, easy, obvious, simple, fast, clean, seamless, user-friendly? Quote it.
- Does any requirement bundle multiple behaviours behind an "and"?
- Does any requirement assume a backend, API, or third-party capability that is asserted rather than confirmed?
- What edge case is missing? Check specifically: empty state, first use, offline, interrupted mid-flow, permission denied, maximum and minimum values, returning user with existing state.
- Is there any requirement you could not begin work on without asking a question? What's the question?

## Pass 2 — The skeptical stakeholder

You are not convinced this is worth doing.

- Which factual claim in this document is unsupported? List every one. Include any statistic, percentage, user behaviour, market fact, competitor detail, or performance figure that is stated without a source.
- Which claims are presented as observed fact but are actually inference?
- Where does the document assert a causal link it hasn't established — "because X, users do Y"?
- Is the problem statement specific enough to be arguable, or is it general enough that nobody could disagree with it? A problem nobody can disagree with is a problem nobody needs to solve.
- Are the metrics measuring the thing that matters, or the thing that is easy to count?
- Does any metric have a target without a real baseline?
- What is the strongest argument for *not* doing this? Does the document engage with it anywhere?

## Pass 3 — The editor

- Which two sections contradict each other? Quote both.
- Where does the document repeat a point it already made?
- Does the argument in the final sections match the problem framed at the start, or has it drifted?
- Which sentences carry no information — pure transition, or restating a heading?
- Any corporate filler: leverage, synergy, seamless, delight, robust, empower, streamline, holistic, best-in-class, move the needle?
- Where does the tone change noticeably between sections?

---

## Output format

Group by pass. For each finding:

- **Location:** section name and requirement/story/metric ID where applicable
- **Finding:** what's wrong, in one sentence
- **Quote:** the exact text at issue
- **Severity:** High (misleads a reader or blocks implementation) / Medium (weakens the document) / Low (polish)

Order each group by severity, highest first.

Then, at the end, two short lists:

1. **Unsupported claims** — every factual assertion you could not trace to evidence within the document. This list is the most important output; be exhaustive rather than diplomatic.
2. **The three changes** that would most improve this document, in order.

---

## Instructions on your own behaviour

**Be genuinely adversarial.** A critique that finds five polite issues is useless. A first draft of a document like this typically has ten to twenty real problems. Find them.

**Do not soften findings.** Do not add "overall this is strong" framing. I am not asking for balance; I am asking for the list of problems.

**Do not suggest new sections or features.** "Consider adding a section on internationalisation" is scope creep, not critique. Stay on what is in the document.

**Flag your own uncertainty.** If you cannot tell whether something is a genuine omission or a deliberate scope decision, say so and let me judge. Do not assume an omission is a mistake.

**Include claims you wrote yourself.** Earlier sections of this document were drafted in this same session. Do not treat them as trustworthy on that basis — they are the most likely place for an unsupported claim to be hiding, precisely because they sound consistent with everything around them.
