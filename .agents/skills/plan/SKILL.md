---
name: plan
description: Use this skill when a user requests feature planning, architecture design, technical specification, or implementation strategy. Do NOT use for sprint/ticket breakdown (use scrum-breakdown instead) or for direct coding tasks.
---

# Planning Skill

> **Delegates to:** Planner Agent (`agents/planner.md`)
> **Model:** `claude-opus-4-6`

## When to Invoke

- User says "plan", "design", "architect", "how should we build", "technical approach"
- User provides a feature request or user story that needs technical analysis
- User asks about impact analysis or risk assessment

## Execution Steps

1. Read the full requirement from the user
2. Identify which teams are affected (Core, Angular, React Native)
3. Analyze the existing codebase for relevant files and patterns
4. Produce a complete implementation plan following the Planner Agent output format
5. Include risk assessment and acceptance criteria
6. Suggest ticket breakdown for the Scrum Master agent

## Context to Provide

- Project structure and existing patterns
- Current tech stack versions
- Related existing functionality
- Known constraints and dependencies

## Output

A structured implementation plan ready for the Scrum Master to break into tickets. See `agents/planner.md` for the full output format.
