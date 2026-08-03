# The Case Study

**Status: in progress.** Requirement gathering and design are both done. PRD generation is the remaining step.

| | |
|---|---|
| **Subject** | [Traveloka](https://www.traveloka.com) — shuttle pickup location, in the bus/shuttle booking flow |
| **Requirement notes** | [`requirement-notes.md`](requirement-notes.md) — done |
| **Design & context** | [`context/current/`](context/current/notes.md), [`context/new/`](context/new/notes.md) — done |
| **PRD** | Not started |

---

## Where this came from

Not a stakeholder conversation — a research insight. A [survey synthesis](https://github.com/RaamPujanggaSadewa/survey-automation/blob/claude/automated-survey-gemini-gy6b21/synthesis/shuttle-pickup-location.md) from a separate project found that most surveyed users booking Traveloka's Bandung–Jakarta shuttle route leave the app to check their pickup pool's location on Google Maps, because pool names like *"Stop Point Pasteur"* aren't specific enough to locate confidently — and that this has caused real failures (wrong pool, near-missed departures) for some of them.

[Step 02](../workflow/02-requirement-gathering.md) covers both ways a requirement can start: a conversation with whoever asked, or a research insight the data surfaced first. This case study is the second kind — nobody asked for this; the survey made the case for it. [`requirement-notes.md`](requirement-notes.md) is written up from that data, honestly caveated: four respondents supports a hypothesis worth building and testing, not a proven company-wide pattern.

---

## The design decision

The research's two highest-rated findings — an embedded in-app map, and a one-tap Gojek/Grab shortcut — are both fairly involved to build. The design direction taken here deliberately doesn't attempt either. It ships the two cheaper findings instead: a short address helper added to the search list, and a full address plus an outbound Google Maps link added to the Bus Details screen, which had no location information at all before.

That's a real MVP trade-off, not a compromise hidden in the fine print — see [`context/new/notes.md`](context/new/notes.md) for exactly what shipped, what was deferred, and why. The PRD needs to carry that trade-off explicitly rather than read as if it fully addresses the research.

---

## Structure

```
case-study/
├── README.md                    This page
├── requirement-notes.md         Done — the research and what it supports
├── context/
│   ├── current/
│   │   ├── notes.md               Done
│   │   └── screens/before.png
│   └── new/
│       ├── notes.md               Done
│       └── screens/after.png
└── PRD.md                       Not started
```

---

## What's next

[Step 04](../workflow/04-generate-prd.md): hand the AI the context folder and requirement notes, generate against the template, review, refine.

---

## One note on publishing

An in-progress case study, honestly labeled as such, is a more accurate signal than either an empty placeholder or a PRD generated ahead of the design work it's supposed to be built from.
