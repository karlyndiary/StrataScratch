Find the rate of processed tickets for each type.

facebook_complaints:
| Column Name   | Data Type |
|---------------|-----------|
| complaint_id  | int       |
| type          | int       |
| processed     | bool      |

```
select type, sum(processed)/count(*) as processed_rate
from facebook_complaints
group by type
```
