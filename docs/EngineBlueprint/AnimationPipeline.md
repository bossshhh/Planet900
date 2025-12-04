
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

- Duration: **3-5 for small reoccurring loops, 5-10 for medium event loops, & 20+ seconds for big events ** per loop
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

```markdown
Notes:

-framerate 12 → 12 FPS

-g 10 -keyint_min 10 → keyframe every 10 frames (for sync)

-crf 18 → good quality/size balance, tweak as needed


---
## 4.Placing Animations in Floors

```jsonc
(as an initial thought)
{
  "id": "mist_vent_1",
  "src": "assets/floors/niflheim/origin/mist_vent_1.mp4",
  "x": 1200,
  "y": 300,
  "width": 128,
  "height": 128,
  "loop": true
}
```markdown

The viewer:

Creates <video> elements for each entry

Positions them absolutely over the background

Ensures they all start together

## 5.Syncing Animations

Because MP4 playback can drift slightly between elements, sync is maintained by:

Using a fixed loop duration (5 seconds)

Using regular keyframes every 10 frames

Periodically (e.g., every 5 seconds) resetting all videos to currentTime = 0
to realign them at loop boundaries

## 6.Future Editor Integration

The long-term goal:

The editor can:

Draw on <canvas>

Manage layers

Scrub through frames

Preview loops

Export PNG sequences and a metadata file

The build pipeline:

Automatically encodes animations

Updates floor JSON with correct paths and sizes
This pipeline allows Planet900 to scale to many floors and realms while keeping
file sizes manageable and animation authoring efficient.
