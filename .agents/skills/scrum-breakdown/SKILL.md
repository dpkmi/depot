---
name: scrum-breakdown
description: Use this skill to break down features, plans, or requirements into sprint-ready tickets with story points and dependencies. Do NOT use for technical planning (use plan instead) or for writing code.
---

# Scrum Breakdown Skill

> **Delegates to:** Scrum Master Agent (`agents/scrum-master.md`)
> **Model:** `claude-haiku-4-5-20251001`

## When to Invoke

- User says "break down", "tickets", "sprint planning", "backlog", "story points"
- After the Planning skill produces an implementation plan
- User provides a feature that needs to be split into tasks
- User asks about sprint capacity or task estimation

## Execution Steps

1. Read the implementation plan or feature description
2. Identify all teams involved (Core, Angular, React Native)
3. Break into atomic tickets (max 8 story points each)
4. Map dependencies between tickets
5. Assign story points using Fibonacci scale
6. Group into suggested sprints based on team capacity
7. Write acceptance criteria for each ticket

## Capacity Reference

- Core team: ~20 SP / sprint
- Angular (2 devs): ~30 SP / sprint
- React Native (1 dev): ~15 SP / sprint

## Output

Structured tickets following the template in `agents/scrum-master.md`. Each ticket includes team assignment, story points, dependencies, acceptance criteria, and definition of done.
