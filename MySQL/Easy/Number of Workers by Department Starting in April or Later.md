Find the number of workers by department who joined in or after April.
Output the department name along with the corresponding number of workers.
Sort records based on the number of workers in descending order.

worker:
| Field        | Type     |
|--------------|----------|
| worker_id    | int      |
| first_name   | varchar  |
| last_name    | varchar  |
| salary       | int      |
| joining_date | datetime |
| department   | varchar  |

```
select department, count(*) as num_workers
from worker
where month(joining_date) >= 4
group by department
order by num_workers
```
