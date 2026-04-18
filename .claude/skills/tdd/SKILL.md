---
name: tdd
description: Implement features using Test-Driven Development (Red-Green-Refactor). Use when asked to "use TDD", "write tests first", or when building any new function, API endpoint, or component that needs test coverage.
---

# TDD — Test-Driven Development

Red → Green → Refactor. Write a failing test, make it pass with minimal code, then clean up.

## How It Works

1. **Red** — Write a failing test that describes desired behavior. Run it, confirm it fails.
2. **Green** — Write the minimum production code to make the test pass. Run tests, confirm green.
3. **Commit** — Commit the passing state before refactoring.
4. **Refactor** — Improve code quality without changing behavior. Tests must stay green.
5. Repeat for the next behavior.

## Usage

```
"Use TDD to implement the checkout total calculation"
"/tdd add email validation to the signup form"
"Write this feature test-first"
```

## Workflow

```
Feature request
    │
    ▼
┌─────────────────────────┐
│ RED                     │
│ Write failing test      │
│ Run → must fail         │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│ GREEN                   │
│ Minimal passing code    │
│ Run → must pass         │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│ COMMIT                  │
│ git commit (green state)│
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│ REFACTOR                │
│ Clean up, no new tests  │
│ Run → still green       │
└─────────────────────────┘
```

## Test Structure

```
describe('[Unit under test]', () => {
  it('[should do X when Y]', () => {
    // Arrange
    // Act
    // Assert
  });
});
```

## Rules

ALWAYS:
- Run tests after each phase — never skip the red step
- Commit after green, before refactor
- Test behavior, not implementation
- One failing test at a time
- Keep each test independent (no shared mutable state)

NEVER:
- Write production code before a failing test exists
- Write multiple failing tests at once
- Refactor and add features simultaneously
- Skip the refactor step — accumulated debt compounds
- Mock things that don't need mocking

## Troubleshooting

**Test passes immediately (no red phase):** The behavior already exists — check if you're testing the right thing or if it's a duplicate.

**Can't get green without complex code:** Break the test into smaller behaviors and test them incrementally.

**Refactor breaks tests:** You've changed behavior, not just structure. Revert and separate the concerns.
