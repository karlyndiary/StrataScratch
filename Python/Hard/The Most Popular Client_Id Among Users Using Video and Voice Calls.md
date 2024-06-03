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

```
