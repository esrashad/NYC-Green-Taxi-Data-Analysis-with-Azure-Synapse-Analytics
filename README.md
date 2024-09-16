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

1-Explore the data
  ###### - Query CSV files
    -Query taxi_zone.csv 
    -Query Calender_file.csv
    -Query Vendor_file.csv
    -Query_trip_type_file.tsv
  ###### - Query JSON files
    -Query payment_type.json 
    -Query rate_code.json
  ###### - Query Folders and Subfolders
    -Query trip_data_green_csv Folder
    -Query trip_data_green_parquet Folder
    
   2- Discover the data
     - Identify duplicates in data
     - Check for missing data values
     - Invalid/Unexpected data in columns
     - Join data from multiple files
     - Summarize/Aggregate data
     - Apply some transforms
     
   3- Data Virsulaisation (Bronze Layer)
    Combine data drom multible sources at query time without having to write complex pipelines to load the data.
     
## 2-Data Ingestion (Silver Layer)
- Ingested data to be stored as Parquet.
- Ingested data to be stored as Tables/Views.
- Ability to query the ingested data unsing SQL.
![image](https://github.com/user-attachments/assets/8b5d4fe0-b9a8-48c0-b0e2-f0cb1adc3b08)


## 3-Data Transformation (Gold Layer)
- Join the key information required for reporting to create a new table.
- Join the key information required for Analysis to create a new table.
- Must be able to analyze the transformed data via SQL.
- Transformed data must be stored in Parquet format.
  ![image](https://github.com/user-attachments/assets/6eeb9227-6acc-415c-ae0c-209f7a5c4607)

#### Requirement:
##### Campaign to encourage credit card payments
  - Trips made using credit card/ cash payments
  - Payment behaviour during days of the week/ weekend
  - Payment behaviour between boroughs
###### The result:
![image](https://github.com/user-attachments/assets/9dc8bc5e-97aa-422e-b687-21eba2e2529f)

#### Requirement 2:
##### Identify taxi demand
  - Demand based on borough
  - Demand based on day of the week/ weekend
  - Demand based on trip type (i.e., Street hail/ Despatch)
  - Trip distance, trip duration, total fare amount etc per day/ borough
###### The result:
![image](https://github.com/user-attachments/assets/cdf62c55-0b49-4e9c-8277-1c4ce0566aab)


## 4-Reporting
- Taxi Demand
- Credit Card Campaign
- Operational Reporting

## 5-Sceduling
- Monitor Pipelines.
- Set-up alerts on failures.
- Set-up alerts.
- Run at regular interval.


