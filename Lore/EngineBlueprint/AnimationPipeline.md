
---

### `AnimationPipeline.md`

```markdown
# Planet900 Animation Pipeline

Planet900 uses a Floor796-style animation system:
- Short pixel-art loops
- Synchronized MP4 tiles
- Data-driven placement on floors

---

## 1. Animation Specs

- Duration: **5 seconds** per loop
- Framerate: **12 FPS**
- Frames per animation: **60**
- Style: pixel art (raster)

Each animation typically has:
- A background or static base
- One or more moving elements:
  - Vents, flames, spirits, water, etc.

---

## 2. Frame Creation

Frames can be created by:

- The custom browser-based editor (`editor/`)
- External pixel-art tools (e.g., Aseprite, Krita) with export to PNG

Recommended output:
- `animName_000.png` … `animName_059.png`

---

## 3. Encoding to MP4

Use `ffmpeg` (or similar) to convert the 60 PNG frames into an MP4 loop.

Example command:

```bash
ffmpeg -framerate 12 -i animName_%03d.png \
  -c:v libx264 -pix_fmt yuv420p \
  -profile:v high -crf 18 \
  -g 10 -keyint_min 10 \
  animName.mp4
