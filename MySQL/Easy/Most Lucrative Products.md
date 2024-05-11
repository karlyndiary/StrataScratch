You have been asked to find the 5 most lucrative products in terms of total revenue for the first half of 2022 
(from January to June inclusive).

Output their IDs and the total revenue.

online_orders:
| Field          | Type      |
|----------------|-----------|
| product_id     | int       |
| promotion_id   | int       |
| cost_in_dollars| int       |
| customer_id    | int       |
| date           | datetime  |
| units_sold     | int       |

```
select product_id, sum(units_sold * cost_in_dollars) as total_revenue
from online_orders
where month(date) between 1 and 6 and year(date) = 2022
group by product_id
order by total_revenue desc
limit 5
```
