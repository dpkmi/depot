# React Native Team Agent Configuration

> **Team:** Frontend — React Native
> **Stack:** React Native, Expo SDK 54+, TypeScript (strict), Native CSS
> **Developers:** 1

## Working Agreements

- All code must pass `npx expo lint` before committing
- All code must pass `npx prettier --check .` before committing
- Every screen and reusable component must have a `.test.tsx` file
- No `any` types — strict TypeScript only
- Styling via `StyleSheet.create()` only — NO Tailwind, NO inline styles
- Expo SDK 54+ — no deprecated APIs
- Functional components only — no class components

## Code Standards

### Components
- Functional components with TypeScript
- Props defined as explicit interfaces (not inline)
- Use custom hooks for reusable logic
- Use `React.memo()` for components receiving complex props
- Use `useCallback` for handlers passed to children
- Use `useMemo` for expensive computations

### TypeScript
- `strict: true` in `tsconfig.json`
- No `any` — type everything
- Navigation params typed via Expo Router
- API responses typed with interfaces
- Use `readonly` for immutable state shapes

### Styling
```typescript
// CORRECT — always use StyleSheet.create
const styles = StyleSheet.create({
  container: {
    flex: 1,
    padding: 16,
    backgroundColor: colors.background,
  },
});

// WRONG — no inline styles
<View style={{ flex: 1, padding: 16 }} />

// WRONG — no Tailwind
<View className="flex-1 p-4" />
```

- Design tokens in a shared `constants/` directory
- Platform-specific styles via `Platform.select()` or `.ios.ts` / `.android.ts`
- Use `useSafeAreaInsets()` for safe area handling
- Minimum touch target: 44x44 points

### Navigation (Expo Router)
- File-based routing in `app/` directory
- Type-safe navigation params
- Deep linking configuration in `app.json`
- Use `<Stack>`, `<Tabs>`, `<Drawer>` layout components

### Testing (Jest)
- File naming: `[Component].test.tsx` or `__tests__/[Component].test.tsx`
- Use React Native Testing Library
- Mock navigation, native modules, and async storage
- Test renders, interactions, and state
- Minimum 80% coverage

### File Organization
```
features/
├── auth/
│   ├── screens/
│   │   └── LoginScreen.tsx
│   ├── components/
│   │   └── LoginForm.tsx
│   ├── hooks/
│   │   └── useAuth.ts
│   ├── services/
│   │   └── auth.service.ts
│   ├── types/
│   │   └── auth.types.ts
│   └── __tests__/
│       ├── LoginScreen.test.tsx
│       └── useAuth.test.ts
```

## Quality Gates (Pre-Commit)

```bash
npx expo lint                        # ESLint
npx prettier --check .               # Formatting
npx tsc --noEmit                     # Type checking
npx jest --coverage                  # Tests with coverage
npx expo doctor                      # Expo compatibility check
```

## Security Requirements

- Tokens stored in `expo-secure-store` — never `AsyncStorage`
- HTTPS only for all API calls
- Certificate pinning for production builds
- Deep link parameters validated before processing
- No sensitive data in logs or error messages
- Request minimum permissions with clear purpose descriptions
- Use `expo-local-authentication` for biometric auth
