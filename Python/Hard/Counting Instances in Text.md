Find the number of times the words 'bull' and 'bear' occur in the contents. We're counting the number of times the words occur so words like 'bullish' should not be included in our count.
Output the word 'bull' and 'bear' along with the corresponding number of occurrences.

google_file_store:
| Column Name | Data Type |
|-------------|-----------|
| filename    | varchar   |
| contents    | varchar   |

```
import pandas as pd
google_file_store.contents.str.findall(r'\bbull\b|\bbear\b').explode().value_counts().reset_index()
```
