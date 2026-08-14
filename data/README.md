# Data

Datasets and assets used by the project go here (meshes, images, JSON, etc.).

Code should load data with paths relative to the project root, e.g.
`"./data/your_file.ext"`, so it resolves the same way for everyone.

## Clips

| File | What it is | Used for |
|---|---|---|
| `table.mp4` | Slow pan over a tabletop scene | Day 3 demo / fallback footage |
| `boulder.mp4` | A boulder turning against a black background, 20 s | Day 2 good case: rough and smooth texture on one object, featureless background |
| `wall.mp4` | Handheld pan across a blank white wall | Day 2 failure case: no texture, so no features to match |
| `lego.mp4` | Fast handheld motion over a Lego model | Day 2 failure case: motion blur destroys features |

## day2_data.zip

Day 2's notebook needs `boulder.mp4`, `wall.mp4`, `lego.mp4` and
`precomputed/boulder/`. Inside a checkout it reads them straight from this folder; on Colab it
downloads **`day2_data.zip`** instead and unpacks it, so there is one request rather than
seven. Regenerate the archive whenever any of those change:

```
cd data && zip -r day2_data.zip boulder.mp4 wall.mp4 lego.mp4 precomputed/boulder -x '*overview.png' -x '*keyframes.json' -x '*/sparse/*'
```

`boulder.mp4` is derived from [*360-degree view of the Giebichenstein (Stöckse,
October 2023)*](https://commons.wikimedia.org/wiki/File:360-degree_view_of_the_Giebichenstein_(St%C3%B6ckse,_October_2023).webm)
by Redneptun via Wikimedia Commons, licensed
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0), re-encoded to 1280x720 at
30 fps. It is a render of a photogrammetric scan of the real boulder. Attribution
must be kept wherever it is shown.
