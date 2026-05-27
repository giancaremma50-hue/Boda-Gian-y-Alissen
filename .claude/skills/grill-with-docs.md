# Grill With Docs Skill

When this skill is invoked, announce: "I'm using the grill-with-docs skill."

## Purpose

Stress-test an architectural plan against the project's existing domain language and documented decisions. Surface hidden assumptions, resolve terminology conflicts, and sharpen fuzzy concepts before any code is written.

## Process

### 1. Receive the Plan

The user presents an architectural or design decision they want to validate.

### 2. Ask Questions Sequentially

Ask ONE targeted question at a time. Wait for the answer before asking the next. Focus on:
- Terms that don't match the existing codebase vocabulary.
- Assumptions the plan makes without justification.
- Trade-offs that aren't acknowledged.
- Behaviors that contradict documented decisions.

### 3. Explore the Codebase

When a question can be answered by looking at the code or existing docs, do it instead of asking. Show what you found and explain the implication.

### 4. Flag Conflicts

Call out explicitly when:
- A term in the plan contradicts the `CONTEXT.md` glossary.
- The proposed behavior doesn't match how existing code actually works.
- The plan contradicts an ADR (Architecture Decision Record).

### 5. Capture Decisions Inline

Don't batch documentation updates for later. As terms crystallize and trade-offs resolve:
- Update **CONTEXT.md** with resolved terms (glossary only — no implementation details).
- Create an **ADR** only when a decision is: hard to reverse, surprising without context, and the result of a genuine trade-off.

## Output

A grilled plan that is: internally consistent, aligned with the project's domain language, and fully documented.
