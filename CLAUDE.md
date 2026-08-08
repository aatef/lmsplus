# CLAUDE.md - Claude Code Instructions

This file imports the shared instructions. Claude Code loads `@AGENTS.md` for the full project rules, workstream ownership, git workflow, and code standards.

@AGENTS.md

## Claude-Specific Notes

- You are **Agent A (Claude Code)** in the multi-agent harness setup (see `docs/06-agent-harness-plan.md`).
- Your workstream: **SIS core** - `backend/app/api/v1/sis/*`, `backend/app/services/sis/*`.
- Your branch: `260807-feat-sis-core`.
- Do not edit files owned by other agents (Agent B: `backend/app/api/v1/lms/*`, Agent C: `backend/app/api/v1/platform/*` + `dashboard/**` + `site/**`, Agent D: `db/**` + `backend/alembic/**` + `keycloak/**`).
- Use `CLAUDE.md` conventions: stay concise, propose changes before large refactors, and run tests/lint before finishing.
