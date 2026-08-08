# AGENTS.md - Shared Agent Instructions

Instructions for agent harnesses working on **LMS Plus SIS**. Applies to OpenAI Codex CLI, opencode, and PI Coder (local Devstral). Claude Code loads this file via `CLAUDE.md`.

## Project

Unified **Learning Management System (LMS)** and **School Information System (SIS)** consolidating features from Moodle, OpenEduCat, and Open edX.

Read `docs/README.md` first. Key docs:

- `docs/01-vision-and-goals.md` - product vision and scope
- `docs/02-feature-matrix.md` - consolidated feature inventory with priorities
- `docs/03-architecture.md` - tech stack and module layout
- `docs/04-database-schema.md` - consolidated MySQL schema design
- `docs/05-roadmap.md` - phased delivery plan
- `docs/06-agent-harness-plan.md` - your branch, workstream, and coordination rules

## Tech Stack

- **Backend**: Python 3.11+ / FastAPI, SQLAlchemy 2.0 + Alembic, MySQL 8 (consolidated app DB)
- **Identity / SSO**: Keycloak (OIDC); backend validates JWT via JWKS
- **Frontend**: React 18 + Tailwind CSS - two apps: `admin/` (dashboard) and `frontend/` (public learner portal)
- **Background jobs**: Celery + Redis
- REST API (`/api/v1/...`) consumed by both React apps

## Roles / Workstream Ownership

You are assigned ONE workstream. **Edit only files in your domain.**

| Agent | Workstream | Owns |
|-------|-----------|------|
| Agent A (Claude) | SIS core | `backend/app/api/v1/sis/*`, `backend/app/services/sis/*` |
| Agent B (Codex) | LMS core | `backend/app/api/v1/lms/*`, `backend/app/services/lms/*` |
| Agent C (opencode) | Platform + Frontend | `backend/app/api/v1/platform/*`, `backend/app/core/*`, `admin/**`, `frontend/**` |
| Agent D (PI Coder) | Database + Identity | `db/**`, `backend/alembic/**`, `backend/app/db/*`, `keycloak/**` |

Read-only for all agents (human-owned): `docs/`, `tasks/`, `AGENTS.md`, `CLAUDE.md`, `backend/pyproject.toml`, `admin/package.json`, `frontend/package.json`.

If a task requires touching a file outside your domain, do NOT edit it - raise it with the orchestrator.

## Git Workflow

- Branch from `main`: `YYMMDD-feat-<area>` (e.g., `260807-feat-sis-core`).
- Pull/rebase `main` before starting; never force-push shared branches.
- Commit messages: conventional style (`feat:`, `fix:`, `chore:`, `docs:`).
- Finish every task with a PR (push with `-o merge_request.create`), including title + description of changes.

## Code Standards

- Follow existing code style; no debug `console.log` / `print()` left behind.
- No hardcoded secrets; use `.env` / env vars with `.env.example` placeholders.
- Include Alembic migrations for any schema change; keep consolidated schema in `db/consolidated/schema.sql` in sync (Agent D).
- Sanitize/validate all inputs; enforce RBAC via FastAPI dependencies (`require_roles` / `require_permission`).
- Authentication: validate Keycloak JWT on every request; never trust client-supplied identity.
- `utf8mb4`, `InnoDB` for all tables; follow naming conventions in docs/04.

## Definition of Done

- Migrations + seeds included where relevant
- Lint and tests pass (run available test suite)
- Branch pushed, PR opened, no out-of-scope file changes
