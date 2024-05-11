Find how many times each artist appeared on the Spotify ranking list
Output the artist name along with the corresponding number of occurrences.
Order records by the number of occurrences in descending order.

spotify_worldwide_daily_song_ranking:
| Field      | Type      |
|------------|-----------|
| id         | int       |
| position   | int       |
| trackname  | varchar   |
| artist     | varchar   |
| streams    | int       |
| url        | varchar   |
| date       | datetime  |
| region     | varchar   |

```
select distinct artist, count(*) as n_occurences
from spotify_worldwide_daily_song_ranking
group by artist
order by n_occurences desc
```
