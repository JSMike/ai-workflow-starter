# Session Log: ISSUE-2 - Iterate on AI workflow model

# Session 1

**Date:** 2026-04-24

**Prompt/Ask:** User said they are looking to iterate on the AI workflow model.

## Completed

- Checked existing issue records to avoid duplicating prior work.
- Created `ISSUE-2` to track workflow model iteration.
- Added an initial plan with candidate iteration areas and open questions.
- Captured the first two pain points: clarify vague work before implementation, and reduce drift across duplicated agent configuration files.

## Current Status

- `ISSUE-2` started as an idea-level planning issue.
- Awaiting user direction on which parts of the model to refine first.

## Plan Coverage

- Started planning for workflow pain points and goals.

## Files Changed

- `.issues/ISSUE-2/issue.md` - Captured the workflow iteration request.
- `.issues/ISSUE-2/plan.md` - Added initial iteration plan and open questions.
- `.issues/ISSUE-2/session-log.md` - Recorded session progress.
- `.issues/index.md` - Added `ISSUE-2` to the issue index.

## Verification

- Confirmed `.issues/ISSUE-2/` exists with issue, plan, and session log records.
- Confirmed `.issues/index.md` lists `ISSUE-2`.

## Next Steps

- Discuss which workflow pain point matters most.

# Session 2

**Date:** 2026-04-24

**Prompt/Ask:** User clarified that `AI-README.md` and `AI-WORKFLOW.md` can be consolidated into `AGENTS.md`, and that `.gitlab/duo/AGENTS.md` can be removed because GitLab Duo now uses project-level `AGENTS.md`.

## Completed

- Made `AGENTS.md` the canonical source for project guidance and workflow rules.
- Consolidated workflow rules, project conventions, intake-before-issue guidance, status semantics, and tool notes into `AGENTS.md`.
- Removed deprecated `.gitlab/duo/AGENTS.md`.
- Updated `README.md` to describe the canonical guidance structure.
- Reduced `.issues/README.md` to folder-specific conventions and pointed lifecycle rules back to `AGENTS.md`.
- Updated Codex and Claude command docs to include intake guidance, `idea` status, review-before-done semantics, and the issue template readiness checklist.
- Updated `ISSUE-2` records and index status.

## Current Status

- `ISSUE-2` moved to `in-progress`.
- The first two user pain points were implemented in documentation.

## Plan Coverage

- Addressed pre-issue clarification guidance.
- Addressed consolidation of shared agent guidance.
- Addressed removal of deprecated GitLab Duo scoped instructions.
- Partially addressed command-doc/template consistency.

## Files Changed

- `AGENTS.md` - Canonical project and workflow guidance.
- `CLAUDE.md` - Claude-specific adapter.
- `.gitlab/duo/AGENTS.md` - Removed deprecated scoped GitLab Duo instructions.
- `README.md` - Updated starter overview and getting-started guidance.
- `.issues/README.md` - Reduced duplicated workflow rules.
- `.codex/commands/issue.md` - Updated issue command guidance and templates.
- `.claude/commands/issue.md` - Mirrored Codex issue command guidance.
- `.codex/commands/workflow.md` - Updated workflow command guidance.
- `.claude/commands/workflow.md` - Mirrored Codex workflow command guidance.
- `.issues/ISSUE-2/issue.md` - Updated pain points, acceptance criteria, and status.
- `.issues/ISSUE-2/plan.md` - Updated completed plan items and chosen consolidation strategy.
- `.issues/index.md` - Moved `ISSUE-2` to In Progress.
- `.issues/ISSUE-2/session-log.md` - Recorded session progress.

## Verification

- Confirmed command docs stayed mirrored.
- Confirmed deprecated GitLab Duo scoped instructions were removed.

## Next Steps

- Capture any additional user pain points.

# Session 3

**Date:** 2026-04-24

**Prompt/Ask:** User clarified that `AI-README.md` and `AI-WORKFLOW.md` do not need to persist as placeholders because their contents moved to `AGENTS.md`.

## Completed

- Removed obsolete `AI-README.md`.
- Removed obsolete `AI-WORKFLOW.md`.
- Updated `AGENTS.md` and `README.md` so they no longer list obsolete AI files.
- Updated `ISSUE-2` issue and plan records to reflect the final single-source strategy.

## Current Status

- `ISSUE-2` remains `in-progress`.
- The canonical guidance model is now `AGENTS.md` only, with thin tool-specific adapters only where actively useful.

## Plan Coverage

- Refined and completed the shared guidance consolidation strategy.

## Files Changed

- `AI-README.md` - Removed obsolete placeholder.
- `AI-WORKFLOW.md` - Removed obsolete placeholder.
- `AGENTS.md` - Removed obsolete file references from repository structure.
- `README.md` - Removed obsolete files from starter contents.
- `.issues/ISSUE-2/issue.md` - Updated pain points, acceptance criteria, and references.
- `.issues/ISSUE-2/plan.md` - Updated chosen consolidation approach.
- `.issues/ISSUE-2/session-log.md` - Recorded session progress.

## Verification

- Confirmed obsolete AI files were removed from active starter contents.
- Confirmed command docs stayed mirrored.

## Next Steps

- Continue collecting workflow-model pain points.

# Session 4

**Date:** 2026-04-24

**Prompt/Ask:** User requested removing Cursor, Windsurf, and GitHub Copilot files, and documenting how other agent files can point to `AGENTS.md` instead of being permanently checked in.

