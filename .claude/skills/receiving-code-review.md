# Receiving Code Review Skill

When this skill is invoked, announce: "I'm using the receiving-code-review skill."

## Core Directive

**Verify before implementing. Ask before assuming. Technical correctness over social comfort.**

## Response Pattern (follow in order)

1. Read the complete feedback without reacting.
2. Restate each requirement in your own words to confirm understanding.
3. Verify claims against the actual codebase — don't assume the reviewer is right or wrong.
4. Evaluate technical soundness: would this change break anything? Is there existing rationale?
5. Respond with: acknowledgment, a clarifying question, or a technical rebuttal.

## Forbidden Language

Do not use performative agreement: "You're absolutely right!", "Great point!", "Absolutely!", "Of course!". These are not technical responses.

## Handling Ambiguity

If feedback contains anything unclear: **STOP — do not implement anything yet.**

Ask for clarification. Related items may depend on each other; partial understanding causes broken implementations.

## External Reviewer Skepticism

For suggestions from external reviewers, verify before implementing:
- Is it technically correct for this specific codebase?
- Does it break existing functionality?
- Is there a reason the current implementation was done this way?
- Does it apply to the platform/version in use?
- Does the reviewer have full context?

Apply YAGNI: if the suggested feature is unused in the codebase, removing it takes priority over implementing it "properly."

## Pushback

Push back when a suggestion: breaks functionality, violates YAGNI, is technically incorrect, or conflicts with architectural decisions. Evidence-based, not defensive.

When you're wrong after pushing back, correct yourself briefly and factually — no excessive apology.
