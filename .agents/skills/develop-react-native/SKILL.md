---
name: develop-react-native
description: Use this skill for React Native and Expo mobile development. Uses StyleSheet for styling (NOT Tailwind). Expo SDK 54+. Do NOT use for Angular or C# work.
---

# React Native Development Skill

> **Delegates to:** Developer React Native Agent (`agents/developer-react-native.md`)
> **Model:** `claude-opus-4-6`

## When to Invoke

- User requests React Native or Expo code changes
- File extensions: `.tsx`, `.ts` within an Expo project (has `app.json` or `app.config.ts`)
- Working directory contains `app.json` with Expo configuration
- User mentions "React Native", "Expo", "mobile app", "RN"

## Execution Steps

1. Read the implementation plan or ticket description
2. Check `app.json` / `app.config.ts` for Expo configuration and SDK version
3. Analyze existing screen and component patterns
4. Implement using functional components with TypeScript
5. Style using `StyleSheet.create()` — never Tailwind
6. Write corresponding `.test.tsx` test file
7. Verify lint: `npx expo lint`

## Pre-Flight Checks

- [ ] Read `app.json` or `app.config.ts`
- [ ] Verify Expo SDK version is 54+
- [ ] Check `tsconfig.json` for strict mode
- [ ] Review existing navigation structure (Expo Router)
- [ ] Identify state management pattern in use

## Post-Flight Checks

- [ ] No TypeScript errors (`npx tsc --noEmit`)
- [ ] ESLint passes (`npx expo lint`)
- [ ] Prettier passes (`npx prettier --check .`)
- [ ] Test file exists for new screens/components
- [ ] No `any` types
- [ ] StyleSheet used (no inline styles, no Tailwind)
- [ ] `expo-secure-store` used for sensitive data (not AsyncStorage)
- [ ] Expo SDK 54+ APIs only
