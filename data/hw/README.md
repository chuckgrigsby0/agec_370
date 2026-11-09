<!-- To add a dataset: add a row to the Datasets table and a section under Dataset details. -->

# Homework data

Data files for AGEC 370 homework notebooks.

## Datasets

| File | Contents | Years | Source | Retrieved |
|---|---|---|---|---|
| `hogs_production_price.csv` | U.S. hog production, price received, and CPI | 1988 to 2025 | USDA NASS, BLS | October 24, 2026 |
| `corn_production_price.csv` | U.S. corn production, price received, and CPI | 1913 to 2025 | USDA NASS, BLS | October 24, 2026 |
| `corn_planted_acres.csv` | U.S. corn planted acres | 1960 to 2025 | USDA NASS | October 25, 2026 |
| `apples_monthly_price.csv` | U.S. fresh market apple price received, monthly | 2000 to 2025 | USDA NASS | October 25, 2026 |
| `tn_county_yields.csv` | Tennessee county corn and soybean yields, with NASS agricultural district | 2015 to 2025 | USDA NASS | October 25, 2026 |
| `tn_counties.geojson` | Tennessee county boundaries, with NASS agricultural district | 2023 boundaries | U.S. Census Bureau, USDA NASS | October 25, 2026 |

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

### `corn_planted_acres.csv`

One row per year. Planted acres are the final annual estimate for the crop year. Merge with `corn_production_price.csv` on `year` to relate planted acres to prices.

| Column | Description | Units |
|---|---|---|
| `year` | Crop year (calendar year of planting) | |
| `planted_acres_million` | U.S. corn planted acres | Million acres |

### `apples_monthly_price.csv`

One row per month. Months with no published price are not in the file: April 2013 to March 2014. The price is nominal.

| Column | Description | Units |
|---|---|---|
| `year` | Calendar year | |
| `month` | Calendar month | 1 to 12 |
| `nominal_price` | Price received by U.S. growers for fresh market apples | Dollars per pound |

### `tn_county_yields.csv`

One row per crop, county, and year. A county-year is in the file only if NASS published a yield for it, so many counties are missing in each year and fewer reported in 2024 and 2025. Corn is grain corn. Soybean and corn yields are survey estimates.

| Column | Description | Units |
|---|---|---|
| `crop` | `corn` or `soybeans` | |
| `fips` | Five-digit county code (state code 47 followed by the county code). Read it as text so the leading digits are kept. | |
| `county` | County name | |
| `district` | NASS agricultural district: Central Basin, Cumberland Plateau, Delta, East Tennessee, West Tennessee, or Western Rim | |
| `year` | Calendar year | |
| `yield_bu_acre` | Yield per harvested acre | Bushels per acre |

### `tn_counties.geojson`

One feature per Tennessee county, 95 in all. Counties with no yield data are included. The boundaries are simplified for small file size and are drawn in longitude and latitude (EPSG:4326). Join to `tn_county_yields.csv` on `fips`.

| Property | Description |
|---|---|
| `fips` | Five-digit county code |
| `county` | County name |
| `district` | NASS agricultural district |

## Sources

- USDA National Agricultural Statistics Service (NASS), [Quick Stats](https://quickstats.nass.usda.gov/): production and prices.
- U.S. Census Bureau, [cartographic boundary files](https://www.census.gov/geographies/mapping-files/time-series/geo/cartographic-boundary.html): county boundaries.
- U.S. Bureau of Labor Statistics (BLS), [Consumer Price Index](https://www.bls.gov/cpi/): Consumer Price Index for All Urban Consumers (CPI-U), U.S. city average, all items, not seasonally adjusted (series CUUR0000SA0).

## Notes

- Prices are nominal. Files with an `annual_avg_cpi` column can be used to calculate real prices.
- NASS revises recent estimates. Values for the latest years may differ from later downloads.
