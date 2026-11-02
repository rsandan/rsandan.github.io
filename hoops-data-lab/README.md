# Hoops Data Lab

A mobile-friendly NBA analytics lab for practicing data science on real data. Ask a basketball question, get a SQL lesson that runs in the browser, a chart, the equivalent pandas code, and a challenge to solve yourself.

## What's inside

- `index.html`: the whole app (no build step). SQL runs client-side with [AlaSQL](https://github.com/AlaSQL/alasql); charts use [Chart.js](https://www.chartjs.org/).
- `data/players.csv`: one row per NBA player-season-team, 1999-00 through 2026-27. Per-game box stats plus PER, TS%, USG%, WS, WS/48, BPM, VORP.
- `data/teams.csv`: one row per team-season with ratings, pace, SRS and the four factors.

## Data notes

- `season` is the end year (2024 = 2023-24). 2027 is the in-progress season.
- Traded players have a season-total row (`team` = `2TM`, `3TM`, ...) plus one row per team. Filter one or the other to avoid double counting.
- Source: Basketball-Reference, via [sumitrodatta/bball-reference-datasets](https://github.com/sumitrodatta/bball-reference-datasets), snapshot November 2026.

## How the lesson generator works

Inside Claude, the "Build lesson", hint, grading and "What does this tell me?" features call Claude from the page. Hosted elsewhere (like GitHub Pages) those features switch off and the page runs as a SQL playground with a worked example. Running them publicly would need an API key behind a small server, not in this static page.

## Run locally

```
python -m http.server
```

Then open http://localhost:8000. Opening `index.html` directly from disk won't load the CSVs, since browsers block `fetch` on `file://`.
