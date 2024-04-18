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
import pandas as pd
import numpy as np

df = facebook_web_log

df1 = df[df['action'] == 'page_load']
df1['day'] = df1['timestamp'].dt.date
df1 = df1.groupby(['user_id', 'day'], as_index = False).max()

df2 = df[df['action'] == 'page_exit']
df2['day'] = df2['timestamp'].dt.date
df2 = df2.groupby(['user_id','day'], as_index = False).min()

dfm = pd.merge(df1, df2, how = 'inner', on = ['user_id', 'day'])
dfm['diff'] = dfm['timestamp_y'] - dfm['timestamp_x']
dfm.groupby('user_id', as_index = False).apply(np.mean)
```
