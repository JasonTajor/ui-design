# Icons

The standard icon set is **HugeIcons**, Stroke Rounded style — one consistent,
24×24, rounded-corner line family across the whole product.

## Install (React)

```bash
npm install @hugeicons/react @hugeicons/core-free-icons
```

The free pack (`@hugeicons/core-free-icons`, MIT, 5,400+ icons) ships the Stroke
Rounded style only — which is exactly the style we standardize on. `@hugeicons/react`
is the renderer.

```jsx
import { HugeiconsIcon } from "@hugeicons/react";
import { Search01Icon } from "@hugeicons/core-free-icons";

<HugeiconsIcon icon={Search01Icon} size={20} color="currentColor" strokeWidth={1.5} />
```

> For more styles (solid, duotone, etc.) Hugeicons Pro exists, but the system is
> built on Stroke Rounded — don't mix styles. There is also an official `hugeicons`
> agent skill that gives coding agents accurate icon names/props; install it if you
> use Claude Code so icon names aren't guessed.

## Usage rules
- **Size from a fixed set:** 16, 18, 20, 24 (tied to the spacing scale). Most UI
  uses 18–20; 16 inside dense tables/pills; 24 for emphasis.
- **`color="currentColor"`** so an icon inherits its parent's text/status color —
  this is what makes status chips and buttons theme correctly with no extra work.
- **`strokeWidth={1.5}`** everywhere. Don't mix stroke widths.
- Icon + text: the icon takes the text color token; gap of `space-8`.
- Standalone/icon-only controls need an `aria-label`. Decorative icons get
  `aria-hidden="true"`.

## Status icon mapping
See `colors.md` for the canonical status→icon pairs (Pending → `Alert02Icon`,
Success → `CheckmarkCircle02Icon`, etc.). Reuse those; don't invent new pairings.

## In plain HTML / non-React
Inline the SVG (or an `<svg><use>` sprite of the exported paths) and set
`stroke="currentColor"`, `fill="none"`, `stroke-width="1.5"`, `viewBox="0 0 24 24"`.
