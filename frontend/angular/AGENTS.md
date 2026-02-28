# Angular Team Agent Configuration

> **Team:** Frontend — Angular
> **Stack:** Angular 17+, TypeScript (strict), Tailwind CSS, Jest
> **Developers:** 2

## Working Agreements

- All code must pass `ng lint` before committing
- All code must pass `npx prettier --check .` before committing
- Every component must have a corresponding `.spec.ts` file
- No `any` types — strict TypeScript only
- Use standalone components — no new NgModules
- Tailwind CSS for all styling — no custom CSS unless documented exception

## Code Standards

### Components
- Use standalone components with `imports` array
- Use new control flow: `@if`, `@for`, `@switch`, `@defer`
- Use `input()` and `output()` function-based APIs
- Use `inject()` instead of constructor injection
- Use `signal()`, `computed()`, `effect()` for reactive state
- Use `ChangeDetectionStrategy.OnPush` for all components
- Destroy subscriptions with `takeUntilDestroyed()`

### TypeScript
- `strict: true` in `tsconfig.json`
- No `any` — use `unknown` if type is truly unknown
- All API responses typed with interfaces
- Use `readonly` for immutable properties
- Use `as const` for literal types
- Discriminated unions over optional properties

### Tailwind CSS
- Mobile-first: base → `sm:` → `md:` → `lg:` → `xl:`
- Use design tokens from `tailwind.config.ts`
- Dark mode via `dark:` variant
- Extract `@apply` only if pattern repeats 3+ times
- Use `group` and `peer` for parent/sibling styling
- No `!important` — fix specificity instead

### Testing (Jest)
- File naming: `[name].spec.ts`
- Use `TestBed` for component tests
- Use `jest.fn()` for mocks
- Test behavior, not implementation
- Cover: happy path, edge cases, error states
- Minimum 80% coverage per file

### File Organization
```
feature/
├── feature.component.ts
├── feature.component.html
├── feature.component.spec.ts
├── feature.model.ts
├── feature.service.ts
├── feature.service.spec.ts
└── feature.routes.ts
```

## Quality Gates (Pre-Commit)

```bash
ng lint                              # ESLint
npx prettier --check .               # Formatting
npx tsc --noEmit                     # Type checking
npx jest --coverage                  # Tests with coverage
```

## Security Requirements

- Never use `bypassSecurityTrust*` without documented justification and security review
- Auth tokens in `HttpOnly` cookies — never `localStorage`
- CSRF tokens via `HttpClient` interceptor
- Validate all form inputs client-side AND server-side
- Sanitize dynamic content (Angular handles by default)
- Run `npm audit` — zero critical/high vulnerabilities
