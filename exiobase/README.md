# Exiobase – Interactive Trade Charts

Standalone HTML page that renders three interactive trade-flow visualisations
for the [Exiobase.eu](https://www.exiobase.eu) homepage, addressing
[Issue #65](https://github.com/ModelEarth/projects/issues/65).

## Charts included

| # | Chart | Library | What it shows |
|---|-------|---------|---------------|
| 1 | **Trade Flow Map** | Chart.js (bubble) | Total bilateral trade volume per country plotted on an approximate geographic grid. Bubble size scales with trade volume. |
| 2 | **Chord Diagram** | D3.js | Country-to-country trade dependencies. Arc width encodes each country's share of total bilateral trade; ribbon width encodes the bilateral flow between any two countries. |
| 3 | **Sankey Diagram** | Chart.js + chartjs-chart-sankey | Major trade flows as flow-volume ribbons between economies. |

## Data

The page uses **mock Exiobase-inspired data** (USD billion) so it runs entirely
client-side without any backend or API key. Replace the `MATRIX`, `TRADE_VOLUME`,
and `flows` arrays in `index.html` with real Exiobase API responses to go live.

## Usage

Open `index.html` directly in a browser, or serve it from any static host:

```bash
# quick local server (Python 3)
python3 -m http.server 8080
# then visit http://localhost:8080/exiobase/
```

## Styling

The page loads `notion.css` from
`https://model.earth/localsite/css/styles/notion.css` and applies
`<body class="notion">` to match the rest of the model.earth design system.

## Dependencies (CDN, no install needed)

- [Chart.js 4](https://www.chartjs.org/)
- [chartjs-chart-sankey](https://github.com/kurkle/chartjs-chart-sankey)
- [D3.js 7](https://d3js.org/)
