# Examples

## Using this skill repository

This repo is a Claude Code skill repository for requirement-related development guidance. It is not a Python package.

### Add the skill to your project

Copy `CLAUDE.md` to the root of the target project, and use `skills/requirement-skill/SKILL.md` as your task-specific guidance.

### Example workflow

1. Search the codebase for requirement-related types and modules.
2. Normalize the requirement into explicit clauses, assumptions, and open questions.
3. Identify existing classes like `Requirement`, `RequirementRepository`, `RequirementParser`, validators, or a similar domain model.
4. Map each requirement clause to a planned test.
5. Draft failing tests first to specify the feature you are adding.
6. Implement only the code necessary to satisfy those tests.

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

After tests are written, implement the feature using existing requirement-related classes or add a new parser/repository class if needed.
