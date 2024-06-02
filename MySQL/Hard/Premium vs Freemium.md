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
with cte as (
select date, sum(case when paying_customer = 'yes' then downloads end) as paying, 
sum(case when paying_customer = 'no' then downloads end) as non_paying
from ms_acc_dimension acc 
join ms_user_dimension user
on acc.acc_id = user.acc_id
join ms_download_facts facts
on user.user_id = facts.user_id
group by date
order by date
)
select date, non_paying, paying
from cte
where (non_paying - paying) > 0
order by date 
```
