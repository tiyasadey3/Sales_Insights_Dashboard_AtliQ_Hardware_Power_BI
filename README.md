# Sales_Insights_Dashboard_AtliQ_Hardware_Power_BI
Analyzed sales data of AtliQ Hardware ,created a interactive dashboard with Power BI.
![Sales Insights Dashboards](https://user-images.githubusercontent.com/73987736/236285681-3f3fcc91-8289-4a8d-8954-005443378b91.jpg)

# Problem Statement :

AtliQ Hardware is a company that supplies computer hardware and peripherals to many clients across India. The sales director is facing a lot of challenges due to the dynamic growth of the market and the lack of a simple data visualization tool to access on a daily basis. To address this, developed ETL mappings using SQL to extract the data from unstructured data and transform it to the staging area to conduct data cleaning and design star schema data models on Power BI. The dashboard was developed to perform analysis, producing quantitative visualizations in Power BI to draw valuable insights based on different parameters affecting the company performance year on year and further provide business solutions.

# Tools, Software and Libraries :
1.MySQL

2.Microsoft Power BI

3.Power Query Editor

4.DAX Language

# Data Discovery :

## AIMS Grid -
AIMS Grid is a project management tool,it has four components 

1)Purpose - (What to we want to do exactly)

2)Stackholder - (Who all will be involved)

3)End result - (after the project is over ,What do you want to achieve)

4)Success Criteria - (Cost optimization and time save)

## 1. Purpose :- 
To unlock sales insights that are not visible before for the sales them for decision support and automate them to reduced manual time spent in data gathering.

## 2. Stakeholders :-

Sales Director

Marketing Team

Customer Service Team

Data and Analytics Team

IT

## 3. End result :- 
An automated dashboard providing quick and latest sights in order to support Data driven decision making.

## 4. Success Criteria :-

Dahboard uncovering sales order insights with latest data available

Sales team able to take better decisions and prove 10% cost saving of total spend.

Sales analysis stop data gathering manually in order to save 20% business time andreinvest it value added activity.

# Data Analysis using MySQL :

Completed the Data discovery and then performed mySQL for data analysis.

This database has all sales transactions, customers, products, and market information. We will analyse this database and then hook it up with power BI

Download the sql database file in our local computer

Importing Data to MySQL workbench

![sql data import](https://user-images.githubusercontent.com/73987736/236294160-8bfed34f-14c9-47bb-8e68-1254aa78868b.png)

Performed Different SQL query on data base for analyze the database :

## 1.To find of all customers records

SELECT * FROM sales.customers;

## 2.To find total number of customers

SELECT count(*) From sales.customers;

## 3.To find transactions for Chennai market (market code for chennai is Mark001

SELECT * FROM sales.transactions where market_code='Mark001';

## 4.To find distrinct product codes that were sold in chennai

SELECT distinct product_code FROM sales.transactions where market_code='Mark001';

## 5.To find transactions for Chennai market (market code for chennai is Mark002

SELECT * FROM sales.transactions where market_code='Mark002';

## 6.To find distrinct product codes that were sold in mumbai

SELECT distinct product_code FROM sales.transactions where market_code='Mark002';

## 7.To find transactions where currency is US dollars

SELECT * from sales.transactions where currency="USD";

## 8.To find transactions in 2020 join by date table

SELECT sales.transactions.*, sales.date.* FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020;

## 9.To find total revenue in year 2020,

SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r";

## 10.To find total revenue in year 2020, January Month,

SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="January" and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");

## 11.To find total revenue in year 2020 in Chennai

SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.transactions.market_code="Mark001";

# Data Cleaning and ETL (Extract, Transform, Load):

In power BI performed ETL and data cleaning operations to make it ready so that we can build our dashboard.

Extracted Data from mySQL database to Power BI

Transformed Data Using Power Query (done currency normalization, handle invalid values, etc.)

Loaded transformed data into Power BI

# Data Modeling:

And then dataset was cleaned and transformed, it was ready to the data modeled.

The sales insights data model as show below :

![data model_sales insights](https://user-images.githubusercontent.com/73987736/236299485-cac925bb-c878-4df6-95fb-5ca6ead1ff0a.png)

# Data Analysis Using Power BI (DAX):

Measures used in all visualization are:

## Key Measures:

Profit Margin % = DIVIDE([Total Profit Margin],[Revenue],0)

Profit Margin Contribution % = DIVIDE([Total Profit Margin],CALCULATE([Total Profit Margin],ALL('sales products'),ALL('sales customers'),ALL('sales markets')))

Revenue = SUM('sales transactions'[sales_amount])

Revenue Contribution % = DIVIDE([Revenue],CALCULATE([Revenue],ALL('sales products'),ALL('sales customers'),ALL('sales markets')))

Revenue LY = CALCULATE([Revenue],SAMEPERIODLASTYEAR('sales date'[date]))

sales quntity = SUM('sales transactions'[sales_qty])

Total Profit Margin = SUM('Sales transactions'[Profit_Margin])


## Profit Targets:

Profit Target1 = GENERATESERIES(-0.05, 0.15, 0.01)

Profit Target Value = SELECTEDVALUE('Profit Target1'[Profit Target])

Target Diff = [Profit Margin %]-'Profit Target1'[Profit Target Value]

# Build Dashboard/Report:

Build a powerful dashboard in Microsoft Power BI that can help us generate sales insights on the Atliq hardware business. 

Shows reports from Sales insights :

# key Insights :

![sales insights_key](https://user-images.githubusercontent.com/73987736/236302739-208e95be-6095-4b4d-9b4d-c4959faea588.png)

# Profit Analysis: 

![sales insights_1st page](https://user-images.githubusercontent.com/73987736/236303016-a83c4d9e-996e-4253-937f-670580ae59fa.png)

# Performence Insights(2020):

![sales insights_performence](https://user-images.githubusercontent.com/73987736/236303303-5d9bbad8-3d49-4253-91e0-4ede0177ae40.png)

# AtliQ Hardware Sales Insights Report/Dashboard Mobile View :

![sales insight mobile view](https://user-images.githubusercontent.com/73987736/236308272-4ee90e55-a4e9-41e9-8224-f47c1481fa0a.png)


# References :

Codebasics Youtube channel : https://youtu.be/hhZ62IlTxYs





