# SF 311 Signal Towers Map

Interactive 3D map of San Francisco 311 service requests, visualized as color-coded signal towers.

## Features
- **8 signal categories** including a dedicated Human Waste bucket (sourced from `service_details`)
- **Interactive legend** — click rows to toggle signals on/off; dimmed when inactive
- **Neighborhood filter** — isolate a single neighborhood by dropdown
- **Time playback** — autoplay through dates with smooth 250 ms tower transitions

## How to run
Open `index.html` in a browser, or serve locally:
```bash
python -m http.server 8000
```
Then visit http://localhost:8000

## Data source
[SF 311 Cases](https://data.sfgov.org/City-Infrastructure/311-Cases/vw6y-z8j6) via Socrata Open Data API (filtered from 2025-06-01, ~150k reports).

## Tech
- [deck.gl](https://deck.gl) 9.3.4 — ColumnLayer for extruded 3D towers
- [MapLibre GL JS](https://maplibre.org) — basemap rendering
