Write the "Success Metrics" section of PRD.md. Edit the file in place. Do not print the document back. Do not touch any other section.

Read the rules below before writing anything. This section has a specific failure mode and avoiding it matters more than filling the section out.

## The failure mode

The natural thing to write here is:

> Increase onboarding completion rate from 62% to 75% within one quarter.

That sentence contains a baseline, a target, and a timeframe, and it is worthless unless all three came from somewhere real. If the brief doesn't supply the 62%, then the 75% is arithmetic on a guess, and the whole metric is decoration. Worse, it reads more credible than an honest metric would — which is exactly what makes it a problem.

**A named measurement with an unknown baseline is more useful than a confident number that is made up.** Write the honest version.

## Format

For each metric:

**M-01 — [Metric name]**

- **What it measures:** the specific, countable thing
- **Why it matters:** which goal this indicates progress on (reference the ID)
- **Current baseline:** the figure from the brief, or `[NEEDS DATA] requires instrumentation`
- **Target:** a figure only if there is a real baseline; otherwise state direction — "expected to decrease" — and note the target must be set once a baseline exists
- **How to measure:** the specific event, funnel step, or query. Concretely enough that someone could implement it.

## Coverage

Three to five metrics. Include across them:

- At least one **primary** metric — the single number that most directly indicates the change worked
- At least one **counter-metric** — something that must *not* get worse. Every real change trades something off, and a metrics section without a counter-metric is measuring only the outcome you're hoping for.
- At least one metric measurable within days rather than quarters, so the team gets a signal before the full result is in

## Rules

**Do not invent baselines.** Not even approximate ones. Not "roughly 60%", not "industry average is around". If the brief doesn't have the number, you don't have the number.

**Do not invent targets.** A target without a baseline is not a target.

**Do not invent industry benchmarks or competitor figures.** These are the most tempting to fabricate because they sound like general knowledge. Mark them `[NEEDS DATA]`.

**Every metric must be measurable with something that exists or could plausibly be instrumented.** "User satisfaction with the new flow" is not measurable as written. "Completion rate of the flow, measured as sessions reaching playback ÷ sessions entering onboarding" is.

**No vanity metrics.** Total signups, page views, and time-in-app do not indicate whether this specific change worked. Tie each metric to a specific goal from the Goals section — if you can't, cut it.

**Plain language.** No "engagement uplift", "north star" framing, "actionable insights", "move the needle".

When finished: list the metric IDs, and separately list every `[NEEDS DATA]` marker you used so I can see exactly what needs instrumenting before this PRD is actionable.
