# Task Registry

Systematic task tracking for all agent workstreams. Human-owned; agents do not edit these files.

See `docs/07-task-management.md` for the scheme.

## Task Index

| Area | File | Owner |
|------|------|-------|
| SIS | `SIS.md` | Agent A |
| LMS | `LMS.md` | Agent B |
| PLT / FE | `PLT.md` | Agent C |
| DB | `DB.md` | Agent D |
| QUE | `QUE.md` | Agent E (queue infra) |

## Worker Pool

Tasks are executed by a **pool of worker nodes** that autonomously pull and claim tasks (see `docs/08-worker-pool.md`). The queue service (FastAPI + Redis) provides atomic claiming; any machine can join as a worker at any time.

## Status Legend

`backlog` -> `todo` -> `in-progress` -> `review` -> `done`

## Current Sprint

### Sprint 1 - Backend Foundation (Phase 0)

Goal: boot the backend, stand up Keycloak SSO, and enforce RBAC at the API layer.

**Task list (ordered by dependency):**

| Task | Description | Owner | Depends on |
|------|-------------|-------|------------|
| PLT-007 | Dev env: docker-compose (MySQL, Keycloak, Redis) + .env.example | C | - |
| DB-002 | Keycloak realm: roles + dashboard/public-site clients | D | PLT-007 |
| DB-001 | Consolidated schema: `db/consolidated/schema.sql` | D | - |
| PLT-001 | Backend skeleton: FastAPI, config, /health | C | PLT-007 |
| DB-003 | Alembic baseline migration | D | DB-001, PLT-001 |
| PLT-002 | JWT validation vs Keycloak JWKS | C | DB-002, PLT-001 |
| DB-004 | SQLAlchemy models: identity + academic | D | DB-003 |
| PLT-003 | RBAC deps: require_roles / require_permission | C | PLT-002, DB-003 |
| PLT-009 | RBAC verification endpoints (/me, /roles) | C | PLT-003 |

**Sprint exit criteria:** a user logs in via Keycloak, calls a protected API with a JWT, and the API enforces realm roles and app-context permissions (403 on denial). See docs/05-roadmap.md Phase 0.

**Parallel lanes:** Agent C (PLT-001/002/003, PLT-007/009) and Agent D (DB-001/002/003/004) run in parallel; sync at PLT-003.

