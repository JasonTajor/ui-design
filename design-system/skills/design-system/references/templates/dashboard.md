# Dashboard Template

## When to use
Data-dense internal app screens: metrics, tables, management views.

## Sections (top → bottom)
1. **Top bar** — page `Heading`, primary action (one), filters.
2. **KPI row** — 3–4 metric `Card`s in a responsive grid.
3. **Primary content** — chart(s) and/or a `Table`, in `Card`s.
4. **Secondary content** — supporting lists/panels.

## Components
Sidebar, Navbar/Topbar, Card, Table, Badge (status), Button, Dropdown (filters),
Toast (action feedback), empty/loading/error states for every async region.

## Spacing
Page padding `space-32`. Gap between cards `space-32`. KPI row → content `space-48`.
Card inner padding `space-24`.

## Responsive rules
- ≥1024px: sidebar visible, KPI row 4-up, content 2-col.
- 768–1024px: KPI row 2-up, content 1-col.
- <768px: sidebar collapses to a drawer, everything stacks, tables scroll-x or
  switch to stacked rows.

## Animation rules
Cards fade/slide in on load (`motion-base`, staggered subtly). Skeletons while
loading — never a layout jump. Honor reduced-motion.

## Required states
Every data region must define: loading (skeleton), empty (clear CTA), error
(retry). Missing any of these is a review failure.
