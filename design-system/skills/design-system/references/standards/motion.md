# Motion

Motion communicates state change. It should be quick, consistent, and respect
user preferences.

## Duration tokens
| token | ms | use |
|-------|----|-----|
| `motion-fast` | 120 | hovers, small state changes |
| `motion-base` | 200 | most transitions, dropdowns |
| `motion-slow` | 320 | modals, page-level transitions |

## Easing
- `ease-standard` (e.g. cubic-bezier(0.2, 0, 0, 1)) for most UI.
- Enter slightly slower than exit.

## Rules
- Animate `transform` and `opacity`, not `width`/`top`/`left` (jank).
- Always honor `prefers-reduced-motion`: drop non-essential animation.
- No arbitrary durations; pick a token.

## Apple-style spring (optional)
For playful, tactile moments (a sheet appearing, a toggle), an overshoot easing
reads as "Apple": `--ease-spring: cubic-bezier(.34, 1.56, .64, 1)`. Use sparingly —
on most UI, the standard ease is calmer and more trustworthy.
