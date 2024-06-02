Find the total number of downloads for paying and non-paying users by date. 
Include only records where non-paying customers have more downloads than paying customers. 
The output should be sorted by earliest date first and contain 3 columns date, non-paying downloads, paying downloads.

ms_user_dimension:
| Column  | Data Type |
|---------|-----------|
| user_id | int       |
| acc_id  | int       |

ms_acc_dimension:
| Column           | Data Type |
|------------------|-----------|
| acc_id           | int       |
| paying_customer  | varchar   |

ms_download_facts
| Column    | Data Type |
|-----------|-----------|
| date      | datetime  |
| user_id   | int       |
| downloads | int       |

```
import pandas as pd
df = ms_user_dimension.merge(ms_acc_dimension, on = 'acc_id').merge(ms_download_facts, on = 'user_id')
df = df.pivot_table(index = ['date'], columns = 'paying_customer', values = 'downloads', aggfunc = 'sum')
df[df['no']>df['yes']].reset_index()
```
