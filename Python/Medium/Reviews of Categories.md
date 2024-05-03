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
import pandas as pd
yelp_business['category'] = yelp_business['categories'].str.split(';')
yelp_business = yelp_business.explode('category')
df = yelp_business.groupby('category')['review_count'].sum().reset_index()
df.sort_values(by = 'review_count', ascending = False)
```
