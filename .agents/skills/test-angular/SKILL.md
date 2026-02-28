---
name: test-angular
description: Use this skill to write or run Jest tests for Angular components, services, and pipes. Creates .spec.ts files. Do NOT use for React Native or C# tests.
---

# Angular Testing Skill

> **Delegates to:** Tester Agent (`agents/tester.md`)
> **Model:** `claude-sonnet-4-5-20250929`

## When to Invoke

- User requests Angular tests
- User says "test", "spec", "coverage" in context of Angular files
- After Angular development skill completes (pipeline)
- `.spec.ts` file needs to be created or updated

## Execution Steps

1. Identify the component/service/pipe to test
2. Read the source file completely
3. Write comprehensive `.spec.ts` file using Jest
4. Configure `TestBed` with required providers and imports
5. Test happy path, edge cases, error scenarios
6. Run tests: `npx jest [file]`
7. Check coverage: `npx jest --coverage [file]`
8. Verify lint: `ng lint`

## Test Template

```typescript
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { MyComponent } from './my.component';

describe('MyComponent', () => {
  let component: MyComponent;
  let fixture: ComponentFixture<MyComponent>;

  beforeEach(async () => {
    await TestBed.configureTestingModule({
      imports: [MyComponent], // standalone
    }).compileComponents();

    fixture = TestBed.createComponent(MyComponent);
    component = fixture.componentInstance;
    fixture.detectChanges();
  });

  it('should create', () => {
    expect(component).toBeTruthy();
  });

  // Happy path tests
  // Edge case tests
  // Error scenario tests
});
```

## Coverage Requirements

- Business logic: 90%+
- Components: 80%+
- Utilities: 95%+
