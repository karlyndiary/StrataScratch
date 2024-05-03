Find the employee with the highest salary per department.
Output the department name, employee's first name along with the corresponding salary.

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
df = employee[employee['salary'] == employee.groupby(['department'])['salary'].transform('max')][['department','first_name','salary']]
```
