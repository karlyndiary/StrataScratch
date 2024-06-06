Find the monthly retention rate of users for each account separately for Dec 2020 and Jan 2021. Retention rate is the percentage of active users an account retains over a 
given period of time. In this case, assume the user is retained if he/she stays with the app in any future months. For example, if a user was active in Dec 2020 and has 
activity in any future month, consider them retained for Dec. You can assume all accounts are present in Dec 2020 and Jan 2021. Your output should have the account ID and 
the Jan 2021 retention rate divided by Dec 2020 retention rate.

sf_event:
| Column      | Data Type |
|-------------|-----------|
| date        | datetime  |
| account_id  | varchar   |
| user_id     | varchar   |

```
import pandas as pd

sf_events['year_month'] = sf_events['date'].dt.to_period('M')

dec_2020 = sf_events[(sf_events['year_month'].dt.year==2020) & (sf_events['year_month'].dt.month == 12)].drop_duplicates()
          [['account_id','user_id']]
jan_2021 = sf_events[(sf_events['year_month'].dt.year==2021) & (sf_events['year_month'].dt.month == 1)].drop_duplicates()
          [['account_id','user_id']]

max_date = sf_events.groupby('user_id')['date'].max().to_frame('max_date').reset_index()

dec_2020 = dec_2020.merge(max_date, on = 'user_id')
jan_2021 = jan_2021.merge(max_date, on = 'user_id')

dec_2020['retention'] = 0 
jan_2021['retention'] = 0

dec_2020.loc[dec_2020['max_date'] > '2020-12-31', 'retention'] = 1
jan_2021.loc[jan_2021['max_date'] > '2021-01-31', 'retention'] = 1

retention_dec = dec_2020.groupby('account_id')['retention'].mean().to_frame('retention_dec').reset_index()
retention_jan = jan_2021.groupby('account_id')['retention'].mean().to_frame('retention_jan').reset_index()

merged = retention_dec.merge(retention_jan, on = 'account_id')

merged['retention'] = merged['retention_jan']/merged['retention_dec']

result = merged[['account_id','retention']]
```
