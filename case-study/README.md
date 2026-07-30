# The Case Study

**Status: not yet written.** This is the slot for the worked example — a complete PRD produced by running [the workflow](../workflow/README.md) end to end.

The workflow and toolkit in this repo are finished and usable without it. But this page is the one that proves the method produces something worth reading, so it's the one to fill next.

---

## The one adjustment for a public case study

At work, [step 02](../workflow/02-requirement-gathering.md) is a real conversation with whoever actually asked for the work. For a case study on someone else's public product, there's no real stakeholder in the room — so that step becomes a stated, honest simulation: write the requirement notes as if a specific person had asked for this, name the premise clearly in the PRD, and don't present it as a real conversation that didn't happen. Everything after that step runs exactly as documented.

---

## Candidate subjects

Not chosen yet. Options, with the trade-offs:

| Subject | Why it works | The catch |
|---|---|---|
| **LinkedIn feed / profile** | Cluttered by broad agreement, so a critique lands instantly. Sharing a LinkedIn redesign *on* LinkedIn is its own hook. | Heavily discussed already — needs a specific angle, not general complaints |
| **Spotify discovery** | Universally known, genuinely rich UX surface (shelves, recommendations, library) | Redesigned by many people; needs a sharper premise to stand out |
| **Gojek / Tokopedia super-app** | Super-app navigation overload is a meaty and under-covered problem. Strong local differentiation. | Slightly narrower global recognition |
| **Figma comments / handoff** | Designers know the pain firsthand — maximum credibility with the exact target audience | Niche outside that audience |

The pick matters less than the scope. **One flow.** Onboarding, or search, or the discovery shelf — not "the app". A tight PRD on a single flow demonstrates more product thinking than a sprawling one across five, because scoping is itself the skill on display.

---

## What goes here when it's done

```
case-study/
├── README.md              Overview: what, why, what came out of it
├── requirement-notes.md   The simulated stakeholder ask (step 02)
├── context/
│   ├── current/            Screenshots + notes on the product as it stands
│   └── new/                 Screenshots + notes on the proposed change
├── PRD.md                  The finished PRD
```

Publish the requirement notes and context folder alongside the PRD. Showing the input is what makes the output credible — otherwise a reader has to take on faith that the reasoning was there.

---

## How to fill it

1. Pick a subject and one flow within it.
2. Write the simulated requirement notes ([step 02](../workflow/02-requirement-gathering.md)).
3. Design in Figma and build the current-vs-new context folder ([step 03](../workflow/03-design-and-context.md)).
4. Generate and refine the PRD ([step 04](../workflow/04-generate-prd.md)).
5. Drop the files in here and rewrite this page as the overview.

---

## One note on publishing

Until this page has real content, it reads as an unfinished section on an otherwise complete repo — which undersells the rest of the work. Two reasonable options:

- **Keep the repo private** until the case study is in, then publish the whole thing at once.
- **Publish now** and treat this page as an honest, dated placeholder. Fine if the repo is being read as a toolkit; less good if it's being read as portfolio.

If the audience is designer peers looking for a method, the toolkit stands on its own and shipping now is defensible. If a hiring manager might see it, wait for the case study.
