# Code Standards

Purpose: engineering standards that apply across the project.

## Engineering Mindset

- Understand the feature and relevant context before editing.
- Keep changes focused on the requested scope.
- Prefer simple, readable implementation over clever abstraction.
- Fix root causes instead of layering workarounds.
- Build the smallest useful version that can be verified.
- Refactor when repetition or complexity is real, not predicted.
- Leave unrelated code and files alone.

## Minimal Implementation Ladder

Before writing code, stop at the first rung that holds:

1. Does this need to exist at all? If not, do not build it.
2. Does the standard library already do it? Use it.
3. Is there a native platform or language feature? Use it.
4. Does an already-installed dependency do it? Use it.
5. Is it one line? Write the one line.
6. Only then write the minimum implementation that works.

This reduces code, not rigor. Never cut trust-boundary validation, data-loss handling, security, or accessibility to make something shorter. The goal is code that is small because it is necessary, not golfed.

## Project Boundaries

- Follow the ownership rules in `context/architecture.md`.
- Keep durable business rules out of presentation-only code.
- Keep external service details behind integration boundaries.
- Keep tests and fixtures separate from production behavior unless the project deliberately shares them.
- Do not move responsibilities across boundaries without updating `context/architecture.md`.

## Types, Schemas, And Contracts

These rules apply whether the project uses static types, runtime schemas, protocol definitions, or documented data contracts.

- Validate unknown external input at the system boundary.
- Keep shared contracts small, explicit, and version-aware when needed.
- Prefer narrow data shapes over passing large unstructured objects through the system.
- Document required, optional, and nullable fields where that distinction matters.
- Do not silently accept malformed data.

## Naming And Organization

- Name files, modules, components, functions, jobs, and documents after the responsibility they own.
- Keep modules small enough that their purpose is obvious.
- Avoid catch-all utility areas unless the code is genuinely shared.
- Keep examples, fixtures, generated files, and source files clearly separated.
- Follow the project's existing naming conventions once they are established.

## Error Handling

- Handle expected failures explicitly.
- Do not use empty catch blocks or ignored error returns.
- Do not show raw internal errors to end users.
- Include enough diagnostic context in logs to debug safely.
- Avoid logging secrets, tokens, credentials, private data, or full external payloads unless explicitly sanitized.
- Make retry behavior safe and intentional.

## Dependencies

- Do not add a new dependency without a clear reason.
- Prefer the standard library, existing project tools, or established local patterns when they are sufficient.
- If a dependency is added, document why in `context/library-docs.md`.
- Avoid dependencies that force broad architecture changes unless the project explicitly chooses that tradeoff.
- Remove unused dependencies when they are no longer needed.

## Configuration And Secrets

- Keep secrets out of source files, docs, AI chats, logs, screenshots, and memory.
- Document required configuration keys without including real values.
- Clearly distinguish public configuration from private secrets.
- Fail loudly and early when required configuration is missing.
- Use environment-specific configuration intentionally.

## Comments And Documentation

- Comment why something non-obvious is done, not what obvious code does.
- Keep documentation close to the decision it explains.
- Update context docs when architecture, scope, workflows, or standards change.
- Remove stale TODOs or convert them into tracked work.
- Prefer precise notes over broad summaries that cannot guide future work.

## Verification

Every meaningful change should have an appropriate verification path.

- Run the smallest relevant check first.
- Expand verification when the change affects shared behavior, user workflows, data contracts, or system boundaries.
- Document checks that could not run and why.
- Do not claim a change is verified unless the check actually ran or was manually confirmed.
