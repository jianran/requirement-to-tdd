---
name: requirement-to-tdd
description: Turn requirements, specs, PRDs, issues, or feature requests into a disciplined TDD workflow. Use when an agent needs to locate requirement-related code, clarify acceptance criteria, map requirements to tests, write failing tests first, and implement the smallest change that satisfies the requirement.
---

# Requirement to TDD

Use this skill to convert a requirement into verified code changes with a test-first workflow.

## Follow this workflow

1. **Normalize the requirement**
   - Restate the requested behavior in concrete terms.
   - Separate confirmed facts, assumptions, and open questions.
   - Treat each explicit rule, constraint, or acceptance criterion as something that must be covered by tests.
   - If ambiguity is blocking, ask a focused question. If it is not blocking, proceed with the smallest reasonable assumption and state it.

2. **Find the existing implementation seam**
   - Search for requirement-related modules, classes, tests, fixtures, or terminology already used by the codebase.
   - Prefer extending existing `Requirement`, `RequirementParser`, `RequirementRepository`, validators, services, or handlers over introducing new abstractions.
   - Add a new type only when the behavior does not fit an existing seam cleanly.

3. **Design the thinnest useful test slice**
   - Choose the lowest test layer that proves the behavior: unit first, then integration, then end-to-end only if needed.
   - Convert the requirement into a short coverage map before coding.
   - Ensure every `must`, `should`, validation rule, state change, and failure mode has a corresponding planned test.
   - See `references/test-design.md` for decomposition and coverage patterns.

4. **Write failing tests first**
   - Add tests that describe the requested behavior before changing production code.
   - Cover happy path, edge cases, invalid input, and duplicate/idempotency behavior when relevant.
   - Keep tests small, named by behavior, and aligned with existing project conventions.

5. **Implement the minimum change**
   - Change only the code needed to make the new tests pass.
   - Avoid speculative abstractions, broad rewrites, or package restructuring unless the requirement explicitly needs them.
   - Preserve existing public APIs unless the requirement calls for a change.

6. **Refactor without losing coverage**
   - Clean duplication only after tests pass.
   - Keep the diff narrow and easy to review.
   - Re-run the most relevant tests after each meaningful refactor.

7. **Prove requirement coverage**
   - Report which requirement clauses are covered by which tests.
   - Call out remaining assumptions, uncovered gaps, or follow-up tests explicitly.
   - If the requirement changed during implementation, say so plainly.

## Default output structure

When useful, present work in this order:

1. Requirement summary
2. Assumptions / blockers
3. Requirement-to-test coverage map
4. Failing tests added
5. Minimal implementation plan or change summary
6. Verification result and remaining gaps

## Rules

- Prefer requirement traceability over cleverness.
- Prefer one failing test at a time over large speculative test batches.
- Prefer existing project terminology over inventing a parallel domain model.
- Ask for clarification before implementation when a requirement conflict would make the wrong behavior likely.
- Do not claim completion until tests relevant to the requirement pass, or until you clearly mark the work as blocked.
