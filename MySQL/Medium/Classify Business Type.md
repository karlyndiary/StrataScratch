Classify each business as either a restaurant, cafe, school, or other.

- A restaurant should have the word 'restaurant' in the business name.
- A cafe should have either 'cafe', 'café', or 'coffee' in the business name.
- A school should have the word 'school' in the business name.
- All other businesses should be classified as 'other'.

Output the business name and their classification.

sf_restaurant_health_violations:
| Field                   | Type      |
|-------------------------|-----------|
| business_id             | int       |
| business_name           | varchar   |
| business_address        | varchar   |
| business_city           | varchar   |
| business_state          | varchar   |
| business_postal_code    | float     |
| business_latitude       | float     |
| business_longitude      | float     |
| business_location       | varchar   |
| business_phone_number   | float     |
| inspection_id           | varchar   |
| inspection_date         | datetime  |
| inspection_score        | float     |
| inspection_type         | varchar   |
| violation_id            | varchar   |
| violation_description   | varchar   |
| risk_category           | varchar   |

```
select distinct business_name,
case when business_name like '%restaurant%' then 'restaurant'
when business_name like '%cafe%' or business_name like '%café%' or business_name like '%coffee%' then 'cafe'
when business_name like '%school%' then 'school' else 'other' end as business_type
from sf_restaurant_health_violations
```
