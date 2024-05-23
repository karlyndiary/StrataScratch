Find the customer with the highest daily total order cost between 2019-02-01 to 2019-05-01. If customer had more than one order on a 
certain day, sum the order costs on daily basis. Output customer's first name, total cost of their items, and the date.
For simplicity, you can assume that every first name in the dataset is unique.

customers:
| Column Name   | Data Type |
|---------------|-----------|
| id            | int       |
| first_name    | varchar   |
| last_name     | varchar   |
| city          | varchar   |
| address       | varchar   |
| phone_number  | varchar   |

orders:
| Column Name      | Data Type  |
|------------------|------------|
| id               | int        |
| cust_id          | int        |
| order_date       | datetime   |
| order_details    | varchar    |
| total_order_cost | int        |

```
select c.first_name, sum(o.total_order_cost) as total_cost, o.order_date
from customers c 
join orders o 
on c.id = o.cust_id
where order_date between '2019-02-01' and '2019-05-01'
group by order_date, c.first_name
order by total_cost desc
limit 1
```
