# Assets (measured 2026-10-06, before any conversion)
Sizes: bytes / 1024 = KB, bytes / 1048576 = MB. Paths are inside MidtermsFolder/assets/.

| File | Role | Original size | Final size | Format | Color depth / quantization | Compression algorithm | Source / license |
|---|---|---|---|---|---|---|---|
| images/4.jpeg to 4.webp | Placeholder raster image (all raster spots) | 215.8 KB (220,929 B), 2320x1305 | 52.7 KB (53,958 B), resized to 1280x720, WebP quality 80 (images/4.webp) | JPEG to WebP | 24-bit RGB (8 bits per channel) | Lossy: JPEG DCT + Huffman to WebP VP8 prediction + transform | User-provided, license TO VERIFY |
| images/7.png | Unused for now | 713.8 KB (730,880 B), 960x547 | n/a | PNG | 24-bit RGB (pixel format 24bppRgb) | Lossless: DEFLATE | User-provided, license TO VERIFY |
| images/wallpaper 1.jpg | Unused for now | 397.1 KB (406,608 B), 1920x1080 | n/a | JPEG | 24-bit RGB | Lossy: DCT + quantization + Huffman | User-provided, license TO VERIFY |
| images/wallpaper 6.jfif | Unused for now | 10.8 KB (11,065 B), 637x358 | n/a | JPEG (JFIF) | 24-bit RGB | Lossy: DCT + quantization + Huffman | User-provided, license TO VERIFY |
| images/Ghost.svg | Vector sample (home, graphics, widget) | 17.9 KB (18,354 B), viewBox 210x297 | inline in graphics.html (cleaned copy, about 12.0 KB (12,281 characters) of markup); img elsewhere | SVG (XML text) | n/a, vector | None (text; gzip only when served) | User-provided, license TO VERIFY |
| audio/HammerAndBolter.mp3 | PLACEHOLDER audio 1 and 2 | 38.86 MB (40,745,500 B) | no change | MP3, 48 kHz, stereo | decodes to 16-bit; bitrate and duration TO VERIFY (no ffprobe) | Lossy: MDCT + psychoacoustic model + Huffman | User-provided, license TO VERIFY |
| audio/HammerAndBolter.zip | PLACEHOLDER zip | 38.59 MB (40,461,344 B), holds the mp3 above | no change | ZIP | n/a | DEFLATE (saves only 0.7% on an mp3) | User-provided |

## Flags
- The placeholder mp3 is 38.86 MB. That is far too large for the "keep audio small" rule. Replace it with short clips (under 30 s) when your audio is ready.
- Tools missing: cwebp, ffmpeg, ffprobe, ImageMagick. Python 3.13 with Pillow 12.3 is used to convert images. Audio cannot be converted or probed until ffmpeg is installed.
