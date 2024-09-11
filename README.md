## NYC-Green-Taxi-Data-Analysis-with-Azure-Synapse-Analytics

### Summary
This project utilizes Azure Synapse Analytics with serverless SQL pools to handle large-scale data ingestion and transformation tasks. It provides a practical guide to processing data with SQL and Apache Spark, demonstrating how to transform and analyze datasets efficiently. The project also includes creating interactive visualizations with Power BI to extract valuable insights.

### Dataset Overview
![image](https://github.com/user-attachments/assets/25c4244a-7520-4c3a-8bd0-1ec4042b81cc)

## Solution Archticture - Serverless SQL Pool
![image](https://github.com/user-attachments/assets/e4523932-75f9-4c02-9552-b6e2d111a237)
 
1-First, let's create Azure Synapse Analytics Workspace
![image](https://github.com/user-attachments/assets/d64631ff-f0b5-4458-843d-e4e4cae69b14)
2-UpLoad NYC Taxi data to Data Lake
![image](https://github.com/user-attachments/assets/3cbb656b-a2b7-45c2-8c04-cfbcd9b899ac)



# Project Requirement
## 1- Data Discovery
We want to ensure that the quality of the data is good and also the data would offer the business value.

## 2-Data Ingestion
-Ingested data to be stored as Parquet.
-Ingested data to be stored as Tables/Views.
-Ability to query the ingested data unsing SQL.

## 3-Data Transformation
-Join the key information required for reporting to create a new table.
-Join the key information required for Analysis to create a new table.
-Must be able to analyze the transformed data via SQL.
-Transformed data must be stored in Parquet format.

## 4-Reporting
-Taxi Demand
-Credit Card Campaign
-Operational Reporting

## 5-Sceduling
-Monitor Pipelines.
-Set-up alerts on failures.
-Set-up alerts.
-Run at regular interval.


