---
name: develop-react-native
description: React Native / Expo SDK 54+ mobile development with TypeScript and StyleSheet.create(). Never uses Tailwind. Do NOT use for Angular or C#.
compatibility: opencode
---

## When to Use
- React Native or Expo code changes
- Files: `.tsx`, `.ts` in Expo project (has `app.json`)
- Screen, component, hook development

## Standards
- Functional components only, typed props interfaces
- `StyleSheet.create()` exclusively — NO Tailwind, NO inline styles
- Expo SDK 54+ APIs, Expo Router for navigation
- `expo-secure-store` for tokens — never AsyncStorage
- Design tokens in `constants/` directory
- 44pt minimum touch targets, safe area compliance

## Post-Checks
- `npx tsc --noEmit` → `npx expo lint` → `npx prettier --check .`
- Test file exists, no `any`, StyleSheet only, SDK 54+ APIs
