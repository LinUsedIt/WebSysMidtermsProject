---
name: media-optimization
description: Use this skill whenever you add, convert, compress, or measure an image, audio file, video, or zip, fill specs/assets.md, or build the Technical Media Spec Table (Module 3). Use it any time a file is added to /assets, even if the user only says "add an image" or "make the audio smaller".
---

# Media Optimization and Spec Table

## Folders
- Shipped: `MidtermsFolder/assets/images`, `/audio`, `/video`.
- **Before converting or overwriting any file**, record its original size, format, dimensions, and color depth in `specs/assets.md`. That row is the only record of "original size" once the file is optimized.
- Do not delete or overwrite an original until its row is written. If the user keeps originals elsewhere, ask for the path and measure from there.

## Optimizing
Check the tool exists first (`which cwebp ffmpeg convert`). If missing, say so and ask the user.
- **Images:** raster to `.webp` (`cwebp -q 80 in.png -o out.webp`). Resize to the largest size actually displayed (no 4000px photos in a 600px box). Target under 200 KB each.
- **Audio:** short clip (under 30 s) as MP3 (`ffmpeg -i in.wav -b:a 128k out.mp3`). Keep the uncompressed WAV for the Compression page comparison.
- **Zip demo:** a normal zip of the uncompressed audio (`zip -9`). No nested or recursive archives.
- Never use a file you cannot legally use. Note the source and license in assets.md.

## specs/assets.md columns
`File | Role | Original size | Final size | Format | Color depth / quantization | Compression algorithm | Source / license`

## Measuring (never invent numbers)
- Size: `stat -c %s file` (bytes). Convert to KB/MB.
- Image: `identify -verbose file | grep -E "Geometry|Depth|Colors"` or `file file`.
- Audio: `ffprobe -hide_banner file` for codec, bitrate, sample rate, bit depth.
- If a value cannot be measured, write `TO VERIFY` and tell the user.

## Algorithm / depth reference (standard facts)
| Format | Compression algorithm | Typical depth |
|---|---|---|
| PNG | Lossless: DEFLATE (LZ77 + Huffman) | 8-bit indexed (256 palette) or 24-bit |
| JPEG | Lossy: DCT + quantization + Huffman | 24-bit |
| WebP | Lossy (VP8 transform/prediction) or lossless | 24-bit (+alpha) |
| SVG | Text (XML), no pixel compression; gzip when served | n/a, vector |
| WAV | None (uncompressed PCM) | 16-bit |
| MP3 | Lossy: MDCT, psychoacoustic model, Huffman | decodes to 16-bit |
| Ogg Vorbis | Lossy: MDCT | decodes to 16-bit |
Use the real encoder settings from ffprobe/identify over this table when they differ.

## Technical Media Spec Table (Module 3)
- At the bottom of every page the wireframe shows it (home, graphics, compression), unless design.md says otherwise.
- Audit at least 3 embedded assets, covering at least one image, one audio file, and the SVG or another type.
- Columns exactly: Asset Name & File Format | Original Size → Compressed | Color Depth / Quantization | Compression Algorithm.
- Build rows from assets.md. Only list files actually used on that page.

## Quick checks
- `du -sh assets/*` shows each folder; no image over 200 KB without a note in assets.md
- Every `<img src>` and `<audio src>` path exists
- Table rows >= 3 and match assets.md
