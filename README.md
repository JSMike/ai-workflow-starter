# AI Workflow Starter

This repo is a starter kit for using an AI issue-tracking workflow in new projects.

## Contents

- `AGENTS.md`: canonical project guidance and AI workflow rules
- `.issues/`: issue tracking folder with index and templates
- `.codex/commands/` and `.claude/commands/`: optional command docs
- `CLAUDE.md`: Claude-specific pointer to `AGENTS.md`

GitLab Duo now uses the project-level `AGENTS.md`; this starter does not maintain `.gitlab/duo/AGENTS.md`.

## Starter Repository Structure

- `AGENTS.md` - Template for canonical project guidance and workflow rules.
- `README.md` - Human-facing setup and customization guidance for this starter.
- `CLAUDE.md` - Claude-specific pointer to `AGENTS.md`.
- `.issues/` - Starter issue audit trail and conventions.
- `.codex/commands/` - Optional Codex command docs.
- `.claude/commands/` - Optional Claude command docs.

## Getting Started

1. Read `AGENTS.md`.
2. Ask your agent to clarify vague requirements before implementation.
3. Ask your agent to create or resume an issue when work becomes actionable.
4. Update `AGENTS.md` as necessary to improve DevEx for your app.
5. If you reach your usage limit with one plan, continue from the current issue's context.
6. Check in `.issues/` records so coworkers or other agents can continue the work.

## Customize

- Fill in the `Project Details` section in `AGENTS.md` for the target project.
- If the target project already has an `AGENTS.md`, merge this workflow guidance into it instead of replacing project-specific instructions.
- If your tool provides an `/init` flow, use it to preserve discovered project conventions, then add this workflow model.
- Decide on your issue ID prefix; the starter uses `ISSUE-N`.
- Only add tool-specific instruction files for agents your project actually uses.

## Other Agents

`AGENTS.md` should remain the canonical source of truth. Avoid checking in extra agent files unless the project actively uses that tool; unused files add noise and create drift risk.

Keep general notes about optional agent support in this README instead of `AGENTS.md`; every extra note in `AGENTS.md` becomes context that agents must read during normal work.

If another agent requires a tool-specific file, keep it as a thin pointer to `AGENTS.md`. For example:

```markdown
# Tool Instructions

Read `AGENTS.md` first. It is the canonical source for project guidance and the AI issue workflow.

Tool-specific notes:
- Follow `AGENTS.md` manually if slash commands are unavailable.
- Do not duplicate shared workflow rules here.
```

If the tool supports local or user-level configuration, prefer that over committing a project file.

When maintaining checked-in command docs, keep `.codex/commands/*` and `.claude/commands/*` in sync.

## Optional Commands

Some tools can expose slash commands for issue workflow operations. If unavailable, agents can perform the same updates manually in `.issues/`.

| Command | Purpose |
|---------|---------|
| `/issue init` | Initialize `.issues/` in a new project |
| `/issue create <title>` | Create a new issue |
| `/issue match <desc>` | Find existing issues |
| `/issue work <id>` | Start or resume work |
| `/issue session <id>` | Record session progress |
| `/issue done <id>` | Mark verified work complete |
| `/issue list [status]` | List issues |
| `/issue show <id>` | View issue details |
| `/issue status <id> <status>` | Update status; create `qa-instructions.md` when moving to `review` |
| `/issue plan <id>` | Create or update plan |
| `/issue index` | Regenerate index |
| `/issue delete <id>` | Remove after merge |
