Output ids of students with a median score from the writing SAT.

sat_scores:
| Column Name | Data Type |
|-------------|-----------|
| school      | varchar   |
| teacher     | varchar   |
| student_id  | float     |
| sat_writing | float     |
| sat_verbal  | float     |
| sat_math    | float     |
| hrs_studied | float     |
| id          | int       |
| average_sat | float     |
| love        | datetime  |

```
import pandas as pd
median_scores = sat_scores[sat_scores['sat_writing'] == sat_scores['sat_writing'].median()][['student_id']]
```
