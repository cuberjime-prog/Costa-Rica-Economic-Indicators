# Costa Rica Economic Indicators | Data Engineering Pipeline

## Project Overview

An end-to-end Data Engineering project developed using **Databricks Free Edition, Python, PySpark, SQL, and Delta Lake**.

The project extracts economic data from the World Bank REST API, processes it through a Medallion Architecture (Bronze, Silver, Gold), performs automated data quality checks, and generates analytical datasets for interactive dashboards.

The entire pipeline is orchestrated using Databricks Jobs.

## Business Objective

Analyze Costa Rica's economic performance between 2000 and 2025 using four key indicators:

- GDP Growth (annual %)
- Inflation, Consumer Prices (annual %)
- Unemployment Rate (%)
- Total Population

The project enables historical trend analysis, economic comparisons, and KPI monitoring.

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | REST API extraction |
| PySpark | Data processing and transformations |
| SQL | Analytical queries and KPIs |
| Databricks Free Edition | Data engineering platform |
| Delta Lake | Data storage |
| World Bank API | Economic data source |
| Databricks Jobs | Pipeline orchestration |
| Databricks AI/BI Dashboards | Data visualization |

## Data Architecture

World Bank REST API

↓

JSON Files — Unity Catalog Volume

↓

**Bronze Layer**

Stores original API responses and ingestion metadata.

↓

**Silver Layer**

Parses JSON records, standardizes data types, removes duplicates, and filters missing indicator values.

↓

**Gold Layer**

Creates five analytical Delta tables for economic reporting.

↓

**Data Quality**

Validates data integrity, uniqueness, completeness, and consistency.

↓

**AI/BI Dashboards**

Visualizes economic indicators and historical trends.

## Data Pipeline

### 1. Data Extraction

Retrieves economic indicators from the World Bank API using Python and the `requests` library.

### 2. Bronze Layer

Stores the original JSON payloads in a Delta table, including source metadata and ingestion timestamps.

### 3. Silver Layer

Transforms nested JSON data into structured records with the following fields:

- country_code
- country
- year
- indicator_code
- indicator_name
- value

### 4. Gold Layer

Creates five analytical tables:

- `gold_economic_summary`
- `gold_gdp_analysis`
- `gold_inflation_analysis`
- `gold_unemployment_analysis`
- `gold_population_analysis`

### 5. Data Quality

Implements six automated checks covering:

- Duplicate detection
- Null value validation
- Year range validation
- Expected indicator validation
- Positive population validation
- Silver-to-Gold year coverage consistency

The validation results are stored in a Delta table for historical tracking.

All six checks passed during the validated pipeline execution.

### 6. Dashboards

**Dashboard 1 — Costa Rica Economic Overview**

Provides executive KPIs and trend charts for GDP growth, inflation, unemployment, and population.


### 7. Pipeline Orchestration

A Databricks Job executes five dependent notebook tasks:

1. API Extraction
2. Bronze Ingestion
3. Silver Transformation
4. Gold Analytics
5. Data Quality

The end-to-end Job was executed successfully, with all five tasks completing.

## Data Source

World Bank Open Data API

https://data.worldbank.org/country/costa-rica

API documentation:

https://datahelpdesk.worldbank.org/knowledgebase/articles/889392

## Project Results

- Four economic indicators integrated from a public REST API.
- Three-layer Medallion Architecture implemented.
- Five analytical Delta tables created.
- Six automated data quality checks passed.
- Two interactive analytical dashboards developed.
- Five-task Databricks Job successfully executed.

## Future Improvements

- Implement incremental data ingestion.
- Add automated schema validation.
- Introduce historical ingestion versioning.
- Expand the analysis to other Central American countries.
- Implement additional data quality and monitoring metrics.
- Parameterize the extraction period to include newly published years automatically.

## Author

| Moises Cubero Jimenez. | 

