# LITA-CAPSTONE-PROJECT
### My LITA Capstone project documentation
---
## Project Outline
[Project Overview](Project-Overview)

[Data Sources](Data-Sources)

[Tools Used](Tools-Used)

[Data cleaning and Preparation](Data-cleaning-and-Preparation)

[Exploratory Data Analysis](Exploratory-Data-Analysis)

[Data Analysis](Data-Analysis)

[Data Visualization](Data-Visualization)

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
1.	Data Loading and Inspection
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

This includes the functions used in Excel, and Lines of query used in SQL;
- Using the AVERAGEIF function, to get the average sale per product in excel
```EXCEL
=AVERAGEIF(C:C,C7,H:H)
```

also I used the SUMIF function to get the total sales per region
```EXCEL
=SUMIF(D:D,D4,H:H)
```
Below are the queries used in SQL

- To retrieve the total sales for each product category
```SQL
Select 
Product, Sum (Total_Sales_Revenue) as total_sales
from [dbo].[Sales Data]
group by Product
order by total_sales
```
To find the number of sales transactions in each region
```SQL
select region,
count (*) as Number_Of_Sales_Transaction
from [dbo].[Sales Data]
group by Region
```
To find the highest-selling product by total sales value
```SQL
SELECT TOP 1 PRODUCT,
sum (Quantity * UnitPrice) as Highest_Selling
From [dbo].[Sales Data]
GROUP BY PRODUCT
order by Highest_Selling DESC
```
To calculate total revenue per product.
```SQL
SELECT PRODUCT,
SUM (Quantity * UnitPrice) as total_revenue
from [dbo].[Sales Data]
group by Product
order by total_revenue
```

To calculate monthly sales totals for the current year
```SQL
SELECT
Sum (Total_Sales_Revenue) as SalesTotal
from [dbo].[Sales Data]
where Year (OrderDate) = '2024'
Group by month(OrderDate)
ORDER BY SalesTotal
```
To find the top 5 customers by total purchase amount
```SQL
SELECT TOP 5 CUSTOMER_ID, 
sum (Quantity * UnitPrice) as Total_Purchase_Amount
from [dbo].[Sales Data]
Group by Customer_Id
order by Total_Purchase_Amount DESC
```
To calculate the percentage of total sales contributed by each region.
```SQL
select
Region, sum (Total_Sales_Revenue) as Region_Sales,
concat (round ((sum (Total_Sales_Revenue) / (select sum (Total_Sales_Revenue) from [dbo].[Sales Data])* 100),2),'%')
as percentage_of_total_sales
from [dbo].[Sales Data]
Group by Region
order by Region_Sales
```
To identify products with no sales in the last quarter
```SQL
select product,
count (Total_Sales_Revenue) as Sales
from [dbo].[Sales Data]
where Total_Sales_Revenue = '0'
group by Product
order by Sales
```


#### Data Visualization

Below are the visualiztions created for the data set ranging from pivot tables, to Power BI visualization dashboards These visuals shows and highlights key insights found in excel and SQL. The visuals show the sales overview of each product highlighting the maximun, average and total sales per product and the total sale made from each region showcasing the top product and region with the most revenue

- Excel sheet showing average sales per product and total revenue by region

![Sales data average sales function](https://github.com/user-attachments/assets/87e0dd38-e476-4db9-a256-490f51dd7046)

Pivot table showing 

![Pivot (Sales data)](https://github.com/user-attachments/assets/76cd9566-83f1-4945-af30-d6d5a9c31e36)

![Dashboard (Sales Data)](https://github.com/user-attachments/assets/cfa29c4a-6e02-4b7c-a95c-bcfff79c4118)



