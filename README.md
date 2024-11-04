# LITA-PROJECT-2
LITA PROJECT 2
This project gives the detailed documentation of LITA DATA ANALYSIS Project work2

### PROJECT TITLE: LITA CAPSTONE DATA ANALYSIS FOR CUSTOMER DATA
## PROJECT OVERVIEW:
In this project, you are tasked with analyzing the sales performance of a retail store. 

AIMS AND OBJECTIVE: explore sales data to uncover key insights such as top-selling products, regional 
performance, and monthly sales trends and produce an interactive Power BI
dashboard highlighting these findings.

### DATA SOURCES
The main data source is the Capstone data uploaded to the learners' database. 
this is an open source data downloaded from my dashboard on the LMS learning platform

### TOOLS USED
- Microsoft Excel [Download Here](https://www.microsoft.com)
  1.  For Data Cleaning
  2.  For Analysis
  3.  For Data Visualization
     
- Microsoft PowerBi [Download Here](https://apps.microsoft.com)
  - For Analysis Cleaning and Visualization
  - For Data Visualization and reporting
    
- CSV (Comma Separated Value)  File
  
- SQL (STRUCTURED QUERY LANGUAGE) [Download Here](https://www.microsoft.com)
  - For Data query
    
- GITHUB
  - For documentation AND Portfolio Building  


## EXPLORATORY DATA ANALYSIS:
Exploratory Data Analysis (EDA) involves investigating and summarizing datasets to discover patterns, trends, relationships, and anomalies, often before applying more complex statistical models.
EDA involves graphical and statistical techniques, helping analysts understand the data's underlying structure, spot errors, and gain insights that inform decision-making and further analysis.


## STAGE 1: WORKING WITH DATA ON MICROSOFT EXCEL
At the initial stage of the project, we downloaded the file from CANVAS LMS 
then we went ahead with Data Cleaning, Removing Duplicates value
  - Data cleaning i.e removing Duplicate values - Using this operation in Excel, 40079 duplicate values were removed and 9921 Unique values remained
  - I also calculated TOTAL REVENUE that is Quantity * Unit sold, to determine the total amount of product sold per day

## GENERATING REPORT USING PIVOT TABLE
  Highlight or click on the desired cell within your data range
  Go to the insert Tab, Click on the pivot  table button to open a dialog box
  Select Data Range, Choose where to place the pivot table (a new worksheet or in the existing worksheet)
  Build customize and format the table
  
Summarize Total sales by product and pie chart representation

![Image_alt](
![Image_alt](

 Summarize Total Sales by region and pie chart representation
 
![Image_alt](
![Image_alt](

Summarize Total Sales by Month In 2023 and pie chart representation

![Image_alt](
![Image_alt](

Summarize average sales by Product 

![Image_alt](
![Image_alt](

Average revenue per Region

![Image_alt](

Summarize total revenue per Region

![Image_alt](


# EXPLORATORY DATA ANALYSIS (WITH SQL)
Convert excel sheet to csv
Remove headers
import the csv to my sql
Ensure to format the the date column into YYY-MM-DD while importing the csv into my SQL

A. Top selling product by total sales value

```
SELECT FROM SALESDATA
SELECT Product, SUM(TotalSales) As TotalSales
FROM orders
GROUP BY TotalSales DESC
LIMIT 1

```
B. Total sales for each product category
```
SELECT Product, SUM(Totalsales) As TotalSales
FROM orders
GROUP BY Product;
```
Number of sales transaction in each region
```
SELECT Region, COUNT(*)As NumberOfTransaction
FROM Orders
GROUP BY Region;
```
4.Total revenue per product

```
SELECT Product, SUM(TotalSales)As TotalRevenue
FROM Orders
GROUP BY Product;
```
5.Monthly sales total for the current year

```
SELECT MONTH(OrderDate)As Month, SUM (TotalSales)As MonthlySales
FROM Orders
WHERE YEAR(OrderDate)=YEAR(CURDATED())
GROUP BY MONTH(OrderDate)
ORDER BY MONTH;
```

Top 5 customer by totalpurchase amount
```
SELECT CustomerID,SUM(TotalSales) As TotalPurchase
FROM orders
GROUP BY CustomerID
ORDER BY TotalPurchase DESC
LIMIT 5;
```

Percentage of total sales contributed by each region
```
SELECT Region,
SUM(TotalSales) As TotalSales,
(SUN(TotalSaless)/(SELECTSUM(TotalSales)FROM orders)*100) As PercentageOfTotalSales
FROM orders
GROUP BY Region;
```
Products with no sale in the last quarter
```
SELECT DISTINCT Product
FROM orders
WHERE Product NOT IN(
SELECT Product
FROM orders
WHERE OrderDate>=DATE_SUB(CURDATE(),INTERVAL 3 MONTH)
);
```
EDA involves the exploring of Data to answer some questions about the Data such as;


Pivot tables: the use of Pivot Tables in Excel is an essential part of Exploratory Data Analysis (EDA). Pivot tables help to quickly summarize, analyze, and explore large datasets by organizing and aggregating data in a flexible way, which is key to understanding trends, relationships, and patterns in the data.
The image below is an example of a pivot table that has categorised the total sum of revenue from each region from a dataset


