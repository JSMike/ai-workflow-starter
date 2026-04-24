---
description: Manage issues in the .issues/ folder
---

# Issue Management

Manage the issue tracking system in `.issues/`. This command is portable and can bootstrap issue tracking in any repository.

**Usage:** `/issue <action> [arguments]`

## Actions

### init

Initialize the `.issues/` folder structure in a new project.

1. Create `.issues/` directory
2. Create `.issues/README.md` with conventions documentation (template below)
3. Create empty `.issues/index.md` with header

**README.md Template:**
```markdown
# Issue Tracking

This folder contains issue tracking for the repository. Each issue has its own folder with documentation.

Canonical workflow rules live in `../AGENTS.md`. Keep this file focused on `.issues/` folder conventions.

## Structure

Each `ISSUE-N/` folder contains:
- `issue.md` - Requirements and metadata (always present)
- `plan.md` - Implementation approach (created when planning)
- `session-log.md` - Append-only session progress records
- `qa-instructions.md` - Step-by-step human validation guide (created when moving to review)
- `summary.md` - Final completion record (created after verification)

## Status Values

| Status | Meaning |
|--------|---------|
| idea | Captured thought, exploration, or vague request; not yet scoped |
| backlog | Scoped but not ready to work |
| ready | Ready to work, dependencies met, acceptance criteria clear |
| in-progress | Currently being worked on |
| review | Implementation complete, awaiting verification |
| done | Verified working and accepted |

## Metadata Fields

| Field | Description |
|-------|-------------|
| Status | Current status (see above) |
| Owner | Agent / TBD / person name |
| Created | Date created (YYYY-MM-DD) |
| Source | Origin category (design-review, bug-report, etc.) |
| External | External ticket reference (optional) |
| Blocks | Issues this blocks (optional) |
| Blocked-by | Issues blocking this (optional) |
| Priority | high / medium / low |

## Commands

Use `/issue <action>` to manage issues:
- `init` - Initialize this folder structure
- `create <title>` - Create new issue
- `match <description>` - Find existing issues matching a description
- `work <id>` - Start working on an issue
- `list [status]` - Show issues
- `show <id>` - Display issue details
- `status <id> <status>` - Update status
- `plan <id>` - Create/update plan
- `session <id>` - Append session progress (run at end of each work session or before handoff)
- `done <id>` - Mark verified work complete with comprehensive summary
- `delete <id>` - Remove issue
- `index` - Regenerate index.md

## Lifecycle

1. Clarify vague requests before creating implementation-ready issues
2. Create issue with `/issue create`
3. Plan implementation, add plan.md
4. Work on issue, update status to `in-progress`
5. **After each work session or before handoff, run `/issue session` to append progress to `session-log.md`** (mandatory)
6. When implementation is complete, create `qa-instructions.md` and set status to `review`
7. After verification, run `/issue done` for final summary
8. After PR merge, run `/issue delete`

**Important:** Session log entries are mandatory for each work session or handoff point, not optional. One entry can cover multiple related edits in the same uninterrupted work session. The audit trail depends on consistent session recording.

## Session Log Template

Append each work session to `ISSUE-N/session-log.md` using this structure:

- `# Session N`
- `**Date:** YYYY-MM-DD`
- `**Prompt/Ask:**` Briefly state the user request that triggered this work.
- `## Completed`
- `## Current Status`
- `## Plan Coverage`
- `## Files Changed`
- `## Verification`
- `## Next Steps`
```

---

### create <title>

Create a new issue folder with issue.md template.

**Clarify vague requests first.** Use `idea` for exploratory or underspecified requests, and only move issues to `ready` or `in-progress` once requirements are clear enough to plan responsibly.

1. Find the next available ISSUE-N number by scanning existing folders
2. Create `.issues/ISSUE-N/` directory
3. Create `.issues/ISSUE-N/issue.md` with template:

```markdown
# ISSUE-N: <title>

