# Online-Marketplace-Sales-Analysis
Designed and implemented a database for an online marketplace to analyze customers, products, orders, and seller performance. Performed revenue calculation, monthly sales trend analysis, top-selling products identification, seller-wise revenue comparison, and customer spending insights using SQL queries.
🛒 Online Marketplace Sales Analysis – SQL Mini Project

A SQL-based analytical project designed to understand business performance of an online marketplace. The system stores and analyzes customer behavior, product details, seller contribution, and revenue insights using SQL queries.

📁 Project Overview

This project demonstrates how SQL can be used to manage and analyze e-commerce data.
It includes tables for customers, sellers, products, orders, and order items, followed by analytical queries to extract meaningful insights.

Key Outcomes:

✔ Total revenue generated
✔ Monthly sales trends
✔ Top-selling products
✔ Seller-wise revenue comparison
✔ Customer spending analysis

🏗 Database Schema
Table Name	Description
customers	Customer details & signup date
sellers	Marketplace seller information
products	Product price & seller mapping
orders	Order details with date & customer
order_items	Ordered product-level details
🔧 Technologies Used

SQL

Joins & Foreign Keys

Aggregate Functions (SUM, COUNT)

GROUP BY & ORDER BY queries

Date Formatting for Monthly Analysis

📊 Business Queries Included
-- 1. Total Revenue
SELECT SUM(p.price * oi.quantity) AS total_revenue
FROM order_items oi
JOIN products p ON oi.product_id = p.product_id;

-- 2. Monthly Sales Trend
SELECT DATE_FORMAT(o.order_date, '%Y-%m') AS month,
SUM(p.price * oi.quantity) AS monthly_sales
FROM orders o
JOIN order_items oi ON o.order_id = oi.order_id
JOIN products p ON oi.product_id = p.product_id
GROUP BY month ORDER BY month;

-- 3. Top Selling Products
SELECT p.product_name, SUM(oi.quantity) AS total_units_sold
FROM order_items oi JOIN products p ON oi.product_id = p.product_id
GROUP BY p.product_name ORDER BY total_units_sold DESC;


