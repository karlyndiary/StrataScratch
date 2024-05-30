You’re given a table of rental property searches by users. The table consists of search results and outputs host information for searchers. 
Find the minimum, average, maximum rental prices for each host’s popularity rating. The host’s popularity rating is defined as below:
0 reviews: New
1 to 5 reviews: Rising
6 to 15 reviews: Trending Up
16 to 40 reviews: Popular
more than 40 reviews: Hot

Tip: The id column in the table refers to the search ID. You'll need to create your own host_id by concating price, room_type, host_since, zipcode, and number_of_reviews.

Output host popularity rating and their minimum, average and maximum rental prices.

airbnb_host_searches:
| Field                  | Data Type          |
|------------------------|--------------------|
| id                     | int                |
| price                  | float              |
| property_type          | varchar            |
| room_type              | varchar            |
| amenities              | varchar            |
| accommodates           | int                |
| bathrooms              | int                |
| bed_type               | varchar            |
| cancellation_policy    | varchar            |
| cleaning_fee           | bool               |
| city                   | varchar            |
| host_identity_verified | varchar            |
| host_response_rate     | varchar            |
| host_since             | datetime           |
| neighbourhood          | varchar            |
| number_of_reviews      | int                |
| review_scores_rating   | float              |
| zipcode                | int                |
| bedrooms               | int                |
| beds                   | int                |

```
import pandas as pd
import numpy as np

df = airbnb_host_searches

df['host_id'] = df['price'].map(str) + df['room_type'].map(str) + df['host_since'].map(str) + df['zipcode'].map(str) + df['number_of_reviews'].map(str)

df1 = df[['host_id','price','number_of_reviews']].drop_duplicates()

df1['host_popularity_rating'] = df1['number_of_reviews'].apply(lambda x: 'New' if x < 1 else 'Rising' if x <= 5 else 'Trending Up' if x <=15 else 'Popular' if x <= 40 else 'Hot')

result = df1.groupby('host_popularity_rating').agg(min_price = ('price', min), avg_price = ('price', np.mean), max_price = ('price', max)).reset_index()
```
