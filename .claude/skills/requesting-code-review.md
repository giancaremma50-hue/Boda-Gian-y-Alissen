# Requesting Code Review Skill

When this skill is invoked, announce: "I'm using the requesting-code-review skill."

## When to Request a Review

**Required:**
- After completing each task in subagent-driven development.
- After finishing a major feature.
- Before merging to the main branch.

**Recommended:**
- When stuck and need a fresh perspective.
- Before a significant refactor (establish a baseline).
- After a complex bug fix.

## Process

1. **Get git identifiers:**
   ```bash
   BASE_SHA=$(git merge-base HEAD main)
   HEAD_SHA=$(git rev-parse HEAD)
   echo "BASE: $BASE_SHA  HEAD: $HEAD_SHA"
   ```

2. **Dispatch a code-reviewer subagent** using the Task tool with `general-purpose` type. Include: BASE_SHA, HEAD_SHA, the feature's requirements, and what specifically to review.

3. **Act on feedback by priority:**
   - **Critical** — Fix immediately before continuing.
   - **Important** — Fix before merging.
   - **Minor** — Log for later; may defer.

## Rules

- Never skip the review step at task completion in subagent workflows.
- Never dismiss critical findings without a technical rebuttal backed by evidence.
- Never proceed with unfixed critical or important issues.
- Disagreement is allowed — but requires a technical argument, not a preference.
