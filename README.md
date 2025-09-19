# Retail Orders Analytics — Data Engineering & MDM MVP

This repository contains my solution for the Retail Orders Analytics case study.  
It covers end-to-end data engineering tasks: from KPI definition and solution design, through data quality checks and master data management, to creation of clean data marts.

---

## 📊 Work Summary (Tasks 1–6)

### **Task 1 — KPI Glossary**
Defined the key performance indicators required for the MVP dashboard:
- Avg price dynamics for best-selling products  
- Sales dynamics by state  
- Best customers in each segment  
- Top/Bottom products by sales and delivery time  
Created **Task_1_KPI_Glossary.csv** with KPI names, descriptions, formulas, and granularity.

---

### **Task 2 — High-Level Design**
Designed the **technical architecture** of the solution:
- Ingestion: SFTP → Python ETL (pandas), automated with Airflow/Prefect
- Storage layers: Raw, Staging, Master Data, Analytics (DWH)  
- Processing: cleansing, normalization, MDM survivorship rules  
- Delivery: data marts in CSVs for BI dashboards  
Produced **Task_2_HLD.pptx** with architecture, data flow, and inconsistency handling.

---

### **Task 3 — Entity Relationship Diagram**
Modeled a **star schema**:
- Fact table: `fct_sales` (order line grain)  
- Dimensions: `dim_customer`, `dim_product`, `dim_date`, `dim_geography`, `dim_ship_mode`  
Kept master data separated from transactional data, normalized to 3NF.  
Produced **Task_3_ERD.jpg**.

---

### **Task 4 — DWH Physical Design**
Created **DDL scripts** for all schemas and tables:  
- Defined data types, primary/foreign keys, and constraints  
- Ensured referential integrity and uniqueness of business keys  
Stored in **Task_4_DDL.txt**.

---

### **Task 5 — Inconsistencies Analysis**
Ran ETL pipeline with profiling and cleansing. Identified 5 main inconsistency types, including:
- Duplicate `(Order ID + Product ID)` rows with conflicting values
- Invalid Quantity (negative)
- Invalid dates (Ship Date < Order Date) or date format inconsistency  
- Null or negative Profit values  
- Product IDs with multiple names/categories (MDM issue)  
- Geography mismatches (Postal Code vs City/State)  

Deliverables:  
- **Inconsistencies_Summary** → type, description, suggestion, counts  
- **Inconsistencies_Examples** → sample rows with issues highlighted  
- **Quality_Report** → business-facing summary of data needing SME clarification  
Saved as **Task_5_Inconsistencies_Analysis.xlsx**.

---

### **Task 6 — Data Marts**
Loaded cleansed and normalized data into **final marts**:
- Dimensions: `dim_date`, `dim_customer`, `dim_product`, `dim_geography`, `dim_ship_mode`  
- Fact: `fct_sales`

Exported:
- **Task_6_1_Data_Marts.zip** → CSVs of all marts  
- **Task_6_2_Data_Marts_Rows.csv** → row counts and distinct key counts for validation

---

## ✅ Next Step (Task 7)
All scripts and deliverables are pushed to this GitHub repo.  
This README explains the workflow and deliverables as required.
