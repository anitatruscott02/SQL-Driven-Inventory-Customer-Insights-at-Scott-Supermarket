## SQL-Driven-Inventory-Customer-Insights-at-Scott-Supermarket
This project leverages SQL analytics to transform Scott Supermarket's sales data into actionable insights, optimizing inventory management and enhancing customer engagement for better profitability.

## Project Overview
I have observed that Scott Supermarket is sitting on a wealth of sales and product data that isn't being effectively utilized. As a result, they often face issues like overstocking or understocking, miss opportunities to target the right customers, and overlook key trends that could boost profits. My goal is to design a smart system using SQL analytics that transforms this raw data into clear, actionable insights. This will enable Scott Supermarket to understand sales patterns, grasp customer preferences, and make data-driven decisions to optimize inventory, improve customer targeting, and enhance overall profitability.

## About Data
This project's data was obtained from the Adventure Works Sample Database and encompasses a wide range of sales transactions and product details from a manufacturing and distribution enterprise. The analysis leverages key tables including SalesOrderHeader, SalesOrderDetail, Production.Product, Production.ProductSubcategory, Production.ProductCategory, Production.ProductReview, Production.ProductInventory, and Sales.Customer. The integrated dataset captures various dimensions of the business, enabling in-depth analyses such as monthly sales trends, product category performance, order accumulation, customer behavior, and inventory turnover.
Source - https://www.kaggle.com/datasets/algorismus/adventure-works-in-excel-tables

Key Attributes used in this Analysis:

| Column Name          | Description                                                                                                  |
|----------------------|--------------------------------------------------------------------------------------------------------------|
| TerritoryID          | Identifier for the sales territory where the order was placed.                                               |
| CountryRegionCode    | Code representing the country or region associated with the sale.                                            |
| ProductName          | Name of the product sold.                                                                                    |
| OrderQty             | Number of units ordered in the sales order.                                                                  |
| LineTotal            | Total amount for the line item (calculated as unit price multiplied by quantity, adjusted for discounts).    |
| OrderDate            | Date when the order was placed by the customer.                                                              |
| TotalDue             | Total amount due for the order, including taxes and any additional fees.                                     |
| ProductCategory      | Category to which the product belongs (e.g., Bikes, Accessories, Components).                                |
| TotalRevenue         | Aggregate revenue generated from the order or a series of orders.                                            |
| SalesOrderID         | Unique identifier for the sales order.                                                                       |
| CustomerID           | Unique identifier for the customer who placed the order.                                                     |
| PersonType           | Type of person related to the customer record (such as individual or organization).                          |
| ReviewDate           | Date when the product or service was reviewed by the customer.                                               |
| Rating               | Customer or product rating, typically measured on a scale (for example, 1 to 5).                             |
| Quantity             | Number of items involved in the order (may reflect shipped quantity, distinct from OrderQty if needed).      |
| ProductID            | Unique identifier for the product.                                                                           |
| AvgStock             | Average stock level for the product, indicating typical inventory availability over time.                    |


## Analysis
**Product Analysis**  
This project examines various product categories to determine the highest revenue-generating items and identify underperforming products. By analyzing profitability and inventory turnover, we can assess which products contribute most to overall sales and which may require strategic adjustments.  

**Sales Analysis**  
The analysis focuses on sales trends across different periods to uncover patterns in customer spending. Monthly sales trends, cumulative revenue growth, and sales distribution across categories help in evaluating business performance and optimizing sales strategies.  

**Customer Analysis**  
This section explores customer purchasing behavior by segmenting buyers based on transaction frequency and order value. Identifying top customers, analyzing spending trends, and comparing average order values provide insights into customer preferences and business growth opportunities.

## Methodology
### **1. Data Wrangling**  
The dataset is first examined for inconsistencies and structured to align with the analysis objectives. Missing values are checked, but due to enforced constraints (e.g., NOT NULL fields), data integrity is maintained from the tables importing stage.  

- The AdventureWorks dataset is structured into relevant tables for sales, products, and customers  
- SQL queries are used to validate data completeness and identify key fields required for analysis.  

