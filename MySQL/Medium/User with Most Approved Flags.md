Which user flagged the most distinct videos that ended up approved by YouTube? Output, in one column, their full name or names in case of a tie. 
In the user's full name, include a space between the first and the last name.

user_flags:
| Column Name   | Data Type |
|---------------|-----------|
| worker_ref_id | int       |
| bonus         | int       |

flag_review:
| Column Name       | Data Type  |
|-------------------|------------|
| flag_id           | varchar    |
| reviewed_by_yt    | bool       |
| reviewed_date     | datetime   |
| reviewed_outcome  | varchar    |

```
select username
from
  (select concat(f.user_firstname, ' ', f.user_lastname) as username, 
  dense_rank() over(order by count(distinct video_id) desc) as rn
  from user_flags f 
  join flag_review r 
  on f.flag_id = r.flag_id
  where lower(r.reviewed_outcome) = 'approved'
  group by username) as sub
where rn = 1
```
