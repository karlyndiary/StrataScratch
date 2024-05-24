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
select distinct song_name, year_rank, group_name
from billboard_top_100_year_end
where year = "2010"
order by year_rank
limit 10
```
