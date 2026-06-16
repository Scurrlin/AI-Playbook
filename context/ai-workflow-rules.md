# AI Workflow Rules

Purpose: collaboration rules for planning, building, reviewing, remembering, and recovering.

## Start With Context

Before planning or implementing:

1. Read `AGENTS.md`.
2. Read the relevant files in `context/`.
3. Read the matching slash skill in `skills/` when one applies.
4. Inspect the current project state instead of assuming it matches the docs.

If the docs and the project disagree, call that out. Decide whether the code or the docs are the source of truth before continuing.

## Skill Workflows

Matching workflows:

- `/architect` -> `skills/architect/SKILL.md`
- `/review` -> `skills/review/SKILL.md`
- `/remember save` and `/remember restore` -> `skills/remember/SKILL.md`
- `/recover` -> `skills/recover/SKILL.md`
- `/imprint` -> `skills/imprint/SKILL.md`

When a workflow applies, read the matching skill file and follow it.

## Clarify Intent Before Building

Make sure these are clear:

- Goal: what outcome the user wants.
- Success criteria: how the user will know it works.
- Audience: who the work is for.
- Scope: what is in and out.
- Constraints: technical, product, legal, operational, design, or time limits.
- Tradeoffs: decisions that would change the implementation.

Ask only questions that materially change the work. Do not ask for information that can be discovered from the project.

## Plan The Smallest Useful Increment

Break work into increments that can be completed and verified.

Split the work if it combines unrelated changes, crosses multiple system boundaries, or cannot be checked end to end quickly.

A good implementation step has:

- A clear behavior change.
- A small set of affected files or areas.
- A verification method.
- A known stopping point.

## Build In Scope

- Do the requested work, not adjacent improvements.
- Prefer existing patterns over inventing new ones.
- Keep edits close to the feature or issue being addressed.
- Do not rewrite unrelated files.
- Do not install dependencies without approval or a documented reason.
- Do not hide uncertainty behind confident implementation.

## Keep Context In Sync

Update the relevant context file when work changes:

- Product scope or user flows.
- Architecture boundaries or data ownership.
- Code standards or project conventions.
- Library, service, or tool usage.
- Build plan status or next steps.
- UI patterns that should be reused.

The context should describe the real current state, not the hoped-for state.

## Review Before Moving On

After a feature or fix:

1. Compare the result to the plan.
2. Check architecture and ownership boundaries.
3. Check code standards and project conventions.
4. Verify error states, empty states, edge cases, and failure behavior.
5. Run relevant automated or manual checks.
6. Record remaining risks or follow-up work.

Use `/review` by reading `skills/review/SKILL.md` when the user asks for a review or when a change is large enough to deserve one.

## Preserve Memory

At meaningful stopping points, save only the context a future session needs:

- What changed.
- What decisions were made.
- What works now.
- What is incomplete or risky.
- What should happen next.

Do not store secrets. Use `/remember save` and `/remember restore` by reading `skills/remember/SKILL.md`.

## Recover Deliberately

When work goes wrong, diagnose the failure mode before trying another fix.

- If one specific thing is broken, find the root cause and fix it directly.
- If repeated fixes made the session messy, stop and create a clean reset note.
- If the foundation is wrong, revisit the assumption before rebuilding.

Use `/recover` by reading `skills/recover/SKILL.md` when debugging turns into churn.
