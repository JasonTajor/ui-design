# Design System — Claude Code Marketplace

A Git-based [Claude Code](https://docs.claude.com/en/docs/claude-code) marketplace.
This repo **is** the package manager: install the plugin straight from GitHub, no
npm required.

```
ui-design/
├── .claude-plugin/
│   └── marketplace.json        ← the catalog (points at ./design-system)
└── design-system/              ← the plugin
    ├── .claude-plugin/plugin.json
    ├── skills/design-system/   ← source of truth (tokens, standards, patterns)
    ├── agents/                 ← orchestrator, ui-ux, frontend, qa, guardian
    ├── commands/               ← /dashboard, /review
    └── templates/CLAUDE.md
```

## Install as a Claude Code package

You need [Claude Code](https://docs.claude.com/en/docs/claude-code) installed. Then,
inside Claude Code in **any** project, run these three slash commands:

```text
/plugin marketplace add JasonTajor/ui-design
/plugin install design-system@design-system-marketplace
/reload-plugins
```

What each step does:

| Command | What it does |
| --- | --- |
| `/plugin marketplace add JasonTajor/ui-design` | Registers this GitHub repo as a plugin marketplace (clones it locally). |
| `/plugin install design-system@design-system-marketplace` | Installs the `design-system` plugin from the `design-system-marketplace` catalog. |
| `/reload-plugins` | Activates the plugin's skills, agents, and commands in the current session. |

> The format is `<plugin-name>@<marketplace-name>`, i.e.
> `design-system@design-system-marketplace`.

### Verify it installed

```text
/plugin
```

You should see **design-system** listed as installed, and `/dashboard` and `/review`
available as commands.

## Use it

Once installed, use it anywhere:

- `/dashboard an e-commerce analytics dashboard` — plan → design → build → QA
- `/review` — audit the current UI against the system
- or just describe the work; the agents trigger themselves.

## Live showcase

[`showcase.html`](./showcase.html) is a single self-contained file that renders the
whole system live — every token, primitive, component, and page pattern, in **light
and dark**, with controls to retune the primary/secondary colors and corner radius
on the fly.

**Preview it** — just open the file in any browser (no server, no build):

```
file:///C:/design/design-system-repo/showcase.html
```

or double-click `showcase.html` in the repo.

**Update it** — the page is driven by the same tokens defined in
`design-system/skills/design-system/`. When you change a standard there (a color, a
radius, spacing), mirror the change in the `:root` / `[data-theme="dark"]` token
block at the top of `showcase.html`, then refresh the browser. Commit both so the
showcase always matches the system.

## Update everything in one place

The agents read the `design-system` skill — they hardcode nothing. Edit a token or
standard, bump the `version` in `design-system/.claude-plugin/plugin.json`, commit,
and push. Every project then pulls the change with:

```text
/plugin marketplace update design-system-marketplace
```

One edit, all projects.

## Local install (before pushing changes)

To test changes against a local checkout instead of GitHub:

```text
/plugin marketplace add /path/to/this/repo
/plugin install design-system@design-system-marketplace
/reload-plugins
```

## Uninstall

```text
/plugin uninstall design-system@design-system-marketplace
/plugin marketplace remove design-system-marketplace
```

## License

MIT
