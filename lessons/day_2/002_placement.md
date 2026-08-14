# Day 2 — Block 3: Putting something in

The handoff to day 3. Having just made a reconstruction, students meet the fact that it has
no size — and do the practical thing: guess, place, look, adjust.

**Students should be able to:** say why a reconstruction has shape but no size, and that the
size is chosen; say what the **origin** is; describe centring a scene and dividing by its
bounding box; place an object on a ground plane; and say why overlap is free here and hard in
real footage.

## Deck — slides 13–17

[`camera_basics_structure_from_motion.pdf`](camera_basics_structure_from_motion.pdf)

13. *Part 3: Inserting an Object*
14. **Tomorrow** — the desk clip beside its reconstruction and camera path
15. **What good capture means** — two frames of the desk with the matches drawn between them
16. **Scene structure** — the axes gizmo anchored in the desk: we want to anchor the insertion
    somewhere
17. **A plane in the point cloud**, from two angles → the setup for Exercise 11

## The notebook

Opens by picking up the thread parked in Block 1: nothing in the footage says whether the rock
is a pebble or the size of a car. So **guess a size, put it in, look, adjust** — a slider and
their eyes. Worth saying plainly that this is the job, not a workaround, and exactly what they
do tomorrow.

- *(showcase)* **One panda in a box.** A bounding box, the origin marked well away from it, and
  a toggle that centres it and scales the box to 1 across. The printed numbers follow.
11. **Put the ground where it belongs.** One slider until the panda stands on the plane; the
    readout says "sunk" or "floating" without giving the number away.
12. **A panda family.** A button adds up to five, all arriving at the origin. Five dials each:
    along, across, height, size, facing — one rotation only, because a panda cannot lean.

Closes on occlusion: the renderer knows the distance to every surface it drew, so overlap is
free. Tomorrow the background is a photograph with no depth attached, which is why real VFX
needs compositing.

## Pacing (~35 min)

Framing + the two concepts 8 · box showcase 5 · Ex 11 5 · Ex 12, competitively 12 · occlusion
and the question into tomorrow 5.

## Discussion prompts

- What would break if we left every reconstruction at whatever size it came out?
- Two pandas at the same size setting, one near and one far, look very different. Is either
  the wrong size?
- The renderer handled overlap without being asked. What does it know that it will *not* know
  about tomorrow's video?
