# Database + Identity Tasks (Agent D - PI Coder / Devstral)

## Sprint 1 - Backend Foundation (Phase 0)

### DB-002: Keycloak realm setup - realm, clients, realm roles
- **Status**: [ ] todo
- **Priority**: P0
- **Owner**: Agent D
- **Depends on**: PLT-007 (docker-compose Keycloak)
- **Scope**: keycloak/realm.json (realm-export)
- **Acceptance**: Realm import defines admin/staff/teacher/student/parent roles and dashboard + public-site clients.

### DB-001: Consolidated schema - db/consolidated/schema.sql
- **Status**: [ ] todo
- **Priority**: P0
- **Owner**: Agent D
- **Depends on**: none
- **Scope**: db/consolidated/schema.sql
- **Acceptance**: Executable MySQL 8 script covering core domain groups from docs/04; utf8mb4 + InnoDB; FKs correct.

### DB-003: Alembic baseline - initial migration from schema
- **Status**: [ ] todo
- **Priority**: P0
- **Owner**: Agent D
- **Depends on**: DB-001, PLT-001
- **Scope**: backend/alembic/**
- **Acceptance**: `alembic upgrade head` builds DB matching consolidated schema.

### DB-004: SQLAlchemy models - core identity + academic tables
- **Status**: [ ] todo
- **Priority**: P0
- **Owner**: Agent D
- **Depends on**: DB-003
- **Scope**: backend/app/db/models.py
- **Acceptance**: Models for users, roles, permissions, contexts, academic structure; relationships mapped.

### DB-005: Seeders - base roles, permissions, activity types, demo institution
- **Status**: [ ] backlog
- **Priority**: P1
- **Owner**: Agent D
- **Depends on**: DB-004
- **Scope**: backend/app/db/seed.py
- **Acceptance**: Idempotent seed script populates baseline data.

### DB-006: Source DB scripts preserved under db/source/
- **Status**: [ ] backlog
- **Priority**: P1
- **Owner**: Agent D
- **Depends on**: none
- **Scope**: db/source/openeducat.sql, db/source/openedx.sql, db/source/moodle.sql
- **Acceptance**: User-provided reference scripts placed; noted as reference-only.
