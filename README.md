# LITA-CAPSTONE-PROJECT
### My LITA Capstone project documentation
---
### Project 1: Sales Performance Analysis for a Retail Store
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
 

![Pivot (Sales data)](https://github.com/user-attachments/assets/76cd9566-83f1-4945-af30-d6d5a9c31e36)


![Dashboard (Sales Data)](https://github.com/user-attachments/assets/cfa29c4a-6e02-4b7c-a95c-bcfff79c4118)





---
### Project 2: Customer Segmentation for a Subscription Service
---

#### Project Overview
This project aims to analyze customer data for a subscription service identifying segments and trends. By analyzing this data I seek to understand customer behavior, track subscription types, and identify key trends in cancellations and renewals and then produce an interactive dashboard that highlights these findings that will enable me to tell compelling stories

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
- What is the average subscription duration 
- What is the most popular subscription type
- What is the total number of customers for each region


#### Data Analysis


This includes the functions used in Excel, Pivot Tables, and Lines of query used in SQL;
- Using the DAYS function to determine the subscription duration. 

```EXCEL
=DAYS(F2:F33788,E2:E33788)
```
Then I used the average function to determine the average subscription duration. 
```EXCEL
=AVERAGE(I2:I33788)
``` 

Below are the queries used in SQL
- To retrieve the total number of customers from each region
```SQL
select region,
count (customerid) as Total_no_of_customers
from [dbo].[Customer data]
group by region
order by Total_no_of_customers
```
- To find the most popular subscription type by number of customers
```SQL
SELECT TOP 1 SubscriptionType,
COUNT (CUSTOMERID) AS NUMBER_OF_CUSTOMER
FROM [dbo].[Customer data]
GROUP BY SubscriptionType
ORDER BY NUMBER_OF_CUSTOMER DESC
```
- To find customers who canceled their subscription within six months
```SQL
SELECT CustomerID, SubscriptionEnd
from [dbo].[Customer data]
where  canceled = 'true'
and subscriptionEnd >=
dateadd(month, -6, getdate());
```
- To calculate the average subscription duration for all customers
```SQL
SELECT 
AVG (DATEDIFF(day, SubscriptionStart, SubscriptionEnd)) as Average_subscription_duration
from [dbo].[Customer data]
```
- To find customers with subscription longer than 12 months
```SQL
select CustomerID, CustomerName, SubscriptionStart, SubscriptionEnd
from [dbo].[Customer data]
where Datediff (Month, SubscriptionStart, ISNULL (SubscriptionEnd, GETdate())) >12
```
- To calculate total revenue by subscription type
```SQL
SELECT SubscriptionType,
sum (Revenue) as Total_Revenue
from [dbo].[Customer data]
group by SubscriptionType
Order by Total_Revenue
```

- To find the top 3 region by subscription cancellations
```SQL
select TOP 3 Region,
count (*) as Subscription_Cancellation
from [dbo].[Customer data]
where Canceled = 'True'
group by Region
Order by Subscription_Cancellation DESC
```
- To find the total number of active and canceled subscription
```SQL
SELECT Canceled,
count (*) as Total_Subscription
from [dbo].[Customer data]
Group by Canceled
order by Total_Subscription
```
