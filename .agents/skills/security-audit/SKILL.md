---
name: security-audit
description: Use this skill for security reviews, vulnerability scanning, OWASP compliance checks, and dependency audits. Use for any code that handles authentication, authorization, user input, or sensitive data.
---

# Security Audit Skill

> **Delegates to:** Security Specialist Agent (`agents/security-specialist.md`)
> **Model:** `claude-opus-4-6`

## When to Invoke

- User says "security review", "vulnerability", "audit", "OWASP"
- Code changes involve authentication, authorization, or session management
- Code handles user input, file uploads, or database queries
- New dependencies are added to the project
- Before merging security-sensitive PRs
- Automatically invoked at end of development pipeline for sensitive changes

## Execution Steps

1. Read all modified files
2. Run OWASP Top 10 checklist against the code
3. Check for stack-specific vulnerabilities (C#, Angular, React Native)
4. Audit dependencies for known CVEs:
   - .NET: `dotnet list package --vulnerable`
   - Angular: `npm audit`
   - React Native: `npm audit` / `npx expo doctor`
5. Classify findings by severity
6. Provide specific remediation for each finding
7. Issue verdict: APPROVED, APPROVED WITH CONDITIONS, or BLOCKED

## Auto-Trigger Conditions

This skill should be automatically invoked when changes touch:
- Authentication / login / session code
- Authorization / role / permission code
- Database queries or ORM configurations
- API endpoint definitions
- File upload or download handlers
- Cryptographic operations
- User input processing
