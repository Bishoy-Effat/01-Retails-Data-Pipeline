# 🛍️ Retail Data Pipeline Project  

> **End-to-End Data Engineering Project** built using **Azure Data Factory**, **Azure Data Lake**, **Azure Databricks (Spark)**, and **Power BI** following the **Medallion Architecture (Bronze–Silver–Gold)**.

---

## 🚀 Project Overview  

This project demonstrates a **Retail Data Pipeline** that automates data ingestion, transformation, and visualization.  
The architecture leverages **Azure Data Factory**, **Azure Data Lake Storage**, **Databricks**, and **Power BI** to create a **scalable, efficient, and modern data lakehouse solution**.

---

## 🧱 Architecture Diagram  

```mermaid
graph TD
A[Azure SQL Database 🗄️] -->|Extract| B[Azure Data Factory ⚙️]
C[REST API 🌐] -->|Extract| B
B -->|Load Parquet| D[Azure Data Lake Storage 🪣]
D -->|Read| E[Azure Databricks 🔥]
E -->|Transform & Model| F[Bronze → Silver → Gold Layers]
F -->|KPI Tables| G[Power BI 📊]

```
<img width="967" height="476" alt="Screenshot 2025-10-31 142550" src="https://github.com/user-attachments/assets/3c17b9fe-de0d-4a36-947e-2c772a6e9bfe" />


## 🗂️ Data Sources
1. Azure SQL Database

Contains 3 core tables:

🛒 products

💳 transactions

🏬 stores

2. REST API

Contains 1 table:

👤 customers

```mermaid
erDiagram
    CUSTOMERS {
        string customer_id
        string full_name
        string email
        string country
        date registration_date
    }

    PRODUCTS {
        string product_id
        string product_name
        string category
        float price
    }

    STORES {
        string store_id
        string store_name
        string location
    }

    TRANSACTIONS {
        string transaction_id
        string customer_id
        string product_id
        string store_id
        int quantity
        date transaction_date
    }

    CUSTOMERS ||--o{ TRANSACTIONS : "makes"
    PRODUCTS ||--o{ TRANSACTIONS : "included in"
    STORES ||--o{ TRANSACTIONS : "occurs at"
```


---
 ## 🏗️ Stage 1: **Azure Data Factory** for Data Ingestion    <img width="70" height="70" alt="10126-icon-service-Data-Factories" src="https://github.com/user-attachments/assets/a20a4f27-53e5-4a4c-bf28-36a55c97fe1b" /> 


 
-Build **Pipeline**  that

🔹 Extract data from:  
- Azure SQL Database (3 tables)  
- REST API (1 table)
 
🔹 Store all files in **Azure Data Lake Storage** as Parquet Files.  

### DATA FACTORY PIPELINE
<img width="1251" height="168" alt="image" src="https://github.com/user-attachments/assets/9f28bfb8-e6a0-466b-ad2a-016b761e9f92" />

### DATA lAKE STORAGE ACCOUNT
<img width="741" height="453" alt="image" src="https://github.com/user-attachments/assets/cb1036af-ff85-407f-872c-3832338264df" />



---

## ⚙️ Stage 2: Data Processing with Azure Databricks  <img width="70" height="70" alt="image" src="https://github.com/user-attachments/assets/bccc8e2b-51ec-400c-b92f-e232946b6534" />


### 🧮 Environment Setup  
- Create **Catalog(Database)** , and **Schema** in Databricks.  
- Connect to **Azure Data Lake Storage** .  
- Use **Apache Spark** for distributed data processing.  

### 🥇 Medallion Architecture  

| Layer | Description | Example Naming |
|-------|--------------|----------------|
| 🥉 Bronze | Raw ingested data | `table_name_bronze` |
| 🥈 Silver | Cleaned and transformed data | `table_name_silver` |
| 🥇 Gold | Business-ready KPI tables | `table_name_gold` |

### 💡 KPI Tables  
- 🗺️ top_countries  
- 🏆 top_products  
- 🏬 top_stores  
- 👥 top_customers  
- 🌍 geography  
- 📆 top_year  
- 📅 top_months  

---

## 📊 Stage 3: Visualization with Power BI  <img width="70" height="70" alt="image" src="https://github.com/user-attachments/assets/c5e5b2ad-11e0-4816-b8d8-51f0d778f705" />


Connect **Power BI** to **Databricks SQL Endpoint** using an **Access Token**.  
Create an interactive report with **three main pages**:

| Page | Focus | Highlights |
|------|--------|-------------|
| 💰 Sales | Total revenue, monthly trends, regional breakdowns | Line & map charts |
| 📦 Products | Top-selling items, category performance | Bar charts |
| 👤 Customers | Top customers, customer locations, demographics | Pie & map visuals |

### Sales 
<img width="1745" height="812" alt="page1" src="https://github.com/user-attachments/assets/89cb8224-205a-4dac-8259-cd4c253b1cee" />

---

### Products
<img width="1743" height="803" alt="page2" src="https://github.com/user-attachments/assets/949f086e-1670-411f-b4fa-a7b4a3ce222a" />

---

### Customers
<img width="1741" height="805" alt="page3" src="https://github.com/user-attachments/assets/7c338378-d194-48fe-922d-2f22a18d162c" />


---

## 🧰 Tech Stack  

| Category | Tools |
|-----------|-------|
| 💾 Storage | Azure Data Lake Storage (ADLS) |
| 🔄 Ingestion | Azure Data Factory |
| 🧮 Processing | Azure Databricks (Spark, PySpark) |
| 📈 Visualization | Power BI |
| 🏗️ Architecture | Medallion (Bronze–Silver–Gold) |

---

## 🧠 Key Learnings  

- Implemented **end-to-end data pipeline** in Azure ecosystem.  
- Applied **ETL/ELT design** using **Data Factory + Databricks**.  
- Followed **Medallion Architecture** for scalable lakehouse design.  
- Integrated **Power BI** for dashboarding.

  
