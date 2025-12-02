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
```
## 2. Floor

Represents a single interactive “room” or “area” (like a Floor796 tile group).
```jsonc
{
  "id": "niflheim_origin_chamber",
  "realmId": "niflheim",
  "name": "Hvergelmir Basin – Origin Chamber",
  "background": "assets/floors/niflheim/origin/bg.png",
  "videos": [
    {
      "id": "mist_vent_1",
      "src": "assets/floors/niflheim/origin/mist_vent_1.mp4",
      "x": 1200,
      "y": 300,
      "width": 128,
      "height": 128,
      "loop": true
    }
  ],
  "hotspots": [
    {
      "id": "vent_1_hotspot",
      "shape": "rect",
      "x": 1190,
      "y": 290,
      "width": 140,
      "height": 140,
      "onClickEvents": ["event_frostburst_vent_1"]
    }
  ],
  "events": ["event_frostburst_vent_1", "event_spirit_drift_1"]
}
```

## 3. Entity
An entity can be visual or logical (e.g., a wolf, spirit, rune).

```jsonc
{
  "id": "wolf_pack_1",
  "type": "creature",
  "subtype": "frostroot_wolf",
  "floorId": "niflheim_origin_chamber",
  "position": { "x": 800, "y": 600 },
  "state": "idle",
  "properties": {
    "speed": 1.2,
    "visionRadius": 200
  }
}
```

## 4. Hotspot
Hotspots define interactive zones the player can click or hover over.

```jsonc
{
  "id": "spirit_hotspot_1",
  "shape": "circle",
  "x": 1500,
  "y": 400,
  "radius": 50,
  "onClickEvents": ["event_spirit_whisper_1"]
}
```
## 5. Event
Events are the core behavior units.
```jsonc
{
  "id": "event_spirit_whisper_1",
  "type": "small",
  "floorId": "niflheim_origin_chamber",
  "triggers": [
    {
      "type": "onClick",
      "targetHotspotId": "spirit_hotspot_1"
    }
  ],
  "actions": [
    {
      "type": "showText",
      "textId": "lore_spirit_whisper_1"
    },
    {
      "type": "playSound",
      "soundId": "spirit_whisper_fx_1"
    }
  ]
}
```
## 6. Trigger Types:

onClick – player clicks a hotspot

onTimer – event fires after a delay or interval

onSequence – a specific order of interactions

onRealmState – something happens depending on broader conditions

onEpicEvent – triggered by an epic cross-realm event



## 7. Action Types (Examples)

showText – show a lore box / whisper

playVideoSegment – temporarily change animation or seek a video

spawnEntity – add a creature or object

despawnEntity – remove something

modifyFloorState – toggle flags (e.g., “ice_cracked = true”)

openPortal – enable traversal to another floor
