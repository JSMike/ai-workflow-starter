# ISSUE-6: Review AGENTS.md token efficiency

<!-- Metadata -->
| Field        | Value        |
|--------------|--------------|
| Status       | backlog      |
| Owner        | TBD          |
| Complexity   | low          |
| Created      | 2026-04-24   |
| Source       | user-request |
| External     |              |
| Blocks       |              |
| Blocked-by   |              |
| Priority     | low          |

## Summary

Review `AGENTS.md` for small token-efficiency improvements without reducing workflow clarity or agent steering value.

## Prompt

User asked to keep the Unicode issue-folder tree for now, but capture token-efficiency suggestions as a separate backlog issue.

## Context

The tokenizer warning appears to be caused by the box-drawing characters in the issue-folder tree. Replacing them with ASCII would remove the warning, but would not meaningfully reduce token usage.

The current `AGENTS.md` is intentionally compact enough for normal use and still includes guardrails for intake, issue quality, workflow steps, review handoff, and session logging.

## Acceptance Criteria

- [ ] Review whether the issue-folder tree should stay as-is, become ASCII, or be compressed to a one-line list.
- [ ] Evaluate whether `Command Support` can be merged into workflow steps without losing clarity.
- [ ] Evaluate whether `Red Flags` should remain in `AGENTS.md` or move to `.issues/README.md`.
- [ ] Evaluate whether `Status Values` can be shortened while preserving clear status semantics.
- [ ] Avoid removing guidance that prevents premature implementation, skipped issue tracking, or premature `done` status.
- [ ] If changes are made, update command docs or README only when needed to avoid drift.

## References

- Related files: `AGENTS.md`, `.issues/README.md`
- Related issues: `ISSUE-2`
