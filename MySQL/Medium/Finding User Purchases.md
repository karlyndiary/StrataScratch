Write a query that'll identify returning active users. 
A returning active user is a user that has made a second purchase within 7 days of any other of their purchases. 
Output a list of user_ids of these returning active users.

amazon_transactions:
| Field      | Type      |
|------------|-----------|
| id         | int       |
| user_id    | int       |
| item       | varchar   |
| created_at | datetime  |
| revenue    | int       |

```
select distinct a1.user_id
from amazon_transactions a1
join amazon_transactions b1
on a1.user_id = b1.user_id and a1.id <> b1.id
where datediff(b1.created_at, a1.created_at) between 0 and 7
order by a1.user_id
```
