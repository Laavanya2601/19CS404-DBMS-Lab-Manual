# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--

<img width="682" height="417" alt="597338501-6810c99f-0e34-4a40-9438-7aa48a8fb107" src="https://github.com/user-attachments/assets/14bfad89-8b6d-4da6-95bd-6763a450bdd5" />

```sql

update Employees
set hire_date='2024-01-24'
where department_id=50;

```

**Output:**

<img width="776" height="222" alt="597338521-e27c1c69-4109-488e-80eb-c3f120316f5f" src="https://github.com/user-attachments/assets/a1ef826d-50ed-4ae3-affd-b628d8d73e0d" />



**Question 2**
---

<img width="581" height="550" alt="597338588-2d48c402-4333-409c-a94f-4b67f087bd45" src="https://github.com/user-attachments/assets/80b77491-67dc-4e48-890a-9d70b4a07c7f" />


```sql

update SALES
set sell_price=sell_price+3
where product_id IN (select product_id  from PRODUCTS where supplier_id=4);

```

**Output:**

<img width="772" height="282" alt="597338603-c72c3abb-97ff-4acf-ac06-ff39bfd9fb0a" src="https://github.com/user-attachments/assets/fa4d8053-ccaf-4d36-832b-afb20c0a8922" />



**Question 3**
---


<img width="747" height="365" alt="597338622-aadec72b-c9dc-4690-9c28-ea40f9b21e96" src="https://github.com/user-attachments/assets/b65add59-9a90-454c-a4ed-ddffea5bf173" />

```sql

update products
set sell_price=CAST(cost_price*1.35 AS INT) 
where((sell_price-cost_price)/sell_price)*100<30;

```

**Output:**


<img width="707" height="242" alt="597338653-c0663f50-babd-42ae-9e76-73ad31824cd8" src="https://github.com/user-attachments/assets/a8dec7a5-d0d3-417a-ba60-d4924874749c" />

**Question 4**
---

<img width="685" height="381" alt="597338660-10ba8f76-7c49-45d0-aab9-fe271b256e7a" src="https://github.com/user-attachments/assets/eb56c6cc-6194-4711-939f-7433fb3b4267" />


```sql

update Products 
set category='Household'
where product_name like '%Detergent%';
```

**Output:**



<img width="735" height="282" alt="597338678-823b8322-e985-481e-9fc2-f43bd0dec487" src="https://github.com/user-attachments/assets/799f2533-fc6d-4f5c-a306-a2976f9afc17" />


**Question 5**
---

<img width="682" height="213" alt="597338686-e547c507-1a79-4005-b322-ae2c9d44a98d" src="https://github.com/user-attachments/assets/fd8f6e6c-f66a-4001-8575-9e3e2586263b" />

```sql

update suppliers
set supplier_name='A1 Suppliers'
where supplier_id=8;

```

**Output:**


<img width="671" height="227" alt="597338711-f8d75406-53ac-4038-aa8d-ea343731af3e" src="https://github.com/user-attachments/assets/e6161264-cc1c-4c80-a695-4e883fcc95d7" />



**Question 6**
---


<img width="777" height="732" alt="597338726-4b2f2976-ea79-4680-9a9c-3a4b78e6e838" src="https://github.com/user-attachments/assets/e94164b8-b896-4a49-9392-40a61125b0f8" />

```sql

delete from customer
where AGENT_CODE='A003' or  AGENT_CODE='A008';

```

**Output:**


<img width="480" height="770" alt="597338741-d800cb10-5b06-4f3a-8703-70c9e6623e15" src="https://github.com/user-attachments/assets/76370153-56cf-40ed-ba58-77ed75315322" />

**Question 7**
---


<img width="768" height="356" alt="597338754-1ff90d79-b9f4-426f-87d1-0dc8ee5dc777" src="https://github.com/user-attachments/assets/b27c6304-16f8-47c7-a3f7-7e873d0c2477" />

```sql

delete from  Doctors
where (specialization='Pediatrics' or specialization='Cardiology') and last_name  like 'Brown'; 

```

**Output:**



<img width="762" height="677" alt="597338773-f571bf7d-9004-4583-ba49-546d26f0accd" src="https://github.com/user-attachments/assets/9d6976bc-f5a9-4795-9b48-df7c42ffbe35" />

**Question 8**
---


<img width="777" height="491" alt="597338783-b59c3821-3397-4360-ae4b-bdef31ff3bf8" src="https://github.com/user-attachments/assets/5006dae4-59a7-43fc-a186-a4e8bdfbf461" />

```sql

delete from Customer
where CUST_CITY like "l%";

```

**Output:**

<img width="777" height="761" alt="597338804-859ec185-6735-4ecb-8078-2031e90e4877" src="https://github.com/user-attachments/assets/2fca7141-cb37-4bd8-907c-cf298197514c" />

**Question 9**
---

<img width="772" height="457" alt="597338816-07f5448e-de3a-499d-8ea4-1ba1296d4103" src="https://github.com/user-attachments/assets/d836b909-188a-47ca-bd01-8b92d0e15b88" />

```sql
delete from Customer
where CUST_NAME like "______";

```

**Output:**


<img width="767" height="541" alt="597338832-96a08aa4-414f-402a-8d10-2505c4908753" src="https://github.com/user-attachments/assets/d44c0987-bb44-494d-926a-92e28db16f17" />


**Question 10**
---

<img width="773" height="122" alt="597338842-51e93482-e246-487a-9e94-4586eeff2dce" src="https://github.com/user-attachments/assets/2d1e6aae-7e0a-4066-8340-3c0df784e679" />


```sql

delete from Doctors
where Specialization like 'Pediatrics' and first_name like 'Michael';

```

**Output:**


<img width="765" height="291" alt="597338871-732be449-b281-4d42-a23e-edc7ddf01f01" src="https://github.com/user-attachments/assets/f2e5de2c-472c-490d-be4a-39a6d0d61c87" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.


<img width="1175" height="81" alt="image" src="https://github.com/user-attachments/assets/a5e4ca63-840e-48ea-9f32-d5265770c8f4" />

