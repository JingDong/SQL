
175. Combine Two Tables
```sql
select
FirstName, LastName,City, State
from Person
left join
Address
ON
Person.PersonId=Address.PersonId
```

176. Second Highest Salary
```sql
SELECT IFNULL(
(SELECT DISTINCT Salary 
FROM Employee 
ORDER BY Salary DESC LIMIT 1 OFFSET 1),NULL) 
AS SecondHighestSalary
```

181. Employees Earning More Than Their Managers
```sql
Select a.Name as 'Employee'
From
 Employee as a,
 Employee as b
 where a.ManagerId = b.Id and a.Salary > b.Salary
```
182. Duplicate Emails
```sql
Select Email
From Person
Group by Email
Having count(Email) > 1
```

183. Customers Who Never Order
``` sql
Select Name as 'Customers' 
From Customers
left Join Orders
on Orders.customerId = Customers.Id where Orders.CustomerId is null
```

196. Delete Duplicate Emails
```sql
Delete p1 
From Person as p1,
Person as p2 
where p1.Email = p2.Email
And p1.Id > p2.Id
```

197. Rising Temperature
```sql
Select w1.Id As 'Id'
From Weather  w1
join Weather  w2
on DATEDIFF(w1.RecordDate, w2.RecordDate) = 1
and w1.Temperature > w2.Temperature;
```

511. Game Play Analysis I
```sql
select player_id, min(event_date) as 'first_login'
from Activity
group by player_id
```

512. Game Play Analysis II
```sql
select player_id, device_id
from Activity
where (player_id, event_date) 
in 
(select player_id,min(event_date) from Activity group by player_id)
```


577. Employee Bonus
```sql
select e.name, b.bonus
from Employee e
left join Bonus b
on e.empId = b.empId
where b.bonus < 1000 or b.bonus is null
```

584. Find Customer Referee
```sql
select name
from customer
where referee_id != 2 or referee_id is null
```

586. Customer Placing the Largest Number of Orders
```sql
select customer_number
from orders 
group by customer_number
order by count(*) desc
limit 1;
```

595. Big Countries
```sql
Select name, population, area
From World
Where population > 25000000 or area > 3000000;
```



