# Typography

Use semantic roles, never raw sizes. `text-[17px]` is forbidden — it carries no
meaning and drifts. Each role maps to a fixed size/weight/line-height defined
once; change the role, not the call site.

## Typeface

**Inter** is the default UI/body face — an open-source (SIL OFL) variable font
designed for screens, with excellent legibility at small sizes. The data/mono
face is a system monospace stack (no extra web font to load).

Load via the Google Fonts API (add to your app's `<head>`):

```html
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
```

Tokens (always include the fallback stack so UI holds up before the font loads
or offline):

```
--font-sans: "Inter", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
--font-mono: ui-monospace, SFMono-Regular, Menlo, Consolas, monospace;
```

> Prefer self-hosting (e.g. an `@fontsource/inter` package or local woff2 files)
> in production — it removes the third-party request and the flash before load.
> Inter is variable, so any weight 100–900 is available from one file; the system
> standardizes on 400 / 500 / 600 / 700.

## Roles

| Role      | Size | Weight | Purpose                         |
|-----------|------|--------|---------------------------------|
| `Display` | 40   | 700    | hero headlines                  |
| `Heading` | 28   | 700    | page / major section titles     |
| `Title`   | 18   | 600    | card / dialog titles            |
| `Body`    | 15   | 400    | default running text            |
| `Caption` | 13   | 400    | secondary / metadata text       |
| `Label`   | 12   | 600    | form labels, small UI labels    |
| `Button`  | 14   | 600    | button text                     |

## Rules
- Pick a role by *meaning*, not by how big it looks.
- One `Display`/`Heading` as the page's primary title; everything steps down.
- Define each role once; never set font-size/weight ad hoc at a call site.
- Any literal font size is a review violation — replace with the nearest role.
