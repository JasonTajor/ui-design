# Spacing — 8pt grid

All spacing (padding, margin, gap, layout) comes from an **8-point grid**: every
value is a multiple of 8, with **4 as the only half-step** for fine optical
adjustments. This single rule is what makes layouts feel even and rhythmic.
Arbitrary values (`p-[13px]`, `gap-[18px]`) are forbidden.

## Scale (token = pixel value)

| token | px | step | typical use |
|-------|----|------|-------------|
| `--space-4`  | 4  | ½ (use sparingly) | icon↔label, hairline insets |
| `--space-8`  | 8  | 1× | tight gaps, control inner padding |
| `--space-16` | 16 | 2× | default element padding, base gap |
| `--space-24` | 24 | 3× | card padding, comfortable gap |
| `--space-32` | 32 | 4× | gaps between cards/blocks |
| `--space-40` | 40 | 5× | sub-section separation |
| `--space-48` | 48 | 6× | section separation |
| `--space-56` | 56 | 7× | large section separation |
| `--space-64` | 64 | 8× | major page-section separation |
| `--space-80` | 80 | 10× | hero / page rhythm |
| `--space-96` | 96 | 12× | hero / page rhythm |

## Rules
- Multiples of 8 first. Reach for `--space-4` only when 8 is visibly too much
  (e.g. icon-to-text). Never use a value off this scale.
- Control **heights** also sit on the grid: 32 / 40 / 48 (sm / md / lg).
- Prefer `gap` on a flex/grid parent over per-child margins.
- Optical exceptions: text inside pills/badges may use a sub-4 vertical pad
  (e.g. 2–3px) purely to center the cap-height — this is an optical tweak, not a
  layout value, and is the only sanctioned exception.

## Tailwind mapping
4·8·16·24·32·40·48·56·64·80·96 → `1 2 4 6 8 10 12 14 16 20 24`. Disallow arbitrary
brackets in review: any `-[…]` spacing value is a violation.