### **2. Feature Engineering**  
To support deeper insights, new attributes are derived from existing columns.    
- **Day and Month Extraction:** Weekday and month columns are derived to highlight peak sales days and seasonal trends.  
- **Cumulative Sales Calculation:** Running totals of revenue are computed to track progressive business growth.  

### **3. Exploratory Data Analysis (EDA)**  
SQL-based analysis is conducted to meet the project objectives, leveraging the AdventureWorks dataset:  

- **Sales Trends Analysis:** Monthly sales trends are examined to detect seasonal fluctuations and peak demand periods.  
- **Revenue Drivers Identification:** Top-performing product categories and individual items are ranked by revenue contribution.  
- **High-Value Transactions Detection:** Orders exceeding the average transaction value are highlighted to understand high-impact sales patterns.  
- **Customer Insights:** The most frequent buyers are identified to support loyalty strategies.   
- **Inventory Turnover Analysis:** Stock movement is evaluated to align supply with demand.  
 

These insights provide Scott Supermarket with actionable intelligence for optimizing sales strategies, inventory management, and customer engagement.

## Business Questions

**Generic Questions**  
- **How many distinct regions are represented in the Adventure Works dataset?**
<pre> ```sql -- Get total number of distinct regions 
 SELECT COUNT(DISTINCT TerritoryID) AS TotalRegions 
 FROM Sales.SalesTerritory; ``` </pre>
Out of the dataset, I found 10 distinct regions, indicating that Scott Supermarket operates across 10 different territories. I will now focus on analyzing regional performance to optimize our local strategies.

Total Region -10 
- **In which city or territory is each store or branch located?**
-- In which city or territory is each store or branch located?
SELECT 
    TerritoryID, 
    Name AS TerritoryName, 
    CountryRegionCode
FROM 
    Sales.SalesTerritory;


| TerritoryID | TerritoryName     | CountryRegionCode |
|-------------|------------------|-------------------|
| 1           | Northwest        | US                |
| 2           | Northeast        | US                |
| 3           | Central          | US                |
| 4           | Southwest        | US                |
| 5           | Southeast        | US                |
| 6           | Canada           | CA                |
| 7           | France           | FR                |
| 8           | Germany          | DE                |
| 9           | Australia        | AU                |
| 10          | United Kingdom   | GB                | 

Scott Supermarket operates across 10 territories, including Northwest, Northeast, Central, Southwest, and Southeast in the US, as well as Canada, France, Germany, Australia, and the UK. I will now analyze store performance across these regions to identify trends and opportunities.

**Product Analysis**  
- **How many distinct product categories or lines exist in the dataset?**
  
TotalProductCategories: 4

Scott Supermarket offers products across 4 distinct categories. I will now analyze category performance to identify best-selling and underperforming product lines.
 
- **Which product line is the highest seller based on revenue and volume?**

| ProductCategory | TotalUnitsSold | TotalRevenue        |
|----------------|---------------|----------------------|
| Bikes         | 90,268         | 94,651,172.70       |
| Components    | 49,044         | 11,802,593.29       |
| Clothing      | 73,670         | 2,120,542.52        |
| Accessories   | 61,932         | 1,272,072.88        |

At Scott Supermarket, the Bikes category stands out as the top performer, with 90,268 units sold generating approximately $94.65 million in revenue. I will now explore what drives this success to further boost our overall performance.

- **What is the total monthly revenue generated by each product line?**

