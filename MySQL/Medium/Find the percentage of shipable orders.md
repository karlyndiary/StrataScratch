Find the percentage of shipable orders.
Consider an order is shipable if the customer's address is known.

orders:
| Column Name      | Data Type  |
|------------------|------------|
| id               | int        |
| cust_id          | int        |
| order_date       | datetime   |
| order_details    | varchar    |
| total_order_cost | int        |

customers:
| Column Name   | Data Type |
|---------------|-----------|
| id            | int       |
| first_name    | varchar   |
| last_name     | varchar   |
| city          | varchar   |
| address       | varchar   |
| phone_number  | varchar   |

```
select count(c.address)/count(*)*100 as percent
from orders o 
join customers c 
on o.cust_id = c.id
```
