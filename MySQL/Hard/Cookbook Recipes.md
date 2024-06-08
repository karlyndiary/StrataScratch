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
with page_index as (select (row_number() over(order by page_number) - 1) * 2 as left_page,
                           (row_number() over(order by page_number) - 1) * 2 + 1 as right_page
from cookbook_titles)

select t.left_page, t1.title as left_title, t2.title as right_title
from page_index t
left join cookbook_titles t1 on t.left_page = t1.page_number
left join cookbook_titles t2 on t.right_page = t2.page_number
```

Page number starts from 1 in the cookbook_titles the page numbers for both left and right are then calculated from there
left page is calculated -> 1 - 1 * 2 => 0 
right page -> 1 - 1 * 2 + 1 => 3 and so on
