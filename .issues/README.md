# Issue Tracking

This folder contains the repository issue audit trail.

Canonical lifecycle rules, statuses, and session-log requirements live in `../AGENTS.md`. Keep this file focused on `.issues/` folder conventions so workflow rules do not drift.

## Structure

Each `ISSUE-N/` folder contains:
- `issue.md` - Requirements and metadata.
- `plan.md` - Implementation approach, created once work is clear enough to plan.
- `session-log.md` - Append-only session progress records.
- `qa-instructions.md` - Step-by-step human validation guide, created when work moves to review.
- `summary.md` - Final completion record, created after verification.

## Metadata Fields

| Field | Description |
|-------|-------------|
| Status | Current status; see `../AGENTS.md` |
| Owner | Agent, TBD, or person name |
| Complexity | low, medium, or high |
| Created | Date created, `YYYY-MM-DD` |
| Source | Origin category, such as user-request or bug-report |
| External | External ticket reference, optional |
| Blocks | Issues this blocks, optional |
| Blocked-by | Issues blocking this, optional |
| Priority | high, medium, or low |

## Complexity

Use `Complexity` to indicate reasoning level:

| Complexity | Use for |
|------------|---------|
| low | Small, well-defined docs or code changes |
| medium | Standard implementation or workflow changes |
| high | Architecture, complex reasoning, or ambiguous requirements |

## Index Upkeep

If you are not using an index command, update `.issues/index.md` when creating, completing, or changing the status of issues.

## Session Log Template

Append each work session to `ISSUE-N/session-log.md` using this structure:

```markdown
# Session N

**Date:** YYYY-MM-DD

**Prompt/Ask:** Briefly state the user request that triggered this work.

## Completed
- What was accomplished
- Commits made, if any

## Current Status
- Where the issue stands
- Blockers or concerns

## Plan Coverage
- Plan items addressed in this session, if applicable

## Files Changed
- `path/to/file` - description

## Verification
- Commands run, behaviors checked, and expected outcomes
- Verification still needed, if any

## Next Steps
- What remains, if anything
```
