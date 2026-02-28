---
name: test-core
description: Write and run unit tests for C# / .NET using MSTest, NUnit, or xUnit with Moq. Do NOT use for Angular or React Native tests.
compatibility: opencode
---

## When to Use
- C# / VB.NET test writing or running
- After Core development completes
- Test project needs new classes

## Standards
- Match existing framework (MSTest/NUnit/xUnit)
- Moq or NSubstitute for mocking, FluentAssertions preferred
- File naming: `[ClassName]Tests.cs`
- AAA pattern, descriptive test names
- Minimum 85% data access, 90% business logic, 95% utilities

## Run Command
- `dotnet test` — run all tests
