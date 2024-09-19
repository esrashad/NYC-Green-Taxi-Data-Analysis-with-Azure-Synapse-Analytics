## NYC-Green-Taxi-Data-Analysis-with-Azure-Synapse-Analytics
This project utilizes Azure Synapse Analytics with serverless SQL pools to handle large-scale data ingestion and transformation tasks. It provides a practical guide to processing data with SQL , demonstrating how to transform and analyze datasets efficiently. The project also includes creating interactive visualizations with Power BI to extract valuable insights.

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


## 4-Sceduling
- Monitor Pipelines.
- Set-up alerts on failures.
- Set-up alerts.
- Run at regular interval.

#### Silver Tables Pipeline:
![image](https://github.com/user-attachments/assets/3eb28475-5281-41e6-9a74-2cbed87a9071)

##### Silver trip data green folder pipeline:
![Screenshot 2024-09-17 155829](https://github.com/user-attachments/assets/0afaa9bb-e04b-4b85-b6e0-c0a536ce411d)

gold trip data green folder pipeline:
![Screenshot 2024-09-17 164138](https://github.com/user-attachments/assets/2df344b7-a918-4b9a-83e0-8a6e4429497a)

##### Execute all pipelines:
![Screenshot 2024-09-17 180443](https://github.com/user-attachments/assets/8a30b944-ffcd-4c5b-b845-4e37a3e90231)

#### Make Trigger to schedual the execute pipeline:
![Screenshot 2024-09-17 182759](https://github.com/user-attachments/assets/8dfb2b31-8e38-4b6a-a6bf-fe2561d9764b)

## 5-Reporting
- Taxi Demand
- Credit Card Campaign
- Operational Reporting
![image](https://github.com/user-attachments/assets/bc955798-0402-4eb7-a348-dee73c7668eb)


##### Synapse Link For Cosmos DB:
- NYC Taxis are fitted with a device to manage taxi hires
- Device sends data to Cosmos DB every minute
- Create a Cosmos DB analytic store using Synapse Link 
- Ability to query and make data available to PowerBI using Serverless SQL Pool
##### The Result:
![Screenshot 2024-09-19 182227](https://github.com/user-attachments/assets/3ba9ec0e-136d-4d58-9180-a4bb4760ab8f)

## Use Dedicated SQL pool as a serving layer
#### Requirements
![Screenshot 2024-09-19 204913](https://github.com/user-attachments/assets/0de4980e-d620-4fca-8548-a55d1fc72844)
1) Create Dedicated SQL Pool
![Screenshot 2024-09-19 211548](https://github.com/user-attachments/assets/4c9e813b-3e5b-4e33-8319-c5999e6bcc64)
2) Create External Table staging.trip_data_green
3) Copy the data from external table into physical table
`COPY INTO dwh.trip_data_green_copy`
`FROM 'https://nyctaxisynapsedl.dfs.core.windows.net/nyc-green-taxi-data/gold/trip_data_green'`
`WITH`
`(`
    `FILE_TYPE = 'PARQUET'`
    `,MAXERRORS = 0`
    `,COMPRESSION = 'snappy'`
    `,AUTO_CREATE_TABLE='ON'`
`)`
`GO`
`SELECT TOP 100 * FROM dwh.trip_data_green_copy`
`GO`







