Find matching hosts and guests pairs in a way that they are both of the same gender and nationality.
Output the host id and the guest id of matched pair.

airbnb_hosts:
| Column Name | Data Type |
|-------------|-----------|
| host_id     | int       |
| nationality | varchar   |
| gender      | varchar   |
| age         | int       |


airbnb_guests:
| Column Name | Data Type |
|-------------|-----------|
| guest_id    | int       |
| nationality | varchar   |
| gender      | varchar   |
| age         | int       |

```
import pandas as pd

df = pd.merge(airbnb_hosts, airbnb_guests, on = ['gender', 'nationality'], how = 'left').drop_duplicates()

df[['host_id', 'guest_id']]
```
