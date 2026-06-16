# Library And Integration Docs

Purpose: project-specific library, service, API, tool, protocol, and shared package notes.

Capture only project-specific usage rules, setup notes, known pitfalls, and decisions.

## Before Using A Dependency

1. Check whether the project already has a wrapper, adapter, helper, or documented pattern.
2. Check whether the dependency is approved for this project.
3. Confirm where the dependency is allowed to run.
4. Confirm how configuration and secrets are provided.
5. Prefer official documentation for current API details when behavior may have changed.

## Approved Dependencies And Services

| Name | Purpose | Owner or boundary | Notes |
| ---- | ------- | ----------------- | ----- |
| [DEPENDENCY_1] | [PURPOSE] | [BOUNDARY] | [NOTES] |
| [DEPENDENCY_2] | [PURPOSE] | [BOUNDARY] | [NOTES] |
| [DEPENDENCY_3] | [PURPOSE] | [BOUNDARY] | [NOTES] |

Add a dependency here when it becomes part of the project architecture.

## Integration Template

```markdown
## [LIBRARY_OR_SERVICE_NAME]

**Used for:** [PURPOSE]
**Owned by:** [MODULE_OR_BOUNDARY]
**Allowed runtime:** [WHERE_IT_CAN_RUN]
**Configuration:** [ENV_OR_CONFIG_KEYS_WITHOUT_VALUES]
**Secrets:** [SECRET_NAMES_WITHOUT_VALUES]

### Project Pattern

[PROJECT_USAGE_PATTERN]

### Data Shape

[IMPORTANT_DATA_SHAPES]

### Failure Behavior

[FAILURE_AND_RECOVERY_BEHAVIOR]

### Do Not

- [RULE_1]
- [RULE_2]
- [RULE_3]

### Known Pitfalls

- [PITFALL_1]
- [PITFALL_2]
```

## Configuration Inventory

Document required configuration keys without real values.

| Key | Public or secret | Used by | Required |
| --- | ---------------- | ------- | -------- |
| [CONFIG_KEY_1] | [PUBLIC_OR_SECRET] | [OWNER] | [YES_OR_NO] |
| [CONFIG_KEY_2] | [PUBLIC_OR_SECRET] | [OWNER] | [YES_OR_NO] |

## Notes

- Never store real credentials in this file.
- Remove stale integration notes when a dependency is removed.
- Keep examples short and clearly marked as examples.
