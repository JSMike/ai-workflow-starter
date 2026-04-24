# ISSUE-3: Explore SQLite and MCP-backed issue storage

<!-- Metadata -->
| Field        | Value        |
|--------------|--------------|
| Status       | backlog      |
| Owner        | TBD          |
| Complexity   | high         |
| Created      | 2026-04-24   |
| Source       | readme-future-consideration |
| External     |              |
| Blocks       |              |
| Blocked-by   |              |
| Priority     | medium       |

## Summary

Evaluate adding local SQLite database storage and MCP support for issue records instead of relying only on `.issues/` markdown files.

## Context

README future consideration:

"Add local SQLite database and MCP support to store issues in a DB instead of `.issues/`."

## Requirements Readiness

- [ ] Goal is clear
- [ ] Constraints are documented
- [ ] Acceptance criteria are testable
- [ ] Open questions are resolved or captured

## Acceptance Criteria

- [ ] Define whether SQLite/MCP replaces `.issues/` or acts as an optional synchronization layer.
- [ ] Identify the required schema and migration path.
- [ ] Document how agents would read/write issue context through MCP.
- [ ] Define fallback behavior when MCP or SQLite is unavailable.

## References

- Related files: `AGENTS.md`, `.issues/`, `README.md`
- Related issues:
