Compare each employee's salary with the average salary of the corresponding department.
Output the department, first name, and salary of employees along with the average salary of that department.

employee:
| Field          | Type    |
|----------------|---------|
| id             | int     |
| first_name     | varchar |
| last_name      | varchar |
| age            | int     |
| sex            | varchar |
| employee_title | varchar |
| department     | varchar |
| salary         | int     |
| target         | int     |
| bonus          | int     |
| email          | varchar |
| city           | varchar |
| address        | varchar |
| manager_id     | int     |

```
select department, first_name, salary, avg(salary) over(partition by department) as average_salary from employee
```
