# Card

## Source of truth
`components/ui/Card.tsx` — read before use.

## Purpose
A surface that groups related content. The default container for dashboard
widgets, list items, and panels.

## Anatomy
`Card` > optional `Card.Header` (Title + actions) > `Card.Body` > optional
`Card.Footer`. Compose these; don't rebuild a card from a bare `div`.

## Tokens used
Background `--color-surface`, border `--color-border`, padding `space-24`
(`space-16` for compact), radius `radius-lg`, gap between cards `space-32`.

## States
default · hover (only if interactive — then it's a button/link, give focus ring)
· selected (border `--color-brand`).

## Accessibility
A non-interactive card is a region, not a button. If the whole card is clickable,
make it a single focusable control with an accessible name.

## Do / Don't
- Do: use `Card.Header` for titles so type/spacing stay consistent.
- Don't: hand-roll padded bordered divs — that's a duplicate Card.
