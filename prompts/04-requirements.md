Write the "Requirements" section of PRD.md. Edit the file in place. Do not print the document back. Do not touch any other section.

Group requirements under the three priority headings already in the template: Must have, Should have, Could have.

## Format

Each requirement:

**REQ-01** — [One sentence stating what the product must do.]

- **Why:** which goal or story this serves (reference the ID)
- **Acceptance criteria:**
  - [Testable condition]
  - [Testable condition]
- **Edge cases:** [what happens when empty, offline, interrupted, at limits — or `None identified`]

## Rules for requirements

**One requirement, one behaviour.** If a requirement contains "and", check whether it should be two. A requirement that bundles three behaviours cannot be partially delivered, partially tested, or partially cut, which makes it useless for planning.

**State what, not how.** "The system must let the user reach playback without completing genre selection" is a requirement. "Add a Skip link in the top-right corner at 14px" is a design spec. Design specs belong in the design section or in Figma, not here.

**Every requirement traces to a goal or story.** The `Why` line is mandatory and must reference a real ID from the sections above. If you can't trace it, don't write it.

**Priority means something.** Must have = the release is pointless without it. Should have = significant value lost, but shippable. Could have = genuine improvement, first thing cut under pressure. If more than about half your requirements are Must have, the prioritisation isn't doing any work — reconsider.

## Rules for acceptance criteria

This is the part developers and QA actually use. Get it right.

**Each criterion must be objectively checkable.** Someone who didn't write it must be able to determine pass or fail without asking you.

- Untestable: "The flow feels fast"
- Testable: "Playback begins within 2 seconds of tap on a 3G connection" — but only include a number like this if the brief supplies it; otherwise write `[NEEDS DATA] target latency not specified`
- Untestable: "The distinction between the two shelves is clear"
- Testable: "Each shelf displays a one-line label stating what generated it, visible without scrolling or tapping"

**Never use these words in a criterion:** intuitive, clear, easy, obvious, simple, fast, clean, delightful, seamless, user-friendly. They cannot be tested. If a criterion needs one of them, it isn't finished — replace it with the observable thing you actually mean.

**Two to four criteria per requirement.** One is usually insufficient. More than four usually means the requirement should be split.

## Rules for edge cases

Consider each requirement against: empty state, first use, offline or slow connection, interrupted mid-flow, permission denied, maximum and minimum values, returning user with existing state.

Only list the ones that genuinely apply. Write `None identified` rather than padding.

## Do not invent evidence

No performance targets, technical constraints, platform limitations, third-party API capabilities, latency figures, or data-volume numbers unless they appear in the brief.

This section is where fabrication is most likely and hardest to spot, because invented technical constraints read exactly like real ones. If a requirement needs a number or a platform fact you don't have, write `[NEEDS DATA]` and state what needs confirming.

Do not assume what any backend, API, or third-party service can do.

## Plain language

No "leverage", "seamless", "robust", "streamline", "empower", "holistic", "best-in-class".

When finished: list the requirement IDs by priority group, and separately list anything you marked `[NEEDS DATA]` so I can see what needs resolving.
