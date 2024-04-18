Write a query that will calculate the number of shipments per month. The unique key for one shipment is a combination of shipment_id and sub_id. 
Output the year_month in format YYYY-MM and the number of shipments in that month.

amazon_shipment:
| Column Name    | Data Type  |
|----------------|------------|
| shipment_id    | int        |
| sub_id         | int        |
| weight         | int        |
| shipment_date  | datetime   |

```
import pandas as pd
amazon_shipment['year_month'] = amazon_shipment['shipment_date'].dt.strftime('%Y-%m')
amazon_shipment.groupby('year_month')['shipment_id'].count().reset_index()
```
