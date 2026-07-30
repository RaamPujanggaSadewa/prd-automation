# Heuristic Teardown Checklist

Work through the product's primary flow, one screen at a time. For each screen, answer only the questions that apply — this is a set of lenses, not a form to complete.

Record findings in your own notes. They become the "Problems found" section of the design brief.

## Per screen

1. What is the single job this screen is trying to do?
2. What is the user trying to do here? Are those the same thing?
3. What does this screen ask the user to supply, decide, or remember that it could have inferred, defaulted, or carried forward?
4. Where does the visual hierarchy disagree with the actual priority of the content?
5. What is the most prominent element? Is it the most important one?
6. If the user does nothing, what happens? Is that the right default?
7. What is the error, empty, and loading state? Does the flow dead-end in any of them?

## Across the flow

8. Count the steps to the primary outcome. How many are strictly necessary?
9. Where is the first point the user gets something of value? How many screens precede it?
10. Which two screens do the same job but look or behave differently?
11. Which single step would you expect the most people to abandon at? Why that one?
12. What does the flow assume about the user's context — connection, prior knowledge, time available, device — that won't always hold?
13. Where does the product's own language differ from the words a user would use?
14. What can the user not undo?

## Turning findings into evidence

For each finding, write it out with three parts:

- **The observation.** The specific screen, step, or interaction. Not a category.
- **The evidence.** What you saw, counted, or tried. A screenshot reference where you have one.
- **The "so what".** Why this costs the user or the business something. If you can't answer this, it's an aesthetic preference rather than a problem, and it doesn't belong in a PRD.

## Specificity test

Each finding must survive a hostile "so what?" from someone who disagrees with you.

Not specific enough:
- "The navigation is confusing"
- "Onboarding is too long"
- "The empty state is bad"

Specific enough:
- "Five tabs, two of which show overlapping content with no stated distinction between them"
- "Seven screens before first value; three of them collect data the app could infer from first-session behaviour"
- "The empty saved-items state shows an illustration and no action, dead-ending the only exit from the primary flow"

If a finding reads like it could have been written without opening the product, rewrite it or drop it.

## Stop when

You have three to five findings that are specific, evidenced, and consequential. More than five and the PRD loses focus; fewer than three and there probably isn't a problem worth writing up.
