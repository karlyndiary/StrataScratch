Find the most profitable company from the financial sector. Output the result along with the continent.

forbes_global_2010_2014:
| Field          | Type    |
|----------------|---------|
| company        | varchar |
| sector         | varchar |
| industry       | varchar |
| continent      | varchar |
| country        | varchar |
| marketvalue    | float   |
| sales          | float   |
| profits        | float   |
| assets         | float   |
| rank           | int     |
| forbeswebpage  | varchar |

```
select company, continent
from forbes_global_2010_2014
where sector = 'Financials'
limit 1
```
