Find the popularity percentage for each user on Meta/Facebook. The popularity percentage is defined as the total number of friends the user has divided by the total number of users on the platform, then converted into a percentage by multiplying by 100.
Output each user along with their popularity percentage. Order records in ascending order by user id.
The 'user1' and 'user2' column are pairs of friends.

facebook_friends:
| Column Name | Data Type |
|-------------|-----------|
| user1       | int       |
| user2       | int       |

```
import pandas as pd
reverse_df = facebook_friends.rename(columns = {'user2':'user1','user1':'user2'})
df = pd.concat([facebook_friends, reverse_df])
100 * df.groupby('user1')['user2'].nunique()/df.user1.nunique()
```
