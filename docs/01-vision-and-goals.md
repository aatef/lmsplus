# 1. Vision and Goals

## 1.1 Product Vision

Build a single, unified education platform that serves as both a **Learning Management System (LMS)** and a **School Information System (SIS)**. It brings together the best of three established open-source products:

| Product | Type | Primary Strengths |
|---------|------|-------------------|
| Moodle | LMS | Activities, quizzes, grading, competencies, badges, forums, plugins |
| OpenEduCat | SIS/ERP | Admissions, fees, attendance, library, hostel, transport, finance |
| Open edX | LMS/MOOC | Course authoring (Studio), XBlocks, video delivery, scalable learning |

Instead of deploying three separate products and integrating them, we consolidate all features into **one 3-tier application**: a FastAPI backend backed by one MySQL database, with Keycloak single sign-on and two React frontends (admin dashboard + public learner portal).

## 1.2 Goals

1. **Single sign-on** - Keycloak (OIDC) provides one identity for student, learner, teacher, staff, admin, and parent across all apps.
2. **Unified data model** - a student record ties together academic, financial, administrative, and learning data in one place.
3. **Full academic lifecycle** - admission -> enrollment -> attendance -> learning -> assessment -> grading -> certification -> alumni.
4. **Modern course authoring** - adopt Open edX's structured course authoring (courses > sections > activities) combined with Moodle's rich activity types.
5. **ERP-grade operations** - fees, payroll, library, hostel, transport managed natively, inspired by OpenEduCat.
6. **One MySQL database** - a consolidated app schema with clean foreign keys, migrations, and backups (Keycloak holds identity data in a separate store).

## 1.3 Target Users

| Role | Needs |
|------|-------|
| Student / Learner | Enroll in courses, complete activities, view grades, pay fees, access library |
| Parent | View child progress, fees, attendance, communication |
| Teacher / Faculty | Author courses, grade work, take attendance, manage classes |
| Administrator / Staff | Admissions, scheduling, reports, finance, hostel/transport admin |
| Institution Owner | Multi-campus management, dashboards, analytics |

## 1.4 High-Level Feature Scope (Consolidated)

- **SIS**: admissions, student records, faculty records, attendance, timetable, fee management, library, hostel, transport, events, alumni.
- **LMS**: course authoring, activities (assignments, quizzes, lessons, forums, SCORM, H5P), grading, competencies, badges, certificates, analytics.
- **Platform**: roles/permissions, messaging, notifications, calendar, reports, audit logs, multi-tenant support.

## 1.5 Non-Goals (Phase 1)

- Full Moodle plugin ecosystem compatibility (we build native modules instead).
- Real-time video conferencing (integrate via external providers).
- Migration tooling for existing Moodle/OpenEduCat/Open edX instances (addressed later).
- Mobile native apps (responsive web app first).

## 1.6 Success Metrics

- 100% feature coverage across the consolidated feature matrix (see doc 02).
- Single MySQL app schema with no data duplication between LMS and SIS records; identity isolated in Keycloak.
- < 500ms p99 API latency for common operations.
- Role-based access enforced at every endpoint (Keycloak realm roles + app context permissions).
