# Building an Azure Data Lake for Bike Share Data Analytics

## 📝 Project Overview
Divvy is a bike-sharing program in Chicago, Illinois, USA. It allows riders to purchase a pass at a kiosk or use a mobile application to unlock a bike at stations around the city for a specified amount of time. After the trip, bikes can be returned to any station in the network. The City of Chicago makes this anonymized bike trip data publicly available for analysis.

![Project Overview](images/Project%20Overview.png) 

### **The Goal**
The objective of this project is to develop a **Data Lakehouse solution** using **Azure Databricks** with a **Medallion (Lakehouse) Architecture**.

* **Design** a star schema based on business requirements.
* **Import** data into Azure Databricks using Delta Lake to create a **Bronze** data store.
* **Transform** and refine data into a **Gold** data store structured as a Star Schema.

---

## 🎯 Business Goals
1. **Ride Duration Analysis**
    * Segmented by day of week, time of day, and station.
    * Analyzed by rider age and membership status (Member vs. Casual).
2. **Financial Analysis**
    * Tracking revenue per month, quarter, and year.
    * Spend analysis based on rider age at account start.
3. **Engagement Metrics (Extra Credit)**
    * Average monthly rides per member.
    * Total minutes spent on bikes per month.

---

## 🏗️ Technical Implementation

### **1. Star Schema Design**
The Gold layer is modeled as a Star Schema to optimize analytical queries and business intelligence reporting.
![Star Schema](images/Star%20Schema.png) 

### **2. Azure Databricks Environment**
The project was deployed using a dedicated Spark cluster within the Azure Databricks workspace.
![Azure DataBricks](images/%20Azure%20DataBricks.png)

### **3. Data Ingestion & Delta Lake**
Raw data was uploaded to DBFS (Databricks File System) and ingested into the Bronze layer as Delta tables to ensure ACID transactions.
![DBFS Upload](images/dbfs.png)

---

## 🛠️ Technologies Used
* **Azure Databricks**: Spark-based analytics platform.
* **Delta Lake**: Storage layer providing ACID transactions and data versioning.
* **PySpark & Spark SQL**: For ETL processes and data transformations.
* **Azure Data Lake Storage (ADLS) Gen2**: Underlying cloud storage for the Lakehouse.

## 📁 Project Structure
- `01_bronze_ingestion.ipynb`: Handles the initial ingestion of raw CSV data into Delta tables.
- `02_dimensions_gold.ipynb`: Contains logic for building the dimension tables (`dim_rider`, `dim_station`, `dim_date`).
- `03_facts_gold.ipynb`: Aggregates business metrics into fact tables (`fact_trip`, `fact_payment`).
- `Divvy_data_lakehouse.pdf`: Full Entity Relationship Diagram (ERD) of the data model.