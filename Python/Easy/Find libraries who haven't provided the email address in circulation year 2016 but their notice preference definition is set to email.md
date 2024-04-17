Find libraries who haven't provided the email address in circulation year 2016 but their notice preference definition is set to email.
Output the library code.

library_usage:
| Column Name                  | Data Type  |
|------------------------------|------------|
| patron_type_code             | int        |
| patron_type_definition       | varchar    |
| total_checkouts             | int        |
| total_renewals               | int        |
| age_range                    | varchar    |
| home_library_code            | varchar    |
| home_library_definition      | varchar    |
| circulation_active_month     | varchar    |
| circulation_active_year      | float      |
| notice_preference_code       | varchar    |
| notice_preference_definition | varchar    |
| provided_email_address       | bool       |
| year_patron_registered       | int        |
| outside_of_county            | bool       |
| supervisor_district          | float      |

```
import pandas as pd
library_usage.query('notice_preference_definition == "email" and
circulation_active_year == 2016 and provided_email_address == False')
[['home_library_code']].drop_duplicates()
```
