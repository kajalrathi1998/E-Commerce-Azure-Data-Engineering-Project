# E-commerce Azure Data Engineering Project

## Project Overview
This project demonstrates an end-to-end Azure-based data engineering pipeline for processing and transforming e-commerce datasets. The data includes information about `users`, `buyers`, `sellers`, and `countries`. 

Key Objectives:
- Handle frequently updated datasets efficiently.
- Use Azure Data Lake and Data Factory for scalable data ingestion and storage.
- Leverage Databricks and PySpark for data transformations using the **Medallion Architecture**.
- Prepare an analysis-ready dataset in a unified table for business intelligence and reporting.

---

## Architecture
### Azure Services Used
1. **Azure Data Lake Storage (ADLS)**: Multi-zone storage.
2. **Azure Data Factory (ADF)**: For orchestrating data ingestion and format conversion.
3. **Azure Databricks**: For data transformations using PySpark.

### Medallion Architecture
- **Bronze Layer**: Converts raw data which is in parquet format to delta format.
- **Silver Layer**: Cleaned and transformed datasets.
- **Gold Layer**: A unified analytics-ready table for downstream analysis.

---

## Technologies Used
- **Azure Services**: Data Lake, Data Factory, Databricks
- **Programming Language**: Python (PySpark)
- **File Formats**: CSV, Parquet, delta
- **Architecture**: Medallion Architecture (Bronze, Silver, Gold layers)

---

## Dataset Details
The datasets were sourced from Data.world and include:
- **users**: A large and frequently updated dataset, requiring chunking for processing.
- **buyers**: Information about buyers in the e-commerce platform.
- **sellers**: Data about sellers participating in the platform.
- **countries**: Metadata about the countries involved.

---

## Workflow
### 1. Chunking Large Data
- The `users` dataset was divided into **10 smaller chunks** using a Python script to handle its size and optimize processing.
- The chunks were uploaded to ADLS **Landing Zone 1** in the `users` folder.

### 2. Uploading Raw Data
- The datasets (`users`, `buyers`, `sellers`, and `countries`) in **CSV format** were uploaded to ADLS **Landing Zone 1** in respective folders.

### 3. Conversion to Parquet Format
- Using **Azure Data Factory (ADF)**:
  - Raw CSV files from **Landing Zone 1** were converted to **Parquet** format.
  - The Parquet files were stored in ADLS **Landing Zone 2**, maintaining the same folder structure.

### 4. Data Transformation with Databricks
- **Bronze Layer**: Ingest raw Parquet files.
- **Silver Layer**: Clean and enrich the data using PySpark.
- **Gold Layer**: Consolidate all datasets into a **single unified table** for analytics.

### 5. Analysis-Ready Data
- The Gold layer's unified table is ready for querying and use in BI tools like Power BI or Tableau.

---
