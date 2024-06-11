# CUSTOMER SALES ORDERS PORFOLIO PROJECT
# EXCEL AND SQL PROJECT
## Table of Contents
  - Objective
    - Business Problem
    - Project Objective 
- Data Source
- Stages
- Design
   - Tools
- Development
   - Pseudocode
   - Data Exploration
   - Data Cleaning
- Testing
  - Data Quality Tests
- Visualization
  - Results
-  Analysis
    - Findings
     - Validation
    - Discovery
 - Recommendations
    - Potential ROI
    -  Potential Courses of Actions 
 - Conclusion
# Objective
# Business Problem
There are several business problems we need to addresss in this project :
- The following are the problems:
1. How can we track and analyze sales performance across different product categories to identify trends and patterns?
2. What are the key factors influencing the sales volume and total revenue?
3. How can we optimize inventory levels based on sales data to avoid stockouts and overstock situations?
4. Which product categories require more attention in terms of inventory replenishment?
5. What are the purchasing behaviors and preferences of our customers based on order history and payment types?
6. How can we segment our customers to tailor marketing strategies effectively?
7. How can we predict future sales and revenue based on historical data?
8. What impact do seasonal trends and order statuses have on our sales forecasts?
9. How can we improve our order processing times and reduce delays in order fulfillment?
10. What are the common causes of order cancellations and how can we mitigate them?
# Project Objective 
- The Customer Sales Orders Data Analysis project aims to optimize sales performance, enhance inventory management, and improve customer satisfaction by analyzing sales data. It seeks to uncover trends, forecast revenue, and streamline order processing. These insights will drive strategic decisions and operational efficiency.
- Ideal Solution is:

  Creating Dashboard that will provide the  insights on Customer Sales orders Project that includes their:
  - Total Orders
  - Total Revenue
  - Total Quantity

This will help to identify trends and patterns in data and overal business .
# Data source
We need data on larger sales dataset that include their:
- Order Id
- Product Category
- Quantity
- Total Price
-  Order Date
-  Payment Type
-   Order Status

The data is sourced from Kaggle (an Excel extract),link is here https://www.kaggle.com/datasets/hassaneskikri/fictional-e-commerce-sales-data
# Stages
- Design
- Developement
- Testing
- Analysis
# Design
# Dashboard components required
The following are requirements that our dashboard will answer:
1. Top and Bottom Order Status that influence customer sales orders.
2. Top and Bottom Payment type popular widely used and their influence to customer sales orders.
3. Top and Bottom Product Categories that contributes to high income and low income growth influence in customer sales orders.
4. Distributiuon of sales over time i.e(weeky trend and monthly trend).
# Dashboard Design
Some of the data visuals that may be appropriate in answering our questions include:
- Culumn Chart
- Horizontal Bar Chart
- Donut Chart
- Area Chart
# Tools
| Tool | Purpose |        
|------------|------------|
| Excel | Exploring the data and Visualizing the data via interactive dashboards | 
| SQL Server  | Cleaning, testing, and analyzing the data    |  
| GitHub  | 	Hosting the project documentation and version control  | 
# Development
# Pseudocode
- The general approach in creating this solution from start to finish  was:
1. Get the data
2. Explore the data in Excel
3. Load the data into SQL Server
4. Clean the data with SQL
5. Test the data with SQL
6. Visualize the data in Excel
7. Generate the findings based on the insights
8. Write the documentation + commentary
9. Publish the data to GitHub Pages
# Data exploration notes
The following caught my attention so far:
1. We need atleast 7 columns for our analysis the rest of other columns are unnessesary need to be removed.
2. Their is product category column which indicates analysis of various sales distributions across different products.
3. Their is Order Id ,Total Price  And Quantity columns that we need to determine their relationships and contributions towards various products.
4. We have also Order Status And Payment Types column which will help to identify efficency of order and also preferences of customers based on the payment methods.
# Data cleaning
The aim is to refine our dataset to ensure it is structured and ready for analysis.

The cleaned data should meet the following criteria and constraints:
- Only relevant columns should be retained.
- All data types should be appropriate for the contents of each column.
- No column should contain null values, indicating complete data for all records.
- No Duplicates in Order ids should be encountered.
Steps are needed to clean and shape the data into the desired format is:
1. Removing unnecessary Columns by dropping and retaining necessary columns.
2. Adding some columns that are necessary for our analysis by performing data pre-processing.
3. Data type conversions.
# Dropping Unnecessary Columns
# SQL Query

    ALTER TABLE larger_sales_datasets

    DROP COLUMN Product_ID,

    Unit_Price,

    Customer_ID

