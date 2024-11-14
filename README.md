# LITA-PROJECT-2
CUSTOMER DATA ANALYSIS
This project gives detailed documentation of  DATA ANALYSIS Project  CUSTOMER DATA

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

Pivot tables: Pivot Tables in Excel is an essential part of Exploratory Data Analysis (EDA). Pivot tables help to quickly summarize, analyze, and explore large datasets by organizing and aggregating data in a flexible way, which is key to understanding trends, relationships, and patterns in the data.



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

### EXPLORATORY DATA ANALYSIS USING MICROSOFT EXCEL:

Summarize the Total Number of Customers by region and  Bar chart representation

![Image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/7a8ac35888449933fc470b87512281cddaff3a00/4A1.JPG)
![Image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/7a8ac35888449933fc470b87512281cddaff3a00/4A2.JPG)

 Summarize the Most popular Subscription and pie chart representation
 
![Image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/7a8ac35888449933fc470b87512281cddaff3a00/3a.JPG)
![Image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/7a8ac35888449933fc470b87512281cddaff3a00/3b.JPG)


Summarize The Total Revenue by Subscription type and pie chart representation

![Image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/ee3d1b01a94283c6e50015aa898f8f9f0372b06d/1a.JPG)
![Image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/7a8ac35888449933fc470b87512281cddaff3a00/1b.JPG)


Summarize The Total Revenue by month and pie chart representation

![Image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/7a8ac35888449933fc470b87512281cddaff3a00/2a.JPG)
![Image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/7a8ac35888449933fc470b87512281cddaff3a00/2b.JPG)


Summarize The Total Revenue by Subscription type and Bar chart representation

![Image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/7a8ac35888449933fc470b87512281cddaff3a00/5A.JPG)
![Image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/7a8ac35888449933fc470b87512281cddaff3a00/5B.JPG)


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
H. Find the total number of active and canceled subscriptions.
```
   SELECT 
  SUM(CASE WHEN SubscriptionType = 'active' THEN 1 ELSE 0 END) AS active_subscriptions,
  SUM(CASE WHEN SubscriptionType = 'canceled' THEN 1 ELSE 0 END) AS canceled_subscriptions
FROM 
 CUSTOMERDATA;

```
### EXPLORATORY DATA ANALYSIS USING POWERBI

OVERVIEW OF CUSTOMER DATA

![image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/b3955e39f81be8f503b080d0f0881603921f99b9/powebi%201.JPG)

OVERVIEW OF CUSTOMER DATA FOR BASIC SUBSCRIPTION TYPE

![image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/b3955e39f81be8f503b080d0f0881603921f99b9/BASIC%20SUB.JPG) 

OVERVIEW OF CUSTOMER DATA FOR PREMIUM SUBSCRIPTION TYPE

![image_alt](https://github.com/Menieleven/LITA-PROJECT-2/blob/b3955e39f81be8f503b080d0f0881603921f99b9/PREMIUM.JPG)

### SUMMARY
The image is a comprehensive data analysis report titled "LITA DATA ANALYSIS - CUSTOMER DATA PROJECT REPORT." It provides various metrics and visualizations related to customer data, including counts, sums, and averages. Key metrics include:
- **Count of CustomerID:** 33.79K
- **Sum of Revenue:** 67.5M
- **Sum of Subscription Duration:** 12M
- **Count of Subscription Type:** 3
- **Average Subscription Duration:** 365 days
- **Average Total:** 1,999

The report includes several visualizations:
1. **Sum of Revenue by Region:** Displays revenue distribution across different regions (East, South, North, West).
2. **Sum of Customer ID by Region:** Shows the number of customers in each region.
3. **Sum of Revenue by Subscription Type:** Compares revenue generated by Basic, Premium, and Standard subscription types.
4. **Sum of Subscription Duration by Region and Canceled:** Illustrates subscription duration across regions and cancellations.
5. **Highest Performing Subscription Type:** Highlights the subscription type with the highest performance.
6. A map showing the sum of revenue by region, with regions labeled (e.g., Nigeria, Cameroon).

### CONCLUSION
The data analysis reveals several insights:
1. The highest revenue is generated from the Basic subscription type, contributing 34M.
2. The East region has the highest sum of revenue and customer count, indicating a strong market presence.
3. The average subscription duration is 365 days, suggesting annual subscriptions are common.
4. The average total metric of 1,999 indicates a significant customer base engagement.

### RECOMMENDATION 
1. **Focus on the East Region:** Given its high revenue and customer count, further marketing and customer engagement efforts should be concentrated in the East region to maximize growth.
2. **Enhance Basic Subscription Offerings:** Since the Basic subscription type generates the most revenue, consider enhancing its features or offering additional benefits to retain and attract more customers.
3. **Investigate Cancellations:** Analyze the reasons behind subscription cancellations in various regions to develop strategies for reducing churn and improving customer retention.
4. **Expand in Underperforming Regions:** Develop targeted marketing campaigns and promotions to boost revenue and customer acquisition in regions with lower performance, such as the North and West regions.

By focusing on these areas, the business can enhance its overall performance and customer satisfaction. If you need more detailed strategies or assistance with other tasks, I'm here to help!
