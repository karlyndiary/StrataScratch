Find the second highest salary of employees.

employee:
| Column Name    | Data Type |
|----------------|-----------|
| id             | int       |
| first_name     | varchar   |
| last_name      | varchar   |
| age            | int       |
| sex            | varchar   |
| employee_title | varchar   |
| department     | varchar   |
| salary         | int       |
| target         | int       |
| bonus          | int       |
| email          | varchar   |
| city           | varchar   |
| address        | varchar   |
| manager_id     | int       |

```
import pandas as pd
df = employee['salary'].sort_values(ascending = False).iloc[1]
```
