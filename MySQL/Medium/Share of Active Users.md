Output share of US users that are active. Active users are the ones with an "open" status in the table.

fb_active_users:
| Column Name | Data Type |
|-------------|-----------|
| user_id     | int       |
| name        | varchar   |
| status      | varchar   |
| country     | varchar   |

```
select avg(case when status = 'open' then 1 else 0 end) as active_users_share
from fb_active_users
where country = 'USA'
```