| SalesYear | SalesMonth | ProductCategory | TotalRevenue |
|-----------|-----------|-----------------|--------------|
| 2011      | 5         | Bikes           | 467709.14    |
| 2011      | 5         | Components      | 31525.96     |
| 2011      | 5         | Clothing        | 2875.15      |
| 2011      | 5         | Accessories     | 1695.67      |
| 2011      | 6          | Bikes           | 458,910.82         |
| 2011      | 7          | Bikes           | 1,919,445.21       |
| 2011      | 7          | Components      | 114,523.02         |
| 2011      | 7          | Clothing        | 7,038.58           |
| 2011      | 7          | Accessories     | 3,593.20           |
| 2011      | 8          | Bikes           | 2,317,589.60       |
| 2011      | 8          | Components      | 164,317.13         |
| 2011      | 8          | Clothing        | 8,722.08           |
| 2011      | 8          | Accessories     | 5,187.93           |
| 2011      | 9          | Bikes           | 502,073.85         |
| 2011      | 10         | Bikes           | 4,258,153.85       |
| 2011      | 10         | Components      | 305,108.87         |
| 2011      | 10         | Clothing        | 15,740.53          |
| 2011      | 10         | Accessories     | 9,758.57           |
| 2011      | 11         | Bikes           | 737,839.82         |
| 2011      | 12         | Bikes           | 1,283,924.64       |
| 2011      | 12         | Components      | 23,698.06          |
| 2011      | 12         | Clothing        | 1,655.14           |
| 2011      | 12         | Accessories     | 585.41             |
| 2012      | 1          | Bikes           | 3,804,873.10       |
| 2012      | 1          | Components      | 151,345.70         |
| 2012      | 1          | Clothing        | 10,048.19          |
| 2012      | 1          | Accessories     | 4,360.28           |
| 2012      | 2          | Bikes           | 1,406,374.23       |
| 2012      | 2          | Components      | 63,623.65          |
| 2012      | 2          | Clothing        | 3,652.62           |
| 2012      | 2          | Accessories     | 1,776.41           |
| 2012      | 3          | Bikes           | 2,789,357.61       |
| 2012      | 3          | Components      | 171,325.62         |
| 2012      | 3          | Clothing        | 9,487.17           |
| 2012      | 3          | Accessories     | 5,577.84           |
| 2012      | 4          | Bikes           | 1,481,915.87       |
| 2012      | 4          | Components      | 141,297.30         |
| 2012      | 4          | Clothing        | 7,108.08           |
| 2012      | 4          | Accessories     | 4,279.54           |
| 2012      | 5          | Bikes           | 2,482,840.92       |
| 2012      | 5          | Components      | 508,112.53         |
| 2012      | 5          | Clothing        | 73,171.76          |
| 2012      | 5          | Accessories     | 10,477.60          |
| 2012      | 6          | Bikes           | 3,178,084.92       |
| 2012      | 6          | Components      | 799,484.50         |
| 2012      | 6          | Clothing        | 103,232.55         |
| 2012      | 6          | Accessories     | 18,552.39          |

In May 2011, Bikes led the pack with $467,709 in revenue, while Components, Clothing, and Accessories generated much lower figures. This monthly trend shows that Bikes consistently outperforms the other product lines. I will now focus on strategies to further boost revenue in the supporting categories.

- ** Which month recorded the highest overall Cost of Goods Sold (COGS)? **
  
| SalesMonth | SalesYear | TotalCOGS      |
|------------|----------|-----------------|
| 3          | 2014     | 8097036.3137    |

In March 2014, our Cost of Goods Sold peaked at approximately $8,097,036.31. I will now investigate the factors driving this spike to optimize our cost management strategies.

- **Which product line contributes the most to total revenue?**
  
| ProductCategory | TotalRevenue         |
|-----------------|----------------------|
| Bikes           | 94651172.704731      |

At Scott Supermarket, the Bikes category leads revenue generation with approximately $94.65 million. I will now focus on uncovering the key factors behind this success to further enhance our performance.
  
- **Can we classify each product line as “Good” or “Bad” based on whether its sales exceed the average?**

| ProductCategory | TotalRevenue         | ProductCategoryStatus |
|-----------------|----------------------|-----------------------|
| Bikes           | 94651172.704731      | Good                  |
| Components      | 11802593.286430      | Bad                   |
| Clothing        | 2120542.524801       | Bad                   |
| Accessories     | 1272072.883926       | Bad                   |

At Scott Supermarket, only the Bikes category exceeds the average revenue and is classified as "Good." The Components, Clothing, and Accessories categories are below average, and I'll focus on strategies to boost their performance.
**Sales Analysis**  
- **How do monthly sales trends evolve over time?**
  
