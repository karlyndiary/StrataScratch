Find songs that have ranked in the top position. Output the track name and the number of times it ranked at the top.
Sort your records by the number of times the song was in the top position in descending order.

spotify_worldwide_daily_song_ranking:
| Column Name | Data Type |
|-------------|-----------|
| id          | int       |
| position    | int       |
| trackname   | varchar   |
| artist      | varchar   |
| streams     | int       |
| url         | varchar   |
| date        | datetime  |
| region      | varchar   |

```
import pandas as pd
spotify_worldwide_daily_song_ranking[spotify_worldwide_daily_song_ranking['position'] == 1]['trackname'].value_counts()
```
