Which user flagged the most distinct videos that ended up approved by YouTube? Output, in one column, their full name or names in case of a tie. 
In the user's full name, include a space between the first and the last name.

user_flags:
| Column Name   | Data Type |
|---------------|-----------|
| worker_ref_id | int       |
| bonus         | int       |

flag_review:
| Column Name       | Data Type  |
|-------------------|------------|
| flag_id           | varchar    |
| reviewed_by_yt    | bool       |
| reviewed_date     | datetime   |
| reviewed_outcome  | varchar    |

```

```
