---
name: code-review
description: Use this skill to review code for quality, correctness, maintainability, and adherence to team standards. Use for PR reviews and post-implementation quality checks. Do NOT use for security-specific reviews (use security-audit instead).
---

# Code Review Skill

> **Delegates to:** Code Reviewer Agent (`agents/code-reviewer.md`)
> **Model:** `claude-sonnet-4-5-20250929`

## When to Invoke

- User says "review", "code review", "PR review", "check my code"
- After development skill completes (pipeline)
- Before merging a pull request
- User wants feedback on implementation quality

## Execution Steps

1. Read all modified/new files
2. Check against team coding standards for the relevant stack
3. Evaluate code structure, naming, and SOLID principles
4. Verify error handling and edge case coverage
5. Check that tests exist and are meaningful
6. Review for performance issues
7. Provide actionable feedback categorized by severity

## Review Focus Areas

### Core (C#)
- Resource disposal, thread safety, naming conventions
- Parameterized queries, exception handling

### Angular
- Standalone components, strict TypeScript, Tailwind usage
- Observable management, `.spec.ts` coverage

### React Native
- Hooks rules, StyleSheet usage, Expo SDK compatibility
- Platform-specific handling, performance (memo/callback)

## Output

Structured review following the template in `agents/code-reviewer.md`. Includes verdict, categorized findings, and positive feedback.
