# Lakeflow Pipeline Bike Demo on Databricks (GCP Standard Workspace)

This repository contains a clone of the Databricks **Pipeline Bike** (Lakeflow Declarative Pipeline – Bike) demo, adapted to run on Databricks on Google Cloud (GCP) using a standard (non-trial) workspace. [databricks](https://www.databricks.com/resources/demos/tutorials/lakehouse-platform/lakeflow-declarative-pipeline)

## Overview

The original demo ingests bike rental data in near real time, applies quality checks with Lakeflow (Delta Live Tables), and publishes curated tables for analytics. [notebooks.databricks](https://notebooks.databricks.com/demos/pipeline-bike/00-Lakeflow-Declarative-Pipeline-Introduction.html)
This version keeps the same logical pipeline but assumes:

- Databricks workspace deployed on GCP  
- Storage in Google Cloud Storage (GCS)  
- Standard workspace features (no special preview or trial-only setup required)  

You can use it as a reference implementation for Lakeflow / DLT-style pipelines on GCP.

## Architecture

At a high level, the demo implements:

- Ingestion: Raw bike sharing data (CSV/JSON) landing in a GCS bucket.  
- Bronze layer: Auto Loader (cloudFiles) to incrementally load raw data into Delta tables.  
- Silver layer: Cleansed and conformed ride-level and station-level tables.  
- Gold layer: Aggregated tables for reporting (e.g., trips by hour, station utilization, geospatial rollups).  

All transformations are defined as a declarative pipeline (Lakeflow / DLT semantics) so that dependencies, execution order, and data quality rules are managed automatically. [databricks](https://www.databricks.com/resources/demos/tutorials/lakehouse-platform/lakeflow-declarative-pipeline)
