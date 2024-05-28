Find the number of times the words 'bull' and 'bear' occur in the contents. We're counting the number of times the words occur so words like 'bullish' should not be included in our count.
Output the word 'bull' and 'bear' along with the corresponding number of occurrences.

google_file_store:
| Column Name | Data Type |
|-------------|-----------|
| filename    | varchar   |
| contents    | varchar   |

```
select 'bull' as word, count(*) as count
from google_file_store
where contents like '%bull%'
union
select 'bear' as word, count(*) as count
from google_file_store
where contents like '%bear%'
```
