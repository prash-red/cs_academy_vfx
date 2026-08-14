# Day 2 — Block 2: From photos to a reconstruction

The block day 3 rests on. Students play the matcher, then watch a camera get solved from
their own clicks, right or wrong.

**Students should be able to:** say what structure from motion recovers and why cameras are
solved before points; say why corners can be found again and blank walls cannot; count 6
unknowns per camera against 2 equations per matched point; and say why one bad match ruins a
solve.

## Deck — slides 8–12

[`camera_basics_structure_from_motion.pdf`](camera_basics_structure_from_motion.pdf)

8. *Part 2: Structure from Motion*
9. **Problem setting** — two views, the same point landing at `x1` and `x2`. Recover the
   camera motion and the 3D structure
10. **How to solve** — position is 3 degrees of freedom, orientation another 3, **six
    overall**; a geometric constraint turns matches into a **linear system**
11. **Bottom line** — find *enough matching pixels* and the system is solvable
12. **The pipeline** — the real COLMAP diagram, with feature extraction and matching flagged
    as what comes next → Exercises 6–10 live here

## The notebook

Exercises 6–10, shaped as **predict, then reveal**.

6. **A look at the clip.** The footage plays, then six stills.
7. **Click the same ten spots.** Nine the matcher itself gets right; **one is not on the rock
   at all**. The feedback picture draws a line from each click to the true spot — spot 10 gets
   none. Say out loud that we can only grade this because the rock was solved in advance.
   *(showcase)* What the algorithm found: ~340 points per frame, 83 matched.
8. **The blank wall.** 1 point in one frame, 0 in the other, 0 matches. Predictions first.
9. **Motion blur.** 109 and 71 points but only 3 matches, one visibly wrong. Predictions first.
10. **Solve for the camera**, using **every** point, mistakes included. Then `good_points`, the
    one visible code cell: try three good clicks, then three bad ones.

**Two discussion beats.** After 7: which spots were easy, which hard, and what the right
answer would be for the one that was never on the rock. Before 8 and 9: sort a brick wall, a
painted door, gravel, a window, a lake, a bookshelf and a green screen into easy and hard.

## Pacing (~70 min)

Slides 9–11 6 · Ex 6 + Ex 7 with feedback 20 · discussion + findability slides 12 · showcase,
predictions, Ex 8–9 15 · counting argument 8 · Ex 10 and `good_points` 12.

## Discussion prompts

- Which spot was worst, and what did that bit of rock look like?
- Spot 10 was never on the rock. What would a *correct* answer even mean?
- The wall gave 1 point. How would you film a white room for a VFX shot?
- Removing your bad clicks snapped the camera back. In a real reconstruction nobody knows
  which match was bad — so how could a computer do it?