## Completed

- Removed `.cursorrules`.
- Removed `.windsurfrules`.
- Removed `.github/copilot-instructions.md`.
- Updated `README.md` with an "Other Agents" section and an example thin pointer to `AGENTS.md`.
- Updated `AGENTS.md` to describe only actively used tool-specific files and discourage unused checked-in adapters.
- Updated `ISSUE-2` issue and plan records.

## Current Status

- `ISSUE-2` remains `in-progress`.
- The repo now uses `AGENTS.md` as the sole canonical workflow source, with only actively useful adapters checked in.

## Plan Coverage

- Further refined shared guidance consolidation by removing unused agent-entrypoint noise.

## Files Changed

- `.github/copilot-instructions.md` - Removed unused Copilot adapter.
- `.cursorrules` - Removed unused Cursor adapter.
- `.windsurfrules` - Removed unused Windsurf adapter.
- `README.md` - Added guidance and example for optional other-agent pointers.
- `AGENTS.md` - Updated repository structure and tool-specific guidance.
- `.issues/ISSUE-2/issue.md` - Updated pain points and acceptance criteria.
- `.issues/ISSUE-2/plan.md` - Updated chosen consolidation approach.
- `.issues/ISSUE-2/session-log.md` - Recorded session progress.

## Verification

- Confirmed removed optional adapter files no longer exist.
- Confirmed command docs stayed mirrored.

## Next Steps

- Continue collecting workflow-model pain points.

# Session 5

**Date:** 2026-04-24

**Prompt/Ask:** User noted that some notes added to `AGENTS.md` belong in `README.md`; general tool-specific notes about agents that may not be used add unnecessary context and tokens for active agents.

## Completed

- Removed broad optional-agent notes from `AGENTS.md`.
- Simplified `AGENTS.md` repository structure to avoid listing optional agent adapters not part of the working workflow.
- Kept only workflow-critical command sync guidance in `AGENTS.md`.
- Moved general optional-agent guidance into `README.md`.
- Added README guidance that optional-agent notes should stay out of `AGENTS.md` to reduce agent context.
- Updated `ISSUE-2` issue and plan records.

## Current Status

- `ISSUE-2` remains `in-progress`.
- `AGENTS.md` is leaner and more directly focused on instructions needed during normal agent work.

## Plan Coverage

- Further refined shared guidance consolidation by separating agent runtime instructions from repository-maintainer guidance.

## Files Changed

- `AGENTS.md` - Removed general optional-agent notes and reduced tool-specific context.
- `README.md` - Added maintainer guidance for optional agent files and command-doc sync.
- `.issues/ISSUE-2/issue.md` - Added pain point and completed acceptance criterion.
- `.issues/ISSUE-2/plan.md` - Updated chosen consolidation approach.
- `.issues/ISSUE-2/session-log.md` - Recorded session progress.

## Verification

- Confirmed optional-agent details live in `README.md`, not `AGENTS.md`.
- Confirmed command docs stayed mirrored.

## Next Steps

- Continue collecting workflow-model pain points.

# Session 6

**Date:** 2026-04-24

**Prompt/Ask:** User asked whether the optional command reference in `AGENTS.md` belongs in `README.md` for human users instead of in the AI-agent guidance.

## Completed

- Replaced the detailed optional command table in `AGENTS.md` with a short `Command Support` rule.
- Added the detailed optional command table to `README.md`.
- Updated `ISSUE-2` issue and plan records.

## Current Status

- `ISSUE-2` remains `in-progress`.
- `AGENTS.md` is leaner and avoids carrying reference material that agents do not need during normal work.

## Plan Coverage

- Further separated agent runtime instructions from human/reference documentation.

## Files Changed

- `AGENTS.md` - Removed detailed command table and kept minimal command-use instruction.
- `README.md` - Added detailed optional command reference.
- `.issues/ISSUE-2/issue.md` - Added and checked off command-reference cleanup.
- `.issues/ISSUE-2/plan.md` - Updated chosen documentation split.
- `.issues/ISSUE-2/session-log.md` - Recorded session progress.

## Verification

- Confirmed `AGENTS.md` only has command behavior guidance, while the command table is in `README.md`.
- Confirmed command docs stayed mirrored.

## Next Steps

- Continue collecting workflow-model pain points.

# Session 7

**Date:** 2026-04-24

**Prompt/Ask:** User suggested that maintaining many per-session files may be overly burdensome and that a single `session-log.md` could concatenate session details.

## Completed

- Updated `AGENTS.md` to use append-only `session-log.md` entries instead of separate per-session files.
- Updated `.issues/README.md` structure guidance to use `session-log.md`.
- Updated Codex and Claude issue command docs to append `/issue session` output to `session-log.md`.
- Updated Codex and Claude workflow command docs to reference session-log entries.
- Updated `ISSUE-2` issue and plan records with the new session-log model.
- Created this consolidated `session-log.md` for `ISSUE-2`.

## Current Status

- `ISSUE-2` remains `in-progress`.
- New workflow guidance uses `session-log.md` for session progress and keeps `summary.md` for final verified completion.

## Plan Coverage

- Addressed a workflow simplification pain point: reducing issue-folder noise and overhead from many session files.

## Files Changed

