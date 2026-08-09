# LMS Tasks (Agent B - Codex)

### LMS-001: Course authoring API - courses, sections, units, components
- **Status**: [ ] backlog
- **Priority**: P0
- **Owner**: Agent B
- **Depends on**: DB-001
- **Scope**: backend/app/api/v1/lms/authoring.py
- **Acceptance**: CRUD for course -> section -> unit -> component hierarchy.

### LMS-002: Activity engine API - activity types and instances
- **Status**: [ ] backlog
- **Priority**: P0
- **Owner**: Agent B
- **Depends on**: LMS-001
- **Scope**: backend/app/api/v1/lms/activities.py
- **Acceptance**: Plug-in activity types; instance CRUD; config stored as JSON.

### LMS-003: Quiz engine API - question bank, quiz instances, attempts
- **Status**: [ ] backlog
- **Priority**: P0
- **Owner**: Agent B
- **Depends on**: LMS-002
- **Scope**: backend/app/api/v1/lms/quizzes.py
- **Acceptance**: Create questions, build quizzes, submit attempts, auto-grade objective items.

### LMS-004: Assignment activity API - uploads, grading, feedback
- **Status**: [ ] backlog
- **Priority**: P0
- **Owner**: Agent B
- **Depends on**: LMS-002
- **Scope**: backend/app/api/v1/lms/assignments.py
- **Acceptance**: Submit files, teacher grades, feedback, late-submission rules.

### LMS-005: Gradebook API - categories, items, aggregation
- **Status**: [ ] backlog
- **Priority**: P0
- **Owner**: Agent B
- **Depends on**: LMS-003
- **Scope**: backend/app/api/v1/lms/gradebook.py
- **Acceptance**: Grade categories/items, weighted aggregation, grade export.
