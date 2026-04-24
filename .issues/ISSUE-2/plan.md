# Plan: ISSUE-2 - Iterate on AI workflow model

## Goals

- Keep the workflow lightweight enough for routine agent work.
- Preserve the audit trail and handoff value that motivated the starter.
- Identify improvements that reduce agent mistakes, duplicate tracking, and stale issue records.

## Proposed Iteration Areas

- [x] Add a pre-issue discovery/intake stage for prompts that lack enough detail to create a useful issue.
- [x] Require agents to assess requirement clarity before planning or implementation.
- [x] Define when clarifying questions are mandatory versus when reasonable assumptions are acceptable.
- [x] Define when related follow-up asks should stay under the active issue instead of creating a new issue.
- [x] Strengthen intake with focused question limits, one-question-at-a-time complex planning, and repo exploration before asking.
- [x] Clarify when to create `idea`, `backlog`, `ready`, and `in-progress` issues.
- [x] Add explicit guidance for discovery-only sessions versus implementation sessions.
- [x] Tighten issue guidance so requirements, decisions, scope, and verification are easier to scan.
- [x] Add required human QA instructions when work moves to review.
- [x] Tighten ambiguous `AGENTS.md` decision rules, session-log timing, and verification wording after review.
- [ ] Add a lightweight decision log pattern for workflow/model changes.
- [ ] Improve index generation expectations so manual updates stay consistent.
- [x] Reconcile status guidance into canonical `AGENTS.md` and reduce `.issues/README.md` to folder conventions.
- [x] Consolidate duplicated agent instructions into `AGENTS.md` and remove unused tool-specific entrypoints.

## Open Questions

- Should vague prompts create an `idea` issue immediately, or should agents ask clarification questions first and only create an issue once scope is clearer?
- Should the workflow include a short "requirements readiness checklist" before any issue can move to `ready` or `in-progress`?
- Which part of the current flow feels too heavy: issue creation, planning, session logging, review gating, or index maintenance?
- Is the goal to improve this starter repo only, or to define a portable workflow spec for multiple repositories?
- Should the model support multiple active agents working on the same issue, or keep one active owner per issue?
- Should verification remain user-driven, or should the workflow define automated/agent verification levels?
- Tool-specific files now contain minimal pointers to canonical `AGENTS.md`.
- Symlinks were not used because tool and hosting support can vary.

## Candidate Change: Intake Before Issue Creation

For vague or underspecified prompts, agents should pause before creating an implementation issue and perform a short intake pass:

- Restate the likely goal in concrete terms.
- Identify missing requirements, constraints, acceptance criteria, and non-goals.
- Ask targeted clarifying questions when missing information could materially change the solution.
- Only create an implementation-ready issue once the prompt has enough detail to plan responsibly.
- Ask only the questions needed to remove meaningful ambiguity.
- Explore the repo, docs, tests, and issue records before asking questions that can be answered locally.
- Ask one question at a time for complex planning and provide a recommended answer when useful.
- Keep simple clarification to a few short questions.
- Flag vague terms and propose precise wording.

If the user is only brainstorming or explicitly asks to explore, the agent may create an `idea` issue or update an existing one, but should not treat it as implementation-ready.

## Candidate Change: Related Work Under Active Issue

Avoid creating unnecessary issues for asks that are aligned with active work.

Chosen approach:

- Continue under the active issue for clarifications, refinements, tangentially related asks, documentation, verification, or handoff work tied to the current goal.
- Update `issue.md` and `plan.md` when the related ask changes requirements or approach.
- Record the work in `session-log.md`.
- Create a new issue only when the ask is materially separate, independently reviewable, changes ownership or priority, or makes the active issue too broad.

## Candidate Change: Durable Issue Quality

Improve issue quality so work remains useful across refactors and handoffs.

Chosen approach:

- Issues should describe behavior, system capability, or workflow outcomes rather than implementation details.
- Bug issues should capture expected behavior, actual behavior, and reproduction or validation steps.
- Acceptance criteria should be testable.
- Non-goals should be captured when they prevent churn.
- Work breakdown should prefer independently reviewable vertical slices over horizontal layer-only tasks.
- QA should validate behavior through public interfaces and user-visible outcomes.

