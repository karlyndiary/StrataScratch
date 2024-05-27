Find the top business categories based on the total number of reviews. Output the category along with the total number of reviews. Order by total reviews in descending order.

yelp_business:
| Column Name   | Data Type |
|---------------|-----------|
| business_id   | varchar   |
| name          | varchar   |
| neighborhood  | varchar   |
| address       | varchar   |
| city          | varchar   |
| state         | varchar   |
| postal_code   | varchar   |
| latitude      | float     |
| longitude     | float     |
| stars         | float     |
| review_count  | int       |
| is_open       | int       |
| categories    | varchar   |

```
with recursive num(n) as(
    select 1 
    union all
    select n+1 from num where n < 12)

select substring_index(substring_index(categories, ';', n), ';', -1) as category,
sum(review_count) as reviews_count
from yelp_business
join num
on n <= char_length(categories) - char_length(replace(categories,';','')) + 1 
group by category
```
