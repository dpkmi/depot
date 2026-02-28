---
name: debug
description: Use this skill to investigate bugs, trace errors, perform root cause analysis, and diagnose application issues. Do NOT use for fixing bugs (use the appropriate develop skill after diagnosis).
---

# Debug Skill

> **Delegates to:** Debugger Agent (`agents/debugger.md`)
> **Model:** `chatgpt-codex-5.2-xhigh`

## When to Invoke

- User reports a bug, error, or unexpected behavior
- User says "debug", "investigate", "why is this failing", "root cause"
- Stack trace or error message is provided
- A test is failing and the cause is unclear

## Execution Steps

1. Gather symptom information from the user
2. Read relevant source code files
3. Trace the execution path from entry point to failure
4. Check recent git changes to affected files: `git log --oneline -20 -- [file]`
5. Identify root cause with specific file and line number
6. Classify bug severity
7. Produce fix recommendation (not the fix itself)
8. Suggest regression test

## Debug Shortcuts

### Common C# Issues
- `NullReferenceException` → trace object creation chain
- `InvalidOperationException` → check thread affinity (WinForms)
- `SqlException` → check connection string and query params

### Common Angular Issues
- `ExpressionChangedAfterItHasBeenCheckedError` → change detection issue
- `NullInjectorError` → missing provider in standalone component
- `Observable` not emitting → check subscription and operator chain

### Common React Native Issues
- `Invariant Violation` → check component rendering conditions
- White screen → check navigation setup and error boundaries
- `VirtualizedList` warning → use `FlatList` correctly

## Output

Structured diagnosis report following the template in `agents/debugger.md`. Includes root cause, reproduction steps, and fix recommendation.
