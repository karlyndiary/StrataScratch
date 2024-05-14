Find employees who are earning more than their managers. Output the employee's first name along with the corresponding salary.

employee:
| Field           | Type    |
|-----------------|---------|
| id              | int     |
| first_name      | varchar |
| last_name       | varchar |
| age             | int     |
| sex             | varchar |
| employee_title  | varchar |
| department      | varchar |
| salary          | int     |
| target          | int     |
| bonus           | int     |
| email           | varchar |
| city            | varchar |
| address         | varchar |
| manager_id      | int     |

```
select emp.first_name, emp.salary
from employee emp
join employee man
on emp.manager_id = man.id
where emp.salary > man.salary
```
