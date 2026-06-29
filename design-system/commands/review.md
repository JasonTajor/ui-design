---
description: Audit the current UI against the design system (tokens, 8pt spacing, responsive, a11y, states).
argument-hint: [optional: file or area to review]
---

# /review

Run the `qa-reviewer` against: **$ARGUMENTS** (or the current changes if empty).

Audit using `skills/design-system/references/review-checklist.md` and
`skills/design-system/references/standards/responsive.md`. Report issues grouped
by **Blocking / Should-fix / Nice-to-have**, each with location, the rule it
breaks, and the fix. End with a verdict. Do not modify code.
