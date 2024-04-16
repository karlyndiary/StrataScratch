Meta/Facebook has developed a new programing language called Hack.To measure the popularity of Hack they ran a survey with their employees. 
The survey included data on previous programing familiarity as well as the number of years of experience, age, gender and most importantly satisfaction with Hack. 
Due to an error location data was not collected, but your supervisor demands a report showing average popularity of Hack by office location. 
Luckily the user IDs of employees completing the surveys were stored.
Based on the above, find the average popularity of the Hack per office location.
Output the location along with the average popularity.

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
