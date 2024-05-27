Calculate the percentage of spam posts in all viewed posts by day. A post is considered a spam if a string "spam" is inside keywords of the post. 
Note that the facebook_posts table stores all posts posted by users. The facebook_post_views table is an action table denoting if a user has viewed a post.

facebook_posts:
| Column Name    | Data Type  |
|----------------|------------|
| post_id        | int        |
| poster         | int        |
| post_text      | varchar    |
| post_keywords  | varchar    |
| post_date      | datetime   |

facebook_post_views:
| Column Name | Data Type |
|-------------|-----------|
| post_id     | int       |
| viewer_id   | int       |

```
select post_date, avg(case when (post_keywords like '%spam%') then 1 else 0 end) * 100 as spam_percent
from facebook_posts p 
join facebook_post_views v 
on p.post_id = v.post_id
group by post_date
```
