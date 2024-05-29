Find the popularity percentage for each user on Meta/Facebook. The popularity percentage is defined as the total number of friends the user has divided by the total number of users on the platform, then converted into a percentage by multiplying by 100.
Output each user along with their popularity percentage. Order records in ascending order by user id.
The 'user1' and 'user2' column are pairs of friends.

facebook_friends:
| Column Name | Data Type |
|-------------|-----------|
| user1       | int       |
| user2       | int       |

```
with users as (
select *
from facebook_friends
union
select user2 as user1, user1 as user2
from facebook_friends
order by user1)

select user1, (count(user2)/(select count(distinct(user1)) from users)) * 100 as percentage_popularity
from users
group by user1
```
