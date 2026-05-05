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
  -   County-level employment and wage data
- U.S. Census Population Estimates (PEP)
  -   Annual population estimates by county
-   FCC Broadband Data
    - Internet access availability at the census tract level

## Key Features
- Large dataset ingestion and transformation
- Handling real-world constraints (file size, upload limits)
- Data alignment across different granularities (tract vs county)
- Scalable pipeline design for future expansion

## Current Status
  This project is actively in development.

  Due to data size and ingestion constraints, the current implementation uses a subset of the full dataset for demonstration purposes.  The pipeline is designed to scale to a full dataset.

## Planned Output
  - Interactive dashboard showing:
    - Population change vs employment trends
    - Broadband access comparisons
    -  Identification of resilient counties
   
## Why This Matters
Broadband access and economic opportunity are deeply connected, especially in rural regions like Appalachia. This project aims to highlight patterns that may inform future infrastructure and policy decisions.
