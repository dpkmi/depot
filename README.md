# Depot — OpenCode Agent & Skills Configuration

This repository contains the shared AI agent and skills configuration for all development teams, built for **OpenCode** with GitHub Copilot integration.

Pull the `agents/setup` branch to always have the latest configuration.

## Quick Start

```bash
# 1. Clone the repo
git clone -b agents/setup <repo-url> ~/depot-agents

# 2. Navigate to your project root
cd /path/to/your/project

# 3. Symlink the configuration (recommended)
ln -s ~/depot-agents/.opencode .opencode
ln -s ~/depot-agents/opencode.json opencode.json

# Or copy (downside: manual updates required)
cp -r ~/depot-agents/.opencode .opencode
cp ~/depot-agents/opencode.json opencode.json
```

## Structure

```
depot/
├── opencode.json                              # Project config (model, providers, permissions)
└── .opencode/
    ├── agents/                                # Agent definitions (markdown + frontmatter)
    │   ├── orchestrator.md                    # Primary — routes tasks
    │   ├── planner.md                         # Subagent — architecture
    │   ├── scrum-master.md                    # Subagent — ticket breakdown
    │   ├── developer-core.md                  # Subagent — C#/WinForms/VB
    │   ├── developer-angular.md               # Subagent — Angular/TS/Tailwind
    │   ├── developer-react-native.md          # Subagent — RN/Expo/StyleSheet
    │   ├── tester.md                          # Subagent — QA/Jest/xUnit
    │   ├── debugger.md                        # Subagent — root cause analysis
    │   ├── security-specialist.md             # Subagent — OWASP/security
    │   ├── code-reviewer.md                   # Subagent — code review
    │   └── ux-designer.md                     # Subagent — UI/UX design
    └── skills/                                # Reusable skill instructions
        ├── plan/SKILL.md
        ├── develop-core/SKILL.md
        ├── develop-angular/SKILL.md
        ├── develop-react-native/SKILL.md
        ├── test-angular/SKILL.md
        ├── test-core/SKILL.md
        ├── test-react-native/SKILL.md
        ├── scrum-breakdown/SKILL.md
        ├── security-audit/SKILL.md
        ├── debug/SKILL.md
        ├── code-review/SKILL.md
        └── ux-design/SKILL.md
```

## Agent Overview

| Agent | Mode | Model | Temp | Tools |
|-------|------|-------|------|-------|
| **Orchestrator** | primary | `anthropic/claude-haiku-4-5` | 0.1 | task, question, skill |
| **Planner** | subagent | `anthropic/claude-opus-4-6` | 0.2 | read, grep, glob, webfetch |
| **Scrum Master** | subagent | `anthropic/claude-haiku-4-5` | 0.1 | read, todowrite |
| **Developer Core** | subagent | `anthropic/claude-opus-4-6` | 0.1 | read, write, edit, bash |
| **Developer Angular** | subagent | `anthropic/claude-opus-4-6` | 0.1 | read, write, edit, bash |
| **Developer RN** | subagent | `anthropic/claude-opus-4-6` | 0.1 | read, write, edit, bash |
| **Tester** | subagent | `anthropic/claude-sonnet-4-5` | 0.1 | read, write, edit, bash |
| **Debugger** | subagent | `openai/chatgpt-codex-5.2-xhigh` | 0.15 | read, bash, grep, lsp |
| **Security** | subagent | `anthropic/claude-opus-4-6` | 0.1 | read, bash, grep, webfetch |
| **Code Reviewer** | subagent | `anthropic/claude-sonnet-4-5` | 0.15 | read, grep, glob |
| **UX Designer** | subagent | `google/gemini-3.2` | 0.8 | read, webfetch, websearch |

## Usage

### Invoking Agents
- **Tab** — switch between primary agents (orchestrator)
- **@planner** — invoke the planner subagent
- **@developer-angular** — invoke the Angular developer
- **@security-specialist** — invoke a security review
- etc.

### Using Skills
Skills are automatically loaded by agents when relevant. Each agent has explicit skill access permissions defined in its frontmatter.

## Pipeline

### Feature Development
```
@planner → @ux-designer (if UI) → @scrum-master → @developer-[team] → @tester → @security-specialist → @code-reviewer
```

### Bug Fix
```
@debugger → @developer-[team] → @tester
```

### Security Audit
```
@security-specialist (standalone)
```

## Teams

### Core Team
- Desktop application: C#, WinForms, VB.NET
- Complex business logic
- Agent: `@developer-core`, Skill: `develop-core`

### Angular Team (2 developers)
- Angular 17+, TypeScript strict, Tailwind CSS
- Jest + `.spec.ts`, ESLint + Prettier
- Agent: `@developer-angular`, Skill: `develop-angular`

### React Native Team (1 developer)
- Expo SDK 54+, TypeScript strict
- Native CSS (StyleSheet) — no Tailwind
- Jest, ESLint + Prettier
- Agent: `@developer-react-native`, Skill: `develop-react-native`

## Environment Setup

Set API keys as environment variables on your system:

```bash
# ~/.zshrc or ~/.bashrc
export ANTHROPIC_API_KEY="sk-ant-..."
export OPENAI_API_KEY="sk-..."
export GOOGLE_API_KEY="AI..."
```

## Updating

```bash
cd ~/depot-agents
git pull origin agents/setup
# Symlinks → immediately active in all projects
```
