# World Happiness Report

To demonstrate building an end-to-end **serverless data pipeline** and a full-stack application using *AWS S3, Glue, Athena, Lambda* and/or *Fargate*.


# What Makes People Happy vs Country GDPs

## Problem Statement

What makes people happy in their day-to-day activities and how does it relate to  country’s GDP?

## Solution
To answer the aforementioned problem, we collected data from multiple sources. The data was in different formats such as CSV and JSON. Some of this data was static in nature such as country codes and some other will change over time such as countries GDP.

The static data in CSV format was loaded into a RDBMS table (PostgreSQL DB on AWS) using a AWS Glue script. 

The other data in CSV and JSON format was loaded into a AWS S3 bucket.

With this data as input, we built an ETL  job (ETL - Extract, Transform & Load) using AWS Glue and PySpark to transform the data into a denormalized CSV format.



### Input

-   Happiness comments & demographics from Kaggle (CSV in S3)
    
-   GDP from Happy Planet Index (JSON in S3)
    
-   Country ISO codes from Kaggle (Tabular data in Postgres)
    

### Processing

-   Crawl all data & generate Data Catalog
    
-   Build ETL job (PySpark) to load Country ISO code into Postgres managed RDS
    
-   Combine Comments, Demographics in CSV format with GDP data in JSON format along with Country ISO codes in RDS to generate denormalized Happiness Report in CSV format
    
-   Build an Athena query to vend Happiness Report using SQL query
    
-   Build a Microservice using Lambda/Fargate container to expose Happiness data through an API
    
-   Build a single-page web application hosted on S3 to visualize the Happiness Report
    

### Output

-   World Happiness Report - Charts

## Solution Architecture
![World Happiness Report - Solution Architecture](https://github.com/skarlekar/WorldHappinessReport/blob/master/images/Glue_POC_Solution_Arch.png)
## AWS Glue
## AWS Athena
## AWS Lambda
## AWS Fargate

## Project Setup Instructions


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1MTUyMjc3MTcsMTYwNDUxMzQwNyw4OT
Q4MjE0ODAsLTE3NDM0NjQ0NjldfQ==
-->