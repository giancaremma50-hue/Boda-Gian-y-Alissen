# Using Git Worktrees Skill

When this skill is invoked, announce: "I'm using the git-worktrees skill."

## Core Principle

Detect existing isolation first. Use native tools if available. Fall back to git worktrees. Never fight the harness.

## Step 0: Detect Existing Isolation

Check if already in an isolated workspace:
```bash
echo "GIT_DIR=$GIT_DIR, GIT_COMMON=$GIT_COMMON"
git rev-parse --show-superproject-working-tree
```

If already isolated, skip creation. If not, request user consent before proceeding.

## Step 1: Create Isolated Workspace

**Preferred**: Use native worktree tools if the environment provides them.

**Fallback**: Manual git worktree creation.
- Directory priority: user instructions > existing `.worktrees/` directory > project-local `.worktrees/` (create it) > legacy global path.
- Verify the chosen directory is gitignored before creating the worktree.
- Never nest worktrees inside another worktree.

## Step 2: Project Setup

Auto-detect and install dependencies in the new worktree:
- Node.js: `npm install`
- Rust: `cargo build`
- Python: `pip install -r requirements.txt` or `poetry install`
- Go: `go mod download`

## Step 3: Verify Baseline

Run the project's test suite in the new worktree before starting any implementation. Confirm a clean baseline — no pre-existing failures.

## Critical Safeguards

- Always get user consent before creating a worktree.
- Verify gitignore before creation.
- Only clean up worktrees you created under standard superpowers directories — never clean up externally managed environments.
