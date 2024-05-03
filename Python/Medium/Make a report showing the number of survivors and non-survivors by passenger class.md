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
import pandas as pd
df = titanic.pivot_table(index = 'survived', columns = 'pclass', values = 'passengerid', aggfunc = 'nunique').reset_index()
df = df.rename(columns = {1:'first_class', 2:'second_class', 3:'third_class'})
```
