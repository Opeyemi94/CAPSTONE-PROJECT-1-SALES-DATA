![Screenshot (18)](https://github.com/user-attachments/assets/85cf4d2d-7a65-4f5e-ba4e-70e713419b94)# COMFORTZONE-ENTERPRISES-SALES-DATA

### **PROJECT SUMMARY:**
____________
**COMFORTZONE ENTERPRISES** project aims to perform a detailed exploration of sales data to provide actionable insights into product performance, regional sales, and monthly sales trends. The ultimate goal is to create an interactive Power BI dashboard that allows managements and stakeholders to quickly and easily visualize key sales insights.

### **PROJECT OVERVIEW:**
________________
**COMFORTZONE ENTERPRISES** want to boost its sales but is having trouble figuring out what's really driving their performance. With a lot of sales data coming from different regions and products, it's tough to see whcih items are the best sellers, how each area us doing, and how sales change month to month. 

So the goes of this project is to look more into this data to find more clear insights. By doing so, I will create a Power BI Visualization so as to know what's wortking and what's not working. So am helping COMFORTZONE make smarter decision to increase sales and better serve their customers. 

### **DATA SOURCES**
______________
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
________________
1. Identify Top-Selling Products: Analyze sales data to determine which products drive the highest revenue.
2. Assess Regional Performance: Examine sales across different regions to highlight the strongest and weakest performers.
3. Analyze Monthly Sales Trends: Track monthly sales patterns to identify seasonality, peaks, and troughs.

### **DATA ANALYSIS APPROACH:**
_______________
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
   5. Calculate monthly sales totals for the current year.
      ```
       select * from [dbo].[SALES DATA]

      alter table [dbo].[SALES DATA]
      Add OrderMonth nvarchar (50)
      update [dbo].[SALES DATA]
      set OrderMonth = datename (Month, Orderdate)

      alter table [dbo].[SALES DATA]
      add OrderYear int
      
      update [dbo].[SALES DATA]
      set OrderYear = YEar (OrderDate)
      
      select OrderMonth, Sum (quantity*UnitPrice) as Total_Sales 
      From [dbo].[SALES DATA]
      where orderYear = 2024
      group by OrderMonth
      ```
   6. Find the top 5 customers by total purchase amount.
      ```
      SELECT TOP 5 CUSTOMER_ID, SUM(QUANTITY) AS Total_Purchase
      FROM [dbo].[SALES DATA]
      GROUP BY CUSTOMER_ID  
      Order by Total_Purchase Desc
      ``` 
   7. Calculate the percentage of total sales contributed by each region.
      ```
      select Region, sum (Revenue) /
      Sum (Quantity*UnitPrice) * 0.1 as Percentage_of_Total_Sales
      from [dbo].[SALES DATA]
      group by Region
      Order by Percentage_of_Total_Sales
      ```
    8. Identify products with no sales in the last quarter.
       ```
       select product, sum (Quantity) as Sales
      from [dbo].[SALES DATA]
      where Month (Orderdate) between 10 and 12 
      group by product 
      having sum(Quantity) = 0 
       ```

### **EXCEL (PIVOT TABLE AND EXCEL VISUALIZATION):**
- Product Sales Summary: Create a pivot table that displays total sales by product, allowing for the quick identification of top sellers.
- Regional Sales Summary: Summarize sales by region to compare performance across different geographic areas.
- Monthly Sales Trends: Use a pivot table to show sales trends by month, highlighting seasonal variations.
- Use Excel formulas to calculate metrics such as average sales per product and 
  total revenue by region

### **INSIGHT**

#### TOTAL SALES BY PRODUCT 
This pivot table presents below shows the total sales of six different product categories. Here's a breakdown and analysis:
```
Gloves	 296,900 
Hat	     316,195 
Jacket	 208,230 
Shirt	   485,600 
Shoes	   613,380 
Socks	   180,785 
```

#### ***Top-Performing Products:***
Shoes: With sales of $613,380 , shoes are the highest-grossing product, contributing approximately 29.2% of the overall sales.

Shirt: The second highest, with $485,600  in sales, accounting for around 23.1% of total sales.

#### **Mid-Level Performers:**

Hat: Sales are $316,195 about 15% of total sales.

Gloves: Sales amount to $296,900, close to hats, contributing roughly 14.2%.

#### ***Low-Performing Products:***

Jacket: Sales are $208,230 , making up around 9.9% of the total.

Socks: The lowest in terms of sales, with $180,785 or about 8.6%.

#### ***Potential Recommendations***
Shoes and Shirts are the dominant categories, together making up over 52% of the total sales. Efforts to promote or expand these categories might yield high returns.
Socks and Jackets have the lowest sales and may require further investigation—such as pricing, demand, or seasonal influences—to determine if improvements or adjustments are needed.
This breakdown can help prioritize product focus areas and sales strategies based on contribution to total sales.

### **INSIGHTS**

#### ***Key Points***
This pivot table presents below shows the total sales of Four different Region. Here's a breakdown and analysis:

#### ***Top-Performing Region:***
The South Region has the highest sales, totaling $480,820
This region alone contributes approximately 43.5% of the total sales.

#### ***Second-Highest Sales Region:***
The East Region follows, with $393,945 in sales.
It accounts for roughly 35.6% of the total sales.

#### ***Third-Highest Sales Region:***
The North Region follows, with $143,960 in sales.
It accounts for roughly 13.1% of the total sales.

#### ***Lowest Sales Region:***
The West region shows the lowest sales, amounting to $86,605.
This represents just about 7.8% of the total sales, indicating it may be underperforming compared to other regions.

#### ***Comparative Performance:***
The South region's sales are over 3.3 times higher than the West region.
The West and North regions have significantly different sales figures, with the East achieving about 2.7 times more sales than the North.

#### ***Proportional Analysis:***
South and East together make up a large portion of sales, totaling $874,765 or 79.1% of the total sales.
North and West combined contribute only $230,565 or 20.9%, suggesting that they may need attention or growth strategies.
Visual Insights (Hypothetical Suggestions for Visualization)
To further understand and communicate this data, consider:

Bar Chart: To highlight each region's total sales, showing the comparison between them visually.

Pie Chart: For a percentage view of each region's contribution to the total sales, emphasizing how much each region adds to the overall performance.

[Uploading Screenshot (18).png…]()

#### ***Potential Recommendations***
Focus on Growth in the West: Given its low sales, the West region may benefit from targeted marketing or expansion strategies to boost its performance.
Maintain Strength in the South and East: These regions are the largest contributors and could be optimized further to maintain or even increase their dominance.
Investigate North Region’s Performance: While not as low as the West, the North’s sales could be improved, possibly by identifying challenges unique to this region.
This analysis highlights disparities across regions and suggests possible actions to balance and improve sales distribution.


















Power BI Dashboard Development:

Import the summarized data from SQL and Excel into Power BI.
Develop an interactive dashboard with visuals like bar charts, line graphs, and maps to illustrate:
Top-selling products.
Regional performance through a heat map or regional bar charts.
Monthly sales trends with a line graph for easy pattern recognition.

