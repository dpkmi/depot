---
name: test-react-native
description: Write and run Jest tests for React Native / Expo components and hooks using React Native Testing Library. Do NOT use for Angular or C# tests.
compatibility: opencode
---

## When to Use
- React Native / Expo test writing or running
- After React Native development completes
- `.test.tsx` creation or updates

## Standards
- Jest + React Native Testing Library
- File naming: `[Component].test.tsx` or `__tests__/`
- Mock navigation, native modules, external services
- Test renders, interactions, state changes
- Minimum 80% screens/components, 90% hooks/services, 95% utilities

## Run Commands
- `npx jest [file]` — run tests
- `npx jest --coverage [file]` — coverage report
- `npx expo lint` — lint check
