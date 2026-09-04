---
name: appsmith-build-internal-tool
description: Build a working Appsmith internal tool from a brief — resolve the workspace, create the application, wire a datasource-backed query, lay out the page, and hand the user a link.
api: Appsmith MCP server
surface: mcp
endpoint: https://{your-appsmith-instance}/mcp
operations:
  - get_capabilities
  - list_workspaces
  - resolve_workspace
  - list_presets
  - get_preset
  - validate_app_spec
  - build_application
  - list_datasources
  - get_datasource_structure
  - create_query
  - edit_page
  - patch_widgets
  - wire_event
  - read_semantic_page
generated: '2026-09-04'
method: generated
source: https://github.com/appsmithorg/appsmith/blob/release/app/client/packages/mcp/README.md
---

# Build an Appsmith internal tool

Every tool name below was read from `server.tool()` registrations in
`app/client/packages/mcp/src/app.ts`. Nothing here is invented.

## Before you start

1. The MCP server is **off by default**. If `/mcp` returns `404 mcp_disabled`, stop and tell the user an
   administrator must turn on `APPSMITH_MCP_ENABLED` in Admin Settings → MCP Server (BETA).
2. Datasource and query tools are a **separate** switch (`APPSMITH_MCP_DATA_ENABLED`). If
   `list_datasources` is not registered, that layer is off — build the UI only and say so.
3. Call `get_capabilities` first. It tells you which layers are actually live on this instance instead of
   letting you discover it through failures.
4. Authenticate with the user's own `mcp_` bearer token from Profile → MCP tokens. Every call you make is
   bounded by **their** ACL, so a permission error is a real permission answer, not a bug to route around.

## Steps

1. **Pick the workspace.** `list_workspaces`, or `resolve_workspace` when the user named one. Never guess.
2. **Look for a starting shape.** `list_presets` then `get_preset` — a preset is faster and more idiomatic
   than composing a page from scratch.
3. **Draft and validate the spec.** Compose the application spec, then run `validate_app_spec` *before*
   building. This is the dry run; use it rather than building and repairing.
4. **Build.** `build_application`. It **auto-publishes the new app** and returns `editorUrl` and
   `viewerUrl`. Two things to tell the user: publishing does not make the app public (`isPublic` is a
   separate ACL switch), but it *does* make a half-built app visible in view mode to workspace members who
   already have access. Finish wiring before you share the viewer link.
   If the result carries `warnings: ["created but not deployed: …"]`, the app exists but the deploy failed —
   report that, do not retry blindly.
5. **Wire data.** `list_datasources` → `get_datasource_structure` → `create_query` (or the typed variants:
   `create_rest_api`, `create_mongo_query`, `create_redis_query`, `create_s3_query`, `create_graphql_query`,
   `create_sheets_query`, `create_ai_query`). You never write raw SQL or `{{ }}` bindings — the server
   compiles them from your tool arguments. That is the closed-vocabulary invariant; do not try to escape it.
6. **Lay out the page.** `edit_page` and `patch_widgets`, then `wire_event` to bind a widget event to a query.
7. **Verify.** `read_semantic_page` (or `inspect_page`) to confirm what actually exists, then re-publish
   through `prepare_publish` → `confirm_publish` before handing over the link.

## Rules

- **Git-connected apps need a `branch`.** If the app is git-connected, every mutating call requires a
  `branch` parameter equal to the app's current branch. Read it with `read_git_status`.
  `git_branch_required` / `git_branch_changed` carry the current branch, so recovery is one retry.
  `git_state_unknown` means the gate failed closed — do not proceed.
- **Never retry a write blindly.** Appsmith has no idempotency mechanism. A retried create makes a second
  object. On a timeout, read the state back before acting.
- **Rate limits have no headers.** A 429 with `AE-TMR-4029` is the only signal you get; there is no
  `Retry-After`. Back off on your own clock. `create_query` test/execute traffic is capped at 3 per 5s.
