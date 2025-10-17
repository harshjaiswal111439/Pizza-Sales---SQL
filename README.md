# 🍕 Pizza Sales Analysis using SQL (SSMS)

An end-to-end SQL-based analysis project built using **SQL Server Management Studio (SSMS)** to extract business insights from pizza sales data. The project focuses on KPI calculations, sales trends, and performance evaluation using SQL queries.

---

## 📌 Short Description / Purpose

This project analyzes pizza sales data using SQL to generate key insights such as total revenue, order volume, top-performing pizzas, and category-wise performance. It supports data-driven decision-making for business optimization.

---

## 🛠️ Tech Stack

- 🗄️ SQL Server Management Studio (SSMS)  
- 🧮 Transact-SQL (T-SQL)  
- 🗂️ Relational Database Tables  
- 📝 Custom SQL Queries

---

## 📂 Data Source

The dataset includes:

- Order ID  
- Order Date & Time  
- Pizza Name  
- Pizza Category  
- Pizza Size  
- Quantity  
- Unit Price  
- Total Price / Revenue

---

## ⭐ Features / Highlights

### 🔹 Business Problem
The business needed insights into:  
- Sales by date, time, and month  
- Best and worst-selling pizzas  
- Size and category-based performance  
- Peak demand hours  
- Revenue distribution

### 🎯 Goal of the Project
To write optimized SQL queries that:  
- Calculate business KPIs  
- Analyze sales trends  
- Identify product performance  
- Compare category and size insights  
- Support reporting and strategy

---

## 📊 Key SQL Queries & Analysis

### ✅ 1. Total Revenue
```sql
SELECT SUM(total_price) AS total_revenue
FROM pizza_sales;
```

### ✅ 2. Total Orders
```sql
SELECT COUNT(DISTINCT order_id) AS total_orders
FROM pizza_sales;
```

### ✅ 3. Average Order Value
```sql
SELECT 
    SUM(total_price) / COUNT(DISTINCT order_id) AS avg_order_value
FROM pizza_sales;
```

### ✅ 4. Total Pizzas Sold
```sql
SELECT SUM(quantity) AS total_pizzas_sold
FROM pizza_sales;
```

### ✅ 5. Sales by Pizza Category
```sql
SELECT pizza_category, SUM(total_price) AS revenue
FROM pizza_sales
GROUP BY pizza_category;
```

### ✅ 6. Sales by Pizza Size
```sql
SELECT pizza_size, SUM(total_price) AS revenue
FROM pizza_sales
GROUP BY pizza_size;
```

### ✅ 7. Top 5 Best-Selling Pizzas (by Revenue)
```sql
SELECT TOP 5 pizza_name, SUM(total_price) AS revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY revenue DESC;
```

### ✅ 8. Bottom 5 Lowest-Selling Pizzas
```sql
SELECT TOP 5 pizza_name, SUM(total_price) AS revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY revenue ASC;
```

### ✅ 9. Daily Sales Trend
```sql
SELECT 
    DATENAME(WEEKDAY, order_date) AS day_name,
