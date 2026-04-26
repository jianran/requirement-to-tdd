---
name: requirement-to-tdd
description: Turn requirements, specs, PRDs, issues, or feature requests into a disciplined TDD workflow. Use this skill repository when an agent needs to clarify acceptance criteria, decompose simple or complex features into testable slices, map requirements to tests, write failing tests first, and implement the smallest verified change.
---

# Requirement-to-TDD Skill

This repository contains a Claude-style skill for turning requirements into verified code changes with a test-first workflow.

It is not a Python library package. It helps an agent:

- normalize ambiguous requirements into testable clauses
- scale from small changes to complex feature requirements
- locate requirement-related modules and existing implementation seams
- map requirement clauses and delivery slices to tests before changing runtime code
- prefer the smallest useful test strategy and implementation diff
- report requirement coverage, assumptions, and remaining gaps

## How to use

1. Copy `CLAUDE.md` into your project root.
2. Use the `skills/requirement-skill/SKILL.md` file for instruction when implementing requirement-related features.
3. Use `skills/requirement-skill/references/test-design.md` when the requirement needs decomposition or a clearer coverage map.
4. Use `skills/requirement-skill/references/complex-features.md` when the feature spans multiple modules, boundaries, or delivery steps.
5. Use `skills/requirement-skill/references/system-design.md` when designing system interactive flows and API specifications.
6. Prefer test-first development: write the tests that capture the next useful behavior before editing runtime code.
