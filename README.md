# 311SFMap

Every 311 call in San Francisco leaves a footprint. This map turns those footprints into towers.

311SFMap pulls half a year of real service requests straight from the city's open data portal and builds a living 3D skyline out of them. Each tower is a neighborhood block. Its height is how many complaints landed there. Its color tells you what people were complaining about.

## What you're looking at

**Eight distinct signals** compete for height in every tower. Graffiti and street cleaning, encampments and abandoned vehicles, noise complaints and tree issues. Plus a dedicated poop bucket sourced from a field the city buries inside `service_details` that no other dashboard bothers to surface.

**Click the legend.** Toggle any signal on or off and the whole map recomputes in real time. Towers shrink, colors shift, and the skyline reorganizes itself around what you actually care about. Watching a bucket of 5,700 human waste reports materialize out of the Street Cleaning category is its own kind of data journalism.

**Pick a neighborhood.** The dropdown isolates a single district. Every tower outside it fades to zero. The numbers at the bottom update to match. You can see exactly which blocks in the Mission carry the most noise reports, or how the Tenderloin lights up differently than the Sunset.

**Press play.** The timeline slider autoplays through six months day by day. Towers grow and shrink with 250 millisecond transitions. Patterns emerge that a static heatmap would never show you.

## How it works

The page is a single self contained HTML file. No build step, no framework, no server. It loads deck.gl and MapLibre from a CDN, fires off a Socrata query for 50,000 recent 311 cases, then bins every row into a master grid of 9,293 neighborhood cells. Each cell remembers how many of each signal type landed on it per day. When you move the slider or toggle a filter, the active window recomputes the weighted mix and pushes the results into a deck.gl ColumnLayer. Smooth transitions handle the rest.

## Run it

```bash
python -m http.server 8000
```

Then open http://localhost:8000. The CORS policy on local `file://` fetches is strict, so a quick local server is the cleanest path.

## Data

[SF 311 Cases](https://data.sfgov.org/City-Infrastructure/311-Cases/vw6y-z8j6) via the Socrata Open Data API. Filtered from June 2025 onward. Roughly 150,000 reports and counting.

## Stack

[deck.gl](https://deck.gl) 9.3.4 for the extruded 3D ColumnLayer towers
[MapLibre GL JS](https://maplibre.org) for the dark basemap
Pure vanilla JavaScript for everything else
