# Border Radius

Tuned for the soft, continuous Apple feel: generous rounding, derived from one
base so the whole product reshapes together. The default control radius is large
(12px) — that single choice is most of the "friendly" impression.

| token | px | use |
|-------|----|-----|
| `--radius-xs` | 6  | tags, small chips, inline pills |
| `--radius-sm` | 8  | inputs, menu items |
| `--radius-md` | 12 | buttons, controls (default) |
| `--radius-lg` | 16 | cards, panels |
| `--radius-xl` | 22 | modals, sheets, large surfaces |
| `--radius-2xl`| 28 | hero / feature surfaces |
| `--radius-full` | 9999 | pills, avatars, status dots |

## Derive from one base
Define `--radius-base: 12px` and compute the rest with `calc()`
(sm = base × .67, lg = base × 1.33, xl = base × 1.83). Changing the base alone
shifts the entire product from crisp to pillowy — useful for dialing in feel.

## Rules
- One radius system product-wide. Mismatched corners read as sloppy.
- Nested elements: inner radius ≤ outer radius (a control inside a card is never
  rounder than the card).
- No arbitrary radii (`rounded-[7px]`). Pick a token.
- Pills/avatars use `--radius-full`; everything rectangular uses the scale.
