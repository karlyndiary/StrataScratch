Find the average total compensation based on employee titles and gender. Total compensation is calculated by adding both the salary and bonus of each employee. 
However, not every employee receives a bonus so disregard employees without bonuses in your calculation. Employee can receive more than one bonus.
Output the employee title, gender (i.e., sex), along with the average total compensation.

sf_employee:
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
| email          | varchar   |
| city           | varchar   |
| address        | varchar   |
| manager_id     | int       |

sf_bonus:
| Column Name   | Data Type |
|---------------|-----------|
| worker_ref_id | int       |
| bonus         | int       |

```
with bonus as (
select worker_ref_id, sum(bonus) as bonus
from sf_bonus
group by worker_ref_id)

select employee_title, sex, avg(salary + bonus) as avg_comp
from sf_employee emp 
join bonus b
on emp.id = b.worker_ref_id
where bonus is not null
group by employee_title
```
