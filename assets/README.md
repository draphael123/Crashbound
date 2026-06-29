# Crashbound — character art brief (Darkest-Dungeon style)

Drop PNG sprite strips here to replace the built-in vector characters. Missing files
fall back to the vector rendering automatically — nothing breaks. The engine already
animates **idle / walk / attack** states, so frame-animated art plays in-game with no
code changes beyond the manifest.

---

## 1. Art-direction brief (what "Darkest Dungeon" means here)

- **Ink:** heavy, variable-weight near-black outlines; bold spot-black shadow shapes;
  minimal soft mid-tones. Mike Mignola / Hellboy sensibility.
- **Palette:** grim and desaturated — muted earth, iron, bruise tones. Reserve
  saturated color for tiny accents (torch orange, blood red, arcane cyan).
- **Lighting:** hard directional torch-light from one side (the game lights from the
  lower corners). Bright warm rim on the lit edge, the rest sinking into shadow.
- **Silhouette:** exaggerated, readable at a glance — hunched backs, big shoulders,
  oversized hands/weapons, strong gesture. The shape should read with zero color.
- **Texture:** subtle paper/ink grain is welcome; the engine also overlays grain + vignette.

Cast (ids): `brand` (bronze knight), `wisp` (steel-blue mage), `grunt` (sickly-green
goblin), `brute` (bruised-purple ogre), `archer` (leather hood), `elite` (blood-red
ogre captain), `boss` (dark-iron warlord).

## 2. Sprite-sheet format

- **One horizontal strip per state**, equal-width frames left → right, **transparent PNG**.
- Character **feet-anchored at bottom-center**, **facing right** (engine mirrors for left).
- Frame box ~**128 × 160 px** (engine scales to ~132 px tall, preserves aspect).
  4 frames → 512 × 160; 6 frames → 768 × 160.
- States & how the engine plays them:
  - `idle` — **required**, ~4 frames, looped slowly (gentle breathe/sway).
  - `walk` — optional, ~6 frames, looped (used in the village + map travel).
  - `attack` — optional, ~6 frames, played **once across the swing** (anticipation →
    strike → recover). Frame 0 = wind-up, last frame = follow-through.
- Keep the figure roughly centered frame-to-frame so it doesn't jitter.

## 3. Enable it

In `index.html`, fill `SPRITE_MANIFEST`:

```js
const SPRITE_MANIFEST = {
  brand: { idle:{src:'assets/brand_idle.png',frames:4},
           walk:{src:'assets/brand_walk.png',frames:6},
           attack:{src:'assets/brand_attack.png',frames:6} },
  wisp:  { idle:{src:'assets/wisp_idle.png',frames:4} },   // idle-only is fine
};
```

Overlays still render over sprites (freeze ice, burn flames, hit-flash, airborne ✦,
screen-shake, the torch rim-light, and the rig's lean/lunge motion), so even idle-only
art gains motion for free.

## 4. Where to get the art (the engine doesn't generate it)

- **Commission** a 2D/pixel artist — hand them §1 + §2.
- **Generate** base frames with an external image tool, then clean up and cut into an
  even horizontal strip (Aseprite: File → Export Sheet → horizontal).
- For full DD-grade weighty animation, deliver a **rigged skeleton** (Spine/Spriter);
  ping me and I'll extend the loader to a per-part bone format (the rig in this engine
  already poses parts procedurally, so it's a natural upgrade).
