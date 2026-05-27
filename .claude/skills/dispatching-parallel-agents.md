# Dispatching Parallel Agents Skill

When this skill is invoked, announce: "I'm using the dispatching-parallel-agents skill."

## When to Use This

Use when you have **3 or more failures or independent tasks in different domains** that don't share dependencies.

Do NOT use when: failures are interconnected, tasks require full system understanding, or concurrent changes would cause resource conflicts.

## Process

### 1. Group by Domain

Categorize each failure or task by what is actually broken — not by file location. One domain = one agent.

### 2. Craft Focused Prompts

Each agent prompt must contain:
- **Focus**: one specific problem domain.
- **Scope constraint**: "Do NOT change production code" or equivalent boundary.
- **Context**: the exact error message or failure description.
- **Expected output**: "Return: summary of what you found and what you fixed."

Self-contained means the agent gets everything it needs in the prompt — it does not inherit your session history.

### 3. Launch Concurrently

Dispatch all agents at the same time using the Task tool. Do not wait for one to finish before starting the next.

### 4. Integrate Results

After all agents complete:
- Read each summary.
- Check for conflicts between changes.
- Run the full test suite to confirm no regressions.
- Merge acceptable changes; discard conflicting or incorrect ones.

## Common Mistakes to Avoid

- Overly broad assignments: "fix all tests" — narrow the scope.
- Missing error context: always include the specific error message.
- No output constraints: always specify what the agent should return.
- No scope boundaries: always say what the agent should NOT touch.
