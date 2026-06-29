# Crashbound — character art (sprite sheets)

Drop PNG art here to replace the built-in vector characters. If a file is missing,
the game falls back to the vector rendering automatically — nothing breaks.

## How to enable

In `index.html`, find `SPRITE_MANIFEST` and uncomment / add entries:

```js
const SPRITE_MANIFEST = {
  brand: {src:'assets/brand.png', frames:4},
  wisp:  {src:'assets/wisp.png',  frames:4},
  grunt: {src:'assets/grunt.png', frames:4},
  brute: {src:'assets/brute.png', frames:4},
  archer:{src:'assets/archer.png',frames:4},
  elite: {src:'assets/elite.png', frames:4},
  boss:  {src:'assets/boss.png',  frames:4},
};
```

Valid ids: `brand, wisp, grunt, brute, archer, elite, boss`.

## Sprite-sheet format

- **One horizontal strip per character**, `frames` equal-width frames left→right (an idle loop; the game cycles them ~6.7 fps).
- **Transparent background** (PNG with alpha).
- The character should be **feet-anchored at the bottom-center** of each frame, **facing right** (the engine mirrors it for left-facing).
- Recommended frame size: **~128 × 160 px** (the engine scales to ~132 px tall and preserves aspect ratio).
- Example sheet for 4 frames: **512 × 160 px** (4 × 128 wide).

## Where to get the art

This engine just *renders* the PNGs — it doesn't generate them. Options:
- Commission a pixel/vector artist (give them the format above).
- Generate with an external image tool, then cut into an even horizontal strip.
- Export from a tool like Aseprite (File → Export Sheet → horizontal strip).

## Notes

- Overlays still work over sprites: freeze (ice), burn (flames), hit-flash, the
  airborne ✦, screen-shake, idle bob, walk stride offset, and the attack lunge.
- For per-state animation (separate walk/attack rows) we can extend the manifest
  later; v1 uses a single idle strip and reuses the engine's motion offsets.
