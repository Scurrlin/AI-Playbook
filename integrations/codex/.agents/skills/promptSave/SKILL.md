---
name: promptSave
description: Design, optimize, and document a prompt or GPT so the result is a reusable, governed asset instead of a one-off. Aligns on the use case, tests against real cases, and captures the pattern for the team to reuse.
---

A good prompt is not the one that worked once in the chat window. It is the one that works reliably across the cases that matter, that someone else can understand, and that the team can reuse without rebuilding it from scratch.

This skill turns an idea for a prompt or GPT into a documented, tested asset. It is the difference between a clever one-off and a repeatable operating model.

This is a design session. Build the asset deliberately, then prove it works before calling it done.

## Step 1 — Understand the Use Case

Before writing any prompt text, understand what this is actually for.

- Who uses it, and how often?
- What task does it do, and what decision or workflow does the output feed?
- What inputs will be available when it runs?
- What does good output look like — and what does unacceptable output look like?

Read `context/ai-standards.md` and check whether an existing prompt or GPT already covers this. Reuse or extend before building new.

If the use case is unclear, ask before drafting. A prompt built on a fuzzy use case will be fuzzy.

## Step 2 — Define Success and Test Cases First

Decide how you will know the prompt works before you write it.

Write down representative inputs and the behavior you expect for each:

- Typical cases — the everyday inputs this will see.
- Edge cases — empty input, partial input, unusually large or unusual input.
- Adversarial cases — inputs that try to pull the model off task or out of bounds.

These cases are the bar the prompt has to clear. Do not write them after the fact to match what the prompt already does.

## Step 3 — Draft the Prompt or GPT

Now write it. Follow the design rules in `context/ai-standards.md`:

- A clear role, task, and scope.
- The expected input and the exact output shape.
- Worked examples when the output is specific or easy to get wrong.
- Explicit guardrails: what it must not do, and how it should refuse or escalate.

Keep it as short as it can be while staying unambiguous.

## Step 4 — Test and Optimize

Run the draft against the cases from Step 2.

- Where output is wrong, weak, or off-task, identify why before changing the prompt.
- Tighten instructions, add an example, or strengthen a guardrail to address the root cause.
- Watch for hallucination and fabricated detail; confirm claims that can be checked.
- Re-run the full set after each meaningful change so a fix does not break another case.

Stop when the prompt clears the bar across the cases, not when it passes once.

## Step 5 — Document as a Reusable Asset

Capture what the team needs to reuse and govern it. Keep the asset and its notes where the project stores reusable AI patterns.

```
## [Asset Name]

### Use case
[Who uses it, the task, and the workflow it supports]

### Input and output
[What it takes in, and the exact shape it returns]

### Guardrails
[What it must not do; how it refuses or escalates]

### Known limits
[Where it is weak, what it should not be trusted for]

### Governance
[Owner, approval status, model used, version, last tested date]
```

Flag anything sensitive: if real data was used in testing, confirm none of it is embedded in the documented asset.

## What This Session Is Not

This is not a one-off prompt thrown into a chat. The output is an asset other people will reuse, so it is designed, tested, and documented like one.

This is not done when the prompt produces something good once. It is done when it behaves reliably across the cases that matter and the pattern is captured for reuse.
