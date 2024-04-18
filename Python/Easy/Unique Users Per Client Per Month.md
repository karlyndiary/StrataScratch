Write a query that returns the number of unique users per client per month

fact_events:
| Column Name | Data Type  |
|-------------|------------|
| id          | int        |
| time_id     | datetime   |
| user_id     | varchar    |
| customer_id | varchar    |
| client_id   | varchar    |
| event_type  | varchar    |
| event_id    | int        |

```
import pandas as pd
fact_events['month'] = fact_events['time_id'].dt.month
fact_events.groupby(['month','client_id'])['user_id'].nunique().reset_index()
```
