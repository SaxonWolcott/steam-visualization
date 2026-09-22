# The Evolution of the Steam Library

A scrollytelling visualization of how Steam's catalog has evolved across two decades.
Designed to help developers identify trends and understand the environment they
will be realeasing their games into.

**Live demo:** https://saxonwolcott.github.io/steam-visualization

## Sections

0. **Setting the Scale** — Defines the ownership count scale used for this project based on SteamSpy
   estimates. "Drowned" represents the games with fewest owners, "Phenomenon" represents the games with
   the most.
1. **The Flood** — Shows the growing number of games that fail to find an audience.
   can toggle between proportions and raw counts.
2. **The Indie Wave** — Highlights the growing percentage of games classified in the "indie
   genre.
3. **Will anyone see your game?** — Switch between the number proportion of games getting
   50+ reviews and average ratings of games with that achievement. Illustrates how game quality
   is still good, but only for the few games that find an audience.
4. **Find Your Game** — A search bar + graph to explore the trends for yourself. Type a name
   into the search bar or hit random to get its info. Graph has filters, year timeline, and
   autoplay. Games sorted by number of owners. Click on any game to get its info.

## Tech stack

- Vanilla HTML, CSS, and JavaScript with native ES modules.
- D3.js v7
- Node.js with d3 (`scripts/build.js`) for the offline data pipeline. The browser only
  fetches small pre-aggregated JSONs.
- Hosted on GitHub Pages directly from `main`.

## Data

**Dataset:** [`fronkongames/steam-games-dataset`](https://www.kaggle.com/datasets/fronkongames/steam-games-dataset)

The data pipeline must be run locally; the browser only fetches the JSONs in `data/`.
Place data in `raw_data/games.csv` (too large to commit).

```
cd scripts
npm install
npm run build
```

Outputs are written to `data/*.json` (committed, served to the browser) and a markdown
summary to `data-pipeline-report.md` at the project root.

Dataset Caveats:

- Owner counts are SteamSpy algorithmic estimates.
- Two parsing fixes, but both fixed by `scripts/build.js`:
  1. the source CSV has a malformed header (missing comma `Discount` and `DLC count`)
  2. `Genres` / `Tags` / `Categories` are comma-delimited rather than semicolon-delimited.
