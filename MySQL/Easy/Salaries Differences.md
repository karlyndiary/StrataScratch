Write a query that calculates the difference between the highest salaries found in the marketing and engineering departments. 
Output just the absolute difference in salaries.

db_employee:
| Field         | Type    |
|---------------|---------|
| id            | int     |
| first_name    | varchar |
| last_name     | varchar |
| salary        | int     |
| department_id | int     |

db_dept:
| Field      | Type    |
|------------|---------|
| id         | int     |
| department | varchar |

```
select abs(max(a.salary) - max(b.salary)) as diff_salary
from db_employee a, db_employee b
where a.department_id = 1 and b.department_id = 4
```
