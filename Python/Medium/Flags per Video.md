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
import pandas as pd
df = user_flags[user_flags['flag_id'].notnull()]
df["username"] = df['user_firstname'].astype(str) + " " + df['user_lastname'].astype(str)
df = df.groupby(by='video_id')['username'].nunique().reset_index()
df = df.rename(columns = {'username': 'num_unique_users'})
```
