Find the Olympics with the highest number of athletes. The Olympics game is a combination of the year and the season, and is found in the 'games' column. 
Output the Olympics along with the corresponding number of athletes.

olympics_athletes_events:
| Column Name | Data Type |
|-------------|-----------|
| id          | int       |
| name        | varchar   |
| sex         | varchar   |
| age         | float     |
| height      | float     |
| weight      | datetime  |
| team        | varchar   |
| noc         | varchar   |
| games       | varchar   |
| year        | int       |
| season      | varchar   |
| city        | varchar   |
| sport       | varchar   |
| event       | varchar   |
| medal       | varchar   |

```
import pandas as pd
olympics_athletes_events.drop_duplicates(subset = ['name', 'games'])['games'].value_counts().reset_index().head(1)
```
