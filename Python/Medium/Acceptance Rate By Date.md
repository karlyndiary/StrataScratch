What is the overall friend acceptance rate by date? Your output should have the rate of acceptances by the date the request was sent. Order by the earliest date to latest.
Assume that each friend request starts by a user sending (i.e., user_id_sender) a friend request to another user (i.e., user_id_receiver) that's logged in the table 
with action = 'sent'. If the request is accepted, the table logs action = 'accepted'. If the request is not accepted, no record of action = 'accepted' is logged.

fb_friend_requests:
| Column Name      | Data Type |
|------------------|-----------|
| user_id_sender   | varchar   |
| user_id_receiver | varchar   |
| date             | datetime  |
| action           | varchar   |

```
import pandas as pd
df = fb_friend_requests[fb_friend_requests.action == 'sent']
df = df.merge(fb_friend_requests[fb_friend_requests.action == 'accepted'], how = 'left', on = ['user_id_sender', 'user_id_receiver'])
df.assign(action_y = df.action_y.notnull()).groupby('date_x', as_index = False)['action_y'].mean()
```
