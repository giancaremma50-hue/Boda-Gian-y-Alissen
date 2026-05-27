# Finishing a Development Branch Skill

When this skill is invoked, announce: "I'm using the finishing-a-development-branch skill."

## Step 1: Verify Tests Pass

Run the full test suite. **Stop if any tests fail** — do not proceed until all tests pass.

## Step 2: Detect Git Environment

Determine which situation you're in:
- Normal repository on a named feature branch.
- Named-branch worktree (created by git-worktrees skill).
- Detached HEAD state (externally managed by a harness).

## Step 3: Determine Base Branch

Identify the branch this feature branch split from:
```bash
git merge-base HEAD main  # or master
```

## Step 4: Present Options

**For normal repo or named-branch worktree (4 options):**
1. Merge back to base branch locally.
2. Push and create a Pull Request.
3. Keep the branch as-is (no action).
4. Discard this work (requires typed confirmation).

**For detached HEAD (3 options):**
1. Push as a new branch and create a PR.
2. Keep as-is (no action).
3. Discard this work (requires typed confirmation).

## Step 5: Execute and Clean Up

- For **merge** or **discard**: clean up the worktree if it was self-created under standard superpowers directories.
- Never run cleanup from inside the worktree being removed.
- Require typed confirmation (not just "yes/no") before any discard operation.
- Never clean up worktrees managed by external harnesses.
