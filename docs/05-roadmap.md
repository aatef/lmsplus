# 5. Roadmap

Phased delivery plan for LMS Plus SIS.

## 5.1 Phase 0 - Foundation (Weeks 1-2)

**Goal**: Repo structure, tooling, consolidated schema baseline, identity foundation.

- [ ] Initialize backend skeleton (FastAPI + SQLAlchemy + Alembic)
- [ ] Initialize React apps (admin dashboard + public site) with Tailwind
- [ ] Create `db/source/` and place user-provided OpenEduCat, Open edX, Moodle scripts
- [ ] Author `db/consolidated/schema.sql` from doc 04
- [ ] Set up MySQL 8, Redis, object storage dev environment
- [ ] Stand up **Keycloak** (realm, clients, realm roles, JWT validation in FastAPI)
- [ ] RBAC skeleton (contexts, roles, permissions, user_roles)
- [ ] CI pipeline (lint, tests, migration check)
- **Exit criteria**: fresh install migrates consolidated schema; user logs in via Keycloak and calls a protected FastAPI endpoint.

## 5.2 Phase 1 - SIS Core (Weeks 3-6)

**Goal**: Administrative backbone - P0 SIS features.

- [ ] Academic structure (institution -> campus -> department -> program -> batch -> class -> section)
- [ ] Admissions + student records + guardians + documents
- [ ] Faculty records + contracts
- [ ] Attendance (settings, daily entry, reports)
- [ ] Timetable (slots, class schedule, conflict checks)
- [ ] Fees (structures, invoices, payments, receipts, ledger)
- [ ] Admin dashboard: SIS admin screens (students, attendance, fees)
- **Exit criteria**: end-to-end student lifecycle (admission -> enrollment -> attendance -> fees) works in the dashboard.

## 5.3 Phase 2 - LMS Core (Weeks 7-10)

**Goal**: Authoring and learning delivery - P0 LMS features.

- [ ] Course authoring (courses -> sections -> units -> components)
- [ ] Activity engine with assignment + quiz activity types
- [ ] Question bank + quiz engine
- [ ] Gradebook (categories, items, aggregation, exports)
- [ ] Course enrollment + groups
- [ ] Learner view (public site): enroll, study, submit, view grades
- **Exit criteria**: a teacher authors a course with a quiz, students enroll, complete, and get grades end-to-end.

## 5.4 Phase 3 - Collaboration & Completion (Weeks 11-13)

**Goal**: P1 LMS/platform features.

- [ ] Forums + discussion moderation
- [ ] Messaging + notifications (email/SMS)
- [ ] Calendar (institution/course/personal)
- [ ] Lesson/SCORM activity types
- [ ] Video components with transcripts/captions
- [ ] Competencies + learning plans
- [ ] Badges + certificates
- **Exit criteria**: full course experience with collaboration and completion credentials.

## 5.5 Phase 4 - Advanced SIS & Integrations (Weeks 14-17)

**Goal**: P1-P2 SIS and platform features.

- [ ] Library (catalog, circulation, fines)
- [ ] Hostel (rooms, allocations, billing)
- [ ] Transport (routes, stops, assignments)
- [ ] Events + registrations
- [ ] Reports builder + analytics dashboards
- [ ] REST API hardening + API tokens (Keycloak service accounts)
- [ ] LTI consumer/provider, external IdP federation, payment gateway
- **Exit criteria**: full P0-P1 feature coverage; external integrations work.

## 5.6 Phase 5 - Data Migration & Polish (Weeks 18-20)

**Goal**: Source-system migration tooling and hardening.

- [ ] Migration extractors: OpenEduCat -> consolidated
- [ ] Migration extractors: Open edX -> consolidated
- [ ] Migration extractors: Moodle -> consolidated
- [ ] Alumni + HR/payroll (P2)
- [ ] Mobile responsive hardening, accessibility
- [ ] Performance audit, security review, load testing
- **Exit criteria**: data from a sample Moodle/OpenEduCat/Open edX dump migrates losslessly.

## 5.7 Cross-Cutting Backlog

- Audit logs on all sensitive tables
- Multi-tenancy scoping (institution/campus)
- Backup/restore automation for MySQL
- Export/import (CSV, PDF, Excel) for all reports
- Localization (multi-language UI)
- Documentation + admin/user manuals
