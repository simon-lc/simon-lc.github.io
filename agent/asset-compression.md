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

## Compressing longer / high-resolution videos (`assets/release/**`)

The ~1 MB budget above is tuned for short gallery GIFs. Longer clips and
high-resolution footage (e.g. multi-second 1080p/4K `.mp4` demos under
`assets/release/**`) need a larger budget to stay watchable. For these:

- Preserve the original file (never overwrite it) and write a `_lq.mp4` sibling.
- Target **just under 5 MB** per file — small enough for fast web delivery,
  large enough to keep motion-heavy footage clean.
- Downscale to a max of **1080p** (web-friendly): `scale='min(1920,iw)':-2`
  keeps the aspect ratio, caps width at 1920, and forces an even height.
- Drop the audio track (`-an`) — these are silent visual demos.
- Prefer web-quality **CRF ~26** first; if the result exceeds 5 MB, fall back to
  a **two-pass** encode at a computed bitrate so the size stays capped.

### CRF-first command (try this first)

```bash
ffmpeg -y -i INPUT.mp4 \
  -movflags +faststart \
  -pix_fmt yuv420p \
  -vf "scale='min(1920,iw)':-2" \
  -c:v libx264 -crf 26 -preset slow -an \
  INPUT_lq.mp4
```

### Two-pass fallback (when CRF 26 is over 5 MB)

Compute the target video bitrate from the duration and a ~4.6 MB budget
(leaving container headroom so the final file lands just under 5 MB):

```bash
DUR=$(ffprobe -v error -show_entries format=duration \
  -of default=noprint_wrappers=1:nokey=1 INPUT.mp4)
BR=$(python3 -c "print(int(4.6*1024*1024*8/${DUR}/1000))")   # kbit/s

ffmpeg -y -i INPUT.mp4 -vf "scale='min(1920,iw)':-2" -pix_fmt yuv420p \
  -c:v libx264 -b:v ${BR}k -preset slow -pass 1 -an -f mp4 /dev/null
ffmpeg -y -i INPUT.mp4 -movflags +faststart -vf "scale='min(1920,iw)':-2" \
  -pix_fmt yuv420p -c:v libx264 -b:v ${BR}k -preset slow -pass 2 -an \
  INPUT_lq.mp4

rm -f ffmpeg2pass-0.log ffmpeg2pass-0.log.mbtree
```

### Example: `assets/release/spot_smpc/`

All source `.mp4` clips were compressed to `_lq.mp4` siblings (originals kept),
downscaled to 1080p and capped under 5 MB:

| File                        | Original | `_lq.mp4` | Method    |
| --------------------------- | -------- | --------- | --------- |
| `spot_rl_training`          | ~48.0 MB | ~5.0 MB   | two-pass  |
| `spot_smpc_blender`         | ~33.3 MB | ~4.7 MB   | two-pass  |
| `spot_tire_drag`            | ~14.4 MB | ~4.3 MB   | CRF 26    |
| `spot_tire_rl_upright`      | ~29.5 MB | ~4.3 MB   | CRF 26    |
| `spot_tire_roll_circle`     | ~65.6 MB | ~4.9 MB   | two-pass  |
| `spot_tire_roll`            | ~14.1 MB | ~4.8 MB   | CRF 26    |
| `spot_tire_stack`           | ~19.5 MB | ~4.9 MB   | two-pass  |
| `spot_tire_upright`         | ~8.2 MB  | ~2.3 MB   | CRF 26    |
