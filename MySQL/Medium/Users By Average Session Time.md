Calculate each user's average session time. A session is defined as the time difference between a page_load and page_exit. 
For simplicity, assume a user has only 1 session per day and if there are multiple of the same events on that day, 
consider only the latest page_load and earliest page_exit, with an obvious restriction that load time event should happen before exit time event. 
Output the user_id and their average session time.

facebook_web_log:
| Column Name | Data Type |
|-------------|-----------|
| user_id     | int       |
| timestamp   | datetime  |
| action      | varchar   |

```
select user_id, avg(timestampdiff(second, load_time, exit_time)) as session_time
from (
  select date(timestamp), user_id,
  max(if(action = 'page_load', timestamp, null)) as load_time,
  min(if(action = 'page_exit', timestamp, null)) as exit_time
  from facebook_web_log
  group by 1, 2) sub
group by user_id
having session_time is not null
```
