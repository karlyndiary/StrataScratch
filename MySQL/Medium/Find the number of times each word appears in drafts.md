Find the number of times each word appears in drafts.
Output the word along with the corresponding number of occurrences.

google_file_store:
| Field     | Type     |
|-----------|----------|
| filename  | varchar  |
| contents  | varchar  |

```
with recursive num(n) as (
    select 1 as num
    union all
    select n+1 from num
    where n <= 100
)

select trim(trailing ',' from 
       trim(trailing '.' from 
       substring_index(substring_index(contents,' ', n),' ',-1)
       )
       ) as word, count(*) as nentry
from google_file_store g
join num
on n <= length(contents) - length(replace(contents, ' ', '')) + 1
where filename regexp 'draft'
group by word
```
