# Test-Driven Development (TDD) Skill

When this skill is invoked, announce: "I'm using the TDD skill."

## Non-Negotiable Rule

**NO PRODUCTION CODE WITHOUT A FAILING TEST FIRST.**

You must witness a test fail before writing any implementation. If you write code before its test, delete the code and start over. Using it as "reference" while writing tests is a rationalization — stop.

## The Three-Phase Cycle

### RED — Write a Failing Test

- Write a minimal test that describes ONE specific behavior.
- The test name must clearly describe what behavior it proves.
- Run the test suite and confirm it fails.
- Do not write any implementation in this phase.

### GREEN — Implement the Minimum

- Write the simplest code that makes the failing test pass.
- Do not add features, abstractions, or optimizations beyond what the test requires.
- Run the test suite and confirm it passes.

### REFACTOR — Clean Up

- Improve clarity, remove duplication, rename for readability.
- Run the test suite after each change to confirm all tests still pass.
- Do not change behavior during refactor.

## Rationalizations to Reject

- "It's too simple to need a test" — write the test anyway.
- "I'll test it afterward" — no. Delete the code and start with the test.
- "I already manually tested it" — manual tests don't count.
- "Deleting hours of work is wasteful" — sunk cost fallacy. Delete it.
- "This case is different because..." — it isn't.

## Cycle Discipline

Complete the full RED → GREEN → REFACTOR cycle for each behavior before moving to the next. Never stack multiple behaviors in one cycle.
