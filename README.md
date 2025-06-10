# lab-task-6
TASK 6: Sales Trend Analysis Using Aggregations
objective:
To analyze monthly revenue and order volume using SQL aggregation functions.

Step-by-Step Implementation (MySQL)
Step 1: Create a Database
Create a new database to store the sales data.

sql
Copy
Edit
CREATE DATABASE IF NOT EXISTS sales_db;
Step 2: Use the Database
Select the newly created database.

sql
Copy
Edit
USE sales_db;
Step 3: Create the orders Table
This table will store individual sales records.

sql
Copy
Edit
CREATE TABLE IF NOT EXISTS orders (
    order_id INT,
    order_date DATE,
    amount DECIMAL(10, 2),
    product_id INT
);
Step 4: Insert Sample Data
Populate the table with mock data for testing and analysis.

sql
Copy
Edit
INSERT INTO orders (order_id, order_date, amount, product_id) VALUES
(1, '2024-01-15', 120.50, 101),
(2, '2024-01-20', 80.00, 102),
(3, '2024-02-10', 150.00, 103),
(4, '2024-02-18', 90.00, 101),
(5, '2024-03-05', 200.00, 104),
(6, '2024-03-10', 50.00, 105),
(7, '2024-03-25', 75.50, 106),
(8, '2024-04-01', 300.00, 107),
(9, '2024-04-12', 110.00, 108),
(10, '2024-05-09', 500.00, 109);
Step 5: Run Sales Trend Analysis Query
Use aggregation to calculate monthly revenue and order volume.

sql
Copy
Edit
SELECT 
    YEAR(order_date) AS year,
    MONTH(order_date) AS month,
    SUM(amount) AS total_revenue,
    COUNT(DISTINCT order_id) AS order_volume
FROM 
    orders
GROUP BY 
    YEAR(order_date), MONTH(order_date)
ORDER BY 
    year, month;
Expected Output:
year	month	total_revenue	order_volume
2024	1	200.50	2
2024	2	240.00	2
2024	3	325.50	3
2024	4	410.00	2
2024	5	500.00	1

Outcome:
This task helps you learn how to:

Use aggregation functions (SUM, COUNT)

Extract date components (YEAR(), MONTH())

Group and sort data for trend analysis
