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

## Tokens in code — `tokens.css`

[`tokens.css`](./tokens.css) is the **single source of truth, in code**: all design
tokens as CSS custom properties for light and dark (`:root` + `[data-theme="dark"]`).
This is the one file you edit to change the system.

Use it in any web project — no build, no npm:

```html
<link rel="stylesheet" href="tokens.css">
```

```css
/* then style with semantic tokens only — never raw hex */
.btn { background: var(--color-primary); color: var(--color-on-accent); }
.card { background: var(--color-surface); border: 1px solid var(--color-border);
        border-radius: var(--radius-lg); padding: var(--space-5); }
```

Toggle themes by setting `data-theme="dark"` on `<html>`.

**How it stays in sync:** `tokens.css` is the code; the markdown under
`design-system/skills/design-system/references/standards/` is the rationale (the
"why" behind each value). The Claude Code agents read that markdown. When you change
a value, edit `tokens.css` and update the matching standards doc, then commit both.

## Live showcase

[`showcase.html`](./showcase.html) renders the whole system live — every token,
primitive, component, and page pattern, in **light and dark**, with controls to
retune the primary/secondary colors and corner radius on the fly. It `<link>`s
`tokens.css`, so it reflects whatever is in that file.

**Preview it** — open it in any browser (no server, no build):

```
file:///C:/design/design-system-repo/showcase.html
```

or double-click `showcase.html` in the repo.

**Update it** — edit [`tokens.css`](./tokens.css) and refresh the browser. The
showcase (and every project that links `tokens.css`) updates from that one edit.

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
