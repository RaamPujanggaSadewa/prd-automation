# PRD — Shuttle Pickup Location

| | |
|---|---|
| **Status** | Draft |
| **Author** | Raam Pujangga Sadewa |
| **Last updated** | 2026-08-03 |
| **Scope** | Shuttle pickup location display |

---

## Problem

**AI-drafted, then rewrite yourself.**

A user booking a Traveloka bus or shuttle ticket on the Bandung–Jakarta route sees their pickup point identified only by a name — *"Stop Point Pasteur,"* *"Pasteur Trans Grogol"* — with nothing else to go on. No screen in the current booking flow shows an address, a landmark, or a way to view the location on a map, including the Bus Details screen, which exists specifically to give more information about a trip.

A survey of 4 users on this route found that 3 of them leave the Traveloka app to check a pool's location on Google Maps or a ride-hailing app before completing a booking — either almost every time, or whenever the pool is unfamiliar. For 2 of the 4, that ambiguity has caused a real failure: going to the wrong operator's pool after confusing it with a similarly-named one nearby, or arriving late enough to nearly miss their shuttle. The sample is small — four respondents is enough to say this is worth investigating, not enough to know how common it is across everyone booking this route.

The cost isn't abstract for the users it does affect. Going to the wrong pool or arriving late can mean missing a scheduled departure on a trip already paid for. And every trip out to Google Maps before booking is a moment the user has left Traveloka's flow, with no guarantee they come back to finish it there.

---

## Context

**AI-drafted.**

This covers the Traveloka bus/shuttle booking flow for the Bandung ↔ Jakarta route, specifically how a pickup or drop-off pool's location is communicated to the user — in the search results list, the Fill In Details booking form, and the Bus Details screen. It does not cover booking, payment, or any route other than the one the underlying research examined.

### Out of scope

- An interactive map embedded inside Traveloka — the survey's top-rated finding, not part of this version
- A "set as destination in Gojek/Grab" shortcut — also top-rated, not part of this version
- Any change to the Fill In Details screen — deliberately left untouched in this pass
- Routes other than Bandung ↔ Jakarta — the underlying survey doesn't cover them

---

## Goals

**AI-drafted.**

1. Let a user find out roughly where their pickup pool is without needing to leave the Traveloka app.
2. Give a user enough information to tell their booked pool apart from a similarly-named one nearby.
3. Reduce how often users leave the app to check a pool's location before booking.
4. Ship a first version quickly, rather than wait to build the research's full recommendation.

---

## Users & Stories

**AI-drafted.**

### Primary user

Someone booking a Traveloka shuttle on the Bandung–Jakarta route, choosing between several similarly-named operators — Pasteur Trans and a nearby competitor, for example — who doesn't already know exactly where each one's pool is.

### Stories

**US-01** — As someone comparing shuttle operators in the search results, I want to see roughly where a pool is located without leaving the list, so that I can judge how convenient it is before choosing one.
- **Traces to:** Goal 1; requirement-notes.md (3 of 4 respondents leave the app to check location)

**US-02** — As someone who has picked an operator, I want the Bus Details screen to show the pickup and drop-off addresses, so that I can look up or navigate to the exact location.
- **Traces to:** Goal 1; context/current/notes.md (Bus Details currently has no location information at all)

**US-03** — As someone unfamiliar with a pool's exact address, I want a way to open its location in Google Maps directly from Traveloka, so that I don't have to search for it myself in a separate app.
- **Traces to:** Goal 3; requirement-notes.md ("Open in Google Maps/Waze" finding, 4.25/5)

