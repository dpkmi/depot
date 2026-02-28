---
name: test-angular
description: Write and run Jest tests for Angular components, services, and pipes. Creates .spec.ts files with TestBed configuration. Do NOT use for React Native or C# tests.
compatibility: opencode
---

## When to Use
- Angular test writing or running
- After Angular development completes
- `.spec.ts` creation or updates

## Standards
- Jest with `TestBed`, Angular Testing Library
- File naming: `[component].spec.ts`
- AAA pattern, descriptive test names
- Cover: happy path, edge cases, errors, null/undefined, state transitions
- Minimum 80% components, 90% services, 95% utilities

## Run Commands
- `npx jest [file]` — run tests
- `npx jest --coverage [file]` — coverage report
- `ng lint` — lint check
