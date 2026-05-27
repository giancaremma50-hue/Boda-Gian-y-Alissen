# Verification Before Completion Skill

When this skill is invoked, announce: "I'm using the verification-before-completion skill."

## Core Rule

**NO COMPLETION CLAIMS WITHOUT FRESH VERIFICATION EVIDENCE.**

Any statement that work is done, passing, or fixed requires executing a verification command and reading its output immediately beforehand. No exceptions.

## The Verification Gate

Before any success claim, run these five steps:

1. Identify which command proves your assertion (test suite, build, curl, etc.).
2. Execute the command fresh — cached or remembered results don't count.
3. Read the complete output including exit codes.
4. Confirm the output actually supports the claim.
5. Only then make the claim, citing the evidence.

## Forbidden Language Patterns

These words in a completion claim signal you skipped verification:
- "should pass", "probably works", "seems fine", "looks good"
- "Done!" or "Complete!" before running any verification
- "Tests should be green" (run them and confirm they are)

## Scope

This rule applies to ALL success assertions including:
- Committing code ("ready to commit").
- Creating pull requests ("this is ready for review").
- Delegating to subagents ("this task is complete").
- Reporting bug fixes ("the bug is fixed").

## The Principle

Exhaustion is not an excuse. Confidence is not evidence.

**Run the command. Read the output. THEN claim the result.**
