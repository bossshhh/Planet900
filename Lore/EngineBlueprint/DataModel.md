# Planet900 Data Model

This document defines the core data structures for the Planet900 engine.

The goal is to make realms, floors, entities, and events data-driven.

---

## 1. Realm

Represents a mythological domain (e.g., Niflheim, Asgard, Midgard).

```jsonc
{
  "id": "niflheim",
  "name": "Niflheim",
  "description": "The Frostroot Realm, primordial ice and memory.",
  "floors": ["niflheim_origin_chamber", "niflheim_thousand_foot_glacier"]
}
