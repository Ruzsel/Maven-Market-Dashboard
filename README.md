# Maven-Market-Dashboard
In this project, I have taken a series of critical steps in developing the Power BI dashboard
# About this project
Maven Market Sales Performance Analysis
The project explores the sales performance analysis of "Maven Market". The primary objective of this project is to gain insights into the overall topline performance of "Maven Market", understand the performance of individual stores, customer characteristics.

### Objectives:
- Overall Sales Performance: Analyze the overall sales performance of "Maven Market" to understand its position in the market and identify areas for improvement.

- Store-specific Performance: Evaluate the performance of each store within the Maven Market chain to identify top-performing locations and areas that require optimization.

- Customer Profiling: Utilize customer data to create detailed profiles, including demographics, purchasing behavior, and preferences, to better understand and target Maven Market's customer base.

### Key Insights:
- Topline Performance Trends: Identify trends and patterns in overall sales data to understand Maven Market's performance over time.

- Store Comparison: Compare sales metrics, such as revenue, profit, and product return, across different Maven Market locations also each store detail.

- Customer Segmentation: Segment Maven Market's customer base based on various criteria, such as transaction, member type, and showing top 100 customers by transaction.

### Methodology:
The analysis will involve connecting and processing sales data from various Maven Market stores, creating data models to facilitate analysis, and utilizing advanced analytics techniques to derive actionable insights. The project will leverage tools such as Power BI for data visualization and statistical analysis.

### Expected Outcomes:
By the end of the project, we aim to provide Maven Market Dashboard to optimize sales performance, enhance customer satisfaction, and drive overall business growth.

