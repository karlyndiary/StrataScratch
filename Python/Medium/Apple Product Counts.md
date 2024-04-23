Find the number of Apple product users and the number of total users with a device and group the counts by language. 
Assume Apple products are only MacBook-Pro, iPhone 5s, and iPad-air. Output the language along with the total number of Apple users and users with any device. 
Order your results based on the number of total users in descending order.

playbook_events:
| Column Name | Data Type  |
|-------------|------------|
| user_id     | int        |
| occurred_at | datetime   |
| event_type  | varchar    |
| event_name  | varchar    |
| location    | varchar    |
| device      | varchar    |

playbook_users:
| Column Name  | Data Type  |
|--------------|------------|
| user_id      | int        |
| created_at   | datetime   |
| company_id   | int        |
| language     | varchar    |
| activated_at | datetime   |
| state        | varchar    |

```
import pandas as pd
df = pd.merge(playbook_events, playbook_users, on = 'user_id', how = 'inner')
apple_devices  = ["macbook pro", "iphone 5s", "ipad air"]
df = df.drop_duplicates(subset=['user_id', 'device'])
df['n_apple_users'] = df['device'].isin(apple_devices)
df_grouped = df.groupby('language').agg({'n_apple_users': 'sum', 'user_id':'nunique'}).reset_index()
df_grouped = df_grouped.sort_values(by='user_id', ascending=False)
```
