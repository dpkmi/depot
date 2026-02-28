---
name: code-review
description: Code quality review for correctness, maintainability, SOLID principles, and team standards compliance. Provides actionable feedback categorized by severity. Does NOT modify code.
compatibility: opencode
---

## When to Use
- PR reviews, post-implementation quality checks
- "Review my code" requests
- Before merging pull requests

## Review Focus
- **Must Fix:** Logic errors, missing error handling, security issues, missing tests, `any` types
- **Should Fix:** DRY violations, poor naming, missing edge cases, accessibility gaps
- **Nice to Have:** Style preferences, alternative approaches, documentation

## Stack Checks
- C#: IDisposable, thread safety, parameterized SQL
- Angular: Standalone components, strict TS, Tailwind, .spec.ts
- React Native: StyleSheet, hooks rules, Expo SDK 54+ APIs
