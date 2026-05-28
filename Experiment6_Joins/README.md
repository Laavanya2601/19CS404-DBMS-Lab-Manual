# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--


<img width="582" height="452" alt="597341819-fee7e633-ebf6-42eb-9dee-955a8bbafbb5" src="https://github.com/user-attachments/assets/e316420b-140a-4719-8c79-f1dde78f30b3" />

```sql

select c.cust_name,s.commission from customer c
LEFT JOIN salesman s
ON c.salesman_id=s.salesman_id;

```

**Output:**

<img width="568" height="748" alt="597341841-c5333a91-d2d3-4aac-9c5e-019dbcbbbdbe" src="https://github.com/user-attachments/assets/a21e99b6-b477-419d-b15c-737cda165d15" />

**Question 2**
---

<img width="580" height="812" alt="597341949-c98dd97c-f68b-4df1-b27c-dfd18b49f58c" src="https://github.com/user-attachments/assets/4cfc5ad8-3a32-47d7-9e5f-68400a4b7bd5" />


```sql

select o.ord_no,o.ord_date,o.purch_amt,c.cust_name as "Customer Name",c.grade,s.name as "Salesman",s.commission from orders o
join customer c
on o.customer_id=c.customer_id
join salesman s
on o.salesman_id=s.salesman_id;

```

**Output:**

<img width="570" height="915" alt="597341969-1a5da3ab-1ab8-443d-84e8-20258efcd503" src="https://github.com/user-attachments/assets/2e606577-dc7d-4d2c-bef6-533012737618" />

**Question 3**
---


<img width="565" height="770" alt="597341977-a2fcc7a4-041c-4e30-9f1e-a6207646dc1a" src="https://github.com/user-attachments/assets/524c4e34-5871-4a85-8eff-b646c2309d5f" />

```sql

select o.ord_no,o.purch_amt,o.ord_date,c.cust_name,c.city as "customer_city",c.grade,s.name as "salesman_name",s.city as "salesman_city",s.commission from orders o
inner join customer c
on o.customer_id=c.customer_id
inner join salesman s
on o.salesman_id=s.salesman_id;

```

**Output:**

<img width="572" height="912" alt="597342010-4243d964-28cf-4254-b4df-944bd673ceb6" src="https://github.com/user-attachments/assets/42e4011c-dbaf-41c3-95b7-c0878c7f2c72" />


**Question 4**
---

<img width="612" height="560" alt="597342024-c092ade1-d862-4d7f-a5c1-90dc565e6bd5" src="https://github.com/user-attachments/assets/a71bce3b-39dc-4ae9-98d2-c86cc990944d" />

```sql

select n.nurse_id,department_name from nurses n
inner join departments d
on n.department_id=d.department_id
where n.first_name='David' and  last_name='Moore';
```

**Output:**

<img width="543" height="297" alt="597342041-5cf09f69-214d-40e5-b596-4b2614a795c4" src="https://github.com/user-attachments/assets/d304d1d0-2744-4eb5-aaef-b13e10596d16" />


**Question 5**
---


<img width="578" height="928" alt="597342089-22d47833-dda0-4d78-8d8c-c87df45efb82" src="https://github.com/user-attachments/assets/aa04c490-7fc3-4b2d-a05e-5629693eab86" />

```sql

select c.cust_name,c.city,o.ord_no,o.ord_date,o.purch_amt as "Order Amount" from customer c
left join orders o 
on c.customer_id=o.customer_id
order by o.ord_date ASC;

```

**Output:**


<img width="576" height="916" alt="597342127-e9022d67-634e-4eab-93ad-31366bde9394" src="https://github.com/user-attachments/assets/5f768cfe-c459-4c1e-aba8-f7da0e84c129" />

**Question 6**
---

<img width="607" height="977" alt="597342134-51ff6c34-59e0-49f9-91f1-8d949cfcc275" src="https://github.com/user-attachments/assets/b2123d63-2d5e-40ae-99c4-084274ad2f22" />


```sql

select c.cust_name,c.city,o.ord_no,o.ord_date,o.purch_amt as 'Order Amount',s.name,s.commission
from customer c
left join orders o
on c.customer_id  =o.customer_id  
left join salesman s
on c.salesman_id=s.salesman_id;

```

**Output:**


<img width="573" height="915" alt="597342150-1d0101d1-f406-4c0f-ad00-e6ed6e521880" src="https://github.com/user-attachments/assets/70b051fa-703b-42a7-ba06-f4c607ee2f92" />


**Question 7**
---

<img width="565" height="746" alt="597342179-6178f51f-25ef-4730-b81d-2d9743cc9c34" src="https://github.com/user-attachments/assets/b6a7e9fb-ffb6-4017-b8cb-8bf01a4a9be3" />


```sql

select c.cust_name as 'Customer Name',c.city,s.name as 'Salesman',s.commission
from customer c
join salesman s
on c.salesman_id =s.salesman_id 
where s.commission>0.12;

```

**Output:**

<img width="572" height="561" alt="597342204-4278b75e-30dc-4481-b679-540d28df3247" src="https://github.com/user-attachments/assets/3c7a3cf4-1453-4076-869d-358316c5aa55" />



**Question 8**
---


<img width="588" height="642" alt="597342223-724ce2e6-cddf-49ce-b85e-73fdbefb233d" src="https://github.com/user-attachments/assets/5a844de2-4bd2-42df-944e-447d5d5b7634" />

```sql

SELECT
    p.first_name AS patient_name,
    a.*
FROM
    patients AS p
INNER JOIN
    appointments AS a ON p.patient_id = a.patient_id;


```

**Output:**


<img width="595" height="422" alt="597342265-202772aa-1e90-4546-83bf-a3907737602c" src="https://github.com/user-attachments/assets/2cbca6aa-5dad-4455-adc2-339b7ef995d8" />


**Question 9**
---

<img width="582" height="620" alt="597342290-c62aa786-55fd-4ca6-904e-0b31ee1ad476" src="https://github.com/user-attachments/assets/98354420-1183-4692-9e20-11fc35913c4e" />


```sql
SELECT
    p.first_name AS patient_name,
    d.first_name AS doctor_name
FROM
    patients p
INNER JOIN
    doctors d ON p.doctor_id = d.doctor_id
WHERE
    p.discharge_date IS NOT NULL;

```

**Output:**


<img width="580" height="292" alt="597342353-8f446849-99f1-40fe-ac7f-f438f13e7b5a" src="https://github.com/user-attachments/assets/661c6747-dfe7-4b68-a65f-92e306dd7ddb" />


**Question 10**
---

<img width="590" height="277" alt="597342388-c03e9154-2e60-4ca5-b29b-81214021af08" src="https://github.com/user-attachments/assets/2b1b2b9b-8c4a-49b6-9b43-c1a7ad70c342" />


```sql

select c.* from customer c
left join salesman s on c.salesman_id=s.salesman_id
where s.name="Mc Lyon";

```

**Output:**

<img width="573" height="312" alt="597342441-aea0ef4c-378e-410b-98cd-936b1f03ab4a" src="https://github.com/user-attachments/assets/1cdf8b26-69f8-4d87-a0b5-5f269e48c1e3" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
