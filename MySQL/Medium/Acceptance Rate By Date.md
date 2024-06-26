What is the overall friend acceptance rate by date? Your output should have the rate of acceptances by the date the request was sent. Order by the earliest date to latest.

Assume that each friend request starts by a user sending (i.e., user_id_sender) a friend request to another user (i.e., user_id_receiver) that's logged in the table with action = 'sent'. If the request is accepted, the table logs action = 'accepted'. If the request is not accepted, no record of action = 'accepted' is logged.

fb_friend_requests:
| Field              | Type      |
|--------------------|-----------|
| user_id_sender     | varchar   |
| user_id_receiver   | varchar   |
| date               | datetime  |
| action             | varchar   |

```
with a as (select * from fb_friend_requests where action = 'accepted'),
b as (select * from fb_friend_requests where action = 'sent')

select b.date, count(a.user_id_receiver)/count(b.user_id_sender) as acceptance_rate
from a 
right join b 
on a.user_id_sender = b.user_id_sender and a.user_id_receiver = b.user_id_receiver
group by date
```
