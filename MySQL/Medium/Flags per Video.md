For each video, find how many unique users flagged it. A unique user can be identified using the combination of their first name and last name. 
Do not consider rows in which there is no flag ID.

user_flags:
| Column Name     | Data Type |
|-----------------|-----------|
| user_firstname  | varchar   |
| user_lastname   | varchar   |
| video_id        | varchar   |
| flag_id         | varchar   |

```
select video_id, count(distinct concat(ifnull(user_firstname, ''), ifnull(user_lastname, ''))) as num_unique_users
from user_flags
where flag_id is not null
group by video_id
```
