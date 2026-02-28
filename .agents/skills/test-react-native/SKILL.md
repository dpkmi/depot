---
name: test-react-native
description: Use this skill to write or run Jest tests for React Native / Expo components and hooks. Uses React Native Testing Library. Do NOT use for Angular or C# tests.
---

# React Native Testing Skill

> **Delegates to:** Tester Agent (`agents/tester.md`)
> **Model:** `claude-sonnet-4-5-20250929`

## When to Invoke

- User requests React Native or Expo tests
- User says "test" in context of `.tsx` files in an Expo project
- After React Native development skill completes (pipeline)
- Test file needs to be created or updated

## Execution Steps

1. Identify the component/hook/service to test
2. Read the source file completely
3. Write comprehensive test file using Jest + React Native Testing Library
4. Mock navigation, native modules, and external services
5. Test renders, interactions, and state changes
6. Run tests: `npx jest [file]`
7. Check coverage: `npx jest --coverage [file]`

## Test Template

```typescript
import React from 'react';
import { render, fireEvent, waitFor } from '@testing-library/react-native';
import { LoginScreen } from '../LoginScreen';

// Mock navigation
const mockNavigate = jest.fn();
jest.mock('expo-router', () => ({
  useRouter: () => ({ navigate: mockNavigate }),
}));

describe('LoginScreen', () => {
  beforeEach(() => {
    jest.clearAllMocks();
  });

  it('renders email and password fields', () => {
    const { getByPlaceholderText } = render(<LoginScreen />);
    expect(getByPlaceholderText('Email')).toBeTruthy();
    expect(getByPlaceholderText('Password')).toBeTruthy();
  });

  it('shows error when submitting empty form', async () => {
    const { getByText, getByTestId } = render(<LoginScreen />);
    fireEvent.press(getByText('Sign In'));
    await waitFor(() => {
      expect(getByTestId('error-message')).toBeTruthy();
    });
  });
});
```

## Coverage Requirements

- Screens: 80%+
- Components: 80%+
- Hooks/Services: 90%+
- Utilities: 95%+
