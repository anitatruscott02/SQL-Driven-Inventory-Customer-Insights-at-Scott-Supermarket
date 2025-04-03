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
