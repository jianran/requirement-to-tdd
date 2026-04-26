# Requirement decomposition and test design

Use this reference when a requirement is vague, dense, or spans multiple behaviors.

## 1. Break the requirement into testable clauses

For each requirement, extract:

- **Actor / trigger** — who or what initiates the behavior
- **Input** — text, fields, events, commands, or state
- **Rule** — validation, transformation, storage, authorization, ordering, formatting, or side effect
- **Output / observable effect** — return value, persisted record, emitted event, rendered text, or state transition
- **Failure mode** — invalid input, duplicates, missing fields, unsupported states, conflicts, or timeouts

Treat each clause as a candidate test.

## 2. Choose the right test layer

- **Unit** — pure parsing, validation, mapping, deduplication, state transitions, formatting
- **Integration** — repository behavior, database persistence, serialization boundaries, service orchestration, messaging boundaries
- **Contract** — requests/responses or payload shape at an external boundary
- **End-to-end** — only when the requirement depends on the full user-visible flow

Start at the lowest layer that can prove the behavior.

## 3. Use this lightweight coverage map

```text
Requirement clause -> Planned test
Valid requirement text is parsed -> parses_valid_requirement_text
Malformed requirement text is rejected -> rejects_malformed_requirement_text
Duplicate titles are prevented -> rejects_duplicate_requirement_title
Stored requirements can be listed -> lists_saved_requirements
```

For complex work, extend it with slices:

```text
Slice A: accept new requirement payload
  - validates required fields
  - stores normalized value
Slice B: expose retrieval flow
  - lists saved requirements
  - preserves sort order
```

## 4. Common requirement categories to cover

### Parsing / ingestion

- valid structured input
- malformed or partial input
- whitespace / casing / delimiter variance
- unknown fields
- versioned or legacy payloads

### Validation

- required fields
- allowed values / ranges
- cross-field rules
- conflict handling
- invariant preservation

### Storage / repository behavior

- create
- read / list / filter
- update
- duplicate prevention
- idempotency
- migration or backfill effects

### State transitions / workflows

- allowed transition
- forbidden transition
- unchanged state no-op
- audit / timestamp / side-effect expectations
- retries / eventual consistency behavior when relevant

### External boundaries

- request / response contract
- serialization format
- third-party failure or timeout handling
- backward compatibility expectations

## 5. Ambiguity checklist

Ask or state an assumption when the requirement is unclear about:

- required vs optional fields
- duplicate semantics
- ordering / sorting expectations
- case sensitivity
- error shape or message expectations
- backward compatibility constraints
- migration behavior
- async timing or retry expectations

## 6. Completion bar

Before calling the task done, check:

- Every explicit requirement clause maps to at least one test.
- The chosen test layer is no broader than necessary.
- Negative cases exist where invalid behavior matters.
- Complex features are split into independently testable slices.
- The implementation diff does not exceed the scope of the requirement.
- Test results or a concrete blocker are reported.
