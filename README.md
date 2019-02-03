# World Happiness Report

To demonstrate building an end-to-end **serverless data pipeline** and a full-stack application using *AWS S3, Glue, Athena, Lambda* and/or *Fargate*.


# What Makes People Happy vs Country GDPs

## Problem Statement

What makes people happy in their day-to-day activities and how does it relate to  country’s GDP?

## Solution
To answer the aforementioned problem, we collected data from multiple sources. The data was in different formats such as CSV and JSON. Some of this data was static in nature such as country codes and some other will change over time such as countries GDP.

The static data in CSV format was loaded into a RDBMS table (PostgreSQL DB on AWS) using a AWS Glue script. 

The other data in CSV and JSON format was loaded into a AWS S3 bucket.

With this data as input, we built an ETL  job (ETL - Extract, Transform & Load) using AWS Glue  to transform the data into a denormalized CSV format which was pushed out to another S3 bucket.

With the final data in S3, we built an Athena query to query this data in SQL format. 

With the Athena query in place, we wrote a micro service using AWS Lambda function that calls the Athena query and vends the data out in JSON format.

The micro service was exposed via an API through AWS API Gateway.

A front-end web application hosted in S3 was used to visualize the data as charts.

### Input

-   Happiness comments & demographics from Kaggle (CSV in S3).  
	Happy DB is a corpus of more than 100,000 happy moments crowd-sourced from various people across the world.  The data consists of comments and demographics.
    https://www.kaggle.com/ritresearch/happydb
-   GDP from Happy Planet Index (JSON in S3).  
    Happy Planet Index is an organization that measures how well nations are doing at achieving, long, happy and sustainable lives. Apart from HPI index, this data contains the GDP of different nations around the world.
    http://happyplanetindex.org/s/hpi-data-2016.xlsx
    (the above spreadsheet was converted to JSON format to demonstrate AWS Glue's ability to use JSON as input)
-   Country ISO codes from Kaggle (tabular data in Postgres).  
	The country names in Happy DB were three character ISO code, whereas the country names in Happy Planet Index that contained nations' GDP were in English names. To combine these two data sets, we downloaded the Country ISO code Kaggle set.
    

### Processing

-   Crawl all data & generate Data Catalog
    
-   Build ETL job (PySpark) to load Country ISO code into Postgres managed RDS
    
-   Combine Comments, Demographics in CSV format with GDP data in JSON format along with Country ISO codes in RDS to generate denormalized Happiness Report in CSV format
    
-   Build an Athena query to vend Happiness Report using SQL query
    
-   Build a Microservice using Lambda/Fargate container to expose Happiness data through an API
    
-   Build a single-page web application hosted on S3 to visualize the Happiness Report
    

### Output

-   World Happiness Report - Charts.  
	The generated report plots various happiness categories as a stacked bar chart and overlays the corresponding nation's GDP on top of it. It further allows, isolating a happiness dimension by double-clicking on it as the following animation shows.
	
![World Happiness Report Output](https://github.com/skarlekar/WorldHappinessReport/blob/master/images/WorldHappinessReport_Animated.gif)

## Solution Architecture
![World Happiness Report - Solution Architecture](https://github.com/skarlekar/WorldHappinessReport/blob/master/images/Glue_POC_Solution_Arch.png)
## AWS Glue
## AWS Athena
## AWS Lambda
## AWS Fargate

## Project Setup Instructions


<!--stackedit_data:
eyJoaXN0b3J5IjpbNzY5ODk0MzM1LDIwMDE5OTkxOTEsLTE3Nj
EzNjg0MDIsLTE2OTI3MzY0MzgsNTU4OTA1NTEwLDkwMjc5NzY5
NiwxNjA0NTEzNDA3LDg5NDgyMTQ4MCwtMTc0MzQ2NDQ2OV19
-->