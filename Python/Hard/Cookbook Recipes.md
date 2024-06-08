You are given the table with titles of recipes from a cookbook and their page numbers. You are asked to represent how the recipes will be distributed in the book.
Produce a table consisting of three columns: left_page_number, left_title and right_title. The k-th row (counting from 0), should contain the number and the title of the page with the 
number 2×k in the first and second columns respectively, and the title of the page with the number 2×k+1 in the third column.
Each page contains at most 1 recipe. If the page does not contain a recipe, the appropriate cell should remain empty (NULL value). 
Page 0 (the internal side of the front cover) is guaranteed to be empty.

cookbook_titles:
|Column|Datatype|
|------|---------|
|page_number|int|
|title|varchar|

```
import pandas as pd
empty_df = pd.DataFrame({'page_number': range(max(cookbook_titles['page_number']) + 1)})
df = pd.merge(empty_df, cookbook_titles, how = 'left', on = 'page_number')
df_even = df[df['page_number']%2==0]
df_odd = df[df['page_number']%2==1]
df_odd['page_number'] = df_odd['page_number']-1
result = pd.merge(df_even, df_odd, how='left', on='page_number').rename(columns = {'page_number':'left_page_number','title_x': 'left_title', 'title_y':'right_title'})
```
