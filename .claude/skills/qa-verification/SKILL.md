---
name: qa-verification
description: Use this skill whenever you finish a task or stage, before ticking a task done, before the final stage report, or when the user asks to check, test, validate, or review the site against the requirements or the midterm. Use it at the end of every stage, not only at the end of the project.
---

# QA Verification

Run cheap checks first. Do not read whole files back. Report only failures plus a one-line pass count.

## Midterm checklist
**Module 1 (all on the page):**
- Text: one `<h1>`, ordered `<h2>`/`<h3>`, `<p>` copy
- Graphics: inline `<svg>` present
- Images: raster `.webp/.png/.jpg` in /assets/images, optimized
- Audio: `<audio>` element or Web Audio API
- Interactive: a working JS widget

**Module 2 (in style.css):** web font, sans-serif; `line-height` 1.4-1.6; `letter-spacing` on headers/labels; `font-kerning: normal`.

**Module 3:** spec table at the bottom, 3+ assets, 4 required columns, values match assets.md.

**Submission shape:** `index.html`, `style.css`, `/assets/images`, `/assets/audio`, `/assets/video`. All relative paths. Works when opened from the zip, and on the deployed URL.

## Checks to run
- HTML: `npx html-validate *.html` or the W3C validator if available. Else check unclosed tags and duplicate ids with grep.
- JS: `node --check script.js`
- Paths: every `src`/`href` target exists
- Responsive: no horizontal scroll at 375px, 768px, 1280px (use a headless browser if installed, else review the CSS media queries)
- Accessibility: `alt` on all images, labels on all inputs, heading order, contrast, focus styles
- Performance: `du -sh assets/*`, no unoptimized originals in /assets

## Content handoff (final stage)
- `grep -rn "CONTENT-TODO" *.html script.js` and list each: file, id, what to write.
- Report the count. Do not fill them in.

## Report format
`Passed: N | Failed: [list] | Next: ...` (3 lines max). Failures go into tasks.md under Blocked if unresolved.
