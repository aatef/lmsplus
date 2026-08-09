# Queue Service Tasks (Agent E - Queue Infra)

> These tasks build the worker-pool infrastructure described in `docs/08-worker-pool.md`. The queue service and worker client are a new infrastructure workstream (area code `QUE`). Owned by Agent E (or any dedicated infra agent).

## Sprint 1.5 - Worker Pool (Parallel to Sprint 1)

### QUE-001: Task queue service - FastAPI + Redis skeleton
- **Status**: [ ] todo
- **Priority**: P0
- **Owner**: Agent E
- **Depends on**: none
- **Scope**: worker/queue_service/main.py
- **Acceptance**: FastAPI app boots; Redis connected; `/health` returns ok; Redis key namespace `lmsplus:tasks:*`.

### QUE-002: Atomic claim endpoint - POST /tasks/claim
- **Status**: [ ] todo
- **Priority**: P0
- **Owner**: Agent E
- **Depends on**: QUE-001
- **Scope**: worker/queue_service/routes/claim.py
- **Acceptance**: Two concurrent workers requesting the same area cannot both claim the same task; CAS/lease applied; dependency check (all `depends_on` done) enforced.

### QUE-003: Lease + heartbeat - claim TTL, POST /tasks/{id}/heartbeat, auto-release
- **Status**: [ ] todo
- **Priority**: P0
- **Owner**: Agent E
- **Depends on**: QUE-002
- **Scope**: worker/queue_service/services/lease.py
- **Acceptance**: Claim sets 10-min lease; heartbeat extends; expired lease auto-reopens task.

### QUE-004: Complete/fail endpoints - POST /tasks/{id}/complete, /fail
- **Status**: [ ] todo
- **Priority**: P0
- **Owner**: Agent E
- **Depends on**: QUE-002
- **Scope**: worker/queue_service/routes/status.py
- **Acceptance**: Worker marks task done with PR url, or failed with reason; failed tasks not auto-reclaimed.

### QUE-005: Task sync from git registry - POST /tasks/sync
- **Status**: [ ] backlog
- **Priority**: P1
- **Owner**: Agent E
- **Depends on**: QUE-001
- **Scope**: worker/queue_service/services/sync.py
- **Acceptance**: Parses `tasks/*.md` and upserts tasks into Redis; human-authored registry stays source of truth.

### QUE-006: Worker client - claim, branch, run harness, push PR, complete
- **Status**: [ ] backlog
- **Priority**: P0
- **Owner**: Agent E
- **Depends on**: QUE-002, QUE-004
- **Scope**: worker/worker.py, worker/worker.example.yaml
- **Acceptance**: Headless worker loop pulls tasks, checks out branch, invokes configured harness, pushes PR, reports status; survives harness failures.

### QUE-007: Node provisioning docs - one-liner join
- **Status**: [ ] backlog
- **Priority**: P1
- **Owner**: Agent E
- **Depends on**: QUE-006
- **Scope**: docs/09-node-provisioning.md
- **Acceptance**: A new machine can join the pool following documented steps in under 5 minutes.