- `AGENTS.md` - Replaced separate per-session file guidance with `session-log.md`.
- `.issues/README.md` - Updated issue folder structure.
- `.codex/commands/issue.md` - Updated `/issue session` behavior and templates.
- `.claude/commands/issue.md` - Mirrored Codex issue command changes.
- `.codex/commands/workflow.md` - Updated workflow guidance around session-log entries.
- `.claude/commands/workflow.md` - Mirrored Codex workflow changes.
- `.issues/ISSUE-2/issue.md` - Added pain point and acceptance criterion.
- `.issues/ISSUE-2/plan.md` - Added selected single-session-log approach.
- `.issues/ISSUE-2/session-log.md` - Started consolidated session log for this issue.

## Verification

- Confirmed active workflow docs reference `session-log.md`.
- Confirmed command docs stayed mirrored.

## Next Steps

- Normalize the starter issue records so they follow the session-log pattern directly.

# Session 8

**Date:** 2026-04-24

**Prompt/Ask:** User clarified that this starter is intended to be added fresh, so it should directly use the newly established `session-log.md` pattern.

## Completed

- Converted `ISSUE-1` session records into `.issues/ISSUE-1/session-log.md`.
- Consolidated `ISSUE-2` session records into this `session-log.md`.
- Removed separate per-session files from `ISSUE-1` and `ISSUE-2`.
- Removed migration language about old session-file conventions from current workflow docs.
- Updated command docs so new issues only scan `session-log.md` for session numbering.

## Current Status

- `ISSUE-2` remains `in-progress`.
- The starter now demonstrates the current `session-log.md` convention directly.

## Plan Coverage

- Completed the single-session-log conversion for existing starter issues.

## Files Changed

- `.issues/ISSUE-1/session-log.md` - Added consolidated session log.
- `.issues/ISSUE-1` per-session files - Removed.
- `.issues/ISSUE-2/session-log.md` - Consolidated session history and added Session 8.
- `.issues/ISSUE-2` per-session files - Removed.
- `.issues/README.md` - Removed migration guidance.
- `.codex/commands/issue.md` - Removed old session-file numbering compatibility.
- `.claude/commands/issue.md` - Mirrored Codex issue command changes.

## Verification

- Ran a targeted stale-reference search for old per-session file naming; no matches remain.
- Ran `find .issues/ISSUE-1 .issues/ISSUE-2 -maxdepth 1 -type f -printf '%p\\n' | sort`; issue folders now contain `session-log.md` instead of separate session files.
- Ran `cmp -s .codex/commands/issue.md .claude/commands/issue.md` and `cmp -s .codex/commands/workflow.md .claude/commands/workflow.md`; both returned `0`, confirming command docs remain mirrored.
- Ran `git status --short`; expected deletions, updates, and new session logs are present.

## Next Steps

- Continue collecting workflow-model pain points or move `ISSUE-2` to review when the iteration is complete.

# Session 9

**Date:** 2026-04-24

**Prompt/Ask:** User asked to review `../matt-pocock-skills` for inspiration and determine whether `AGENTS.md` should be revised with stronger supplemental workflow language.

## Completed

- Located the referenced skills directory at `../matt-pockock-skills`.
- Reviewed the local skills for process patterns relevant to this workflow.
- Identified useful patterns: focused clarification, one-question-at-a-time complex planning, exploring the repo before asking discoverable questions, durable behavior-focused issue writing, vertical slices, explicit non-goals, domain-language precision, and public-behavior validation.
- Updated `AGENTS.md` with stronger Intake Before Issues guidance.
- Added an `Issue Quality` section to `AGENTS.md`.
- Strengthened readiness guidance before moving issues to `ready` or `in-progress`.
- Strengthened QA guidance to validate behavior through public interfaces and user-visible outcomes.
- Updated `ISSUE-2` issue and plan records.

## Current Status

- `ISSUE-2` remains `in-progress`.
- `AGENTS.md` now gives agents sharper guidance for intake, issue quality, slicing, readiness, and QA validation.

## Plan Coverage

- Improved workflow language using the skill set as inspiration without importing skill-specific mechanics.

## Files Changed

- `AGENTS.md` - Added clarification discipline, issue quality, vertical-slice, readiness, and QA validation guidance.
- `.issues/ISSUE-2/issue.md` - Added and checked off skill-review improvement criterion.
- `.issues/ISSUE-2/plan.md` - Updated selected approaches for intake and durable issue quality.
- `.issues/ISSUE-2/session-log.md` - Recorded this session.

## Verification

- Confirm `AGENTS.md` includes the revised intake and issue-quality guidance.
- Confirm Codex and Claude command docs still match.

## Next Steps

- Continue collecting workflow-model pain points or move `ISSUE-2` to review when the iteration is complete.

# Session 10

**Date:** 2026-04-24

**Prompt/Ask:** User requested creating backlog issues from the `README.md` Future Considerations section and then removing that section from the README.

## Completed

- Created `ISSUE-3` for SQLite and MCP-backed issue storage.
- Created `ISSUE-4` for external issue ID integrations.
- Created `ISSUE-5` for syncing audit details to external systems.
- Added session logs for each new backlog issue.
- Updated `.issues/index.md` to list the new backlog items.
- Removed the `Future Considerations` section from `README.md`.

## Current Status

- `ISSUE-2` remains `in-progress`.
- Future consideration items now live as backlog issues instead of README notes.

## Plan Coverage

