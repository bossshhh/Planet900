# Contributing to Planet900

Thanks for your interest in contributing to Planet900!

This document explains how to contribute code, lore, or ideas in a way that
keeps the project consistent and maintainable.

---

## 1. Project Vision

Planet900 is:
- A Floor796-style interactive pixel-art multiverse
- Driven by data (JSON / configs) rather than hard-coded content
- Built on mythological realms that can expand over time
- Both a technical project and a worldbuilding project

Contributions should:
- Respect the core style (pixel loops, mythic tone)
- Fit within the established world rules (see `docs/WorldBook`)
- Follow the engine structure (see `docs/EngineBlueprint`)

---

## 2. Code Contributions

1. **Fork the repo** and create a feature branch:
   - `feature/add-basic-viewer`
   - `feature/editor-canvas-tools`
2. Follow general best practices:
   - Keep functions short and readable
   - Use clear naming
   - Prefer data-driven behavior where possible
3. If adding dependencies, document them in the README or a dedicated section.
4. Open a **Pull Request** with:
   - Description of what you did
   - Screenshots or GIFs if it affects visuals
   - Any notes about future work or limitations

---

## 3. Lore / Worldbuilding Contributions

1. Read existing docs in `docs/WorldBook/` to understand the world.
2. Propose new:
   - Realms
   - Floors
   - Events
   - Entities
   - Epic arcs
3. Add them as markdown drafts in `docs/WorldBook/` and open a Pull Request.
4. Avoid contradicting core established canon without discussion.

---

## 4. Art / Animation Contributions
Planet900 Uses a Multi-Length Animation System:
1. the core specs:
   - Pixel art
   - 3-5 seconds for small loops, 5-10 seconds for medium loops, & 20+ seconds for long event loops
   - 12 FPS (60 frames)
2. Provide:
   - PNG frame sequences
   - Or ready-made MP4 loops
   - Any palette or style notes
3. Place work under appropriate folders in `assets/` (once created).
4. All art contributions must follow the `LICENSE_ASSETS.txt` terms.

---

## 5. Issue Tracking & Suggestions

- Use GitHub Issues to:
  - Report bugs
  - Suggest features
  - Propose realms, floors, or events
- Tag issues appropriately (e.g., `engine`, `viewer`, `editor`, `lore`).

---

## 6. Licensing & Ownership

By contributing, you agree that:
- Code contributions are licensed under the MIT License (see `LICENSE_CODE.txt`)
- Art and lore contributions fall under the Planet900 Creative Assets License
  (see `LICENSE_ASSETS.txt`), unless explicitly negotiated otherwise.

If you want special credit or have concerns, open an issue or mention it in
your Pull Request.

---

Thanks again for helping build Planet900.
