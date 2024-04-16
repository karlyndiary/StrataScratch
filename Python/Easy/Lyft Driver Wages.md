Find all Lyft drivers who earn either equal to or less than 30k USD or equal to or more than 70k USD.
Output all details related to retrieved records.

lyft_drivers:
| Column Name   | Data Type  |
|---------------|------------|
| index         | int        |
| start_date    | datetime   |
| end_date      | datetime   |
| yearly_salary | int        |

```
import pandas as pd
lyft_drivers[(lyft_drivers['yearly_salary'] <= 30000) | (lyft_drivers['yearly_salary'] >= 70000)]
```
