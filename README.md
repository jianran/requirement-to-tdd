# requirement-to-tdd

A Claude-style skill repository for turning requirements into a disciplined TDD workflow.

This repository is designed as a skill, not a Python library. It helps an agent turn requirements, specs, PRDs, issues, and feature requests into failing tests, minimal implementation changes, and explicit coverage reporting.

## Contents

- `CLAUDE.md` — top-level skill metadata and repository guidance
- `skills/requirement-skill/SKILL.md` — requirement-specific instructions for Claude agents
- `skills/requirement-skill/references/test-design.md` — requirement decomposition and coverage patterns
- `skills/requirement-skill/references/complex-features.md` — a lightweight playbook for multi-step and cross-module features
- `EXAMPLES.md` — example workflow and test-first planning

## Purpose

Use this repository when you need to convert a requirement into a verified implementation change in another project.

The skill helps:

- restate and clarify requirements as testable behavior
- scale the workflow from small changes to complex feature requirements
- locate requirement-related modules and existing implementation seams
- map requirement clauses and delivery slices to tests before editing production code
- choose the smallest useful test strategy for the feature
- keep implementation changes minimal and aligned with the requested behavior
- report coverage, assumptions, and remaining gaps

## How to use

1. Copy `CLAUDE.md` to the root of your project.
2. Use `skills/requirement-skill/SKILL.md` as the instruction set for a Claude agent.
3. Use `skills/requirement-skill/references/test-design.md` when you need help decomposing the requirement.
4. Use `skills/requirement-skill/references/complex-features.md` when the feature spans multiple modules, steps, or boundaries.
5. Search the project for requirement-related code and determine where new functionality belongs.
6. Write focused failing tests for the next useful slice.
7. Implement only the behavior needed to satisfy those tests.

## Example workflow

- Search the repository for existing requirement-related classes or packages.
- Classify whether the task is single-behavior or a complex feature.
- Identify whether a parser, repository, validator, service, workflow, or domain model already exists.
- Map each requirement clause and, for complex work, each delivery slice to planned tests.
- Add tests for the next feature slice before changing runtime code.
- Keep edits surgical and avoid unrelated rewrites.

## Advanced pointers

This skill is intentionally lighter than full spec-driven frameworks. Use it when you already have a requirement and want to drive it into TDD quickly, not when you need a full requirements → design → task-management system.

- Need requirement decomposition or better coverage mapping? Start with `skills/requirement-skill/references/test-design.md`.
- Need a cross-module, multi-step, or integration-heavy feature? Read `skills/requirement-skill/references/complex-features.md` first.
- Need a full spec workflow with separate requirements, design, and task artifacts? Pair this skill with a broader spec-driven process before implementation.
- Need hard quality gates, evidence capture, or adversarial review? Add those at the project workflow or CI layer rather than bloating this skill.

## TODO / next improvements

- Add a reference for rollout planning, feature flags, migrations, and backward-compatibility checks.
- Add examples for async, event-driven, and external-integration-heavy features.
- Add a compact verification report template for evidence capture and requirement traceability.
- Add clearer guidance for when to use this skill vs a fuller spec-driven workflow.
- Add an optional architecture and design-question checklist for high-risk features.
- Add examples of contract-test strategy for API and schema boundaries.

## Notes

- This repository is not a runtime Python package.
- The relevant implementation guidance lives in `skills/requirement-skill/SKILL.md`.
- `skills/requirement-skill/references/test-design.md` contains decomposition and coverage guidance.
- `skills/requirement-skill/references/complex-features.md` contains multi-slice planning guidance.
- `EXAMPLES.md` contains usage examples and a test-first planning approach.
