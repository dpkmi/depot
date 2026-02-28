# Core Team Agent Configuration

> **Team:** Core Desktop Application
> **Stack:** C# (.NET), WinForms, VB.NET

## Working Agreements

- All code must compile without warnings before committing
- Use `dotnet build` to verify compilation
- Use `dotnet test` to run all unit tests
- Never commit `.designer.cs` changes without verifying the form renders correctly
- All public methods require XML documentation comments
- NuGet packages must be approved before adding to production projects

## Code Standards

### C# Conventions
- Use file-scoped namespaces (C# 10+) where the project supports it
- Use `var` when the type is obvious from the right side of the assignment
- Private fields: `_camelCase`
- Methods and properties: `PascalCase`
- Interfaces: `IPrefix`
- Always use braces for control flow, even single-line

### VB.NET Conventions
- Maintain existing VB.NET style — do not introduce C# idioms
- Use `Option Strict On` and `Option Explicit On`
- Follow existing naming patterns in the file

### WinForms
- Never perform long operations on the UI thread
- Use `async/await` with `ConfigureAwait(true)` for UI continuations
- Handle `FormClosing` for cleanup
- Use `ErrorProvider` for form validation
- Anchor/Dock controls for resizable forms

## Project Structure

```
Solution.sln
├── ProjectName/                    # Main application
│   ├── Forms/                      # WinForms UI
│   ├── Services/                   # Business logic
│   ├── Repositories/               # Data access
│   ├── Models/                     # Domain models
│   └── Helpers/                    # Utility classes
├── ProjectName.Tests/              # Unit tests
└── ProjectName.Common/             # Shared libraries
```

## Security Requirements

- No hardcoded connection strings — use app.config with encryption
- All database queries must use parameterized queries
- Sensitive data must use `SecureString` in memory
- Log files must not contain PII or credentials
- File operations must validate paths against directory traversal

## Before Committing Checklist

- [ ] `dotnet build` passes
- [ ] `dotnet test` passes
- [ ] No TODO comments without ticket reference
- [ ] XML docs on public members
- [ ] No hardcoded strings (use resources)
- [ ] No compiler warnings