| SalesYear | SalesMonth | TotalSales |
|-----------|------------|------------|
| 2011      | 5          | 43         |
| 2011      | 6          | 141        |
| 2011      | 7          | 231        |
| 2011      | 8          | 250        |
| 2011      | 9          | 157        |
| 2011      | 10         | 327        |
| 2011      | 11         | 230        |
| 2011      | 12         | 228        |
| 2012      | 1          | 336        |
| 2012      | 2          | 219        |
| 2012      | 3          | 304        |
| 2012      | 4          | 269        |
| 2012      | 5          | 293        |
| 2012      | 6          | 390        |
| 2012      | 7          | 385        |
| 2012      | 8          | 285        |
| 2012      | 9          | 352        |
| 2012      | 10         | 321        |
| 2012      | 11         | 383        |
| 2012      | 12         | 378        |
| 2013      | 1          | 400        |
| 2013      | 2          | 325        |
| 2013      | 3          | 441        |
| 2013      | 4          | 428        |
| 2013      | 5          | 428        |
| 2013      | 6          | 719        |
| 2013      | 7          | 1740       |
| 2013      | 8          | 1789       |
| 2013      | 9          | 1791       |
| 2013      | 10         | 1968       |
| 2013      | 11         | 2103       |
| 2013      | 12         | 2050       |
| 2014      | 1          | 2141       |
| 2014      | 2          | 1756       |
| 2014      | 3          | 2399       |
| 2014      | 4          | 2115       |
| 2014      | 5          | 2411       |
| 2014      | 6          | 939        |

At Scott Supermarket, monthly sales orders show a steady growth trend over time—from 43 orders in May 2011 to over 2,000 orders by late 2013 and early 2014. This consistent increase indicates an expanding customer base and stronger market presence.

- **How many high-value transactions (above the average order value) occur?**

| SalesOrderID | TotalDue    | AvgOrderValue |
|--------------|------------|--------------|
| 43659       | 23153.2339  | 3915.9951    |
| 43661       | 36865.8012  | 3915.9951    |
| 43662       | 32474.9324  | 3915.9951    |
| 43664       | 27510.4109  | 3915.9951    |
| 43665       | 16158.6961  | 3915.9951    |
| 43666       | 5694.8564   | 3915.9951    |
| 43667       | 6876.3649   | 3915.9951    |
| 43668       | 40487.7233  | 3915.9951    |
| 43670       | 6893.2549   | 3915.9951    |
| 43671       | 9153.6054   | 3915.9951    |

At Scott Supermarket, several high-value transactions exceed the average order value of $3,915.99, with some reaching over $80,000. I will now analyze patterns in these transactions to identify key customer segments driving high-value sales.
 
- **What is the cumulative sales performance on weekday basis, and how does it reflect overall business growth?**
  
| Weekday  | TotalSales |
|----------|------------|
| 1        | 4444       |
| 2        | 4875       |
| 3        | 4482       |
| 4        | 4591       |
| 5        | 4346       |
| 6        | 4244       |
| 7        | 4483       |

At Scott Supermarket, sales occur consistently across all weekdays.This suggests strong online or automated order processing.

**Customer Analysis**  
- **How many unique customer segments are present in the dataset?**
  
| CustomerSegment | TotalCustomers |
|-----------------|----------------|
| Individual      | 18484          |
| Business        | 1336           |

 Scott Supermarket serves two main customer segments: *18,484 Individual* customers and *1,336 Business* customers. Individual shoppers dominate the customer base, highlighting the need for personalized promotions and loyalty programs.
 
- **Which customer segment contributes the most to sales?**
  
| CustomerSegment | TotalRevenue     |
|-----------------|------------------|
| Business        | 90775446.9931    |
| Individual      | 32441339.1228    |

Business customers generate *$90.78M* in total revenue, nearly *3 times* more than Individual customers, who contribute *$32.44M*. This suggests that Scott Supermarket should focus on strengthening B2B relationships and offering bulk purchase incentives.
    
- **Customer Type Distribution Across Regions**
  
