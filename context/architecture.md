# Architecture

Purpose: system boundaries, ownership, data flow, integrations, and invariants.

## Architecture Snapshot

| Area | Decision | Notes |
| ---- | -------- | ----- |
| Runtime or platform | [RUNTIME_OR_PLATFORM] | [WHY_THIS_CHOICE] |
| User interface | [UI_APPROACH_OR_NONE] | [WHY_THIS_CHOICE] |
| Data storage | [DATABASE_OR_STORAGE] | [WHAT_IT_OWNS] |
| Authentication | [AUTH_APPROACH_OR_NONE] | [WHAT_IT_PROTECTS] |
| Background work | [BACKGROUND_WORK_APPROACH_OR_NONE] | [WHAT_RUNS_ASYNC] |
| External services | [EXTERNAL_SERVICES] | [WHAT_THEY_PROVIDE] |
| Observability | [LOGGING_ANALYTICS_MONITORING] | [WHAT_TO_TRACK] |

Delete rows that do not apply.

## System Boundaries

Major project areas and ownership.

| Boundary | Owns | Must Not Own |
| -------- | ---- | ------------ |
| [BOUNDARY_1] | [RESPONSIBILITIES] | [OUT_OF_SCOPE_RESPONSIBILITIES] |
| [BOUNDARY_2] | [RESPONSIBILITIES] | [OUT_OF_SCOPE_RESPONSIBILITIES] |
| [BOUNDARY_3] | [RESPONSIBILITIES] | [OUT_OF_SCOPE_RESPONSIBILITIES] |

Example boundaries: interface layer, domain logic, persistence, API layer, automation, background jobs, reporting, infrastructure, integrations, tests, documentation.

## Data And State Ownership

Important data, sources of truth, and write ownership.

| Data or state | Source of truth | Written by | Read by |
| ------------- | --------------- | ---------- | ------- |
| [DATA_1] | [LOCATION] | [OWNER] | [CONSUMERS] |
| [DATA_2] | [LOCATION] | [OWNER] | [CONSUMERS] |
| [DATA_3] | [LOCATION] | [OWNER] | [CONSUMERS] |

Rules:

- Do not duplicate source-of-truth data unless the architecture explicitly calls for replication.
- Do not let presentation code own durable business state.
- Do not let integration adapters contain product policy unless the architecture assigns that responsibility there.

## Data Flow

### Primary Flow

```text
[ACTOR_OR_TRIGGER]
  -> [ENTRYPOINT]
  -> [VALIDATION_OR_POLICY]
  -> [CORE_BEHAVIOR]
  -> [PERSISTENCE_OR_OUTPUT]
  -> [USER_OR_SYSTEM_FEEDBACK]
```

### Background Or Asynchronous Flow

```text
[TRIGGER]
  -> [QUEUE_OR_JOB_RUNNER]
  -> [WORKER_OR_AGENT]
  -> [EXTERNAL_SERVICE_OR_INTERNAL_MODULE]
  -> [RESULT_STORAGE]
  -> [NOTIFICATION_OR_STATUS_UPDATE]
```

Remove flows that do not apply.

## Integration Boundaries

External systems, APIs, libraries, tools, and services that affect architecture.

| Integration | Used for | Boundary owner | Failure behavior |
| ----------- | -------- | -------------- | ---------------- |
| [INTEGRATION_1] | [PURPOSE] | [OWNER] | [FALLBACK_OR_ERROR_HANDLING] |
| [INTEGRATION_2] | [PURPOSE] | [OWNER] | [FALLBACK_OR_ERROR_HANDLING] |

Rules:

- Keep integration-specific code behind a small boundary.
- Normalize external responses before the rest of the project depends on them.
- Treat network, file, permission, and service failures as expected states.
- Never expose secrets in client-side code, logs, memory, or documentation.

## Error And Recovery Model

- User-facing failures should be clear, actionable, and free of raw internal details.
- Internal errors should include enough context to debug without leaking secrets.
- Retriable failures should be safe to retry.
- Partial failure behavior should be documented when work spans multiple systems.
- Long-running work should expose status, cancellation, or recovery behavior when appropriate.

## Invariants

Rules the project must not violate.

1. [INVARIANT_1]
2. [INVARIANT_2]
3. [INVARIANT_3]
4. [INVARIANT_4]
5. [INVARIANT_5]

Good invariants are specific enough to catch drift. If a rule would not change implementation, it probably belongs in `code-standards.md` instead.
