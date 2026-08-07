# CLAUDE.md - Claude Code Instructions

This file imports the shared instructions. Claude Code loads `@AGENTS.md` for the full project rules, workstream ownership, git workflow, and code standards.

@AGENTS.md

## Claude-Specific Notes

- You are **Agent A (Claude Code)** in the multi-agent harness setup (see `docs/06-agent-harness-plan.md`).
- Your workstream: **SIS core** - `src/Sis/*`, `resources/js/sis/*`.
- Your branch: `260807-feat-sis-core`.
- Do not edit files owned by other agents (Agent B: `src/Lms/*`, Agent C: `src/Platform/*`, Agent D: `db/**`).
- Use `CLAUDE.md` conventions: stay concise, propose changes before large refactors, and run tests/lint before finishing.
