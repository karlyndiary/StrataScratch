Find the number of workers by department who joined in or after April.
Output the department name along with the corresponding number of workers.
Sort records based on the number of workers in descending order.

worker:
| Column Name   | Data Type  |
|---------------|------------|
| worker_id     | int        |
| first_name    | varchar    |
| last_name     | varchar    |
| salary        | int        |
| joining_date  | datetime   |
| department    | varchar    |

```
import pandas as pd
worker[worker['joining_date'].dt.month >= 4].groupby(['department']).size().reset_index(name = 'num_workers').
sort_values(by = 'num_workers', ascending = False)
```
