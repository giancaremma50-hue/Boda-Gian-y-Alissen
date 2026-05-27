# Subagent-Driven Development Skill

When this skill is invoked, announce: "I'm using the subagent-driven-development skill."

## Core Concept

Fresh subagent per task + two-stage review (spec compliance then code quality) = high quality, fast iteration.

## When to Use

You have an implementation plan with mostly independent tasks to complete in the current session.

## Model Selection

Match computational power to task complexity:
- Simple mechanical tasks (1–2 files, clear spec): use a faster/cheaper model.
- Multi-file integration: use a standard model.
- Architecture, review, ambiguous decisions: use the most capable model available.

## Process Per Task

1. **Dispatch an implementer subagent** — Craft a focused, self-contained prompt with the task spec, affected files, and expected output. The subagent has no memory of your session.

2. **Review subagent status:**
   - `DONE` → proceed to spec review.
   - `DONE_WITH_CONCERNS` → read concerns; address correctness issues before review.
   - `NEEDS_CONTEXT` → provide missing information and re-dispatch.
   - `BLOCKED` → assess: provide more context, use a stronger model, break the task down smaller, or escalate to user.

3. **Spec compliance review** (always first): Does the implementation match the plan spec exactly?

4. **Code quality review** (always second): Is the code clean, maintainable, and free of issues?

5. **Iterate until both reviews pass**, then mark the task complete and proceed to the next.

## Critical Rules

- Never start work on main/master without explicit user permission.
- Never skip either review stage.
- Never accept "close enough" spec compliance — it must match exactly or the spec needs updating.
- Spec compliance review must always run before code quality review.
- If a reviewer finds issues: implementer fixes → reviewer reviews again → repeat until approved.
