---
name: test-core
description: Use this skill to write or run unit tests for C#, VB.NET, and .NET desktop applications. Uses MSTest, NUnit, or xUnit. Do NOT use for Angular or React Native tests.
---

# Core Testing Skill

> **Delegates to:** Tester Agent (`agents/tester.md`)
> **Model:** `claude-sonnet-4-5-20250929`

## When to Invoke

- User requests C# or VB.NET tests
- User says "test", "unit test" in context of .NET files
- After Core development skill completes (pipeline)
- Test project needs new test classes

## Execution Steps

1. Identify the class/method to test
2. Read the source file completely
3. Determine test framework in use (check existing test projects)
4. Write comprehensive test class following AAA pattern
5. Mock dependencies using Moq or NSubstitute
6. Run tests: `dotnet test`
7. Check coverage if configured

## Test Template (xUnit)

```csharp
public class UserServiceTests
{
    private readonly Mock<IUserRepository> _mockRepo;
    private readonly UserService _sut;

    public UserServiceTests()
    {
        _mockRepo = new Mock<IUserRepository>();
        _sut = new UserService(_mockRepo.Object);
    }

    [Fact]
    public void GetActiveUsers_WhenUsersExist_ReturnsOnlyActive()
    {
        // Arrange
        var users = new List<User> { /* test data */ };
        _mockRepo.Setup(r => r.GetAll()).Returns(users);

        // Act
        var result = _sut.GetActiveUsers();

        // Assert
        result.Should().OnlyContain(u => u.IsActive);
    }

    [Theory]
    [InlineData(null)]
    [InlineData("")]
    public void GetUser_WithInvalidId_ThrowsArgumentException(string id)
    {
        // Arrange & Act & Assert
        Assert.Throws<ArgumentException>(() => _sut.GetUser(id));
    }
}
```

## Coverage Requirements

- Business logic: 90%+
- Data access: 85%+
- Utilities: 95%+
