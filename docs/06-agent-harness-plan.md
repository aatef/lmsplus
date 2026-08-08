# 6. Multi-Agent Harness Plan

Four agent harnesses work on the **same project** in parallel. Each harness has its own branch, its own workstream, and shares the same repo, docs, and conventions.

## 6.1 Harness Inventory

| # | Harness | Config File | Model | Workstream |
|---|---------|-------------|-------|------------|
| A | Claude Code | `CLAUDE.md` | Claude (cloud) | SIS core (backend) |
| B | OpenAI Codex CLI | `AGENTS.md` | GPT (cloud) | LMS core (backend) |
| C | opencode | `AGENTS.md` + `opencode.json` | Cloud LLM | Platform + frontend apps |
| D | PI Coder | `AGENTS.md` | Devstral Small 2 (local) | Database + identity (Keycloak) |

- `AGENTS.md` is the **shared source of truth** for Codex, opencode, and PI Coder.
- `CLAUDE.md` imports `AGENTS.md` so Claude Code inherits identical rules, plus Claude-specific notes.

## 6.2 Workstream Assignments

| Agent | Branch | Scope (from docs/02 feature matrix) |
|-------|--------|--------------------------------------|
| A (Claude) | `260807-feat-sis-core` | Backend SIS: academic structure, admissions, student records, faculty, attendance, timetable, fees |
| B (Codex) | `260807-feat-lms-core` | Backend LMS: course authoring, activity engine, quizzes, assignments, gradebook |
| C (opencode) | `260807-feat-platform` | Backend platform (RBAC, enrollment, messaging, calendar) + **both React apps** (`admin/` dashboard, `frontend/` public site) |
| D (PI Coder) | `260807-feat-db-schema` | `db/consolidated/schema.sql`, Alembic migrations, seeders, Keycloak realm setup, ER mappings from docs/04 |

## 6.3 Git Workflow (no conflicts)

1. All agents branch from the **same base** (`main`), using the branch naming convention `YYMMDD-feat-<area>`.
2. **No agent touches another agent's folder.** Folder ownership:
   - Agent A: `backend/app/api/v1/sis/*`, `backend/app/services/sis/*`
   - Agent B: `backend/app/api/v1/lms/*`, `backend/app/services/lms/*`
   - Agent C: `backend/app/api/v1/platform/*`, `admin/**` (dashboard), `frontend/**` (public site), `backend/app/core/*` (auth/RBAC deps)
   - Agent D: `db/**`, `backend/alembic/**`, `backend/app/db/*`, `keycloak/**`
3. Agents `pull origin main` before starting and `rebase` on merge to keep history linear.
4. **Rule of thumb**: if a file doesn't belong to your workstream, you do not edit it; open an issue/mention instead.
5. Every change is merged via **PR** with review, never force-pushed to shared branches.
6. `docs/`, `AGENTS.md`, `CLAUDE.md` are read-only for all agents (owned by the human orchestrator).

## 6.4 Shared Files That May Conflict

| File | Why it conflicts | Resolution |
|------|------------------|------------|
| `backend/pyproject.toml` / `requirements.txt` | Dependencies added by multiple agents | Single "dependency owner" = Agent C; others request via issue |
| `backend/app/main.py` / `router.py` | Router registration | Split routers per domain: `api/v1/sis/router.py`, `api/v1/lms/router.py`, `api/v1/platform/router.py` |
| `admin/package.json` / `frontend/package.json` | Frontend deps | Owned by Agent C only |
| `AGENTS.md` / `CLAUDE.md` | Everyone reads them | Only the human/orchestrator edits |

## 6.5 Local LLM Considerations (Agent D - Devstral Small 2)

- Devstral Small 2 (7B-24B class, local) has a **smaller context window**; keep `AGENTS.md` lean and point to docs instead of inlining the full schema.
- Prefer smaller, single-file tasks; long multi-file diffs are error-prone.
- Keep prompt/instructions deterministic: explicit file paths, explicit acceptance criteria.
- Use the same `AGENTS.md` as Codex/opencode; add a `docs/07-devstral-notes.md` if local-model guidance diverges.
- Agent D also owns Keycloak realm config (realm JSON, clients, realm roles) - keep this in small files, validated with `kcadm` locally.

## 6.6 Task Coordination Protocol

> Task tracking now lives in the **task registry** (`tasks/`, see `docs/07-task-management.md`). Agents pick up tasks by their area code; orchestrator owns the registry.

1. Orchestrator creates tasks per workstream in `tasks/` (e.g., `SIS.md`, `LMS.md`, `PLT.md`, `DB.md`).
2. Each agent picks up only its own area-coded tasks (`SIS-*`, `LMS-*`, `PLT-*`/`FE-*`, `DB-*`).
3. On branch merge, orchestrator runs full test suite + migration check before squashing to `main`.
4. Cross-cutting decisions (auth design, response envelope, table names) are decided once in docs and then **not changed** mid-sprint, to avoid two agents re-doing work.

## 6.7 Definition of Done (per agent)

- Code follows shared conventions (docs/03 architecture + code standards).
- Migrations included for any schema change; consolidated schema kept in sync.
- Tests pass; lint clean.
- Branch pushed; PR opened with `-o merge_request.title`/description.

## 6.8 Agent File Layout

```
/workspace
├── AGENTS.md              # Shared instructions (Codex, opencode, PI Coder)
├── CLAUDE.md              # Claude Code entry (imports AGENTS.md)
├── opencode.json          # opencode-specific settings (optional)
├── docs/                  # Planning docs (read-only to agents)
├── tasks/                 # Task registry (systematic task management)
├── backend/               # FastAPI app (Agents A/B/C shared, split by api/v1/*)
├── admin/                 # React admin dashboard (Agent C)
├── frontend/              # React public site / learner portal (Agent C)
├── db/                    # Agent D owns this
└── keycloak/              # Agent D owns this (realm config)
```