<!-- Metadata -->
| Field        | Value                              |
|--------------|-------------------------------------|
| Status       | idea                                |
| Owner        | TBD                                 |
| Created      | <today's date YYYY-MM-DD>           |
| Source       |                                     |
| External     |                                     |
| Blocks       |                                     |
| Blocked-by   |                                     |
| Priority     | medium                              |

## Summary
<describe what needs to be done>

## Prompt
<original request, if available>

## Context
<background information>

## Requirements Readiness
- [ ] Goal is clear
- [ ] Constraints are documented
- [ ] Acceptance criteria are testable
- [ ] Open questions are resolved or captured

## Acceptance Criteria
- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Criterion 3

## References
- Related files:
- Related issues:
```

4. Display the created issue path
5. Create or update `.issues/ISSUE-N/plan.md` once the issue is clear enough to plan
   - All planning work is captured in the issue folder
   - This becomes the complete audit trail

---

### match <description>

Search for existing issues that match a description. **Use this before starting new work** to avoid creating duplicate issues.

1. Read all `.issues/ISSUE-*/issue.md` files
2. Compare Summary and Title against the provided description
3. Return matching issues with relevance indication
4. If match found, suggest `/issue work <id>` to continue that issue

Example output:
```
Found 2 potential matches:

ISSUE-8: Button hover states fail contrast (high match)
  Status: ready | Priority: high
  → Use `/issue work ISSUE-8` to continue this issue

ISSUE-3: Stat delta colors need AA audit (partial match)
  Status: ready | Priority: medium

No match? Use `/issue create "<title>"` to create new issue.
```

---

### work <id>

Start working on an existing issue.

1. Read `.issues/<id>/issue.md` and display acceptance criteria
2. If status is `ready`, update to `in-progress`
3. If status is `in-progress`, show current progress from plan.md
4. Display reminder: "When implementation is complete, set status to `review`; run `/issue done <id>` only after verification"
5. If plan.md doesn't exist, offer to enter plan mode

This action helps agents pick up existing work rather than starting fresh.

---

### list [status]

Show issues, optionally filtered by status.

1. Scan all `.issues/ISSUE-*/issue.md` files
2. Parse metadata table from each
3. If status filter provided, only show matching issues
4. Display as table grouped by status:

```
## In Progress
| ID | Title | Owner | Priority |
|----|-------|-------|----------|
| ISSUE-1 | Issue title | Agent | high |

## Ready
...
```

---

### show <id>

Display full details of an issue.

1. Read `.issues/<id>/issue.md`
2. If exists, also summarize `plan.md`, `session-log.md`, and `summary.md`
3. Display the content

---

### status <id> <new-status>

Update the status field of an issue.

1. Read `.issues/<id>/issue.md`
2. If `<new-status>` is `review`, create or update `.issues/<id>/qa-instructions.md` before changing the status
3. Update the Status field in the metadata table
4. Valid statuses: idea, backlog, ready, in-progress, review, done
5. Save the file

When moving to `review`, `qa-instructions.md` must include:

```markdown
# QA Instructions: <id> - <title from issue.md>

## What Changed
- <Brief summary of completed work>

## Preconditions
- <Environment, data, accounts, feature flags, or setup needed>

## Validation Steps
1. <Step-by-step human validation action>
2. <Expected result>

## Acceptance Criteria
- [ ] <Criterion or behavior to confirm>

## Regression Checks
- [ ] <Important adjacent behavior to re-check>

## Notes
- <Known limitations, risks, or follow-up context>
```

---

### plan <id>

Create or update plan.md for an issue.

1. If `.issues/<id>/plan.md` doesn't exist, create with template:

```markdown
# Plan: <id> - <title from issue.md>

<!-- Plan Metadata -->
| Field        | Value                              |
|--------------|-------------------------------------|
| Created      | <today's date>                      |
| Author       | Agent                               |
| Approach     | Proposed                            |

## Approach
<describe implementation strategy>

