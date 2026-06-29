---
name: design-system
description: >-
  The single source of truth for this project's UI: design tokens (spacing,
  typography, color, radius, motion, icons), the reusable component library, page
  templates (dashboard, landing page, CRM, admin, auth, settings), plus the
  workflows for building features and reviewing UI against the system. Use this
  skill whenever building, fixing, refactoring, or reviewing any front-end UI,
  dashboard, landing page, component, or layout — even if the user doesn't say
  "design system." Use it before writing any styling, choosing any spacing or
  color value, creating any component, or scaffolding any page, to make sure
  everything stays token-driven and consistent.
---

# Design System

This skill keeps every UI consistent, token-driven, and free of duplicate
components. The body below is the table of contents. Read only the reference
files a given task needs — they stay on disk (zero context cost) until you read them.

**Tokens in code:** the canonical token values live as CSS custom properties in
`tokens.css` at the repo root. The `references/standards/` docs below explain the
*why*; `tokens.css` is the *what* a project actually consumes
(`<link rel="stylesheet" href="tokens.css">`, then `var(--…)`). When a token value
changes, update both the standards doc and `tokens.css`.

## The one rule that overrides everything

If you discover the design system is broken or missing a needed token/primitive,
**fix the system first, then build the feature.** A correct feature on a broken
primitive is still broken. See `references/standards/` for token definitions.

## Where to look (read on demand)

| You are about to... | Read first |
|---|---|
| Choose spacing/padding/gap | `references/standards/spacing.md` |
| Choose a font size or text style | `references/standards/typography.md` |
| Choose a color | `references/standards/colors.md` |
| Round a corner | `references/standards/radius.md` |
| Add a transition/animation | `references/standards/motion.md` |
| Add an icon | `references/standards/icons.md` |
| Build/modify a known component | `references/components/<name>.md` + the real source file |
| Create a *new* component | `references/components/_component-template.md` |
| Scaffold a page (dashboard, landing…) | `references/templates/<type>.md` |
| Make it work on every device | `references/standards/responsive.md` |
| Review finished UI | `references/review-checklist.md` |

## Build workflow (Feature Builder)

Follow these steps in order. Do not jump straight to writing code.

1. **Understand the request.** Restate what's being built in one sentence.
2. **Analyze existing code.** Search for components, tokens, and patterns that
   already solve part of this. Read the real source, not just the spec.
3. **Reuse first.** Prefer an existing primitive. Compose, don't recreate.
4. **Update the system if needed.** Missing token or primitive? Fix it here
   first (and note it), per the rule above. Never inline an arbitrary value as a
   shortcut.
5. **Implement.** Build the feature using tokens and existing components only.
6. **Self-review.** Run through `references/review-checklist.md` before declaring done.
7. **Deliver.** Summarize what you built, which tokens/components you used, and
   anything you added to the system.

## Review workflow (Quality Reviewer)

Audit UI against `references/review-checklist.md`. Report findings as a list of
issues, each with: location, the rule it violates, and the fix. **Reviewing does
not change code** — produce the report; let the builder apply fixes.

## Guardian workflow (Design System Guardian)

Scan for system-level violations: arbitrary values that should be tokens,
duplicate components, drift between a component's source and its spec. Fix at the
primitive layer, then report what changed and what now needs to adopt the fix.

## Authoring new reference files

New component or template docs must follow the templates in `references/`
(`_component-template.md`, `_template-template.md`) so the library stays uniform.
Document *why and what rules*; point to the code for *the exact API*.

## This skill ships with a team (plugin)
This skill is the single source of truth. The plugin around it adds agents that
all read this skill: `design-orchestrator` (plans), `ui-ux-designer` (layout &
aesthetic), `frontend-engineer` (builds, mobile-first), `qa-reviewer` (audits
system + responsive + a11y), and `design-system-guardian` (maintains primitives).
Update this skill and the whole team builds to the change.
