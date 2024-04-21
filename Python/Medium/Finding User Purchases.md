Write a query that'll identify returning active users. A returning active user is a user that has made a second purchase within 7 days of any other of their purchases. 
Output a list of user_ids of these returning active users.

amazon_transactions:
| Column Name | Data Type  |
|-------------|------------|
| id          | int        |
| user_id     | int        |
| item        | varchar    |
| created_at  | datetime   |
| revenue     | int        |

```

```
