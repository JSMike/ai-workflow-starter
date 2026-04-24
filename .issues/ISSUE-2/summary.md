# Summary: ISSUE-2 - Iterate on AI workflow model

## Completed

Iterated the AI workflow starter so `AGENTS.md` is the canonical, portable agent guidance source and the surrounding repository docs support that model without unnecessary duplicated agent context.

Major outcomes:
- Consolidated shared workflow guidance into `AGENTS.md`.
- Removed obsolete or unused agent instruction files.
- Moved human-facing starter details, optional-agent notes, and optional command references into `README.md`.
- Replaced per-session summary files with append-only `session-log.md`.
- Added required `qa-instructions.md` review handoff.
- Strengthened intake, issue quality, related-work, review, verification, and copied-project guidance.
- Created backlog issues for future considerations and token-efficiency cleanup.

## Key Decisions

- `AGENTS.md` is the source of truth for agent workflow behavior.
- `AI-README.md` and `AI-WORKFLOW.md` were removed because their contents were consolidated.
- Tool-specific files should be checked in only when actively used; optional agent guidance belongs in `README.md`.
- `CLAUDE.md` remains as a thin pointer to `AGENTS.md`.
- Session progress uses `session-log.md`; `summary.md` is reserved for final verified completion.
- Work moves to `done` only after external verification.

## Verification

- User confirmed `ISSUE-2` is done on 2026-04-24.
- Codex and Claude command docs were repeatedly checked for parity during the iteration.
- `ISSUE-2` session log is sequential through Session 24 before final completion.
- `ISSUE-3`, `ISSUE-4`, `ISSUE-5`, and `ISSUE-6` preserve future/backlog work.

## Follow-Up

- `ISSUE-3`: Explore SQLite and MCP-backed issue storage.
- `ISSUE-4`: Integrate issue IDs with external tracking systems.
- `ISSUE-5`: Sync audit details to external systems.
- `ISSUE-6`: Review `AGENTS.md` token efficiency.
