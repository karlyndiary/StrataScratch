Find the most profitable company from the financial sector. Output the result along with the continent.

forbes_global_2010_2014:
| Column Name    | Data Type |
|----------------|-----------|
| company        | varchar   |
| sector         | varchar   |
| industry       | varchar   |
| continent      | varchar   |
| country        | varchar   |
| marketvalue    | float     |
| sales          | float     |
| profits        | float     |
| assets         | float     |
| rank           | int       |
| forbeswebpage  | varchar   |

```
import pandas as pd
df = forbes_global_2010_2014
df[(df['sector'] == 'Financials') & (df['rank'] == 1)][['company', 'continent']]
```
