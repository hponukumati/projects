# Exiobase – Interactive Trade Charts

Standalone showcase page for the three interactive trade-flow charts on the
[Exiobase.eu](https://www.exiobase.eu) homepage, addressing
[Issue #65](https://github.com/ModelEarth/projects/issues/65).

## Charts

| # | Chart | Library | Data |
|---|-------|---------|------|
| 1 | **Trade Flow Map** | Leaflet 1.9 + D3 SVG overlay | Mock bilateral country matrix (M EUR) |
| 2 | **Chord Diagram** | D3.js v7 | Mock bilateral country matrix |
| 3 | **Sankey Diagram** | Apache eCharts 5.4.3 | **Live** `trade_impact.csv` from [ModelEarth/trade-data](https://github.com/ModelEarth/trade-data) |

### Trade Flow Map
Renders a CartoDB light-basemap via Leaflet.  
Country bubbles are sized by total bilateral trade. Animated curved arrows show
the top-12 country pairs by volume. Matches the tech stack of
`profile/trade/map/index.html`.

### Chord Diagram
D3 chord layout showing 8 major economies.  
Arc width = total export share; ribbon width = bilateral trade between two countries.

### Sankey Diagram
Uses Apache eCharts (same library as `io/charts/sankey/desktop/index.html`).  
On load, fetches the **live** CSV:
```
https://raw.githubusercontent.com/ModelEarth/trade-data/main/year/2022/WM/domestic/trade_impact.csv
```
Falls back to a mock country-level Sankey if the fetch fails.

**Metric toggle** (controls bar): switch between Trade Amount, CO₂ Emissions,
Water Use, and Employment.

## Styling

- `<body class="notion">` is included as specified in the issue
- `notion.css` is not yet deployed to `localsite`; inline notion-inspired styles
  serve as the fallback so the page renders correctly today
- Colours and typography match the model.earth design system

## Usage

```bash
# From the repo webroot
python3 -m http.server 8887
# Visit: http://localhost:8887/exiobase/
```

## Dependencies (CDN — no build step)

| Library | Version | Used for |
|---------|---------|----------|
| Leaflet | 1.9.4 | Trade Flow Map basemap |
| D3.js | 7.8.5 | Chord diagram + map SVG overlay |
| Apache eCharts | 5.4.3 | Sankey diagram |

## Related pages

- Trade Flow Map prototype: `model.earth/profile/trade/map/`
- Chord Diagram (placeholder): `model.earth/profile/charts/d3/chord-diagram/`
- Sankey (eCharts): `model.earth/io/charts/sankey/`
- Trade data repo: [ModelEarth/trade-data](https://github.com/ModelEarth/trade-data)
