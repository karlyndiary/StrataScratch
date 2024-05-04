Find the date with the highest total energy consumption from the Meta/Facebook data centers. Output the date along with the total energy consumption across all data centers.

fb_eu_energy:
| Column Name  | Data Type |
|--------------|-----------|
| date         | datetime  |
| consumption  | int       |

fb_asia_energy:
| Column Name  | Data Type |
|--------------|-----------|
| date         | datetime  |
| consumption  | int       |

fb_na_energy:
| Column Name  | Data Type |
|--------------|-----------|
| date         | datetime  |
| consumption  | int       |

```
import pandas as pd
energy = pd.concat([fb_eu_energy, fb_asia_energy, fb_na_energy])
consumption = energy.groupby(['date']).sum().reset_index()
max_consumption = consumption[consumption['consumption'] == consumption['consumption'].max()][['date','consumption']]
```
