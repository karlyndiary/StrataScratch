Find order details made by Jill and Eva.
Consider the Jill and Eva as first names of customers.
Output the order date, details and cost along with the first name.
Order records based on the customer id in ascending order.

customers:
| Column Name  | Data Type |
|--------------|-----------|
| id           | int       |
| first_name   | varchar   |
| last_name    | varchar   |
| city         | varchar   |
| address      | varchar   |
| phone_number | varchar   |

orders:
| Column Name      | Data Type  |
|------------------|------------|
| id               | int        |
| cust_id          | int        |
| order_date       | datetime   |
| order_details    | varchar    |
| total_order_cost | int        |

```
import pandas as pd
df = pd.merge(customers, orders, left_on = 'id', right_on = 'cust_id')
df[df['first_name'].isin(['Jill', 'Eva'])][['first_name','order_date','order_details', 'total_order_cost']]
```
