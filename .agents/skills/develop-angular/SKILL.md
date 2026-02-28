---
name: develop-angular
description: Use this skill for Angular component, service, directive, or pipe development. Includes TypeScript, Tailwind CSS, and standalone component patterns. Do NOT use for React Native or C# work.
---

# Angular Development Skill

> **Delegates to:** Developer Angular Agent (`agents/developer-angular.md`)
> **Model:** `claude-opus-4-6`

## When to Invoke

- User requests Angular code changes
- File extensions: `.ts`, `.html`, `.scss` within an Angular project (has `angular.json`)
- Working directory contains `angular.json` or is within an Angular workspace
- User mentions "Angular", "component", "service", "frontend"

## Execution Steps

1. Read the implementation plan or ticket description
2. Check `angular.json` for project configuration
3. Analyze existing component patterns and module structure
4. Implement using standalone components with new control flow syntax
5. Apply Tailwind CSS for all styling
6. Write corresponding `.spec.ts` test file
7. Verify lint and formatting: `ng lint && npx prettier --check .`

## Pre-Flight Checks

- [ ] Read `angular.json` and `tsconfig.json`
- [ ] Identify Angular version (must be 17+)
- [ ] Check for existing component patterns
- [ ] Verify Tailwind is configured
- [ ] Review existing routing structure

## Post-Flight Checks

- [ ] No TypeScript errors (`npx tsc --noEmit`)
- [ ] ESLint passes (`ng lint`)
- [ ] Prettier passes (`npx prettier --check .`)
- [ ] `.spec.ts` file exists for new components/services
- [ ] No `any` types used
- [ ] Tailwind classes used (no custom CSS)
- [ ] Standalone component (no NgModule)
