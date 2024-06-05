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

```
