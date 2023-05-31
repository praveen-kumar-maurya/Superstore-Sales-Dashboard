# Superstore-Sales-Dashboard

# **Dataset Link**
https://www.kaggle.com/datasets/vivek468/superstore-dataset-final

# **Dataset Information**
Row ID => Unique ID for each row,
Order ID => Unique Order ID for each Customer,
Order Date => Order Date of the product,
Ship Mode => Shipping Mode specified by the Customer,
Customer ID => Unique ID to identify each Customer,
Customer Name => Name of the Customer,
Segment => The segment where the Customer belongs,
Country => Country of residence of the Customer,
City => City of residence of of the Customer,
State => State of residence of the Customer,
Postal Code => Postal Code of every Customer,
Region => Region where the Customer belong,
Product ID => Unique ID of the Product,
Category => Category of the product ordered,
Sub-Category => Sub-Category of the product ordered,
Product Name => Name of the Product,
Sales => Sales of the Product,
Quantity => Quantity of the Product,
Profit => Profit/Loss incurred

# **Problem Statement**

**The superstore sales dashboard analysis aims to provide data-driven insights into sales and profit trends to maximize sales and profitability.**

# **Project summary**

The Superstore sales analysis utilized a dataset sourced from Kaggle. The data was initially denormalized and underwent normalization into three tables: dimCustomer, dimProducts, and factSales. Data cleaning was performed to remove irrelevant columns and correct errors in the date format for some dates in date column. A new dimDate table was created which contained all dates and then additional date-related columns were generated. A measures table was also created to consolidate all measures. Data modeling was performed to establish one-to-many relationships between the factSales table and the dimension tables, resulting in a star schema. The resulting dashboard featured various visualizations including line charts, bar charts, maps, KPI cards, ribbon charts, tables, tool tip, slicers and filters. The superstore sales dashboard analysis project aimed to provide insights into sales and profit trends across product categories, segments, and regions. The analysis revealed peak sales in March, September, and November, driven by tax season, back-to-school demand, and holiday shopping respectively. Technology had the highest sales and profits, followed by Furniture and Office Supplies. The South region had the lowest overall profit, with North Carolina being the worst-performing state. The Consumer segment had the highest sales, followed by Corporate and Home Office. Recommendations were made to maximize sales and profitability through targeted marketing initiatives, product diversification, and customer retention strategies.

# **Business Objective**

Business objective for the superstore sales dashboard is to increase sales and profitability by leveraging data-driven insights to make informed decisions. The dashboard provides a comprehensive view of sales and profit trends across product categories, segments, and regions. This information is used to identify opportunities for growth and improvement, such as cross-selling, upselling, and product diversification. The dashboard also informs marketing initiatives, loyalty programs, and customer retention strategies to drive repeat business and increase customer lifetime value. By utilizing the insights provided by the dashboard, the superstore aims to achieve sustainable growth and profitability.

# **DAX Expressions used **

DAX Expressions used for the measures created in Measures table are:- 

1. Total sales = CALCULATE(SUM(factSales[Sales]))
2. YTD Sales = TOTALYTD([Total sales],'dimDate'[Date])
3. LY YTD Sales = COALESCE(CALCULATE([YTD Sales],SAMEPERIODLASTYEAR('dimDate'[Date])),0)
4. YTD sales Growth % = CALCULATE(DIVIDE(([YTD Sales]-[LY YTD Sales]),[LY YTD Sales],0))
5. MTD Sales = TOTALMTD([Total sales],'dimDate'[Date])
6. LY MTD Sales = COALESCE(CALCULATE([MTD Sales],SAMEPERIODLASTYEAR('dimDate'[Date])),0)

YTD sales means Year till date sales
LY YTD Sales means Last Year till date sales
MTD Sales Month till date sales
LY MTD Sales Last Month till date sales


DAX Expressions used for creating columns in Date table are:- 

1. dimDate = CALENDAR(MIN(factSales[Order Date]),MAX(factSales[Order Date]))
2. Fiscal year = YEAR('dimDate'[Date])
3. FY = "FY " & RIGHT('dimDate'[Fiscal year],2) & "-" & RIGHT('dimDate'[Fiscal year]+1,2)
4. Month year = FORMAT('dimDate'[Date],"MMM-YY")
5. Start of year = STARTOFYEAR('dimDate'[Date])
6. Qtr no = QUOTIENT(DATEDIFF('dimDate'[Start of year],'dimDate'[Date],MONTH),3)+1
7. Qtr = "Q" & 'dimDate'[Qtr no]
8. Month year sort = 
   var my = DATEDIFF(dimDate[Start of year],dimDate[Date],MONTH)+1
   return
   if (my<10,dimDate[Fiscal year] & "0"& my,dimDate[Fiscal year] & my)

# **Dashboard**

![Dashboard_image](https://github.com/praveen-kumar-maurya/Superstore-Sales-Dashboard/assets/88583491/c6b2be89-b7c6-43a4-8f57-e6d586c0803d)

# **Insights**

Following are the insights obtained from the Superstore sales dashboard analysis:-

1. Sales peak in March, September, and November. March sales are driven by tax season purchases of Office Supplies and Technology. September sales increase due to back-to-school demand for Furniture, Technology, and Office Supplies. November and December sales rise as customers purchase Technology products, particularly phones, as Christmas gifts.

2. The highest sales and profits are in California, New York, Pennsylvania, Texas, and Washington. 

3. The lowest sales are in South Dakota, District of Columbia, Kansas, Maryland, and Nevada. 

4. The lowest profits are in North Carolina, Arkansas, Kansas, Oregon, and Nevada.

5. Their is zero sales for the states Montana, North Dakota, Idaho, and Wyoming.

6. Technology has the highest sales (836K) and profits (145K), followed by Furniture (742K sales, 18K profits) and Office Supplies (719K sales, 122K profits). The South region has the lowest overall profit, with North Carolina being the worst-performing state. The Consumer segment has the highest sales (1.1M), followed by Corporate (706K) and Home Office (430K).

# **Recommendations**

1. Increase marketing efforts for Office Supplies and Technology products during March to capitalize on the tax season.

2. Focus on Furniture, Technology and Office Supplies during September to target back-to-school/college sales.

3. Promote Technology products, especially phones, as Christmas gifts during November and December.

4. Focus on increasing sales and profits in states with low performance such as South Dakota, District of Columbia, Kansas, Maryland, Nevada, North Carolina, Arkansas, Oregon.

5. Increase efforts to improve profits in the South region and the Furniture category.

6. Conduct market research to understand the needs and preferences of customers in states, Montana, North Dakota, Idaho, and Wyoming. Develop a targeted marketing campaign to raise awareness of the brand and products.

7. Continuously monitor and analyse sales and profit trends by product category and segment. Identify opportunities for cross-selling, upselling, and product diversification to maximize sales and profitability, particularly in the Technology, Office supplies, and Furniture categories.

8. Explore ways to enhance the customer experience and strengthen customer loyalty across all segments, with a particular focus on the Consumer segment, which has the highest sales. Implement personalized marketing initiatives, loyalty programs, and customer retention strategies to drive repeat business and increase customer lifetime value.
