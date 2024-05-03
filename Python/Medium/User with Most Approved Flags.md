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
import pandas as pd
df = pd.merge(user_flags, flag_review, on = 'flag_id', how = 'inner')
df = df[df['reviewed_outcome'] == 'APPROVED']
df['username'] = df['user_firstname'] + ' ' + df['user_lastname']
df = df.groupby('username')['video_id'].nunique().reset_index()
result = df[df['video_id'] == df['video_id'].max()]['username']
```
