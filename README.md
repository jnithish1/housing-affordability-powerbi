# Housing Affordability in Australia — Power BI Dashboard

An interactive Power BI dashboard analysing housing affordability across Australia using ABS Census data (2011, 2016, 2021).

## What it looks at

Housing stress = a household spending more than 30% of its income on mortgage repayments or rent. The dashboard compares mortgage stress and rental stress across ~3,000 geographic areas (national, state, LGA and SA2 level).

## Key findings

- Mortgage stress fell sharply: 26.3% of mortgage-holding households in 2011 → 14.5% in 2021 (−11.8 percentage points).
- Rental stress barely moved: 34.3% → 32.2% (−2.1 pp), peaking at 36.0% in 2016. By 2021, about 1 in 3 renting households was in housing stress, vs. about 1 in 7 mortgage households.
- Stress is uneven geographically: NSW had the highest state-level rental stress (35.5%) in 2021; the Northern Territory the lowest (16.3%). At LGA level, Byron and Fairfield ranked highest (areas with 1,000+ renting households).

## How it's built

- **Data source:** [Census Mortgage and Rent Affordability Indicators for LGAs and SA2s](https://catalogue.data.infrastructure.gov.au/dataset/rdh-census-housing-affordability-data-for-lgas-and-sa2s-mortgage-and-rent-affordability-indicators), sourced from the Australian Bureau of Statistics (ABS), Creative Commons Attribution licence.
- **Power Query:** cleaned the raw file (removed disclaimer row, set data types), split it into a star schema.
- **Data model:** one fact table (`Fact_affordability`) with `Dim_geography` and `Dim_year` dimension tables, one-to-many relationships.
- **DAX measures:** stress rates calculated with `DIVIDE` (to handle zero-renter areas safely), and year-over-year change using `CALCULATE` and `VAR`.
- **Report pages:**
  - *Explore Areas* — KPI cards, a filled map, a ranked bar chart (minimum household threshold applied to avoid small-sample distortion), and geography/year slicers.
  - *National Trend* — a line chart of mortgage and rental stress from 2011 to 2021.

## Files

- `Housing_Affordability_Australia.pbix` — the full Power BI report (open with Power BI Desktop, free).

## Notes on the data

ABS applies small random adjustments to Census cell values to protect confidentiality (perturbation), so totals may differ slightly from official published figures. This is a personal learning project, not an official ABS product.
