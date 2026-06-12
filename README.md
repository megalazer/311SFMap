# 311SFMap

Every 311 call in San Francisco if you really wanted to see it I guess lul

311SFMap pulls half a year of real service requests straight from the city's open data portal and builds a living 3D skyline out of them. Each tower is a neighborhood block. Its height is how many complaints landed there. Its color tells you what people were complaining about.

## What you're looking at

**Eight distinct categoories** compete for height in every tower though it's more like golf where more points are bad seriously sort the tenderloin it's crazy. Graffiti and street cleaning, encampments and abandoned vehicles, noise complaints and tree issues. Plus a dedicated poop bucket sourced from a field the city buries inside `service_details`

**Click the legend.** Toggle any signal on or off and the whole map recomputes in real time. Towers shrink, colors shift, and the skyline reorganizes itself around what you actually care about. Watching a bucket of 5,700 human waste reports materialize out of the Street Cleaning category is both hilarious and a testament to the horrors of houselessness that affected so many in the wake of the opioid crisis

**Pick a neighborhood.** The dropdown isolates a single district. Every tower outside it fades to zero. The numbers at the bottom update to match. You know you're just gonna filter for the Tenderloin aren't you 

**Press play.** The timeline slider autoplays through six months day by day. Towers grow and shrink with 250 millisecond transitions because I have severe ADHD


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
