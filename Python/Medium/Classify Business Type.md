Classify each business as either a restaurant, cafe, school, or other.

- A restaurant should have the word 'restaurant' in the business name.
- A cafe should have either 'cafe', 'café', or 'coffee' in the business name.
- A school should have the word 'school' in the business name.
- All other businesses should be classified as 'other'.

Output the business name and their classification.

sf_restaurant_health_violations:
| Column Name            | Data Type  |
|------------------------|------------|
| business_id            | int        |
| business_name          | varchar    |
| business_address       | varchar    |
| business_city          | varchar    |
| business_state         | varchar    |
| business_postal_code   | float      |
| business_latitude      | float      |
| business_longitude     | float      |
| business_location      | varchar    |
| business_phone_number  | float      |
| inspection_id          | varchar    |
| inspection_date        | datetime   |
| inspection_score       | float      |
| inspection_type        | varchar    |
| violation_id           | varchar    |
| violation_description  | varchar    |
| risk_category          | varchar    |

```
import pandas as pd

sf_restaurant_health_violations['category'] = sf_restaurant_health_violations['business_name'].apply(lambda x: \
'restaurant' if x.lower().find('restaurant') >= 0 \

else 'cafe' if x.lower().find('cafe') >= 0 \
or x.lower().find('café') >= 0 \
or x.lower().find('coffee') >= 0 \

else 'school' if x.lower().find('school') >= 0 \

else 'other')

sf_restaurant_health_violations[['business_name', 'category']].drop_duplicates()
```
