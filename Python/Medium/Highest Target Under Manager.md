Find the highest target achieved by the employee or employees who works under the manager id 13. Output the first name of the employee and target achieved. 
The solution should show the highest target achieved under manager_id=13 and which employee(s) achieved it.

salesforce_employees:
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
df = salesforce_employees[salesforce_employees['manager_id'] == 13]
target = df[df['target'] == df['target'].max()][['first_name', 'target']]
```
