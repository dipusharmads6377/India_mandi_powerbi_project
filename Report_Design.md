# Report Design

4 pages, 16:9. Keep a consistent header band (title + slicers) across all pages.

## Global slicers (top of every page)
- `Commodity` (buttons: Onion / Tomato / Potato / Wheat / Rice)
- `DimDate[Year]` and/or a date range slicer
- `State`

## Page 1 — Executive Overview
- KPI cards: **Avg Modal Price**, **MoM %**, **YoY %**, **Active Markets**, **Reporting Days**
- Line chart: Avg Modal Price by month, one line per commodity (2023–2025)
- Map (or filled map) of India: Avg Modal Price by state (color-coded)
- Callout/text box: 2–3 sentence narrative insight (fill in after seeing real data)

## Page 2 — Price Trends & Seasonality
- Line chart: Modal Price over time for the selected commodity, with a
  visible seasonal pattern (harvest-season dips, monsoon-disruption spikes)
- Area chart: Min/Max/Modal price band over time (shows the spread visually)
- Bar chart: Avg Price Spread by month (which months have the most
  price uncertainty)

## Page 3 — State & Market Comparison
- Bar chart: Avg Modal Price by State, sorted descending, with a reference
  line for the national average
- Table: Top 10 markets by Avg Modal Price, with `Rank State by Avg Price`
  and `Price vs National Avg %`
- Bar chart: Avg Price Spread by State (quality/grading dispersion)

## Page 4 — Commodity Deep-Dive
- Small multiples or a matrix: Avg Modal Price by Commodity × Year
- Volatility comparison: bar chart of `Price Volatility %` by Commodity —
  which crop is riskiest to trade
- Scatter: Avg Price (x) vs Volatility % (y), one bubble per commodity,
  bubble size = Active Markets — a classic risk/return-style view that
  reads well in an interview

## Design notes
- Use a single consistent color per commodity across all pages (e.g. Onion =
  purple-ish, Tomato = red, Potato = tan, Wheat = gold, Rice = green) —
  visual consistency matters more to reviewers than clever chart types
- Keep number formatting in ₹ and note "per quintal" somewhere visible —
  don't leave units ambiguous
- Add a small footer text box on page 1: data source + coverage period +
  "wholesale mandi prices, not retail"
