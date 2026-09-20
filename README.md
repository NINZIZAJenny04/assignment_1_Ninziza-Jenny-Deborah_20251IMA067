# assignment_1_Ninziza-Jenny-Deborah_20251IMA067
 Name: NINZIZA Jenny Deborah  ID:20251IMA067
 ## PL\SQL Assignment one- Sunrise Supermarket
 ## Database Management System i used: Oracle Database 21c
 ## Summary of what you did
I created a Sunrise Supermarket database using Oracle Database. I designed and populated four tables: customers, products, orders, and order_items, with sample data covering customers, products from multiple categories, orders, and order items across different dates.
I wrote SQL queries using **INNER JOIN, LEFT JOIN, CTEs, and window functions** to analyze customer orders, product purchases, customer spending, customer rankings, order sequences, running revenue, and the number of days between repeat orders. I also interpreted the query results from a business perspective to show how the supermarket can use the data for sales analysis, customer understanding, and decision-making.
## How to Run
Open **Oracle SQL Developer** and connect to an Oracle database.Run `schema.sql` to create the database tables.Run `data.sql` to insert the sample customers, products, orders, and order items. Run `queries.sql` to execute the JOIN, CTE, and window-function queries. Review the query results and take screenshots for the README.
## Business Scenario
Sunrise Supermarket sells different products to customers who place orders containing one or more items. The supermarket needs a database to keep track of customers, products, orders, and sales.
Management wants to use the sales data to understand customer purchasing behavior, identify customers who spend more, see which products are being purchased, and monitor how revenue changes over time. The database and SQL queries help management analyze this information and make better decisions about sales, customers, and inventory.
## Database tables
# Customers
Stores customer infomation such as customer ID ,name , email ,and city.[screenshot](https://github.com/NINZIZAJenny04/assignment_1_Ninziza-Jenny-Deborah_20251IMA067/blob/29eaf7b7db5637625ac3c03fe0cc8a89cd9e8a9a/Screenshot%202026-09-20%20121218.png)
# Order
stores customer orders and the dates on which they were placed. [sreenshot](https://github.com/NINZIZAJenny04/assignment_1_Ninziza-Jenny-Deborah_20251IMA067/blob/6511aa032c3d6bfaac831fbe97688610b7d896b9/Screenshot%202026-09-20%20121311.png)
# Products 
stores product information such as product ID, product name ,category,and price.[screenshot](https://github.com/NINZIZAJenny04/assignment_1_Ninziza-Jenny-Deborah_20251IMA067/blob/f58b75792f5babdae0850cf2e061bccbd9490958/Screenshot%202026-09-20%20130034.png)
# Order items 
stores the individual products included in each order,including the quantity.[screenshot](https://github.com/NINZIZAJenny04/assignment_1_Ninziza-Jenny-Deborah_20251IMA067/blob/9cceb257ea279109272961510c4dd5fc7671d3c7/Screenshot%202026-09-20%20121420.png)
## JOIN Queries
## Query 1:This query uses an INNER JOIN to display order information together with the customer who placed each order.
SELECT o.order_id, c.customer_name, c.city, o.order_date FROM orders o INNER JOIN customers c ON o.customer_id = c.customer_id ORDER BY o.order_date; [Screenshot](https://github.com/NINZIZAJenny04/assignment_1_Ninziza-Jenny-Deborah_20251IMA067/blob/0e9b8ea0b52f053979edac6d5ac268bba527b80a/Screenshot%202026-09-20%20131900.png)
## Query 2:
SELECT oi.order_item_id, oi.order_id, p.product_name, p.category, p.price, oi.quantity FROM order_items oi INNER JOIN products p ON oi.product_id = p.product_id ORDER BY oi.order_id; [Screenshot](https://github.com/NINZIZAJenny04/assignment_1_Ninziza-Jenny-Deborah_20251IMA067/blob/99240c8b22f61385a3bcbe46c980c8e942401cce/Screenshot%202026-09-20%20133434.png)
## Query 3:
SELECT c.customer_id, c.customer_name, c.email, c.city, o.order_id, o.order_date FROM customers c LEFT JOIN orders o ON c.customer_id = o.customer_id ORDER BY c.customer_id, o.order_date; [Screenshot](https://github.com/NINZIZAJenny04/assignment_1_Ninziza-Jenny-Deborah_20251IMA067/blob/6573ec5fc7ede0591ecbb0b1db38070208fab864/Screenshot%202026-09-20%20133056.png)
## CTE Query
WITH customer_totals AS ( SELECT c.customer_id, c.customer_name, SUM(oi.quantity * p.price) AS total_spend FROM customers c JOIN orders o ON c.customer_id = o.customer_id JOIN order_items oi ON o.order_id = oi.order_id JOIN products p ON oi.product_id = p.product_id GROUP BY c.customer_id, c.customer_name ) SELECT customer_id, customer_name, total_spend FROM customer_totals WHERE total_spend > ( SELECT AVG(total_spend) FROM customer_totals ) ORDER BY total_spend DESC; [Screenshot](https://github.com/NINZIZAJenny04/assignment_1_Ninziza-Jenny-Deborah_20251IMA067/blob/2d5060d644429e43113f3350a26b5aee6d757833/Screenshot%202026-09-20%20134032.png)
## Window-function queries
Rank customers by total amount spent, highest first
SELECT c.customer_id, c.customer_name, SUM(oi.quantity * p.price) AS total_spend, RANK() OVER ( ORDER BY SUM(oi.quantity * p.price) DESC ) AS spending_rank FROM customers c JOIN orders o ON c.customer_id = o.customer_id JOIN order_items oi ON o.order_id = oi.order_id JOIN products p ON oi.product_id = p.product_id GROUP BY c.customer_id, c.customer_name ORDER BY spending_rank; [Screenshot](https://github.com/NINZIZAJenny04/assignment_1_Ninziza-Jenny-Deborah_20251IMA067/blob/cf48b030c6ed5d38b59b361ef78647a3d49b907b/Screenshot%202026-09-20%20134327.png)
## Number each customer's orders in the order placed
SELECT c.customer_id, c.customer_name, o.order_id, o.order_date, ROW_NUMBER() OVER ( PARTITION BY c.customer_id ORDER BY o.order_date, o.order_id ) AS order_number FROM customers c JOIN orders o ON c.customer_id = o.customer_id ORDER BY c.customer_id, order_number; [Screenshot](
## Show a running total of revenue over time
SELECT o.order_date, SUM(oi.quantity * p.price) AS daily_revenue, SUM(SUM(oi.quantity * p.price)) OVER ( ORDER BY o.order_date ) AS running_revenue FROM orders o JOIN order_items oi ON o.order_id = oi.order_id JOIN products p ON oi.product_id = p.product_id GROUP BY o.order_date ORDER BY o.order_date; [Screenshot](
## Show days between the current and previous order for each customer
SELECT customer_id, customer_name, order_id, order_date, order_date - LAG(order_date) OVER ( PARTITION BY customer_id ORDER BY order_date, order_id ) AS days_between_orders FROM ( SELECT c.customer_id, c.customer_name, o.order_id, o.order_date FROM customers c JOIN orders o ON c.customer_id = o.customer_id ) ORDER BY customer_id, order_date; [Screenshot](