- Moved speculative future work into the issue workflow backlog.

## Files Changed

- `README.md` - Removed Future Considerations section.
- `.issues/index.md` - Added `ISSUE-3`, `ISSUE-4`, and `ISSUE-5` to Backlog.
- `.issues/ISSUE-3/issue.md` - Captured SQLite/MCP-backed issue storage.
- `.issues/ISSUE-3/session-log.md` - Recorded issue creation.
- `.issues/ISSUE-4/issue.md` - Captured external issue ID integration.
- `.issues/ISSUE-4/session-log.md` - Recorded issue creation.
- `.issues/ISSUE-5/issue.md` - Captured external audit sync tooling.
- `.issues/ISSUE-5/session-log.md` - Recorded issue creation.
- `.issues/ISSUE-2/session-log.md` - Recorded this maintenance session.

## Verification

- Ran `rg -n 'Future Considerations|SQLite|Jira|sync tooling|external systems|MCP' README.md .issues/index.md .issues/ISSUE-3 .issues/ISSUE-4 .issues/ISSUE-5`; README no longer contains the Future Considerations section and the new issue records contain the former future items.
- Ran `find .issues/ISSUE-3 .issues/ISSUE-4 .issues/ISSUE-5 -maxdepth 1 -type f -printf '%p\\n' | sort`; each new issue has `issue.md` and `session-log.md`.
- Reviewed `.issues/index.md`; `ISSUE-3`, `ISSUE-4`, and `ISSUE-5` are listed under Backlog.

## Next Steps

- Continue collecting workflow-model pain points or move `ISSUE-2` to review when the iteration is complete.

# Session 11

**Date:** 2026-04-24

**Prompt/Ask:** User requested a workflow feature: when an agent completes a unit of work and moves an item to review, it should generate `qa-instructions.md` with a step-by-step guide for human validation.

## Completed

- Added `qa-instructions.md` to the canonical issue folder structure.
- Updated `AGENTS.md` to require QA instructions before or when moving an issue to `review`.
- Updated `.issues/README.md` to describe `qa-instructions.md`.
- Updated `README.md` optional command reference to note that moving to `review` creates QA instructions.
- Updated Codex and Claude issue command docs so `/issue status <id> review` creates or updates `qa-instructions.md`.
- Added a `qa-instructions.md` template to command docs.
- Updated Codex and Claude workflow docs to call out review handoff with QA instructions.
- Updated `ISSUE-2` issue and plan records.

## Current Status

- `ISSUE-2` remains `in-progress`.
- Review handoff now requires human QA instructions.

## Plan Coverage

- Added a new review-stage artifact to improve human validation and reduce ambiguity during acceptance.

## Files Changed

- `AGENTS.md` - Added QA instructions requirement and issue folder artifact.
- `.issues/README.md` - Added `qa-instructions.md` folder convention.
- `README.md` - Updated optional command reference.
- `.codex/commands/issue.md` - Added review-status QA generation behavior and template.
- `.claude/commands/issue.md` - Mirrored Codex issue command changes.
- `.codex/commands/workflow.md` - Added QA review handoff guidance.
- `.claude/commands/workflow.md` - Mirrored Codex workflow changes.
- `.issues/ISSUE-2/issue.md` - Added pain point and acceptance criterion.
- `.issues/ISSUE-2/plan.md` - Added selected QA instructions approach.
- `.issues/ISSUE-2/session-log.md` - Recorded this session.

## Verification

- Ran `rg --hidden -n 'qa-instructions|QA Instructions|Review without QA|status <id> review|moving to `review`|Submitting For Review' AGENTS.md README.md .issues/README.md .codex/commands .claude/commands .issues/ISSUE-2`; active workflow docs now mention `qa-instructions.md`.
- Ran `cmp -s .codex/commands/issue.md .claude/commands/issue.md` and `cmp -s .codex/commands/workflow.md .claude/commands/workflow.md`; both returned `0`, confirming command docs remain mirrored.
- Ran `git status --short`; expected updates are present.

## Next Steps

- Continue collecting workflow-model pain points or move `ISSUE-2` to review when the iteration is complete.

# Session 12

**Date:** 2026-04-24

**Prompt/Ask:** User asked to update the `AGENTS.md` Project Overview because the file will be copied into other projects and should emphasize audit workflow expectations instead of describing the starter kit.

## Completed

- Rewrote the `AGENTS.md` Project Overview as an agent-facing workflow contract.
- Emphasized that the project requires auditable AI work.
- Added explicit user expectations around clarification, tracking, current plans/progress, handoff context, session logs, and avoiding premature `done` status.
- Updated `ISSUE-2` issue records.

## Current Status

- `ISSUE-2` remains `in-progress`.
- `AGENTS.md` now reads more appropriately for copied projects.

## Plan Coverage

- Further improved the canonical agent guidance to reduce ambiguity and reinforce workflow compliance.

## Files Changed

- `AGENTS.md` - Updated Project Overview.
- `.issues/ISSUE-2/issue.md` - Added pain point and completed acceptance criterion.
- `.issues/ISSUE-2/session-log.md` - Recorded this session.

## Verification

- Review the top of `AGENTS.md` and confirm the overview is project-agnostic and expectation-focused.

## Next Steps

- Continue collecting workflow-model pain points or move `ISSUE-2` to review when the iteration is complete.

# Session 13

**Date:** 2026-04-24

