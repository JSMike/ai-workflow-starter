# AGENTS.md

Canonical guidance for AI agents working in this repository.

This file is the source of truth for project conventions and the AI issue workflow.

## Project Overview

This project requires an auditable AI workflow. Agents are expected to follow the process below so work is traceable, reviewable, and easy to resume across sessions or tools.

The user expects agents to:
- Clarify vague or underspecified requests before implementation.
- Track actionable work in `.issues/`.
- Keep plans, decisions, progress, and verification notes current.
- Preserve enough context for another agent or human to continue without reconstructing the conversation.
- Avoid untracked work, skipped session logs, and premature `done` status.

## Project Details

Fill this section in for the target project. If the project already has an `AGENTS.md`, merge this workflow guidance into the existing file instead of replacing project-specific instructions.

Agents should keep these details current when they discover or change them:

- Project purpose:
- Primary runtime and package manager:
- Build, test, lint, and dev commands:
- Key source and test directories:
- Environment variables and local setup:
- Deployment, sync, or background job notes:
- Project-specific conventions and constraints:

## Core Workflow Principle

Every task must be tracked in `.issues/` once it becomes actionable work.

Actionable work includes:
- Code, documentation, configuration, design, or workflow changes.
- Creating or updating issue records, plans, QA instructions, or summaries.
- Repository investigation that produces decisions, plans, recommendations, or implementation steps.
- Follow-up requests that change scope, acceptance criteria, verification, or handoff context.

Casual questions or discussion do not require an issue unless they become planned work or need durable follow-up.

The `.issues/` audit trail should preserve the request, clarifications, plan, delivered changes, verification path, and remaining next steps.

## Intake Before Issues

Do not turn vague prompts into implementation issues too quickly.

Before creating or advancing an issue, evaluate whether the request has enough information to plan responsibly:
- Restate the likely goal in concrete terms.
- Identify missing requirements, constraints, acceptance criteria, and non-goals.
- Ask targeted clarifying questions when missing information could materially change the solution.
- State any assumptions if the missing details are low risk and work can proceed safely.

Clarification discipline:
- Ask only the questions needed to remove meaningful ambiguity.
- A simple request is low-risk, single-scope, and has an obvious verification path. Ask at most 2-3 short questions before either proceeding or capturing it as `idea` / `backlog`.
- Complex planning involves multiple systems, unclear acceptance criteria, architecture, data loss/security risk, or broad user-visible impact. Ask one question at a time and provide a recommended answer when useful.
- If a question can be answered by reading the repo, docs, tests, or existing issue records, investigate first instead of asking the user.
- Flag vague or overloaded terms and propose precise wording for the issue.

Decision rules:
- If the user asks a question and no durable follow-up is needed, answer without creating an issue.
- If the user is brainstorming, planning, or exploring, create or update an `idea` issue only when the context should be preserved.
- If the request is worth tracking but not ready to implement, create or update a `backlog` issue.
- If requirements, acceptance criteria, dependencies, and verification are clear, use `ready`.
- If an agent starts implementation or concrete documentation changes, use `in-progress`.

## Issue Quality

Issues should be durable and behavior-focused. A good issue should still make sense after files are renamed or internals are refactored.

When creating or refining an issue:
- Describe the user-visible behavior, system capability, or workflow outcome.
- Include expected behavior and actual behavior for bugs.
- Include reproduction or validation steps when applicable.
- Use project domain language and define ambiguous terms.
- Keep acceptance criteria testable.
- Capture non-goals or out-of-scope items when they prevent churn.
- Avoid coupling issue descriptions to specific file paths, line numbers, or implementation details unless the task is explicitly about those files.

When breaking work down:
- Prefer thin vertical slices that are independently reviewable and verifiable.
- Avoid horizontal slices that only complete one layer without a usable behavior path.
- Mark dependencies honestly so parallel work is possible where safe.

## Workflow Steps

### 1. Before Starting Work

- Check for existing issues in `.issues/`; do not create duplicates.
- If your tool supports issue commands, use `/issue match <description>`.
- Run intake before creating an implementation-ready issue.

### 2. Starting New Work

