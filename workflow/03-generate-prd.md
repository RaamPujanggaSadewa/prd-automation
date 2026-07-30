# 03 — Generate

Six prompts, run in order. Each one reads what the previous one wrote and adds a section. 20–30 minutes.

---

## Set up the file

Copy the template in, then let the prompts fill it:

```bash
cp templates/prd-template.md PRD.md
```

`PRD.md` now has the section headings and nothing under them. The prompts fill one section each, in place.

---

## Why six prompts instead of one

You can ask for an entire PRD in a single prompt. I don't, for three reasons:

**Each output is small enough to actually check.** A 400-word section gets read properly. A 4,000-word document gets skimmed, and skimming is how fabricated claims survive into the final version.

**Mistakes stay local.** If the problem statement drifts from my brief, I fix that section and move on. In a single-shot document, a wrong premise in section 1 propagates through every section after it, and you end up regenerating the whole thing.

**Later sections get better inputs.** By the time prompt 04 writes requirements, it's reading a problem statement and user stories that I've already corrected. Generating everything at once means every section is derived from the raw brief, and none of them benefit from my edits to the others.

The cost of six prompts over one is about ten minutes. It's the best trade in the workflow.

---

## The sequence

Run these from the repo root. Full text of each is in [`prompts/`](../prompts/README.md) — copy it, or reference the file directly as shown.

### 01 — Teardown

Already done by hand in [step 02](02-design-inputs.md). The prompt file is a checklist for that work, not something you run here.

### 02 — Problem framing

```bash
opencode run -f design-brief.md "$(cat prompts/02-problem-framing.md)"
```

Writes the **Problem**, **Context**, and **Goals** sections of `PRD.md` from the brief.

Check before continuing: is the problem statement recognisably *your* problem, or has it been generalised into something safer? Models smooth specifics into abstractions by default. If "two adjacent shelves are visually identical but generated differently" has become "discovery lacks clarity", push back and re-run.

### 03 — User stories

```bash
opencode run -c "$(cat prompts/03-user-stories.md)"
```

`-c` continues the previous session, so the model still has the brief and the sections it just wrote in context.

Check: every story should map to a problem in the brief. Extra stories that sound plausible but trace to nothing are the most common failure here — delete them.

### 04 — Requirements

```bash
opencode run -c "$(cat prompts/04-requirements.md)"
```

The longest section, and the one to review most carefully. Each requirement gets acceptance criteria.

Check: any requirement asserting a technical constraint, third-party capability, or performance number you didn't supply. Those get cut or marked `[NEEDS DATA]`.

### 05 — Success metrics

```bash
opencode run -c "$(cat prompts/05-success-metrics.md)"
```

Check: this is the highest-risk section for invented numbers. A target like "increase completion by 15%" is meaningless without a baseline you actually have. If you don't have the baseline, the metric should name what to measure and state that the baseline is unknown — not guess at both.

### 06 — Adversarial critique

Belongs to [step 04](04-critique-and-refine.md). Don't run it in the same pass — you want to read the assembled draft first.

---

## Reviewing as you go

After each prompt, read the diff rather than the document:

```bash
git diff PRD.md
```

This is the main reason the PRD lives in git from the first draft. The diff shows exactly what changed, and reviewing a 30-line diff is a completely different activity from re-reading a growing document. Anything fabricated shows up as a line you don't recognise.

Commit after each section you're happy with:

```bash
git add PRD.md && git commit -m "PRD: add problem framing"
```

Small commits mean you can always fall back one section instead of starting over.

---

## Three failure modes and what to do

**Confident invention.** The draft states a fact you never supplied — a percentage, a user behaviour, a platform limitation. It reads exactly like the real content around it, which is what makes it dangerous. Cut it, and if the section needs that fact to work, mark it `[NEEDS DATA]` and move on. Tightening `AGENTS.md` reduces the rate but never to zero, so the review step stays mandatory.

**Smoothing.** Your sharp, specific finding comes back as a generic industry observation. Re-run the prompt with the specific language quoted back: *"Use the exact framing from the brief: two adjacent shelves, visually identical, different generation logic. Don't generalise it."*

**Scope creep.** The model adds requirements for adjacent features you never scoped in — notifications, sharing, settings. Delete them. Then note that this happened, because it usually means your brief's scope boundary was implied rather than stated. Fix it in the brief, not in the prompt.

---

## Optional: save the prompts as commands

If you'll run this workflow more than once, OpenCode supports custom commands as markdown files in `.opencode/command/`:

```bash
mkdir -p .opencode/command
cp prompts/02-problem-framing.md .opencode/command/prd-problem.md
```

Then in the TUI, `/prd-problem`. Or from the shell:

```bash
opencode run --command prd-problem
```

Nice ergonomics once the prompts have stopped changing. Skip it on your first run — you'll want to edit the prompt text as you learn what your project needs, and that's easier in one place.

---

**Next → [04 — Critique](04-critique-and-refine.md)**
