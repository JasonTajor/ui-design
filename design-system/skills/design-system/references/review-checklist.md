# Quality Review Checklist

Audit UI against every item. For each issue found, report: **location**, the
**rule** it breaks, and the **fix**. Reviewing produces a report — it does not
edit code.

## Tokens & system integrity
- [ ] No arbitrary spacing (`p-[..px]`, `gap-[..]`) — all from the spacing scale.
- [ ] No literal font sizes — semantic typography roles only.
- [ ] No raw hex / named colors — semantic color tokens only.
- [ ] No arbitrary radius or motion durations.
- [ ] No duplicate components (anything that re-implements an existing primitive).
- [ ] Component usage matches its source API (no drift from the spec).

## Accessibility
- [ ] Color contrast meets WCAG AA.
- [ ] Visible focus state on every interactive element.
- [ ] Full keyboard operability; logical tab order.
- [ ] Images have alt text; icon-only controls have labels; decorative icons hidden.
- [ ] Correct semantic elements/roles (`button` vs `div`, headings in order).

## Responsive
- [ ] Works at mobile / tablet / desktop breakpoints.
- [ ] No horizontal overflow; tables handle small screens.
- [ ] Touch targets ≥ ~44px.

## States (each async/interactive region)
- [ ] Loading state (skeleton/spinner, no layout jump).
- [ ] Empty state (clear, with a next action).
- [ ] Error state (message + recovery).
- [ ] Disabled state where relevant.

## Visual & consistency
- [ ] Clear visual hierarchy; one primary action per view.
- [ ] Consistent alignment and spacing rhythm.
- [ ] Consistent component usage with the rest of the product.

## Performance
- [ ] No obviously heavy re-renders / unbounded lists (virtualize long lists).
- [ ] Images sized/lazy-loaded appropriately.
- [ ] Animations use transform/opacity and respect reduced-motion.

## Code health
- [ ] No dead code or unused imports.
- [ ] Consistent, meaningful naming.
- [ ] Imports follow project conventions.
- [ ] Components reused rather than copy-pasted.
