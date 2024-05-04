Output share of US users that are active. Active users are the ones with an "open" status in the table.

fb_active_users:
| Column Name | Data Type |
|-------------|-----------|
| user_id     | int       |
| name        | varchar   |
| status      | varchar   |
| country     | varchar   |

```
import pandas as pd
result = fb_active_users[fb_active_users['country'] == 'USA'].groupby('status')['user_id'].count().to_frame('user_count')
result = result.loc['open'] / result['user_count'].sum()
```
