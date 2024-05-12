Write a query that returns the number of unique users per client per month

fact_events:
| Field       | Type      |
|-------------|-----------|
| id          | int       |
| time_id     | datetime  |
| user_id     | varchar   |
| customer_id | varchar   |
| client_id   | varchar   |
| event_type  | varchar   |
| event_id    | int       |

```
select client_id, month(time_id) as month, count(distinct user_id) as users_num
from fact_events
group by client_id, month(time_id)
```
