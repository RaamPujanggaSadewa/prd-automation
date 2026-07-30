# 04 — Critique & Refine

The draft is complete and it is not done. This step is what stops it reading like AI output.

30–45 minutes.

---

## Read it start to finish first

Before running anything, read the whole assembled draft in one sitting. Section-by-section review catches fabrication; only a full read catches these:

- **Contradictions across sections.** Requirement 3 assumes something the problem statement ruled out.
- **Drift.** By section 5, the document is arguing for something subtly different from section 1.
- **Repetition.** The same point made three times in three different registers.
- **Tonal seams.** Sections that don't sound like they came from the same author, because they didn't.

Fix these by hand. They're editorial judgment calls, and asking a model to smooth them tends to flatten the document into uniform blandness rather than making it coherent.

---

## Run the adversarial pass

```bash
opencode run -c "$(cat prompts/06-adversarial-critique.md)"
```

This asks the model to attack the draft: find unsupported claims, vague requirements, untestable acceptance criteria, and missing edge cases.

**It reports. It does not edit.** That's deliberate and it's set in `AGENTS.md`. A model given permission to fix its own critique will rewrite around the criticism — softening a claim until it's unfalsifiable rather than either supporting it or cutting it. You want the list, then your own decisions.

Expect 10–20 findings on a first draft. Roughly:

| Finding type | Usual verdict |
|---|---|
| Unsupported factual claim | Cut, or mark `[NEEDS DATA]` |
| Untestable acceptance criterion | Rewrite — genuinely useful catch |
| Vague requirement | Rewrite, usually by adding a boundary |
| Missing edge case | Often a real gap; sometimes correctly out of scope |
| "Consider adding a section on…" | Usually ignore — this is scope creep in critique clothing |

Not every finding is right. The model doesn't know your constraints and will flag deliberate scope decisions as omissions. Your job is triage, not compliance.

---

## The traceability pass

This is the one that matters most, and there's no shortcut for it.

Go through the PRD claim by claim. For each factual assertion, ask: **where did this come from?**

Three possible answers:

1. **It's in my brief** → fine, leave it.
2. **It's a reasonable inference from my brief** → fine, but check the document doesn't present it as observed fact.
3. **I can't trace it** → cut it, or mark `[NEEDS DATA]`.

Category 3 is why this step exists. These lines are indistinguishable in tone from categories 1 and 2 — that's the whole problem. A fabricated statistic doesn't announce itself; it sits in a sentence that reads exactly like the real ones around it. The only reliable detection is going line by line and checking the source.

I find two or three of these in every PRD I write with this workflow, no matter how carefully `AGENTS.md` is written. Budget for it.

---

## Where to write yourself

Some sections should be yours in your own words. I write or heavily rewrite:

**The problem statement.** It's the first thing anyone reads and the thing that carries your point of view. Model-drafted problem statements are structurally fine and rhetorically flat.

**Design rationale.** Why this approach and not the alternatives. This is the actual designer contribution and the reasoning is yours — a model can only restate what you already told it, so the restatement is strictly worse than the original.

**Anything expressing judgment.** Trade-offs, priority calls, what you'd cut under pressure. These are the lines a hiring manager reads closely.

The sections that benefit most from AI drafting are the structural ones: requirements, acceptance criteria, edge-case enumeration. Mechanical, high-volume, easy to verify. Let it do those.

---

## Final checklist

- [ ] Every factual claim traces to the brief, or is marked `[NEEDS DATA]`
- [ ] Every requirement has acceptance criteria a developer could test
- [ ] No contradictions between sections
- [ ] Problem statement is in your voice
- [ ] Design rationale includes rejected alternatives
- [ ] Scope boundary is stated explicitly — what's *out*, not just what's in
- [ ] No "leverage", "synergy", "seamless", "delight", "robust"
- [ ] Screenshots and annotations are in, and referenced from the text
- [ ] You'd be comfortable defending every line of this in a room

The last one is the real test. If there's a line you'd rather not be asked about, that's the line to fix.

---

**Next → [05 — Publish](05-publish-to-pages.md)**
