<!-- To add a dataset: add a row to the Datasets table and a section under Dataset details. -->

# Homework data

Data files for AGEC 370 homework notebooks.

## Datasets

| File | Contents | Years | Source | Retrieved |
|---|---|---|---|---|
| `hogs_production_price.csv` | U.S. hog production, price received, and CPI | 1988 to 2025 | USDA NASS, BLS | October 24, 2026 |
| `corn_production_price.csv` | U.S. corn production, price received, and CPI | 1913 to 2025 | USDA NASS, BLS | October 24, 2026 |

## Dataset details

### `hogs_production_price.csv`

One row per year. Production and price are both for the calendar year.

| Column | Description | Units |
|---|---|---|
| `year` | Calendar year | |
| `production_billion_lb` | U.S. hog production, live weight | Billion pounds |
| `nominal_price` | Price received by U.S. hog producers, annual average | Dollars per hundredweight (cwt) |
| `annual_avg_cpi` | CPI-U, all items, annual average | Index (1982-84 = 100) |

### `corn_production_price.csv`

One row per year. Production is for the calendar year. The price is the marketing year average, labeled by the year the marketing year starts. The corn marketing year currently runs from September to August. For example, the 2024 price is the average for September 2024 through August 2025.

| Column | Description | Units |
|---|---|---|
| `year` | Calendar year for production. Marketing year for price. | |
| `production_billion_bu` | U.S. corn production | Billion bushels |
| `nominal_price` | Marketing year average price received by U.S. corn producers | Dollars per bushel |
| `annual_avg_cpi` | CPI-U, all items, annual average | Index (1982-84 = 100) |

## Sources

- USDA National Agricultural Statistics Service (NASS), [Quick Stats](https://quickstats.nass.usda.gov/): production and prices.
- U.S. Bureau of Labor Statistics (BLS), [Consumer Price Index](https://www.bls.gov/cpi/): Consumer Price Index for All Urban Consumers (CPI-U), U.S. city average, all items, not seasonally adjusted (series CUUR0000SA0).

## Notes

- Prices are nominal. Files with an `annual_avg_cpi` column can be used to calculate real prices.
- NASS revises recent estimates. Values for the latest years may differ from later downloads.
