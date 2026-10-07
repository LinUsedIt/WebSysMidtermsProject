---
name: svg-graphics
description: Use this skill whenever you create, edit, or animate an inline SVG, build the vector side of a raster-vs-vector comparison, make a diagram or flowchart, or add zoom, scale, or color interactions to graphics. Use it for any task involving vector graphics or the Module 1 Graphics element.
---

# SVG Graphics

## Authoring
- Inline `<svg>` in the HTML (not an `<img>`), so CSS and JS can reach its parts.
- Always set `viewBox` and omit fixed `width`/`height` (or set `width: 100%; height: auto` in CSS) so it scales.
- Accessibility: `role="img"`, `<title>` and `<desc>` as the first children, plus `aria-labelledby`.
- Use basic shapes (`rect`, `circle`, `path`, `line`, `text`). Keep the markup hand-readable: indent, group with `<g id="...">`, comment sections.
- Colors through CSS variables (`fill: var(--accent)`) so the SVG matches the theme.
- Text inside the SVG that teaches a concept is the user's content: leave a CONTENT-TODO comment. Plain labels from the spec are fine.

## Interactivity
- Target parts by `id` or class from script.js. Change attributes with `setAttribute`, or toggle CSS classes.
- Typical widgets: zoom slider that scales the SVG, a color picker that updates `fill`, hover highlights on `path` nodes.
- Keep it keyboard-usable: controls are real `<input>`/`<button>` elements with labels.

## Raster side of a comparison
- To show pixelation when zoomed, display a small raster image scaled up with CSS `image-rendering: pixelated;`, beside the SVG at the same zoom.
- Keep both panels the same size and driven by one shared slider.

## Quick checks
- `grep -c "<svg" page.html` is at least 1
- Every `<svg` has `viewBox`
- Resize the window narrow: the SVG shrinks without scrollbars
