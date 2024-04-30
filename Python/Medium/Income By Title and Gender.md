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
import pandas as pd
sf_bonus = sf_bonus.groupby(['worker_ref_id']).sum().reset_index()
df = pd.merge(sf_employee, sf_bonus, left_on = 'id', right_on = 'worker_ref_id', how = 'inner')
df['total_comp'] = df['salary'] + df['bonus']
df1 = df.groupby(['employee_title', 'sex'])['total_comp'].mean().reset_index()
df1.rename(columns={'total_comp': 'avg_total_comp'}, inplace=True)
result = df1[['employee_title', 'sex', 'avg_total_comp']]
```
