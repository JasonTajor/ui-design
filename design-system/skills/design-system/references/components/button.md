# Button

## Source of truth
`components/ui/Button.tsx` — read before use.

## Purpose
Trigger an action. Not for navigation (use a link styled as needed).

## Variants
- `primary` — the single main action in a context (`--color-brand`).
- `secondary` — supporting actions (surface + border tokens).
- `ghost` — low-emphasis, toolbars.
- `danger` — destructive actions (`--color-danger`); confirm before destructive use.

## Sizes
`sm` (height ~32, `space-8` x-padding) · `md` default (~40, `space-16`) ·
`lg` (~48, `space-16`). Sizes pull from the spacing scale only.

## Tokens used
Padding: `space-8/3/4`. Radius: `radius-md`. Text: `Button` role.
Color: brand/surface/danger semantic tokens. Motion: `motion-fast` on hover.

## States
default · hover (`--color-brand-hover`) · active · focus-visible (`--color-focus`
ring) · disabled (reduced opacity, no pointer) · loading (spinner, label kept for
width, control disabled).

## Accessibility
Real `<button>`. Icon-only buttons require `aria-label`. Focus ring must be
visible (never `outline:none` without a token-based replacement).

## Do / Don't
- Do: keep exactly one `primary` per view.
- Don't: create `BlueButton`, `BigButton`, etc. — use variants/sizes.
