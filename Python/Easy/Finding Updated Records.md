We have a table with employees and their salaries, however, some of the records are old and contain outdated salary information. 
Find the current salary of each employee assuming that salaries increase each year. 
Output their id, first name, last name, department ID, and current salary. Order your list by employee ID in ascending order.

ms_employee_salary
| Column Name   | Data Type |
|---------------|-----------|
| id            | int       |
| first_name    | varchar   |
| last_name     | varchar   |
| salary        | int       |
| department_id | int       |

```
import pandas as pd
import numpy as np
ms_employee_salary.sort_values(['id','salary'], ascending = (True, False)).groupby(['id']).first().reset_index()

or

ms_employee_salary.groupby('id').max().reset_index()
```
