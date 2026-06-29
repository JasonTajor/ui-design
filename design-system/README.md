# Design System — Claude Code Plugin

Install once, call it from any project. This plugin bundles a **design-system
skill** (the single source of truth) and a **team of agents** that design, build,
and QA UIs to it — so updating the one skill updates how everything gets built.

## What's inside

```
design-system/
├── .claude-plugin/
│   ├── plugin.json            plugin manifest
│   └── marketplace.json       so you can install it with one command
├── skills/
│   └── design-system/         THE SOURCE OF TRUTH
│       ├── SKILL.md           lean entry point + build/review workflows
│       └── references/
│           ├── standards/     colors · spacing (8pt) · typography (Inter) ·
│           │                  radius · motion · icons (HugeIcons) · responsive
│           ├── components/     button, card, … (+ template)
│           ├── templates/      dashboard, landing, … (+ template)
│           └── review-checklist.md
├── agents/
│   ├── design-orchestrator.md  plans the work, sequences the team
│   ├── ui-ux-designer.md       layout, IA, aesthetic → spec
│   ├── frontend-engineer.md    builds in code, mobile-first
│   ├── qa-reviewer.md          audits system + responsive + a11y (read-only)
│   └── design-system-guardian.md  maintains the primitives
├── commands/
│   ├── dashboard.md            /dashboard — build end-to-end
│   └── review.md               /review — audit current UI
├── templates/CLAUDE.md         copy into a repo for always-on laws
└── README.md
```

## Install — Claude Code

From the folder that contains this plugin (or its git repo):

```
/plugin marketplace add ./design-system        # add the bundled marketplace
/plugin install design-system@design-system-marketplace
/reload-plugins
```

(For team-wide use, push this folder to a git repo and
`/plugin marketplace add your-org/your-repo`.)

Then, in any project:

- `/dashboard an analytics dashboard for sales` → plans, designs, builds, and QAs
  it end-to-end on the system.
- `/review` → audits the current UI for token/8pt/responsive/a11y/state issues.
- Or just describe the work — the agents trigger themselves from their descriptions.

Optionally copy `templates/CLAUDE.md` into your repo root for always-on rules.

## Install — Claude apps (Cowork / desktop)

The apps use Skills (not agents/commands). Install the packaged
`design-system.skill` via the Skills menu — you get the same standards and the
build/review workflows, invoked directly.

## Updating everything in one place

The agents don't hardcode design rules — they read `skills/design-system`. Change
a token or standard there, bump `plugin.json`'s `version`, and every project that
installed the plugin picks up the change on its next update. One edit, all projects.

## The team at a glance

Orchestrator plans → Designer specs the layout/aesthetic → Engineer builds it
mobile-first with tokens → QA audits compliance, responsiveness, and accessibility
→ Guardian keeps the primitives clean. All grounded in one skill.
EOF
