# Diagnose Skill

When this skill is invoked, announce: "I'm using the diagnose skill."

Trigger automatically when: a user reports a bug, describes something broken or throwing errors, mentions a performance problem, or says "debug this" / "diagnose this."

## The Six Phases

### Phase 1: Build a Feedback Loop (most critical)

Create a fast, deterministic pass/fail signal before anything else. Preferred options in order:
1. Failing automated test.
2. `curl` or HTTP script that reproduces the failure.
3. CLI invocation that demonstrates the error.
4. Headless browser script.
5. Minimal reproduction script.

A 2-second deterministic loop is a debugging superpower. Invest heavily here — everything else follows mechanically once you have it.

### Phase 2: Reproduce

Run the loop and confirm:
- The bug appears consistently.
- The failure matches the user's description.
- It's reproducible across multiple runs (not flaky).

### Phase 3: Hypothesize

Before testing anything, generate **3–5 ranked, falsifiable hypotheses**:

> "If X is the cause, then changing Y will make the bug disappear."

Share the hypotheses with the user for course-correction before testing.

### Phase 4: Instrument

- Test one hypothesis at a time.
- Prefer a debugger over logging. If using logs, tag them with a unique prefix for easy cleanup.
- Map each probe to a specific prediction from Phase 3.
- Do not test multiple hypotheses simultaneously.

### Phase 5: Fix + Regression Test

1. Write a regression test that reproduces the bug at the correct seam.
2. Confirm it fails.
3. Apply a single targeted fix.
4. Confirm the regression test passes.
5. Run the full test suite — confirm no regressions.

### Phase 6: Cleanup + Post-Mortem

- Remove all debug instrumentation and temporary logs.
- Confirm the original reproduction scenario no longer triggers the bug.
- Document: what prevented catching this bug earlier, and any architectural improvements worth making.

## Red Flag

If you've attempted 3+ different fixes and none worked: stop. This signals an architectural problem. Escalate to the user rather than continuing to guess.
