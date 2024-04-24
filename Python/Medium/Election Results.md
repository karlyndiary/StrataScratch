The election is conducted in a city and everyone can vote for one or more candidates, or choose not to vote at all. 
Each person has 1 vote so if they vote for multiple candidates, their vote gets equally split across these candidates. 
For example, if a person votes for 2 candidates, these candidates receive an equivalent of 0.5 vote each.
Find out who got the most votes and won the election. Output the name of the candidate or multiple names in case of a tie. 
To avoid issues with a floating-point error you can round the number of votes received by a candidate to 3 decimal places.

voting_results:
| Column Name | Data Type |
|-------------|-----------|
| voter       | varchar   |
| candidate   | varchar   |

```
import pandas as pd
df = voting_results[voting_results['candidate'].notna()].copy()
df['share'] = 1 / df.groupby('voter', as_index = False)['candidate'].transform('count')
total_shares = df.groupby('candidate', as_index = False)['share'].sum()
total_shares[total_shares['share'] == total_shares['share'].max()]['candidate']
```
