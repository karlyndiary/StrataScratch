Find the number of apartments per nationality that are owned by people under 30 years old.
Output the nationality along with the number of apartments.
Sort records by the apartments count in descending order.

airbnb_hosts:
| Column Name | Data Type |
|-------------|-----------|
| host_id     | int       |
| nationality | varchar   |
| gender      | varchar   |
| age         | int       |

airbnb_units:
| Column Name | Data Type |
|-------------|-----------|
| host_id     | int       |
| unit_id     | varchar   |
| unit_type   | varchar   |
| n_beds      | int       |
| n_bedrooms  | int       |
| country     | varchar   |
| city        | varchar   |

```
import pandas as pd
df = pd.merge(airbnb_hosts, airbnb_units, on = 'host_id', how = 'left')
df = df[(df['age'] < 30) & (df['unit_type'] == 'Apartment')]
df.groupby(['nationality'])['unit_id'].nunique().reset_index(name='apartment_count').
sort_values(by='apartment_count', ascending=False)
```
