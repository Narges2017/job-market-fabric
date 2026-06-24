# 💼 Job Market Data Engineering on Microsoft Fabric

[![Microsoft Fabric](https://img.shields.io/badge/Microsoft%20Fabric-Lakehouse%20%7C%20ETL-blue)](https://learn.microsoft.com/fabric/)
[![PySpark](https://img.shields.io/badge/PySpark-Delta%20Lake-orange)](https://spark.apache.org/)
[![Power BI](https://img.shields.io/badge/Power%20BI-Semantic%20Model-yellow)](https://powerbi.microsoft.com/)

An end-to-end **Job Market ETL and Analytics** solution built on **Microsoft Fabric** using the Medallion Architecture (Bronze → Silver → Gold), PySpark notebooks, and Power BI semantic models.

---

## 📌 Project Overview

This project builds a complete data platform for **Job Market analytics**. It demonstrates modern data engineering practices on Microsoft Fabric by:

- Ingesting raw job market data into the **Bronze** layer
- Cleaning, transforming, and enriching data in the **Silver** layer
- Creating a dimensional model (**Fact + Dimensions**) in the **Gold** layer
- Preparing semantic models and reports for business intelligence

The solution is designed to be scalable, maintainable, and ready for analytics workloads.

---

## 🏗️ Architecture

```
Raw Job Data (CSV, API, etc.)
        ↓
┌──────────────────────┐
│     Bronze Layer     │   ← Raw data ingestion (save_bronze_table.ipynb)
└──────────────────────┘
        ↓
┌──────────────────────┐
│     Silver Layer     │   ← Cleaning & business transformations (data_processing.ipynb)
└──────────────────────┘
        ↓
┌──────────────────────┐
│      Gold Layer      │   ← Star Schema (Fact + Dimensions) (fact_and_dimensinos_table.ipynb)
└──────────────────────┘
        ↓
┌──────────────────────┐
│  Semantic Models     │   ← Power BI ready models
│     + Reports        │
└──────────────────────┘
```

---

## 🛠️ Technologies Used

| Component              | Technology                     |
|------------------------|--------------------------------|
| Data Platform          | Microsoft Fabric               |
| Storage & Compute      | Lakehouse + Delta Lake         |
| Data Processing        | PySpark Notebooks              |
| Orchestration          | Fabric Pipelines               |
| Analytics & BI         | Power BI Semantic Models       |
| Architecture Pattern   | Medallion (Bronze / Silver / Gold) |

---

## 📁 Project Structure

```
job-market-fabric/
├── notebooks/
│   ├── save_bronze_table.ipynb
│   ├── data_processing .ipynb
│   └── fact_and_dimensinos_table.ipynb
├── pipelines/
│   └── job_market_etl/           # ETL pipeline definitions
├── semantic-models/              # Power BI semantic models
├── reports/                      # Power BI reports
├── docs/                         # Documentation
├── .gitignore.txt
└── README.md
```

---

## ✅ Prerequisites

- Microsoft Fabric workspace with sufficient capacity (F8+ recommended)
- A **Lakehouse** created in the workspace
- Source job market data (e.g., job postings, applications, salaries, etc.)
- Power BI Desktop or Power BI Service

---

## 🚀 How to Run

### 1. Initial Setup

1. Create a **Lakehouse** in your Fabric workspace.
2. Upload or connect your raw job market data.
3. Attach the Lakehouse to the notebooks.

### 2. Execute Notebooks in Order

| Order | Notebook                          | Layer     | Purpose |
|-------|-----------------------------------|-----------|---------|
| 1     | `save_bronze_table.ipynb`         | Bronze    | Ingest raw data into Delta table |
| 2     | `data_processing .ipynb`          | Silver    | Clean, validate, and enrich data |
| 3     | `fact_and_dimensinos_table.ipynb` | Gold      | Build Fact and Dimension tables |

> **Tip**: Use `.mode("overwrite")` or `CREATE OR REPLACE TABLE` to avoid `TABLE_OR_VIEW_ALREADY_EXISTS` errors when rerunning notebooks.

### 3. Capacity Management

If you see the **`TooManyRequestsForCapacity`** error:
- Open **Monitoring hub** and cancel any stuck Spark jobs
- Wait 2–5 minutes before retrying
- Use **Workspace settings → Job management** to monitor concurrency

---

## 📓 Notebooks Description

### 1. `save_bronze_table.ipynb`
- Loads raw job market data
- Creates the `bronze_*` tables in the Lakehouse
- Adds metadata columns (ingestion timestamp, source, etc.)

### 2. `data_processing .ipynb`
- Data cleaning and standardization
- Handling missing values, duplicates, and outliers
- Business rule application and feature engineering
- Outputs cleaned tables to the Silver layer

### 3. `fact_and_dimensinos_table.ipynb`
- Implements dimensional modeling (Kimball style)
- Creates Fact table(s) (e.g., `fact_job_postings`, `fact_applications`)
- Builds supporting Dimension tables (`dim_company`, `dim_job_title`, `dim_location`, `dim_date`, etc.)
- Produces analytics-ready Gold layer tables

---

## 📊 Semantic Models & Reports

This project includes:
- **Semantic Models** in the `semantic-models/` folder — ready for Direct Lake or Import mode in Power BI
- **Reports** in the `reports/` folder — pre-built dashboards for job market insights

Common analytics scenarios:
- Job posting trends over time
- Salary analysis by role, location, and experience
- Company hiring patterns
- Skills demand analysis

---

## ⚠️ Common Issues & Solutions

| Error                                      | Solution |
|--------------------------------------------|----------|
| `TABLE_OR_VIEW_ALREADY_EXISTS`             | Add `.mode("overwrite")` to DataFrame writes or use `CREATE OR REPLACE TABLE` |
| `TooManyRequestsForCapacity`               | Cancel jobs in Monitoring hub + wait, or upgrade capacity |
| Notebook fails to start Livy session       | Stop other active notebooks and retry |

---

## 📈 Future Improvements

- [ ] Add incremental / CDC loading for Bronze layer
- [ ] Implement data quality checks and monitoring
- [ ] Create automated pipelines using Fabric Data Factory
- [ ] Add machine learning models (e.g., salary prediction, job matching)
- [ ] Enable real-time ingestion using Eventstreams
- [ ] Improve naming consistency (fix typos in notebook filenames)

---

## 🤝 Contributing

Contributions are welcome! Please feel free to open issues or submit pull requests to improve the project.

---

## 📄 License

This project is open source. Please check the repository for license details.

---

## 👩‍💻 Author

**Narges**  
Job Market Data Engineering Project on Microsoft Fabric

---

> Built with modern data engineering best practices using Microsoft Fabric Lakehouse.

---

