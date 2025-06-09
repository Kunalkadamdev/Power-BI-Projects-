
# 🏠 Housing Data Analysis Report- Power BI Dashboard

📌 Problem Statement

To analyze housing data using Google BigQuery and visualize key market trends using Power BI, including purchase behavior, pricing trends, regional performance, and other real estate metrics.

🔑Key Learnings

Google Cloud BigQuery: Uploading datasets, running complex SQL queries, data transformations.

SQL Queries: UPDATE, GROUP BY, WHERE, CREATE TABLE operations.

Power BI Visualizations: Bar charts, line charts, scatter plots, key influencer visual, stacked column charts, clustered bar charts, slicers.

Data Transformation: Using both Power BI’s Power Query Editor and SQL.

Data Modeling: Structuring and organizing the data model for reporting.

DAX Calculations: Measures and calculated columns for performance analytics.




🛠️ Tools Used:

Data Source > Google Cloud BigQuery (100K+ Housing Records).

Google Cloud Platform, BigQuery, Power BI, SQL, DAX




🧾 Steps Followed 🧠 Advanced Calculations


-Step 1 : Data Setup:

Created a Google Cloud account and uploaded the housing CSV data.

The data auto-generated a table in BigQuery for querying.

-Step 2 : Power BI Connection:

Opened Power BI and connected to BigQuery using credentials.

Selected Import Mode to load a local copy of the dataset into Power BI for optimized performance.

-Step 3 : BigQuery Data Prep:

Created a copy of the main table to perform SQL operations for better analysis.

-Step 4 :Power Query Editor Cleanup:

Performed data cleaning and transformation: removing nulls, handling redundancies, and fixing format issues.

-Step 5 : DAX Calculations and Visuals:

5.1 Year-over-Year (YoY) Sales Growth – Line Chart

YOY_Sales_Growth =  
VAR curYear = YEAR(MAX('Housing Data'[date]))
VAR curYearSales = 
    CALCULATE(
        SUM('Housing Data'[purchase_price]),
        YEAR('Housing Data'[date]) = curYear
    )
VAR prevYearSales = 
    CALCULATE(
        SUM('Housing Data'[purchase_price]),
        YEAR('Housing Data'[date]) = curYear - 1
    )
RETURN 
    IF(prevYearSales <> 0, (curYearSales - prevYearSales) / prevYearSales, BLANK())


5.2 Offer Price – Calculated Column

Offer price = (100 * 'Housing Data'[purchase_price]) / (100 - 'Housing Data'[%_change_between_offer_and_purchase])

5.3 Offer Price vs Purchase Price – Scatter Plot
5.4 Median Sales Price Change by Region – Bar Chart

Median sales price change =  
VAR curMedian =  
    MEDIANX(FILTER('Housing Data', YEAR('Housing Data'[date]) = YEAR(MAX('Housing Data'[date]))), 'Housing Data'[purchase_price])  
VAR prevMedian =  
    MEDIANX(FILTER('Housing Data', YEAR('Housing Data'[date]) = YEAR(MAX('Housing Data'[date])) - 1), 'Housing Data'[purchase_price])  
RETURN  
    IF(prevMedian <> 0, (curMedian - prevMedian) / prevMedian, BLANK())


5.5 Units Sold in Latest Quarter – Card Visual

Units Sold Current Qtr =  
VAR MaxDate = MAX('Housing Data'[date])  
RETURN  
    CALCULATE(  
        DISTINCTCOUNT('Housing Data'[house_id]),  
        YEAR('Housing Data'[date]) = YEAR(MaxDate),  
        QUARTER('Housing Data'[date]) = QUARTER(MaxDate)  
    )

5.6 Last 12 Months Sales – Card Visual

Last 12 Month Sales = 
CALCULATE(
    SUM('Housing Data'[purchase_price]),
    DATESINPERIOD('Housing Data'[date], MAX('Housing Data'[date]), -12, MONTH)
)


5.7 Total YTD Sales – Table Visual

Total YTD Sales = TOTALYTD(SUM('Housing Data'[purchase_price]), 'Housing Data'[date])


5.8 Average Price Per Square Meter by Region – Donut Chart

Average price sq mtr = AVERAGE('Housing Data'[sqm_price])


5.9 House Age – Calculated Column

Age = ABS(YEAR('Housing Data'[date]) - 'Housing Data'[year_build])


5.10 Key Influencer Visual – Age-Based House Buying Analysis
5.11 Offer Price to Sqm Ratio – DAX Measure

offer to sqm ratio = DIVIDE(SUM('Housing Data'[Offer price]), SUM('Housing Data'[sqm]))


-Step 6 : House Type Analysis Page:

Stacked Column Chart: Comparison between offer price and purchase price across different house types.

Clustered Bar Chart: Shows average interest rate, inflation, and yield on mortgage credit bonds.

-Step 7 : Line & Stacked Column Chart: For average area (sqm) and average price per square meter.

-Step 8 : Filters & Slicers Added:

Filters include: Area, City, House Type, Region.

Searchable slicers enhance interactivity and user navigation.






📸 Snapshots

Data Source: Housing market analysis

![Image](https://github.com/user-attachments/assets/4bef578e-4b61-4356-8800-597de9fa03fa)

Data Source: Housing Sales analysis

![Image](https://github.com/user-attachments/assets/adb1b1fa-fe4c-4b74-b3f9-e926789baedc)


Data Source: Housing price analysis

![Image](https://github.com/user-attachments/assets/758aa50e-9e0d-4472-9bc1-b4d12ba55efe)





📊 Data Dictionary

| Column Name                           | Description                                              |
| ------------------------------------- | -------------------------------------------------------- |
| `date`                                | Date of transaction.                                     |
| `quarter`                             | Fiscal quarter of the year (Q1–Q4).                      |
| `house_id`                            | Unique house identifier.                                 |
| `house_type`                          | Type of house (detached, apartment, etc.).               |
| `sales_type`                          | Sale classification (new vs. resale).                    |
| `year_build`                          | Year the house was built.                                |
| `purchase_price`                      | Final transaction value of the property.                 |
| `%_change_between_offer_and_purchase` | Price difference between initial offer and purchase.     |
| `no_rooms`                            | Number of rooms.                                         |
| `sqm`                                 | Area of the house in square meters.                      |
| `sqm_price`                           | Price per square meter.                                  |
| `address`                             | Full address of the property.                            |
| `zip_code`                            | Postal code.                                             |
| `city`                                | Urban city or municipality name.                         |
| `area`                                | Neighborhood/district within the city.                   |
| `region`                              | Administrative region (e.g., Capital Region of Denmark). |
| `nom_interest_rate%`                  | Nominal interest rate on mortgage.                       |
| `dk_ann_infl_rate%`                   | Denmark's annual inflation rate.                         |
| `yield_on_mortgage_credit_bonds%`     | Return on mortgage credit bonds.                         |



