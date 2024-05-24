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
with cte as (
select date, sum(consumption) as consumption from (
select * from fb_eu_energy as eu
union
select * from fb_asia_energy as asia 
union
select * from fb_na_energy as na ) as sub
group by date )

select * from cte
where consumption = (select max(consumption) from cte)
```
