---
# Copy this file to _build/ named YYYY-MM-DD-short-name.md
# (e.g. _build/2026-11-10-first-umap.md). Images go to assets/img/build/<short-name>/

title: "What I did / what happened"
date: 2026-11-10            # must match the date in the file name

# Optional: images shown as a grid under the text.
# Plain paths, or objects with src + caption.
images:
  - /assets/img/build/short-name/screenshot-1.png
  - src: /assets/img/build/short-name/screenshot-2.png
    caption: "Optional caption"

# Optional: links shown at the bottom (repo, notebook, tweet, ...)
links:
  - title: "Notebook"
    url: "https://github.com/VladimirOpaits/..."
---

A few lines about what you built, what worked and what didn't.

You can also put an image anywhere in the text:

{% include figure.html src="/assets/img/build/short-name/plot.png" caption="Caption under the image" %}
