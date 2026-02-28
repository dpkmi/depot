---
name: develop-core
description: C# / WinForms / VB.NET desktop application development following Core team standards. Use for .cs, .vb, .csproj, .sln files. Do NOT use for Angular or React Native.
compatibility: opencode
---

## When to Use
- C#, VB.NET, or WinForms code changes
- Files: `.cs`, `.vb`, `.resx`, `.csproj`, `.sln`, `.designer.cs`
- Desktop application work

## Standards
- PascalCase methods, `_camelCase` private fields, `I` prefix interfaces
- Separate logic from UI, async/await for I/O, IDisposable for resources
- Never block UI thread, use Invoke for cross-thread updates
- Parameterized SQL only, SecureString for credentials
- XML docs on public members

## Post-Checks
- `dotnet build` passes
- No hardcoded credentials
- Proper resource disposal
- Thread safety verified
