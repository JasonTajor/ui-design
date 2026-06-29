# Design System — Claude Code Marketplace

A Git-based Claude Code marketplace. This repo **is** the package manager: install
the plugin straight from GitHub, no npm required.

```
your-repo/
├── .claude-plugin/
│   └── marketplace.json        ← the catalog (points at ./design-system)
└── design-system/              ← the plugin
    ├── .claude-plugin/plugin.json
    ├── skills/design-system/   ← source of truth (tokens, standards, patterns)
    ├── agents/                 ← orchestrator, ui-ux, frontend, qa, guardian
    ├── commands/               ← /dashboard, /review
    └── templates/CLAUDE.md
```

## Install (from GitHub)

In any project, inside Claude Code:

```
/plugin marketplace add YOUR_USERNAME/YOUR_REPO
/plugin install design-system@design-system-marketplace
/reload-plugins
```

Then use it anywhere:

- `/dashboard an e-commerce analytics dashboard` — plan → design → build → QA
- `/review` — audit current UI against the system
- or just describe the work; the agents trigger themselves.

## Update everything in one place

The agents read the `design-system` skill — they hardcode nothing. Edit a token or
standard, bump `design-system/.claude-plugin/plugin.json`'s `version`, commit, and
every project re-runs `/plugin marketplace update design-system-marketplace` to
pull the change. One edit, all projects.

## Local install (before pushing)

```
/plugin marketplace add /path/to/this/repo
/plugin install design-system@design-system-marketplace
/reload-plugins
```
