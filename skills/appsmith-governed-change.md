---
name: appsmith-governed-change
description: Make a reviewable, reversible change to an existing Appsmith application — read state first, edit on a reserved mcp/ branch, get explicit human approval, and know exactly what can and cannot be taken back.
api: Appsmith MCP server
surface: mcp
endpoint: https://{your-appsmith-instance}/mcp
operations:
  - read_git_status
  - get_application_context
  - read_pages
  - inspect_page
  - read_publish_status
  - create_branch
  - patch_widgets
  - update_action
  - update_js_object
  - prepare_commit
  - confirm_commit
  - prepare_publish
  - confirm_publish
  - prepare_rollback
  - confirm_rollback
  - list_changes
  - get_change_diff
generated: '2026-09-04'
method: generated
source: https://github.com/appsmithorg/appsmith/blob/release/app/client/packages/mcp/README.md
---

# Change an existing Appsmith application safely

This skill exists because Appsmith's write surface has **no idempotency and no stated undo window**. The
safety comes from the governance handshake, not from being able to fix it afterwards.

## Read before you write

1. `get_application_context` — what this app is.
2. `read_git_status` — is it git-connected, which branch, is it dirty, which branches are protected.
   Pass `compareRemote: true` only when you actually need ahead/behind counts; it costs a remote fetch.
3. `read_pages` / `inspect_page` — the current shape.
4. `read_publish_status` — is there a deployed copy that your edit would diverge from.

## Edit on an agent branch

For a git-connected app, do not edit the user's branch.

1. `create_branch` under the reserved `mcp/` namespace (max 5 per application). **This pushes the new ref to
   the customer's git remote under the instance deploy key** — remote CI and webhooks watching branch pushes
   will fire. Say so before you do it.
2. Appsmith is branch-per-application and has no checkout: `create_branch` returns a **new
   `applicationId`**. Every subsequent edit must target that id, not the original.
3. Make edits (`patch_widgets`, `update_action`, `update_js_object`, …), passing `branch` on every call.

## Get approval, then commit

- `prepare_commit` returns a one-time confirmation with a **5-minute TTL**, bound to the app, branch,
  message and current content revision. If anything drifts between prepare and confirm, it fails — re-read
  and re-prepare rather than forcing it.
- `confirm_commit` prompts the human directly on clients that support MCP elicitation. On clients that do
  not, **you must relay the prepare text and get an explicit yes yourself** — that is the documented
  fallback posture, not an optional courtesy.
- **A commit implies a push.** Appsmith's commit API always pushes to the customer's remote; there is no
  commit-without-push. That is why commits are refused outside `mcp/` branches
  (`git_commit_branch_forbidden`).
- Messages are one printable line, ≤200 characters, must not start with `[`. The server prepends a
  non-strippable `[mcp] ` marker, so your commits are always identifiable.
- Non-accept outcomes come back as `declined`, `cancelled`, `timeout`, `accepted_without_confirm` or
  `client_error`. Only `client_error` means the human never saw the prompt — in that case fall back to
  relaying. The rest mean **no**. Do not re-prepare to get a second prompt; the per-session budget is 20
  approvals and exhausting it returns `elicitation_budget_exhausted`.

## What is actually reversible

| Action | Reversal | Window |
|---|---|---|
| Publish | `prepare_rollback` → `confirm_rollback` | **none published** |
| Delete page / action / JS object | none — prevention only | n/a |
| Commit (pushed to remote) | none from MCP; human reverts on the remote | n/a |
| Instance state | `appsmithctl restore` / `import_db` | operator's own backup schedule |

Never tell a user a change can be undone within a specific time. Appsmith publishes no such window.
Publishing from MCP stays disabled for git apps by design: the deliverable is the `mcp/` branch and its
review URL — the human merges it.

## Audit

When Mongo + Redis are configured, mutations produce change records: `list_changes`, `get_change`,
`get_change_diff`. Without that backend the server starts with read + spec-authoring tools only, and
governed/destructive tools are simply not there.
