Find the number of employees working in the Admin department that joined in April or later.

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
worker[(worker['department'] == 'Admin') & (worker['joining_date'].dt.month >= 4)]['department'].count()
```
