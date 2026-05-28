# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--


<img width="1245" height="575" alt="597339908-dd3541ca-2a7d-4119-9898-ac2f0ebcf6b0" src="https://github.com/user-attachments/assets/49d58803-0d4c-40f1-8d38-316cf9f20b70" />

```sql

SELECT ord_no,purch_amt,ord_date,customer_id,salesman_id
FROM orders
WHERE salesman_id = (
    SELECT salesman_id
    FROM orders
    WHERE customer_id = 3007
);


```

**Output:**

<img width="1237" height="440" alt="597339923-efca6619-90e4-4756-8661-df6e2809b4b0" src="https://github.com/user-attachments/assets/23af4030-293b-4027-8424-1f5d1a11bda9" />



**Question 2**
---

<img width="983" height="680" alt="597339928-cf081c93-cc94-4509-add3-73e2b2aaaa21" src="https://github.com/user-attachments/assets/18a6a73c-8f80-4af2-828a-84524695db30" />


```sql

select * from CUSTOMERS 
WHERE SALARY>4500;

```

**Output:**


<img width="1202" height="428" alt="597339937-08833032-4745-4793-9fef-4638a6acca57" src="https://github.com/user-attachments/assets/cb48c0ed-b5c8-4432-9fd0-fa18735d1fa9" />


**Question 3**
---

<img width="1077" height="537" alt="597339944-7971f764-2b1a-45d4-9eb7-1967fcd9d6df" src="https://github.com/user-attachments/assets/62977935-00e7-402c-ab0d-ab7a7c7d9ad0" />


```sql

SELECT name, city FROM customer WHERE city IN (SELECT city FROM customer WHERE id IN (3, 7))

```

**Output:**

<img width="547" height="488" alt="597339957-eb135eea-e449-4342-b135-e75a5bee55d0" src="https://github.com/user-attachments/assets/049ad784-9b6c-4ea0-99d8-f35c80ce4717" />



**Question 4**
---

<img width="1250" height="647" alt="597339966-ec8dcde1-c1aa-4ba3-9cbd-30364c8f62bc" src="https://github.com/user-attachments/assets/edb6086a-68bf-48ac-807b-9c90849e8f7e" />

```sql

SELECT student_id, student_name, subject, grade
FROM GRADES g
WHERE grade = (
    SELECT MIN(grade)
    FROM GRADES
    WHERE subject = g.subject
);


```

**Output:**

<img width="1202" height="427" alt="597339971-7cedc63c-b07a-4b18-b647-8e9a5ed18955" src="https://github.com/user-attachments/assets/f9ea4063-95b4-428e-831c-1e75918c8460" />

**Question 5**
---

<img width="1277" height="716" alt="597339981-88adc98a-a2c1-4cfe-af63-84f614cf243a" src="https://github.com/user-attachments/assets/619d292d-a190-4d18-a40d-e4762cfbc471" />

```sql

SELECT
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    o.customer_id,
    o.salesman_id
FROM
    orders o
JOIN
    salesman s ON o.salesman_id = s.salesman_id
WHERE
    s.city = 'New York';

```

**Output:**

<img width="1115" height="446" alt="597339993-b808d2dd-36e8-4a7c-afae-5793774c0966" src="https://github.com/user-attachments/assets/0a0055b6-593a-4389-a751-9be869fb6468" />

**Question 6**
---

<img width="1226" height="578" alt="597340005-17fc4d62-e9f7-429b-9ff9-d97f40da3d8e" src="https://github.com/user-attachments/assets/c2efd2c3-0a3b-4931-8c43-7f98a8a696f4" />

```sql
SELECT student_name, grade
FROM GRADES g
WHERE grade = (
    SELECT MIN(grade)
    FROM GRADES
    WHERE subject = g.subject
);

```

**Output:**

<img width="655" height="427" alt="597340016-104ca694-77fb-4ca9-9288-321406807790" src="https://github.com/user-attachments/assets/88eb5d89-be13-4ee4-a2be-10c23e762fab" />

**Question 7**
---


<img width="1165" height="432" alt="597340023-cc544266-1bc1-4cbc-abba-7e07030ff9de" src="https://github.com/user-attachments/assets/508526e1-f0ec-486e-8bf7-42e1048b049b" />

```sql

SELECT grade, COUNT(*)
FROM customer
WHERE grade>(
    SELECT AVG(grade)   
    FROM customer 
    WHERE city='New York'
)
GROUP BY grade;

```

**Output:**

<img width="497" height="336" alt="597340036-7016811e-60c2-4c6a-8a75-ce3f972bf374" src="https://github.com/user-attachments/assets/9e3efaf9-e8ac-4ba4-a562-a5c3e4cc5259" />



**Question 8**
---

<img width="1012" height="428" alt="597340041-d46ad219-a1e8-4a43-916c-9094512c6d13" src="https://github.com/user-attachments/assets/94561e68-5355-4ca7-86de-b1f580dd2391" />


```sql

SELECT department_id, department_name
FROM Departments
WHERE LENGTH(department_name) > (SELECT AVG(LENGTH(department_name)) FROM Departments);

```

**Output:**


<img width="496" height="392" alt="597340055-e91b3e6a-ddf0-4264-821e-fdd84c708b5f" src="https://github.com/user-attachments/assets/68762650-aa00-4a2f-b5c1-6cc69bbd4220" />


**Question 9**
---

<img width="1262" height="631" alt="597340062-a195cb6f-d586-4eb4-b4f3-511505ea73ce" src="https://github.com/user-attachments/assets/c99c216e-ea69-4f03-81ff-6ba0eabe3a22" />


```sql

SELECT
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    o.customer_id,
    o.salesman_id
FROM
    orders o
JOIN
    salesman s ON o.salesman_id = s.salesman_id
WHERE
    s.city = 'London';

```

**Output:**

<img width="1113" height="405" alt="597340076-15a7a33d-b15b-4f27-9e48-00333806cebf" src="https://github.com/user-attachments/assets/79fa5333-4d47-423c-90ef-48c4348a1f32" />

**Question 10**
---

<img width="963" height="653" alt="597340079-1f771903-dbf9-4b98-8ec7-be49ff75704a" src="https://github.com/user-attachments/assets/b34fb2ce-4fb8-40bb-b103-078a137ca2ef" />


```sql

SELECT *
FROM CUSTOMERS
WHERE SALARY > 1500;
```

**Output:**



<img width="1091" height="578" alt="597340128-496897df-8c98-4fbc-b31f-3cf7bbdd62a7" src="https://github.com/user-attachments/assets/9a974429-d549-40f2-85b9-57ebd53b6d8c" />


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.

<img width="1170" height="81" alt="image" src="https://github.com/user-attachments/assets/8c95a13a-f273-46d8-bd1d-6777d7eabd90" />

