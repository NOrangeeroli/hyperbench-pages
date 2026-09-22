# Hyperbench documentation website

Public documentation for the hyperbolic PDE solver benchmark. The code repository
remains private. This repository contains only the reading site, case descriptions,
usage examples, model documentation and an allowlisted frozen result figure.

Live site: https://norangeeroli.github.io/hyperbench-pages/

## Read and preview

Open `index.html`, or run `python3 -m http.server 8767` in this directory.
The site has no CDN, backend, analytics or npm dependency. It supports chapter
permalinks, mobile layout, copyable code and collapsible equation-family tables.

## Maintenance

The source of truth is `docs/hyperbench-site/` in the benchmark repository.
Curated chapters are in `content.js`; navigation/rendering in `app.js`;
styles in `style.css`. From that repository root, use its scientific Python to run:

```bash
python docs/update_hyperbench_site.py
node --check docs/hyperbench-site/app.js
node --check docs/hyperbench-site/content.js
node --check docs/hyperbench-site/catalogue.js
```

The updater runs no PDE solver. It regenerates the case catalogue from the active
registry, copies the full computation-model document and one frozen plot, and
records source fingerprints in `source-manifest.json`. Review curated prose when
behavior changes; it is not generated from docstrings. Do not publish raw run
directories, local environment files or private repository history.

Publish this static directory to the documentation repository's `main` branch.
GitHub Pages serves the root of `main`; `.nojekyll` disables template processing.
Changes to the private code repository do not automatically republish this site.
Check the Pages deployment and live chapter links after every publish.

Visual direction was inspired by the user-provided
[Matrix DSL documentation](https://dyu056.github.io/mixtensor-pages/index.html).
The implementation and benchmark text are authored for Hyperbench.
