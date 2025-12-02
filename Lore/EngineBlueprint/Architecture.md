# Planet900 Engine Architecture

Planet900 is built as a browser-based interactive world, inspired by Floor796.
The engine is split into three main parts:

1. **Viewer** – What players see (interactive floors, videos, events)
2. **Editor** – Internal pixel-art and animation tool
3. **Content Layer** – JSON/configs that define realms, floors, entities, and events

---

## 1. Viewer

The viewer is a web application responsible for:

- Rendering backgrounds for each floor
- Placing and syncing looping animations (MP4 `<video>` tiles)
- Handling camera movement (panning/zoom)
- Managing clickable hotspots
- Dispatching and handling events
- Loading floor definitions from JSON or JS objects

**Technologies:**
- HTML, CSS, JavaScript (or TypeScript)
- `<video>` elements for tile animations
- Optional Canvas overlay for special effects / hitboxes

---

## 2. Editor

The editor is an internal, browser-based pixel animation tool.

Goals:
- Draw pixel art in a custom palette
- Support multiple layers (background, midground, characters, effects)
- Provide a timeline for 5-second, 12 FPS loops (60 frames)
- Export:
  - Frame sequences (PNG)
  - Metadata (layers, positions)
  - Animation configs

**Technologies:**
- HTML + CSS + JavaScript
- `<canvas>` API for drawing
- Browser File System Access API (for saving/loading large scene files)

---

## 3. Content Layer

The content layer is data-driven. It describes:

- Realms
- Floors
- Entities
- Hotspots
- Events
- Lore

This allows adding new content mostly by editing JSON or markdown, not by
changing engine code.

---

## 4. Build & Asset Pipeline

Pipeline overview:

1. Draw and animate scenes with the editor (60 frames per animation)
2. Export PNG frames
3. Use ffmpeg (or similar) to encode frames → MP4 loops
   - 12 FPS
   - Keyframe every 10 frames (for sync)
4. Place videos and metadata into floor configs
5. Viewer loads the configs and displays the world

---

## 5. Separation of Concerns

- Viewer code should not hard-code “Niflheim” or “Asgard”
- Editor should not depend on specific lore
- Content should be independent data files that both systems can work with

This enables Planet900 to scale: many floors, many realms, one engine.
