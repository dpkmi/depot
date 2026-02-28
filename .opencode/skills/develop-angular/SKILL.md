---
name: develop-angular
description: Angular component, service, and directive development with TypeScript strict mode and Tailwind CSS. Standalone components, signals, new control flow. Do NOT use for React Native or C#.
compatibility: opencode
---

## When to Use
- Angular code changes in projects with `angular.json`
- Files: `.ts`, `.html`, `.scss` in Angular workspace
- Component, service, directive, pipe development

## Standards
- Standalone components, `@if`/`@for`/`@switch`, signals
- `input()`/`output()` APIs, `inject()` function
- TypeScript strict, no `any`, interfaces for all data
- Tailwind CSS only — no custom CSS
- `.spec.ts` for every component/service
- `ChangeDetectionStrategy.OnPush`
- `takeUntilDestroyed()` for subscriptions

## Post-Checks
- `npx tsc --noEmit` → `ng lint` → `npx prettier --check .`
- `.spec.ts` exists, no `any` types, Tailwind only