- Sequence: match existing work, run intake, choose status per Decision rules, create the issue folder with `issue.md`, then create or update `plan.md` once requirements are clear enough.
- If your tool supports issue commands, use `/issue create <title>`, then set status according to readiness.
- Before moving to `ready` or `in-progress`, confirm goal, scope, acceptance criteria, non-goals, and verification are clear enough to avoid preventable churn.

### 3. Resuming Existing Work

- Read `issue.md` for requirements.
- Read `plan.md` for approach.
- Read the latest entry in `session-log.md` for current context.
- If status is `ready` and you begin work, update it to `in-progress`.

### 4. After Any Work

Never skip session records.

Record progress after:
- Creating a new issue.
- Updating a plan.
- Implementing changes.
- Modifying issue files.
- Changing workflow documentation.

Entry timing:
- One entry can cover multiple related edits in the same uninterrupted session.
- Append a new entry before handoff or final response.
- Add to the current entry only while the session is still in progress and the entry has not been used for handoff.

If your tool supports issue commands, use `/issue session <id>` to append the next entry to `session-log.md`.

#### Related Work During Active Issues

Do not over-eagerly create new issues for follow-up asks that are aligned with the current work.

Continue under the active issue when the new ask is:
- A clarification or refinement of the current requirement.
- Tangentially or similarly related to the active issue goal.
- Needed to complete, verify, document, or safely hand off the current work.
- Small enough that splitting it out would create more tracking overhead than clarity.

When continuing under the active issue:
- Update `issue.md` acceptance criteria or context if the requirement changed.
- Update `plan.md` if the approach or scope changed.
- Record the work in `session-log.md` per the entry timing rules above.

Create a new issue only when the ask is materially separate, would be better planned/reviewed independently, changes ownership or priority, or would make the current issue too broad.

### 5. Submitting For Review

- Do not mark issues `done` yourself after implementation.
- Set status to `review` when implementation is complete.
- Create `qa-instructions.md` with step-by-step human validation instructions before or when moving to `review`.
- Append a session log entry documenting what changed and how to verify it.
- Only external verification moves an issue from `review` to `done`. External verification means user confirmation, human QA, CI accepted by the user, or another explicit review signal outside the implementing agent's own confidence.

QA instructions should validate behavior through public interfaces and user-visible outcomes. Avoid asking humans to inspect internal implementation unless the issue explicitly concerns internals.

### 6. Verified Complete

- Mark `done` only after the user or designated verifier confirms the changes work as expected.
- Create `summary.md` as the comprehensive final record.
- If your tool supports issue commands, use `/issue done <id>` only after verification.

## Issue Folder Structure

```text
.issues/
├── README.md
├── index.md
└── ISSUE-N/
    ├── issue.md
    ├── plan.md
    ├── session-log.md
    ├── qa-instructions.md
    └── summary.md
```

## Session Log Format

Append each work session to `.issues/ISSUE-N/session-log.md`.

Each entry should capture:
- Prompt or ask.
- Completed work.
- Current status, blockers, or concerns.
- Plan coverage.
- Files changed.
- Verification performed or still needed.
- Next steps.

Use the full template in `.issues/README.md` when creating entries manually.

## Status Values

| Status | Meaning |
|--------|---------|
| idea | Captured thought, exploration, or vague request; not yet scoped |
| backlog | Scoped but not ready to work |
| ready | Ready to work, dependencies met, acceptance criteria clear |
| in-progress | Currently being worked on |
| review | Implementation complete, awaiting verification |
| done | Verified working and accepted |

## Command Support

If your tool provides `/issue` commands, use them. Otherwise, perform the equivalent `.issues/` file updates manually.

## Red Flags

Watch for these workflow violations:
- Creating duplicate issues instead of matching existing ones first.
- Creating implementation-ready issues from vague prompts without clarification.
- Making changes without an active issue once work is actionable.
- Ending a session without a session log entry.
- Marking `done` without external verification (for example, skipping `review`).

## Starter-Only: Remove After Copying

This section is only for maintaining the `ai-workflow-starter` repository. Remove this section after copying `AGENTS.md` into another project.

When changing the workflow model:
- Update `AGENTS.md` first.
- Avoid duplicating shared rules across files.
- Keep `.codex/commands/*` and `.claude/commands/*` in sync when command docs change.
- Update `.issues/index.md` when creating or completing issues.
- Record a session log entry for every workflow change.
