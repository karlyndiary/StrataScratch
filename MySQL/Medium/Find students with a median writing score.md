Output ids of students with a median score from the writing SAT.

sat_scores:
| Field        | Type     |
|--------------|----------|
| school       | varchar  |
| teacher      | varchar  |
| student_id   | float    |
| sat_writing  | float    |
| sat_verbal   | float    |
| sat_math     | float    |
| hrs_studied  | float    |
| id           | int      |
| average_sat  | float    |
| love         | datetime |

```
with cte as (
select *, row_number() over(order by sat_writing) as roww from sat_scores)

select student_id 
from cte
where sat_writing = (select sat_writing
                    from cte
                    where roww = (select round(count(*)/2)
                                from cte))
```
