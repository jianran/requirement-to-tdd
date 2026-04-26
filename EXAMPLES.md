# Examples

## Using this skill repository

This repo is a Claude Code skill repository for requirement-related development guidance. It is not a Python package.

### Add the skill to your project

Copy `CLAUDE.md` to the root of the target project, and use `skills/requirement-skill/SKILL.md` as your task-specific guidance.

### Example workflow for a small change

1. Search the codebase for requirement-related types and modules.
2. Normalize the requirement into explicit clauses, assumptions, and open questions.
3. Identify the existing class, service, validator, or handler that should own the behavior.
4. Map each requirement clause to a planned test.
5. Draft a failing test for the next behavior.
6. Implement only the code necessary to satisfy that test.

### Example workflow for a complex feature

1. Classify the feature as multi-step or cross-module.
2. Capture the outcome, invariants, boundaries, risks, and non-goals.
3. Slice the feature into thin vertical behaviors.
4. Map each slice to the smallest useful test mix.
5. Add failing tests for the first high-value slice.
6. Implement and verify slice by slice.

## Example test-first plan

For a new requirement ingestion feature:

- Requirement clause: valid requirement text with `Title`, `Description`, `Priority`, `Status`, and `Tags` is parsed.
  - Test: parse requirement text with all supported fields.
- Requirement clause: malformed requirement input is rejected.
  - Test: reject malformed requirement input.
- Requirement clause: duplicate requirement titles are prevented.
  - Test: prevent duplicate requirement titles.
- Requirement clause: saved requirements are retrievable.
  - Test: expose a list or retrieval API for requirements.

For a more complex feature that ingests, stores, and exposes requirements:

- Slice A: accept and validate the payload.
  - Tests: required fields, malformed input, normalization rules.
- Slice B: persist safely.
  - Tests: create record, prevent duplicates, preserve compatibility with existing records.
- Slice C: expose retrieval behavior.
  - Tests: list saved requirements, preserve ordering, return expected shape.
- Slice D: trigger downstream effects if required.
  - Tests: emitted event or side effect at the boundary that matters.

After tests are written, implement the feature using existing requirement-related classes or add a new parser, repository, or workflow seam only when needed.
