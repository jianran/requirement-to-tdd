---
name: requirement-to-ddd-skill
description: A Claude skill for requirement-related development tasks. Use this skill when adding or improving requirement parsing, validation, repository storage, or requirement-driven features.
license: MIT
---

# Requirement Development Skill

Use this skill when the task involves requirement-related classes, modules, or package structure. The goal is to implement or extend requirement behavior using a test-first workflow.

## When to use

- You need to locate requirement-related modules or packages in an existing codebase.
- You need to identify existing domain classes like `Requirement`, `RequirementRepository`, `RequirementParser`, or equivalent.
- A new feature requires a new class or domain object.
- You must write unit tests before making implementation changes.

## What to do

1. **Locate the requirement module/package**
   - Search the repository for `Requirement`, `requirement`, `requirements`, or `parser`.
   - Identify which files currently define requirement models or storage behavior.

2. **Inspect existing classes and behavior**
   - If there is a `Requirement` class, inspect its fields and validation rules.
   - If there is a repository or parser class, understand its purpose and public methods.

3. **Determine if a new class is needed**
   - If the new feature requires parsing structured text, add or extend a parser class.
   - If the feature requires storage, filtering, listing, or duplicate prevention, add or extend a repository class.
   - Keep existing classes intact unless the feature requires small, surgical changes.

4. **Write unit tests first**
   - Create tests that describe the new behavior before implementing it.
   - Use the existing class names and method names where possible.
   - Keep test cases focused on the feature and edge cases.

5. **Check requirement coverage and enrich tests**
   - After writing initial tests, review if all requirement aspects are covered by TDD.
   - If more test data or edge cases are needed for complete coverage, request to enrich the unit tests.
   - Ensure tests cover all stated requirements before proceeding to implementation.

6. **Implement only what the tests require**
   - Avoid adding unrelated helpers or abstractions.
   - Match the project's existing style.
   - Keep the diff minimal and verifiable.

## Example feature flow

For a new feature that ingests requirement text and stores it:

1. Find existing classes: `Requirement`, `RequirementParser`, `RequirementRepository`, and `ClaudeSkill`.
2. Decide whether to add a new parser method or a new repository behavior.
3. Write tests for:
   - parsing valid requirement text
   - rejecting invalid requirement format
   - preventing duplicate requirement titles
   - storing parsed requirements and listing them
4. Check if all requirement aspects are covered by the tests.
5. If more test data is needed, request to enrich the unit tests with additional scenarios.
6. Implement the feature to make those tests pass.

## Skill rules

- Do not build a Python library package unless the project already requires it.
- Prefer documentation and instructions that map directly to the code changes.
- Do not rewrite unrelated code or add abstractions beyond the feature.
- Ask clarifying questions if the codebase already contains requirement-related classes but their intended use is ambiguous.
- Always check if all requirements are covered by TDD before implementation.
- Request to enrich unit tests if more data or edge cases are needed for complete coverage.
