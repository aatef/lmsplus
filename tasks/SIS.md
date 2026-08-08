# SIS Tasks (Agent A - Claude Code)

### SIS-001: Academic structure API - institutions, campuses, departments, programs, batches, classes, sections
- **Status**: [ ] todo
- **Priority**: P0
- **Owner**: Agent A
- **Depends on**: DB-001
- **Scope**: backend/app/api/v1/sis/academic_structure.py
- **Acceptance**: CRUD for the full academic hierarchy; RBAC enforced; validation via Pydantic.

### SIS-002: Admissions API - application, eligibility, offer
- **Status**: [ ] backlog
- **Priority**: P0
- **Owner**: Agent A
- **Depends on**: SIS-001
- **Scope**: backend/app/api/v1/sis/admissions.py
- **Acceptance**: Submit application, validate eligibility, issue offer, link to student record.

### SIS-003: Student records API - profile, guardians, documents
- **Status**: [ ] backlog
- **Priority**: P0
- **Owner**: Agent A
- **Depends on**: SIS-001
- **Scope**: backend/app/api/v1/sis/students.py
- **Acceptance**: CRUD student profile + guardians + document uploads; linked to Keycloak user.

### SIS-004: Faculty records API - profile, contracts
- **Status**: [ ] backlog
- **Priority**: P0
- **Owner**: Agent A
- **Depends on**: SIS-001
- **Scope**: backend/app/api/v1/sis/faculty.py
- **Acceptance**: CRUD faculty profile + contract status.

### SIS-005: Attendance API - settings, daily entry, reports
- **Status**: [ ] backlog
- **Priority**: P0
- **Owner**: Agent A
- **Depends on**: SIS-001
- **Scope**: backend/app/api/v1/sis/attendance.py
- **Acceptance**: Mark attendance per class/date, view reports, holiday handling.

### SIS-006: Timetable API - slots, schedule, conflict checks
- **Status**: [ ] backlog
- **Priority**: P0
- **Owner**: Agent A
- **Depends on**: SIS-001
- **Scope**: backend/app/api/v1/sis/timetable.py
- **Acceptance**: Define slots, assign classes, detect conflicts.

### SIS-007: Fees API - structures, invoices, payments, ledger
- **Status**: [ ] backlog
- **Priority**: P0
- **Owner**: Agent A
- **Depends on**: SIS-003
- **Scope**: backend/app/api/v1/sis/fees.py
- **Acceptance**: Fee structure per program, generate invoices, record payments, ledger audit trail.
