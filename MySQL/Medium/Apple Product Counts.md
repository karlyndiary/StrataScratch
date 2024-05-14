Find the number of Apple product users and the number of total users with a device and group the counts by language. 
Assume Apple products are only MacBook-Pro, iPhone 5s, and iPad-air. 
Output the language along with the total number of Apple users and users with any device. 
Order your results based on the number of total users in descending order.

playbook_events:
| Field         | Type      |
|---------------|-----------|
| user_id       | int       |
| occurred_at   | datetime  |
| event_type    | varchar   |
| event_name    | varchar   |
| location      | varchar   |
| device        | varchar   |

playbook_users:
| Field       | Type      |
|-------------|-----------|
| user_id     | int       |
| created_at  | datetime  |
| company_id  | int       |
| language    | varchar   |
| activated_at| datetime  |
| state       | varchar   |

```
select u.language,
count(distinct case when e.device in ('macbook pro','iphone 5s','ipad air') then e.user_id else null end) as apple_users,
count(distinct e.user_id) as total_users
from playbook_events e
join playbook_users u
on e.user_id = u.user_id
group by u.language
order by total_users desc
```