**US-04** — As someone who has confused two similarly-named pools before, I want enough distinguishing detail to tell my pool apart from a nearby one, so that I don't end up in the wrong place.
- **Traces to:** Goal 2; requirement-notes.md (2 of 4 respondents went to the wrong operator's pool)

---

## Design Direction

**Write yourself.** Assembled here from what's already stated in `context/new/notes.md` — see the note in Appendix → Method.

### Approach

Ship the two cheapest fixes for the location-ambiguity problem, not the two most-requested ones. The search results list gets a short address line under each stop name — plain text, no new interaction. The Bus Details screen, which previously had no location information at all, gets a new Detail Route section with the full address for both stops and a map icon that opens the location in Google Maps. Fill In Details is untouched.

The principle: get something shipped fast rather than wait to build the survey's top two findings — an embedded in-app map and a Gojek/Grab shortcut — which are both substantially more involved to build.

### Why this and not the alternatives

| Option | Why not |
|---|---|
| Embedded interactive map inside Traveloka (survey's top-rated finding, 4.5/5, 75% must-have) | More involved to build than an outbound link to Google Maps; deferred to keep this release fast |
| "Set as destination in Gojek/Grab" shortcut (also 4.5/5, tied top finding) | Requires a third-party integration; deferred for the same reason |

### Screens

**Before:** [`context/current/screens/before.png`](context/current/screens/before.png) — search results, Fill In Details, and Bus Details, as they exist today.

**After:** [`context/new/screens/after.png`](context/new/screens/after.png) — the same three screens, with an address line added to the search results and a new Detail Route section added to Bus Details.

REQ-01 and REQ-02 below map directly to what's visible in `after.png`.

---

## Requirements

**AI-drafted.** REQ-01 through REQ-03 describe what's already built in the design shown in `after.png`. REQ-04 through REQ-06 are proposed next steps that haven't been designed yet — their acceptance criteria are marked `[NEEDS DATA]` for that reason, not because they were skipped.

### Must have

**REQ-01** — The search results list shows a short address line beneath each pickup and drop-off stop name.
- **Why:** US-01, Goal 1
- **Acceptance criteria:**
  - Each stop name in an operator's card is followed by a line of address text (e.g., *"Jl. Pasteur no 35, Pajajaran,..."*).
  - The address text may be truncated to fit the card; no additional interaction is required to see it.
- **Edge cases:** A pool with no address on file — `[NEEDS DATA]` what the list shows in that case; not addressed in the current design.

**REQ-02** — The Bus Details screen includes a Detail Route section showing the full street address for both the pickup and drop-off stop.
- **Why:** US-02, US-04, Goal 1, Goal 2
- **Acceptance criteria:**
  - A Detail Route section is present on the Bus Details screen for a route with a pickup and drop-off stop.
  - Each stop shows its name and full street address.
  - The section appears between the operator rating line and Fleet Specifications, matching the position shown in `after.png`.
- **Edge cases:** A route with more than two stops — `[NEEDS DATA]` whether Detail Route handles more than the pickup/drop-off pair shown here.

**REQ-03** — Each stop's address in the Detail Route section has a map icon that opens the location in Google Maps.
- **Why:** US-03; requirement-notes.md ("Open in Google Maps/Waze" finding)
- **Acceptance criteria:**
  - Tapping the map icon next to a stop opens that stop's location in Google Maps.
- **Edge cases:** Google Maps not installed on the device — `[NEEDS DATA]`, behavior not specified.

### Should have

**REQ-04** — Add a landmark or other distinguishing detail next to a pool name that could be confused with a similarly-named nearby operator.
- **Why:** US-04; requirement-notes.md (2 of 4 respondents went to the wrong operator's pool); addresses the "nearby landmark" half of the source research's P1 finding, which isn't covered by REQ-01/REQ-02 alone
- **Acceptance criteria:** `[NEEDS DATA]` — not yet designed; no screen shows this. Needs a design pass before acceptance criteria can be written.
- **Edge cases:** `[NEEDS DATA]`

### Could have

**REQ-05** — Embed an interactive map showing the pool location directly inside Traveloka, instead of linking out to Google Maps.
- **Why:** requirement-notes.md (top-rated finding, 4.5/5, 75% must-have)
- **Acceptance criteria:** `[NEEDS DATA]` — deliberately deferred for this release; not designed. See Design Direction → Why this and not the alternatives.
- **Edge cases:** `[NEEDS DATA]`

**REQ-06** — Add a one-tap shortcut to set a pool as the destination in Gojek or Grab.
- **Why:** requirement-notes.md (top-rated finding, tied 4.5/5, 75% must-have)
- **Acceptance criteria:** `[NEEDS DATA]` — deliberately deferred for this release; not designed. See Design Direction → Why this and not the alternatives.
- **Edge cases:** `[NEEDS DATA]`

---

## Success Metrics

**AI-drafted.** No baseline exists for any of these yet — this is research-driven, not instrumented in production. Every target below is intentionally left open rather than guessed at.

**M-01 — Off-platform check rate before booking**
- **What it measures:** Share of users who leave the Traveloka app (to Google Maps or a ride-hailing app) before completing a shuttle booking on this route.
- **Why it matters:** Goal 3; the survey's central finding (3 of 4 respondents reported doing this)
- **Current baseline:** `[NEEDS DATA]` — the survey measured this by self-report from 4 respondents, not by in-product instrumentation.
- **Target:** `[NEEDS DATA]` — no target should be set until a real baseline exists.
- **How to measure:** `[NEEDS DATA]` — would need an event marking app backgrounding or an outbound map-icon tap during the booking flow, compared against completed bookings.

**M-02 — Wrong-pool or near-missed-departure incidents**
- **What it measures:** How often a user reports going to the wrong pool, or nearly missing their shuttle, due to location confusion.
- **Why it matters:** Goal 2; this is the more severe, real-world cost identified in the research (2 of 4 respondents affected), distinct from the app-switching friction alone.
- **Current baseline:** `[NEEDS DATA]` — the survey found this happened to 2 of 4 respondents historically; that isn't a rate that can be projected onto in-product volume.
- **Target:** `[NEEDS DATA]`
- **How to measure:** `[NEEDS DATA]` — likely a post-trip survey question or support-ticket tagging, since this isn't an in-app event today.

**M-03 — Booking completion rate for this flow (counter-metric)**
- **What it measures:** Share of users who start a booking on this route and complete it.
- **Why it matters:** The new address lines and Detail Route section add content to screens that didn't have it before; this shouldn't come at the cost of completed bookings.
- **Current baseline:** `[NEEDS DATA]`
- **Target:** Should not decrease from baseline.
- **How to measure:** Standard funnel measurement from search results view to completed booking, segmented to this route.

---

## Open Questions

**Write yourself.** Compiled here from what's already flagged as unresolved elsewhere in the source material — see the note in Appendix → Method.

- [ ] No confirmed timeline or budget exists for this work — it's research-triggered, not conversation-triggered, so there's no stakeholder commitment on file.
- [ ] No one has formally signed off on this direction yet.
- [ ] The survey is 4 respondents on one route — whether the same pattern holds on other routes, or at real scale, is unknown.
- [ ] Whether the deferred items (REQ-05, REQ-06) should be built next, or whether this version is sufficient on its own, isn't decided.
- [ ] REQ-04 (landmark disambiguation) hasn't been designed — how it would actually appear on screen is still open.
- [ ] No baseline exists yet for any Success Metric above — all instrumentation questions are open.

---

## Appendix

### Source material

[`requirement-notes.md`](requirement-notes.md) · [`context/current/`](context/current/notes.md) · [`context/new/`](context/new/notes.md)

### Method

This draft was generated by Claude in conversation, using the instructions in [`prompts/01-generate-prd.md`](../prompts/01-generate-prd.md) against `requirement-notes.md` and both `context/` folders — the same process [step 04](../workflow/04-generate-prd.md) documents for running via OpenCode.

Design Direction and Open Questions are marked "Write yourself" in the template because they should carry the author's own reasoning. Here they were assembled from what Raam had already stated in `context/new/notes.md`, rather than freshly authored, and haven't had his own pass yet — per the workflow, they should get one before this is treated as final.
