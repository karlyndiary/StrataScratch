ABC Corp is a mid-sized insurer in the US and in the recent past their fraudulent claims have increased significantly for their personal auto insurance portfolio. 
They have developed a ML based predictive model to identify propensity of fraudulent claims. Now, they assign highly experienced claim adjusters for top 5 percentile 
of claims identified by the model.
Your objective is to identify the top 5 percentile of claims from each state. Your output should be policy number, state, claim cost, and fraud score.

fraud_score:
| Column Name | Data Type |
|-------------|-----------|
| policy_num  | varchar   |
| state       | varchar   |
| claim_cost  | int       |
| fraud_score | float     |

```
import pandas as pd
fraud_score['percent'] = fraud_score.groupby(['state'])['fraud_score'].rank(pct = True)
df = fraud_score[fraud_score['percent'] > 0.95]
result = df[['policy_num','state','claim_cost','fraud_score']]
```
