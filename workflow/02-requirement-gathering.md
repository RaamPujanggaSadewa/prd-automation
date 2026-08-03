# 02 — Requirement Gathering

**No AI in this step.** The point is to have real evidence before anyone opens a model — where that evidence comes from varies.

Two ways this step usually starts:

- **A conversation.** Someone in the office asks for something — a person with a specific complaint, deal, or process problem.
- **A research insight.** Data surfaces a problem before anyone asks for anything — a survey, usage data, interviews, support tickets. Nobody requested the work yet; the evidence is what makes the case for it.

Same output either way: [`requirement-notes.md`](../templates/requirement-notes.md), filled in well enough that step 04 can draft from it without guessing.

---

## If it's a conversation

Not the end user of the product — the person who requested this piece of work. Depending on the request, that's usually one of:

- **The CEO or a founder**, for a strategic or high-visibility change
- **Sales**, when the ask is driven by a deal, a client complaint, or something prospects keep asking for
- **Ops**, when it's an internal efficiency problem — something is slow or manual that shouldn't be

Who it is changes what you're listening for. Sales will describe the problem in terms of a specific deal or a specific client's complaint — the job is to figure out how much of that generalizes. Ops will describe a process, and the problem is often buried in the middle of an explanation of how things currently work. The CEO will usually give you the least detail and the most authority to fill in the rest, which is its own kind of trap if you fill it in wrong.

By the end of the conversation you should be able to answer:

- **What triggered this.** A specific incident, a recurring complaint, a metric, a strategic call. If it's "we should just improve X", push for the specific thing that made them say that today rather than last month.
- **Who's affected**, and how you'd recognize them. Internal team, external customers, one specific client, a segment.
- **What "done" looks like to them.** Not a feature — an outcome they'd recognize. Different stakeholders often want structurally different things from the same request, and this is where you find that out before you've built anything.
- **What's fixed and what's negotiable.** Timeline, budget, which parts of the system they won't let you touch, anything already promised to someone else.
- **Who else needs to sign off**, if anyone. Save yourself a second round by asking now.

If the conversation doesn't naturally answer one of these, ask directly. It's a much cheaper question now than a wrong PRD later.

---

## If it's a research insight

No one to interview — the evidence exists before the ask does. A survey, interview notes, analytics, support ticket patterns. The job here is different: instead of listening for what someone means, you're checking whether the data actually supports doing something about it.

What to establish before writing it up:

- **What was measured, and how.** Survey, interviews, usage data, tickets — and enough about the method that a reader can judge how much weight to put on it.
- **How much to trust it.** Say the sample size and the limitations plainly. Four survey respondents can validate a hypothesis worth investigating further; they don't prove a company-wide pattern. Understating this is how a thin finding ends up load-bearing in a PRD it can't support.
- **What the data actually shows**, distinct from what you'd like it to show. A finding with a clear number attached ("75% did X") is worth more here than a vibe about what users probably want.
- **Who's affected**, same as the conversation case — inferred from who the data covers, not assumed.
- **What "done" would look like** if you acted on this. Since there's no stakeholder to ask, this is your own judgment call — write it as a proposal, not as something someone told you.

---

## Capture it

Write it up right after — same day, while it's still accurate. Use [`templates/requirement-notes.md`](../templates/requirement-notes.md) or your own shorthand; the format matters less than doing it promptly and specifically.

The one-sentence summary you should be able to write from these notes: *what triggered this, what needs to happen, and how you'll know it's done.* If you can't write that sentence from your notes, follow up — talk to the stakeholder again, or dig further into the data — before moving on.

---

## Where this goes next

These notes are the anchor for everything after. When you're in [step 03](03-design-and-context.md) explaining the problem to the AI, or in [step 04](04-generate-prd.md) writing the actual PRD, this is what you're working from — not the AI's idea of what the problem probably is.

---

**Next → [03 — Design & context](03-design-and-context.md)**
