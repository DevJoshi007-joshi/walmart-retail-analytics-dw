# Walmart Retail Analytics: End-to-End Cloud Data Warehouse & BI Pipeline

An enterprise-grade data engineering and business intelligence project architecture. This project takes raw, un-optimized retail transaction data, processes and transforms it inside **Google Cloud Platform (BigQuery)** using SQL schema optimizations, constructs a relational **Star Schema**, and delivers interactive financial tracking via **Power BI**.

---

## 🛠️ System Architecture & Data Pipeline

The pipeline follows a modern cloud data stack design pattern:
1. **Data Ingestion:** Raw historical transaction data loaded into GCP BigQuery storage.
2. **Staging & Transformation (SQL):** Cleaned column schemas (handling reserved keywords, mapping `sales_date`), eliminating null values, and isolating dimension/fact distributions.
3. **Data Modeling:** Designed a highly optimized Star Schema model ensuring high performance for analytical processing (OLAP).
4. **BI Consumption:** Connected Power BI Desktop to BigQuery via DirectQuery/Import to build an interactive executive dashboard.
   ---

## 📐 Data Modeling (Star Schema)

To maximize query speed and filter performance, the transactional dataset was broken down from a flat file into a star schema layout:

* **`fact_sales`**: Contains the core quantitative metrics (`weekly_sales`) linked across multiple operational contexts.
* **`dim_dates`**: A dedicated time-dimension table derived via BigQuery optimization to enable accurate chronological, seasonal, and holiday filtering.
* **`dim_stores`**: A structural dimension table containing store-specific operational identifiers.

---

## 🚀 Key SQL Transformations (BigQuery)

During the data engineering phase, raw transactional records were processed to enforce relational data constraints. A major challenge involved handling system-reserved keywords and schema mismatches dynamically:

```sql
-- Isolating operational data and establishing a true time-dimension table
CREATE OR REPLACE TABLE `sales-496806.walmart_analytics.dim_dates` AS
SELECT DISTINCT
    sales_date AS date_id
FROM 
    `sales-496806.walmart_analytics.cleaned_sales`
WHERE 
    sales_date IS NOT NULL;
    📊 Business Intelligence & Value Delivered
Enterprise Scale: Successfully optimized and rendered a dataset calculating over $6.73 Billion in historical corporate revenue.

Dynamic Slicing: Built relational filters enabling executives to slice multi-billion dollar metrics down to precise quarterly windows instantly.

Clean Presentation: Applied institutional accounting formats to raw floating-point data arrays for executive-ready viewing.

🛠️ Tech Stack Used
Cloud Data Warehouse: Google Cloud Platform (GCP) BigQuery Studio

BI Tooling: Power BI Desktop

Language: Google Standard SQL

MODEL VIEW OF POWER BI
<img width="1447" height="733" alt="Power BI Model View" src="https://github.com/user-attachments/assets/44cd2f60-8466-4065-a16d-35d2fb26b393" />
Querry for this
<img width="1446" height="725" alt="bigquery_code" src="https://github.com/user-attachments/assets/5d90be9d-acd7-4350-b57b-3a9ebaac134e" />
The representation
<img width="1919" height="1006" alt="Power BI MatrixVisual Canvas" src="https://github.com/user-attachments/assets/5ee2518b-3e69-4a60-8bd2-f7fc9efd4dfa" />
