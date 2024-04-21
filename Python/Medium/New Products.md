You are given a table of product launches by company by year. Write a query to count the net difference between the number of products companies launched in 2020 
with the number of products companies launched in the previous year. Output the name of the companies and a net difference of net products released for 2020 
compared to the previous year.

car_launches:
| Column Name   | Data Type |
|---------------|-----------|
| year          | int       |
| company_name  | varchar   |
| product_name  | varchar   |

```
import pandas as pd
df = car_launches.groupby(['company_name','year']).count().reset_index()
df = df.pivot_table(values = 'product_name', index = 'company_name', aggfunc = 'sum', columns = 'year').reset_index()
df['net_diff'] = df[2020]-df[2019]
df = df[['company_name', 'net_diff']]
```
