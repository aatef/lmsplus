# Platform + Frontend Tasks (Agent C - opencode)

### PLT-001: Backend skeleton - FastAPI app, config, health check
- **Status**: [ ] todo
- **Priority**: P0
- **Owner**: Agent C
- **Depends on**: none
- **Scope**: backend/app/main.py, backend/app/core/config.py
- **Acceptance**: App boots, /health returns ok, OpenAPI docs served.

### PLT-002: JWT validation dependency - Keycloak JWKS verify
- **Status**: [ ] todo
- **Priority**: P0
- **Owner**: Agent C
- **Depends on**: DB-001 (Keycloak realm), PLT-001
- **Scope**: backend/app/core/security.py
- **Acceptance**: Bearer JWT verified against Keycloak JWKS; realm roles parsed; protected endpoint rejects bad tokens.

### PLT-003: RBAC dependencies - require_roles / require_permission
- **Status**: [ ] todo
- **Priority**: P0
- **Owner**: Agent C
- **Depends on**: PLT-002
- **Scope**: backend/app/core/deps.py
- **Acceptance**: Endpoints enforce context roles/permissions; 403 on insufficient access.

### PLT-004: Enrollment + groups API
- **Status**: [ ] backlog
- **Priority**: P0
- **Owner**: Agent C
- **Depends on**: PLT-003
- **Scope**: backend/app/api/v1/platform/enrollment.py
- **Acceptance**: Enroll users in courses, manage course groups, list enrollments.

### PLT-005: Messaging + notifications API
- **Status**: [ ] backlog
- **Priority**: P1
- **Owner**: Agent C
- **Depends on**: PLT-003
- **Scope**: backend/app/api/v1/platform/messaging.py
- **Acceptance**: Private messages, in-app notifications, email via Celery.

### PLT-006: Calendar API
- **Status**: [ ] backlog
- **Priority**: P1
- **Owner**: Agent C
- **Depends on**: PLT-003
- **Scope**: backend/app/api/v1/platform/calendar.py
- **Acceptance**: Institution/course/personal events CRUD.

### FE-001: Admin dashboard skeleton - React + Tailwind + auth flow
- **Status**: [ ] todo
- **Priority**: P0
- **Owner**: Agent C
- **Depends on**: PLT-002
- **Scope**: admin/**
- **Acceptance**: App boots, Keycloak login redirect works, protected routes render, Tailwind configured.

### FE-002: Public site skeleton - React + Tailwind + auth flow
- **Status**: [ ] todo
- **Priority**: P0
- **Owner**: Agent C
- **Depends on**: PLT-002
- **Scope**: frontend/**
- **Acceptance**: App boots, Keycloak login redirect works, protected routes render, Tailwind configured.
