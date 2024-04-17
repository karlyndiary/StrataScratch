Find the base pay for Police Captains.
Output the employee name along with the corresponding base pay.

sf_public_salaries:
| Column Name       | Data Type  |
|-------------------|------------|
| id                | int        |
| employeename      | varchar    |
| jobtitle          | varchar    |
| basepay           | float      |
| overtimepay       | float      |
| otherpay          | float      |
| benefits          | float      |
| totalpay          | float      |
| totalpaybenefits  | float      |
| year              | int        |
| notes             | datetime   |
| agency            | varchar    |
| status            | varchar    |

```
import pandas as pd
sf_public_salaries[sf_public_salaries['jobtitle'].str.contains('CAPTAIN')][['employeename','basepay']]
```
