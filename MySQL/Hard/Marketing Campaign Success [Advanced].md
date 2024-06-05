You have a table of in-app purchases by user. Users that make their first in-app purchase are placed in a marketing campaign where they see call-to-actions for more in-app purchases. 
Find the number of users that made additional in-app purchases due to the success of the marketing campaign.

The marketing campaign doesn't start until one day after the initial in-app purchase so users that only made one or multiple purchases on the first day do not count, nor do we count 
users that over time purchase only the products they purchased on the first day.

marketing_campaign:
| Column      | Data Type |
|-------------|-----------|
| user_id     | int       |
| created_at  | datetime  |
| product_id  | int       |
| quantity    | int       |
| price       | int       |

```
with user as (
select user_id, min(created_at) as x
from marketing_campaign
group by user_id),

user_product as (
select user_id, product_id, min(created_at) as y
from marketing_campaign
group by user_id, product_id)

select count(distinct u.user_id) as count_ids
from user u 
join user_product p 
on u.user_id = p.user_id
where x != y
```
