Status: APPROVED
Current stage: DONE (all 8 stages)

Req tags (requirements.md has no IDs): NAV, MAIN, FOOT, IMG, FONT, MOBILE, HOME, GFX, CMP, STACK, THEME. Midterm PDF: M1, M2, M3.
Paths are inside MidtermsFolder/. Checks use grep, wc, ls, node --check.

## Stage 1: Setup
- [x] T1.1 Create style.css: Bootstrap variable overrides with hex colors (:root)
  - Covers: THEME, STACK | Skills: css-typography
  - Done when: `grep -c "\-\-bs-body-bg\|\-\-orange" style.css` is 2 or more
- [x] T1.2 Create script.js with a comment header only
  - Covers: STACK, M1 | Skills: vanilla-js-widgets
  - Done when: `node --check script.js` passes
- [x] T1.3 Confirm folders assets/images and assets/audio exist; ask user to create assets/video (user creates folders)
  - Covers: M3 | Skills: none
  - Done when: `ls assets` shows images, audio, video

## Stage 2: Layout (structure only, no styling yet)
- [x] T2.1 index.html skeleton: head (Bootstrap CSS, Google Font, style.css last), viewport meta, navbar, main, footer
  - Covers: NAV, MAIN, FOOT, MOBILE | Skills: semantic-html
  - Done when: grep finds one each of `<nav`, `<main`, `<footer`, `viewport`, `navbar-toggler`
- [x] T2.2 Same skeleton in graphics.html and compression.html; active link differs per page
  - Covers: NAV, MAIN, FOOT | Skills: semantic-html
  - Done when: each page has one `active` nav link and a different one per page
- [x] T2.3 Home content: title, intro marker, 3 image figures with label markers, 2 buttons
  - Covers: HOME, IMG, D4, D9 | Skills: semantic-html
  - Done when: index.html has 3 `<figcaption` and 2 `btn` links
- [x] T2.4 Graphics content in wireframe order, comparison table, widget placeholder, markers
  - Covers: GFX, IMG | Skills: semantic-html
  - Done when: graphics.html has 3 `section-title` headings and 1 `<table`
- [x] T2.5 Compression content in wireframe order, audio table with placeholders, markers
  - Covers: CMP, IMG | Skills: semantic-html
  - Done when: compression.html has 2 `<audio` (or placeholders noted) and 1 zip link
- [x] T2.6 Marker check against design.md section 8
  - Covers: design 8 | Skills: semantic-html
  - Done when: `grep -c CONTENT-TODO` per page matches the design list

## Stage 3: Typography and styling
- [x] T3.1 Space Grotesk link in each head, font-family in style.css
  - Covers: FONT, M2, D8 | Skills: css-typography
  - Done when: grep finds fonts.googleapis in 3 pages and "Space Grotesk" in style.css
- [x] T3.2 Module 2 rules written explicitly: line-height 1.5, letter-spacing, font-kerning: normal
  - Covers: FONT, M2 | Skills: css-typography
  - Done when: grep finds all three property names in style.css
- [x] T3.3 Navbar hover (color + background) and distinct active link
  - Covers: NAV | Skills: css-typography
  - Done when: style.css has `.nav-link:hover` and `.nav-link.active` rules
- [x] T3.4 Main container, titles, text, labels, footer, specs table classes; mobile media query
  - Covers: MAIN, FOOT, MOBILE, THEME | Skills: css-typography
  - Done when: all 7 design classes exist in style.css and 1+ `@media` rule

## Stage 4: Media
- [x] T4.1 Create specs/assets.md from assets/ files; record original size, format, dimensions, color depth BEFORE any change
  - Covers: M3, gate 6 | Skills: media-optimization
  - Done when: every file in assets/ has a row
- [x] T4.2 Optimize 4.jpeg to .webp, point all placeholder img tags to it, update assets.md
  - Covers: IMG, M1, M3 | Skills: media-optimization
  - Done when: .webp exists, smaller than original (`wc -c`), no img src to 4.jpeg remains
- [x] T4.3 Ghost.svg as inline `<svg>` on graphics page (img tag elsewhere) with aria label
  - Covers: GFX, M1 | Skills: svg-graphics
  - Done when: graphics.html has `<svg` and `role="img"`
- [x] T4.4 Audio players for HammerAndBolter.mp3 placeholder; sizes in table
  - Covers: CMP, M1 | Skills: media-optimization
  - Done when: `<audio` src files and the zip link target exist (`ls assets/audio`)

## Stage 5: Interactivity
- [x] T5.1 Zoom widget markup: form-range slider, raster image and SVG side by side
  - Covers: M1, D6 | Skills: vanilla-js-widgets, svg-graphics
  - Done when: graphics.html has one `form-range` and both elements have ids
- [x] T5.2 script.js: slider input resizes both, simple commented code
  - Covers: M1, D6 | Skills: vanilla-js-widgets
  - Done when: `node --check script.js` passes and graphics.html links script.js

## Stage 6: Spec Table
- [x] T6.1 Technical Media Spec Table on each page, four required columns, only assets used on that page (one row per image use), values from assets.md
  - Covers: M3, D5, D13, D16 | Skills: media-optimization
  - Done when: each page has 1 `specs-table` with 4 `<th` and rows match assets.md, and the site has 3+ distinct assets in total

## Stage 7: QA
- [x] T7.1 Run qa-verification on whole site
  - Covers: all | Skills: qa-verification
  - Done when: report shows no failures

## Stage 8: Content handoff
- [x] T8.1 List every CONTENT-TODO (file, id, what to write); confirm submission shape
  - Covers: finish line | Skills: qa-verification
  - Done when: list printed; index.html, style.css, assets/images, audio, video all present

## Blocked
- Uncompressed audio: waiting on user (D14). HammerAndBolter.zip is the zip placeholder (D15); T4.4 links it.
- QA flags for user: placeholder audio+zip are 78 MB total (use short clips); unused originals in assets/images (7.png, wallpaper 1/6, 4.jpeg) ship in the zip; empty assets/video is dropped by zip/GitHub unless a file is added.
- Not run: browser or responsive test (only on request); color contrast not measured with a tool.
