# requirement-to-tdd

A Claude Code skill repository for requirement-related development guidance.

This repository is designed as a skill, not a Python library. It provides task guidance for requirement-related feature work, based on the Karpathy-style Claude skill format.

## Contents

- `CLAUDE.md` — top-level skill metadata and repository guidance
- `skills/requirement-skill/SKILL.md` — requirement-specific instructions for Claude agents
- `EXAMPLES.md` — example workflow and test-first planning

## Purpose

Use this repository when you need to implement or extend requirement-related code in another project.

The skill helps:

- locate requirement-related modules and classes
- identify existing domain objects like `Requirement`, `RequirementRepository`, or `RequirementParser`
- decide whether a new class should be created for a feature
- write unit tests first before implementation
- keep changes minimal and aligned with the requested feature

## How to use

1. Copy `CLAUDE.md` to the root of your project.
2. Use `skills/requirement-skill/SKILL.md` as the instruction set for a Claude agent.
3. Search the project for requirement-related code and determine where new functionality belongs.
4. Write focused unit tests for the new feature first.
5. Implement only the behavior needed to satisfy those tests.

## Example workflow

- Search the repository for existing requirement-related classes or packages.
- Identify whether a parser, repository, or domain model already exists.
- Add new tests for the requested feature before changing runtime code.
- Keep edits surgical and avoid unrelated rewrites.

## Notes

- This repository is not a runtime Python package.
- The relevant implementation guidance lives in `skills/requirement-skill/SKILL.md`.
- `EXAMPLES.md` contains usage examples and a test-first planning approach.
