What were the top 10 ranked songs in 2010?
Output the rank, group name, and song name but do not show the same song twice.
Sort the result based on the year_rank in ascending order.

billboard_top_100_year_end:
| Column Name | Data Type |
|-------------|-----------|
| year        | int       |
| year_rank   | int       |
| group_name  | varchar   |
| artist      | varchar   |
| song_name   | varchar   |
| id          | int       |

```
import pandas as pd
df = billboard_top_100_year_end[billboard_top_100_year_end['year']==2010].drop_duplicates(subset = 'song_name', keep = 'last')
[0:10][['year_rank','group_name','song_name']]
```
