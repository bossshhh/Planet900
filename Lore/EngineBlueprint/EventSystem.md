
---

### `EventSystem.md`

```markdown
# Planet900 Event System

The event system drives all dynamic behavior in Planet900: ambient activity,
floor changes, and cross-realm consequences.

---

## 1. Event Categories

Events are categorized by scale:

- **Small:** Local, frequent, low impact
- **Medium:** Stronger visual/behavioral changes, moderate impact
- **Big:** Rare, floor- or realm-altering
- **Epic:** Cross-realm, multi-floor narrative events

---

## 2. Lifecycle of an Event

1. **Definition:**  
   Event exists as data (JSON) with triggers and actions.

2. **Registration:**  
   On floor load, relevant events are registered with the event system.

3. **Listening:**  
   Triggers listen for:
   - User input (click, hover)
   - Timers
   - Other events firing
   - Realm or global state

4. **Activation:**  
   When all trigger conditions match, the event fires.

5. **Execution of Actions:**  
   Actions run in sequence or parallel:
   - Show text
   - Play animation
   - Spawn entities
   - Open portals
   - Modify state

6. **Aftermath:**  
   Event may:
   - Mark itself used (one-time)
   - Schedule itself to repeat
   - Change into another variant

---

## 3. Triggers

Examples:

```jsonc
{
  "type": "onClick",
  "targetHotspotId": "vent_1_hotspot"
}

{
  "type": "onTimer",
  "delayMs": 30000,
  "repeat": true
}

{
  "type": "onSequence",
  "sequence": ["rune_1", "rune_3", "rune_2"]
}

{
  "type": "onEpicEvent",
  "epicEventId": "epic_primordial_wakes"
}

---

## 4. Actions
Examples: 
``jsonc
{
  "type": "showText",
  "textId": "lore_spirit_whisper_1"
}

{
  "type": "spawnEntity",
  "entityTemplateId": "wolf_standard",
  "position": { "x": 900, "y": 580 }
}

{
  "type": "modifyFloorState",
  "key": "ice_cracked",
  "value": true
}
{
  "type": "openPortal",
  "fromFloorId": "niflheim_origin_chamber",
  "toFloorId": "niflheim_thousand_foot_glacier",
  "portalId": "rift_1"
}

---

## 5. Stateful vs Stateless Events

``markdown
#Stateless:
Can always fire when triggered (good for small ambient events).

Stateful:
Maintain flags:

hasFiredOnce

cooldownEndTime

isEnabled

These events can:

Fire once and never again

Fire periodically

Unlock or lock subsequent events

---

## 6. Integration with Epic Events
``markdown
Epic events (like The Midgard Convergence) are represented as:

High-level state flags

Large event definitions that may:

Affect multiple floors at once

Trigger cascades of smaller events

The event system should support:

Global event state (per realm or globally)

Subscriptions to epic event status
