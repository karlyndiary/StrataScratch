You are given a dataset that provides the number of active users per day per premium account. A premium account will have an entry for every day that it’s premium. 
However, a premium account may be temporarily discounted and considered not paid, this is indicated by a value of 0 in the final_price column for a certain day. 
Find out how many premium accounts that are paid on any given day are still premium and paid 7 days later.
Output the date, the number of premium and paid accounts on that day, and the number of how many of these accounts are still premium and paid 7 days later. 
Since you are only given data for a 14 days period, only include the first 7 available dates in your output.

premium_accounts_by_day:
| Column Name        | Data Type |
|--------------------|-----------|
| account_id         | varchar   |
| entry_date         | datetime  |
| users_visited_7d   | int       |
| final_price        | int       |
| plan_size          | int       |

```
select a.entry_date, count(a.account_id) as premium_paid_accounts, count(b.account_id) as premium_paid_accounts_after_7d
from premium_accounts_by_day a
left join premium_accounts_by_day b 
on a.account_id = b.account_id
and datediff(b.entry_date, a.entry_date) = 7
and b.final_price > 0 
where a.final_price > 0 
group by a.entry_date
order by a.entry_date
limit 7
```
