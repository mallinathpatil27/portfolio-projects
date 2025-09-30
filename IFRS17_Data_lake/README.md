# 📘 IFRS17 Data Lake Implementation (AWS)

This project represents a real-world **Data Lake Implementation** for **IFRS17 Insurance Contracts** reporting and compliance, built entirely on **AWS cloud-native services** such as AWS Glue, S3, Athena, and RDS.

As a Data Engineer, I was responsible for designing and implementing **scalable, auditable ETL pipelines** using **PySpark on AWS Glue**, integrating multiple data sources, performing business-rule-driven transformations, and delivering structured outputs to downstream systems such as **SAP FPSL** and **Prophet**.

---

## 📜 Background: What is IFRS17?

**IFRS 17 – Insurance Contracts** is an International Financial Reporting Standard issued by the IASB to replace IFRS 4. It requires insurance companies to recognize revenue and profits in a consistent and comparable manner. Compliance is mandatory for accounting periods starting **1 January 2023**.

This implementation was part of a company-wide compliance program to enable automated and accurate financial reporting for both **life and general insurance portfolios**.

---

## 🧱 Architecture Overview

The data lake architecture follows a **layered approach**, where data flows through various stages — from ingestion to transformation to final curated delivery.

### 📊 Data Lake Layers

| Layer             | Description |
|------------------|-------------|
| **Raw Layer (Staging Area)**      | Ingests raw files from both **PAS** and **Non-PAS** sources (e.g., SAP GL, Prophet, PAPM, manual files) |
| **Tech_Staging Layer**            | Applies data quality (DQ) checks before further transformation |
| **Harmonized Layer**              | Lowest grain harmonized data serving as **single source of truth** |
| **Derived Layer**                 | Domain-specific transformations for IFRS17 and Target models |
| **Curation Layer**                | Upsert logic (SCD Type 2) applied, ready for consumption |
| **Extraction Layer (Target)**     | Final outputs formatted for downstream systems (FPSL, Prophet, Alteryx) |

---

## 🧮 Data Sources

Data is enriched from **two types of source systems**:

### 1️⃣ Policy Administration Systems (PAS)
- Frequency:  
  - **Monthly**: Regular BAU loads  
  - **Half-Yearly**: Historical backfill (2021–2023)


### 2️⃣ Non-PAS Sources  
 
---

## ⚙️ ETL Design & Implementation

### ✅ Tools & Technologies
- **Cloud**: AWS Glue, S3, Athena, RDS
- **Processing**: PySpark, Spark SQL
- **Monitoring**: Audit Tables
- **Orchestration**: Airflow

### 🔁 ETL Flow Summary
1. Ingest raw files from PAS / Non-PAS sources into **Raw Layer**
2. Perform **Data Quality (DQ) checks** in **Tech_Staging**
3. Apply **business rules and harmonization** in **Harmonized Layer**
4. Perform SCD Type 2 **upserts** in **Curated Layer**
5. Export cleaned, structured outputs to **Target Layer**
6. Downstream systems (e.g., SAP FPSL, Prophet) consume the data


