Write a query that calculates the difference between the highest salaries found in the marketing and engineering departments. Output just the absolute difference in salaries.

db_employee:
| Column Name   | Data Type  |
|---------------|------------|
| id            | int        |
| first_name    | varchar    |
| last_name     | varchar    |
| salary        | int        |
| department_id | int        |

db_dept:
| Column Name | Data Type |
|-------------|-----------|
| id          | int       |
| department  | varchar   |

```
import pandas as pd
db_employee[db_employee['department_id'] == 4]['salary'].max() -
  db_employee[db_employee['department_id'] == 1]['salary'].max()
```
