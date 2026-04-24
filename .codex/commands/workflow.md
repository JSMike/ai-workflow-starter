---
description: Issue tracking workflow guidance and verification
---

# Workflow Assistant

Helps ensure the issue tracking workflow is followed correctly. Canonical rules live in `AGENTS.md`; every actionable task in this repository must be tracked in `.issues/`.

**Usage:** `/workflow [action]`

## Actions

### (no action) - Overview

Display the complete workflow with current context. Show:
1. Any in-progress issues from `.issues/index.md`
2. The workflow steps
3. Reminders about mandatory session-log entries

---

### start

Begin work properly. Follow this checklist:

1. **Understand the request** - What is the user asking for, and is it clear enough to plan?

2. **Clarify vague requests:**
   - Restate the likely goal
   - Identify missing requirements, constraints, acceptance criteria, and non-goals
   - Ask targeted clarifying questions before creating an implementation-ready issue

3. **Check for existing issues:**
   ```
   /issue match <description of the work>
   ```
   - If match found → Use `/issue work <id>` to continue
   - If no match → Use `/issue create <title>` to start new

4. **If continuing existing issue:**
   - Read the issue.md for requirements
   - Read the plan.md for approach
   - Read the latest `session-log.md` entry for where we left off
   - Update status to `in-progress` if not already

5. **If creating new issue:**
   - Use `idea` for exploration or vague requests
   - Use `ready` only when requirements and acceptance criteria are clear enough to implement
   - Plan file is at `.issues/ISSUE-N/plan.md`

6. **Confirm tracking:**
   - Display: "Working on ISSUE-N: <title>"
   - Display: "Remember to run `/issue session ISSUE-N` after completing work"

---

### check

Verify the workflow is being followed. Check:

1. **Is there an active issue?**
   - Scan `.issues/*/issue.md` for `in-progress` status
   - If none, warn: "No issue in progress - run `/workflow start`"

2. **Is the current work related to an issue?**
   - Compare recent file changes to issue acceptance criteria
   - Warn if work appears untracked

3. **Are session-log entries up to date?**
   - Check if commits or file changes exist since the last `session-log.md` entry
   - Warn: "Work found since last session-log entry - run `/issue session <id>`"

4. **Checklist output:**
   ```
   Workflow Check:
   [x] Issue exists: ISSUE-18
   [x] Status: in-progress
   [x] Plan exists: yes
   [ ] Session log current: NO - work exists since last session-log entry

   Action needed: Run `/issue session ISSUE-18`
   ```

---

### end

Prepare to end the current session. Mandatory steps:

1. **Identify active issue(s):**
   - List all issues with `in-progress` status

2. **For each active issue:**
   - Prompt to append a session-log entry:
     ```
     /issue session <id>
     ```
   - Session-log entry must include:
     - What was completed
     - Current status
     - Files changed
     - Next steps

3. **Verify all work is committed:**
   - Check `git status` for uncommitted changes
   - Warn if changes exist that should be committed

4. **Confirm completion:**
   - Display: "Session-log entries created for: ISSUE-N, ISSUE-M"
   - Display: "Safe to end session"

---

### help

Show quick reference for issue commands:

```
Issue Workflow Commands:

Starting work:
  /issue match <desc>     Find existing issues
  /issue create <title>   Create new issue
  /issue work <id>        Continue existing issue

During work:
  /issue show <id>        View issue details
  /issue status <id> <s>  Update status
  /issue plan <id>        Create/update plan

Recording progress:
  /issue session <id>     Append session-log entry before handoff (MANDATORY)
  /issue status <id> review
                          Create QA instructions and submit for review
  /issue done <id>        Mark verified work complete with final summary

Maintenance:
  /issue list [status]    List issues
  /issue index            Regenerate index
  /issue delete <id>      Remove after PR merge
```

---

## Workflow Diagram

```
User Request
     │
     ▼
┌─────────────────┐
│ clarify prompt  │ ─── Vague? ─────────→ ask questions
└────────┬────────┘
         │ Clear enough
         ▼
┌─────────────────┐
│ /issue match    │ ─── Match found? ──→ /issue work <id>
└────────┬────────┘                              │
         │ No match                              │
         ▼                                       │
┌─────────────────┐                              │
│ /issue create   │                              │
│ (enters plan    │                              │
│  mode)          │                              │
└────────┬────────┘                              │
         │                                       │
         ▼                                       ▼
┌─────────────────────────────────────────────────┐
│                  Do Work                        │
│  - Implement changes                            │
│  - Update plan checkboxes                       │
│  - Commit code                                  │
└────────────────────┬────────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────────┐
│  /issue session <id>  (MANDATORY)               │
│  - Record what was done                         │
│  - Note current status                          │
│  - List files changed                           │
│  - Define next steps                            │
│  - Append to session-log.md                     │
└────────────────────┬────────────────────────────┘
                     │
         ┌───────────┴───────────┐
         │                       │
         ▼                       ▼
   More work?              Ready for review?
         │                       │
         │                       ▼
         │              ┌─────────────────┐
         │              │ qa + review     │
         │              └────────┬────────┘
         │                       │
         └───────────────────────┘
```

---

## Common Scenarios

### "User asks to fix a bug"
1. `/issue match bug description` - check if already tracked
2. If found: `/issue work ISSUE-N`
3. If not: `/issue create "Fix: bug description"`
4. Implement fix
5. `/issue session ISSUE-N` - append the fix to `session-log.md`
6. If implementation is complete: create `qa-instructions.md` and run `/issue status ISSUE-N review`
7. After verification: `/issue done ISSUE-N`

### "User asks to add a feature"
1. `/issue match feature description`
2. If not found: `/issue create "Add: feature name"`
3. Plan mode activates - design the approach
4. Implement in iterations
5. `/issue session ISSUE-N` after each work block
6. Create `qa-instructions.md` and run `/issue status ISSUE-N review` when implementation is complete
7. `/issue done ISSUE-N` after verification

### "Resuming work from previous session"
1. Check `.issues/index.md` for in-progress issues
2. `/issue work ISSUE-N` to see context
3. Read latest `session-log.md` entry for where we left off
4. Continue implementation
5. `/issue session ISSUE-N` before ending

### "Quick idea to capture"
1. `/issue create "Idea: brief description"`
2. Fill in minimal details in issue.md
3. Set status to `idea` or `backlog`
4. `/issue session ISSUE-N` to record creation
5. Return later to flesh out

---

## Red Flags

Watch for these workflow violations:

- **Creating implementation issues from vague prompts** - Clarify first
- **Making changes without an active issue** - Always have an ISSUE-N once work is actionable
- **Ending session without a session-log entry** - Never skip `/issue session` before handoff
- **Creating duplicate issues** - Always `/issue match` first
- **Work not reflected in issue folder** - Plans and session logs must be updated
- **Commits without session record** - Each work session with commits needs a session-log entry
- **Review without QA instructions** - `qa-instructions.md` is required before status `review`
