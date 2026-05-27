# Writing Plans Skill

When this skill is invoked, announce: "I'm using the writing-plans skill."

## Purpose

Create a complete, unambiguous implementation plan that any engineer can follow without guessing.

## Plan Document Format

Save to: `docs/superpowers/plans/YYYY-MM-DD-<feature-name>.md`

### Required Header

```
Goal: [what this plan accomplishes]
Architecture: [brief description of approach]
Tech Stack: [languages, frameworks, tools]
```

### File Map

Before tasks, list every file that will be created or modified and its single responsibility.

### Task Decomposition Rules

- Each task = 2–5 minutes of work.
- Every task includes: affected files, numbered steps with exact code, test commands with expected output, git commit message.
- **No ambiguity**: "add validation" or "TBD" are forbidden. Every step must be immediately actionable.
- Example task steps: "Write failing test", "Run to verify failure", "Implement code", "Run to verify pass", "Commit".

## Quality Gate (self-review before saving)

- Every spec requirement maps to at least one task.
- No placeholder patterns (TODO, TBD, "etc.", "and so on").
- Type names and function signatures are consistent across all tasks.
- Each task can be completed independently without knowledge of other tasks.

## Execution Handoff

After saving the plan, offer two execution paths:
1. **Subagent-driven** (recommended): fresh agent per task via the subagent-driven-development skill.
2. **Inline execution**: batch with checkpoints via the executing-plans skill.
