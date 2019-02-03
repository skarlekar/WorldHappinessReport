# World Happiness Report

To demonstrate building an end-to-end **serverless data pipeline** and a full-stack application using *AWS S3, Glue, Athena, Lambda* and/or *Fargate*.


# What Makes People Happy vs Country GDPs

## Problem Statement

What makes people happy in their day-to-day activities and each country’s GDP.

## Solution Architecture
![World Happiness Report - Solution Architecture](https://github.com/skarlekar/WorldHappinessReport/blob/master/images/Glue_POC_Solution_Arch.png)
#### Input

-   Happiness comments & demographics from Kaggle (CSV in S3)
    
-   GDP from Happy Planet Index (JSON in S3)
    
-   Country ISO codes from Kaggle (Tabular data in Postgres)
    

#### Processing

-   Crawl all data & generate Data Catalog
    
-   Build ETL job (PySpark) to load Country ISO code into Postgres managed RDS
    
-   Combine Comments, Demographics in CSV format with GDP data in JSON format along with Country ISO codes in RDS to generate denormalized Happiness Report in CSV format
    
-   Build an Athena query to vend Happiness Report using SQL query
    
-   Build a Microservice using Lambda/Fargate container to expose Happiness data through an API
    
-   Build a single-page web application hosted on S3 to visualize the Happiness Report
    

#### Output

-   World Happiness Report - Charts


## AWS Glue
## AWS Athena
## AWS Lambda
## AWS Fargate

## Project Setup Instructions


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ5MTE5NjM3MSwxNjA0NTEzNDA3LDg5ND
gyMTQ4MCwtMTc0MzQ2NDQ2OV19
-->