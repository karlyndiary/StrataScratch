Find employees who are earning more than their managers. Output the employee's first name along with the corresponding salary.

employee:
| Column Name      | Data Type  |
|------------------|------------|
| id               | int        |
| first_name       | varchar    |
| last_name        | varchar    |
| age              | int        |
| sex              | varchar    |
| employee_title   | varchar    |
| department       | varchar    |
| salary           | int        |
| target           | int        |
| bonus            | int        |
| email            | varchar    |
| city             | varchar    |
| address          | varchar    |
| manager_id       | int        |

```
import pandas as pd
df = pd.merge(employee, employee, left_on = 'manager_id', right_on = 'id', how = 'inner')
result = df[df['salary_x']>df['salary_y']][['first_name_x','salary_x']]
```
