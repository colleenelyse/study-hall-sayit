# Pip the Sprite: art files

The live copies are on GitHub Pages (Settings row **Pip art folder link**,
`https://colleenelyse.github.io/study-hall-sayit/pip/`); this folder keeps the originals.

| File | What |
|---|---|
| `pip_idle.webp` | Pip's resting pose, shown whenever nothing plays |
| `animations/pip_anim_[action].webp` (or .png) | sprite sheets: frames in reading order, left to right, then the next row; transparent background |
| `outfits/pip_outfit_[occasion].png` | future outfits (not used yet; each must be designed per animation) |
| `pip_pose_[name].png` | future still poses (waving, sleeping, reading...) |

## Sheets that are not an even grid
Add `layout: 'figures'`: the player finds each figure by its outline and numbers them left to right, row by row
(the idle sheet has 57: rows of 11, 12, 11, 12, 11). Use `sequence: [[frame, ms], ...]` to choose the frames and how long each shows.

## Priorities
`priority: 3` with `loop: true` is the idle loop (the default). One-off animations (`priority: 1`) pause it, play once, then it resumes.
With reduced motion turned on, Pip shows his resting picture instead of the loop.

## Adding an animation
1. Make the sheet with a see-through background, equal cells, Pip the same size in every cell, his feet near the bottom.
2. Name it `pip_anim_[action].webp` and put it in `animations/` on GitHub (sayit/pip/animations) and here.
3. Add one line to `pipAnimations` in Index.html, for example
   `backflip: { src: 'animations/pip_anim_backflip.webp', cols: 4, rows: 3, frameCount: 12, durationMs: 2000, loop: false, anchor: 'feet' }`
   (`anchor: 'feet'` lines his feet up across frames; `'none'` keeps the frames exactly as drawn, for jumps that are part of the art).
4. Play it with `PIP_TEST.play('backflip')`, or from any `new PipAnimationPlayer(canvas)`.
