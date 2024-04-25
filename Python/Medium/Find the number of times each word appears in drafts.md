Find the number of times each word appears in drafts.
Output the word along with the corresponding number of occurrences.

google_file_store:
| Column Name | Data Type |
|-------------|-----------|
| filename    | varchar   |
| contents    | varchar   |

```
import pandas as pd
import numpy as np

draft = google_file_store[google_file_store['filename'].str.contains('draft')]
result = draft.contents.str.split('\W+', expand=True).stack().value_counts().reset_index()
result = result[result['index'] != '']
```
