Find the activity date and the pe_description of facilities with the name 'STREET CHURROS' and with a score of less than 95 points.

los_angeles_restaurant_health_inspections:
| Column Name            | Data Type  |
|------------------------|------------|
| serial_number          | varchar    |
| activity_date          | datetime   |
| facility_name          | varchar    |
| score                  | int        |
| grade                  | varchar    |
| service_code           | int        |
| service_description    | varchar    |
| employee_id            | varchar    |
| facility_address       | varchar    |
| facility_city          | varchar    |
| facility_id            | varchar    |
| facility_state         | varchar    |
| facility_zip           | varchar    |
| owner_id               | varchar    |
| owner_name             | varchar    |
| pe_description         | varchar    |
| program_element_pe     | int        |
| program_name           | varchar    |
| program_status         | varchar    |
| record_id              | varchar    |

```
import pandas as pd
df = los_angeles_restaurant_health_inspections
df[(df['facility_name'] == 'STREET CHURROS') & (df['score'] < 95)][['activity_date', 'pe_description']]
```