## Candidate Change: Shared Agent Guidance

Reduce drift by making one canonical source for shared workflow instructions and avoiding checked-in tool-specific files unless they are actively used.

Chosen approach:

- `AGENTS.md` is the canonical shared source.
- `AI-WORKFLOW.md` and `AI-README.md` are removed because their contents moved to `AGENTS.md`.
- `CLAUDE.md` remains as a thin Claude-specific adapter.
- `.github/copilot-instructions.md`, `.cursorrules`, and `.windsurfrules` are removed because they add noise when unused.
- `README.md` documents how projects can add tool-specific files as thin pointers to `AGENTS.md` when needed.
- `README.md` contains the detailed optional command reference for human users.
- General optional-agent guidance lives in `README.md`, not `AGENTS.md`, to keep agent context focused.
- `AGENTS.md` keeps only the command behavior rule: use slash commands when available, otherwise update `.issues/` manually.
- `AGENTS.md` contains target-project details placeholders instead of starter repository structure.
- `README.md` documents this starter repository's structure and customization guidance for existing target-project `AGENTS.md` files.
- The `AGENTS.md` starter-maintenance section is explicitly marked for removal after copying to another project.
- `.gitlab/duo/AGENTS.md` is removed because GitLab Duo uses project-level `AGENTS.md`.
- Symlinks are avoided as the default because some tools or web UIs may not resolve them consistently.

## Candidate Change: Single Session Log

Use one append-only `session-log.md` per issue instead of creating a separate file for every work session.

Chosen approach:

- New issues use `session-log.md` for all per-session progress records.
- `/issue session <id>` appends the next `# Session N` entry to `session-log.md`.
- `summary.md` remains the final verified completion summary.
- Existing starter issues use `session-log.md` directly.

## Candidate Change: QA Instructions at Review

Require a `qa-instructions.md` file when implementation is complete and an issue moves to `review`.

Chosen approach:

- `qa-instructions.md` is a first-class issue artifact.
- Agents create or update it before setting status to `review`.
- The file includes what changed, preconditions, validation steps, acceptance criteria, regression checks, and notes.
- Human verification uses `qa-instructions.md`; final verified completion still uses `summary.md`.

## Candidate Change: Ambiguity Reduction

Clarify rules that agents may interpret inconsistently under pressure.

Chosen approach:

- Define actionable work with concrete examples.
- Clarify simple versus complex requests for intake behavior.
- Add compact decision rules for answering directly, creating `idea` / `backlog` issues, moving to `ready`, and starting `in-progress`.
- Clarify that one session-log entry can cover multiple related edits in the same uninterrupted session.
- Keep the full session-log template in `.issues/README.md` and keep `AGENTS.md` to a shorter checklist.
- Define external verification before `done` as user confirmation, human QA, CI accepted by the user, or another explicit review signal.
- Rename starter-maintenance guidance to make removal after copying harder to miss.
- Make `Decision rules` the single canonical spot for status selection; remove duplicate restatements in Workflow Steps 1 and 2 and the brainstorming note.
- Promote session-log entry timing into Step 4 top-level so the "append before handoff, addend only mid-session" rule applies universally rather than living inside the related-work subsection.
- Collapse the redundant Red Flags bullets about `done` verification into one.
- Drop the Core Workflow Principle audit-trail list since Steps 5 and 6 and the folder-structure section already cover the same ground.

## Deferred Candidates

These were considered but not added to `AGENTS.md` in this iteration to keep the default workflow lean:

- Add a lightweight decision log pattern only if future workflow/model changes become hard to reconstruct from issue plans and session logs.
- Improve index generation expectations only if manual `.issues/index.md` updates become inconsistent.

## Next Steps

1. Human reviewer follows `qa-instructions.md`.
2. If accepted, move the issue from `review` to `done` and create `summary.md`.
3. If changes are requested, move back to `in-progress`, update the plan, and append a new session-log entry.
