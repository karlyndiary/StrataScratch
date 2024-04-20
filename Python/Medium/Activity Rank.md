Find the email activity rank for each user. Email activity rank is defined by the total number of emails sent. 
The user with the highest number of emails sent will have a rank of 1, and so on. Output the user, total emails, and their activity rank. 
Order records by the total emails in descending order. Sort users with the same number of emails in alphabetical order.
In your rankings, return a unique value (i.e., a unique rank) even if multiple users have the same number of emails. 
For tie breaker use alphabetical order of the user usernames.

google_gmail_emails:
| Column Name | Data Type |
|-------------|-----------|
| id          | int       |
| from_user   | varchar   |
| to_user     | varchar   |
| day         | int       |

```
import pandas as pd
df = google_gmail_emails.groupby('from_user').size().reset_index()
df = df.sort_values([0, 'from_user'], ascending = [False, True])
df['rank'] = df[0].rank(ascending=False, method='first')
df
```
