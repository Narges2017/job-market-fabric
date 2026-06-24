# Job Market Fabric Project

**End-to-End Remote Job Market Analytics Platform** built on **Microsoft Fabric**.

## Overview
This project extracts remote job data from the **Remotive API**, processes it using Medallion architecture (Bronze → Silver → Gold), builds a semantic model, and delivers insights through a Power BI report.

## Architecture

- **Source**: Remotive Remote Jobs API
- **Ingestion**: Fabric Data Pipeline (`job_market_etl`)
- **Storage**: Lakehouse (Delta Lake)
- **Processing**: PySpark Notebooks
- **Modeling**: Semantic Model (`jobs model`)
- **Visualization**: Power BI Report (`jobs_dash`)

## Project Structure

```bash
job-market-fabric/
├── docs/
│   └── screenshots/          ← Add project screenshots here
├── notebooks/
├── pipelines/
│   └── job_market_etl/
├── reports/
├── semantic-models/
├── .gitignore
└── README.md


## Pipeline Flow (job_market_etl)

Copy_jobs → Call Remotive API (REST Source)
save to bronze → Load raw data into Bronze layer
process data → Data cleaning & transformation (Silver)
fact and dims → Build Fact & Dimension tables (Gold)
Semantic model refresh → Refresh jobs model


## Technologies Used

Microsoft Fabric (Lakehouse, Pipelines, Notebooks)
Remotive Jobs API + REST Copy Activity
Delta Lake (Medallion Architecture)
PySpark + Delta Lake
DAX Semantic Model
Power BI

## Clone this repository
Import the Pipeline and Notebooks into your Fabric workspace
Update Lakehouse references if needed
Run the job_market_etl pipeline

## Future Enhancements

Incremental loading from API
Data quality validation
Automated pipeline scheduling
Advanced analytics (salary trends, skill demand, etc.)