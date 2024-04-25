Find the rate of processed tickets for each type.

facebook_complaints:
| Column Name   | Data Type |
|---------------|-----------|
| complaint_id  | int       |
| type          | int       |
| processed     | bool      |

```
import pandas as pd
facebook_complaints.groupby('type', as_index = False)['processed'].mean()
```
