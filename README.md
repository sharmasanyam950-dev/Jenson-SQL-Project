🚲 Jenkins BikeStores SQL Analysis Project
📌 Project Overview

The Jenkins BikeStores Project is a SQL-based data analysis project performed on the BikeStores sample database.
The goal of this project is to analyze sales, customers, products, staff performance, and pricing trends using advanced SQL queries.

This project demonstrates:

Strong understanding of SQL joins

Use of window functions

Aggregations & subqueries

EXISTS, GROUP BY, HAVING

Real-world business problem solving

🗂️ Database Used

BikeStores Sample Database (MySQL)

Schemas & Tables:

stores

categories

brands

products

customers

staffs

orders

order_items

stocks

🛠️ Tools & Technologies

MySQL 8.0

MySQL Workbench

SQL (Advanced Queries)

GitHub

🎯 Objectives

The project answers 12 real-world business questions, such as:

Store-wise sales performance

Best-selling products

Customer spending behavior

Staff sales performance

Product pricing analysis

📊 SQL Questions Solved
1️⃣ Total products sold by each store

Identifies how many items each store sold in total.

2️⃣ Cumulative quantity sold per product over time

Tracks product demand trends using window functions.

3️⃣ Highest revenue-generating product in each category

Finds the most profitable product per category.

4️⃣ Customer who spent the most money

Identifies the top customer based on total purchase value.

5️⃣ Highest-priced product per category

Helps understand premium products in each category.

6️⃣ Orders placed by each customer per store

Analyzes customer engagement across stores.

7️⃣ Staff members with no sales

Detects inactive or non-performing staff.

8️⃣ Top 3 most sold products by quantity

Highlights best-selling products.

9️⃣ Median value of the product price list

Calculates median product price using window functions.

🔟 Products that were never ordered (EXISTS)

Identifies dead stock or unpopular products.

1️⃣1️⃣ Staff with sales above average

Evaluates staff performance against the team average.

1️⃣2️⃣ Customers who ordered from every category

Finds loyal and diverse customers.

🧠 Sample Query (Median Price – Question 9)
WITH temp AS (
  SELECT 
      list_price,
      ROW_NUMBER() OVER (ORDER BY list_price) AS rn,
      COUNT(*) OVER () AS cn
  FROM products
)
SELECT 
  CASE
    WHEN MOD(cn, 2) = 1 THEN
      MAX(CASE WHEN rn = (cn + 1) / 2 THEN list_price END)
    ELSE
      ROUND(AVG(CASE WHEN rn IN (cn / 2, cn / 2 + 1) THEN list_price END), 2)
  END AS median_price
FROM temp;

📈 Key Insights

Certain stores significantly outperform others in product sales.

A small number of products generate the majority of revenue.

Some staff members have zero sales, indicating training or allocation issues.

Median pricing helps understand overall product affordability.

Loyal customers often purchase across multiple categories.

🚀 How to Run This Project

Clone the repository

Execute:

create objects.sql

load data.sql

Run the analysis queries in MySQL Workbench

View results in tabular format

📌 Future Improvements

Create Power BI / Tableau dashboard

Add indexes for performance optimization

Convert queries into stored procedures

Add sales forecasting analysis

👤 Author

Sanyam Sharma
📊 Aspiring Data Analyst
💻 Skills: SQL | Python | Power BI | Advanced Excel | AI/ML
