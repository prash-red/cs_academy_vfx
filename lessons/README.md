# Syllabus

This folder holds the written lessons for the project. Students work through them
in order, and each one should build directly on the previous.

Replace the list below with your own lessons. Number files so they sort in reading
order (`000_...`, `001_...`, ...), and link each one from here with a one-line
summary. The hands-on coding companion for the lessons lives in `notebooks/`.

0. [**Day 1 — Intro to VFX**](day_1/000_intro_to_vfx.md) — an introduction to visual effects, CGI, and how film creates believable impossible scenes.
1. [**Day 1 — Session 2: Draw an Object Across 4 Frames**](day_1/001_draw_object_on_four_frames.md) — a hands-on drawing exercise where students track one object across four frames of video.
2. [**Day 1 — Session 3: Intro to Python**](day_1/002_intro_to_python.md) — students' first hands-on Python session, from `print()` and variables through conditionals, lists, and loops.
3. [**Day 2 — Block 1: Where is the camera?**](day_2/000_camera_pose.md) — camera pose as
   position + forward + up, degrees of freedom, and why a photo cannot tell you size.
4. [**Day 2 — Block 2: From photos to a reconstruction**](day_2/001_sfm_matching.md) — features,
   matching, and solving for a camera from your own clicks.
5. [**Day 2 — Block 3: Putting something in**](day_2/002_placement.md) — choosing a size,
   standing an object on the ground, and why occlusion is hard in real footage.

Day 2's four blocks (a vector primer plus those three) share one Colab notebook,
[`notebooks/day_2/day_2_geometry_and_sfm.ipynb`](../notebooks/day_2/day_2_geometry_and_sfm.ipynb),
and one slide deck,
[`day_2/camera_basics_structure_from_motion.pdf`](day_2/camera_basics_structure_from_motion.pdf).
Each block's note says which slides belong to it.

<!--
Guidelines for writing a lesson:
- One concept per file; assume only what earlier lessons established.
- Explain in plain English first, then formalize.
- Point to the matching notebook exercise so students can apply the idea.
-->