# OUTPUT
 ![columns Drop img](https://github.com/kipngetichs/Customer-Orders/assets/169267198/7fe51e51-0dd3-4dd0-8352-70e198c1e2cf)

 - Column like Unit Price,Customer Id and Product Id were able to be removed retaining the necessesary column.

# Data Pre-Processing
# Adding Week Name Column
# SQL Query
    ALTER TABLE larger_sales_datasets

    ADD Week_Name VARCHAR(50)

    UPDATE larger_sales_datasets

    SET Week_Name=DATENAME(DW,Order_Date)

# OUTPUT

![Week Name  Alter img](https://github.com/kipngetichs/Customer-Orders/assets/169267198/c532d1f6-d303-40c1-9cce-145622723359)

- Week Name column was able to be added as well updating it with days of the week.
# Adding Month Name Column 
# SQL Query
    ALTER TABLE larger_sales_datasets

    ADD Month_Name VARCHAR(50)

    UPDATE larger_sales_datasets

    SET Month_Name=DATENAME(MONTH,Order_Date)

# OUTPUT
![Month Name Column img](https://github.com/kipngetichs/Customer-Orders/assets/169267198/3792c813-3989-4863-a297-3a2125ad7da7)

- Month Name column was able to be added and updated with month names as well.
- Week numbers and Month numbers columns was also added using the same procedure for sorting purposes.
# Data Type Conversions
# SQL Query
    ALTER TABLE larger_sales_datasets

    ALTER COLUMN Order_ID VARCHAR(50)

    ALTER TABLE larger_sales_datasets

    ALTER COLUMN Product_Category VARCHAR(50)

    ALTER TABLE larger_sales_datasets

    ALTER COLUMN Quantity SMALLINT

    ALTER TABLE larger_sales_datasets

    ALTER COLUMN Total_Price FLOAT

    ALTER TABLE larger_sales_datasets

    ALTER COLUMN Order_Date DATE

    ALTER TABLE larger_sales_datasets

    ALTER COLUMN Payment_Type VARCHAR(50)

    ALTER TABLE larger_sales_datasets

    ALTER COLUMN Order_Status VARCHAR(50)

# OUTPUT
![Date type conversions img](https://github.com/kipngetichs/Customer-Orders/assets/169267198/bd9ad1fb-f208-4da0-a887-409350b40ebe)

- All data type were converted to the relevent ones.

# Testing
- Here are the data quality tests conducted:
# Duplicate Count Check
    SELECT Order_ID,

    COUNT(*)Duplicates_Count_Check

    FROM larger_sales_datasets

    GROUP BY Order_ID

    HAVING COUNT(*)>1

# OUTPUT

![Duplicates Count Check img](https://github.com/kipngetichs/Customer-Orders/assets/169267198/f6c1352d-53d0-4f6e-a6af-e3586db44199)

- There were no dupliactes encounterd in the data meaning the data is accurate for analysis.

# Null Count Check
# SQL Query
    SELECT Order_ID,

    COUNT(*)Null_Count_Check

    FROM larger_sales_datasets

    WHERE Order_ID IS NULL

    GROUP BY Order_ID
# OUTPUT
![Null count check](https://github.com/kipngetichs/Customer-Orders/assets/169267198/ddcff2e3-33a4-4dbc-9f63-efd791bb82bb)

- There were no null values in Order Id colulmn as well as other columns i have crossed check all meaning our data is valid.

# Data Type Check
# SQL Query
    SELECT COLUMN_NAME,DATA_TYPE

    FROM INFORMATION_SCHEMA.COLUMNS

    WHERE TABLE_NAME='larger_sales_datasets'

# OUTPUT
![data Type img](https://github.com/kipngetichs/Customer-Orders/assets/169267198/a9bcc4d3-8b36-4003-968a-4f5f679a1940)

- All data types were matching the relevent columns.
# Visualization
# Results
- This is the look of the dashboard
![Sales Dashboard img](https://github.com/kipngetichs/Customer-Orders/assets/169267198/e1180041-cd4e-4f2b-b7a1-ace20e19e15d)

# Analysis
# Findings
- Here are some of the questions we need to answer for our project
1. Top  and bottom  product category by Total Orders
2. Top  Payment Types by Total Quantity
3. Top and Bottom Orders Status by Total Orders
4. Weekly Trend for Total orders
5. Monthly Trend For Total price
 
# 1. Top  and bottom  product category by Total Orders
|Rank|Product Category|Total Orders
|---------|--------|---------|
|1|Sports & Outdoors|1719K
|2|Clothing|1704K
|3|Electronics| 1665K
|4|Home & Kitchen| 1664K
|5|Books|1634K
|6|Beauty & Health|1614K
# 2. Top  Payment Types by Total Quantity
|Rank|Payment Type|Total Quantity
|---------|--------|---------|
|1|PayPal|7832K
|2|Debit Card|7640K
|3|Gift Card| 7320K
|4|Credit Card| 7305K
# 3. Top and Bottom Orders Status by Total Orders
|Rank|Order Status|Total Orders
|---------|--------|---------|
|1|Pending|2575K
|2|Cancelled|2537K
|3|Completed| 2457K
|4|Refunded| 2431K

# 4. Weekly Trend for Total orders
|Rank|Week Name|Total Orders
|---------|--------|---------|
|1|Sunday|1433K
|2|Monday|1449K
|3|Tuesday| 1486K
|4|Wednesday| 1379K
|5|Thursday|1372K
|6|Friday|1470K
|7|Saturday| 1411K
# 5. Monthly Trend For Total price
|Rank|Month Name|Total Price
|---------|--------|---------|
|1|January|$681775.81K
|2|February|$590371.60K
|3|March| $658498.00K
|4|April| $593018.86K
|5|May|$646233.03K
|6|June|$612352.99K
|7|July| $667303.41K
|8|August| $637847.23K
|9|September| $608390.98K
|10|October|$670278.96K
|11|November|$552576.79K
|12|December| $708594.32K
 # Notes
 - For this analysis, we'll prioritize analysing the metrics that are important in generating the expected ROI for our project, which are the product category,order status,payment type and times (weeks and months) with the most:
   - Total Orders
   - Total Price
   - Total Quantity
# Validation
# 1. Top  and Bottom Product Categories With Highest and Lowest Income Growth Contributions
Calculation Breakdown

Top Product category=High income growth
1. Sports & Outdoors
   - Total Orders=1719K
   - Total Price=$1313735.43K
   - Total Quantity=5190K
2. Clothing
   - Total Orders=1704K
   - Total Price=$1303679.19K
   - Total Quantity=5121K
3. Electronics
   - Total Orders=1665K
   - Total Price=$1290283.08K
   - Total Quantity=5077K
4. Home & Kitchen
   - Total Orders=1664K
   - Total Price=$1268471.94K
   - Total Quantity=5049K
5. Books
   - Total Orders=1634K
   - Total Price=$1249307.25K
   - Total Quantity=4888K
6. Beauty & Health
   - Total Orders=1614K
   - Total Price=$1201765.07K
   - Total Quantity=4772K
# SQL Query
    SELECT Product_Category,

    COUNT(Order_ID)Total_Orders,

    CAST(SUM(Total_Price) AS DECIMAL(10,2))Total_price,

    SUM(Quantity)Total_Quantity

    from larger_sales_datasets

    GROUP BY Product_Category

    ORDER BY Total_price DESC
# OUTPUT

![Top Category img](https://github.com/kipngetichs/Customer-Orders/assets/169267198/e7a6cb22-ffd2-4163-a9b7-d6f27e8a5af7)

# 2.Most and least popular Payment Types
Calculation Breakdown

Popular Payment Type=Top Widely used
1. PayPal
   - Total Orders=2573K
   - Total Price=$1968860.18K
   - Total Quantity=7832K
2. Debit Card
   - Total Orders=2529K
   - Total Price=$1936094.39K
   - Total Quantity=7640K
3. Gift Card
   - Total Orders=2445k
   - Total Price=$1864970.44K
   - Total Quantity=7320K
4. Credit Card
   - Total Orders=2453K
   - Total Price=$1857316.95K
   - Total Quantity=7305K
# SQL Query
    SELECT Payment_Type,

    COUNT(Order_ID)Total_Orders,

    CAST(SUM(Total_Price) AS DECIMAL(10,2))Total_price,

    SUM(Quantity)Total_Quantity

    FROM larger_sales_datasets

    GROUP BY Payment_Type

    ORDER BY Total_price DESC
# OUTPUT

![Top Payment type](https://github.com/kipngetichs/Customer-Orders/assets/169267198/81857182-0a59-4c8f-9d3a-e2e6c9101785)
# 3. Order Status Trend
1. Pending
   - Total Orders=2575K
   - Total Price=$1970902.18K
   - Total Quantity=7787K
2. Cancelled
   - Total Orders=2537K
   - Total Price=$1968945.61K
   - Total Quantity=7733K  
3. Completed
   - Total Orders=2457K
   - Total Price=$1846623.55K
   - Total Quantity=7304K
4. Refunded
   - Total Orders=2431K
   - Total Price=$1840770.63K
   - Total Quantity=7273K
# SQL Query
    SELECT Order_Status,

    COUNT(Order_ID)Total_Orders,

    CAST(SUM(Total_Price) AS DECIMAL(10,2))Total_price,

    SUM(Quantity)Total_Quantity

    FROM larger_sales_datasets

    GROUP BY Order_Status

    ORDER BY Total_price DESC
# OUTPUT

![Top Order status](https://github.com/kipngetichs/Customer-Orders/assets/169267198/05e20885-0a8a-4b4f-a7c0-8e2e3c84a934)
# 4. Weekly Trend Contributions to the business
Calculation Breakdown

Highest Week=High income growth

1. Sunday
   - Total Orders=1433K
   - Total Price=$1105088.89K
   - Total Quantity=4358K
2. Monday
   - Total Orders=1449K
   - Total Price=$1089617.37K
   - Total Quantity=4340K
3. Tuesday
   - Total Orders=1486K
   - Total Price=$1140649.68K
   - Total Quantity=4457K
4. Wednesday
   - Total Orders=1379K
   - Total Price=$1025331.48K
   - Total Quantity=4158K
5. Thursday
   - Total Orders=1372K
   - Total Price=$1036657.71K
   - Total Quantity=4054K
6. Friday
   - Total Orders=1470K
   - Total Price=$1156185.18K
   - Total Quantity=4466K
# SQL Query
    SELECT Week_Num,Week_Name,

    COUNT(Order_ID)Total_Orders,

    CAST(SUM(Total_Price) AS DECIMAL(10,2))Total_price,

    SUM(Quantity)Total_Quantity

    FROM larger_sales_datasets

    GROUP BY Week_Num,Week_Name

    ORDER BY Week_Num

# OUTPUT
![Weekly treng img](https://github.com/kipngetichs/Customer-Orders/assets/169267198/99a9a5fc-0f73-4296-8c71-3b8e0a8d3d64)

# 5. Monthly Trend Contribution to the business
Calculation Breakdown

Top Month=high income growth

1. January
   - Total Orders=873K
   - Total Price=$681775.81K
   - Total Quantity=2587K
2. February
   - Total Orders=795K
   - Total Price=$590371.60K
   - Total Quantity=2291K
3. March
   - Total Orders=841K
   - Total Price=$658498.00K
   - Total Quantity=2569K
4. April
   - Total Orders=810K
   - Total Price=$593018.86K
   - Total Quantity=2461K
5. May
   - Total Orders=839K
   - Total Price=$646233.03K
   - Total Quantity=2515K
6. June
   - Total Orders=840K
   - Total Price=$612352.99K
   - Total Quantity=2487K
7. July
   - Total Orders=873K
   - Total Price=$667303.41K
   - Total Quantity=2669k
8. August
   - Total Orders=851K
   - Total Price=$637847.23K
   - Total Quantity=2547K
9. September
    - Total Orders=795K
    - Total Price=$608390.98K
    - Total Quantity=2367K
10. October
    - Total Orders=868K
    - Total Price=$670278.96K
    - Total Quantity=2689K
11. November
    - Total Orders=727K
    - Total Price=$552576.79K
    - Total Quantity=2173K
12. December
    - Total Orders=888K
    - Total Price=$708594.32K
    - Total Quantity=2742K

# SQL Query
    SELECT Month_Num,Month_Name,

    COUNT(Order_ID)Total_Orders,

    CAST(SUM(Total_Price) AS DECIMAL(10,2))Total_price,

    SUM(Quantity)Total_Quantity

    FROM larger_sales_datasets

    GROUP BY Month_Num,Month_Name

    ORDER BY Month_Num
# OUTPUT 
![Monthly trend img](https://github.com/kipngetichs/Customer-Orders/assets/169267198/c16d2804-425a-4aed-81b4-c9908ccc69e9)
# Discovery
We discovered that:
1. Sports & Outdoors,Clothing,Electronics and Home & Kitchen are among product categories that contributes to high income growth to the customer sales order project than 
Books and Beauty & Health that tend to contribute lowe income growth.
2. PayPal and Debit Card are among payment types that are popular and widely used by many customers compared to Gift Card and Credit Card which few customers prefer.
3. Pending and Cancelled are among order status where high income growth contributions relay on compared to Completed and Refunded status.
4. Fridays and Tuesdays are among week days that contributes to high income growth compared to the rest ot the week that contributes to moderate consistent growth.
5. December,January and October are among the months that contributes to high income growth contributions compared to rest of the months that contributes to moderate slightly consistent growth.
# Recommendations
- Here is the recommendations based on the insights discovered
1. Prioritizing High-Growth  Product Categories: Increasing inventory, marketing and promotional efforts for Sports & Outdoors, Clothing, Electronics and Home & Kitchen. These categories should be highlighted in advertisements, sales promotions, and special offers to maximize their revenue potential.
   - Re-evaluating Low-Growth Product Categories: Assessing the market strategy for Books and Beauty & Health. Considering if these categories need better marketing, bundling with high-growth products, or if resources should be reallocated to more profitable categories.
2. Enhancing Popular Payment Methods: Streamlining the payment process for PayPal and Debit Card to ensure a smooth and efficient customer experience. Highlighting these options during checkout and in promotional materials.
   - Promoting Less Preferred Options: Implementing special incentives such as discounts or rewards for using Gift Cards and Credit Cards to increase their usage. This can help in diversifying payment method preferences and reduce dependence on just a few payment types.
3. Converting Pending and Cancelled Orders: Analyzing the reasons behind high contributions from Pending and Cancelled orders. Developing strategies to address issues leading to cancellations and delays in order completion. For instance, improving inventory accuracy, enhancimg customer service and providing timely updates on order status.
   - Enhancing Completed Orders: Focusing on reducing the time to complete orders and ensuring that the majority of orders are moved to Completed status promptly to improve cash flow and customer satisfaction.
4. Leveraging High-Growth Days: Planning major sales events, flash sales and promotions around Fridays and Tuesdays to capitalize on their higher income potential. These days should also see increased staffing and inventory levels to meet higher demand.
   - Optimizing Other Days: Implementing strategies to boost sales on other weekdays. Introducing mid-week special deals or loyalty program points on less popular days to encourage more consistent growth throughout the week.
5. Maximizing High-Growth Months: Focusing on aggressive marketing campaigns and inventory buildup for December, January and October. These months should have planned large-scale promotions, holiday sales and special events to take full advantage of the high-income growth potential.
   - Steady Growth in Other Months: Maintaining consistent marketing and engagement activities during other months to ensure steady income. Using these periods to build customer relationships, testing new marketing strategies and preparing for the peak months.
# Potential ROI
1. 10% Revenue increase due to focused marketing and inventory management for high-growth categories this will lead to an estimates growth of  $1,100,000 new monthly revenue.
2. 2% Payment Type increase by streamlining popular payment methods and promoting less preferred ones this will lead to an estimate growth of   $1,122,000 new monthly revenue.
3. 3% Order status increase by converting pending and cancelled orders to completed orders this will lead to an estimate growth of $1,155,660 new monthly revenue.
4. 2% increase by leveraging high-growth days and boosting other weekdays this will lead to an estimate of $1,178,773 new monthly revenue.
5. 3% increase by maximizing high-growth months and maintaining steady growth in other months this will lead to an estimate of $1,213,136 new monthly revenue. 
# Potential Courses of Actions
# Action plan
The following are actoins needed to be taken in order to achieve this:
1. Conducting a detailed market analysis to understand customer preferences within high-growth categories.
2. Optimizing inventory levels for high-growth categories to ensure stock availability.
3. Launching targeted marketing campaigns highlighting high-growth categories
4. Conducting A/B testing to identify the best user interface for payment options
5. Planning and execute major sales events on Fridays and Tuesdays  and Offer exclusive deals and discounts to drive traffic on these days.
6. Develop a marketing campaign calendar for December, January  and October also Planning holidays sales, special events and promotional activities.
# Conclusion
1. Focusing on high-growth product categories can significantly boost revenue.
2. Enhancing PayPal and Debit Card payment options and promoting Gift Cards and Credit Cards will improve customer satisfaction and sales.
3. Addressing issues with pending and cancelled orders will increase order completion rates.
4. Leveraging Fridays and Tuesdays for major promotions and boosting sales on other weekdays will optimize revenue.
5. Planning aggressive marketing and inventory strategies for December, January, and October will maximize seasonal sales growth.
