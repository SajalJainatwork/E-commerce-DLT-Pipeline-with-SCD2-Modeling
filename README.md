![eshoper](https://github.com/user-attachments/assets/306d6c09-6d51-408c-bf36-16e77b34ffb2)

# E-Commerce Data Engineering Project – Azure Databricks

## 📌 Project Overview
This project demonstrates an end-to-end data engineering solution for an **e-commerce dataset** using **Azure Databricks** and **Azure Data Lake Storage Gen2 (ADLS Gen2)**.  

The goal was to build a scalable **medallion architecture** (Bronze → Silver → Gold), transform raw e-commerce data into a **star schema**, and implement **Slowly Changing Dimension (SCD) Type 2** for dimensional tables.  

The solution leverages **Delta Lake** for reliable storage, **jobs** for orchestration, and **Unity Catalog** for secure, governed access.  

---

## ⚙️ Architecture
![Medallion Architecture](assets/medallion_architecture.png)

- **Bronze Layer** – Raw ingestion of parquet/CSV files from ADLS Gen2  
- **Silver Layer** – Data cleaning, validation, and transformations  
- **Gold Layer** – Star schema modeling with fact and dimension tables  

👉 The medallion design ensures modularity, reliability, and reusability of data.  

---

## 📂 Data Model
![Star Schema](assets/star_schema.png)

- **Fact Tables**: Orders, Transactions  
- **Dimension Tables**: Products, Customers, Dates, Categories  
- **Star Schema**: Optimized for analytical queries  
- **SCD Type 2**: Implemented for dimensions like `DimProducts` and `DimCustomers` to track historical attribute changes (`valid_from`, `valid_to`, `is_active`)
- 
<img width="1024" height="1024" alt="star_schema" src="https://github.com/user-attachments/assets/eca6d5f6-0556-4570-bba9-1b4c2f193ad4" />

---

## 🚀 Key Features
- **Ingestion**: Pulled raw data from **Azure ADLS Gen2** into Databricks  
- **File Formats**: Worked with **Parquet** and Delta tables  
- **Transformations**: Filtering, joins, aggregations, schema evolution, rule-based validations  
- **Orchestration**: Designed ETL pipelines with **Databricks Jobs**  
- **Governance**: Access controlled with **Azure IAM** and managed using **Databricks Unity Catalog**  
- **Delta Lake Features**: Time travel, schema enforcement, ACID transactions  

---

## 🛠️ Tech Stack
- **Azure Databricks** (PySpark, Delta Lake, SQL)  
- **Azure ADLS Gen2** (data lake storage)  
- **Azure IAM** (identity & access management)  
- **Unity Catalog** (data governance & cataloging)  
- **Parquet & Delta Tables** (storage formats)  

---

## 📊 Pipeline Flow
1. **Raw Data → Bronze**  
   - Landed in ADLS Gen2  

2. **Bronze → Silver**  
   - Cleaned & validated with PySpark transformations  

3. **Silver → Gold**  
   - Built star schema with fact and dimension tables  
   - Applied **SCD2** for history tracking  

4. **Job Scheduling**  
   - Designed scheduling with Databricks Jobs for daily/weekly runs  
   - ⚠️ *Note*: Due to Azure student subscription limits, jobs could not be executed, but full pipeline logic was validated in notebooks  

![data_warehoues_archicture](https://github.com/user-attachments/assets/dd9ba2a4-6020-46f5-83cb-946652ec3f5e)


---

## 📈 Outcomes
- Designed a **scalable medallion architecture** in Databricks  
- Built a **star schema** optimized for analytics and reporting  
- Implemented **SCD2** for historical accuracy in dimensions  
- Automated pipeline logic (tested in notebooks, job scheduling designed but not runnable on student account)  
- Ensured **security and governance** with Azure IAM + Unity Catalog  

---

## ▶️ How to Run
1. Mount or connect ADLS Gen2 to Databricks  
2. Create Databricks notebooks for Bronze, Silver, and Gold layers  
3. Run transformation notebooks step by step  
4. (Optional) Set up Databricks Jobs to schedule and orchestrate (requires full subscription)  
5. Query final star schema tables from the **Gold layer**  

---

## 📚 Learnings
- How to integrate **Azure ADLS Gen2 with Databricks**  
- Working with **Parquet** and **Delta Lake** formats  
- Building **medallion architecture** pipelines  
- Designing a **star schema** and applying **SCD2**  
- Setting up **IAM roles, Unity Catalog, and job scheduling** in Azure Databricks  
- Handling **student subscription limitations** creatively by testing orchestration logic inside notebooks  

