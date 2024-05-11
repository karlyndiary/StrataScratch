Find all posts which were reacted to with a heart. For such posts output all columns from facebook_posts table.

facebook_reactions:
| Field     | Type    |
|-----------|---------|
| poster    | int     |
| friend    | int     |
| reaction  | varchar |
| date_day  | int     |
| post_id   | int     |

facebook_posts:
| Field         | Type      |
|---------------|-----------|
| post_id       | int       |
| poster        | int       |
| post_text     | varchar   |
| post_keywords | varchar   |
| post_date     | datetime  |

```
select *
from facebook_posts fp 
where post_id in (select post_id 
                  from facebook_reactions
                  where reaction = 'heart')
```

```
select distinct fp.* 
from facebook_posts as fp
join facebook_reactions as fr on fp.post_id = fr.post_id
where fr.reaction = 'heart'
```
