---
name: semantic-html
description: Use this skill whenever you create or edit any HTML page, add page structure, headings, navigation, images, audio, or sections, or place CONTENT-TODO markers. Use it for index.html and every other page, even for small edits like adding a link or an image.
---

# Semantic HTML

## Page skeleton
- `<!DOCTYPE html>`, `<html lang="en">`, `<meta charset="utf-8">`, viewport meta, a unique `<title>` per page.
- Link `style.css` in `<head>`. Load scripts at the end of `<body>` or with `defer`.
- Landmarks: one `<header>` with `<nav>`, one `<main>`, one `<footer>`. Use `<section>` with a heading and `<figure>`/`<figcaption>` for media.

## Text (Module 1, element 1)
- Exactly one `<h1>` per page. Then `<h2>`, `<h3>` in order. Never skip a level for looks.
- Body text in `<p>`. Lists in `<ul>`/`<ol>`. No `<br>` for spacing, no `<div>` where a semantic tag fits.

## Images (Module 1, element 3)
- Always `alt` text that describes the image's purpose. Empty `alt=""` only for decoration.
- Always `width` and `height` attributes (prevents layout shift). `loading="lazy"` below the fold.
- Prefer `.webp`. Use `<picture>` with a fallback only if the spec asks.

## Audio (Module 1, element 4)
- `<audio controls preload="metadata">` with `<source>` and a text fallback. Add a visible label above it.

## SVG (Module 1, element 2)
- Inline `<svg>` only. See skill `svg-graphics`.

## Technical Media Spec Table
- Real `<table>` with `<caption>`, `<thead>`, `<th scope="col">`. See skill `media-optimization`.

## CONTENT-TODO markers (teaching content is the user's)
Format: `<!-- CONTENT-TODO [id]: what to write | where it appears | target length -->`
- Put it inside the element that will hold the text, for example `<p><!-- CONTENT-TODO [raster-what]: define raster graphics | "What are Raster Graphics?" section | 3-4 sentences --></p>`.
- IDs are unique, lowercase, hyphenated. Never delete a marker.
- Allowed to write: wireframe headings, nav labels, button labels, alt text, aria labels.

## Quick checks
- `grep -c "<h1" page.html` is 1
- Every `<img` has `alt=`
- `grep -oh "CONTENT-TODO \[[a-z0-9-]*\]" *.html | sort | uniq -d` prints nothing (no duplicate ids)
