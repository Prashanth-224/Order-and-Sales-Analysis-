1. Understanding the Task
You want to:
•  Analyze order status (e.g., Completed, Cancelled)
•  Analyze sales data (order_amount)
•  Identify key metrics and trends (e.g., number of orders, revenue, fulfillment rates)
2. Planning the SQL Query
Key metrics to include:
•  Total number of orders by status
•  Total sales (sum of order_amount) by status
•  Trends over time (e.g., by month)
Approach:
•  Use GROUP BY to aggregate by order status and by time period (e.g., month).
•  Use COUNT() for number of orders, SUM() for total sales.
•  Use DATE_TRUNC() or EXTRACT() to group by month if your database supports it.
________________________________________
3. SQL Queries
   
a) Orders and Sales by Status
   
SELECT
  order_status,
  COUNT(order_id) AS total_orders,
  SUM(order_amount) AS total_sales
FROM
  customer_orders
GROUP BY
  order_status
ORDER BY
  total_orders DESC;

  
b) Orders and Sales by Month and Status
   
SELECT
  DATE_TRUNC ('month', order_date) AS month,
  order_status,
  COUNT(order_id) AS total_orders,
  SUM(order_amount) AS total_sales
FROM
  customer_orders
GROUP BY
  DATE_TRUNC ('month', order_date),
  order_status
ORDER BY
  month,
  order_status;
________________________________________
