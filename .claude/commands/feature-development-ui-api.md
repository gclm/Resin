---
name: feature-development-ui-api
description: Workflow command scaffold for feature-development-ui-api in Resin.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /feature-development-ui-api

Use this workflow when working on **feature-development-ui-api** in `Resin`.

## Goal

Implements a new UI feature backed by API logic and type definitions.

## Common Files

- `webui/src/features/platforms/PlatformDetailPage.tsx`
- `webui/src/features/platforms/PlatformMonitorPanel.tsx`
- `webui/src/features/platforms/api.ts`
- `webui/src/features/platforms/types.ts`
- `webui/src/i18n/translations.ts`
- `webui/src/styles/theme.css`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Create or update UI components for the new feature.
- Update or add API client logic and types for the new feature.
- Update translations and styles as needed.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.