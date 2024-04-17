Compare each employee's salary with the average salary of the corresponding department.
Output the department, first name, and salary of employees along with the average salary of that department.

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
employee['avg_salary'] = employee.groupby('department')['salary'].transform('mean')
employee[['first_name', 'department', 'salary', 'avg_salary']]
```
