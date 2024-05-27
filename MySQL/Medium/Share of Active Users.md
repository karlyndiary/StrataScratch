Output share of US users that are active. Active users are the ones with an "open" status in the table.

fb_active_users:
| Column Name | Data Type |
|-------------|-----------|
| user_id     | int       |
| name        | varchar   |
| status      | varchar   |
| country     | varchar   |

```
SELECT active_users/cast(total_users as float) as active_users_share 
FROM
(SELECT COUNT(user_id) total_users,
          COUNT(CASE WHEN status = 'open' THEN 1 ELSE NULL END) AS active_users
   FROM fb_active_users
   WHERE country = 'USA') sub
```
