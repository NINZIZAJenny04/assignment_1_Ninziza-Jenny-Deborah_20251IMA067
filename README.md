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
Stores customer infomation such as customer ID ,name , email ,and city.
