Count the number of movies that Abigail Breslin was nominated for an oscar.

oscar_nominees:
| Field    | Type    |
|----------|---------|
| year     | int     |
| category | varchar |
| nominee  | varchar |
| movie    | varchar |
| winner   | bool    |
| id       | int     |

```
select count(movie)
from oscar_nominees
where nominee = 'Abigail Breslin'
```
