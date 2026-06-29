# Color

Solid color only — no gradients. Neutrals use a Figma/Zinc ramp; the system has a
**Primary** and **Secondary** accent, and the status palette is positioned around
the color wheel so the states stay distinct yet harmonious with the accents.
Components reference **semantic tokens only**, so one component works in both
light and dark automatically.

## Neutral primitives (Gray ramp)

| token | hex | | token | hex |
|-------|-----|-|-------|-----|
| `gray-0` | #FFFFFF | | `gray-400` | #A1A1AA |
| `gray-50` | #F9FAFB | | `gray-500` | #71717A |
| `gray-75` | #F4F4F5 | | `gray-600` | #52525B |
| `gray-100` | #EFEFF1 | | `gray-700` | #3F3F46 |
| `gray-200` | #E4E4E7 | | `gray-800` | #27272A |
| `gray-300` | #D4D4D8 | | `gray-900` | #18181B |
|  |  | | `gray-950` | #09090B |

## Semantic neutrals

| token | light | dark |
|-------|-------|------|
| `--color-bg` | gray-50 | gray-950 |
| `--color-bg-subtle` | gray-75 | #111113 |
| `--color-surface` | gray-0 | gray-900 |
| `--color-surface-2` | gray-75 | gray-800 |
| `--color-border` | gray-200 | #27272A |
| `--color-border-strong` | gray-300 | gray-700 |
| `--color-text` | gray-900 | #FAFAFA |
| `--color-text-muted` | gray-600 | gray-400 |
| `--color-text-subtle` | gray-500 | gray-500 |

Dark mode uses **elevated surfaces** (bg darkest → each layer lighter), not inversion.

## Accents (Primary + Secondary) — solid

| token | light | dark | role |
|-------|-------|------|------|
| `--color-primary` | #4C6EF5 | #5C7CFA | main actions, links, focus, selection |
| `--color-primary-hover` | #3B5BDB | #748FFC | hover/pressed |
| `--color-primary-tint` | rgba(76,110,245,.10) | rgba(92,124,250,.16) | selected rows, soft fills |
| `--color-secondary` | #7C3AED | #A78BFA | secondary CTAs, highlights, accents, data-viz pairing |
| `--color-secondary-hover` | #6D28D9 | #8B5CF6 | hover/pressed |
| `--color-secondary-tint` | rgba(124,58,237,.10) | rgba(167,139,250,.16) | soft secondary fills |

`--color-brand` aliases `--color-primary`. Accents are brighter in dark to stay
vivid on near-black. No gradient fills.

## Color-wheel reasoning

Primary indigo sits at ~231° on the wheel. The other roles are placed
deliberately:

- **Secondary = violet (~272°)** is *analogous* to primary (adjacent on the
  wheel) — the most harmonious partner, so the two accents never fight. This is
  the indigo→violet pairing in the references.
- **Pending = amber (~38°)** is near the *complement* of indigo → maximum
  salience, which is what "needs attention" should have.
- **Status hues are spread around the wheel** so no two states read as the same
  color, while each keeps its conventional meaning (green = good, red = bad, etc.).
- **Submitted moved to cyan (~191°)** so it no longer collides with the secondary
  accent's violet — accents and states stay visually separate.

## Status (icon-led, wheel-positioned)

Tint = `color-mix(in srgb, <color> 13%, transparent)` (works over both themes).
Colors brighten in dark.

| status | hue | light | dark | icon |
|--------|-----|-------|------|------|
| Pending | 38° | #D97706 | #FBBF24 | `Alert02Icon` |
| In review | 47° | #CA8A04 | #FCD34D | `AiSearchIcon` |
| Success | 145° | #16A34A | #4ADE80 | `CheckmarkCircle02Icon` |
| Submitted | 191° | #0891B2 | #22D3EE | `Navigation03Icon` |
| In progress | 211° | #2563EB | #60A5FA | `Loading03Icon` |
| Failed | 4° | #DC2626 | #F87171 | `CancelCircleIcon` |
| Expired | — (neutral) | #52525B | #A1A1AA | `Clock01Icon` |

## Rules
- Solid color only — no gradient backgrounds or text.
- Components use semantic tokens; light/dark values live in `:root` and
  `[data-theme="dark"]`. Components never branch on theme.
- No raw hex / color names in component code.
- Every interactive element defines hover / active / focus / disabled via tokens.
- Maintain WCAG AA contrast in both themes, including text on tints.
