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
import pandas as pd
df = pd.merge(facebook_posts, facebook_post_views, on = 'post_id', how = 'inner')
df['is_spam'] = df['post_keywords'].str.contains('spam')
df1 = df.groupby(['post_date']).agg(total_posts = ('post_id', 'count'),spam_posts = ('is_spam', 'sum')).reset_index()
df1['spam_share'] = (df1['spam_posts']/df1['total_posts'])*100
df1[['post_date','spam_share']]
```
