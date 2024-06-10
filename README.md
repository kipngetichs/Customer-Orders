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












