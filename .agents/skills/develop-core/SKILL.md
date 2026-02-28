---
name: develop-core
description: Use this skill for C#, WinForms, VB.NET, or .NET desktop application development tasks. Do NOT use for Angular, React Native, or web frontend work.
---

# Core Development Skill

> **Delegates to:** Developer Core Agent (`agents/developer-core.md`)
> **Model:** `claude-opus-4-6`

## When to Invoke

- User requests C#, VB.NET, or WinForms code changes
- File extensions: `.cs`, `.vb`, `.resx`, `.csproj`, `.sln`, `.designer.cs`
- Working directory is within a .NET project structure
- User mentions "desktop app", "WinForms", "Core team"

## Execution Steps

1. Read the implementation plan or ticket description
2. Analyze existing code structure, namespaces, and patterns
3. Implement the required changes following Core team coding standards
4. Ensure thread safety for any UI-related code
5. Add XML documentation for public members
6. Verify the solution builds: `dotnet build`

## Pre-Flight Checks

- [ ] Read all files that will be modified
- [ ] Understand the existing namespace and project structure
- [ ] Identify the .NET version in use (Framework vs .NET 8+)
- [ ] Check for existing patterns (DI, Repository, etc.)

## Post-Flight Checks

- [ ] Code compiles without errors
- [ ] No warnings introduced
- [ ] XML documentation on public members
- [ ] No hardcoded credentials or connection strings
- [ ] Proper resource disposal
