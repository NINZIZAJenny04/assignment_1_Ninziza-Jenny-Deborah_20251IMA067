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
