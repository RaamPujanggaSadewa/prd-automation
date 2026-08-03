# Requirement Notes — Traveloka Shuttle Pickup Location

---

## Where this came from

**Type:** Research insight

- **Method:** Survey, run against a hypothesis that vague shuttle pool naming causes users to leave the Traveloka app to check locations elsewhere before booking. The synthesis was produced with AI assistance from the raw survey responses.
- **Sample / scope:** 4 respondents, Bandung ↔ Jakarta bus/shuttle route.
- **Confidence:** Small. Four respondents is enough to say a hypothesis is worth investigating and to point at a plausible direction — it is not enough to claim a company-wide pattern or to size the actual business impact. Every percentage below is "3 or 4 out of 4," not a statistically meaningful rate. Treat this PRD as a case for building and testing something, not as proof it will move a number.
- **Source:** [`shuttle-pickup-location.md`](https://github.com/RaamPujanggaSadewa/survey-automation/blob/claude/automated-survey-gemini-gy6b21/synthesis/shuttle-pickup-location.md), from a separate research-synthesis project. Included here as an example of research-driven requirement gathering — see [workflow/02](../workflow/02-requirement-gathering.md).

---

## What triggered this

The hypothesis under test: shuttle pool names shown in the Traveloka booking flow (e.g., *"Stop Point Pasteur"*, *"Pasteur Trans Grogol"*) are too vague for users to locate confidently, so they leave the app to check Google Maps or a ride-hailing app before completing a booking.

The survey found:
- 3 of 4 respondents said they leave Traveloka to check a pool's location on Google Maps or Gojek/Grab before paying, either almost every time or whenever the pool is unfamiliar.
- 2 of 4 reported a real failure caused by this ambiguity — going to the wrong operator's pool (mistaking one operator's stop for a similarly-named competitor's), or arriving late enough to nearly miss their shuttle.
- All 4 respondents rated an in-app interactive map and a one-tap "set as destination in Gojek/Grab" shortcut at 4.5/5 average importance, with 3 of 4 rating each a 5/5 (must-have).

---

## Who's affected

Users booking bus or shuttle tickets on routes with multiple similarly-named or ambiguously-located pickup pools — the Bandung ↔ Jakarta route specifically in this data, plausibly other routes with the same pool-naming pattern, though that's outside what this survey covered.

---

## What "done" looks like

No stakeholder to ask, since this is research-triggered — this is a proposal built from what the data supports, not something someone requested in these terms.

Based on the synthesis's own findings, in rough priority order:
- A user can identify exactly where their pickup pool is without leaving the Traveloka app — addressed directly by the top two findings (map + ride-hailing shortcut), both rated 4.5/5.
- A user can distinguish their booked pool from a similarly-named nearby one — addressed by the "prevent operator confusion" finding (landmark tags), rated lower (4.0/5, 25% must-have) and treated as secondary.
- A user can get to and from the pool more easily on either end of the trip — the first/last-mile ride-hailing shortcut, same 4.5/5 finding as above.

---

## Fixed vs. negotiable

`[NEEDS DATA]` — not established. This is research-triggered rather than conversation-triggered, so there's no stakeholder-stated budget, timeline, or off-limits system. A real version of this PRD would need that conversation before requirements harden into commitments.

---

## Who else signs off

`[NEEDS DATA]` — not established, for the same reason.

---

## The one-sentence summary

A small survey found most Traveloka shuttle bookers on the Bandung–Jakarta route leave the app to check pickup pool locations elsewhere, sometimes leading to real errors like the wrong pool or a missed departure, and rated an in-app map plus a ride-hailing shortcut as the clearest fix.
