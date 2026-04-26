---
name: requirement-to-tdd
description: Turn requirements, specs, PRDs, issues, or feature requests into a disciplined TDD workflow. Use this skill repository when an agent needs to locate requirement-related code, clarify acceptance criteria, map requirements to tests, write failing tests first, and implement the smallest verified change.
---

# Requirement-to-TDD Skill

This repository contains a Claude-style skill for turning requirements into verified code changes with a test-first workflow.

It is not a Python library package. It helps an agent:

- normalize ambiguous requirements into testable clauses
- locate requirement-related modules and existing implementation seams
- map requirement clauses to tests before changing runtime code
- prefer the smallest useful test layer and minimal implementation diff
- report requirement coverage, assumptions, and remaining gaps

## How to use

1. Copy `CLAUDE.md` into your project root.
2. Use the `skills/requirement-skill/SKILL.md` file for instruction when implementing requirement-related features.
3. Use `skills/requirement-skill/references/test-design.md` when the requirement needs decomposition or a clearer coverage map.
4. Prefer test-first development: write the tests that capture the feature behavior before editing runtime code.
