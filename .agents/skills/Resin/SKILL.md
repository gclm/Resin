```markdown
# Resin Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches the core development patterns and workflows used in the Resin repository, a Go-based project with a web UI. It covers coding conventions, file organization, and step-by-step guides for common feature, UI, and documentation updates. By following these patterns, contributors can ensure consistency, maintainability, and smooth collaboration across backend and frontend code.

## Coding Conventions

**File Naming**
- Use `camelCase` for file names.
  - Example: `requestLogRepo.go`, `platformMonitorPanel.tsx`

**Import Style**
- Use relative imports.
  - Go example:
    ```go
    import "../utils"
    ```
  - TypeScript example:
    ```typescript
    import { fetchData } from './api'
    ```

**Export Style**
- Use named exports.
  - Go example:
    ```go
    func NewRequestLogRepo() *RequestLogRepo { ... }
    ```
  - TypeScript example:
    ```typescript
    export function fetchPlatformData() { ... }
    ```

**Commit Patterns**
- Use prefixes such as `feat` for features and `docs` for documentation.
- Keep commit messages concise (average ~43 characters).
  - Example: `feat: add responseTime field to request logs`

## Workflows

### Feature Development with Schema and UI Update
**Trigger:** When adding a new field or metric to a core entity, exposing it through the API and UI.  
**Command:** `/new-feature-schema-ui`

1. **Update backend schema and repository logic**
   - Edit `internal/requestlog/schema.go` to add the new field.
   - Update `internal/requestlog/repo.go` for repository logic.
   - Apply database migrations if necessary.
   - Example:
     ```go
     type RequestLog struct {
         // ...
         ResponseTime int `json:"responseTime"`
     }
     ```
2. **Update backend logic and API handlers**
   - Modify `internal/api/handler_requestlog.go` to handle the new field.
3. **Update or add backend and API contract tests**
   - Edit or add tests in `internal/api/contract_test.go` and `internal/requestlog/repo_service_test.go`.
4. **Expose the new field in API responses**
   - Ensure the new field is included in API structs and responses.
5. **Update UI components and types**
   - Edit `webui/src/features/requestLogs/RequestLogsPage.tsx` to display the new field.
   - Update types in `webui/src/features/requestLogs/types.ts`.
   - Example:
     ```typescript
     export interface RequestLog {
       // ...
       responseTime: number;
     }
     ```
6. **Update UI translations if necessary**
   - Add new labels or strings in `webui/src/i18n/translations.ts`.

### Feature Development UI + API
**Trigger:** When adding a new UI feature that interacts with the backend.  
**Command:** `/new-ui-feature`

1. **Create or update UI components**
   - Edit or add files like `webui/src/features/platforms/PlatformDetailPage.tsx` or `PlatformMonitorPanel.tsx`.
2. **Update or add API client logic and types**
   - Modify `webui/src/features/platforms/api.ts` and `types.ts` for new endpoints or data structures.
   - Example:
     ```typescript
     export async function fetchPlatformStatus(id: string) { ... }
     ```
3. **Update translations and styles as needed**
   - Add new strings to `webui/src/i18n/translations.ts`.
   - Update styles in `webui/src/styles/theme.css`.

### Documentation Update After Feature
**Trigger:** When a new feature or field is added and needs documentation.  
**Command:** `/update-docs`

1. **Update documentation files**
   - Edit `DESIGN.md` or relevant docs to describe the new feature or field.
   - Example:
     ```markdown
     ## RequestLog.responseTime
     Added in v1.2. Tracks the response time for each log entry.
     ```

## Testing Patterns

- Test files follow the pattern `*.test.*` (e.g., `repo_service_test.go`).
- Testing framework is unspecified; use Go's built-in testing for backend.
  - Example:
    ```go
    func TestNewRequestLogRepo(t *testing.T) {
        // test logic
    }
    ```
- For frontend, use `.test.tsx` or similar patterns for component tests.

## Commands

| Command                | Purpose                                                 |
|------------------------|---------------------------------------------------------|
| /new-feature-schema-ui | Start a backend+UI feature involving schema changes     |
| /new-ui-feature        | Start a new UI feature backed by API logic              |
| /update-docs           | Update documentation after adding new features/fields   |
```