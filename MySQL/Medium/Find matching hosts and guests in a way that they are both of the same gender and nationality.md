Find matching hosts and guests pairs in a way that they are both of the same gender and nationality.
Output the host id and the guest id of matched pair.

airbnb_hosts:
| Field      | Type      |
|------------|-----------|
| id         | int       |
| user_id    | int       |
| item       | varchar   |
| created_at | datetime  |
| revenue    | int       |

airbnb_guests:
| Field       | Type    |
|-------------|---------|
| guest_id    | int     |
| nationality | varchar |
| gender      | varchar |
| age         | int     |

```
select distinct ah.host_id, ag.guest_id
from airbnb_hosts ah
inner join airbnb_guests ag
on ah.gender = ag.gender and ah.nationality = ag.nationality
```
