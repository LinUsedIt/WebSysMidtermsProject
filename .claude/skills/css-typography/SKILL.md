---
name: css-typography
description: Use this skill whenever you write or edit style.css, set fonts, spacing, colors, layout, or responsive behavior, or implement Module 2 (Typography and Screen Legibility). Use it for any styling task, even small ones like changing a heading size or adding a media query.
---

# CSS and Typography

## Module 2 requirements (must be explicit in style.css)
- **Sans-serif primary typeface via web font.** Load with a Google Fonts `<link>` (or self-host with `@font-face`). Use a real fallback stack: `font-family: "Inter", system-ui, -apple-system, "Segoe UI", Arial, sans-serif;`. Use `font-display: swap`.
- **Leading:** `line-height` between 1.4 and 1.6 on body text (use 1.5). Headings may be tighter, but write the value.
- **Tracking:** `letter-spacing` set on headers and labels (for example `0.02em` on `h1`-`h3`, `0.05em` uppercase on labels/nav).
- **Kerning:** `font-kerning: normal;` on `body`.
- Comment each of these three rules so the user can point to them in Phase 3.

## Structure of style.css
Order and label sections with comments:
1. Design tokens in `:root` (colors, font stack, type scale, spacing, max width)
2. Reset / base (box-sizing, body, links)
3. Typography
4. Layout (nav, main, footer, grid/flex)
5. Components (cards, buttons, comparison panels, table, widgets)
6. Responsive (`@media (max-width: 768px)` and a small-phone breakpoint)

## Rules
- Use `rem` for font sizes. Body about `1rem` to `1.125rem`. Line length around 60-75 characters (`max-width: 70ch` on text).
- Colors only through tokens. Text/background contrast at least 4.5:1.
- Mobile-first layout: flexbox or CSS grid, no fixed pixel widths on containers.
- Visible `:focus-visible` outline on links, buttons, inputs.
- Tables and code scroll inside a wrapper with `overflow-x: auto`. The page body must not scroll sideways.
- If design.md says to use Bootstrap 5, load it by CDN, keep all Module 2 rules in style.css, and override Bootstrap's defaults there.

## Quick checks
- `grep -n "line-height" style.css` shows a value from 1.4 to 1.6 on body
- `grep -n "letter-spacing" style.css` finds rules on headings and labels
- `grep -n "font-kerning: normal" style.css` finds one
- `grep -n "font-family" style.css` shows a sans-serif stack with fallbacks
