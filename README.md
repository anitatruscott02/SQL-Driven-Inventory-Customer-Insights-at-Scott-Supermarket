## SQL-Driven-Inventory-Customer-Insights-at-Scott-Supermarket
This project leverages SQL analytics to transform Scott Supermarket's sales data into actionable insights, optimizing inventory management and enhancing customer engagement for better profitability.

## Project Overview
I have observed that Scott Supermarket is sitting on a wealth of sales and product data that isn't being effectively utilized. As a result, they often face issues like overstocking or understocking, miss opportunities to target the right customers, and overlook key trends that could boost profits. My goal is to design a smart system using SQL analytics that transforms this raw data into clear, actionable insights. This will enable Scott Supermarket to understand sales patterns, grasp customer preferences, and make data-driven decisions to optimize inventory, improve customer targeting, and enhance overall profitability.

## About Data
This project's data was obtained from the Adventure Works Sample Database and encompasses a wide range of sales transactions and product details from a manufacturing and distribution enterprise. The analysis leverages key tables including SalesOrderHeader, SalesOrderDetail, Production.Product, Production.ProductSubcategory, Production.ProductCategory, Production.ProductReview, Production.ProductInventory, and Sales.Customer. The integrated dataset captures various dimensions of the business, enabling in-depth analyses such as monthly sales trends, product category performance, order accumulation, customer behavior, and inventory turnover.
Source - https://www.kaggle.com/datasets/algorismus/adventure-works-in-excel-tables
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

- **Sales Trends Analysis:** Monthly and daily sales trends are examined to detect seasonal fluctuations and peak demand periods.  
- **Revenue Drivers Identification:** Top-performing product categories and individual items are ranked by revenue contribution.  
- **High-Value Transactions Detection:** Orders exceeding the average transaction value are highlighted to understand high-impact sales patterns.  
- **Customer Insights:** The most frequent buyers are identified to support loyalty strategies.  
- **Profitability Ranking:** Products are ranked by profitability, factoring in unit sales and margin.  
- **Inventory Turnover Analysis:** Stock movement is evaluated to align supply with demand.  
- **Product Review Integration:** Customer feedback is merged with sales data to assess satisfaction levels and guide product improvements.  

These insights provide Scott Supermarket with actionable intelligence for optimizing sales strategies, inventory management, and customer engagement.

## Business Questions

**Generic Questions**  
- How many distinct regions, territories, or cities are represented in the Adventure Works dataset?  
- In which city or territory is each store or branch located?

**Product Analysis**  
- How many distinct product categories or lines exist in the dataset?  
- Which product line is the highest seller based on revenue and volume?  
- What is the total monthly revenue generated by each product line?  
- Which month recorded the highest overall Cost of Goods Sold (COGS)?  
- Which product line contributes the most to total revenue?  
- Can we classify each product line as “Good” or “Bad” based on whether its sales exceed the average?  
- Which store or region sells more products than the average, and how does that compare across product lines?  
- What is the average customer rating for each product line?

**Sales Analysis**  
- How do monthly and daily sales trends evolve over time, and what are the peak sales periods?  
- What is the cumulative sales performance on a daily basis, and how does it reflect overall business growth?  
- How many high-value transactions (above the average order value) occur, and what can we learn from them?  
- How do sales vary by the time of day (e.g., morning, afternoon, evening) and by weekday?  
- Which customer segment or sales channel drives the highest revenue?

**Customer Analysis**  
- How many unique customer segments are present in the dataset?  
- Which customer segment contributes the most to sales, both in frequency and total revenue?  
- What is the gender distribution among customers, and how does it vary across branches or regions?  
- During which time of day and on which days of the week do customers tend to leave the highest ratings?  
- How do different customer segments respond to promotions based on their purchasing patterns and feedback?

**Inventory Turnover Analysis**
- What is the total inventory available for each product category?
- How many units of each product were sold within a specific period (e.g., monthly, yearly)?
- What is the inventory turnover ratio for each product category?
- Which products have the highest and lowest inventory turnover rates?
- How long does it take on average for a product to be sold after being stocked?
- Are there any products with very low sales but high stock levels (overstocking issue)?
- Are there any products with high sales but low stock levels (risk of stockouts)?

These questions guide the SQL analyses—ranging from monthly sales trends and product profitability to customer segmentation and behavior—providing actionable insights to refine business strategies at Scott Supermarket.

## Recommendation
**Summary of Recommendations for Scott Supermarket**

Based on my analysis, I recommend focusing on optimizing sales, inventory, and customer engagement at Scott Supermarket:

1. **Sales Optimization**: Launch promotions during peak sales periods, capitalize on high-value transactions through upselling, and enhance marketing efforts around best-selling product categories.
2. **Inventory Management**: Align stock levels with demand patterns, prepare for seasonal demand by restocking popular items, and strategically place slow-moving products to boost sales.
3. **Customer Engagement**: Refine customer segmentation and loyalty strategies, tailor promotions to customer types, and address feedback to improve customer satisfaction and retention.
4. **Operational Enhancements**: Expand investments in high-performing product lines, implement data-driven marketing campaigns, and optimize store efficiency based on sales performance.

By implementing these recommendations, Scott Supermarket can improve profitability, customer satisfaction, and overall operational efficiency.
