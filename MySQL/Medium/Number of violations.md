You're given a dataset of health inspections. Count the number of violation in an inspection in 'Roxanne Cafe' for each year. 
If an inspection resulted in a violation, there will be a value in the 'violation_id' column. Output the number of violations by year in ascending order.

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
select year(inspection_date) as year, count(violation_id) as violation_count
from sf_restaurant_health_violations
where business_name like '%Roxanne Cafe%'
group by year
order by year 
```
