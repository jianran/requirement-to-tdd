# requirement-to-tdd

A Claude-style skill repository for turning requirements into a disciplined TDD workflow.

This repository is designed as a skill, not a Python library. It helps an agent turn requirements, specs, PRDs, issues, and feature requests into failing tests, minimal implementation changes, and explicit coverage reporting.

## Contents

- `CLAUDE.md` — top-level skill metadata and repository guidance
- `skills/requirement-skill/SKILL.md` — requirement-specific instructions for Claude agents
- `skills/requirement-skill/references/test-design.md` — requirement decomposition and coverage patterns
- `EXAMPLES.md` — example workflow and test-first planning

## Purpose

Use this repository when you need to convert a requirement into a verified implementation change in another project.

The skill helps:

- restate and clarify requirements as testable behavior
- locate requirement-related modules and existing implementation seams
- map requirement clauses to tests before editing production code
- choose the smallest useful test layer
- keep implementation changes minimal and aligned with the requested behavior
- report coverage, assumptions, and remaining gaps

## How to use

1. Copy `CLAUDE.md` to the root of your project.
2. Use `skills/requirement-skill/SKILL.md` as the instruction set for a Claude agent.
3. Use `skills/requirement-skill/references/test-design.md` when you need help decomposing the requirement.
4. Search the project for requirement-related code and determine where new functionality belongs.
5. Write focused failing tests for the new feature first.
6. Implement only the behavior needed to satisfy those tests.

## Example workflow

- Search the repository for existing requirement-related classes or packages.
- Identify whether a parser, repository, validator, service, or domain model already exists.
- Map each requirement clause to a planned test.
- Add new tests for the requested feature before changing runtime code.
- Keep edits surgical and avoid unrelated rewrites.

## Notes

- This repository is not a runtime Python package.
- The relevant implementation guidance lives in `skills/requirement-skill/SKILL.md`.
- `skills/requirement-skill/references/test-design.md` contains decomposition and coverage guidance.
- `EXAMPLES.md` contains usage examples and a test-first planning approach.