| TerritoryID | PersonType | TotalCustomers |
|-------------|------------|----------------|
| 1           | IN         | 3341           |
| 1           | SC         | 87             |
| 2           | SC         | 49             |
| 2           | IN         | 8              |
| 3           | SC         | 61             |
| 3           | IN         | 8              |
| 4           | IN         | 4450           |
| 4           | SC         | 115            |
| 5           | SC         | 79             |
| 5           | IN         | 12             |
| 6           | IN         | 1571           |
| 6           | SC         | 106            |
| 7           | IN         | 1810           |
| 7           | SC         | 34             |
| 8           | IN         | 1780           |
| 8           | SC         | 32             |
| 9           | IN         | 3591           |
| 9           | SC         | 34             |
| 10          | IN         | 1913           |
| 10          | SC         | 38             |

The Customer Type Distribution Across Regions shows that most customers fall under the "IN" (Individual) category, with significantly fewer in the "SC" (Store/Company) category.Scott Supermarket may benefit from targeted regional strategies, such as loyalty programs for individual shoppers in high-volume territories and corporate partnerships in areas with fewer business accounts.

**Inventory Turnover Analysis**
- ** What is the total inventory available for each product category? **
  | Product Category | Total Inventory |
| --- | --- |
| Components | 47214 |
| Bikes | 15536 |
| Accessories | 9128 |
| Clothing | 5940 |

 At Scott Supermarket, Components hold the highest inventory at 47,214 units, followed by Bikes (15,536), Accessories (9,128), and Clothing (5,940). This distribution indicates a need to align inventory levels with sales trends for optimal stock management.

- ** Calculate the total number of units sold per product category **
  | Product Category | Total Units Sold |
| --- | --- |
| Bikes | 90268 |
| Clothing | 73670 |
| Accessories | 61932 |
| Components | 49044 |

At Scott Supermarket, Bikes lead with 90,268 units sold, followed by Clothing at 73,670, Accessories at 61,932, and Components at 49,044. This highlights Bikes as the top performer in sales volume.

- ** What is the inventory turnover ratio for each product category? **
| Product Category | Inventory Turnover Ratio |
| --- | --- |
| Bikes | 1128 |
| Clothing | 383 |
| Accessories | 261 |
| Components | 99 |

At Scott Supermarket, Bikes have the highest inventory turnover ratio at 1,128, followed by Clothing at 383, Accessories at 261, and Components at 99. This indicates that Bikes move quickly off the shelves, while Components may require closer inventory management to better match demand.

- ** How long does it take on average for a product to be sold after being stocked? **
 ** Table has 266 records and it's a lot to show, you can run the attached sql script **
 At Scott Supermarket, the average time to sell stocked products varies widely—from items selling almost immediately, like the Water Bottle - 30 oz., to others, such as the LL Touring Frame - Blue, 58, taking over 2,000 days to sell. This significant variation suggests a need to review slow-moving inventory and adjust stocking strategies accordingly.

- ** Are there any products with very low sales but high stock levels (overstocking issue)?**
 ** Table has 647 records and it's a lot to show, you can run the attached sql script **
 At Scott Supermarket, several items like Seat Lug, Hex Nut 7, and Spokes have extremely high stock levels yet report zero sales, indicating these products are significantly overstocked and require immediate inventory review or promotional clearance.

- Are there any products with high sales but low stock levels (risk of stockouts)?
  At Scott Supermarket, fast-selling products like AWC Logo Cap, Water Bottle - 30 oz., and Sport-100 Helmet, Blue are at risk of stockouts due to their low current inventory compared to high sales volumes. This highlights the need to prioritize these items for prompt restocking.

**Summary:**  
At Scott Supermarket, our SQL analytics reveal that operations span 10 regions with Bikes driving the highest revenue, while inventory data shows clear imbalances, some items are overstocked and others are fast-selling and at risk of stockouts.  

**Recommendation:**  
I recommend optimizing inventory management by reducing overstocked items and ensuring timely restocking of fast-moving products. Additionally, enhancing customer targeting based on regional sales trends will help drive profitability.

**Future Work:**  
Future work should focus on developing predictive models for inventory turnover and demand forecasting, as well as advanced customer segmentation techniques to further refine marketing strategies and improve overall operational efficiency.
