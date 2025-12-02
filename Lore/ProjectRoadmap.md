# Planet900 – Project Roadmap

This document outlines the development plan for Planet900: a Floor796-style,
browser-based interactive pixel-art multiverse.

The roadmap is organized into phases. Each phase should produce something
playable or visibly useful, so the project always feels alive.

---

## Phase 1 – Minimal Viewer Slice (Niflheim Origin Chamber)

**Goal:** A tiny but real, interactive demo.

**Deliverables:**
- A static background image for Niflheim’s Origin Chamber
- A basic HTML page in `viewer/` that:
  - Displays the floor background
  - Allows panning/scrolling
  - Defines a few clickable hotspots (vents, spirits, runes)
  - Shows simple popups (whispers, tooltips) on click
- A small JSON (or JS object) describing the floor layout and hotspots

**Success condition:**  
Can open an HTML file in the browser and interact with a rough Origin
Chamber scene.

---

## Phase 2 – Looping Animation Tiles (Floor796-Style)

**Goal:** Add real animated loops like Floor796.

**Deliverables:**
- A few hand-made 5-second, 12 FPS animations (60 frames each)
- A simple ffmpeg script/command to convert PNG frames → MP4 loops
- A viewer page that:
  - Places multiple `<video>` elements over the background
  - Plays them in sync
  - Periodically resyncs based on keyframes (e.g., every 10th frame)

**Success condition:**  
A “living” Origin Chamber: vents breathing mist, spirits flickering,
small idle animations looping.

---

## Phase 3 – Data-Driven Floors

**Goal:** Make the world described by data files, not hard-coded JS.

**Deliverables:**
- Data model defined in `docs/EngineBlueprint/DataModel.md`
- A JSON format for:
  - Realms
  - Floors
  - Entities
  - Hotspots
  - Events
- Viewer code that:
  - Loads floor JSON
  - Spawns videos/hotspots based on config
  - Attaches event handlers from the data

**Success condition:**  
Can add a new floor (e.g., Thousand-Foot Glacier) mostly by editing JSON,
not rewriting code.

---

## Phase 4 – Event System v1

**Goal:** Add small and medium events.

**Deliverables:**
- Implement event types:
  - Small events (e.g., Frostburst, Spirit Drift)
  - Medium events (e.g., Wolf Hunt, Abyssal Surge)
- Trigger types:
  - On click
  - On timer
  - On sequence (e.g., runes in order)
- Event engine implementation described in `EventSystem.md`

**Success condition:**  
On the Origin Chamber and Glacier floors, events trigger as designed, some
repeatable, some cyclical.

---

## Phase 5 – Niflheim Slice (Multi-Floor)

**Goal:** Make Niflheim feel like a real realm.

**Deliverables:**
- Implement:
  - Origin Chamber
  - Thousand-Foot Glacier
  - Silent Plains
  - Frostroot Labyrinth
  - River Gjöll (basic)
- Floor-to-floor traversal:
  - Clicks/portals/edges move between floors
- Lore-driven UI ([docs/WorldBook/002_Niflheim.md] as reference)

**Success condition:**  
Niflheim is explorable as a connected multi-floor area with events and secrets.

---

## Phase 6 – Asgard & First Cross-Myth Links

**Goal:** Start Inter-realm & cross-myth events.

**Deliverables:**
- Basic Asgard floor(s) (e.g., Odin’s Hall, Bifrost segment)
- Implement:
  - “Wukong’s Asgard Intrusion” (early version)
  - Hooks for “The Primordial Wakes”
- Add first use of epic events described in `003_EpicEvents.md`

**Success condition:**  
You can travel from Niflheim to Asgard, see cross-realm hints/events.

---

## Phase 7 – Midgard & The Midgard Convergence

**Goal:** Launch the first major hero crossover event.

**Deliverables:**
- Midgard convergence area floor
- Implement:
  - Thor, Heracles, Wukong, Cú Chulainn entities
  - The “Midgard Convergence” event (basic version)
- Add visual + textual lore for this epic moment

**Success condition:**  
Can witness the Midgard Convergence event in a rough but working way.

---

## Phase 8+ – Expansion & Polish

After core systems and a few realms exist, future phases include:

- More realms (Greek Underworld, Egyptian Duat, Celtic Otherworld, etc.)
- More epic events:
  - The Thirteenth Labor (Heracles in Helheim)
  - Surtr’s Hesitation
  - Fully realized Primordial Wakes
- Improved editor in `editor/`:
  - Timeline UI
  - Palette tools
  - Per-floor config
- Performance optimization, better UI/UX, contributions from others.

Planet900 is meant to grow slowly over time, floor by floor, event by event.
