# The Case Study

**Status: in progress.** Subject picked, requirement gathering done. Design and PRD generation are the remaining steps.

| | |
|---|---|
| **Subject** | [Traveloka](https://www.traveloka.com) — shuttle pickup location, in the bus/shuttle booking flow |
| **Requirement notes** | [`requirement-notes.md`](requirement-notes.md) — done |
| **Design & context** | [`context/current/`](context/current/notes.md), [`context/new/`](context/new/notes.md) — pending |
| **PRD** | Not started — depends on the design step above |

---

## Where this came from

Not a stakeholder conversation — a research insight. A [survey synthesis](https://github.com/RaamPujanggaSadewa/survey-automation/blob/claude/automated-survey-gemini-gy6b21/synthesis/shuttle-pickup-location.md) from a separate project found that most surveyed users booking Traveloka's Bandung–Jakarta shuttle route leave the app to check their pickup pool's location on Google Maps, because pool names like *"Stop Point Pasteur"* aren't specific enough to locate confidently — and that this has caused real failures (wrong pool, near-missed departures) for some of them.

[Step 02](../workflow/02-requirement-gathering.md) covers both ways a requirement can start: a conversation with whoever asked, or a research insight the data surfaced first. This case study is the second kind — nobody asked for this; the survey made the case for it. [`requirement-notes.md`](requirement-notes.md) is written up from that data, honestly caveated: four respondents supports a hypothesis worth building and testing, not a proven company-wide pattern.

---

## What's still needed

The design and context steps ([workflow/03](../workflow/03-design-and-context.md)) are genuinely pending, not filled in with a placeholder pretending otherwise — see the status notes in [`context/current/notes.md`](context/current/notes.md) and [`context/new/notes.md`](context/new/notes.md). That means real screenshots of Traveloka's current flow, and a real Figma design for the proposed one. Both are design work, which is the part of this workflow that has to be done by hand — the research names a direction, it doesn't design a screen.

Once those exist, [step 04](../workflow/04-generate-prd.md) runs as documented: hand the AI the context folder and requirement notes, generate against the template, review, refine.

---

## Structure

```
case-study/
├── README.md                    This page
├── requirement-notes.md         Done — the research and what it supports
├── context/
│   ├── current/notes.md          Pending
│   └── new/notes.md               Pending
└── PRD.md                       Not started
```

---

## One note on publishing

An in-progress case study, honestly labeled as such, is a more accurate signal than either an empty placeholder or a PRD generated ahead of the design work it's supposed to be built from. If you're reading this before the design step lands, that's the actual state of the example — not a gap I've papered over.
