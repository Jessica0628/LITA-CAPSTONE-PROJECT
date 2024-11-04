# LITA-CAPSTONE-PROJECT
### My LITA Capstone project documentation
---
### Project 1: Sales Performance Analysis for a Retail Store 
#### Project Overview
This project aims to generate insight and analyze the sales performance of a retail store. By analyzing the sales data I seek to uncover key insights and produce an interactive dashboard that highlights these findings and enables me to tell compelling stories.

#### Data Sources
The Source of the data used is LITA Capstone Project. xlsx, gotten from CANVAS INSTRUCTURE

#### Tools Used
- Microsoft Excel [Download Here](https://WWW.microsoft.com)
   1. For data cleaning
   2. Analysis
   3. and visualization
- SQL – Structured Query Language [Download Here](WWW.microsoft.com)
   1. For querying of data
- Power BI [Download Here](https://www.microsoft.com)
   1. for visualization of data
- GitHub [Open Here](https://github.com)
   1. for portfolio building

#### Data cleaning and Preparation

Once the dataset was obtained, data cleaning was done and duplicate data were removed using the following actions
1.	Data Inspection
- performed an initial exploratory analysis to understand the structure and type of data
2.	Duplicate Removal
- Identified and removed duplicate records to ensure the data integrity of results.
3.	Handling Missing Data
- Addressed missing data by applying appropriate techniques such as creating new columns where necessary

#### Exploratory Data Analysis

This involved the exploration of the data to answer some questions about the data such as;
-	What is the average sales per product 
-	What is the total revenue by region
-	What is the total sales per product
-	What is the maximum sales per product
-	What is the total sales for each month

#### Data Analysis

This includes the functions used in Excel, Pivot Tables, and Lines of query used in SQL;
- Using the AVERAGEIF function, to get the average sale per product in excel
```EXCEL
=AVERAGEIF(C:C,C7,H:H)
```

also used the SUMIF function to get the total sales per region
```EXCEL
=SUMIF(D:D,D4,H:H)
```

