Find the customer with the highest daily total order cost between 2019-02-01 to 2019-05-01. If customer had more than one order on a certain day, 
sum the order costs on daily basis. Output customer's first name, total cost of their items, and the date.

For simplicity, you can assume that every first name in the dataset is unique.

customers:
| Column Name   | Data Type |
|---------------|-----------|
| id            | int       |
| first_name    | varchar   |
| last_name     | varchar   |
| city          | varchar   |
| address       | varchar   |
| phone_number  | varchar   |

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
df = pd.merge(customers, orders, left_on = 'id', right_on = 'cust_id', how = 'left')
datedf = df[(df['order_date'].dt.month >= 2) & (df['order_date'].dt.month <= 5)]
df1 = datedf.groupby(['first_name','order_date'], as_index = False)['total_order_cost'].sum().reset_index()
df2 = df1.sort_values(by = 'total_order_cost', ascending = False).head(1)
df2.rename(columns = {'total_order_cost':'max_cost'})[['first_name','order_date','max_cost']]
```
