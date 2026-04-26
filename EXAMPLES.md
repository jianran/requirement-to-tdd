# Examples

## Using this skill repository

This repo is a Claude Code skill repository for requirement-related development guidance. It is not a Python package.

### Add the skill to your project

Copy `CLAUDE.md` to the root of the target project, and use `skills/requirement-skill/SKILL.md` as your task-specific guidance.

### Example workflow

1. Search the codebase for requirement-related types and modules.
2. Identify existing classes like `Requirement`, `RequirementRepository`, `RequirementParser`, or a similar domain model.
3. Draft unit tests first to specify the feature you are adding.
4. Implement only the code necessary to satisfy those tests.

## Example test-first plan

For a new requirement ingestion feature:

- Test: parse requirement text with `Title`, `Description`, `Priority`, `Status`, and `Tags`.
- Test: reject malformed requirement input.
- Test: prevent duplicate requirement titles.
- Test: expose a list or retrieval API for requirements.

After tests are written, implement the feature using existing requirement-related classes or add a new parser/repository class if needed.
