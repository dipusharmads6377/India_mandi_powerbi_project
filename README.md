# India Mandi Price Intelligence — Power BI Dashboard

Power BI dashboard analyzing real wholesale agricultural commodity prices from
Indian government mandis (2023–2025), covering Onion, Tomato, Potato, Wheat, and Rice.

## Data Source

- **Dataset:** [Indian Agricultural Mandi Prices (2023–2025)](https://www.kaggle.com/datasets/arjunyadav99/indian-agricultural-mandi-prices-20232025) — Kaggle, by Arjun Yadav
- **Original source:** AGMARKNET Portal (agmarknet.gov.in), Directorate of Marketing & Inspection,
  Ministry of Agriculture & Farmers Welfare, Government of India — released under the
  National Data Sharing and Accessibility Policy (NDSAP)
- **Coverage:** Daily wholesale min/max/modal prices by state, district, and market (mandi)
  for five crops, 2023–2025
- **Why this dataset:** real government-published data (not synthetic), directly relevant
  to India's agricultural economy, with enough time-series depth for trend and
  seasonality analysis

## Objective

Build a decision-support dashboard for a hypothetical agri-trading or policy team to answer:
- How have modal prices for each commodity moved over 2023–2025?
- Which states/markets consistently trade at a premium or discount?
- How volatile is each commodity's price, and when do seasonal spikes occur?
- Where is the spread between min and max price (grading/quality dispersion) widest?

## Tools Used

- **Power BI Desktop** — data model, DAX measures, report pages
- **Power Query (M)** — cleaning, type-casting, date table generation
- **DAX** — time intelligence, volatility, and ranking measures

## Repo Contents

| File | Purpose |
|---|---|
| `README.md` | This file |
| `Data_Source.md` | Exact download steps for the raw dataset |
| `Power_Query_Cleaning_Steps.md` | Step-by-step Power Query transformations |
| `DAX_Measures.md` | All DAX measures used in the report, with explanations |
| `Report_Design.md` | Page-by-page layout and visual spec |
| `screenshots/` | Dashboard screenshots (added after build) |
| `India_Mandi_Prices.pbix` | Power BI file (added after build) |

## Key Insights

*(fill in after building the report — e.g. "Onion prices spiked 60% between
Aug–Oct across all states, consistent with the known monsoon supply-chain
pattern" or "Madhya Pradesh mandis price wheat ~4% below the national modal
average, the widest discount of any major state.")*

## How to Reproduce

1. Download the dataset (see `Data_Source.md`)
2. Open Power BI Desktop → Get Data → follow `Power_Query_Cleaning_Steps.md`
3. Load the DAX measures in `DAX_Measures.md`
4. Build report pages per `Report_Design.md`
5. Publish/export and add screenshots to `screenshots/`
