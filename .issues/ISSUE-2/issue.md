# ISSUE-2: Iterate on AI workflow model

<!-- Metadata -->
| Field        | Value        |
|--------------|--------------|
| Status       | done         |
| Owner        | Codex        |
| Complexity   | medium       |
| Created      | 2026-04-24   |
| Source       | user-request |
| External     |              |
| Blocks       |              |
| Blocked-by   |              |
| Priority     | medium       |

## Summary

Explore improvements to the starter AI workflow model so it remains useful for planning, execution, handoff, verification, and multi-agent collaboration without becoming too heavy.

## Prompt

"I'm looking to iterate on this AI workflow model"

## Context

The current repository provides a markdown-first AI workflow starter built around:
- Canonical `AGENTS.md` guidance for project conventions and workflow rules.
- Mandatory `.issues/` audit trail.
- Issue lifecycle statuses from `idea` through `done`.
- Append-only `session-log.md` entries after any work.
- Tool-specific command docs for Codex and Claude.

## Pain Points

- Agents create issues and move toward execution before the request is sufficiently understood.
- The current model encourages task completion but does not strongly require requirement-quality checks.
- Vague prompts can become vague issues, increasing churn during implementation.
- Agents should evaluate the prompt first, identify missing information, and ask clarifying questions before creating implementation-ready issues.
- Multiple agent configuration files are likely to drift because overlapping workflow guidance is duplicated across tool-specific files.
- The starter should consolidate shared agent guidance and avoid checking in unused tool-specific files.
- `AGENTS.md` should become the canonical shared instruction source.
- `AI-README.md` and `AI-WORKFLOW.md` do not need to persist as placeholders because their contents moved to `AGENTS.md`.
- GitLab Duo now reads project-level `AGENTS.md`, so `.gitlab/duo/AGENTS.md` should be removed.
- Cursor, Windsurf, and GitHub Copilot instruction files should not be checked in by default; README should explain how active projects can add thin pointers when needed.
- General notes about optional or unused agents should live in `README.md`, not `AGENTS.md`, to avoid unnecessary context for agents doing normal work.
- Detailed optional command reference belongs in `README.md`; `AGENTS.md` only needs the operational rule to use commands when available.
- Multiple per-session files add issue-folder noise and can become burdensome on long-running issues; session progress should use a single append-only `session-log.md`.
- `AGENTS.md` project overview should read as instructions for copied projects, not as a description of the starter kit repository.
- The overview should emphasize auditability and user expectations for agent behavior.
- When implementation is complete and an issue moves to `review`, agents should create `qa-instructions.md` with step-by-step human validation guidance.
- Starter repository structure belongs in `README.md`, not `AGENTS.md`, because copied projects need their own project details.
- `AGENTS.md` should include a fill-in project details section and should support merging into an existing target-project `AGENTS.md`.
- The micro-change exception is too strict when based on file or line counts; related follow-up asks should remain under the active issue when aligned with current goals.
- `AGENTS.md` has an "Updating This Starter" section that is useful here but should be removed after copying the file into another project.
- Workflow guidance can be strengthened by borrowing patterns from agent skills: focused clarification, repo exploration before asking, durable behavior-focused issues, vertical slices, explicit non-goals, and public-behavior validation.
- `AGENTS.md` should reduce ambiguity around actionable work, simple versus complex requests, session-log timing, review-to-done verification, and starter-only sections.

## Acceptance Criteria

- [x] Identify the main pain points or goals for the next iteration.
- [x] Define a pre-issue or pre-implementation clarification step for vague requests.
- [x] Define a consolidation strategy for shared agent instructions across tools.
- [x] Consolidate `AI-WORKFLOW.md` and `AI-README.md` contents into `AGENTS.md`.
- [x] Remove obsolete `AI-WORKFLOW.md` and `AI-README.md`.
- [x] Remove deprecated `.gitlab/duo/AGENTS.md`.
- [x] Remove unused Cursor, Windsurf, and GitHub Copilot instruction files.
- [x] Document how other agent files can point to `AGENTS.md` without being permanently checked in.
- [x] Move general optional-agent notes out of `AGENTS.md` and into `README.md`.
- [x] Move detailed optional command reference from `AGENTS.md` to `README.md`.
- [x] Replace per-session file guidance with append-only `session-log.md` guidance.
- [x] Update `AGENTS.md` project overview to emphasize audit workflow expectations for copied projects.
- [x] Require `qa-instructions.md` when moving an issue to `review`.
- [x] Move starter repository structure from `AGENTS.md` to `README.md`.
- [x] Add target-project `Project Details` placeholders to `AGENTS.md`.
- [x] Replace strict micro-change exception with related-work guidance for active issues.
- [x] Mark the `AGENTS.md` starter-maintenance section as removable after copying.
- [x] Review local skills for stronger supplemental workflow language and update `AGENTS.md`.
- [x] Tighten ambiguous `AGENTS.md` guidance identified during review.
- [x] Decide which workflow changes should be implemented in this starter.
- [x] Update workflow docs, command docs, and templates consistently if changes are requested.
- [x] Record session log entries for each work session.

## References

- Related files: `AGENTS.md`, `.issues/README.md`, `.codex/commands/`, `.claude/commands/`
- Related issues: `ISSUE-1`
