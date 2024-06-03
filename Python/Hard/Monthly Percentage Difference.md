Given a table of purchases by date, calculate the month-over-month percentage change in revenue. The output should include the year-month date (YYYY-MM) and percentage change, 
rounded to the 2nd decimal point, and sorted from the beginning of the year to the end of the year. The percentage change column will be populated from the 2nd month forward 
and can be calculated as ((this month's revenue - last month's revenue) / last month's revenue)*100.

sf_transactions:
| Field        | Type       |
|--------------|------------|
| id           | int        |
| created_at   | datetime   |
| value        | int        |
| purchase_id  | int        |

```
import pandas as pd
sf_transactions['year_month'] = sf_transactions['created_at'].dt.to_period('M')
monthly_values = sf_transactions.groupby(['year_month'])['value'].sum().reset_index()
monthly_values['percentage_change'] =  monthly_values['value'].pct_change() * 100
monthly_values['percentage_change'] = round(monthly_values['percentage_change'], 2)
monthly_values[['year_month', 'percentage_change']]
```