**Prompt/Ask:** User asked to review the Micro-change Exception because the 20-line rule is too strict; related follow-up asks during active work should remain in the current issue when aligned with current goals.

## Completed

- Replaced the strict Micro-change Exception in `AGENTS.md` with `Related Work During Active Issues` guidance.
- Removed file-count and line-count criteria.
- Added guidance to continue under the active issue for clarifications, refinements, tangentially related asks, verification, documentation, and handoff work.
- Added requirements to update `issue.md`, `plan.md`, and `session-log.md` when related work changes scope or approach.
- Clarified when a new issue is still appropriate.
- Updated `ISSUE-2` issue and plan records.

## Current Status

- `ISSUE-2` remains `in-progress`.
- The workflow now discourages unnecessary issue creation for aligned follow-up asks.

## Plan Coverage

- Improved issue scope guidance and reduced tracking churn for active work.

## Files Changed

- `AGENTS.md` - Replaced Micro-change Exception with related-work guidance.
- `.issues/ISSUE-2/issue.md` - Added and checked off related-work guidance criterion.
- `.issues/ISSUE-2/plan.md` - Added selected approach for related work under active issues.
- `.issues/ISSUE-2/session-log.md` - Recorded this session.

## Verification

- Confirmed `AGENTS.md` no longer contains the strict 20-line micro-change rule.
- Confirmed guidance explains when to continue active issues versus create a new issue.

## Next Steps

- Continue collecting workflow-model pain points or move `ISSUE-2` to review when the iteration is complete.

# Session 14

**Date:** 2026-04-24

**Prompt/Ask:** User noted that the `Updating This Starter` section is specific to this starter project and should include instructions to remove it after copying `AGENTS.md` into another project.

## Completed

- Added a starter-only note to `AGENTS.md` under `Updating This Starter`.
- Clarified that the section should be removed after copying `AGENTS.md` into another project.
- Updated `ISSUE-2` issue and plan records.
- Reordered session log entries so sessions are sequential.

## Current Status

- `ISSUE-2` remains `in-progress`.
- Starter-maintenance guidance remains available in this repo without being silently carried into target projects.

## Plan Coverage

- Further separated starter-maintainer instructions from copied-project agent guidance.

## Files Changed

- `AGENTS.md` - Marked `Updating This Starter` as starter-only and removable after copy.
- `.issues/ISSUE-2/issue.md` - Added and checked off starter-maintenance cleanup.
- `.issues/ISSUE-2/plan.md` - Updated chosen documentation split.
- `.issues/ISSUE-2/session-log.md` - Recorded this session and reordered prior entries.

## Verification

- Review the `Updating This Starter` section in `AGENTS.md`.
- Confirm session headings are sequential.
- Confirm Codex and Claude command docs still match.

## Next Steps

- Continue collecting workflow-model pain points or move `ISSUE-2` to review when the iteration is complete.

# Session 15

**Date:** 2026-04-24

**Prompt/Ask:** User noted that the `AGENTS.md` Repository Structure section is starter-specific and belongs in `README.md`; copied projects should instead have a project-details section, potentially merged with an existing `AGENTS.md` or generated by `/init`.

## Completed

- Replaced the starter-specific `Repository Structure` section in `AGENTS.md` with a `Project Details` section for target-project information.
- Added placeholders for project purpose, runtime, commands, directories, environment setup, deployment notes, and conventions.
- Added guidance to merge workflow instructions into an existing target-project `AGENTS.md` instead of replacing project-specific details.
- Added a `Starter Repository Structure` section to `README.md`.
- Updated README customization guidance to mention `/init` and existing `AGENTS.md` preservation.
- Updated `ISSUE-2` issue and plan records.
- Normalized prior session numbering in this log.

## Current Status

- `ISSUE-2` remains `in-progress`.
- `AGENTS.md` is less starter-specific and better suited for copying into target projects.

## Plan Coverage

- Further separated starter-maintainer documentation from agent-facing target-project guidance.

## Files Changed

- `AGENTS.md` - Replaced starter repository structure with target-project details placeholders.
- `README.md` - Added starter repository structure and customization guidance.
- `.issues/ISSUE-2/issue.md` - Added and checked off project-details cleanup.
- `.issues/ISSUE-2/plan.md` - Updated chosen documentation split.
- `.issues/ISSUE-2/session-log.md` - Recorded this session and normalized session numbering.

## Verification

- Review `AGENTS.md` and confirm it no longer describes this starter repo's file layout.
- Review `README.md` and confirm starter-specific structure lives there.
- Confirm Codex and Claude command docs still match.

## Next Steps

- Continue collecting workflow-model pain points or move `ISSUE-2` to review when the iteration is complete.

# Session 16

**Date:** 2026-04-24

**Prompt/Ask:** User asked to proceed with the workflow iteration after providing the full set of pain points and optimization questions.

## Completed

- Verified `ISSUE-2` session headings are sequential through Session 15.
- Verified Codex and Claude command docs are mirrored.
- Reviewed `AGENTS.md`, `README.md`, `ISSUE-2` issue records, and the issue index for stale workflow state.
- Updated `ISSUE-2` acceptance criteria to reflect the implemented iteration choices.
- Updated the plan to mark status/discovery guidance complete and defer only lower-value future candidates.
- Created `qa-instructions.md` for human review.
- Tightened the QA regression checks to avoid false positives from the intentional README starter-structure section.
- Moved `ISSUE-2` to `review` in `issue.md` and `.issues/index.md`.
- Corrected the session-log ordering so Session 16 appears after Session 15.

