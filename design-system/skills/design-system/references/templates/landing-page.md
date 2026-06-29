# Landing Page Template

## When to use
Public marketing pages: product, feature, campaign.

## Sections (top → bottom)
1. **Hero** — `Display` headline, sub-`Body`, primary + secondary CTA.
2. **Social proof** — logos / testimonials.
3. **Features** — 3-up benefit grid (Cards or icon+text).
4. **Deep dive** — alternating image/text rows.
5. **Pricing** (optional).
6. **FAQ**.
7. **Final CTA**.
8. **Footer**.

## Components
Navbar, Button (primary CTA = one brand action per section max), Card, Badge,
Accordion (FAQ), Footer.

## Spacing
Section separation `space-64` (desktop), `space-48` (mobile). Content max-width
container, generous side gutters.

## Responsive rules
- Hero text/image: side-by-side ≥1024px, stacked below (text first).
- Feature grid: 3-up → 2-up → 1-up.
- Nav collapses to a menu under 768px.

## Animation rules
Subtle reveal-on-scroll (`motion-base`, transform+opacity only). Hero may animate
on load. Nothing that blocks reading. Honor reduced-motion.
