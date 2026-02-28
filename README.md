# Depot — AI Agent & Skills Configuration

Dit repository bevat de gedeelde AI agent configuratie en skills voor alle development teams. Pull deze branch om altijd de meest recente agent-configuratie op je systeem te hebben.

## Quick Start

```bash
# Clone of pull de agents/setup branch
git clone -b agents/setup <repo-url> .agents-config

# Kopieer naar je project root (of symlink)
cp -r .agents-config/.agents /pad/naar/je/project/
cp .agents-config/AGENTS.md /pad/naar/je/project/
cp -r .agents-config/agents/ /pad/naar/je/project/

# Of gebruik een symlink (aanbevolen — altijd up to date)
ln -s /pad/naar/.agents-config/.agents /pad/naar/je/project/.agents
ln -s /pad/naar/.agents-config/AGENTS.md /pad/naar/je/project/AGENTS.md
ln -s /pad/naar/.agents-config/agents /pad/naar/je/project/agents
```

## Structuur

```
depot/
├── AGENTS.md                              # Orchestrator (Haiku 4.5)
├── agents/                                # Sub-agent definities
│   ├── planner.md                         # Opus 4.6
│   ├── scrum-master.md                    # Haiku 4.5
│   ├── developer-core.md                  # Opus 4.6
│   ├── developer-angular.md               # Opus 4.6
│   ├── developer-react-native.md          # Opus 4.6
│   ├── tester.md                          # Sonnet 4.5
│   ├── debugger.md                        # ChatGPT Codex 5.2 xHigh
│   ├── security-specialist.md             # Opus 4.6
│   ├── code-reviewer.md                   # Sonnet 4.5
│   └── ux-designer.md                     # Gemini 3.2
├── .agents/
│   └── skills/                            # Invokable skills
│       ├── plan/                          # Feature planning
│       ├── develop-core/                  # C# / WinForms / VB.NET
│       ├── develop-angular/               # Angular / TypeScript / Tailwind
│       ├── develop-react-native/          # React Native / Expo
│       ├── test-angular/                  # Jest tests voor Angular
│       ├── test-core/                     # Unit tests voor .NET
│       ├── test-react-native/             # Jest tests voor React Native
│       ├── scrum-breakdown/               # Ticket breakdown
│       ├── security-audit/                # Security review
│       ├── debug/                         # Bug investigation
│       ├── code-review/                   # Code review
│       └── ux-design/                     # UI/UX design (Gemini 3.2)
├── core/
│   └── AGENTS.md                          # Core team regels
└── frontend/
    ├── angular/
    │   └── AGENTS.md                      # Angular team regels
    └── react-native/
        └── AGENTS.md                      # React Native team regels
```

## Agent Model Overzicht

| Agent | Model | Waarom |
|-------|-------|--------|
| **Orchestrator** | Claude Haiku 4.5 | Snel, goedkoop, hoeft alleen te routeren |
| **Planner** | Claude Opus 4.6 | Diep redeneren voor architectuur |
| **Scrum Master** | Claude Haiku 4.5 | Simpele taken: tickets opsplitsen |
| **Developer (alle)** | Claude Opus 4.6 | Beste codeerkwaliteit |
| **Tester** | Claude Sonnet 4.5 | Goede balans kwaliteit/snelheid |
| **Debugger** | ChatGPT Codex 5.2 xHigh | Gespecialiseerd in code analyse |
| **Security** | Claude Opus 4.6 | Diepgaande security analyse nodig |
| **Code Reviewer** | Claude Sonnet 4.5 | Goede balans voor review |
| **UX Designer** | Gemini 3.2 | Multimodaal, kan designs analyseren en web researchen |

## Pipeline

### Feature Development
```
Planner → UX Designer (indien UI) → Scrum Master → Developer → Tester → Security → Code Review
```

### Bug Fix
```
Debugger → Developer → Tester
```

### Security Audit
```
Security Specialist (standalone)
```

## Teams

### Core Team
- Desktop applicatie: C#, WinForms, VB.NET
- Complexe business logic
- Zie `core/AGENTS.md` voor team-specifieke regels

### Angular Team (2 developers)
- TypeScript strict mode
- Tailwind CSS
- Jest + .spec.ts bestanden
- ESLint + Prettier
- Zie `frontend/angular/AGENTS.md`

### React Native Team (1 developer)
- Expo SDK 54+
- TypeScript strict mode
- Native CSS (StyleSheet) — GEEN Tailwind
- Jest
- ESLint + Prettier
- Zie `frontend/react-native/AGENTS.md`

## Updaten

```bash
# Pull de laatste versie
git pull origin agents/setup

# Klaar — als je symlinks gebruikt zijn alle projecten direct bijgewerkt
```

## Aanpassen

Om team-specifieke overrides toe te voegen, maak een `AGENTS.override.md` in de betreffende directory. Dit overschrijft de standaard `AGENTS.md` regels voor die scope.
