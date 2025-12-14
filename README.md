🚲 Jenkins BikeStores SQL Analysis Project

 📌 Project Overview
The Jenkins BikeStores Project is a SQL-based data analysis project performed on the BikeStores sample database.
The objective of this project is to analyze sales performance, customer behavior, product trends, and staff efficiency
using advanced SQL queries.

This project demonstrates:
- Advanced SQL querying
- Joins and subqueries
- Window functions
- Aggregations and grouping
- EXISTS and HAVING clauses
- Real-world business problem solving

---

 🗂️ Database Used
BikeStores Sample Database (MySQL)

 Tables
- stores
- categories
- brands
- products
- customers
- staffs
- orders
- order_items
- stocks

---

 🛠️ Tools & Technologies
- MySQL 8.0
- MySQL Workbench
- SQL
- GitHub

---

🎯 Project Objectives
This project answers the following business questions:

1. Find the total number of products sold by each store along with the store name.
2. Calculate the cumulative sum of quantities sold for each product over time.
3. Find the product with the highest total sales (quantity × price) for each category.
4. Find the customer who spent the most money on orders.
5. Find the highest-priced product for each category name.
6. Find the total number of orders placed by each customer per store.
7. Find the names of staff members who have not made any sales.
8. Find the top 3 most sold products in terms of quantity.
9. Find the median value of the price list.
10. List all products that have never been ordered (using EXISTS).
11. List the names of staff members who have made more sales than the average number of sales by all staff members.
12. Identify the customers who have ordered all types of products (from every category).

---

 🧠 Sample SQL Query (Median Price)
```sql
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

Some stores significantly outperform others in total product sales.

A small number of products generate the majority of revenue.

Certain staff members have not made any sales, highlighting performance gaps.

Median price analysis helps understand overall product pricing strategy.

Loyal customers tend to purchase products from all categories.

🚀 How to Run the Project

Clone the repository

Run the following SQL files in order:

create objects.sql

load data.sql

Execute the analysis queries using MySQL Workbench

📌 Future Enhancements

Build a Power BI or Tableau dashboard

Optimize queries using indexes

Add stored procedures

Perform predictive sales analysis

👤 Author

Sanyam Sharma
Aspiring Data Analyst
Skills: SQL | Python | Power BI | Advanced Excel | AI/ML
