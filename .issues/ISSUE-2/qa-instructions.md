# QA Instructions: ISSUE-2 - Iterate on AI workflow model

## What Changed

The workflow starter now uses `AGENTS.md` as the canonical agent instruction source, removes obsolete duplicated agent files, moves starter-specific and optional-agent reference material into `README.md`, uses append-only `session-log.md` files, requires `qa-instructions.md` before review handoff, and tightens ambiguous agent decision rules.

## Preconditions

- Review from the repository root.
- No external services are required.

## Validation Steps

1. Open `AGENTS.md` and confirm it is project-agnostic, audit-focused, and includes `Project Details` placeholders instead of this starter repository's structure.
2. Confirm `AGENTS.md` includes intake guidance that tells agents to clarify vague requests, investigate repo-discoverable facts before asking, and avoid moving vague work directly to implementation.
3. Confirm `AGENTS.md` defines actionable work, simple versus complex requests, and decision rules for answering directly versus creating `idea`, `backlog`, `ready`, or `in-progress` issues.
4. Confirm `AGENTS.md` includes behavior-focused issue quality guidance, related-work guidance for active issues, the shorter `session-log.md` checklist, and the `qa-instructions.md` review requirement.
5. Confirm `AGENTS.md` defines external verification before `done` and uses the heading `Starter-Only: Remove After Copying`.
6. Open `.issues/README.md` and confirm the full session-log template lives there.
7. Open `README.md` and confirm starter-specific repository structure, optional command reference, and optional-agent pointer guidance live there instead of in `AGENTS.md`.
8. Confirm obsolete shared guidance files are removed: `AI-README.md`, `AI-WORKFLOW.md`, `.gitlab/duo/AGENTS.md`, `.github/copilot-instructions.md`, `.cursorrules`, and `.windsurfrules`.
9. Confirm `.codex/commands/issue.md` matches `.claude/commands/issue.md`, and `.codex/commands/workflow.md` matches `.claude/commands/workflow.md`.
10. Confirm `.issues/ISSUE-1/` and `.issues/ISSUE-2/` use `session-log.md` instead of separate `summary-N.md` session files.
11. Confirm `.issues/ISSUE-3`, `.issues/ISSUE-4`, and `.issues/ISSUE-5` exist as backlog issues created from the former README future considerations.
12. Confirm `.issues/index.md` lists `ISSUE-2` under Review, `ISSUE-3` through `ISSUE-5` under Backlog, and `ISSUE-1` under Done.

## Acceptance Criteria

- `AGENTS.md` contains only agent-facing workflow guidance and target-project placeholders.
- Human-facing starter setup, optional-agent notes, optional command reference, and starter repository structure live in `README.md`.
- Removed/obsolete agent guidance files are not present.
- The active workflow uses `session-log.md` for session progress and `summary.md` only for final verified completion.
- `AGENTS.md` gives unambiguous decision rules for actionable work, issue status selection, session-log timing, and review-to-done verification.
- Moving work to review requires a `qa-instructions.md` artifact.
- Command docs remain mirrored between Codex and Claude.

## Regression Checks

Run these commands from the repository root:

```bash
test ! -e AI-README.md
test ! -e AI-WORKFLOW.md
test ! -e .gitlab/duo/AGENTS.md
test ! -e .github/copilot-instructions.md
test ! -e .cursorrules
test ! -e .windsurfrules
cmp -s .codex/commands/issue.md .claude/commands/issue.md
cmp -s .codex/commands/workflow.md .claude/commands/workflow.md
find .issues/ISSUE-1 .issues/ISSUE-2 -maxdepth 1 -name 'summary-[0-9]*.md' -print -quit
rg --hidden -n 'Future Considerations|Micro-change' README.md AGENTS.md .codex .claude
rg --hidden -n '^## Repository Structure' AGENTS.md .codex .claude
rg --hidden -n 'Starter-Only: Remove After Copying|Decision rules:|Actionable work includes:|External verification means' AGENTS.md
```

Expected results:

- All `test ! -e` commands pass.
- Both `cmp -s` commands pass.
- The `find` command prints nothing.
- The first two `rg` commands print nothing.
- The final `rg` command prints matches in `AGENTS.md` for the clarified guidance.

## Notes

Historical issue records may still mention removed files or previous section names because they document what changed during this workflow iteration.