## Files to Modify
- `path/to/file` - description

## Implementation Steps
1. [ ] Step one
2. [ ] Step two
3. [ ] Step three

## Risks & Considerations
-

## Alternatives Considered
```

2. If issue status is `ready`, update to `in-progress`
3. Display the plan path

---

### done <id>

Mark a verified issue as complete with a **comprehensive summary** that serves as the audit record.

Only run this after user confirmation, human QA, CI accepted by the user, or another explicit review signal outside the implementing agent's own confidence.

**Important:** The summary.md becomes the permanent record of what was actually done. It should be detailed enough for non-technical stakeholders to understand the work completed.

1. Create `.issues/<id>/summary.md` with comprehensive content:

```markdown
# Summary: <id> - <title from issue.md>

## Completed
<today's date> by Agent

## What Was Done
<Detailed description of the implementation - not just "done" but what specifically was built/changed/fixed>

## Files Changed
- `path/to/file.ts` - <specific description of changes>
- `path/to/file.scss` - <specific description of changes>
<List ALL files that were modified with meaningful descriptions>

## Key Decisions Made
- <Any decisions made during implementation>
- <Trade-offs chosen>
- <Why certain approaches were taken>

## Deviations from Plan
- <If anything was done differently than originally planned, explain why>

## Acceptance Criteria Results
- [x] Criterion 1 - <how it was verified>
- [x] Criterion 2 - <how it was verified>
- [x] Criterion 3 - <how it was verified>

## Artifacts
- Branch: <branch name>
- PR: <PR number/link>
- Commits: <commit hashes>

## Notes
<Any additional context for future reference>
```

2. Update issue.md status to `done`
3. Display confirmation with link to summary.md

---

### session <id>

Record progress after completing work on an issue. **This is mandatory after any work** - creating issues, updating plans, implementing changes, or any other modifications. Never skip this step.

1. Find the next session number by scanning existing `# Session N` headings in `.issues/<id>/session-log.md`; if the file does not exist, start at Session 1
2. Append this entry to `.issues/<id>/session-log.md`:

```markdown
# Session N

**Date:** <today's date YYYY-MM-DD>

**Prompt/Ask:** <briefly state the user request that triggered this work>

## Completed
- <What was accomplished in this session>
- <Specific tasks completed>
- <Commits made>

## Current Status
- <Where the issue stands now>
- <What acceptance criteria are complete>
- <Any blockers or concerns>

## Plan Coverage
- <Plan items addressed in this session, if applicable>

## Files Changed
- `path/to/file.ts` - <description of changes>
- `path/to/file.scss` - <description of changes>

## Verification
- <How to verify the changes work>
- <Commands run, behaviors checked, expected outcomes>

## Next Steps
- <What remains to be done>
- <Recommended next actions>
```

3. Display confirmation with `session-log.md` path
4. Remind: "Set status to `review` when implementation is complete; run `/issue done <id>` only after verification"

---

### delete <id>

Remove an issue folder after PR merge.

1. Confirm the issue exists and status is `done`
2. Delete the entire `.issues/<id>/` folder
3. Run `index` action to regenerate index.md
4. Display confirmation

---

### index

Regenerate the index.md file from all issues.

1. Scan all `.issues/ISSUE-*/issue.md` files
2. Parse metadata from each
3. Generate `.issues/index.md`:

```markdown
# Issue Index

Generated: <today's date>

## By Status

### In Progress
| ID | Title | Owner | Blocked By |
|----|-------|-------|------------|
| [ISSUE-1](./ISSUE-1/issue.md) | Title | Owner | - |

### Ready
| ID | Title | Owner | Priority |
|----|-------|-------|----------|

### Backlog
| ID | Title | Owner | Priority |
|----|-------|-------|----------|

### Review
| ID | Title | Owner | PR |
|----|-------|-------|-----|

### Done
| ID | Title | Completed |
|----|-------|-----------|
```

4. Display count of issues by status
