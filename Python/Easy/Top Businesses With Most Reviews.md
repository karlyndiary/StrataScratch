Find the top 5 businesses with most reviews. Assume that each row has a unique business_id such that the total reviews for each business is listed on each row. 
Output the business name along with the total number of reviews and order your results by the total reviews in descending order.

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
import pandas as pd
yelp_business.sort_values('review_count', ascending = False)[0:5][['name','review_count']]
```
