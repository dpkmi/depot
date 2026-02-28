# Depot — OpenCode Agent & Skills Configuratie

Dit repository bevat de gedeelde AI agent en skills configuratie voor alle development teams, gebouwd voor **OpenCode** met GitHub Copilot koppeling.

Pull de `agents/setup` branch om altijd de meest recente configuratie te hebben.

## Quick Start

```bash
# 1. Clone de repo
git clone -b agents/setup <repo-url> ~/depot-agents

# 2. Ga naar je project root
cd /pad/naar/jouw-project

# 3. Symlink de configuratie (aanbevolen)
ln -s ~/depot-agents/.opencode .opencode
ln -s ~/depot-agents/opencode.json opencode.json

# Of kopieer (nadeel: handmatig updaten)
cp -r ~/depot-agents/.opencode .opencode
cp ~/depot-agents/opencode.json opencode.json
```

## Structuur

```
depot/
├── opencode.json                              # Project config (model, providers, permissions)
└── .opencode/
    ├── agents/                                # Agent definities (markdown + frontmatter)
    │   ├── orchestrator.md                    # Primary — routeert taken
    │   ├── planner.md                         # Subagent — architectuur
    │   ├── scrum-master.md                    # Subagent — tickets
    │   ├── developer-core.md                  # Subagent — C#/WinForms/VB
    │   ├── developer-angular.md               # Subagent — Angular/TS/Tailwind
    │   ├── developer-react-native.md          # Subagent — RN/Expo/StyleSheet
    │   ├── tester.md                          # Subagent — QA/Jest/xUnit
    │   ├── debugger.md                        # Subagent — root cause analysis
    │   ├── security-specialist.md             # Subagent — OWASP/security
    │   ├── code-reviewer.md                   # Subagent — code review
    │   └── ux-designer.md                     # Subagent — UI/UX design
    └── skills/                                # Herbruikbare skill instructies
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

## Agent Model Overzicht

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

## Hoe te Gebruiken

### Agents aanroepen
- **Tab** — wissel tussen primary agents (orchestrator)
- **@planner** — roep planner subagent aan
- **@developer-angular** — roep Angular developer aan
- **@security-specialist** — roep security review aan
- Etc.

### Skills gebruiken
Skills worden automatisch geladen door agents wanneer relevant, of je kunt ze expliciet aanroepen.

## Pipeline

### Feature Development
```
@planner → @ux-designer (indien UI) → @scrum-master → @developer-[team] → @tester → @security-specialist → @code-reviewer
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
- Desktop applicatie: C#, WinForms, VB.NET
- Complexe business logic
- Agent: `@developer-core`, Skill: `develop-core`

### Angular Team (2 developers)
- Angular 17+, TypeScript strict, Tailwind CSS
- Jest + `.spec.ts`, ESLint + Prettier
- Agent: `@developer-angular`, Skill: `develop-angular`

### React Native Team (1 developer)
- Expo SDK 54+, TypeScript strict
- Native CSS (StyleSheet) — GEEN Tailwind
- Jest, ESLint + Prettier
- Agent: `@developer-react-native`, Skill: `develop-react-native`

## Environment Setup

Stel API keys in als environment variables op je systeem:

```bash
# ~/.zshrc of ~/.bashrc
export ANTHROPIC_API_KEY="sk-ant-..."
export OPENAI_API_KEY="sk-..."
export GOOGLE_API_KEY="AI..."
```

## Updaten

```bash
cd ~/depot-agents
git pull origin agents/setup
# Symlinks → direct actief in alle projecten
```
