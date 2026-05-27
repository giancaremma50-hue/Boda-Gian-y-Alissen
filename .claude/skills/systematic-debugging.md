# Systematic Debugging Skill

When this skill is invoked, announce: "I'm using the systematic-debugging skill."

## Core Rule

**NO FIXES WITHOUT ROOT CAUSE INVESTIGATION FIRST.**

Never propose a solution before tracing the data flow and confirming the root cause. Attempting multiple simultaneous fixes is explicitly forbidden.

## The Four-Phase Framework

### Phase 1: Root Cause Investigation

- Read the full error message and stack trace carefully.
- Reproduce the issue consistently before doing anything else.
- Review recent changes and updated dependencies.
- For multi-component systems: add diagnostic instrumentation and trace the data flow through the call stack.

### Phase 2: Pattern Analysis

- Find similar working code in the codebase and compare it to the broken code.
- Study the reference implementation completely — not just the relevant section.
- Catalog every difference between the working and broken implementations.
- Identify all dependencies and assumptions each version makes.

### Phase 3: Hypothesize and Test

- Generate 3–5 ranked, falsifiable hypotheses: "If X is the cause, then changing Y will make the bug disappear."
- Share hypotheses with the user for course-correction before testing.
- Test one hypothesis at a time with a minimal change.
- Validate results before moving to the next hypothesis.

### Phase 4: Fix

- Write a failing regression test that reproduces the bug at the correct seam.
- Apply a single targeted fix.
- Verify the regression test passes and no other tests regress.

## Red Flags (stop and reassess)

- You think "quick fix for now, investigate later."
- You're proposing a solution before tracing the data flow.
- You've tried 3+ different fixes and none worked — this signals an architectural problem. Escalate to the user rather than continuing.
