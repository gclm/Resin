---
name: feature-development-with-schema-and-ui-update
description: Workflow command scaffold for feature-development-with-schema-and-ui-update in Resin.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /feature-development-with-schema-and-ui-update

Use this workflow when working on **feature-development-with-schema-and-ui-update** in `Resin`.

## Goal

Implements a new backend feature that requires schema changes, backend logic, API exposure, and corresponding UI updates.

## Common Files

- `internal/requestlog/schema.go`
- `internal/requestlog/repo.go`
- `internal/api/handler_requestlog.go`
- `internal/api/contract_test.go`
- `internal/requestlog/repo_service_test.go`
- `webui/src/features/requestLogs/RequestLogsPage.tsx`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Update backend schema and repository logic (e.g., add column to schema, migrate databases).
- Update backend logic and API handlers to support the new field.
- Update or add backend and API contract tests.
- Expose the new field in API responses.
- Update UI components and types to display the new field.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.