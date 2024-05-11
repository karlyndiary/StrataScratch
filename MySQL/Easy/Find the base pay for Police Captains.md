Find the base pay for Police Captains.
Output the employee name along with the corresponding base pay.

sf_public_salaries:
| Field             | Type    |
|-------------------|---------|
| id                | int     |
| employeename      | varchar |
| jobtitle          | varchar |
| basepay           | float   |
| overtimepay       | float   |
| otherpay          | float   |
| benefits          | float   |
| totalpay          | float   |
| totalpaybenefits  | float   |
| year              | int     |
| notes             | datetime|
| agency            | varchar |
| status            | varchar |

```
select employeename, basepay
from sf_public_salaries
where jobtitle like 'Captain%'
```
