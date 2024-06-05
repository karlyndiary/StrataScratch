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
import pandas as pd
df = marketing_campaign
df1 = df.groupby('user_id').created_at.min().reset_index()
df2 = df.groupby(['user_id','product_id']).created_at.min().reset_index()
df3 = pd.merge(df1, df2, on = 'user_id')
df4 = df3.query('created_at_x != created_at_y')
df4.user_id.drop_duplicates().size
```
