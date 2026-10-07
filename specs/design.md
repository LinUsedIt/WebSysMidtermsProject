Status: APPROVED

# Design: Graphics and Compression Learning Site
Sources: requirements.md, wireframe, decisions.md (D1-D10).

## 1. Pages
| Page | Purpose | Wireframe |
|---|---|---|
| index.html | Short intro, 3 sample images, 2 buttons, specs table | Home |
| graphics.html | Raster, Vector, Raster vs. Vector, zoom slider widget | Graphics |
| compression.html | Compression, RLE explained, audio table + zip | Compression |

Out of scope: Test page / quiz, zip bomb, RLE interactive demo (optional, later).

## 2. File structure (site root: MidtermsFolder/)
```
MidtermsFolder/
  index.html, graphics.html, compression.html
  style.css            (new, written from scratch; style1.css not used)
  script.js            (zoom slider only)
  bootstrap-5.3.8-dist/
  assets/
    images/            (raster images, SVG files if separate)
    audio/             (2 audio files + zip)
    video/             (empty, kept for submission shape)
```

## 3. Design tokens (plain hex codes in style.css, D17)
Bootstrap-first: `<html data-bs-theme="dark">`, override Bootstrap variables (--bs-body-bg, --bs-body-color, --bs-link-color) in style.css using the hex values below. No custom CSS variables. Use standard Bootstrap navbar, table, btn, grid, form-range classes. Module 2 rules are written explicitly in style.css.
| Token | Value | Use |
|---|---|---|
| background | #120d0a | page background |
| panel | #1c1510 | table and card background |
| orange | #ffa500 | titles, borders, nav bar |
| dark orange | #cc8400 | nav hover background, button hover |
| cream | #f0e6d8 | body text |
| font | "Space Grotesk", sans-serif | everything |
- Type scale: body 1rem, h1 2.25rem, h2 1.5rem, labels 0.875rem.
- Body line-height 1.5, letter-spacing 0.05em on headings and labels, font-kerning: normal.
- Spacing: 1rem steps. Main container max-width ~900px, centered, 3px orange border, rounded 10px, side space on desktop, smaller margin on mobile.

## 4. Shared parts (same on all 3 pages)
- **Navbar:** Bootstrap responsive navbar (collapses on mobile). Home | Graphics | Compression. Hover changes text and background. Current page link has its own style (class `active`).
- **Footer:** Copyright "alias" name 2026. User fills in the name (CONTENT-TODO).
- **Technical Media Spec Table:** bottom of every page, inside main. Four columns: Asset Name & File Format | Original Size -> Compressed | Color Depth / Quantization | Compression Algorithm. At least 3 assets in total across the site; values measured, filled in assets.md first.

## 5. Page layout (inside the main container)
- **Home:** title "Graphics and Compression Learning Site" | intro | 3 images side by side with labels (Raster, Vector, Compression) | buttons "Learn Graphics", "Learn Compression" | specs table.
- **Graphics:** title | sample image + label | "What are Graphics?" | Raster section + image + label | Vector section + inline SVG + label | Raster vs. Vector 2-column table (image + 3 differences each) | zoom widget | specs table.
- **Compression:** title | compression image + label | "What is Compression?" | "How does it work?" | "RLE Algorithm" + image + label | "Sample Compression" + 3-cell table (uncompressed player, compressed player, zip link, sizes noted) | specs table.
- Mobile: single column, 3 home images stack, tables scroll or stack.
- **Reusable classes (same on every page):** `.main-container`, `.page-title`, `.section-title`, `.content-text` (every paragraph), `.image-label` (every caption), `.specs-table`, `.site-footer`.

## 6. Interactive feature
- **Raster vs. vector zoom (graphics.html):** user drags a slider; a raster image and an inline SVG scale together side by side. The raster gets blurry or pixelated, the SVG stays sharp. Plain JS: one `input` listener changing the CSS size/transform of both.

## 7. Media plan
| Item | Purpose | Source | Target format |
|---|---|---|---|
| 4.jpeg | PLACEHOLDER for every raster image spot (home x3 incl. raster, graphics x3, compression x2) | User (assets/images/4.jpeg) | .webp or optimized .jpg; record original in assets.md |
| Ghost.svg | Vector image: home, graphics vector section, comparison, zoom widget | User (assets/images/Ghost.svg) | inline `<svg>` where required (Graphics page), else `<img>` |
| HammerAndBolter.mp3 | PLACEHOLDER audio; user replaces later (mp3) | User (assets/audio/) | .mp3 |
| Audio pair | Audio 1 uncompressed, Audio 2 compressed | See open question 1 | TBD |
| Zip | Both audio files | Built from audio 1 and 2 | .zip |
- Unused for now: wallpaper 1.jpg, wallpaper 6.jfif, 7.png.

## 8. Content map (CONTENT-TODO markers, no copy)
- index: home-intro, home-img-label-raster, home-img-label-vector, home-img-label-compression
- graphics: gfx-title-img-label, gfx-what-are-graphics, gfx-raster-text, gfx-raster-img-label, gfx-vector-text, gfx-vector-img-label, gfx-compare-raster-diff1..3, gfx-compare-vector-diff1..3, gfx-compare-raster-img-label, gfx-compare-vector-img-label, gfx-widget-instructions
- compression: cmp-img-label, cmp-what-is, cmp-how-works, cmp-rle-what, cmp-rle-how, cmp-rle-img-label, cmp-sample-intro
- all pages: footer-name-home, footer-name-graphics, footer-name-compression (alias and student name)

## 9. Open questions
(Resolved: audio pair, user will add the uncompressed file later (D14); images use 4.jpeg + Ghost.svg placeholders; specs table lists only assets used on that page, D11-D13.)
