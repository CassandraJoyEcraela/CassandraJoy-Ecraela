# Data

## oews_wages_annual.xlsx

BLS Occupational Employment and Wage Statistics, SOC 43-4051 (Customer Service Representatives), national estimates, May 2016–May 2025. Employment and nominal median annual wage for 2019–2023 pulled from individual BLS occupation pages (bls.gov/oes/[year]/may/oes434051.htm); 2016–2018 and 2024–2025 pulled from BLS's bulk national spreadsheets (`national_M[year]_dl.xlsx`, included in this folder). Retrieved September 28–29, 2026 (see `data_sources.xlsx` for the exact date and URL per year). The real-wage column deflates nominal wages to May 2025 dollars using CPIAUCNS: real = nominal × (May 2025 CPI ÷ May [year] CPI). Occupation code and title match across all ten years; the full occupation description text was verified identical only for 2019–2023, the years with individual web pages.

## oews_reference_tables.xlsx

Supplementary detail from the same ten BLS sources as `oews_wages_annual.xlsx`: employment RSE, mean hourly/annual wage, wage RSE, and the 10th/25th/50th/75th/90th percentile wages (hourly and annual). Reference only — not an input to the break test, timing test, or any figure. The analysis draws on `oews_wages_annual.xlsx`.

## data_sources.xlsx

One row per year (2016–2025) and per FRED series, listing the exact source, URL, and retrieval date behind every number in this folder's OEWS, CPI, and postings files.

## CPIAUCNS.xlsx

U.S. Bureau of Labor Statistics, Consumer Price Index for All Urban Consumers: All Items in U.S. City Average, monthly, not seasonally adjusted, retrieved via FRED (fred.stlouisfed.org/series/CPIAUCNS) on September 29, 2026. Used only to deflate OEWS wages into real dollars; not a standalone finding.

## IHLIDXUSTPCUSTSERV.xlsx

Indeed Hiring Lab, Customer Service sector job postings index, daily, seasonally adjusted, indexed to 100 on February 1, 2020, retrieved via FRED (fred.stlouisfed.org/series/IHLIDXUSTPCUSTSERV) on September 29, 2026.

## postings_quarterly.xlsx

Derived from IHLIDXUSTPCUSTSERV.xlsx: daily values averaged into calendar quarters, with quarter-over-quarter percent change and a falling-quarter flag at the 1%, 3%, and 5% thresholds specified in the spec. 2026 Q3 is a partial quarter (source data runs only through September 18, 2026).

## national_M2016_dl.xlsx / national_M2017_dl.xlsx / national_M2018_dl.xlsx / national_M2024_dl.xlsx / national_M2025_dl.xlsx

BLS OEWS bulk national spreadsheets, the primary source for the five years without an individual occupation page. Row for SOC 43-4051 is what's compiled into `oews_wages_annual.xlsx` and `oews_reference_tables.xlsx`. See `data_sources.xlsx` for the exact download URL and retrieval date for each year.
