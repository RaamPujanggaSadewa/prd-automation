# Version Context — New

Same three screens, captured together in [`screens/after.png`](screens/after.png). The design direction: ship the fastest path to addressing the location problem, not the fullest one — an MVP scoped for speed to release rather than for completeness against the research.

1. **Search results.** Unchanged in layout. Each stop under the Pasteur Trans card now carries a short address line directly beneath the stop name — e.g. *"Stop Point Pasteur"* / *"Jl. Pasteur no 35, Pajajaran,..."* — as plain, truncated text. No map icon or interaction here; it's a lightweight signal at the point of comparing operators, not a full location tool.
2. **Fill In Details.** Unchanged. Deliberately not touched by this pass.
3. **Bus Details.** A new **Detail Route** section has been added, positioned between the rating line and Fleet Specifications. It lists both stops with their full street address, and a small map icon next to each stop name — tapping it opens the location in Google Maps.

---

## What changed and why

Both changes trace to the same finding in [`requirement-notes.md`](../../requirement-notes.md) — that pool names alone don't give users enough to locate a pickup point — but each is the lighter-weight version of what the research recommended:

- **Address helper text in the search list** addresses the research's "Full Street Address & Nearby Landmark" finding (rated 4.0/5, 25% must-have — the survey's P1, not its top-rated item). Implemented as plain text, not a redesigned card.
- **Full address + map icon in Bus Details** is the fuller version of the same finding, placed where there's room for it, plus the research's separate "Open in Google Maps / Waze" finding (4.25/5, also P1) — covered by linking out to Google Maps rather than building anything in-app.

## Deliberately deferred

The research's two highest-rated findings — both 4.5/5, both rated must-have by 75% of respondents — are **not** in this version:

- **An interactive map pin embedded inside Traveloka.** What shipped instead is a link out to the external Google Maps app, not an in-app map.
- **A "set as destination in Gojek/Grab" shortcut.** Not present anywhere in this version.

This is the actual trade-off behind the release: the two P0 items from the research are also the two most involved to build (an embedded map surface, a ride-hailing integration). The two P1 items — an address string and an outbound map link — are close to free by comparison. Choosing the cheaper pair first is a legitimate MVP call, but it means this version tests a narrower fix than the research pointed at, and the PRD should say so plainly rather than imply full coverage of the findings.

---

## Constraints

`[NEEDS DATA]` on anything formal — no stakeholder-confirmed timeline or budget exists for this case study. The MVP framing above is the designer's own scoping decision, stated here as exactly that.
