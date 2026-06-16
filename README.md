# Mapping-Economic-Transition-in-Appalachia
End-to-end data pipeline analyzing economic resilience in Appalachian counties using Census, BLS QCEW, and FCC broadband data.

This project explores how Appalachian counties are changing economically by combining population, employment, and broadband data into a unified analytical dataset.

## Central Question
Which Appalachian counties are demonstrating economic resilience despite population decline, and what factors, such as industry shifts and broadband access, are associated with that resilience?

## Project Overview
This project builds a data pipeline that integrates multiple public datasets to analyze regional economic change:
- Population trends (U.S. Census)
- Employment and wage data (BLS QCEW)
- Broadband access (FCC)

Rather than forcing a causal model, this project focuses on:
- aligning datasets by county and time
- enabling exploration of relationships
- identifying patterns of resilience

## Architecture
This Project follows a Medallion Architecture approach:
  - Bronze Layer: Raw data ingestion (CSV / compressed files)
  - Silver Layer: Cleaned and standardized datasets
  - Gold Layer: Aggregated metrics for analysis and visualization
Data is stored and processed using Databricks and Spark.

## Data Sources
- BLS QCEW (Quarterly Census of Employment and Wages)
  -   [County-level employment and wage data](https://www.bls.gov/cew/downloadable-data-files.htm)
  -   [Field Layout Link](https://www.bls.gov/cew/about-data/downloadable-file-layouts/annual/naics-based-annual-layout.htm)
- U.S. Census Population Estimates (PEP)
  -   [Annual population estimates by county](https://www.census.gov/data/tables/time-series/demo/popest/2020s-counties-total.html)
  -   [Field Layout Link](https://www2.census.gov/programs-surveys/popest/technical-documentation/file-layouts/2020-2025/CO-EST2025-ALLDATA.pdf)
-   FCC Broadband Data
    - [Internet access availability at the census tract level](https://www.fcc.gov/form-477-census-tract-data-internet-access-services)

## Key Features
- Large dataset ingestion and transformation
- Handling real-world constraints (file size, upload limits)
- Data alignment across different granularities (tract vs county)
- Scalable pipeline design for future expansion

## Current Status
  This project is actively in development.

## Planned Output
  - Interactive dashboard showing:
    - Population change vs employment trends
    - Broadband access comparisons
    -  Identification of resilient counties
   
## Why This Matters
Broadband access and economic opportunity are deeply connected, especially in rural regions like Appalachia. This project aims to highlight patterns that may inform future infrastructure and policy decisions.

## Data Considerations
- FCC broadband source files used different availability category fields across years.
- During ingestion, schema alignment was required to create a consistent broadband dataset.
- Broadband data is reported at the census tract level, while population and employment data are reported at the county level.
- Gold-layer transformations aggregate broadband metrics to support county-level analysis.

## Broadband-Specific Data Considerations

The FCC broadband data is reported at the census tract level and represented as ordinal categories rather than continuous measurements. To support county-level analysis while preserving multiple perspectives of broadband availability, the Gold layer includes several summary metrics:

- Mean category
- Median category
- Mode category
- Minimum category
- Maximum category
- Percentage of tracts in categories 4–5 (higher broadband availability)
- Percentage of tracts in categories 0–1 (lowest broadband availability)
- Percentage of tracts in categories 0–2 (limited broadband availability)

Because the source data is categorical, no single aggregation fully captures broadband conditions within a county. Including multiple summary measures provides a more complete view of the distribution of broadband availability across county tracts.

Both the 0–1 and 0–2 percentages are included because they highlight different levels of limited broadband access and support comparison of alternative measures during analysis.