## Current Status

- `ISSUE-2` is in `review`.
- Human validation should follow `.issues/ISSUE-2/qa-instructions.md`.

## Plan Coverage

- Completed the workflow documentation iteration and review handoff.

## Files Changed

- `.issues/ISSUE-2/issue.md` - Moved to review and completed remaining implemented acceptance criteria.
- `.issues/ISSUE-2/plan.md` - Updated completed/deferred planning state and review next steps.
- `.issues/ISSUE-2/qa-instructions.md` - Added step-by-step human validation guidance.
- `.issues/index.md` - Moved `ISSUE-2` from In Progress to Review.
- `.issues/ISSUE-2/session-log.md` - Recorded review handoff.

## Verification

- Ran `rg -n '^# Session ' .issues/ISSUE-2/session-log.md`; headings are sequential through Session 16.
- Ran `cmp -s .codex/commands/issue.md .claude/commands/issue.md`; returned `0`.
- Ran `cmp -s .codex/commands/workflow.md .claude/commands/workflow.md`; returned `0`.
- Ran removed-file checks for obsolete AI/agent files; returned `0`.
- Ran stale active-guidance searches for old Future Considerations, Micro-change, and AGENTS Repository Structure guidance; no matches in active docs.
- Confirmed no `summary-N.md` files remain for `ISSUE-1` or `ISSUE-2`.
- Reviewed active workflow docs for stale references to removed files, old summary-session files, and old micro-change guidance.

## Next Steps

- Human reviewer validates the workflow changes using `qa-instructions.md`.
- If accepted, move `ISSUE-2` to `done` and create `summary.md`.

# Session 17

**Date:** 2026-04-24

**Prompt/Ask:** User asked to proceed with revisions based on review observations about ambiguous or improvable `AGENTS.md` guidance.

## Completed

- Defined actionable work in `AGENTS.md` with concrete examples.
- Clarified simple versus complex requests for intake behavior.
- Added decision rules for answering directly, preserving ideas, creating backlog items, moving to ready, and starting in-progress work.
- Clarified the new-work sequence: match, intake, choose status, create or update issue, then plan.
- Clarified session-log timing so one entry can cover related edits in an uninterrupted session, but a new entry is required before handoff or final response.
- Clarified external verification before `done`.
- Moved the full session-log template to `.issues/README.md` and kept `AGENTS.md` to a shorter checklist.
- Renamed starter-maintenance guidance to `Starter-Only: Remove After Copying`.
- Aligned Codex and Claude command docs with the revised session-log and verification wording.
- Updated `ISSUE-2` issue, plan, and QA instructions for this follow-up revision.

## Current Status

- `ISSUE-2` remains in `review`.
- Human validation should use the updated `.issues/ISSUE-2/qa-instructions.md`.

## Plan Coverage

- Completed the ambiguity-reduction follow-up identified during `AGENTS.md` review.

## Files Changed

- `AGENTS.md` - Tightened decision rules, session-log timing, verification wording, and starter-only heading.
- `.issues/README.md` - Added the full session-log template.
- `.codex/commands/issue.md` - Aligned session-log and done-verification wording.
- `.claude/commands/issue.md` - Mirrored Codex issue command updates.
- `.codex/commands/workflow.md` - Aligned session-log reminders.
- `.claude/commands/workflow.md` - Mirrored Codex workflow command updates.
- `.issues/ISSUE-2/issue.md` - Added completed ambiguity-reduction criterion.
- `.issues/ISSUE-2/plan.md` - Added ambiguity-reduction chosen approach.
- `.issues/ISSUE-2/qa-instructions.md` - Updated human validation steps.
- `.issues/ISSUE-2/session-log.md` - Recorded this revision.

## Verification

- Ran `cmp -s .codex/commands/issue.md .claude/commands/issue.md`; returned `0`.
- Ran `cmp -s .codex/commands/workflow.md .claude/commands/workflow.md`; returned `0`.
- Ran removed-file checks for obsolete AI/agent files; returned `0`.
- Confirmed no `summary-N.md` files remain for `ISSUE-1` or `ISSUE-2`.
- Ran stale active-guidance searches for old Future Considerations, Micro-change, and AGENTS Repository Structure guidance; no matches in active docs.
- Confirmed `AGENTS.md` contains actionable-work examples, decision rules, external verification wording, and the starter-only heading.
- Confirmed `.issues/README.md` contains the full session-log template.
- Ran `rg -n '^# Session ' .issues/ISSUE-2/session-log.md`; headings are sequential through Session 17.

## Next Steps

- Run final verification checks.
- Human reviewer validates the workflow changes using `qa-instructions.md`.

# Session 18

**Date:** 2026-04-24

**Prompt/Ask:** User asked for a fresh read of `AGENTS.md` to confirm whether prior concerns were resolved and identify any further suggested revisions.

## Completed

- Re-read `AGENTS.md` from the current file state.
- Evaluated the file against the session goals: ambiguity reduction, workflow steering, copied-project portability, context/noise reduction, and review handoff clarity.
- Confirmed the prior concerns are materially resolved.
- Identified only optional polish-level improvements: reduce duplicated status explanations and clarify one command-order phrase around `/issue create`.

## Current Status

