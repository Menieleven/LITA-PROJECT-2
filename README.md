# LITA-PROJECT-2
LITA PROJECT 2
This project gives detailed documentation of LITA DATA ANALYSIS Project work2

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
  - Data cleaning i.e removing Duplicate values - Using this operation in Excel, 41,213 duplicate values were removed and 33787 Unique values remained
  - I also calculated the Subscription Duration USING =DATEDIF([@SubscriptionStart],[@SubscriptionEnd],"D")

## GENERATING REPORT USING PIVOT TABLE
  Highlight or click on the desired cell within your data range
  Go to the insert Tab, Click on the pivot  table button to open a dialog box
  Select Data Range, Choose where to place the pivot table (a new worksheet or in the existing worksheet)
  Build customize and format the table
  
Summarize the Total Number of Customers by region and  Bar chart representation

![Image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/7a8ac35888449933fc470b87512281cddaff3a00/4A1.JPG)

![Image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/7a8ac35888449933fc470b87512281cddaff3a00/4A2.JPG)

 Summarize the Most popular Subscription and pie chart representation
 
![Image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/7a8ac35888449933fc470b87512281cddaff3a00/3a.JPG)


![Image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/7a8ac35888449933fc470b87512281cddaff3a00/3b.JPG)


Summarize The Total Revenue by Subscription type and pie chart representation
![Image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/7a8ac35888449933fc470b87512281cddaff3a00/1a.JPG )

![Image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/7a8ac35888449933fc470b87512281cddaff3a00/1b.JPG)


Summarize The Total Revenue by month and pie chart representation

![Image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/7a8ac35888449933fc470b87512281cddaff3a00/2a.JPG)

![Image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/7a8ac35888449933fc470b87512281cddaff3a00/2b.JPG)


Summarize The Total Revenue by month and pie chart representation

![Image_alt](
![Image_alt](


# EXPLORATORY DATA ANALYSIS (WITH SQL)
Convert excel sheet to csv
Remove headers
import the csv to my sql
Ensure to format the the date column into YYY-MM-DD while importing the csv into my SQL

A. Retrieve the total number of customers from each region.

```
SELECT Region, COUNT(CustomerId) AS Total_Customer
FROM CUSTOMERDATA
GROUP BY Region;


```

B. Find the most popular subscription type by the number of customers.

```
SELECT SubscriptionType, COUNT(Customerid) AS Customer_count
FROM CUSTOMERDATA
GROUP BY Subscriptiontype
ORDER BY  customer_count DESC

```
C. Find customers who canceled their subscription within 6 months.
```
SELECT *
FROM CUSTOMERDATA
WHERE DATEDIFF(month, SubscriptionStart, SubscriptionEnd) <= 6
AND SubscriptionEnd IS NOT NULL 
    AND canceled =1 ;

```
D. calculate the average subscription duration for all customers.

```
SELECT  AVG(Subscription_duration) AS Avg_subscription_duration
from CUSTOMERDATA
```
E. find customers with subscriptions longer than 12 months.

```
SELECT 
    CustomerID, 
    SubscriptionStart, 
    SubscriptionEnd
FROM 
    CUSTOMERDATA

WHERE  DATEDIFF(day, SubscriptionStart, SubscriptionEnd) > 365;
```

F. Calculate total revenue by subscription type.
```
SELECT SubscriptionType, SUM(Revenue) AS Total_revenue

FROM CUSTOMERDATA

GROUP BY SubscriptionType;
```

G. find the top 3 regions by subscription cancellations.
```
alter table customerdata
alter column canceled varchar (50);

SELECT 
  Region, COUNT(*) AS cancellation_count
FROM 
  CUSTOMERDATA
WHERE 
  Canceled = 'cancellation'
GROUP BY 
  region
ORDER BY 
  cancellation_count DESC
```
H Find the total number of active and canceled subscriptions.
```
   SELECT 
  SUM(CASE WHEN SubscriptionType = 'active' THEN 1 ELSE 0 END) AS active_subscriptions,
  SUM(CASE WHEN SubscriptionType = 'canceled' THEN 1 ELSE 0 END) AS canceled_subscriptions
FROM 
 CUSTOMERDATA;

```
EDA involves the exploring of Data to answer some questions about the Data such as;


Pivot tables: the use of Pivot Tables in Excel is an essential part of Exploratory Data Analysis (EDA). Pivot tables help to quickly summarize, analyze, and explore large datasets by organizing and aggregating data in a flexible way, which is key to understanding trends, relationships, and patterns in the data.
The image below is an example of a pivot table that has categorised the total sum of revenue from each region from a dataset


