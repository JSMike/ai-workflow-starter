# AI Workflow Starter

This repo is a starter kit for using the AI issue-tracking workflow in new projects.

## Contents

- AI-WORKFLOW.md: the mandatory workflow rules
- AI-README.md: template for project-specific conventions
- Instructions for AI agents to use the AI-README.md and AI-WORKFLOW.md
  - AGENTS.md
  - CLAUDE.md
  - .github/copilot-instructions.md
  - .gitlab/duo/AGENTS.md
- .issues/: issue tracking folder with index and templates
- .codex/commands and .claude/commands: optional command docs

## Getting Started

1. Read AI-WORKFLOW.md and AI-README.md.
2. Ask your agent to create a new issue and provide details
3. Update AI-README.md and AI-WORKFLOW.md as necessary to improve DevEx for your app.
4. If you reach your usage limit with one plan, try swapping to another and continuing with the current issue's context.
5. Check in your .issue and pass context to a co-worker to steer/complete the remaining work.

## Customize

- Replace the placeholder sections in AI-README.md.
- Decide on your issue ID prefix (the starter uses ISSUE-N).

## Future considerations

- Add local sqlite database and mcp to store issues in DB instead of .issues
  - Can potentially do things like add skill/logic to put current issue in .issues only to reduce overall context.
- Add integration to align issue id's with other system, such as Jira or GitHub/GitLab issues, and add sync to push details for audit.
