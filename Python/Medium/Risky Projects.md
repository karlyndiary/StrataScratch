Identify projects that are at risk for going overbudget. A project is considered to be overbudget if the cost of all employees assigned to the project is greater than the budget of the project.
You'll need to prorate the cost of the employees to the duration of the project. For example, if the budget for a project that takes half a year to complete is $10K, 
then the total half-year salary of all employees assigned to the project should not exceed $10K. Salary is defined on a yearly basis, so be careful how to calculate salaries 
for the projects that last less or more than one year.
Output a list of projects that are overbudget with their project name, project budget, and prorated total employee expense (rounded to the next dollar amount).
HINT: to make it simpler, consider that all years have 365 days. You don't need to think about the leap years.

linkedin_projects:
| Column Name | Data Type  |
|-------------|------------|
| id          | int        |
| title       | varchar    |
| budget      | int        |
| start_date  | datetime   |
| end_date    | datetime   |

linkedin_emp_projects:
| Column Name | Data Type |
|-------------|-----------|
| emp_id      | int       |
| project_id  | int       |

linkedin_employees:
| Column Name | Data Type |
|-------------|-----------|
| id          | int       |
| first_name  | varchar   |
| last_name   | varchar   |
| salary      | int       |

```

```
