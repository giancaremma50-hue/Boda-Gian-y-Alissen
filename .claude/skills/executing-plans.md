# Executing Plans Skill

When this skill is invoked, announce: "I'm using the executing-plans skill."

## Process

### Phase 1: Load and Review

1. Read the plan document completely.
2. Raise any concerns with the user before starting — missing dependencies, ambiguous steps, conflicting assumptions.
3. Create a TodoWrite list with every task from the plan.
4. Confirm you are NOT on main/master (use a feature branch or worktree).

### Phase 2: Execute Tasks

For each task:
1. Mark the task as `in_progress`.
2. Follow the plan steps exactly — do not improvise.
3. Run every specified verification command and read the full output.
4. Only mark as `completed` after all verifications pass.

### Critical Stop Points

Halt immediately and ask for clarification if:
- A dependency is missing or incompatible.
- A test fails for an unexpected reason.
- A step is unclear or contradicts another step.
- Verification fails more than twice in a row.

Do not attempt workarounds or "close enough" implementations — stop and ask.

### Phase 3: Complete

After all tasks pass verification, invoke the **finishing-a-development-branch** skill.

## Constraints

- Never start on main/master without explicit user permission.
- Follow plan steps exactly; do not add unrequested features.
- If the plan requires fundamental rethinking, return to writing-plans rather than improvising.
