You have been asked to find the job titles of the highest-paid employees.

Your output should include the highest-paid title or multiple titles with the same salary.

Worker:
| Column Name   | Data Type  |
|---------------|------------|
| worker_id     | int        |
| first_name    | varchar    |
| last_name     | varchar    |
| salary        | int        |
| joining_date  | datetime   |
| department    | varchar    |

title:
| Column Name    | Data Type  |
|----------------|------------|
| worker_ref_id  | int        |
| worker_title   | varchar    |
| affected_from  | datetime   |

```
import pandas as pd
worker[worker.salary == worker.salary.max()].
merge(title, how = 'inner', left_on = 'worker_id', right_on = 'worker_ref_id')[['worker_title']]
```
