You have been asked to find the 5 most lucrative products in terms of total revenue for the first half of 2022 (from January to June inclusive).
Output their IDs and the total revenue.

online_orders:
| Column Name    | Data Type  |
|----------------|------------|
| product_id     | int        |
| promotion_id   | int        |
| cost_in_dollars| int        |
| customer_id    | int        |
| date           | datetime   |
| units_sold     | int        |

```
import pandas as pd

online_orders = online_orders[(online_orders['date'].dt.month >= 1) & (online_orders['date'].dt.month <= 6)]

online_orders['total_revenue'] = online_orders['units_sold'] * online_orders['cost_in_dollars']

online_orders = online_orders.groupby('product_id')[['total_revenue']].sum('total_revenue').reset_index()

online_orders.sort_values('total_revenue', ascending = False).head()

```
