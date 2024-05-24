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
select company_name, count(case when (year = 2020) then 1 end) - count(case when (year = 2019) then 1 end) as net_diff
from car_launches
group by company_name
```
