---
description: Build or update a dashboard/page end-to-end using the design system.
argument-hint: [what to build, e.g. "an analytics dashboard for sales"]
---

# /dashboard

Build or update UI for: **$ARGUMENTS**

Run the full pipeline, using the `design-system` skill as the source of truth:

1. **Consult the system** — read `skills/design-system/SKILL.md` and the relevant
   standards before deciding anything.
2. **Plan** — use the `design-orchestrator` to break the request into screens,
   pick patterns/components/tokens, and set responsive targets.
3. **Design** — use the `ui-ux-designer` to produce the layout spec (structure,
   components, token usage, light/dark, responsive intent, states).
4. **Build** — use the `frontend-engineer` to implement it mobile-first, tokens
   only, reusing components. If a primitive is missing, run
   `design-system-guardian` first.
5. **Review** — use the `qa-reviewer` to audit system compliance, responsiveness
   (360/768/1280), accessibility, and states. Apply blocking fixes.
6. **Summarize** — what was built, components/tokens used, and any follow-ups.
