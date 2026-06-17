# Data Standards

Purpose: engineering standards for data work — ingestion, transformation, analysis, and visualization.

## Engineering Mindset

- Understand the data and its source before transforming it.
- Treat raw data as read-only; regenerate derived data instead of editing it in place.
- Prefer simple, inspectable transformations over clever pipelines.
- Make every result reproducible by someone who was not there when it was produced.
- Trust no input until it has been validated, including data from internal systems.

## Minimal Implementation Ladder

Before writing a new pipeline, model, or query, stop at the first rung that holds:

1. Does this analysis or dataset need to exist at all? If not, do not build it.
2. Does an existing query, table, view, or dataset already answer it? Use it.
3. Does a standard library or built-in function do it? Use it.
4. Does an already-approved tool or dependency do it? Use it.
5. Is it one query or one transformation? Write the one.
6. Only then build the minimum pipeline that works.

This reduces code, not rigor. Never cut validation, reconciliation, privacy handling, or reproducibility to make something shorter.

## Reproducibility

- Work must be deterministic and re-runnable from a clean state.
- Pin dependency versions and set random seeds where results depend on them.
- Avoid manual one-off steps that cannot be repeated; capture them as code or documented commands.
- Raw source data is read-only. Derived data is regenerated from raw data, never hand-edited.
- Record the data source, extraction date, and any filters applied to a dataset.
- A result that cannot be reproduced is not a result yet.

## Data Validation And Contracts

These rules apply whether the data is a dataframe, a table, an API response, or a file.

- Validate shape, types, and value ranges at ingestion, the way trust-boundary input is validated elsewhere.
- Document which columns or fields are required, optional, and nullable.
- Fail loudly on malformed, missing, or out-of-range data; do not silently coerce or drop it.
- State key assumptions explicitly (grain, units, time zone, currency, primary keys).
- Treat external query results and API payloads as untrusted until normalized.

## SQL Conventions

- List columns explicitly instead of `SELECT *` in anything durable.
- Qualify columns and join conditions so the relationship between tables is clear.
- Comment non-obvious business logic, filters, and edge-case handling.
- Keep transformations inspectable; prefer readable CTEs over deeply nested subqueries.
- Treat query results as an external boundary — validate row counts and key assumptions before relying on them.
- Avoid hidden side effects; separate read queries from writes intentionally.

## Notebooks And Exploration

- Notebooks are for exploration and communication, not durable production logic.
- Promote reusable or critical code out of notebooks into modules that can be tested.
- A notebook must run top to bottom from a fresh kernel (restart-and-run-all) before it is shared.
- Keep secrets, credentials, and large or sensitive outputs out of committed notebooks.
- Clear or scope output that would bloat version control or leak data.

## Visualization Integrity

- Label axes, units, and legends; never ship a chart a reader cannot interpret unaided.
- Do not mislead with truncated axes, distorted scales, or cherry-picked ranges.
- Do not let color be the only way meaning is communicated.
- State the data source and date on shared visuals.
- Match the chart type to the question; do not decorate at the cost of clarity.

## Sensitive And Regulated Data

- Keep PII, account data, credentials, and secrets out of source files, notebooks, logs, AI chats, screenshots, and memory.
- Collect and retain the minimum data needed; document what is retained and why.
- Aggregate, mask, or redact sensitive values in shared artifacts and examples.
- Follow the project's data handling, retention, and access rules; when unsure, treat data as sensitive.
- Never paste real regulated data into prompts or third-party tools without approval.

## Verification

Every meaningful data change should have an appropriate verification path.

- Run the smallest relevant check first: row counts, schema assertions, null and range checks, spot-checks against a known source.
- Reconcile transformed data against trusted totals or a source of truth when correctness matters.
- Expand verification when the result feeds reporting, models, downstream systems, or decisions.
- Document checks that could not run and why.
- Do not claim a result is correct unless the check actually ran or was manually confirmed.
