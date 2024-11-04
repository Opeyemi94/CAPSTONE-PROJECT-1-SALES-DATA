# COMFORTZONE-SALES-DATA

### **PROJECT SUMMARY:**
____________
**COMFORTZONE ENTERPRISES** project aims to perform a detailed exploration of sales data to provide actionable insights into product performance, regional sales, and monthly sales trends. The ultimate goal is to create an interactive Power BI dashboard that allows managements and stakeholders to quickly and easily visualize key sales insights.

### **PROJECT OVERVIEW:**
________________
**COMFORTZONE ENTERPRISES** want to boost its sales but is having trouble figuring out what's really driving their performance. With a lot of sales data coming from different regions and products, it's tough to see whcih items are the best sellers, how each area us doing, and how sales change month to month. 

So the goes of this project is to look more into this data to find more clear insights. By doing so, I will create a Power BI Visualization so as to know what's wortking and what's not working. So am helping COMFORTZONE make smarter decision to increase sales and better serve their customers. 

### **DATA SOURCES**
The Primary source of Data used here is coming from COMFORTZONE ENTERPRISES Sales and Marketing Department.  

#### ***Tools used in this project are:***
- Micro-soft Excel [Download Here](http://www.microsoft.com)
  1. Data Cleaning
  2. Analysis
  3. For Data Visualization
- Structred Query Langauge(SQL) [Download Here](https://www.mircosoft.com)
  1. For Data Quries  
- Power Business Intelligence [Download Here](https://www.mircosoft.com)
  1. To Create a dashboard that visualizes the insights found in Excel and SQL.

### **OBJECTIVES:**
1. Identify Top-Selling Products: Analyze sales data to determine which products drive the highest revenue.
2. Assess Regional Performance: Examine sales across different regions to highlight the strongest and weakest performers.
3. Analyze Monthly Sales Trends: Track monthly sales patterns to identify seasonality, peaks, and troughs.

### **DATA ANALYSIS APPROACH:**

#### ***SQL Data Extraction:***
- Use SQL to query and organize the raw data, filtering by product, region, and date.
- Apply SQL aggregations the following below:
   1. Retrieve the total sales for each product category.
      ```
      Select product, SUM (quantity*UnitPrice) as Total_Sales
      From [dbo].[SALES DATA]
      Group by Product
      ```
   2. Find the number of sales transactions in each region.
      
      ```
      select region, sum(quantity*UnitPrice) as Sales_Per_Region
      From [dbo].[SALES DATA]
      Group by Region
      ```
   3. Find the highest-selling product by total sales value.
      ```
      Select Product, Sum(Quantity*UnitPrice) as Total_Sales
      from  [dbo].[SALES DATA]
      group by Product
      ```
   4. Calculate total revenue per product.
        ```
       select Product, sum(Revenue) as Total_Revenue
      from [dbo].[SALES DATA]
      group by product
      ```
   6. Calculate monthly sales totals for the current year.
   7. Find the top 5 customers by total purchase amount.
   8. Calculate the percentage of total sales contributed by each region.
   9. Identify products with no sales in the last quarter.


#### ***Pivot Tables in Excel:***
- Product Sales Summary: Create a pivot table that displays total sales by product, allowing for the quick identification of top sellers.
- Regional Sales Summary: Summarize sales by region to compare performance across different geographic areas.
- Monthly Sales Trends: Use a pivot table to show sales trends by month, highlighting seasonal variations.
Power BI Dashboard Development:

Import the summarized data from SQL and Excel into Power BI.
Develop an interactive dashboard with visuals like bar charts, line graphs, and maps to illustrate:
Top-selling products.
Regional performance through a heat map or regional bar charts.
Monthly sales trends with a line graph for easy pattern recognition.

