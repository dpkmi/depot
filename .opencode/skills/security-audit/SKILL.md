---
name: security-audit
description: OWASP Top 10 security review, vulnerability scanning, and dependency auditing. Use for any code handling auth, user input, database queries, or sensitive data.
compatibility: opencode
---

## When to Use
- Security review requests
- Code touching auth, authorization, sessions
- User input handling, file uploads, database queries
- New dependencies added
- Before merging security-sensitive PRs

## OWASP Top 10 Check
A01 Broken Access Control, A02 Crypto Failures, A03 Injection,
A04 Insecure Design, A05 Misconfiguration, A06 Vulnerable Components,
A07 Auth Failures, A08 Data Integrity, A09 Logging Failures, A10 SSRF

## Dependency Audit Commands
- .NET: `dotnet list package --vulnerable`
- Angular: `npm audit`
- React Native: `npm audit` + `npx expo doctor`

## Severity → Response
- Critical/High: BLOCK merge
- Medium: Fix within sprint
- Low: Track in backlog