- `ISSUE-2` remains in `review`.
- No blocking concerns were found in `AGENTS.md`.

## Plan Coverage

- Completed a final review pass against the ambiguity concerns raised in this session.

## Files Changed

- `.issues/ISSUE-2/session-log.md` - Recorded this review pass.

## Verification

- Read `AGENTS.md` directly from disk and reviewed all workflow sections.

## Next Steps

- Human reviewer can validate using `qa-instructions.md`.

# Session 19

**Date:** 2026-04-24

**Prompt/Ask:** User asked to make the suggested polish changes in `AGENTS.md`.

## Completed

- Removed the redundant `Status distinction` block from `AGENTS.md`.
- Kept the canonical status definitions in the `Status Values` table.
- Clarified the `/issue create <title>` guidance so agents create the issue first and then set status according to readiness.

## Current Status

- `ISSUE-2` remains in `review`.
- The final polish suggestions have been applied.

## Plan Coverage

- Completed optional polish identified in the fresh `AGENTS.md` review.

## Files Changed

- `AGENTS.md` - Removed duplicated status wording and clarified `/issue create` status timing.
- `.issues/ISSUE-2/session-log.md` - Recorded this polish pass.

## Verification

- Ran `rg -n 'Status distinction|/issue create <title>|Status Values|Decision rules' AGENTS.md`; `Status distinction` no longer appears, the clarified `/issue create <title>` guidance appears, and `Status Values` remains.
- Ran `cmp -s .codex/commands/issue.md .claude/commands/issue.md`; returned `0`.
- Ran `cmp -s .codex/commands/workflow.md .claude/commands/workflow.md`; returned `0`.
- Ran `rg -n '^# Session ' .issues/ISSUE-2/session-log.md`; headings are sequential through Session 19.

## Next Steps

- Human reviewer can validate using `qa-instructions.md`.

# Session 20

**Date:** 2026-04-24

**Prompt/Ask:** User requested applying the review feedback to improve `AGENTS.md` clarity and conciseness by removing or adding detail where necessary.

## Completed

- Moved `ISSUE-2` from `review` back to `in-progress` to apply the requested changes.
- Dropped the duplicated audit-trail list from the `Core Workflow Principle` section since Steps 5, 6 and the Issue Folder Structure section already cover it.
- Removed the brainstorming-issue note from `Intake Before Issues` because the `Decision rules` list already covers it.
- Tightened Workflow Step 1 to a three-bullet checklist and removed restated intake/status wording.
- Tightened Workflow Step 2 to three bullets, cross-referencing `Decision rules` for status selection and removing the duplicated "new vague requests should start as idea" bullet.
- Promoted session-log `Entry timing` into Step 4 top-level so the append-before-handoff / mid-session-addend rules apply universally, and simplified `Related Work During Active Issues` to reference the top-level rules.
- Collapsed the last two Red Flags bullets about `done` verification into one.
- Updated `plan.md` to record the additional ambiguity-reduction passes.
- Moved `ISSUE-2` back to `review`.

## Current Status

- `ISSUE-2` is back in `review` with a tighter `AGENTS.md`.
- `AGENTS.md` is now 220 lines, down from 234.

## Plan Coverage

- Completed additional ambiguity-reduction polish identified during the post-Session-19 review pass.

## Files Changed

- `AGENTS.md` - Consolidated duplicated status guidance, promoted session-log entry timing, collapsed Red Flags overlap, tightened Workflow Steps 1 and 2, dropped the Core Principle audit-trail list.
- `.issues/ISSUE-2/issue.md` - Round-tripped status `review` -> `in-progress` -> `review`.
- `.issues/ISSUE-2/plan.md` - Recorded the additional ambiguity-reduction passes.
- `.issues/ISSUE-2/session-log.md` - Recorded this session.
- `.issues/index.md` - Round-tripped `ISSUE-2` through In Progress back to Review.

## Verification

- Ran `rg --hidden -n 'Starter-Only: Remove After Copying|Decision rules:|Actionable work includes:|External verification means' AGENTS.md`; all four phrases still present.
- Ran `rg --hidden -n 'Future Considerations|Micro-change' README.md AGENTS.md .codex .claude`; no matches.
- Ran `rg --hidden -n '^## Repository Structure' AGENTS.md .codex .claude`; no matches.
- Confirmed `find .issues/ISSUE-1 .issues/ISSUE-2 -maxdepth 1 -name 'summary-[0-9]*.md'` prints nothing.
- Confirmed `AGENTS.md` line count dropped from 234 to 220.
- Read the revised `AGENTS.md` end-to-end; duplicate status guidance is gone, session-log timing is now a top-level Step 4 block, and the Red Flags tail is collapsed.

## Next Steps

- Human reviewer validates the workflow changes using `qa-instructions.md`.

# Session 21

**Date:** 2026-04-24

**Prompt/Ask:** User asked to review another agent's refinement of `AGENTS.md` and determine whether the instructions remain clear or were over-corrected.

## Completed

- Read the current `AGENTS.md` from disk.
- Reviewed the diff for the latest refinement.
- Confirmed the instructions remain clear and the core workflow still aligns with the session goals.
- Identified one mild over-correction: removing the audit-trail checklist made the purpose of `.issues/` less explicit.
- Identified one minor wording risk: `/issue create` is still clear enough, but could better state that commands create the issue artifact before status adjustment.

