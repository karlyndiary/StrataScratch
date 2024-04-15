Count the number of movies that Abigail Breslin was nominated for an oscar.

oscar_nominees:
| Column Name | Data Type |
|-------------|-----------|
| year        | int       |
| category    | varchar   |
| nominee     | varchar   |
| movie       | varchar   |
| winner      | bool      |
| id          | int       |

```
import pandas as pd
oscar_nominees[oscar_nominees['nominee'] == 'Abigail Breslin']['movie'].count()
```
