Find the top 5 states with the most 5 star businesses. Output the state name along with the number of 5-star businesses and order records by the number of 5-star businesses 
in descending order. In case there are ties in the number of businesses, return all the unique states. If two states have the same result, sort them in alphabetical order.

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
df = yelp_business[yelp_business['stars'] == 5]
df = df.groupby(['state'])['stars'].count().reset_index(name = 'n_businesses')
df = df.sort_values(by = 'n_businesses', ascending = False).head(6)[['state','n_businesses']]
```