## Current Status

- `ISSUE-2` remains in `review`.
- No blocking issue was found in `AGENTS.md`.

## Plan Coverage

- Completed review of the external-agent refinement pass.

## Files Changed

- `.issues/ISSUE-2/session-log.md` - Recorded this review pass.

## Verification

- Read `AGENTS.md` directly from disk.
- Reviewed `git diff -- AGENTS.md` to identify the latest refinement changes.

## Next Steps

- If further polish is desired, restore a compact audit-trail purpose sentence or checklist near `Core Workflow Principle`.

# Session 22

**Date:** 2026-04-24

**Prompt/Ask:** User agreed with both findings from the external-agent refinement review and asked to restore or refine based on them.

## Completed

- Restored a compact audit-trail purpose statement near `Core Workflow Principle`.
- Clarified the starting-new-work sequence so manual agents create the issue folder with `issue.md` before creating or updating `plan.md`.
- Reordered the tail of this session log so Sessions 18-22 are sequential after the external agent's inserted Session 20.

## Current Status

- `ISSUE-2` remains in `review`.
- The two accepted review findings have been addressed.

## Plan Coverage

- Completed the external-agent refinement follow-up.

## Files Changed

- `AGENTS.md` - Restored audit-trail purpose and clarified manual issue creation sequence.
- `.issues/ISSUE-2/session-log.md` - Recorded this follow-up.

## Verification

- Ran `rg -n 'audit trail should preserve|create the issue folder with `issue.md`' AGENTS.md`; both restored/refined lines are present.
- Ran `cmp -s .codex/commands/issue.md .claude/commands/issue.md`; returned `0`.
- Ran `cmp -s .codex/commands/workflow.md .claude/commands/workflow.md`; returned `0`.
- Ran `rg -n '^# Session ' .issues/ISSUE-2/session-log.md`; headings are sequential through Session 22.

## Next Steps

- Human reviewer can validate using `qa-instructions.md`.

# Session 23

**Date:** 2026-04-24

**Prompt/Ask:** User asked whether `AGENTS.md` could be made more token efficient and noted a tokenizer warning about Unicode characters mapping to multiple tokens.

## Completed

- Checked `AGENTS.md` for non-ASCII characters.
- Confirmed the tokenizer warning comes from box-drawing characters in the issue folder tree.
- Reviewed `AGENTS.md` for additional token-efficiency opportunities.

## Current Status

- `ISSUE-2` remains in `review`.
- No edits were made to `AGENTS.md` in this pass.

## Plan Coverage

- Completed a token-efficiency review of the current agent guidance.

## Files Changed

- `.issues/ISSUE-2/session-log.md` - Recorded this review pass.

## Verification

- Ran `LC_ALL=C grep -nP '[^\\x00-\\x7F]' AGENTS.md`; only the issue-folder tree lines contain non-ASCII characters.
- Ran `wc -l -w -c AGENTS.md`; current file is 222 lines, 1529 words, and 10264 bytes.

## Next Steps

- If desired, replace the tree with ASCII and consider a small compression pass on workflow/status sections.

# Session 24

**Date:** 2026-04-24

**Prompt/Ask:** User decided to keep the Unicode tree for now and asked to add token-efficiency suggestions as a separate backlog issue.

## Completed

- Left `AGENTS.md` unchanged.
- Created `ISSUE-6` to track future `AGENTS.md` token-efficiency review.
- Added `ISSUE-6` to `.issues/index.md` under Backlog.
- Normalized this session log so Sessions 19-24 are sequential.

## Current Status

- `ISSUE-2` remains in `review`.
- `ISSUE-6` is in `backlog`.

## Plan Coverage

- Captured token-efficiency suggestions as future work instead of modifying the active workflow instructions.

## Files Changed

- `.issues/ISSUE-6/issue.md` - Created backlog issue.
- `.issues/ISSUE-6/session-log.md` - Recorded issue creation.
- `.issues/index.md` - Added `ISSUE-6` under Backlog.
- `.issues/ISSUE-2/session-log.md` - Recorded this follow-up and normalized session order.

## Verification

- Ran `rg -n 'ISSUE-6|Review AGENTS.md token efficiency' .issues/index.md .issues/ISSUE-6/issue.md .issues/ISSUE-6/session-log.md`; `ISSUE-6` exists and is listed in the Backlog section.
- Ran `rg -n '^# Session ' .issues/ISSUE-2/session-log.md`; headings are sequential through Session 24.

## Next Steps

- Human reviewer can continue validating `ISSUE-2` using `qa-instructions.md`.

# Session 25

**Date:** 2026-04-24

**Prompt/Ask:** User confirmed that `ISSUE-2` is done.

## Completed

- Marked `ISSUE-2` as `done`.
- Created final `summary.md`.
- Moved `ISSUE-2` from Review to Done in `.issues/index.md`.

## Current Status

- `ISSUE-2` is complete.

## Plan Coverage

- Completed final verified closeout.

## Files Changed

- `.issues/ISSUE-2/issue.md` - Updated status to `done`.
- `.issues/ISSUE-2/summary.md` - Added final completion summary.
- `.issues/index.md` - Moved `ISSUE-2` to Done.
- `.issues/ISSUE-2/session-log.md` - Recorded verified completion.

## Verification

- User explicitly confirmed `ISSUE-2` is done.

## Next Steps

- Continue with backlog issues if requested.
