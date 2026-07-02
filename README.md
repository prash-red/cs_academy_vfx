# CS Academy VFX Workshop — Instructor Guide

Materials for a 3-day CS Academy (University of Toronto) workshop introducing
high school students to visual effects, specifically **structure-from-motion
(SfM)** and inserting a 3D model into a real filmed scene. This README is for
the instructor running the workshop, not for students.

## What the workshop covers

Starting from a short video of a real scene, students:

1. Extract frames from the video.
2. Run classical structure-from-motion (via COLMAP / `pycolmap`) to recover
   the camera's position, orientation, and focal length at every frame, plus a
   sparse 3D point cloud of the scene.
3. Define a plane in the scene (e.g. a tabletop) by clicking points in an
   image.
4. Render a 3D mesh with Panda3D along the recovered camera track and
   composite it onto the original footage, so a virtual object appears locked
   into the scene as the camera moves.

Day 3 is where the SfM reconstruction and compositing happen; this repo's
notebook covers that day.

## What's in this repo

For now this repo intentionally holds only two things:

- **Slides** for each day's lecture/lesson material (to be added — not yet
  present in the repo).
- **Colab notebooks** — the hands-on part students run.

```
notebooks/
  day_3_sfm_render_composite.ipynb   # SfM reconstruction + 3D compositing
data/
  table.mp4                          # Example input video for the notebook
```

There is no local Python environment to install and nothing needs to run
outside of Google Colab. The `lessons/`, `src/`, `deps/`, `pyproject.toml`,
`uv.lock`, and `main.py` files are left over from the generic CS Academy
project template this repo was forked from — they are not used by this
workshop and can be ignored.

## Running the notebook (instructor)

1. Open `notebooks/day_3_sfm_render_composite.ipynb` directly in
   [Google Colab](https://colab.research.google.com/) (open from GitHub, or
   upload the file).
2. Set **Runtime > Change runtime type > T4 GPU or better**. The SfM
   reconstruction cell runs `pycolmap`'s feature extraction/matching on CUDA
   and raises an error instead of silently falling back to CPU if no GPU is
   attached.
3. Run the cells in order. The first cell installs the dependencies not
   preinstalled on Colab (`pycolmap-cuda12`, `absl-py`), pinned to match the
   runtime's driver — everything else (`ffmpeg`, `opencv`, `numpy`, `PIL`,
   `plotly`, `matplotlib`, `scipy`) is already on the default Colab runtime.
4. When prompted, upload a video, or use `data/table.mp4` as a ready-made
   example to demo the pipeline or as a fallback if a student's own footage
   doesn't reconstruct well.

Before running this with a class, it's worth doing a full dry run yourself:
capture (or reuse `table.mp4`) a short, well-lit, slow-panning clip of a
static scene with plenty of texture, and confirm the reconstruction and
compositing cells complete end-to-end on a fresh Colab GPU runtime.

### Tips for running it live with students

- Have students shoot slow, steady pans with visible texture (avoid blank
  walls, reflective/transparent surfaces, and moving subjects) — SfM quality
  depends heavily on footage quality, and this is the most common source of
  a failed reconstruction.
- The "filter blurry frames" and "verify SfM worked" cells are the natural
  checkpoints to pause at and check that everyone's reconstruction succeeded
  before moving on to compositing.
- Each Colab session needs a GPU runtime re-selected and dependencies
  reinstalled from scratch, so budget a few minutes at the start of the
  session for that.
