Write a query that will calculate the number of shipments per month. 
The unique key for one shipment is a combination of shipment_id and sub_id. 
Output the year_month in format YYYY-MM and the number of shipments in that month.

amazon_shipment:
| Field          | Type      |
|----------------|-----------|
| shipment_id    | int       |
| sub_id         | int       |
| weight         | int       |
| shipment_date  | datetime  |

```
select count(concat(shipment_id, sub_id)), DATE_FORMAT(shipment_date, '%Y-%m') AS ym
from amazon_shipment
group by ym
```
