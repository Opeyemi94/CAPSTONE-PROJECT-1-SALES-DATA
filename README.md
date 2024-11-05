# COMFORTZONE-ENTERPRISES-SALES-DATA

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

  ### COLUMN DESCRIPTION FOR SALES DATA
  - OrdeID: A unique identifier to each order
  - CustomerID: A unique identifier for each customer placing an order
  - Product: The specific product purchased in each transaction
  - Region: The Geographical location where order are placed
  - Quantity: The number of units purchased for each product ordered
  - UnitPrice: The price per unit of the product
  - Total Sales/Revenue:  Quantity * UnitPrice

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

![Screenshot (18)](https://github.com/user-attachments/assets/85cf4d2d-7a65-4f5e-ba4e-70e713419b94)

#### ***Potential Recommendations***
Focus on Growth in the West: Given its low sales, the West region may benefit from targeted marketing or expansion strategies to boost its performance.
Maintain Strength in the South and East: These regions are the largest contributors and could be optimized further to maintain or even increase their dominance.
Investigate North Region’s Performance: While not as low as the West, the North’s sales could be improved, possibly by identifying challenges unique to this region.
This analysis highlights disparities across regions and suggests possible actions to balance and improve sales distribution.


### **INSIGHTS**

#### ***Key Points***
This pivot table presents below shows the sales trends by month, highlighting seasonal variations.

```
Products	Sum of Quantity
Jan	 2,480 
Feb	 4,950 
Mar	 3,493 
Apr	 1,485 
May	 994 
Jun	 3,976 
Jul	 5,940 
Aug	 1,992 
Sep	 3,472 
Oct	 4,464 
Nov	 2,970 
Dec	 2,465 
![image](https://github.com/user-attachments/assets/b2927611-005b-4d05-8f78-c8bd190ebbd2)
```

#### Here's a breakdown of the monthly sales, which show patterns in demand over time:

High Sales Months: February (4,950), July (5,940), and October (4,464) have the highest sales, suggesting peaks in these months.
Low Sales Months: May (994) and April (1,485) are notably lower, indicating potential off-seasons.

This pivot table approach reveals that summer and early autumn may be peak seasons, while spring sees a dip, possibly due to seasonal changes in customer demand.

#### ***Key Points***
This pivot table presents below shows the calculation of metrics such as average sales per product and total revenue by region

#### Analyzing the average sales per product values from the provided calculated metrics data below to show insight into product performance, demand trends, and inventory considerations. Here’s a breakdown of what each metric could indicate and how you might interpret or use these results.

- Provided Data
```
PRODUCT	AVERAGE SALES PER PRODUCT
Gloves	8.3
Hat    	8.0
Jacket	3.7
Shirt  	8.3
Shoes	  7.2
Sock	  5.3
```

#### ***High-Performing Products:***
Gloves and Shirts both have an average sales value of 8.3, which suggests they are top performers in terms of average monthly sales.
The higher average could indicate steady demand and popularity among customers, making these reliable products to keep in stock.
Regular promotions or inventory expansion for these items might also be beneficial.

#### ***Mid-Range Products:***
Hats and Shoes show moderately high average sales, with 8.0 and 7.2, respectively.
This level indicates consistent demand but slightly lower than Gloves and Shirts, suggesting these products are also popular but may not sell as quickly.
Monitoring seasonal sales trends for these products could be valuable, as demand for hats and shoes might vary by season (e.g., winter hats or summer shoes).

#### ***Lower-Performing Products:***
Jackets and Socks show lower average sales values, at 3.7 and 5.3.
This could indicate a smaller or more sporadic customer demand, possibly influenced by seasonal needs (e.g., jackets selling primarily in colder months).
For these products, strategies like targeted promotions or seasonal sales could help boost performance.

#### ***Excel Formula Insights***
To calculate these averages in Excel, you would typically use the AVERAGEIF or AVERAGEIFS functions if multiple entries are available per product, or simply AVERAGE if there's one sales figure for each product. Here’s a breakdown of the formulas used for each metric:

AVERAGE Formula:
 =AVERAGEIF(A:A, "Gloves", B:B) to find the average sales for Gloves (where A:A contains product names and B:B contains sales data).
Repeated this for each product by changing the product name in the formula.


### EXCEL VISUALIZATION

![Screenshot (19)](https://github.com/user-attachments/assets/6712febc-30fd-4812-b508-04e82eed2525)



Power BI Dashboard Development:

Import the summarized data from SQL and Excel into Power BI.
Develop an interactive dashboard with visuals like bar charts, line graphs, and maps to illustrate:
Top-selling products.
Regional performance through a heat map or regional bar charts.
Monthly sales trends with a line graph for easy pattern recognition.

