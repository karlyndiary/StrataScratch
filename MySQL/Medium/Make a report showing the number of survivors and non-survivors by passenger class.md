Make a report showing the number of survivors and non-survivors by passenger class.
Classes are categorized based on the pclass value as:
pclass = 1: first_class
pclass = 2: second_classs
pclass = 3: third_class
Output the number of survivors and non-survivors by each class.

titanic:
| Column Name  | Data Type |
|--------------|-----------|
| passengerid  | int       |
| survived     | int       |
| pclass       | int       |
| name         | varchar   |
| sex          | varchar   |
| age          | float     |
| sibsp        | int       |
| parch        | int       |
| ticket       | varchar   |
| fare         | float     |
| cabin        | varchar   |
| embarked     | varchar   |

```
select survived,
sum(case when pclass = 1 then 1 else 0 end) as first_class, 
sum(case when pclass = 2 then 1 else 0 end) as second_class,
sum(case when pclass = 3 then 1 else 0 end) as third_class
from titanic
group by survived
```
