---
name: debug
description: Bug investigation, root cause analysis, and error tracing across all stacks. Produces diagnosis reports with fix recommendations. Does NOT apply fixes directly.
compatibility: opencode
---

## When to Use
- Bug reports, errors, unexpected behavior
- Stack traces or error messages provided
- Failing tests with unclear cause
- "Why is this failing?" questions

## Investigation Steps
1. Gather symptoms (expected vs actual)
2. Reproduce (exact steps, minimum case)
3. Trace execution path, check recent git changes
4. Identify root cause (file, line, reason)
5. Classify severity
6. Recommend fix (not apply it)
7. Suggest regression test

## Common Patterns
- C#: NullReferenceException, thread affinity, SqlException
- Angular: ExpressionChanged error, NullInjectorError, Observable leaks
- React Native: Invariant Violation, white screen, VirtualizedList warnings
