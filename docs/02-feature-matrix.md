# 2. Feature Matrix

Consolidated inventory of features from **Moodle**, **OpenEduCat**, and **Open edX**, mapped into unified modules. Priority: **P0** (must have, MVP), **P1** (should have, phase 2), **P2** (nice to have, phase 3).

## 2.1 SIS Features (primarily OpenEduCat)

| Feature | Description | Source | Priority |
|---------|-------------|--------|----------|
| Student Admissions | Application, eligibility, offer letter, enrollment | OpenEduCat | P0 |
| Student Records | Profiles, guardian info, documents, medical info | OpenEduCat | P0 |
| Academic Structure | Institution -> Campus -> Department -> Program -> Batch -> Class -> Section | OpenEduCat | P0 |
| Faculty Records | Profile, qualification, contracts, departments | OpenEduCat | P0 |
| Attendance | Daily/timetable-based attendance, leaves, reports | OpenEduCat | P0 |
| Timetable | Class schedules, room allocation, conflict checks | OpenEduCat | P0 |
| Fees Management | Fee structures, invoices, payments, installments, receipts, refunds | OpenEduCat | P0 |
| Library | Catalog, circulation (issue/return), fines, memberships | OpenEduCat | P1 |
| Hostel | Rooms, allocations, billing | OpenEduCat | P1 |
| Transport | Routes, vehicles, stops, student assignment | OpenEduCat | P1 |
| Events | Institutional events, registrations | OpenEduCat | P1 |
| Alumni | Alumni records, engagement | OpenEduCat | P2 |
| HR / Payroll | Staff payroll, leaves, appraisals | OpenEduCat | P2 |

## 2.2 LMS Features (primarily Moodle + Open edX)

| Feature | Description | Source | Priority |
|---------|-------------|--------|----------|
| Course Authoring | Courses -> sections -> activities; Studio-style authoring UI | Open edX | P0 |
| Activity Engine | Pluggable activity types (assignment, quiz, lesson, page, SCORM, H5P) | Moodle | P0 |
| Quiz Engine | Question bank, multiple question types, timed exams, randomization | Moodle | P0 |
| Assignments | Uploads, grading, feedback, late submission rules | Moodle | P0 |
| Discussion Forums | Threads, replies, moderation, ratings | Moodle | P0 |
| Lesson / SCORM | Branching lessons, SCORM 1.2/2004 package playback | Moodle | P1 |
| Video Delivery | Video components with transcripts, captions, bookmarks | Open edX | P1 |
| Gradebook | Aggregated grades, weighted categories, rounding, exports | Moodle | P0 |
| Competencies | Competency frameworks, learning plans, mapping to activities | Moodle | P1 |
| Badges | Award rules, course-level and site-level badges | Moodle | P1 |
| Certificates | Course completion certificates, templates, issuance | Open edX / Moodle | P1 |
| XBlocks / Widgets | Extensible content components | Open edX | P2 |
| Proctored Exams | Proctoring integration for high-stakes exams | Open edX | P2 |

## 2.3 Platform Features (cross-cutting)

| Feature | Description | Source | Priority |
|---------|-------------|--------|----------|
| Roles & Permissions | Context-based roles (site, course, class) | Moodle | P0 |
| Enrollment | Manual, self, cohort-based, course groups | Moodle | P0 |
| Groups & Cohorts | Grouping learners for differentiated delivery | Moodle | P0 |
| Messaging | Private messages, notifications, email digests | Moodle | P0 |
| Calendar | Institution + course + personal calendars | Moodle / OpenEduCat | P0 |
| Reports & Analytics | Dashboards, learner progress, institutional analytics | All | P0 |
| Audit Logs | Track sensitive data changes | OpenEduCat | P1 |
| Multi-Tenancy | Multiple institutions/campuses in one install | OpenEduCat | P1 |
| Web Services / API | REST API for integrations (LTI, SSO, mobile) | Moodle / Open edX | P1 |
| Mobile Responsive | Responsive web UI | All | P1 |

## 2.4 Coverage Summary

| Category | Moodle | OpenEduCat | Open edX | Count |
|----------|--------|------------|----------|-------|
| SIS | - | 13 | - | 13 |
| LMS | 8 | - | 6 | 14 |
| Platform | 8 | 3 | 2 | 13 |
| **Total unique features** | | | | **40** |

## 2.5 Feature Selection Rules

- When a feature exists in multiple sources, adopt the **strongest implementation** and note the source.
- Example: grades aggregation from Moodle; fee ledger from OpenEduCat; course structuring from Open edX.
- Every P0 feature must have a corresponding schema section in the consolidated DB design (doc 04).
