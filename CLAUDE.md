# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

Instructor materials for a 3-day CS Academy (University of Toronto) workshop that
teaches high school students visual effects — specifically structure-from-motion
(SfM) and compositing a 3D model into real filmed footage. This README/repo is for
the instructor, not for students.

The workshop pipeline: extract frames from a short video → run classical SfM via
COLMAP/`pycolmap` to recover per-frame camera pose + a sparse 3D point cloud →
define a ground plane by clicking points in an image → render a 3D mesh with
Panda3D along the recovered camera track and composite it onto the original
footage, so a virtual object appears locked into the scene as the camera moves.

## Repo layout — what's actually live vs. template leftovers

- `notebooks/day_3_sfm_render_composite.ipynb` — the real content. A Colab
  notebook covering the SfM reconstruction + 3D compositing (day 3 of the
  workshop). This is almost always what you're editing.
- `data/table.mp4` — example input video used by the day-3 notebook (as a demo,
  or fallback when a student's own footage fails to reconstruct).
- `lessons/` — written lesson material for each day (`day_1/` currently has intro
  content; day 3's lesson content is not yet written — the notebook is the day-3
  material for now).
- `notebooks/day_1_intro_to_python.ipynb` — companion notebook for the day-1
  Python lesson.
- `lessons/README.md` — syllabus/index; lessons are numbered so they sort in
  reading order and each links back from there.
- `src/`, `deps/`, `pyproject.toml`, `uv.lock`, `main.py` — left over from the
  generic CS Academy project template this repo was forked from. **Not used by
  the day-3 SfM/compositing workshop content**, which runs entirely inside
  Google Colab with no local Python environment. Only relevant if adding new
  local-Python lesson content (e.g. day 1's Python exercises) outside Colab.

There is intentionally no local build/lint/test tooling for the core (day-3)
workshop content — everything runs as notebook cells in Colab.

## Working with the day-3 notebook

- Open `notebooks/day_3_sfm_render_composite.ipynb` in Google Colab (open from
  GitHub, or upload the file) — it is not run locally.
- Requires a GPU runtime (**Runtime > Change runtime type > T4 or better**). The
  SfM reconstruction cell runs `pycolmap` feature extraction/matching on CUDA and
  raises an error rather than silently falling back to CPU if no GPU is attached.
- The first cell installs the deps not preinstalled on Colab (`pycolmap-cuda12`,
  `absl-py`), pinned to match the runtime's driver. Everything else (`ffmpeg`,
  `opencv`, `numpy`, `PIL`, `plotly`, `matplotlib`, `scipy`) is already on the
  default Colab runtime — don't add installs for those.
- Cells run in order and form one pipeline; the notebook's `# @title` cell names
  reflect the pipeline stages (roughly): configure dataset dirs → flatten/resize
  frames → run COLMAP reconstruction → verify SfM worked → load the pycolmap
  scene into a `Camera`/`SceneManager` representation → filter blurry frames →
  normalize the scene (center/scale from landmarks) → export the camera track →
  install Panda3D and render the mesh along the track → calibrate mesh placement
  against a manually-defined table plane → composite onto the source video →
  preview/download.
- "Filter blurry frames" and "verify SfM worked" are natural checkpoints — good
  places to pause with a class and confirm everyone's reconstruction succeeded
  before moving on to compositing.
- Each fresh Colab session needs the GPU runtime re-selected and dependencies
  reinstalled from scratch (no persistence between sessions).
- Before running with a class, do a full dry run: capture (or reuse
  `data/table.mp4`) a short, well-lit, slow-panning clip of a static scene with
  plenty of texture, and confirm reconstruction + compositing complete
  end-to-end on a fresh Colab GPU runtime.
- SfM quality depends heavily on footage quality: slow, steady pans with visible
  texture work; blank walls, reflective/transparent surfaces, and moving
  subjects tend to break reconstruction. Keep this in mind when debugging a
  failed reconstruction cell — footage is the most common root cause, not code.

## Data conventions

Code should load data with paths relative to the project root (e.g.
`"./data/your_file.ext"`) so it resolves the same way for everyone.

## If touching the template leftovers (`src/`, `main.py`, `pyproject.toml`)

- `src/` is meant to hold reusable library modules, re-exported via
  `src/__init__.py` (`from .mymodule import *`) so they're importable as
  `from src import ...`.
- `main.py` `chdir`s to the project root on startup so relative paths (e.g.
  `./data/...`) resolve regardless of invocation directory.
- Dependencies are managed with `uv` (`uv sync` after editing `dependencies` in
  `pyproject.toml`); `uv.lock` is intentionally committed, not gitignored.
- `deps/` is for local/vendored/editable packages, registered via
  `[tool.uv.sources]` in `pyproject.toml`.
- Local notebook server (only relevant for non-Colab notebooks like day 1):
  `uv run jupyter notebook`.
