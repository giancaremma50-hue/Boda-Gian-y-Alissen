# Brainstorming Skill

When this skill is invoked, announce: "I'm using the brainstorming skill."

## Core Rule

**DO NOT write any code, scaffold any project, or take any implementation action until you have presented a complete design and the user has explicitly approved it.**

## Process (follow in order)

1. **Explore project context** — Read CLAUDE.md, existing code structure, and relevant docs to understand what already exists.

2. **Offer visual companion** — If mockups or diagrams would help clarify the design, offer this as a separate message first.

3. **Ask clarifying questions** — Ask ONE question at a time. Wait for the answer before asking the next. Cover: goals, constraints, users, tech preferences, non-goals.

4. **Propose 2–3 approaches** — Present distinct options with trade-offs for each. Do not pick one; let the user decide.

5. **Present design sections** — Walk through each area (architecture, components, data flow, error handling, testing). Keep each section proportional to its complexity: a few sentences if simple, up to 200–300 words if nuanced. Get approval per section.

6. **Write design documentation** — Save the agreed design to `docs/design/YYYY-MM-DD-<feature-name>.md`.

7. **Self-review the spec** — Check for: placeholders, contradictions, ambiguity, scope creep, missing error paths. Fix before showing the user.

8. **Get final user approval** — Present the complete written spec and wait for explicit approval.

9. **Invoke writing-plans skill** — Only after approval, transition to the writing-plans skill to create an implementation plan.

## Principles

- One question at a time — never ask multiple questions in one message.
- Even "simple" tasks need a design step; unexamined assumptions cause the most wasted work.
- Do not invoke any other implementation skill until Step 9.
