---
name: requirement-to-tdd-skill
description: A Claude skill repository for requirement-related development guidance, with a focus on locating requirement modules/classes, adding new feature classes, and writing unit tests first.
license: MIT
---

# Requirement-to-TDD Skill

This repository contains a Claude Code skill for building requirement-related functionality in an existing codebase.

It is not a Python library package. Instead, it is a skill guide that helps a Claude agent:

- identify requirement-related modules and classes
- understand existing domain objects like `Requirement`, `RequirementRepository`, and `RequirementParser`
- determine whether a new class is needed for a feature
- create unit tests before implementation
- keep changes minimal and aligned with the requested feature

## How to use

1. Copy `CLAUDE.md` into your project root.
2. Use the `skills/requirement-skill/SKILL.md` file for instruction when implementing requirement-related features.
3. Prefer test-first development: write the unit tests that capture the feature behavior before editing runtime code.
