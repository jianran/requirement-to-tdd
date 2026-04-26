# Complex feature playbook

Use this reference when a requirement spans multiple modules, boundaries, or delivery steps.

## 1. Recognize a complex feature

Treat the feature as complex when it includes one or more of these:

- multiple user-visible behaviors bundled together
- changes across API, domain, storage, and UI layers
- asynchronous jobs, events, retries, or background processing
- schema changes, migrations, or compatibility concerns
- integrations with third-party systems
- rollout, permission, or feature-flag constraints

## 2. Build a lightweight feature frame

Capture only what is needed:

- **Outcome** — what becomes true for the user or system
- **Core invariants** — what must always remain true
- **Boundaries** — APIs, queues, databases, files, services, or UI seams
- **Risks** — where the feature is likely to break
- **Non-goals** — what this change explicitly does not include

If the feature frame is unclear, do not rush into implementation.

## 3. Slice before coding

Prefer slices that are:

- vertically valuable
- independently testable
- low-coupling where possible
- ordered by risk and dependency

Good slice examples:

- accept and validate input
- persist the new state safely
- expose retrieval or read behavior
- trigger downstream side effects
- surface the final user-visible behavior

Bad slice examples:

- "backend first"
- "database changes"
- "refactor models"

Those are tasks, not behavior slices.

## 4. Map each slice to tests

Use a small test portfolio for each slice:

- **unit tests** for rules and transformations
- **integration tests** for persistence or orchestration boundaries
- **contract tests** for external interfaces
- **end-to-end tests** only for the minimum critical path

Do not try to prove every detail with end-to-end tests.

## 5. Sequence implementation

A practical order is usually:

1. protect invariants
2. add the first thin failing test for the highest-value slice
3. implement the smallest passing change
4. extend to the next slice
5. add boundary and regression coverage

## 6. Report progress clearly

For complex features, summarize in this shape:

```text
Feature outcome
Known assumptions / blockers
Slices
Coverage by slice
What is implemented now
What remains
```

## 7. Keep it adoptable

- avoid creating a huge upfront test matrix unless the feature truly needs it
- avoid forcing every project into the same architecture
- prefer terminology already used by the repository
- scale the rigor to the cost of failure and the complexity of the feature
