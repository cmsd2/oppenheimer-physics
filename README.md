# The physics in *Oppenheimer*

[![Render](https://github.com/cmsd2/oppenheimer-physics/actions/workflows/render.yml/badge.svg)](https://github.com/cmsd2/oppenheimer-physics/actions/workflows/render.yml)
[![Review](https://img.shields.io/badge/review-online-blue)](https://cmsd2.github.io/oppenheimer-physics/)

Read it online at **<https://cmsd2.github.io/oppenheimer-physics/>**, or as a
[PDF](https://cmsd2.github.io/oppenheimer-physics/oppenheimer-physics.pdf).

A literature review of the physics in Christopher Nolan's *Oppenheimer*
(2023). It starts with what historians and physicists wrote about the film,
then goes through the physics in the order the film meets it, from the
Born–Oppenheimer approximation to the hydrogen bomb. For each topic it gives
the original paper or report, the key equations, and a short Python
calculation that checks the numbers: the Oppenheimer–Volkoff limit, the
critical mass of uranium-235, Taylor's estimate of the Trinity yield, and
others.

`index.qmd` is the review and `references.bib` its bibliography. Journal
articles in the bibliography were checked against Crossref.

Set up from [maths-notes-template](https://github.com/cmsd2/maths-notes-template),
without the Lean and Maxima parts.

## Building

Needs [Quarto](https://quarto.org), [uv](https://docs.astral.sh/uv/) and
LuaLaTeX for the PDF.

```sh
uv sync
uv run quarto render       # HTML and PDF into _site/
uv run quarto preview
```

Run Quarto through `uv run` so the code cells use the project's Python.
`freeze: auto` saves code results in `_freeze/` and re-runs them only when
`index.qmd` changes; commit `_freeze/`.

The PDF hides code and shows results. The HTML folds the code under each
calculation and sets its text in Latin Modern to match the PDF.

## CI and GitHub Pages

`.github/workflows/render.yml` renders the HTML and PDF on every push and
pull request, and publishes `_site/` to GitHub Pages on pushes to the
default branch. Pages has to be switched on once, with GitHub Actions as the
source (Settings → Pages), or:

```sh
gh api -X POST repos/cmsd2/oppenheimer-physics/pages -f build_type=workflow
```
