# NYC-Taxi-Data-Engineering

Project Overview
This project demonstrates a complete End-to-End Data Engineering Pipeline using the NYC Taxi Public Dataset. The goal was to build a scalable Medallion Architecture (Bronze, Silver, Gold) to ingest, transform, and visualize large-scale trip data.

Tech Stack
Orchestration: Azure Data Factory (ADF)

Compute: Azure Databricks (PySpark & Spark SQL)

Storage: Azure Data Lake Storage (ADLS Gen2)

Governance: Unity Catalog & Service Principals

Visualization: Power BI

Version Control: GitHub (CI/CD via ARM Templates)

Architecture & Workflow
1. Ingestion (Bronze Layer)
Utilized Azure Data Factory to ingest raw Parquet files from the source into the Bronze container of ADLS Gen2.

Data is stored in its raw format to ensure a full history of source data is maintained.

2. Transformation (Silver Layer)
Developed a PySpark notebook in Databricks to clean raw data.

Performed schema enforcement, handled null values, and converted data types for optimization.

Saved the cleaned data as Delta Tables to support ACID transactions.

3. Aggregation (Gold Layer)
Created business-level summaries using Spark SQL and PySpark.

Calculated metrics such as total trips, average fare, and revenue per vendor.

Stored final datasets in the Gold layer, ready for downstream reporting.

Key Challenges & Solutions
Security & Governance: Configured Unity Catalog with Service Principals to manage fine-grained access control to ADLS Gen2.

Security Compliance: Resolved GitHub push rejections caused by hardcoded secrets by implementing Secret Scanning best practices.

Data Consistency: Used ARM Templates for ADF to ensure the pipeline configuration is version-controlled and reproducible.
