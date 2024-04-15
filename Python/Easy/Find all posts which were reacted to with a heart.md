Find all posts which were reacted to with a heart. For such posts output all columns from facebook_posts table.

facebook_reactions:
| Column Name | Data Type |
|-------------|-----------|
| poster      | int       |
| friend      | int       |
| reaction    | varchar   |
| date_day    | int       |
| post_id     | int       |

facebook_posts:
| Column Name   | Data Type  |
|---------------|------------|
| post_id       | int        |
| poster        | int        |
| post_text     | varchar    |
| post_keywords | varchar    |
| post_date     | datetime   |

