# Asset Compression Process

This document describes how oversized GIF/video assets in `assets/papers/**`
are compressed into lightweight web-friendly versions for faster page loads.

## Goal

- Preserve the **original** assets in the repo (never overwrite them).
- Produce a compressed sibling with the `_lq` suffix (e.g. `foo.gif` → `foo_lq.mp4`).
- Keep each compressed file **just under ~1 MB** — small enough to load fast,
  but not so aggressive that quality noticeably degrades.

## Encoding settings

Compressed videos are encoded with `ffmpeg` using:

- Codec: `libx264` (H.264) — broad browser support.
- Pixel format: `yuv420p` — required for in-browser playback.
- Even dimensions: `scale=trunc(iw/2)*2:trunc(ih/2)*2` — H.264/`yuv420p`
  requires width and height to be divisible by 2.
- `-movflags +faststart` — moves the MOOV atom to the front so the video can
  start playing before it is fully downloaded.
- Quality: `-crf <N>` — iterate on the CRF value until the output lands just
  under the ~1 MB target (lower CRF = higher quality + larger file).

### Command template

```bash
ffmpeg -y -i INPUT.gif \
  -movflags +faststart \
  -pix_fmt yuv420p \
  -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" \
  -c:v libx264 -crf 24 \
  OUTPUT_lq.mp4
```

## Iteration procedure

1. Probe the source (`ffprobe`) for dimensions, frame count and duration.
2. Encode to a temp file at a starting CRF (e.g. 28).
3. Check the output size. Adjust CRF:
   - File too large → raise CRF.
   - Comfortably under budget → lower CRF to reclaim quality.
4. Repeat until the file "barely passes" under ~1 MB, then move it into place.

## Usage on the site

The `_includes/video-gallery.html` include maps each gallery item's
`image_path` GIF to its `_lq.mp4` sibling (`.gif` → `_lq.mp4`) and renders it as
an autoplaying, looping, muted `<video>`. So a compressed file only needs the
correct `_lq.mp4` name to be picked up automatically.

## Example: `assets/papers/judo/judo_viser.gif`

| Property   | Original (`judo_viser.gif`) | Compressed (`judo_viser_lq.mp4`) |
| ---------- | --------------------------- | -------------------------------- |
| Format     | GIF                         | MP4 (H.264 / yuv420p)            |
| Dimensions | 640 × 453                   | 640 × 452                        |
| Size       | ~7.1 MB                     | ~0.89 MB                         |
| CRF used   | —                           | 24                               |

CRF results while iterating: `28 → 584 KB`, `24 → 892 KB`, `22 → 1.1 MB`.
CRF **24** was chosen as the best quality that stays under the 1 MB budget.
