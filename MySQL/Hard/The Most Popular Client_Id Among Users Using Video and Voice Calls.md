Select the most popular client_id based on a count of the number of users who have at least 50% of their events from the following list: 
'video call received', 'video call sent', 'voice call received', 'voice call sent'.

fact_events:
| Column      | Data Type |
|-------------|-----------|
| id          | int       |
| time_id     | datetime  |
| user_id     | varchar   |
| customer_id | varchar   |
| client_id   | varchar   |
| event_type  | varchar   |
| event_id    | int       |

```
with cte as (
select client_id, user_id,
(sum(case when event_type in ('video call received', 'video call sent', 'voice call received', 'voice call sent') then 1 else 0 end)
                                                 / count(event_type)) as ratio
from fact_events
group by 1, 2 ) 

select client_id
from cte
where ratio > 0.5
```
