---
name: requirement-to-tdd
description: Turn requirements, specs, PRDs, issues, or feature requests into a disciplined TDD workflow. Use when an agent needs to clarify acceptance criteria, decompose simple or complex features into testable slices, map requirements to tests, write failing tests first, and implement the smallest verified change.
---

# Requirement to TDD

Use this skill to convert a requirement into verified code changes with a test-first workflow.

## Use this operating mode

- For a **small feature or bugfix**, move quickly from requirement summary to a thin failing test.
- For a **complex feature**, first decompose the work into slices, invariants, dependencies, and verification layers.
- Keep the process light. Add structure only when complexity requires it.

## Follow this workflow

1. **Normalize the requirement**
   - Restate the requested behavior in concrete terms.
   - Separate confirmed facts, assumptions, open questions, and explicit non-goals.
   - Extract user-visible outcomes, business rules, constraints, and failure cases.
   - If ambiguity is blocking, ask a focused question. If it is not blocking, proceed with the smallest reasonable assumption and state it.

2. **Classify the scope**
   - Decide whether the task is **single-behavior**, **multi-step**, or **cross-module**.
   - If the feature touches multiple components, data boundaries, or asynchronous flows, treat it as complex.
   - For complex features, read `references/complex-features.md` before designing tests.

3. **Clarify missing design decisions**
   - Ask about unclear technology choices: testing frameworks, languages, architecture patterns, integration points, APIs, or third-party services.
   - Ask about unclear UX flow decisions: user interactions, navigation, validation feedback, loading states, error handling, accessibility, and state transitions.
   - Clarify performance, security, backward compatibility, scalability, or rollout constraints when they could change the design.
   - Ask only when the uncertainty is likely to change the implementation materially; otherwise proceed with a narrow stated assumption.

3.5 **Design system interactive flow and API specifications**
   - Generate a high-level system interaction diagram showing component relationships, data flows, and user touchpoints.
   - Design API specifications including endpoints, request/response formats, authentication, error codes, and rate limiting.
   - Define data models, schemas, and validation rules for API payloads.
   - Specify integration points with external systems, databases, or third-party services.
   - Document state transitions, business rules, and edge cases in the API design.
   - Ensure the design supports the clarified UX flow and technology decisions from the previous step.
   - See `references/system-design.md` for detailed guidance on system flow and API specification design.
   - Search for requirement-related modules, classes, tests, fixtures, APIs, schemas, and terminology already used by the codebase.
   - Prefer extending existing domain models, validators, services, handlers, repositories, or workflows over introducing new abstractions.
   - Add a new type only when the behavior does not fit an existing seam cleanly.

5. **Design the thinnest useful test strategy**
   - Choose the lowest test layer that proves the behavior: unit first, then integration, then end-to-end only if needed.
   - For complex features, use a small mix of tests instead of forcing everything into one layer.
   - Convert the requirement into a short coverage map before coding.
   - Ensure every important rule, state change, external boundary, and failure mode has a planned test.
   - See `references/test-design.md` for decomposition and coverage patterns.

6. **Slice complex work into increments**
   - Prefer thin vertical slices that produce observable behavior.
   - Put shared invariants and risky boundaries first.
   - Keep each slice independently testable and reviewable.
   - Do not queue a giant batch of unrelated failing tests before the first implementation step.

7. **Write failing tests first**
   - Add tests that describe the requested behavior before changing production code.
   - Cover happy path, edge cases, invalid input, backward compatibility, and idempotency or duplicate behavior when relevant.
   - Keep tests small, named by behavior, and aligned with project conventions.
   - For complex features, write tests slice by slice.

8. **Implement the minimum change**
   - Change only the code needed to make the current tests pass.
   - Avoid speculative abstractions, broad rewrites, or package restructuring unless the requirement explicitly needs them.
   - Preserve existing public APIs unless the requirement calls for a change.

9. **Refactor without losing coverage**
   - Clean duplication only after tests pass.
   - Keep the diff narrow and easy to review.
   - Re-run the most relevant tests after each meaningful refactor.

10. **Prove requirement coverage**
   - Report which requirement clauses are covered by which tests.
   - Call out assumptions, uncovered gaps, deferred slices, and follow-up tests explicitly.
   - If the requirement changed during implementation, say so plainly.

## Default output structure

When useful, present work in this order:

1. Requirement summary
2. Scope classification
3. Assumptions / blockers
4. Requirement-to-test coverage map
5. Delivery slices for complex work
6. Failing tests added
7. Minimal implementation plan or change summary
8. Verification result and remaining gaps

## Rules

- Prefer requirement traceability over cleverness.
- Prefer the smallest useful slice over a grand design.
- Prefer existing project terminology over inventing a parallel domain model.
- Ask for clarification before implementation when a requirement conflict would make the wrong behavior likely.
- Ask about unclear technology or UX decisions when they would materially change the solution.
- Keep the process proportional to the task; do not turn a small change into ceremony.
- Do not claim completion until relevant tests pass, or until you clearly mark the work as blocked.
