# Day 2 — Block 1: Where is the camera?

A camera pose is where a camera stands and which way it looks. The block ends on the fact
that a photograph cannot tell you how big anything is. Day 3 assumes both without explaining
either.

**Students should be able to:** say what a pose is in day 3's form (a position, a `forward`
and an `up`); normalize a vector; count degrees of freedom and say why a free camera has 6;
say why a look-at direction alone is not enough; and say why enlarging a scene *and* the
camera's distance together leaves the photo unchanged.

**Notebook:** [`day_2_geometry_and_sfm.ipynb`](../../notebooks/day_2/day_2_geometry_and_sfm.ipynb)
— all four blocks, two setup cells, no runtime change needed.

## Deck — slides 1–7

[`camera_basics_structure_from_motion.pdf`](camera_basics_structure_from_motion.pdf)

1. Title
2. Motivation: a reconstruction, and what we want from it — camera positions and scene structure
3. How this fits the VFX pipeline — the Mandalorian shot
4. The same shot split: tracked points for scene structure, a render needing a camera pose
5. **What do we mean by a camera?** The panda, its position (orange dot) and orientation (red
   frustum), and three candidate photos — *which one is ours?* → hook for Exercises 1–3
6. **Putting it into numbers** — three axes, a point at (3, 2, 4), a **vector** → the primer
7. **How large is this rooster?** Alone, against the wall, with a person → Exercises 4–5

## The notebook

**Block 0, the vector primer (~10 min).** Three numbers, the axes, length, normalizing,
adding, times a number — a flat map first, then the third number. It exists so that
"normalize `forward`" later is recall, not first contact.

1. **One dial.** Camera on a ring, always aimed at the middle. Match the target photo.
2. **Six dials.** Three to move, three to turn. Moving no longer re-aims, so wandering loses
   the scene. The 3D panel shows both cameras.
3. **Six dials, one cube.** Every landmark removed — many poses now look alike.
   *(showcase)* **What is still free?** Same position, same `forward`, and the picture still
   changes.
4. **Multiply the whole world.** Take predictions first. The photo does not change at all.
5. **Two dials that used to be one.** Only the ratio matters.

The notebook's Minecraft question sits between 2 and 3; the block turns from *where* to *how
big* after the showcase.

## Pacing (~75 min, primer included)

Primer 10 · slides + Ex 1 20 · Ex 2 and the Minecraft question 12 · Ex 3 8 · *is that
enough?* and how a pose is stored 13 · rooster slide + Ex 4–5 12.

Natural break before the rooster; the size material opens the afternoon well.

## Discussion prompts

- Exercise 1 gave you one dial. What did we decide for you that a photographer chooses?
- Two students matched the target from visibly different positions. How?
- Why store `forward` and `up` rather than all three directions?
- What told you how large the rooster is — and where did that come from?
