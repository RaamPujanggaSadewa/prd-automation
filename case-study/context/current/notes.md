# Version Context — Current

The Traveloka bus/shuttle booking flow, Bandung → Jakarta, as it exists today. Three screens, captured together in [`screens/before.png`](screens/before.png):

1. **Search results.** The list of bus/shuttle options for the route. The Pasteur Trans card shows only stop names — "Stop Point Pasteur" departing, "Pasteur Trans Grogol" arriving — with no address, landmark, or location affordance of any kind.
2. **Fill In Details.** The booking form. The summary card at the top repeats the route, times, and operator; it carries no more location detail than the search results did.
3. **Bus Details.** The modal a user reaches by tapping through for more information on an operator. Shows the vehicle photo, rating, fleet specifications, facilities, and the reschedule/refund policy — but has no route or location section at all. A user who taps into this screen specifically to understand more about the trip still can't find out where the pickup point actually is.

---

## What's wrong

This confirms the friction described in [`requirement-notes.md`](../../requirement-notes.md): pool names like *"Stop Point Pasteur"* and *"Pasteur Trans Grogol"* appear throughout the booking flow with zero supporting location detail — not in the list, not in the booking form, and notably not even in the one screen (Bus Details) where a user might reasonably expect to find it. There's no address, no landmark, and no way to open the location in a maps app without leaving Traveloka entirely.

This matches the survey's central finding directly: nowhere in the current flow can a user resolve where a pool actually is without going elsewhere to check.

---

## Constraints

None stated — this case study is research-driven rather than conversation-driven, so there's no stakeholder-confirmed technical or business constraint on file. See `requirement-notes.md`.
