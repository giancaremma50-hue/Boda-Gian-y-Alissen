# TDD with Claude Workflow

When this skill is invoked, announce: "I'm using the TDD with Claude workflow."

## The Problem This Solves

Claude naturally writes implementation first, then tests. TDD requires the inverse: tests must drive design, not validate pre-existing code.

## Setup

Add to your project's `CLAUDE.md`:

```markdown
## Testing Conventions

### TDD Workflow
- Always write failing tests BEFORE implementation
- One behavior per test, one test per cycle
- Test names describe behavior: "should_return_empty_when_no_items"
- Tests should FAIL initially (no implementation exists)
```

## The Red-Green-Refactor Cycle

### Phase 1 — Red (Write Failing Test)

Prompt Claude:
```
Write a failing test for [feature description].
Do NOT write any implementation yet.
The test should fail because the function does not exist.
```

Verify: run the tests — they must fail before proceeding.

### Phase 2 — Green (Minimal Implementation)

Prompt Claude:
```
Now implement the minimum code to make these tests pass.
Only write enough code to satisfy the current tests, nothing more.
```

Verify: run the tests — they must all pass.

### Phase 3 — Refactor (Clean Up)

Prompt Claude:
```
Refactor the implementation to improve code quality.
Tests must stay green after every change.
Focus on: [readability / removing duplication / performance]
```

## Integration with Claude Code

**CLAUDE.md** — Add testing conventions so every session respects TDD.

**Plan Mode** — Use Shift+Tab to enter plan mode and design the full test strategy before any code is written.

**Hooks** — Auto-run tests after every edit:
```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Edit|Write",
        "command": "npm test --watchAll=false 2>&1 | head -20"
      }
    ]
  }
}
```

**TodoWrite** — Track TDD phases:
```
- [ ] RED: Write failing tests for [feature]
- [ ] GREEN: Implement to pass tests
- [ ] REFACTOR: Clean up
```

## Anti-Patterns to Avoid

| Wrong | Right |
|-------|-------|
| "Write tests for this feature" | "Write FAILING tests that don't exist yet" |
| "Add tests and implementation" | Two separate prompts — tests first |
| "Make sure tests pass" | "Write tests, then implement minimally" |
| Combining Red and Green phases | Always separate: stop after Red, then Green |
| "Test existing code" | Write tests for behavior as if code doesn't exist |

## Key Principle

Tests should FAIL initially. If they pass before you write implementation, the tests are not driving design — they're just describing existing code.