### Table of Contents
- [Connecting and Shaping the data](#connecting--shaping-the-data)
- [Creating Data Model](#creating-the-data-model)
- [Adding DAX measures](#adding-dax-measures)
- [Building Report](#building-the-report)
- [Interactive Dashboard](#interactive-dashboard)

# Connecting & Shaping the Data
Create and shaping :
- [Customers Table](#customers-table)
- [Products Table](#products-table)
- [Stores Table](#stores-table)
- [Regions Table](#regions-table)
- [Calendar Table](#calendar-table)
- [Return_data Table](#return_data-table)
- [Transaction_data Table](#transaction_data-table)

### Customers Table
- Name the table "Customers", and make sure that headers have been promoted
- Confirm that data types are accurate (Note: "customer_id" should be whole numbers, and both "customer_acct_num" and "customer_postal_code" should be text)
- Add a new column named "full_name" to merge the the "first_name" and "last_name" columns, separated by a space
- Create a new column named "birth_year" to extract the year from the "birthdate" column, and format as text
- Create a conditional column named "has_children" which equals "N" if "total_children" = 0, otherwise "Y"
![Load MavenMarket_Customers](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/f8798f97-4fd3-4f7d-8290-c0ba2a1d09ab)
![Customer_id, acct name, postal data type change](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/a2a4ca35-7b11-4e5a-b18a-c74ef91bf327)
![Create full_name Column](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/d05885ee-7d5d-41fd-9a70-67a57b05da15)
![full_name](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/72cd06a6-439e-4639-baa0-f35f06669841)
![Create birth_year Column](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/29599955-ccaa-4d18-8196-09cd582527b0)
![birth_year](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/56073a34-8155-46d0-adc7-424620232315)
![has_children](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/92ae5105-851f-4096-8e0b-fff297ab8ade)
![has_children finish](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/f31a604b-b3b0-47a8-ac68-6d376a7e2a29)

### Products Table
- Name the table "Products" and make sure that headers have been promoted
- Confirm that data types are accurate (Note: "product_id" should be whole numbers, "product_sku" should be text), "product_retail_price" and "product_cost" should be decimal numbers)
- Add a calculated column named "discount_price", equal to 90% of the original retail price Format as a fixed decimal number, and then use the rounding tool to round to 2 digits
- Replace "null" values with zeros in both the "recyclable" and "low-fat" columns
![Extract MavenProducts csv](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/3a7d2692-9ac8-4c31-b23c-c27c1465cc61)
![Create discount_price Column](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/8018ab62-886c-4c4f-99a5-cdb613a277f3)
![discount_price](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/a2c51394-9439-4919-a97a-58a16069b980)
![recyclable](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/d0101c90-d67c-4f34-9fdb-413496f92cb1)
![low_fat](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/d2b59dad-9e5e-41c6-95a8-81187be52f35)
![recyclable and low_fat](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/cf2a83c2-0dbe-4217-a6e9-63d46dfb2633)

### Stores Table
- Name the table "Stores" and make sure that headers have been promoted
- Confirm that data types are accurate (Note: "store_id" and "region_id" should be whole numbers)
- Add a calculated column named "full_address", by merging "store_city", "store_state", and "store_country", separated by a comma and space (hint: use a custom separator)
- Add a calculated column named "area_code", by extracting the characters before the dash ("-") in the "store_phone" field
![Exctract MavenMarketStore](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/d58f53a5-c99d-4f80-8e57-006185623d1a)
![store_id region id whole number](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/00471fbf-3a00-4375-8c5d-f2d06106c652)
![add full_address column](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/e7b5907c-906f-4a9d-8771-3b5883bb9909)
![full_address column](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/0258af18-9f03-4b8b-a40b-7e863fbfb1a5)
![Create area_code](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/acc3ad54-de94-47bc-b833-36f5addd03cf)
![area_code](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/598a21f8-203a-49ce-a28f-0676d26f2f24)

### Regions Table
- Name the table "Regions" and make sure that headers have been promoted
- Confirm that data types are accurate (Note: "region_id" should be whole numbers)
![Extract MavenRegions](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/881878ee-cc8a-46ca-b5e3-daf3c0ed520b)
![Regions ](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/261c8b8e-a105-46f3-b3bf-5e04cfaec12c)

### Calendar Table
- Name the table "Calendar" and make sure that headers have been promoted
- Use the date tools in the query editor to add the following columns:
Start of Week (starting Sunday), Name of Day, Start of Month, Name of Month, Quarter of Year, Year
![MavenCalender](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/d0d1b667-30e2-472b-a35f-450b25660406)
![Calender add column complete](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/a06f5a9e-7dc6-4bf5-8f2f-9909ef4d0cb1)

### Return_data Table
- Name the table "Return_Data" and make sure that headers have been promoted
- Confirm that data types are accurate (all ID columns and quantity should be whole numbers)
![Extract MavenReturns](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/7e5d0870-fcb8-4cf9-bcb7-9969a2a39689)
![return_data](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/1a9f5d85-67a3-4aa0-ad84-2093c14a300a)

### Transaction_data Table
- Add a new folder named "MavenMarket Transactions", containing both the "MavenMarket_Transactions_1997" and "MavenMarket_Transactions_1998" csv files
- Connect to the folder path
- combine the files, then remove the "Source.Name" column
- Name the table "Transaction_data", and confirm that headers have been promoted
- Confirm that data types are accurate (all ID columns and quantity should be whole numbers)
![Create Mavenmarket_transaction](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/be2b22a3-d782-4224-bb37-8e67ab64f68a)
![Exctract MavenTransactions](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/7894896a-ed2d-42be-8907-7a4a194dc081)
![Combine maventransactions file](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/0d35632b-baf3-423e-870b-ce5c3ea23b47)
![pra delete source name](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/f51ea6d0-0dc7-4306-8571-ba721b4534fd)
![post source name](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/fa291896-6aba-4646-9a0c-34ec33268c10)

With the exception of the two data tables("return_data", "transaction_data", disabling "Include in Report Refresh"
Connecting & Shaping the Data Finish

# Creating the Data Model
1. In the MODEL view, arrange tables with the lookup tables above the data tables

- Connect Transaction_Data to Customers, Products, and Stores using valid primary/foreign keys 
- Connect Transaction_Data to Calendar using both date fields, with an inactive "stock_date" relationship
- Connect Return_Data to Products, Calendar, and Stores using valid primary/foreign keys
- Connect Stores to Regions as a "snowflake" schema

2. Confirm the following:

- All relationships follow one-to-many cardinality, with primary keys (1) on the lookup side and foreign keys (*) on the data side
- Filters are all one-way (no two-way filters)
- Filter context flows "downstream" from lookup tables to data tables
- Data tables are connected via shared lookup tables (not directly to each other)

3. Hide all foreign keys in both data tables from Report View, as well as "region_id" from the Stores table

4. In the DATA view:

- Update all date fields (across all tables) to the "M/d/yyyy" format using the formatting tools in the Modeling tab
- Update "product_retail_price", "product_cost", and "discount_price" to Currency ($ English) format
- In the Customers table, categorize "customer_city" as City, "customer_postal_code" as Postal Code, and "customer_country" as Country/Region
- In the Stores table, categorize "store_city" as City, "store_state" as State or Province, "store_country" as Country/Region, and "full_address" as Address

![Creating Data Model Fix](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/5de3b2f1-d47f-435f-b91e-4b967393e3ac)

# Adding DAX Measures
Please Feel Free to check all DAX that i had been create in this power bi file but, in developing the dashboard I will only display the DAX measures used in my dashboard report because if I were to display all the DAX measures, this section would become very long. Here are some of the DAX measures I used in my dashboard:

```DAX
Last Month Transactions = CALCULATE([Total Transactions], PREVIOUSMONTH('Calendar'[date]))
```
```DAX
Total Transactions = COUNTROWS(Transaction_data)
```
```DAX
Last Month Profit = CALCULATE([Total Profit], PREVIOUSMONTH('Calendar'[date]))
```
```DAX
Total Profit = [Total Revenue] - [Total Cost]
```
```DAX
Last Month Returns = CALCULATE([Total Returns], PREVIOUSMONTH('Calendar'[date]))
```
```DAX
Total Returns = COUNTROWS(Return_data)
```
```DAX
Total Revenue = 
    SUMX(
        Transaction_Data,
        Transaction_Data[quantity] * RELATED(Products[product_retail_price])
    )
```
```DAX
Total Cost = 
    SUMX(
        Transaction_Data,
        Transaction_Data[quantity] * RELATED(Products[product_cost])
    )
```
```DAX
Return Rate = DIVIDE([Quantity Returned], [Quantity Sold], 0)
```
```DAX
Profit Margin = DIVIDE([Total Profit], [Total Revenue], 0)
```
```DAX
Average Transaction per Customer = 
DIVIDE(
    [Total Transactions], 
    [Total Customers]
)
```
```DAX
Average Revenue per Customer = 
DIVIDE(
    [Total Revenue], 
    [Total Customers]
)
```
```DAX
Total Customers = 
DISTINCTCOUNT(
    'Customers'[customer_id]
)
```

# Building the Report
![Topline Dash](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/d3da7446-8e2d-49cc-8140-77240cdb28de)
![Store Dash](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/7b3dd709-be17-4484-9a1c-88c35f3ca36c)
![Customer dash](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/f36ccce7-14ba-4b90-87d0-85d80937ed56)

# Interactive Dashboard
[Power Bi Link](https://app.powerbi.com/view?r=eyJrIjoiMjU1MmIyOGMtMzE3Yy00MzE3LTg3YTgtYjcxMzFjMmQ0MWRkIiwidCI6IjUwODkxNmEwLTdiODktNDNhMS1hZjRlLTcyZmUxNWFiYTViOSIsImMiOjEwfQ%3D%3D)
