# Responsive — every device

Build **mobile-first**: write the base styles for the smallest screen, then add
space and columns as the viewport grows. A layout is only "done" when it holds at
360px, 768px, and 1280px.

## Breakpoints

| name | width | what changes |
|------|-------|--------------|
| base (mobile) | < 640px | single column; sidebars become a drawer |
| sm | ≥ 640px | 2-up grids appear |
| md (tablet) | ≥ 768px | denser grids, side-by-side hero |
| lg (desktop) | ≥ 1024px | persistent sidebar; full multi-column |
| xl | ≥ 1280px | max content width caps line length |

Navigation/sidebars collapse to an off-canvas **drawer at ≤ 1024px** (hamburger +
dimmed backdrop, closes on item tap / backdrop / Esc).

## Rules
- **Grids reflow**, never squish: 3-col → 2-col → 1-col across lg→md→base.
- **Tables**: scroll horizontally inside their container, or switch to stacked
  rows on mobile. Never let a table force the page wider than the viewport.
- **No fixed widths that exceed the viewport.** Use `max-width` + `width:100%`
  so elements shrink to fit.
- **Fluid type** for big headings: `clamp(min, vw, max)` so Display/Heading never
  overflow a phone.
- **Spacing steps down** one notch on small screens (e.g. section gap 64 → 48 →
  32), staying on the 8pt grid.
- **Touch targets ≥ 44×44px**; spacing between tappable items ≥ 8.
- Honor `prefers-reduced-motion`.
- Prefer **container queries** for components that appear in both wide and narrow
  slots, so they respond to their container, not just the screen.

## Definition of done
Open at 360 / 768 / 1280: no horizontal overflow, nothing clipped, the drawer
works, every interactive target is comfortably tappable, and text never overflows.
