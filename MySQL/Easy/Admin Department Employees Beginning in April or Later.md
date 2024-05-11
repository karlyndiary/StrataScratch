Find the number of employees working in the Admin department that joined in April or later.

worker:

| Column Name | Data Type |
|---|---|
| worker_id | int |
| first_name | varchar |
| last_name | varchar |
| salary | int |
| joining_date | datetime |
| department | varchar |

```
select count(*)
from worker
where department = 'Admin' and month(joining_date) >= 4;
```
