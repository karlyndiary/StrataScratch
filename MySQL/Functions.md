### EASY
| Function | Description |
|----------|-------------|
| month(joining_date) >= 4 | Filters records where the month of the joining date is greater than or equal to April. |
| avg(salary) over(partition by department) | Calculates the average salary within each department. |
| max(end_time) | Returns the maximum value of the end time. |
| where jobtitle like 'Captain%' | Filters records where the job title starts with 'Captain'. |
| month(date) between 1 and 6 | Filters records where the month of the date falls between January and June. |
| year(date) = 2022 | Filters records where the year of the date is 2022. |
| count(concat(shipment_id, sub_id)) | Counts the concatenated values of shipment_id and sub_id. |
| DATE_FORMAT(shipment_date, '%Y-%m') AS ym | Formats the shipment date as 'Year-Month'. |
| c.first_name in ('Jill','Eva') | Filters records where the first name is either 'Jill' or 'Eva'. |
| abs(max(a.salary) - max(b.salary)) as diff_salary | Calculates the absolute difference between the maximum salaries of two entities. |
| month(time_id) as month | Extracts the month from the time_id. |

### MEDIUM
| Function | Description |
|----------|-------------|
| case when business_name like '%restaurant%' then 'restaurant' | Categorizes records as 'restaurant' if the business name contains the word 'restaurant'. |
| order_date like '%2019-03%' | Filters records where the order date contains '2019-03'. |
| regexp '(plum|rose|cherry|hazelnut)([^a-z])' | Matches strings containing 'plum', 'rose', 'cherry', or 'hazelnut', followed by a non-alphabetical character. |
| datediff(b1.created_at, a1.created_at) between 0 and 7 | Calculates the difference in days between two created_at dates, filtering those differences falling between 0 and 7 days. |
| select * from fb_eu_energy as eu <br> union <br> select * from fb_asia_energy as asia | Performs a union operation on the tables 'fb_eu_energy' and 'fb_asia_energy', selecting all records from both tables. |
| COUNT(CASE WHEN status = 'open' THEN 1 ELSE NULL END) AS active_users | Counts the number of active users based on the status being 'open'. |
| avg(case when (post_keywords like '%spam%') then 1 else 0 end) * 100 as spam_percent | Calculates the percentage of posts flagged as spam based on post keywords. |

### HARD
| Function | Description |
|----------|-------------|
| 'bull' as word | Assigns the string 'bull' to the column 'word'. |
| round((sum(value) - lag(sum(value)) over()) / lag(sum(value)) over() * 100, 2) as percentage_change | Calculates the percentage change between consecutive sums of values, rounded to two decimal places. |
